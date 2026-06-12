---
title: "power outage caused computer issues"
date: 2016-06-18
forum: New to Ubuntu
---

### Post by furioususer on 2016-06-18
I had a power outage in my entire apartment building today and when the power came online again I started to have problems with my computer - I'm unsure if it's hardware or OS (I'm on Ubuntu 14,04 LTS, Intel NUC D34010WYKH). 

** Here are the issues I'm having after the power outage: **

[LIST]
[*]I have an USB-hub connected to my computer and that hub doesn't work anymore. I doubt it's broken since connected devices seem to connect (LED lightens up) for a half second and then shuts down, it just doesn't seem to get any power. I have only one USB-receiver from Logitech connected to it (just like before the power outage) and that receiver doesn't work anymore. So I moved the receiver from the USB-hub to the USB-port on the computer instead and it works. I've tried other USB devices on the hub but it's the same thing. 
[/LIST]
 

[LIST]
[*]the bootup is slow. I have a SSD and it always boots up in a matter of 15 seconds at max, now it takes about 90 seconds. From the moment I boot it up it takes up to 50 seconds to get to the login screen and when I get to the loginscreen it takes up to about 40 seconds before I'm allowed to write my password. But as soon as I type in my password and press enter I'm back in business. It's fast like it's always been. When I start the computer and try to access BIOS it takes up to 50 seconds before I see the setup screen (but as soon as I press the F2 button I enter BIOS fast). 
[/LIST]
 
So the issues can be located to pre-desktop lag and a depowered/powerless USB-hub. I suspect, or rather wish, that these two issues are connected (considering they are both a result of the power outage). Meaning; if I get to the bottom of all this then all will return to normal - meaning; I hope it's just some configuration or OS problem rather than a hardware problem.     

To me it sounds like all these things are connected to power. Like the power output has been cut in half after the power outage or something. But I don't know if that makes sense. I've checked the BIOS but didn't find anything odd (unsure what to look for though). 

I have been meaning to do a memtest, to see if the memory is without  errors, but I got issues with my live CD so I can't try that at the  moment, but does anyone have any ideas what might have happened and what I can  do/try?

---

### Post by gordintoronto on 2016-06-18
Sounds like drive issues.
[https://www.linux.com/answers/does-linux-have-chkdsk-function](https://www.linux.com/answers/does-linux-have-chkdsk-function)

---

### Post by Topsiho on 2016-06-19
Probably you should get better answers from those who experience power outages regularly.
To me it seems that your hardware is affected. I was to suggest to try and run a liveDVD, but I see you already tried that without success.

If your computer was connected to the electricity grid when power was restored, it might have been hit by very high power peaks, before the power settled to the normal voltage.
So probably one or more of the hardware in your computer is not functioning anymore, such as memory, hard disk, graphics card, motherboard.
If you have this possibility, you could check them one by one in another computer.

Best I can think of, wish you success,

Topsiho

---

### Post by poorguy on 2016-06-19
I have found it best to always run any Computer or any Electronic devices as TV / Radios etc through a battery backup as you will always be protected.

---

### Post by RobGoss on 2016-06-19
Using a power strip and surge, will help you in cases like this but using all the machines that I have here in Florida when the weather is really bad I simply unplug everything all my machines from any power to be on the safe side. You might want to get that machine check out

---

