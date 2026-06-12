---
title: "No Graphic login after Nvidia install"
date: 2017-08-09
forum: New to Ubuntu
---

### Post by michel.mds1983 on 2017-08-09
Hi all!

    After trying to setup my Nvidia graphic drivers, I rebooted the notebook and got a wrong resolution in the graphic area dueing the loggin and despites I type correct name and password it come back to the same screen. When I hit ctrl+alt+F1 and go to terminal mode, the loggin works. There I got to remove the drivers update, restarted the pc and boom, everything works fine, except that I need the graphic card.

     Can anyone suggest me a direction to setup it correctly? I know that I have set the correct version.

regards!
Michel

---

### Post by Bashing-om on 2017-08-09
michel.mds1983; Hello;

Think about it please - how are we to know what driver is suitable if you do not tell us the hardware ?
How did you install the nvidia driver ?
How did you remove the nvidia driver ?

Post back the output of terminal commands:
```

lspci -nnk | grep -iA3 vga
dpkg -l | grep -i nvidia*

```

see what can be done.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by michel.mds1983 on 2017-08-10
It is a GTX1070, I just got the newest driver version I got on **System > Software & Updates > Additional Drivers**

---

### Post by ajgreeny on 2017-08-10
Which version of Ubuntu are you using as that very recent graphic card may work better in the most recent version, 17.04.

I have never had an nvidia card so can not help further with this, but you seem to have installed the driver in the best possible way for nvidia cards.

---

### Post by michel.mds1983 on 2017-08-10
I had the 17.04 installed and got the problem, so I decided to install the 16.04 and got the same.

---

### Post by #&amp;thj^% on 2017-08-10
> **michel.mds1983 said:**
> I had the 17.04 installed and got the problem, so I decided to install the 16.04 and got the same.

Could you provide us the output back from the terminal:
```
inxi -G
```
Mine shows:
```
inxi -G
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: x11 (X.Org 1.19.3) driver: nvidia
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2
           version: 4.5.0 NVIDIA 384.59

```
You may have to install inxi first:
```
sudo apt install inxi
```
I have used the drivers for a Long time (10 years) with various PPA's with no issues.
Also you mention Installing the OS a couple of times now and may have some left over .conf's files left behind in "/etc/X11"

---

