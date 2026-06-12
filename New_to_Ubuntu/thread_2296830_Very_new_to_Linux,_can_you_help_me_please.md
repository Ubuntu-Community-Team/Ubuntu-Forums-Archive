---
title: "Very new to Linux, can you help me please???"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by david_richards2 on 2015-09-29
I am sorry if this is covered somewhere else, but I am a complete newbie to Linux.

I have an older PC running 2Gb RAM and Windows XP, and would like to join the world of Linux as I am fed up with my Windows installation running like a snail towing an anvil!!

I would be really grateful if someone can give me some basic advice about installing on my current system.
I have one hard drive partitioned in 2 - one with XP and files etc and the second one empty (I guess I can use this for Linux?)
CPU
            Intel Celeron
            Northwood 0.13um Technology
        RAM
            2.00GB DDR @ 168MHz (2.5-4-4-7)
        Motherboard
            Gigabyte Technology Co., Ltd. GA-8S648-RZ (Socket 478)    16 °C
        Graphics
            W1943 (1280x720@60Hz)
            32MB NVIDIA GeForce2 MX/MX 400 (MSI)
I want to keep XP, so have a dual boot-PC
I will have to install via a USB as my cd-writer has died!

I would just like to see if someone can suggest the best version of Linux to use and give me a step by step guide for installing with the ability to dual boot and NOT lose any of my existing applications and files.

I really hope someone can help me and sorry if this is a **_REALLY_** simple post, but I am nervous of doing the install without some guidance first!

Many thanks in advance for any help and assistance you can offer!

David

---

### Post by mörgæs on 2015-09-29
Hi, welcome to the fora. 
Next time please use a more precise and specific thread title (or even better, edit the post).

There is some advice for old hardware in the link in my signature. Pay special attention to what is written about the Geforce 2 graphics card.

---

### Post by Skaperen on 2015-09-29
do you have any USB flash drive sticks of size 2GB or larger?  can your computer boot from USB (flash drive or CD drive)?

---

### Post by buzzingrobot on 2015-09-29
Hi, I won't offer any specific advise, just a couple of general points about things you should know:

1. By today's standards, you have pretty low-powered hardware. Someone else will likely come along with more detailed advice, but I doubt your hardware can successfully run today's Ubuntu or any other comparable Linux distribution.  You should look at Linux distributions that are built to run on low-powered hardware,  In the Ubuntu family, there is Lubuntu ([http://lubuntu.net/](http://lubuntu.net/)). You will need to know the size of the empty partition available for Linux. You can post that here and someone will tell you if it is large enough.

2. Can your machine can boot from a USB stick? (check your BIOS settings; typically, there's a specific keystroke to tap as the system boots that will trigger the BIOS to prompt you to select the drive to boot from.  You can select the USB. It's a one-time thing; normal booting happens otherwise.)

3.  You need to acquire and "burn" an install image for Ubuntu (or any other distribution) to the USB stick. Check the instructions linked to toward the bottom of this page: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop). (These Ubuntu instructions apply to any installation image.)

4. When you boot into an Ubuntu installation image, you will be offered a choice to try it out in "Live" mode.  This means it runs entirely off the USB and does not touch your existing hard drive.  Doing this is a very good way to see if your limited hardware can handle it and if all your components are compatible.

5. Dual Booting:  Every PC has a reserved and specific physical location on the hard drive that contains the data used to boot the default operating system. One of the common problems people have with setting up dual booting is that they accidentally overwrite or damage this area.  The machine may not boot, or it may boot into Linux but display no option to boot into Windows.  This is the result of misconfiguration and should not happen.  Be sure to read and understand the guidance offered by Ubuntu about setting up dual booting.

6. The safest way to proceed is to copy all the files and data from your Windows system that you want to be sure to preserve to another location, just in case.  That way, if something does go wrong, it can be restored.

7. With that in mind, are you able to do a clean install of XP, if necessary?

---

### Post by mastablasta on 2015-09-29
i will just add that it is good to do a full disk backup with clonezilla or redo backup if you have some external disk available or similar.

I do not know the CPU or GPU in your case. if Lubuntu doesn't boot you maybe have non-PAE cpu. I lhink LXLE distribution supports those.

if GPU has descent support then Lubuntu or Xubuntu are ok otherwise not so much. I have an old 16MB ATI rage card. while you can't really use it for gaming the card has descent support and works well for some desktop use. 

in Linux you can install desktop separately from kernel and OS. so we have a bit more resource heavy desktops that need good acceleration (i.e. new hardware is ok with them but old one not so much) for various special effects, features, funcitons... and then there are more Spartan desktops that use only 2D acceleration (like LXDE or XFCE found in the mentioned *buntus). there are also various windows managers which are even lighter in their resource usage. check for example distributions such as AntiX, ToriOS or Bodhi Linux. they need very little ram and have very low hardware requirements. 

if this is a desktop perhaps you could get a stronger used GPU card. it would help a lot in your experience. I guess it would be similar in winXP. btw I still run XP as well. but I am good in the speed department.

---

### Post by stalkingwolf on 2015-09-29
before installing i would suggest trying a couple distros.   I have several with about the same specs running mint mate.    there is also xubuntu, kubuntu.  then go with the one you like

---

### Post by Geoffrey_Arndt on 2015-09-29
All great advice above . . . a thread worth saving for newbie guidance.   Also, although my #1, 2, 3 PC's all run Ubuntu Unity, I have a "Linux Dual-Boot" with a couple of my units running either Xubuntu OR Ubuntu Mate.

 If running Ubuntu Mate, the install is more likely to avoid the infamous "Linux BSOD" (Black Screen of Despair). #-o

---

