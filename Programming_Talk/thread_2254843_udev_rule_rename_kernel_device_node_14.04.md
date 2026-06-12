---
title: "udev rule rename kernel device node 14.04"
date: 2014-11-30
forum: Programming Talk
---

### Post by straydawg on 2014-11-30
I had a udev rule and c pgm to rename..the alsa_name would take input and rename 


[COLOR=#333333][FONT=Menlo]KERNEL=="pcmC[D0-9cp]*", DRIVERS=="usb", PROGRAM="/usr/bin/alsa_name %k %b", NAME="snd/%c{1}"[/FONT][/COLOR][COLOR=#333333][FONT=Menlo]
[/FONT][/COLOR]    //Arg1 is the kernel device name (i.e. "controlC0" or "pcmC0D0p")
    //Arg2 is the KERNELS name, for usb this is the port name (i.e. "3-2" or "1-1.2")

syslog: [COLOR=#333333][FONT=Menlo]NAME="snd/%c{1}" ignored, kernel device nodes can not be renamed; please fix it in /etc/udev/rules.d/39-usb-alsa.rules:4

[/FONT][/COLOR]This limitation new in 14.04 ? Any way to do this ?

Thanks

---

