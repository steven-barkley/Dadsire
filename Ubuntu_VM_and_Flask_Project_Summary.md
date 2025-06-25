# ✅ System Preparation Summary for Ubuntu Project

**Date Range**: June 25, 2025  
**Prepared by**: Steven Barkley  
**Mentor**: Jeff  
**Goal**: Prepare a stable and performant Ubuntu virtual machine on a Windows 10 PC with 6 cores and limited disk space, to support development of a small project using Flask.

---

## 🛠️ Phase 1 – System Cleanup & Resource Recovery (June 25 Morning)

- Identified large unnecessary system folders, specifically `Windows.old`, which was consuming ~85 GB of disk space.
- Used **Disk Cleanup** to safely remove this folder after verifying that rollback to a previous Windows version was no longer required.
- **Result**: Freed 85+ GB, increasing free disk space from **22 GB to 107 GB**.

---

## 🧠 Phase 2 – Virtual Machine Planning (Midday)

- Reviewed physical system specs: **6 CPU cores**, **Windows 10**, and **sufficient memory for VM hosting**.
- Determined ideal VM allocation:
  - **2 CPU cores**
  - **4 GB RAM**
  - **20.25 GB virtual disk** (initially)

---

## 🧰 Phase 3 – Ubuntu VM Troubleshooting and Successful Installation

- First two installation attempts failed due to insufficient RAM (2 GB), causing freezes during file copying.
- Resolved the issue by **increasing RAM to 4 GB** and allocating **2 CPU cores** to the VM.
- Performed a successful install of **Ubuntu 22.04 Desktop (GUI)**.
- Completed initial package updates:
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```

---

## 💾 Phase 4 – Increasing VM Disk Size (Afternoon)

- Realized the default 20.25 GB disk was insufficient for development.
- Located and verified the path to the `.vdi` virtual hard disk file, correcting a path formatting error involving spaces.
- Executed the following command from Command Prompt to increase the disk to **50 GB**:
  ```bash
  "D:\VirtualBox\VBoxManage.exe" modifyhd "C:\Users\Steven Barkley\VirtualBox VMs\Ubuntu Project\Ubuntu Project.vdi" --resize 51200
  ```
- Verified the virtual disk was resized successfully via progress feedback in CMD.

---

## 🧱 Phase 5 – Partition Expansion (In Progress / Next Steps)

- Installed `gparted` on Ubuntu to visually manage partitions:
  ```bash
  sudo apt install gparted
  ```
- Preparing to use GParted to expand the main partition and utilize the newly added unallocated disk space.

---

## 🌐 Phase 6 – Flask Development Environment Setup

- Activated a Python virtual environment:
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```
- Installed Flask using pip within the virtual environment:
  ```bash
  pip install flask
  ```
- Confirmed proper environment configuration and Flask installation.
- Created a basic Flask app (`hello.py`) and verified it by accessing the running server via browser:
  ```python
  from flask import Flask

  app = Flask(__name__)

  @app.route("/")
  def hello_world():
      return "Hello from Flask inside the virtual environment!"
  ```
- Output confirmed: **"Hello from Flask inside the virtual environment!"** successfully rendered in browser at `http://127.0.0.1:5000/`.

---

## ✅ Summary of Accomplishments

- Freed up **~85 GB** of disk space on host machine
- Successfully installed a stable Ubuntu 22.04 Desktop VM
- Resolved freezing by tuning VM resource allocations
- Increased VM disk size from **20.25 GB → 50 GB**
- Configured Python virtual environment
- Installed and tested Flask app with live browser output
