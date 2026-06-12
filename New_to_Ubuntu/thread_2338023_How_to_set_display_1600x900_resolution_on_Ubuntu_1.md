---
title: "How to set display 1600x900 resolution on Ubuntu 16.04LTS ?"
date: 2016-09-23
forum: New to Ubuntu
---

### Post by dkm171 on 2016-09-23
Dear friends and admins 


I am facing display resolution in my pc, my pc display current setting 1024x768, but my led monitor supports 1600x900.

already i am using 1600x900 at windows, its working perfectly

---

### Post by CantankRus on 2016-09-23
Problem usually related to graphics drivers.
Install inxi (sysinfo script) to show some gfx info about your system.
In a terminal run...
```
sudo apt install inxi
```

After installation run the command...
```
inxi -Gx
```

and post your terminal output.
eg 
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] inxi -Gx**
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 370.28 Direct Rendering: Yes
```

When replying, paste in your terminal output, highlight with left mouse and then hit the # button to enclose in [noparse]```
 
``` [/noparse] tags.

---

### Post by DuckHook on 2016-09-23
In addition to what CantankRus asks for, please also post results of:```
xrandr
``````
sudo apt install read-edid && sudo get-edid | parse-edid
``````
cat /etc/default/grub
``````
ls -laF /etc/modprobe.d | grep blacklist
``````
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by DuckHook on 2016-09-23
Please also provide answers to the following questions:

[LIST=1]
[*]What monitor are you connecting to (Brand, Make, Model)?
[*]What connection type (HDMI, DP, DVI, VGA)?
[*]Are you using a KVM switch?
[*]How long are your video cables?
[/LIST]

---

### Post by dkm171 on 2016-09-24
> **DuckHook said:**
> Please also provide answers to the following questions:

[LIST=1]
[*]What monitor are you connecting to (Brand, Make, Model)?
[*]What connection type (HDMI, DP, DVI, VGA)?
[*]Are you using a KVM switch?
[*]How long are your video cables?
[/LIST]


Dear

1. DELL LED Monitor 20" Inches

2. VGA

3. I don't know, what KVM ?

4. 6 months

Dell monitor correctly working on windows with 1600x900 resolution.

```
 

Graphics:  Card: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.00hz
           GLX Renderer: Mesa DRI Intel Ivybridge Desktop
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes


```

---

### Post by DuckHook on 2016-09-24
[COLOR="#FF0000"]K[/COLOR]eyboard
[COLOR="#FF0000"]V[/COLOR]ideo
[COLOR="#FF0000"]M[/COLOR]ouse
&#8230;switch

If you don't know what it is, then you aren't connected to one. KVM switches are notorious for blocking the *edid* data from the monitor that a video card needs to correctly determine resolution. I was also referring to physical length of your cables; not how old they are. The intent is to determine quality of signal. Please post the results of the commands that I asked for earlier.

---

