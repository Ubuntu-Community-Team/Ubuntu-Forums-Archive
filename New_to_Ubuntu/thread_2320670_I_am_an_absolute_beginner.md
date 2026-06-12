---
title: "I am an absolute beginner"
date: 2016-04-16
forum: New to Ubuntu
---

### Post by Christopher_Hunt on 2016-04-16
Hello.
I am an absolute beginner when it comes to Linux so please excuse the dumb questions. I have just installed Linux alongside Windows 10 and after the first re-boot it asked me which OS I wanted to boot so I selected Windows. Every time I reboot now it defaults to Windows, I read up that I would have to select each time I boot as to what OS I wanted to use. Please tell me how to switch between the two...

Thank you.

Chris

---

### Post by RobGoss on 2016-04-16
Hello and welcome to the forum, Do you see the Grub menu when you start up your machine? if installed correctly you should and it should give you the option to choose which operating system you want to boot up. I'm not sure what the specs are for your machine it would help others help you better by providing your specs.

Here is a help page for UEFI on most if not all new machines.

UEFI Introduction
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Christopher_Hunt on 2016-04-16
Hi Rob thank you for your reply. I don't see the grub menu when I boot! When I first rebooted after installing it, it asked me which OS to load. I chose Windows thinking I could chose Linux the next time I booted.

---

### Post by grahammechanical on 2016-04-16
Did you read that wiki page on UEFI that RobGoss linked to? What version of Ubuntu did you install? And how did you install it? Did you, by any chance, install Ubuntu inside Windows by installing something called wubi.exe? We are not clear on what menu you saw. We are having to guess the situation from several possible situations.

I do not have a motherboard with a UEFI boot system. I do not have Windows 10 installed. I have no idea of what you are seeing. I do know from reading that wiki page that when installing Ubuntu to dual boot with Windows 8 & upwards we need to load the Ubuntu live session in EFI mode because Windows 10 will be installed in EFI mode. If we install Ubuntu in BIOS/Legacy/CSM mode then we lose the option to get a menu that lets us choose which OS to load. We have to enter the UEFI settings utility each time to change the boot mode from EFI to Legacy and back again each time we want to load one or the other OS.

You are not providing enough information for us to know the situation.

Regards

---

### Post by Bucky Ball on 2016-04-16
When the machine boots, after the manufacturer splash screen, hit shift a few times (used to be escape). That should (and in your case may) bring up a menu where you can select OS.

---

