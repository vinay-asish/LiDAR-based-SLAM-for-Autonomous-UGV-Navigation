# LiDAR-based-SLAM-for-Autonomous-UGV-Navigation
autonomous navigation on an Ackermann chassis through path planning and obstacle avoidance
# 🚙 LiDAR-based SLAM for Autonomous UGV Navigation

## 📌 Overview
This repository contains a **ROS Catkin Workspace** for implementing **LiDAR-based SLAM** and **Autonomous Navigation** on an **Unmanned Ground Vehicle (UGV)**.  
It supports multiple SLAM algorithms (Cartographer, GMapping, Hector, Karto) and integrates with **Jetson CSI Camera** for vision support.  
Navigation is handled via `move_base` with costmaps and TEB planner.

---

## 📂 Project Structure
catkin_ws/
├── src/
│ ├── jetracer_ros/ # Main SLAM & navigation package
│ │ ├── cfg/ # Dynamic reconfigure configs
│ │ ├── config/ # SLAM & navigation parameters
│ │ ├── launch/ # Launch files (SLAM, nav, camera, etc.)
│ │ ├── maps/ # Map saving scripts
│ │ ├── scripts/ # Python nodes (nav, TTS, filtering, etc.)
│ │ ├── src/ # C++ source nodes
│ │ └── package.xml
│ │
│ └── jetson_csi_cam/ # Jetson CSI camera package
│ ├── launch/
│ ├── src/
│ └── package.xml
└── CMakeLists.txt

yaml
Copy code

---

## ⚡ Features
- 🔹 Multiple SLAM backends: **Cartographer, GMapping, Hector, Karto**  
- 🔹 Autonomous navigation with **AMCL + move_base + costmaps**  
- 🔹 Jetson CSI camera integration  
- 🔹 Dynamic reconfigure support  
- 🔹 Multi-point navigation  
- 🔹 Speech recognition + Text-to-Speech nodes  

---

## ⚙️ Installation

### 1. Clone & Build
```bash
git clone https://github.com/<your-username>/LiDAR-based-SLAM-for-Autonomous-UGV-Navigation.git
cd LiDAR-based-SLAM-for-Autonomous-UGV-Navigation/catkin_ws
catkin_make
source devel/setup.bash
2. Dependencies
Make sure the following are installed:

ROS (Melodic/Noetic recommended)

Cartographer ROS

GMapping / Hector / Karto

Jetson Nano/Xavier (for camera support)

▶️ Usage
Run SLAM
bash
Copy code
roslaunch jetracer_ros cartographer.launch   # Cartographer
roslaunch jetracer_ros gmapping.launch       # GMapping
roslaunch jetracer_ros hector.launch         # Hector SLAM
roslaunch jetracer_ros karto.launch          # Karto
Run Navigation
bash
Copy code
roslaunch jetracer_ros nav.launch
Save Map
bash
Copy code
rosrun map_server map_saver -f ~/map
Jetson CSI Camera
bash
Copy code
roslaunch jetson_csi_cam jetson_csi_cam.launch
📝 Useful Scripts
multipoint_nav.py → Autonomous multi-goal navigation

laser_filter.py → LiDAR scan filtering

odom_ekf.py → Odometry fusion with EKF

tts_en.py, tts_cn.py → Text-to-Speech nodes

aiui.py, asr.launch, talk.launch → Speech interaction

🚀 Roadmap
 Add 3D LiDAR support

 Integrate advanced planners (RRT*, DWA, etc.)

 Optimize real-time performance for Jetson
