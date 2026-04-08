# 🚗 Vehicle OCR Scanner

แอป Android สำหรับสแกนและเก็บข้อมูลยานพาหนะด้วย Google ML Kit OCR  
รองรับ: ชื่อผู้ใช้, เลขทะเบียน, VIN, เลขกล่อง, เลขไมล์

---

## ✨ ฟีเจอร์

- 📷 **สแกนรูปภาพ** จากกล้องหรือแกลเลอรี่
- 🔍 **OCR อัตโนมัติ** ด้วย Google ML Kit (ทำงานออฟไลน์ ไม่ต้องใช้ API key)
- ✏️ **แก้ไขข้อมูล** ที่อ่านได้ไม่ถูกต้อง
- 📋 **Copy string** พร้อมใช้งานในคลิก เดียว
- 💾 **บันทึก JSON** ลงในเครื่อง
- 📊 **Export CSV** แล้ว Share ออกได้เลย

---

## 📁 โครงสร้างโปรเจกต์

```
vehicle_ocr/
├── lib/
│   ├── main.dart                    # Entry point + Theme
│   ├── models/
│   │   └── vehicle_record.dart      # Data model
│   ├── services/
│   │   ├── ocr_service.dart         # Google ML Kit OCR
│   │   └── storage_service.dart     # JSON storage + CSV export
│   └── screens/
│       ├── home_screen.dart         # รายการทั้งหมด
│       ├── scan_screen.dart         # สแกนและบันทึก
│       └── record_detail_screen.dart # ดูและแก้ไข
├── android/
│   └── app/
│       ├── src/main/AndroidManifest.xml
│       ├── build.gradle
│       └── proguard-rules.pro
├── .github/workflows/
│   └── build-apk.yml               # GitHub Actions
├── codemagic.yaml                   # Codemagic CI/CD
└── pubspec.yaml
```

---

## 🚀 วิธี Build APK (เลือกวิธีใดวิธีหนึ่ง)

### วิธีที่ 1: GitHub Actions (แนะนำ - ฟรี)

1. สร้าง repository ใหม่ใน GitHub
2. อัปโหลดโค้ดทั้งหมดขึ้น GitHub
3. ไปที่ **Actions** > จะเห็น workflow "Build Flutter APK"
4. กด **Run workflow** หรือ push code ใหม่
5. รอประมาณ **5-10 นาที**
6. ดาวน์โหลด APK จาก **Artifacts**

**วิธี push ผ่านมือถือ (GitHub app หรือ Working Copy):**
- ใช้แอป [Working Copy](https://workingcopy.app/) บน iOS  
- หรือ [Spck Editor](https://spck.io/) บน Android

---

### วิธีที่ 2: Codemagic.io (ง่ายมาก)

1. ไปที่ [codemagic.io](https://codemagic.io) → Sign up ด้วย GitHub
2. เพิ่มโปรเจกต์ → เลือก repo นี้
3. ไฟล์ `codemagic.yaml` จะถูกอ่านอัตโนมัติ
4. กด **Start new build**
5. ดาวน์โหลด APK จาก email หรือ dashboard

**Free tier:** 500 นาที/เดือน (เพียงพอสำหรับ build ส่วนตัว)

---

## 📦 Dependencies

| Package | วัตถุประสงค์ |
|---------|------------|
| `google_mlkit_text_recognition` | OCR ออฟไลน์ ไม่ต้อง API key |
| `image_picker` | เลือกรูปจากกล้อง/แกลเลอรี่ |
| `path_provider` | เข้าถึง storage บนเครื่อง |
| `share_plus` | แชร์ไฟล์ CSV |
| `csv` | สร้างไฟล์ CSV |
| `flutter_animate` | animation สวยงาม |
| `google_fonts` | ฟอนต์ Krub (ภาษาไทย) |

---

## 🔧 หากต้องการปรับแต่ง OCR

แก้ไขใน `lib/services/ocr_service.dart`:
- เพิ่ม regex pattern สำหรับรูปแบบทะเบียนหรือ VIN เฉพาะ
- ปรับ label keywords ให้ตรงกับเอกสารที่ใช้จริง

---

## 📱 ความต้องการของระบบ

- Android 5.0+ (API 21+)
- Camera permission (สำหรับถ่ายรูป)
- Storage permission (Android 12 และต่ำกว่า)
