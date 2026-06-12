---
title: "trouble installing ubuntu to a thumb drive to boot on both Mac and PC hardware"
date: 2020-10-29
forum: New to Ubuntu
---

### Post by nivina on 2020-10-29
I'm not new to *nix, however, I believe I'm a little over my head. After digging around a bit, I am unable to figure out what I need to do in order to achieve my goal.

**Goal**
I have a strong need to be able to run Ubunutu 20.04 from a thumb drive, on both a desktop PC ("PC"), which is running Windows 10, and a 2012 MacBook Air ("Laptop"), which is running Mac OS 10.15.x. To be explicit, I want to be able to unplug my thumb drive from one, plug it into the other, and be good to go.
[I]
[SIZE=1]Why? Because I live in an area that requires me evacuate from time to time, and grabbing a thumb drive is way better than grabbing a desktop PC. Also, I have satellite internet and would like to be able to take my system into the "office" to download and install software to my Ubuntu system.[/SIZE][/I]

**Story Thus Far**
I have a thumb drive with the Unbuntu 20.04 installer on it, which I'll refer to as "Installer". I have a second thumb drive to install to, which I'll refer to as "System".

[I][SIZE=1]When I talk about installing Ubuntu, I'm using the standard installer, with standard options. That is to say that I am picking the System as my target, and telling the installer to reformat and install to it. No "advanced" options used during this process.[/SIZE]
[/I]
Both of the following are true:[INDENT]
I can boot my PC into Ubuntu using Installer. I can install Ubuntu to System. I can then reboot and run Ubuntu off of System when connected to PC. However, when I plug System into my Laptop, it doesn't boot. It doesn't seem to even know that there is a system on it. *I am holding option to get the boot menu. I can still boot into Mac OS just fine.*

I can boot my Laptop into Ubuntu using Installer. I can install Ubuntu to System. I can then reboot and run Ubuntu off of System when connected to Laptop. However, when I plug System into my PC, it doesn't boot. UEFI Bios shows that it is a valid boot partition, but it skips over it and goes straight to Windows. *I never get to grub.*[/INDENT]

**Problem**
As you can see, I can clearly run an Ubuntu install from a thumb drive on both of my machines; however I can only run Ubuntu on the machine in which I used to install Ubuntu. And this is the crux of the problem, at least to the extent of my understanding.

I know that there are paths I can go down to possibly solve this problem. Before stumbling in the dark I would love to know if someone has accomplished this and has a good guide or, at the very least, some helpful pointers. I have found a lot of older information in these forums that may apply, but I'm weary of information that is 10 years old.

[I]If the solution is "just throw away that MacBook Air and get yourself a laptop that isn't garbage aka. Apple", that's something I'm already planning on doing; however, as of writing this I do not have a replacement laptop yet. I also value understanding how to accomplish this, as you never know what situation you might be in when your system fits in the small front pocket of your jeans.
[/I][SIZE=2]
I apologize for the long post. I appreciate any help. Thanks in advance to whomever is going to place this into the correct sub-forum.[/SIZE]

---

### Post by tea for one on 2020-10-29
> **nivina said:**
> 
I can boot my PC into Ubuntu using Installer. I can install Ubuntu to System. I can then reboot and run Ubuntu off of System when connected to PC. However, when I plug System into my Laptop, it doesn't boot. It doesn't seem to even know that there is a system on it. *I am holding option to get the boot menu. I can still boot into Mac OS just fine.*

I can boot my Laptop into Ubuntu using Installer. I can install Ubuntu to System. I can then reboot and run Ubuntu off of System when connected to Laptop. However, when I plug System into my PC, it doesn't boot. UEFI Bios shows that it is a valid boot partition, but it skips over it and goes straight to Windows. *I never get to grub.*[/INDENT]

From your description, it looks like you have **fully installed Ubuntu** to a USB thumb drive.

By **fully installed**, I take it that you have created a user name and password.

As you can boot both your PC and MacBook Air via the Ubuntu live session, you could consider using Ubuntu in a live session with [COLOR="#0000FF"]persistence[/COLOR].

Here is some info:-

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by nivina on 2020-10-29
> **tea for one said:**
> From your description, it looks like you have **fully installed Ubuntu** to a USB thumb drive.

By **fully installed**, I take it that you have created a user name and password.

As you can boot both your PC and MacBook Air via the Ubuntu live session, you could consider using Ubuntu in a live session with [COLOR=#0000FF]persistence[/COLOR].

Here is some info:-

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

You are correct, I have a fully installed Ubuntu system with a user name and password. That is what I was trying to convey when I said that I was able to use my Ubuntu Installer on each of the computers to install to my System drive. The Installer is running Ubuntu live (I was unaware of the "live" terminology until now, ty!), and I installed Ubuntu from a live session.

I will take a closer look at those links this afternoon; they seem good at first glance. Thank you, I appreciate it.

---

### Post by tea for one on 2020-10-29
When you **fully install** Ubuntu to a drive, the installer runs a process to configure hardware.

I reckon that the hardware configuration for your Windows PC then prevents booting on your MacBook Air **and** vice-versa.

A usb device with a [COLOR="#0000FF"]persistent[/COLOR] live system will not go through the hardware configuration procedure.

Good luck - fingers crossed.

By the way, if the persistent method is not satisfactory, you could make two **full installations**, one for each machine.

Quite easy to grab two thumb drives in case of emergency evacuation.

---

### Post by sudodus on 2020-10-29
1. If a persistent live system (according to @ *tea for one*) works well for you, fine :-)


2. Otherwise you can try an installed system according to the following method. (It is possible that your problem is that one of the computers boots in BIOS mode (alias CSM alias legacy mode) and the other computer in UEFI mode, and you need an installed system, that boots both in BIOS mode and UEFI mode.)

I made a compressed image file from an installed system of Ubuntu 20.04 LTS. This system can boot both in UEFI mode and BIOS mode. You can download it (and check with md5sum) and then use mkusb to extract and flash it to the USB drive (with size at least 16 GB) in one operation.

See the following links,

[If you need not encrypt the drive, there is an easy alternative](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203)

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by tea for one on 2020-10-29
> **sudodus said:**
> 
2. Otherwise you can try an installed system according to the following method. (It is possible that your problem is that one of the computers boots in BIOS mode (alias CSM alias legacy mode) and the other computer in UEFI mode, and you need an installed system, that boots both in BIOS mode and UEFI mode.)

Yes, very good point - I am familiar with the UEFI/Legacy BIOS conundrum and I should have mentioned it in my reply.
Apologies to the OP.

---

### Post by kurt18947 on 2020-10-29
> **tea for one said:**
> When you **fully install** Ubuntu to a drive, the installer runs a process to configure hardware.

I reckon that the hardware configuration for your Windows PC then prevents booting on your MacBook Air **and** vice-versa.

A usb device with a [COLOR=#0000FF]persistent[/COLOR] live system will not go through the hardware configuration procedure.

Good luck - fingers crossed.

By the way, if the persistent method is not satisfactory, you could make two **full installations**, one for each machine.

Quite easy to grab two thumb drives in case of emergency evacuation.

Two full installations might be the most stable and reliable. Maybe have a 3rd USB for data or sync the data folders between drives? I've been finding out about minor system differences causing problems. I replaced an AM4/Ryzen MoBo with a B350 chipset with a MoBo with a B450 chipset. Same processor, same video card. Very little difference, right? Well, it looks like there's enough difference to cause intermittent hard lockups. I would imagine there's more differences between PC based hardware and Mac hardware, Intel based or not. I just finished a fresh install on the newer MoBo a few days ago so it's premature to declare that the difference between working and not is the chipset but it sorta looks like that.

---

