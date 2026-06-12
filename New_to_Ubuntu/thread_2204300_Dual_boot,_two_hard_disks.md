---
title: "Dual boot, two hard disks"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by Bugscuffle on 2014-02-07
Here is what I have: a new to me computer, a Dell Vostro 220 running Wimdows 7 (32 bit) and with a second H.D. that has something on it, but I can cure that. I have the CD's to format the disk.

Here is what I want: to put ubuntu on the second disk and be able to boot the machine from either disc upon turn on.

Here is what I need: take me by the hand and tell me exactly when and where and what to type into the machine to accomplish this. I am an old guy, a very old guy that is not computer litterate. I need step by step directions in plain language. No, I mean PLAIN language, not the geek language that you smart people use.

Thank you in advance.
The old guy

---

### Post by Vladlenin5000 on 2014-02-07
Have you ever installed Ubuntu?

---

### Post by Bugscuffle on 2014-02-07
No. I tried to once, but had too much trouble and gave up on it. I want to try again.

---

### Post by MartyBuntu on 2014-02-07
Before you do anything, make sure you backup the Windows drive.

The installation disk is pretty straightforward. When it asks which drive you want to use, choose "use entire disk" and select the second drive.
The boot loader will be installed to the same drive that Windows is installed on. No worries...GRUB will handle booting Windows and Ubuntu for you in any configuration you desire.

---

### Post by G_Ajith_Kumar on 2014-02-07
Hello.

 Here is a link to the installation guide for Ubuntu 12.04 the latest Stable version of Ubuntu. [https://help.ubuntu.com/12.04/installation-guide/i386/index.html](https://help.ubuntu.com/12.04/installation-guide/i386/index.html).
You may like to familarise yourself with the procedures.

                      1.  Back up any existing data or documents from your hard disk where you plan to install Ubuntu.  

2. Download the latest Ubuntu 12.04 files from [http://releases.ubuntu.com/precise/ubuntu-12.04.4-desktop-i386.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.4-desktop-i386.iso)

3. Make a DVD of it.

4. Place the DVD in your DVD Drive and reboot.

5. During reboot, enter BIOS and enable booting from CR Rom as the first option.

6. Save and reboot.

7. The Ubuntu installer will walk you through the rest of the booting process. If there is an option asked and if you are unsure, selecting the defualt would be the optimal option .



Good Luck

---

### Post by Bugscuffle on 2014-02-07
I only think that I understand all of that. I took the HD that O want to use for the ubuntu and wiped it clean usong Disc Wiper 2012. When I put ot all back together again the computer doesn't see the wiped HD. I guess that makes sense, but then again I told you that I'm not computer literate. Before I wiped it the computer saw the HD just fine, but I didn't want to have anything on it other than the ubuntu, especially something that I didn't know what it was. So what do I do to get the computer to see this HD so that I can download the ubuntu to it?

---

### Post by Bucky Ball on 2014-02-07
Boot from the Ubuntu installation disk, Try Ubuntu, once at a desktop launch an application called 'Gparted'. That will see everything in the box re. hard drives. 

PS: You could have also repartitioned/wiped the drive using Gparted. Before you install, you can set up partitions with it so when you get to the partitioning section of the install there is no confusion; you know exactly where to install.

So, you might not think you're up to speed with the software side of things, but if you're ever played with the hardware you can always disconnect the Win drive while all this is going on.

Bottom line: Boot from the install CD/DVD/USB, get to a desktop via 'Try Ubuntu', have a look for the 'missing' drive, and we'll go from there.

---

### Post by stinkeye on 2014-02-07
Your best method would be to follow guides and post questions if you don't understand something.

Your first step would be to download the 12.04 LTS iso....
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Then create a bootable USB stick on Windows.
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

...and then try Ubuntu before installing...
[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

When you get this far I, or others can guide you through installing in a dual boot situation.

---

### Post by sudodus on 2014-02-08
If you disconnect the drive with Windows while you install Ubuntu, you will reduce the risk of damaging Windows. When Ubuntu is installed and works properly, you can re-connect the drive with Windows and make a dual boot system of it.

You should install Ubuntu in the same BIOS or UEFI mode as Windows.

---

