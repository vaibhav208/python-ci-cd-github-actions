# Python Flask CI/CD with GitHub Actions (Azure VM Deployment)

This project demonstrates a simple **CI/CD pipeline** using **GitHub Actions** to deploy a Python Flask web application to an **Azure Virtual Machine** using **SSH**.

---

## 🛠 Tech Stack

- **Python + Flask** – Simple web app  
- **GitHub Actions** – CI/CD pipeline  
- **Azure VM** – Hosting the application  
- **SSH** – Secure deployment  
- **Systemd / nohup** – Run app in background  

---

## 🚀 Application Overview

The Flask app returns a simple response at the root URL (`/`):

```python
@app.route('/')
def home():
    return "Hello from Flask deployed via GitHub Actions!"
```

---

## 🔁 CI/CD Workflow

On every push to the `main` branch:

1. GitHub Actions checks out the code  
2. Connects to the Azure VM over SSH  
3. Deploys the updated app (`app.py`)  
4. Installs dependencies in a virtual environment  
5. Starts the app using `nohup` on port `5000`  

---

## 🧠 Secrets Required

Set these **GitHub secrets** under `Settings > Secrets and variables > Actions`:

| Secret Name              | Description                          |
|--------------------------|--------------------------------------|
| `AZURE_VM_PRIVATE_KEY`   | SSH private key to access your VM    |
| `AZURE_VM_USERNAME`      | Username of your Azure VM            |
| `AZURE_VM_IP`            | Public IP address of your Azure VM   |

---

## 🌐 Access the App

After deployment, access your app at:

```
http://<AZURE_VM_IP>:5000
```

> Make sure **port 5000** is allowed in the VM's Network Security Group (NSG) inbound rules.

---

## 📁 Directory Structure

```
.
├── .github
│   └── workflows
│       └── deploy.yml     # GitHub Actions workflow
├── README.md              # This file
└── (app.py generated on VM during deployment)
```

---

## ✅ Status

- [x] CI/CD pipeline works  
- [x] Automatic VM deployment  
- [x] Single-container deployment (Azure VM) 
---

![Screenshot (146)](https://github.com/user-attachments/assets/d3900192-d168-40bb-89b5-2e1cdfa395e4)
![Screenshot (147)](https://github.com/user-attachments/assets/6919d40d-9921-42b1-b28e-0ccce88e3132)
![Screenshot (148)](https://github.com/user-attachments/assets/1a215929-8792-4fcd-9416-99f4d9b3bf45)


## 📬 Author

**Vaibhav**  
[GitHub](https://github.com/vaibhav208)
