# 🧭 Maze Solving Robot – Polymaze Competition

The source code for an **autonomous line follower and maze-solving robot**, developed by **vic-spark-enp** for the **Polymaze competition**.

We built **two versions of this robot (2023 & 2024)**, each with a unique mechanical design and control architecture.


![Robot Overview](images/robot_overview.jpg)

---

## **Design Evolution (2023 → 2024)**

### **2023 Version – 4-Motor Design**
The 2023 robot used **four motors with four wheels**, providing good mechanical stability. However, this configuration required complex motor synchronization, higher power consumption, and increased wiring complexity, which made precise control more difficult.

![2023 Robot](images/robot_2023.jpg)

### **2024 Version – 2-Motor Differential Drive**
In 2024, we switched to a **2-motor differential drive** architecture to simplify control and improve performance.

**Why we chose the 2-motor design:**
- More accurate and predictable turns  
- Easier and more stable **PID control**  
- Reduced weight and power consumption  
- Lower mechanical and wiring complexity  
- Improved reliability in maze navigation  

![2024 Robot](images/robot_2024.jpg)

---

## **Robot Functionality (Technical Overview)**

The robot is an **autonomous line-following and maze-solving system** controlled by an **ESP32 Wroom 32D**. It navigates the maze independently, focusing on precision, speed, and stability.

![System Architecture](images/system_architecture.jpg)

---

## **Line Following & PID Control**

The robot uses a **QTR A8 IR sensor array** to continuously detect the position of the black line relative to its center. A **PID controller** computes the error and generates a control signal:

- **Proportional (P):** Corrects immediate deviation from the line  
- **Integral (I):** Compensates accumulated long-term error  
- **Derivative (D):** Reduces oscillations and smooths turns  

The PID output dynamically adjusts the speed difference between the **two N20 DC motors** via the **L293D motor driver**, enabling smooth and accurate differential steering, especially at intersections and sharp turns.

![PID Control](images/pid_control.jpg)

---

## **Maze Solving Logic**

The robot autonomously explores the maze by detecting junctions using the IR sensor array and applies a predefined maze-solving strategy (e.g., left-hand rule or optimized path learning).  
Once the optimal path is identified, the robot traverses the maze at higher speed while maintaining stability using the tuned PID loop.

![Maze Solving](images/maze_solving.jpg)

---

## **Color Detection & Mini-Games**

A **TCS34725 color sensor** enables interaction with Polymaze mini-games:

- **Red band detected:** Activates a red LED  
- **Blue band detected:** Triggers a buzzer  
- **Maze exit detected:** Displays **“Prison Break”** on the OLED screen  

![Color Detection](images/color_detection.jpg)

---

## **Power & System Stability**

The robot is powered by **three 3.7V LiPo batteries**. A **7805 linear voltage regulator** ensures a stable voltage supply for logic and sensors.  
The ESP32 handles real-time sensor processing, PID computation, and motor control without any external assistance.

---

## **Main Components**

### **Controller**
- ESP32 Wroom 32D (30-pin)

### **Actuators**
- 2 × N20 DC motors  
- L293D motor driver IC  

### **Sensors**
- QTR A8 IR array (line detection)  
- TCS34725 color sensor  

### **Output Modules**
- Red LED  
- Buzzer  
- SSD1306 OLED display  

### **Power**
- 3 × LiPo 503450 (3.7V, 1000mAh)  
- 7805 voltage regulator  

---

## **Software Dependencies**

Make sure the following libraries are installed:

- `Wire`
- `QTRSensors`
- `Adafruit SSD1306`
- `Adafruit TCS34725`
- `Adafruit BusIO`
- `SPI`
