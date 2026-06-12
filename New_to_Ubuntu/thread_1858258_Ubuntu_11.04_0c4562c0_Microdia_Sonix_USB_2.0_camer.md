---
title: "Ubuntu 11.04 0c45:62c0 Microdia Sonix USB 2.0 camera"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by deuxalucard on 2011-10-12
Hi I have a Hp dv6450us with Ubuntu 11.04 installed, and I can't use my webcam does somebody could help me?? please

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


uname -r
2.6.38-11-generic

---

### Post by Pynalysis on 2011-10-12
> **deuxalucard said:**
> Hi I have a Hp dv6450us with Ubuntu 11.04 installed, and I can't use my webcam does somebody could help me?? please

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


uname -r
2.6.38-11-generic

Is your webcam recognized with cheese or gucview?

---

### Post by deuxalucard on 2011-10-12
> **Pynalysis said:**
> Is your webcam recognized with cheese or gucview?

cheese doesn't recognize my webcam, let me try with gucview

---

### Post by deuxalucard on 2011-10-12
> **deuxalucard said:**
> cheese doesn't recognize my webcam, let me try with gucview

yep, it works, thank you very much my friend

---

### Post by Pynalysis on 2011-10-13
Anytime :)

---

