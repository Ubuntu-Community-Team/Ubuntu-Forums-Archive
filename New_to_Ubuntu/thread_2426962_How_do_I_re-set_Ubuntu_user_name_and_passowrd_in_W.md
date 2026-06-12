---
title: "How do I re-set Ubuntu user name and passowrd in Windows 10?"
date: 2019-09-16
forum: New to Ubuntu
---

### Post by tangara on 2019-09-16
I have an icon of Ubuntu in my desktop whereby when I clicked on it it will let me use Ubuntu.

And it will say Ubutu-desktop

So, today I learnt that I need a software in which if I were to use Windows to install it would be HELL.

No choice I have to use Ubuntu.

But, I forgot my username and password.

Please let me know how to cos when I followed the stackoverflow's it doens't work..cos it still asks me for my password

[https://askubuntu.com/questions/931940/unable-to-change-the-root-password-in-windows-10-wsl](https://askubuntu.com/questions/931940/unable-to-change-the-root-password-in-windows-10-wsl)

---

### Post by Impavidus on 2019-09-16
What kind of system is this? Clicking an Ubuntu icon on a desktop is not the normal way of starting a full Ubuntu system.

---

### Post by cruzer001 on 2019-09-16
I think

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

---

### Post by Holger_Gehrke on 2019-09-16
If I understand your post correctly then you're using the Windows Subsystem for Linux with an Ubuntu userland - basically a translation layer that makes it possible to use programs written for Linux on windows similar to what wine does for windows programs on Linux. The probability of anybody on this forum knowing much about this is very low. It's mainly meant for people who want (or need) a Linux command line environment on Windows. Support for graphical Linux applications is ... problematic ... at best since you need to run an x-Server on windows and make your Linux programs use that. Most users here use Ubuntu as their operating system "on bare metal" or inside a VM. The explanation of Linux user accounts in WSL linked from the post on askubuntu is as close to an answer as you're likely to get.

Holger

---

### Post by tangara on 2019-09-16
Yes.  I feel more tired than using Windows 10 which is also a tiring thing with problem opening up the app I want etc.
I think I better go get my laptop service guy to help me out on this since I really need Linux now to install a software which cannot be done via Windows...

---

### Post by yancek on 2019-09-17
I'm not familiar with "the Windows Subsystem for Linux" so can't speak to that but if you need a Linux system for some specific software you use, installing VitualBox or other virtualization software in windows and then Ubuntu/Linux in VirtualBox would probably work a lot better.  Many tutorials on doing this online.

---

### Post by uRock on 2019-09-17
> **tangara said:**
> Yes.  I feel more tired than using Windows 10 which is also a tiring thing with problem opening up the app I want etc.
I think I better go get my laptop service guy to help me out on this since I really need Linux now to install a software which cannot be done via Windows...

Have your tried this? [https://winaero.com/blog/reset-password-wsl-linux-distro-windows-10/](https://winaero.com/blog/reset-password-wsl-linux-distro-windows-10/)

---

