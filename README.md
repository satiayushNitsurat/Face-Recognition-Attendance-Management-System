# Face Recognition Attendance Management System

## Overview

This project is a Python-based attendance management system that uses **facial recognition** to automatically record student attendance. The system provides functionality for registering students, capturing their face images, generating facial encodings, recognizing faces through a webcam, and storing attendance records.

It combines **face_recognition (dlib)** for face detection and recognition, **OpenCV** for webcam operations, **Tkinter** for the graphical user interface, and **SQLite3** for maintaining student and attendance information.

## Features

* Register students using their **name and unique student ID (UID)**
* Capture student face images automatically using a webcam
* Generate facial encodings from the captured images
* Recognize registered students in real time
* Automatically record attendance when a student is recognized
* Store attendance details including **UID, date, time, and status**
* View attendance records using **UID or date**
* Reset the complete system for testing or fresh data collection

## Technologies Used

* **Python**
* **face_recognition** – Facial recognition and face encoding using dlib
* **OpenCV** – Webcam access and image processing
* **Tkinter** – Graphical user interface
* **SQLite3** – Local database management
* **NumPy** – Numerical and array operations
* **os / shutil** – File and directory management

## Project Structure

```text
FaceRecognition_AttendanceSystem/
│
├── data_acquisition.py       # Registers students and starts face capture
├── face_capture.py           # Captures student face images
├── face_train.py             # Creates facial encodings
├── mark_attendance.py        # Recognizes faces and records attendance
├── datareport.py             # Displays attendance records
├── clear_data.py             # Resets the complete system
│
├── student_data.db           # SQLite database (created automatically)
├── encodings.pickle          # Generated facial encodings
├── dataset/                  # Stores captured face images
│     └── UID/
│         └── img_0.jpg ... img_9.jpg
│
└── README.md                 # Project documentation
```

## File Descriptions

### `data_acquisition.py`

Provides a Tkinter-based interface where the administrator enters the student's **name and UID**. The information is stored in the database and the face-capture process is started.

### `face_capture.py`

Uses the webcam to capture **10 facial images** for each registered student. The images are saved inside the `dataset` directory according to the student's UID.

### `face_train.py`

Processes the captured images and generates facial encodings for the registered students. These encodings are then stored in the `encodings.pickle` file for use during recognition.

### `mark_attendance.py`

Starts the webcam and performs real-time facial recognition. When a registered student is identified, the system records their attendance in the database. A student is marked only once per day.

### `datareport.py`

Provides a GUI for checking previously recorded attendance. Attendance can be searched using:

* Student UID
* Specific date

### `clear_data.py`

Used to completely reset the project. It removes the stored database information, facial encodings, and dataset so that the system can be used again with fresh data.

## Execution Order

Run the files in the following sequence:

```text
1. data_acquisition.py
       ↓
2. face_train.py
       ↓
3. mark_attendance.py
       ↓
4. datareport.py
```

`clear_data.py` can be executed whenever you want to clear the existing data and start a new testing cycle.

## How to Run

### 1. Install Dependencies

Install the required Python libraries using:

```bash
pip install face_recognition opencv-python numpy
```

> **Note:** Tkinter is generally included with standard Python installations. On some systems, it may need to be installed separately.

### 2. Start Student Registration

Run:

```bash
python data_acquisition.py
```

Enter the student's name and UID, then allow the webcam to capture the required face images.

### 3. Generate Facial Encodings

After capturing the student images, run:

```bash
python face_train.py
```

This creates the facial encoding file used by the recognition system.

### 4. Mark Attendance

Start the real-time recognition module:

```bash
python mark_attendance.py
```

The webcam will identify registered students and record their attendance automatically.

### 5. View Attendance

Run:

```bash
python datareport.py
```

The attendance records can then be viewed using the available UID and date search options.

### 6. Reset the System

If you want to remove the existing data and start again, run:

```bash
python clear_data.py
```

This clears the database, facial encodings, and captured dataset.
ove.
