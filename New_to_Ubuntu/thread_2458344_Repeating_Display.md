---
title: "Repeating Display"
date: 2021-02-22
forum: New to Ubuntu
---

### Post by g4rve on 2021-02-22
Complete Ubuntu/Linux newb.

I've installed Ubuntu on a fairly elderly Samsung all-in-one PC. It's a great machine which can't handle Windows any more but doesn't deserve to be thrown out.

The installation seems to have gone fine except that the display/desktop repeats 3 times vertically and about 1.5 times horizontally. 

[ATTACH=CONFIG]287995[/ATTACH]

It's difficult to read what's on the screen but I've managed to go to the Display Settings and there's only one resolution setting - 1280 x 720.

I've found it almost impossible to find a good search phrase which might provide me with some help which is why I've posted here. Can anyone suggest what I should do next?

cheers

Garve

---

### Post by Autodave on 2021-02-22
Can you give us the model # of the computer?  And what version of 'buntu are you trying to install?

---

### Post by grahammechanical on 2021-02-22
When you installed Ubuntu did you tick the box Install third party software? If you did then you will be using a proprietary video driver. What video card do you have in that machine. How much of its own video memory does it have.

Do you get a Grub boot menu? If so, then select Advanced Options for Ubuntu. and then select a Linux kernel with recovery mode. At the recovery menu select Resume. That should load to the login screen using a low video resolution open source driver. That should get you to a desktop. Now, open Software & Updates>Additional Drivers tab. And either de-activate the proprietary video driver if it is installed. Or, tick to install it if it is not installed. Then reboot. What is the result now?

It may be that that elderly machine does not have the CPU, Memory & video card that can run Ubuntu. You may need to install a flavour of Ubuntu that is less demanding of system resources. Such as Lubuntu or Xubuntu.

Regards

---

### Post by chrischang2021 on 2021-02-22
Dear g4rve:

Do you inspect your display mode match you software setting sometime that just not match.
I have a test way maybe that not helpful, 


-choice others resolution mode 
-fixed a software resolution mode and selection other setting at your display.
-If both are not working well. try to other USB boot driver of version of Ubuntu, testing compatible.

---

### Post by g4rve on 2021-02-23
I believe I did tick that box but don't know for certain. Each of my tiny repeating desktops are difficult to use/read but not impossible. When I go to Software & Updates > Additonal Drivers it tells me "No Additional Drivers Available" and "No Proprietary Drivers Are In Use".

I'd be surprised if it isn't powerful enough to run Ubuntu. It does run Windows 10, just really slowly.

> **grahammechanical said:**
> When you installed Ubuntu did you tick the box Install third party software? If you did then you will be using a proprietary video driver. What video card do you have in that machine. How much of its own video memory does it have.

Do you get a Grub boot menu? If so, then select Advanced Options for Ubuntu. and then select a Linux kernel with recovery mode. At the recovery menu select Resume. That should load to the login screen using a low video resolution open source driver. That should get you to a desktop. Now, open Software & Updates>Additional Drivers tab. And either de-activate the proprietary video driver if it is installed. Or, tick to install it if it is not installed. Then reboot. What is the result now?

It may be that that elderly machine does not have the CPU, Memory & video card that can run Ubuntu. You may need to install a flavour of Ubuntu that is less demanding of system resources. Such as Lubuntu or Xubuntu.

Regards

---

### Post by g4rve on 2021-02-23
A Samsung all-in-one PC about 8 years old. No obvious model no. Downloaded the latest stable version yesterday.

> **Autodave said:**
> Can you give us the model # of the computer?  And what version of 'buntu are you trying to install?

---

### Post by g4rve on 2021-02-23
When I try to change resolution it only gives me one option, 1280 x 720.

> **chrischang2021 said:**
> Dear g4rve:

Do you inspect your display mode match you software setting sometime that just not match.
I have a test way maybe that not helpful, 


-choice others resolution mode 
-fixed a software resolution mode and selection other setting at your display.
-If both are not working well. try to other USB boot driver of version of Ubuntu, testing compatible.

---

### Post by Autodave on 2021-02-23
Latest stable version?  20.10?  You really need to d-l 20.04 and try that.  That is an LTS (long term service) release.  Anything newer than that may or may not be stable.  Consider 20.10 a beta release.

---

### Post by g4rve on 2021-02-23
Sorry, I should have been clearer. It was 20.04.

> **Autodave said:**
> Latest stable version?  20.10?  You really need to d-l 20.04 and try that.  That is an LTS (long term service) release.  Anything newer than that may or may not be stable.  Consider 20.10 a beta release.

---

### Post by Impavidus on 2021-02-23
Some details on the graphics hardware may help. This command can give some details:```
inxi --graphics
```If inxi isn't installed, first install it using```
sudo apt update
sudo apt install inxi
```Alternatively, use any graphical package manager you like. They are all front-ends to the same package management system.

Also, what type of connection do you use between computer and monitor?

---

### Post by g4rve on 2021-02-23
Graphics:
  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics 
  driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.9 driver: i915 resolution: 1280x720~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 2500 (IVB GT1) 
  v: 4.2 Mesa 20.2.6

It's an all-in-one PC unit - no separate monitor.

> **Impavidus said:**
> Some details on the graphics hardware may help. This command can give some details:```
inxi --graphics
```If inxi isn't installed, first install it using```
sudo apt update
sudo apt install inxi
```Alternatively, use any graphical package manager you like. They are all front-ends to the same package management system.

Also, what type of connection do you use between computer and monitor?

---

### Post by Autodave on 2021-02-24
What happens when you boot the machine to the installation medium?  Do you still get that funny screen?  

I have never seen or heard of that problem before.  I would try booting to the install medium.  If the screen looks OK there, then try re-installation.

---

### Post by mIk3_08 on 2021-02-24
I haven't experience this kind of display but this is very weird though. 
Thanks for sharing this difficulty.  
There are a lot here in this community that is very willing to help.
Just be patience. I'll be following this thread because this is very unique to me and if I encounter this I know what to do if someone can help you here in this community.

---

