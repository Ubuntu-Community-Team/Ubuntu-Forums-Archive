---
title: "Cant dual boot Ubuntu on lenovo y50-70 W8.1"
date: 2015-04-04
forum: New to Ubuntu
---

### Post by sebastiaan5 on 2015-04-04
Hi,
 
I want to dual boot win8.1/ubuntu but everything i tried wont work, I want to run ubuntu in UEFI mode.
 
I tried the following things:
 
I want to boot Ubuntu from a working DVD so i tried to set the secure boot option off in BIOS.
I've set fast restart off in w8.1.
But nothing works.
 
I have already:
 
A working DVD with ubuntu 14.04
A back up of all my files.
Space for ubuntu on my hard disk.
 
I can manage to boot ubuntu but only if i set my UEFI mode off and set it to legacy mode support with legacy as first priorty of booting. That's ofcourse not what i want because then I can't run w8.1.
Greetz,

I really want Ubuntu, i read a lot about it, it seems very very nice.

---

### Post by yancek on 2015-04-04
Is the Ubuntu iso file you put on the DVD 64bit?  I don't believe a 32bit system will work although there may be way around this.

---

### Post by sebastiaan5 on 2015-04-05
hi,

Thanks for your reply but i assure you, my DVD  is 100% correct, its an iso 64bit 14.04 ubuntu I've tried to boot it from an older PC with no UEFI bios function and it works correctly.

My problem is that my pc doesnt want to boot a DVD in UEFI mode, can anyone help me with that?.


greetz

---

### Post by leunam12 on 2015-04-06
I have the same problem; I have to boot from USB; DVD doesn't work. Try booting from USB, but Before you do that boot windows, press WINDOWSKEY+R and type```
shutdown -s -f -t 00
```and press ENTER. Your computer will shutdown. When the computer is off unplug it, pull the battery off the laptop and press and hold the power button for 45 seconds. Put the battery back on and plug in and try to boot from USB. I assume that you made backup of your entire hard drive already.

---

### Post by oldfred on 2015-04-06
What brand/model system.
Some require a password to allow extra settings.
And many require you to specifically allow USB or any other device to boot.

On my Asus motherboard, I have to turn off Windows and change to Other and change several other settings under CSM menu to have UEFI only. I think with ASUS the Other is setting is really secure boot off.

---

### Post by sebastiaan5 on 2015-04-07
thank you all for the replies, but i fixed it.

So, what I've experienced is that windows on new laptops doesn't want people to boot manually from usb/DVD, you need to ask windows.
What have I done, first plug in your DVD/usb (in windows) and press restart computer while holding shift key down. Now you enter a control panel of windows, the 2nd option on the screen 
is using external hardware DVD/usb, click on it and just select DVD. Your laptop will restart and in my case it will say that there is no DVD (i plugged my DVD as usb in) so boot manager will allow
me to choose the right boot system, I choose for USB. and Ubuntu will start.

Instead of installing ubuntu along windows, you will install ubuntu along windows boot manager.


Hope the will help people :)



greetz

---

### Post by Vladlenin5000 on 2015-04-07
No, not really. What if you had a kit of (factory installed Windows) recovery DVDs? You must be able to boot from DVD...
In most UEFI implementations, if you're quick enough, press repeatedly ESC during or immediately after POST so you can at any time access UEFI settings at boot.

---

