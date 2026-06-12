---
title: "why wont my mouse work?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by sentinelx on 2008-06-11
i have no mouse movement with any of my mice, i have two compaq ps/2, one asus and one microsft both infared and both usb. i have restarted with each new mouse installed and none will work. yet i know they function in xp.

---

### Post by pedro_orange on 2008-06-11
What does your /etc/X11/xorg.conf say regarding InputDevices?

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by sentinelx on 2008-06-11
where do i type that code to display the information?

---

### Post by Crafty Kisses on 2008-06-11
> **sentinelx said:**
> where do i type that code to display the information?

The Terminal, also post the output of:
```
lspci
```

---

### Post by sentinelx on 2008-06-11
Section "Input Device"
identifier   "generic keyboard"
driver       "kbd"
option       "xkbRules"    "xorg"
option       "xkbmodel"    "pc105"
option       "xkblayout"   "us"
end section

Section "Input Device"
Identifier   "configured mouse"
driver       "mouse"
option       "corepointer"
end section

---

### Post by iaculallad on 2008-06-11
> **sentinelx said:**
> 
Section "Input Device"
Identifier   "configured mouse"
driver       "mouse"
option       "corepointer"
end section

Open you /etc/X11/xorg.conf file for editing:

```
sudo gedit /etc/X11/xorg.conf
```

Try inserting the lines of text below to your "Configured Mouse" identifier under "Input Device" section.

```
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"

```

Final Output should be like this:

```
Section "Input Device"
        Identifier   "configured mouse"
        driver       "mouse"
        option       "corepointer"
        Option       "Device"                "/dev/input/mice"
        Option       "Protocol"              "ImPS/2"
        Option       "ZAxisMapping"          "4 5"
        Option       "Emulate3Buttons"       "true"
end section

```

Save and Close your file: Press Ctrl+Alt+Backspace.

---

### Post by sentinelx on 2008-06-11
00:00.0 Host bridge: Intel Corporation 82815 815 chipset Host Bridge and memory controller hub (rev 02)
00:01.0 pci bridge: intel corp 82801 815 chipset agp bridge {rev 02)
00:1e.0 pci bridge: intel corp 82801ba isa bridge (lpc) (rev 02)
00:1f.1 ide interface: intel corp 82801ba ide u100 controller (rev 02)
00:1f.2 usb contoller: intel corpoation 82801ba/bam usb controller #1 (rev 02)
00:1f.4 usb contoller: intel corpoation 82801ba/bam usb controller #1 (rev 02)
00:1f.5 multimedia audio controller: intel corp 82801ba/bam ac'97 audio controller (rev02)
01:00.0 vga compatible controller: nvidia corp nv11ddr [geforce2 mx200] (rev b2)
02:00.0 ethernet controller: accton technology corp smc2-1211tx (rev 10)

---

### Post by sentinelx on 2008-06-11
i have entered those extra pieces in the xorg.conf file but apparently i dont have permissions to save the file. this is a new installation and its becoming a headache

---

### Post by wormser on 2008-06-11
> **sentinelx said:**
> i have entered those extra pieces in the xorg.conf file but apparently i dont have permissions to save the file. this is a new installation and its becoming a headache

Gksudo and sudo give you admin rights.  Gksudo is for graphical apps.  Try the following command and use your password.

```
gksudo gedit /etc/X11/xorg.conf
```

---

