# 🦾 6-DOF Robotic Arm — Multi-Mode Control (ESP32 + Python + Web)

This project demonstrates a **6 Degree of Freedom (6-DOF) Robotic Arm** powered by **ESP32**, capable of operating in **four distinct modes**:  
**1️⃣ Joystick Control · 2️⃣ Web Interface Control · 3️⃣ Hand Gesture Control · 4️⃣ Autonomous Pick & Place**

Each mode showcases a unique way of controlling the robotic arm using embedded systems, web technologies, and computer vision.

---

## 🚀 Table of Contents

- [Overview](#-overview)
- [Modes of Operation](#-modes-of-operation)
  - [Joystick Control](#1-joystick-control)
  - [Web Interface Control](#2-web-interface-control)
  - [Hand Gesture Control](#3-hand-gesture-control)
  - [Autonomous Pick--Place](#4-autonomous-pick--place)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Hardware Requirements](#-hardware-requirements)
- [Software Setup](#-software-setup)
- [How to Run](#-how-to-run)
- [System Overview](#-system-overview)
- [Future Improvements](#-future-improvements)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

---

## 🧠 Overview

The 6-DOF robotic arm is designed to perform precise movements and tasks under multiple control interfaces.  
The project integrates **ESP32 microcontroller**, **Python-based computer vision**, and **WebSocket communication** to deliver real-time, versatile control.

---

## 🔧 Modes of Operation

### 1. 🎮 Joystick Control
- Runs directly on the **ESP32**.  
- Utilizes **three analog joysticks**, each axis controlling one servo motor.  
- The control logic:
  - When joystick readings exceed a defined **threshold**, the corresponding servo rotates by a **fixed delta angle per second**.
- Enables smooth, manual control of all six servo motors.

---

### 2. 🌐 Web Interface Control
- Built using **ESP32 Wi-Fi** and **WebSocket communication**.  
- The web client (hosted via **Render.com**) sends servo angles through a **relay server** to the ESP32.  
- ESP32 receives and executes the movement commands in real-time.  
- Features a **responsive web interface** for angle input and control.

---

### 3. ✋ Hand Gesture Control
- Implemented in **Python** using **OpenCV** for real-time hand tracking.  
- Detects and counts **number of fingers raised** using a webcam feed.  
- Each finger count corresponds to a specific servo motor.  
- The mapped servo moves by a **fixed delta angle** when the gesture is detected.  
- Communicates with ESP32 via **serial port** (`pyserial`).

---

### 4. 🤖 Autonomous Pick & Place
- Python-based **autonomous control mode**.  
- The user inputs **pick coordinates (x, y, z)** via terminal.  
- Python computes **inverse kinematics** to determine the necessary servo angles.  
- ESP32 executes the pick-and-place motion sequence.  
- Demonstrates fully automated operation.

---

## 🧰 Tech Stack

| Component | Technology |
|------------|-------------|
| **Microcontroller** | ESP32 |
| **Languages** | C++ (Arduino), Python, HTML, JavaScript |
| **Libraries (Arduino)** | Servo, WiFi, WebSocket |
| **Libraries (Python)** | OpenCV, PySerial, NumPy |
| **Web Hosting** | Render.com (WebSocket relay & UI hosting) |

---

## 📂 Project Structure

├── esp32/
│ ├── joystick_control/
│ ├── websocket_control/
│ ├── common/
├── python/
│ ├── hand_gesture_control/
│ ├── pick_and_place/
│ ├── utils/
├── web/
│ ├── index.html
│ ├── websocket_client.js
│ └── styles.css
└── README.md


---

## ⚙️ Hardware Requirements

- **ESP32 Development Board**
- **6x Servo Motors (3 -MG995 , 3 -SG90 )**
- **3x Analog Joysticks**
- **Camera/ laptop webcam (for gesture detection)**
- **External Power Supply for Servos -- Lipo with buck converter**
- **Jumper Wires, Breadboard, and Connectors**

---

## 🧩 Software Setup

### 🖥️ Arduino IDE Setup
1. Install **ESP32 board package** in Arduino IDE.  
2. Install libraries:
   - `ESP32Servo.h`
   - `WiFi.h`
   - `WebSocketsClient.h`
3. Flash the corresponding `.ino` file depending on the mode.

### 🐍 Python Setup
```bash
pip install opencv-contrib-python pyserial numpy mediapipe

▶️ How to Run
1️⃣ Joystick Mode

Upload joystick_control.ino to ESP32.

Connect joysticks to analog pins.

Move joysticks to control each servo axis.

2️⃣ Web Mode

Upload websocket_control.ino to ESP32.

Open the hosted web interface.

Adjust angles and observe real-time servo motion.

3️⃣ Gesture Mode

Connect camera and ESP32 via USB.

Run:

python hand_gesture_control.py


Move your hand in front of the camera to control servos.

4️⃣ Pick & Place Mode

Run:

python pick_and_place.py


Enter pick coordinates in terminal.

The arm will autonomously pick and place the object.



