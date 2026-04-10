# FaceSecuriry — AI-Powered Facial Recognition Attendance System

A smart attendance system that uses the power of Artificial Intelligence to automatically mark and record attendance when a camera recognises a person's face. This eliminates manual attendance tracking, enhancing both **transparency and security** in any environment.

---

## 🚀 Features

- Real-time face detection and recognition via live camera feed
- Automatic attendance logging with sign-in and sign-out times
- Tracks total time spent (seconds, minutes, hours)
- Daily attendance exported to CSV with date-stamped filenames
- Web-based interface powered by Flask
- Handles unknown faces gracefully

---

## 🛠️ Libraries & Technologies

| Library | Purpose |
|---|---|
| `face_recognition` | Face encoding generation and comparison |
| `OpenCV` | Video capture, frame processing and annotation |
| `Pandas` | Attendance data structuring and CSV export |
| `Flask` | Web deployment and attendance display interface |
| `Pickle` | Loading pre-encoded face data |

---

## ⚙️ How It Works

### 1. Face Encoding
A dataset of known faces is fed into the `face_recognition` library, which generates unique numerical encodings for each person. These encodings are saved and loaded at runtime via a `.pkl` file.

### 2. Real-Time Detection
The system captures a live video feed frame by frame using OpenCV. For each frame:
- Face locations are detected
- Encodings are extracted and compared against the known database
- A **green box** is drawn around recognised faces with their name
- A **red box** is drawn around unknown faces

### 3. Attendance Logging
Once a face is recognised, the person's name and exact timestamp are recorded. Using Pandas, the system calculates:
- **Sign-in time** — first time the face was detected
- **Sign-out time** — last time the face was detected
- **Total duration** — time spent in seconds, minutes, and hours

### 4. Web Interface
Built with Flask, the system provides two routes:
- **`/`** — Live video stream with real-time face annotations
- **`/attendance`** — A web table displaying the day's attendance record

---

## 📁 Project Structure

```
FaceSecuriry/
│
├── deploy.py          # Main Flask application
├── a.pkl              # Pre-encoded face data
├── templates/
│   └── table.html     # Attendance display template
└── Attendance_DD_MM_YYYY.csv  # Auto-generated attendance file
```

---

## ▶️ Getting Started

### Prerequisites
```bash
pip install flask face_recognition opencv-python pandas numpy
```

### Run the Application
```bash
python deploy.py
```
Then open your browser and navigate to `http://127.0.0.1:5000`

---

## 📊 Attendance Output Sample

| Name | Sign_in | Sign_Out | Day | Month | Year | Minutes_spent |
|---|---|---|---|---|---|---|
| John | 09:00 AM | 05:00 PM | Mon 7 | April | 2026 | 480 |

---

## 🔮 Future Improvements
- Add a face registration interface via the web app
- Integrate email notifications for attendance summaries
- Add database support (PostgreSQL/SQLite) instead of CSV
- Deploy to cloud (AWS / Heroku)

---



Would you like me to save this as a downloadable file?
