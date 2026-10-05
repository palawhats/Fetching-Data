# Fetching Data - Next.js

โปรเจกต์ตัวอย่างสำหรับศึกษา **Next.js, React, TypeScript, Prisma, SQLite และการ Fetch ข้อมูลจาก API**

ภายในโปรเจกต์ประกอบด้วย 2 ส่วนหลัก

* **Blogs** — ดึงข้อมูลบทความจาก API และแสดงผลเป็นรายการบทความ
* **Students** — ระบบจัดการข้อมูลนักศึกษาแบบ CRUD สามารถเพิ่ม แก้ไข และลบข้อมูลได้

---

## เทคโนโลยีที่ใช้

* Next.js
* React
* TypeScript
* Prisma ORM
* SQLite
* Zod
* CSS
* REST API

---

## ความต้องการของระบบ

ก่อนติดตั้งโปรเจกต์ ควรติดตั้งโปรแกรมต่อไปนี้

* Node.js เวอร์ชัน 18 ขึ้นไป
* npm
* Visual Studio Code (แนะนำ)

ตรวจสอบเวอร์ชัน Node.js:

```bash
node -v
```

ตรวจสอบเวอร์ชัน npm:

```bash
npm -v
```

---

# วิธีการติดตั้ง

## 1. ดาวน์โหลดโปรเจกต์

ดาวน์โหลดหรือ Clone โปรเจกต์ลงในเครื่อง

```bash
git clone <repository-url>
```

จากนั้นเข้าไปยังโฟลเดอร์โปรเจกต์

```bash
cd Fetching-Data-main
```

---

## 2. ติดตั้ง Dependencies

เปิด Terminal ภายในโฟลเดอร์โปรเจกต์ แล้วรัน:

```bash
npm install
```

คำสั่งนี้จะติดตั้ง Package ที่จำเป็นทั้งหมดจาก `package.json`

---

## 3. ตั้งค่า Database

โปรเจกต์นี้ใช้ **SQLite และ Prisma**

สร้างหรืออัปเดต Prisma Client ด้วยคำสั่ง:

```bash
npx prisma generate
```

จากนั้นทำการ Migrate Database:

```bash
npx prisma migrate dev
```

หากโปรเจกต์มีฐานข้อมูล SQLite อยู่แล้ว สามารถใช้ Database ที่มีอยู่ได้

ไฟล์ Database จะอยู่ใน:

```text
prisma/
└── dev.db
```

หรือไฟล์ฐานข้อมูลตามที่กำหนดไว้ใน `schema.prisma`

---

## 4. ตรวจสอบ Prisma Database

สามารถเปิด Prisma Studio เพื่อดูข้อมูลใน Database ได้ด้วยคำสั่ง:

```bash
npx prisma studio
```

จากนั้นเปิด URL ที่แสดงใน Terminal

Prisma Studio สามารถใช้สำหรับ:

* ดูข้อมูลนักศึกษา
* เพิ่มข้อมูล
* แก้ไขข้อมูล
* ลบข้อมูล
* ตรวจสอบข้อมูลใน Database

---

# วิธีการรันโปรเจกต์

ใช้คำสั่ง:

```bash
npm run dev
```

เมื่อรันสำเร็จ จะสามารถเปิดเว็บไซต์ได้ที่:

```text
http://localhost:3000
```

หากต้องการหยุด Server ให้กด:

```text
Ctrl + C
```

---

# การใช้งานระบบ

## 1. หน้าแรก

เปิด:

```text
http://localhost:3000
```

หน้าแรกจะแสดงเมนูและทางเข้าสู่ส่วนต่าง ๆ ของระบบ

---

# 2. ระบบ Blogs

เข้าใช้งานได้ที่:

```text
http://localhost:3000/blogs
```

ระบบ Blogs ใช้สำหรับดึงข้อมูลบทความจาก API และนำมาแสดงบนเว็บไซต์

### การใช้งาน

1. เปิดหน้า Blogs
2. ระบบจะ Fetch ข้อมูลจาก API
3. ข้อมูลบทความจะแสดงเป็น Card
4. แต่ละ Card จะแสดงข้อมูล เช่น รูปภาพ ชื่อบทความ และรายละเอียด
5. คลิกที่บทความเพื่อดูรายละเอียดเพิ่มเติม

ระบบยังมีหน้า:

* Loading
* Error Handling
* Blog Detail
* Dynamic Route

ตัวอย่าง URL สำหรับดูบทความ:

```text
/blogs/1
/blogs/2
/blogs/3
```

โดยเลขท้าย URL จะเป็น ID ของบทความ

---

# 3. ระบบ Students

เข้าใช้งานได้ที่:

```text
http://localhost:3000/students
```

ระบบนี้เป็นระบบจัดการข้อมูลนักศึกษาแบบ CRUD

CRUD ประกอบด้วย:

* **Create** — เพิ่มข้อมูล
* **Read** — แสดงข้อมูล
* **Update** — แก้ไขข้อมูล
* **Delete** — ลบข้อมูล

---

## เพิ่มนักศึกษา

เข้า:

```text
/students
```

จากนั้นกดปุ่ม:

```text
Add Student
```

หรือปุ่มเพิ่มนักศึกษา

กรอกข้อมูลที่จำเป็น เช่น:

* Student Code
* Name
* Email
* Major
* Year

จากนั้นกดปุ่มบันทึก

ระบบจะตรวจสอบข้อมูลก่อนบันทึกลง Database

---

## แก้ไขข้อมูลนักศึกษา

ในหน้ารายชื่อนักศึกษา ให้เลือกนักศึกษาที่ต้องการแก้ไข แล้วกด:

```text
Edit
```

แก้ไขข้อมูลที่ต้องการ จากนั้นกดบันทึก

---

## ลบนักศึกษา

ในหน้ารายชื่อนักศึกษา ให้เลือกข้อมูลที่ต้องการลบ แล้วกด:

```text
Delete
```

ระบบจะลบข้อมูลออกจาก Database

> ควรตรวจสอบข้อมูลก่อนลบ เนื่องจากการลบข้อมูลอาจไม่สามารถย้อนกลับได้

---

# โครงสร้างโปรเจกต์

```text
Fetching-Data-main/
│
├── app/
│   │
│   ├── blogs/
│   │   ├── [id]/
│   │   │   └── page.tsx
│   │   ├── error.tsx
│   │   ├── loading.tsx
│   │   └── page.tsx
│   │
│   ├── students/
│   │   ├── create/
│   │   │   ├── create-student-form.tsx
│   │   │   └── page.tsx
│   │   ├── edit/
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   ├── actions.ts
│   │   ├── delete-button.tsx
│   │   ├── page.tsx
│   │   └── validation.ts
│   │
│   ├── lib/
│   │   └── prisma.ts
│   │
│   ├── ui/
│   │
│   ├── globals.css
│   └── page.tsx
│
├── prisma/
│   ├── schema.prisma
│   └── migrations/
│
├── dev.db
├── package.json
├── tsconfig.json
├── next.config.ts
└── README.md
```

---

# Database Schema

ตารางหลักของระบบคือ `Student`

| Field       | Type     | Description       |
| ----------- | -------- | ----------------- |
| id          | Int      | รหัสข้อมูล        |
| studentCode | String   | รหัสนักศึกษา      |
| name        | String   | ชื่อนักศึกษา      |
| email       | String   | อีเมล             |
| major       | String   | สาขาวิชา          |
| year        | Int      | ชั้นปี            |
| status      | Boolean  | สถานะ             |
| createdAt   | DateTime | วันที่สร้างข้อมูล |
| updatedAt   | DateTime | วันที่แก้ไขข้อมูล |

`studentCode` ถูกกำหนดให้ไม่สามารถซ้ำกันได้

---

# Validation

ข้อมูลนักศึกษาจะถูกตรวจสอบก่อนบันทึกด้วย Zod

ตัวอย่างเงื่อนไข:

* Student Code ต้องไม่เป็นค่าว่าง
* Name ต้องไม่เป็นค่าว่าง
* Email ต้องมีรูปแบบที่ถูกต้อง
* Major ต้องไม่เป็นค่าว่าง
* Year ต้องอยู่ในช่วงที่กำหนด

หากกรอกข้อมูลไม่ถูกต้อง ระบบจะแสดงข้อความแจ้งเตือนและไม่บันทึกข้อมูล

---

# API

ระบบ Blogs ใช้ API สำหรับดึงข้อมูลบทความ

ตัวอย่าง API:

```text
https://api.vercel.app/blog
```

ข้อมูลที่ได้จาก API จะถูกนำมาแสดงบนหน้า Blogs

---

# คำสั่งที่ใช้บ่อย

ติดตั้ง Package:

```bash
npm install
```

รัน Development Server:

```bash
npm run dev
```

Build โปรเจกต์:

```bash
npm run build
```

รัน Production:

```bash
npm start
```

สร้าง Prisma Client:

```bash
npx prisma generate
```

สร้าง Migration:

```bash
npx prisma migrate dev
```

เปิด Prisma Studio:

```bash
npx prisma studio
```

---

# การแก้ปัญหาเบื้องต้น

## พบ Error `Cannot find module 'next/image'`

ให้ติดตั้ง Dependencies ใหม่:

```bash
npm install
```

หากยังไม่หาย ให้ลบ `node_modules` แล้วติดตั้งใหม่

Windows PowerShell:

```powershell
Remove-Item -Recurse -Force node_modules
Remove-Item -Force package-lock.json
npm install
```

จากนั้นรัน:

```bash
npm run dev
```

---

## Prisma Error

ลองสร้าง Prisma Client ใหม่:

```bash
npx prisma generate
```

จากนั้น:

```bash
npx prisma migrate dev
```

---

# ผู้จัดทำ

โปรเจกต์นี้จัดทำขึ้นเพื่อศึกษาและฝึกปฏิบัติการพัฒนา Web Application ด้วย Next.js และเทคโนโลยีที่เกี่ยวข้อง

**Project:** Fetching Data
**Framework:** Next.js
**Database:** SQLite
**ORM:** Prisma
