# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1920" height="1200" alt="Screenshot 2025-11-10 124822" src="https://github.com/user-attachments/assets/2077b1f4-ad4a-425e-b347-ff3d9c153a96" />

2. Click **File → New STM32 Project**.
   <img width="1033" height="554" alt="Screenshot 2025-11-11 041003" src="https://github.com/user-attachments/assets/099e4f08-b37d-4c84-862d-c3b8e99a155d" />
   <img width="1038" height="562" alt="Screenshot 2025-11-11 041025" src="https://github.com/user-attachments/assets/c0e2f68b-bfbb-40b1-a226-fe5353dc0b8d" />


3. Select the **target microcontroller** or board and click **Next**.
    <img width="1039" height="560" alt="Screenshot 2025-11-11 041054" src="https://github.com/user-attachments/assets/2693b10f-3274-4071-8b18-40e1057e3888" />


4. Name the project.
<img width="642" height="551" alt="Screenshot 2025-11-10 233009" src="https://github.com/user-attachments/assets/ac653713-7e2f-464d-ac0a-0d9493146a26" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="1040" height="559" alt="Screenshot 2025-11-10 233043" src="https://github.com/user-attachments/assets/00f8d127-33e2-4e62-b2db-1f302b7a63a6" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1001" height="565" alt="Screenshot 2025-11-10 233127" src="https://github.com/user-attachments/assets/c7380893-2ec7-4e51-bf5f-8277db781623" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="1050" height="560" alt="Screenshot 2025-11-10 233204" src="https://github.com/user-attachments/assets/18ce0e81-841e-41d8-a80b-1e312ad0be3d" />

8. Edit the generated main program as required.
<img width="1035" height="566" alt="Screenshot 2025-11-10 233318" src="https://github.com/user-attachments/assets/ee21b745-05f7-4b63-ac3b-bd0814ba655b" />

9. Click **Project → Build All**.
 <img width="1007" height="562" alt="Screenshot 2025-11-10 233347" src="https://github.com/user-attachments/assets/05d09ff3-3467-458a-ad4c-f1558af38628" />
   
10. Link the **HEX file** using the post-build process.
<img width="897" height="327" alt="Screenshot 2025-11-10 233414" src="https://github.com/user-attachments/assets/87ca0ed1-6749-49ee-b00f-49a5b2b6ff2d" />

11. Click **Debug** and connect the **STM Nucleo Board**.
 <img width="1040" height="567" alt="Screenshot 2025-11-10 233441" src="https://github.com/user-attachments/assets/6c65f0b7-ed05-4f1c-a3ad-24c485b3f1d6" />
   
13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON

<img width="848" height="362" alt="Screenshot 2025-11-10 233632" src="https://github.com/user-attachments/assets/e204a7ce-d436-44a8-87e9-b7ec83e32f90" />

CASE 2: LED OFF

<img width="759" height="357" alt="Screenshot 2025-11-10 233700" src="https://github.com/user-attachments/assets/f7dbaa94-600d-46d6-b381-2abb9cc7bb7d" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
