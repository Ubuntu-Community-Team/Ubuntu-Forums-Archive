---
title: "Laptop Built-in camera not working- help pls"
date: 2023-04-19
forum: New to Ubuntu
---

### Post by jiyuu31 on 2023-04-19
Hi. I tried everything I could find it the internet. 
I can not use my camera since it can't be detected even in the Cheese app. 
ls /dev/video*
/dev/video0  /dev/video1
lsusb
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1a2c:95f6 China Resource Semico Co., Ltd USB Gaming Keyboard 
Bus 003 Device 002: ID 1ea7:0064 SHARKOON Technologies GmbH 2.4GHz Wireless rechargeable vertical mouse [More&Better]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0bda:4853 Realtek Semiconductor Corp. Bluetooth Radio
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by MAFoElffen on 2023-04-19
What kind of laptop?
```

sudo dmidecode -t 1,2,3

```

---

### Post by blackbird34 on 2023-04-21
Have you checked if your laptop model has a hardware on/off switch for the camera on the keyboard, e.g one of the function keys? That's caught me more than once.

---

### Post by Impavidus on 2023-04-23
And what version of Ubuntu? If the Ubuntu version is of similar age as the laptop or older, the hardware support isn't always what we'd wish for.

---

