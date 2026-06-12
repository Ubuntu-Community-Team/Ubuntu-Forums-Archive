---
title: "USB-C Port not working in ubuntu"
date: 2023-03-07
forum: New to Ubuntu
---

### Post by lovedlx on 2023-03-07
I have an HP laptop with Ubuntu installed on an external hard drive and when I try to use the computer's usb-c port it doesn't detect it
MY laptop only has two usb-a ports and I need to use 3 ports so that's why I had a usb-a to usb-c adapter to connect for example my keyboard through the usb-c port with the adapter and this works correctly when I use it in windows (in the internal hard disk of the laptop I have windows and in an external disk I have ubuntu)

and I don't know what I can do to make the usb-c port work in ubuntu


[I]System info:
[/I]```
System: Ubuntu 22.04.2 LTS

Machine: HP ENVY x360 Convertible 13-ag0xxx

CPU: AMD Ryzen 7 2700U with Radeon Vega Mobile Gfx

Graphics: Radeon Vega Series / Radeon Vega Mobile Series
```

[I]lsusb output:

[/I]```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:b00b Realtek Semiconductor Corp. Realtek Bluetooth 4.2 Adapter
Bus 003 Device 002: ID 04f2:b654 Chicony Electronics Co., Ltd HP IR Camera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 152d:0578 JMicron Technology Corp. / JMicron USA Technology Corp. JMS578 SATA 6Gb/s
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b653 Chicony Electronics Co., Ltd HP Wide Vision HD Camera
Bus 001 Device 006: ID 18f8:0f97 [Maxxter] Optical Gaming Mouse [Xtrem]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by MAFoElffen on 2023-03-07
> **lovedlx said:**
> I have an HP laptop with Ubuntu installed on an external hard drive and when I try to use the computer's usb-c port it doesn't detect it
MY laptop only has two usb-a ports and I need to use 3 ports so that's why I had a usb-a to usb-c adapter to connect for example my keyboard through the usb-c port with the adapter and this works correctly when I use it in windows (in the internal hard disk of the laptop I have windows and in an external disk I have ubuntu)

and I don't know what I can do to make the usb-c port work in ubuntu

[I]lsusb output:
[/I]```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:b00b Realtek Semiconductor Corp. Realtek Bluetooth 4.2 Adapter
Bus 003 Device 002: ID 04f2:b654 Chicony Electronics Co., Ltd HP IR Camera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 152d:0578 JMicron Technology Corp. / JMicron USA Technology Corp. JMS578 SATA 6Gb/s
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b653 Chicony Electronics Co., Ltd HP Wide Vision HD Camera
[COLOR=#ff0000]Bus 001 Device 009: ID 320f:5060 Evision RGB Keyboard
[/COLOR]Bus 001 Device 008: ID 18f8:0f97 [Maxxter] Optical Gaming Mouse [Xtrem]
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I see a keyboard, a mouse and a "Terminus Technology Inc. Hub"... But you would think that it would be something off of Bus 002, not off Bus 001, like I'm seeing. IDK yet.

---

### Post by lovedlx on 2023-03-07
oh true that when I executed the lsusb command I had the mouse and keyboard connected with a usb hub that I had lying around but that I don't use since it's old and doesn't work very well

I already edited the post and the result of the lsusb command appears, now with the keyboard connected via usb-c

---

