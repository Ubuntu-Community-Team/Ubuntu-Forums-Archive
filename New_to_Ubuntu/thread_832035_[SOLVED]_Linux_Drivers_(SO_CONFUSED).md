---
title: "[SOLVED] Linux Drivers (SO CONFUSED)"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Johnathannn on 2008-06-17
Hi there... So I have absolutely no idea about drivers on Linux... On Windows, I went to my manufacturer's website ([http://support.acer-euro.com/drivers/notebook/as_5000.html](http://support.acer-euro.com/drivers/notebook/as_5000.html)) and I downloaded all of the drivers for my Acer Aspire 5000 Notebook. The drivers I have for Windows XP are:
.802bg
.acerem
.acergrid
.audio
.cpu
.ezdock
.index
.lan
.launchm
.modem
.touchpad
.VGA
I'm wondering if I can somehow install all these drivers on my Ubuntu OS somehow... Is there a way where I can download these drivers for Linux instead of XP... Or some other way? Thanks for anyone's answers... 
Johnathannn

---

### Post by Inxsible on 2008-06-17
Your windows drivers are not going to work under Linux. But most all your hardware should be recognized by Linux without any problems.

In case something isn't, then you might have to take a few additional steps to get it working. Have you already installed Ubuntu on your machine or not?

Are you having problems with any device?

---

### Post by Pjotr123 on 2008-06-17
All drivers are already in the Linux kernel, normally. Linux = plug and play. After installation, do this:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

---

### Post by sdennie on 2008-06-17
Is there a specific reason you need different drivers?  In general, vendors don't support linux in the same way they do XP and all the "drivers" available for Ubuntu are normally already installed.

---

### Post by NullHead on 2008-06-17
You cannot install windows drivers in your Linux operating system. This is because of differences with the OSs, but not to fear! The whole goal with linux is to provide an "out of the box" experience; drivers and all. As long as your machine is fully functional, then you do not need drivers. Things to check for is, your wireless networking, your graphics, and printers and other things like that. If you notice that everything "seems" to be working, then your computer is probably all setup already and you don't need to do anything to it! 

There is one thing that I would check. Look in the menu system, System>Administration>Hardware Drivers. If there is anything listed there, then there is something that needs to be setup through that particular interface.

---

### Post by phidia on 2008-06-17
A lot of things, hopefully, will work in linux without installing any drivers (your hardware is detected and the drivers load at boot).
Somethings like your internal modem may need linux drivers and you will need to look for and enable those.
That's the great thing about a live cd you can run it and see what works and what doesn't. Once you know what doesn't work, that you need, you can start looking for that. 
> lspci -v typed in a terminal window will provide you with a list of some but not all connected devices.

---

### Post by MasterSander on 2008-06-17
Are there any drivers not working?

---

### Post by Johnathannn on 2008-06-17
Well I'm not quite sure, because I haven't really thuroughly checked yet, but I'm positive the wireless internet doesn't work... I'm not quite sure how to get that configured... I've tried one method by downloading a file, but my connection speed is very slow. How can I get my wirless internet working properly?
Johnathannn

---

### Post by Pjotr123 on 2008-06-17
> **Johnathannn said:**
> Well I'm not quite sure, because I haven't really thuroughly checked yet, but I'm positive the wireless internet doesn't work... I'm not quite sure how to get that configured... I've tried one method by downloading a file, but my connection speed is very slow. How can I get my wirless internet working properly?
Johnathannn

Check this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by MasterSander on 2008-06-17
Could you also tell us the name of your wireless card?

Ndiswrapper doesn't always work.

---

### Post by Johnathannn on 2008-06-17
Well it's biult in, and it's called like AS35-Wireless Lan b+g (Broadcom...Hope that helps!
Johnathannn

---

### Post by MasterSander on 2008-06-17
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

Try this site.

---

### Post by NullHead on 2008-06-17
> **MasterSander said:**
> [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

Try this site.

That it too old for 8.04. The proper way to use the broadcom restricted driver is using the drivers manager that I explained how to use earlier. Plus bcm43xx is depreciated. b43 is the new driver.

---

### Post by stchman on 2008-06-17
> **Johnathannn said:**
> Hi there... So I have absolutely no idea about drivers on Linux... On Windows, I went to my manufacturer's website ([http://support.acer-euro.com/drivers/notebook/as_5000.html](http://support.acer-euro.com/drivers/notebook/as_5000.html)) and I downloaded all of the drivers for my Acer Aspire 5000 Notebook. The drivers I have for Windows XP are:
.802bg
.acerem
.acergrid
.audio
.cpu
.ezdock
.index
.lan
.launchm
.modem
.touchpad
.VGA
I'm wondering if I can somehow install all these drivers on my Ubuntu OS somehow... Is there a way where I can download these drivers for Linux instead of XP... Or some other way? Thanks for anyone's answers... 
Johnathannn

Use the LiveCD.  Chances are that the only hardware you will have to tinker with on your laptop is the wireless.

My laptop worked OOB including webcam, wireless, and media reader.

---

### Post by Johnathannn on 2008-06-17
What do you mean Use the Live CD? Do you just want me to find out what drivers aren't detected or...?
Johnathannn

---

### Post by BlackDragonBE on 2008-06-17
Yep just use the LiveCD, if everything works in there, everything works in a full install as well.
I have an Acer Aspire 5500Z, and everything just worked "out of the box".

Cheers

---

