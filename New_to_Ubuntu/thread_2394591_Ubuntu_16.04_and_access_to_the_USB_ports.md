---
title: "Ubuntu 16.04 and access to the USB ports"
date: 2018-06-18
forum: New to Ubuntu
---

### Post by po78 on 2018-06-18
Hi,

I am trying to connect to a drone via a radio dongle in one of the USB Ports of my laptop

I'm not sure ubuntu 16.04 (just installed) is even seeing the USB ports

When trying to send a command via the radio dongle via the USB from Ubuntu i get 

'No matching USB device with dev id=0 found'

Would appreciate any ideas

---

### Post by Holger_Gehrke on 2018-06-19
Your post is a bit thin on useful information for people who want to help you. What kind of radio dongle is it, what program are you trying to use to send commands ? You might want to use 'lsusb' from the command line to see your devices connected to USB and 'lsusb -v -s bus:device' for more information on a specific device (substituting numbers from the output of the first command for 'bus' and 'device').

Holger

---

### Post by po78 on 2018-06-19
Hi Holger,

Thank you for your reply.

The radio dongle is a Crazyradio PA for use with the crazyflie 2.0 drone. There is a crazyswarm application that allows me to fly multiple drones. It is loaded on ubuntu 16.04 and should communicate with the crazyflie drone using the radio dongle plugged into the USB port. The communication is fine through python and windows but it seems that Ubuntu doesent recognise the USB drives.

Running lsusb does nothing, it completes, but nothing shows up on the command line

If you were to load Ubuntu 16.04 terminal onto a laptop, would you normally have access to USB and the lsusb command?

I downloaded Ubuntu 16.04 terminal from the Microsoft store

---

### Post by Holger_Gehrke on 2018-06-19
Okay.

What you're saying means you're not running Ubuntu directly, you're running Ubuntu on WSL (Windows Subsystem for Linux). Since I've been free of Windows for longer than that exists, I can't tell you anything about it. Running Ubuntu directly on the machine gives full access to the hardware including the USB. When I enter 'lsusb' I get a dozen lines of output, one for each device on USB on my laptop. 

Holger

---

### Post by po78 on 2018-06-20
Holger,

Your on the right track, its the version of Ubuntu

[COLOR=#111111][FONT=Ubuntu]for those looking at a similar issue in the future, a solution from Arnaud.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The Ubuntu 16.04 installation I used was the Windows subsystem for linux version. As of 20.6.2018 they have not implemented any USB functionality on this version and so I was unable to look at any USB details or use the lsusb command.[/FONT][/COLOR]

---

### Post by bijayalaxmi1808 on 2018-06-21
I see there are many Ubunut variants available in Microsoft store.
What's the [COLOR=#111111][FONT=Ubuntu]Windows subsystem for linux version and how is it different from virtual environment like Virtual Box?
[/FONT][/COLOR]
Is there any option like the Virtual Box where you can assign USB ports to the guest environment to access?

Another possible solution could be; you need to install the Ubuntu on a virtual box.

---

### Post by Holger_Gehrke on 2018-06-22
From what I found on the web, it looks like the wsl is closer to wine than to virtual Box. It's a compatibility layer that loads and excutes elf64 bimaries and translates calls made by Linux applications into windows system calls, so you're not actually running a Linux kernel, just Linux applications. An overview of the WSL-architecture can be found on the [blog at Microsoft]("https://blogs.msdn.microsoft.com/wsl/2016/04/22/windows-subsystem-for-linux-overview/").

Holger

---

