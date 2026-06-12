---
title: "Ubuntu strictly on an external HDD?"
date: 2015-08-06
forum: New to Ubuntu
---

### Post by shield543 on 2015-08-06
I need to use some simulation software which works best on UNIX-type systems. According to Wikipedia, Linux is UNIX-like, since it does not officially conform to the Single Unix Specification (SUS). I decided anyway that I still wanted to try out a Linux OS and I decided to go for Ubuntu, however, I currently have two windows systems (a laptop (8.1) and a desktop (7)) which I need to keep running windows.

I have a spare external plug and play 500GB HDD that connects with USB alone and I was wondering if it is at all possible to install Ubuntu on the external HDD such that whenever I feel like using Ubuntu, I can just boot my laptop from my external HDD. Will this not work? Does anyone see any immediate problems this may cause? I could test it out myself first but I need my laptop to function (on windows) in the next 3 weeks quite badly, so I thought I better ask around about this first.

This is my first time posting so apologies if anything isn't in order,
Thanks,
-Luke

---

### Post by sandyd on 2015-08-06
> **shield543 said:**
> I need to use some simulation software which works best on UNIX-type systems. According to Wikipedia, Linux is UNIX-like, since it does not officially conform to the Single Unix Specification (SUS). I decided anyway that I still wanted to try out a Linux OS and I decided to go for Ubuntu, however, I currently have two windows systems (a laptop (8.1) and a desktop (7)) which I need to keep running windows.

I have a spare external plug and play 500GB HDD that connects with USB alone and I was wondering if it is at all possible to install Ubuntu on the external HDD such that whenever I feel like using Ubuntu, I can just boot my laptop from my external HDD. Will this not work? Does anyone see any immediate problems this may cause? I could test it out myself first but I need my laptop to function (on windows) in the next 3 weeks quite badly, so I thought I better ask around about this first.

This is my first time posting so apologies if anything isn't in order,
Thanks,
-Luke

If your hardware is compatible, it should work fine.

Just make sure that during the installation, select manual partitioning, and create the partitions on the external drive (If you choose any other option, it is likely that Ubuntu will start messing with your internal drive). When it asks for the bootloader disk, install that on the external drive as well.

The other issue that I can see is with drivers if you ever decide to use it on another computer as well. This is a bit subjective, it depends on your hardware and experience. For example, it may be that one computer requires propreitary drivers to function, while one does not work with propreitary drivers. This is mainly if you use it on multiple computers, if you use it with your laptop only, it should be fine.

If you want to test compatability, you can just either burn the ISO to DVD or USB, and run it from there. It will not install on your system (and just run from DVD/USB) until you ask it to. This is called the "Live Session" where the OS is loaded from the DVD/USB into RAM. As such, changes made in the Live Session will be lost when the computer shuts down.

---

### Post by sudodus on 2015-08-06
Welcome to the Ubuntu Forums :-)

If you unplug your internal drive with Windows before you start installing Ubuntu to the USB HDD, things will be easier and ***safer***. If you install proprietary drivers, the USB HDD will work in your computer and other computers with similar hardware (typically graphics and wifi). Otherwise, with the free linux drivers, the system in the USB HDD will be portable between computers, at least if you are prepared to manage the UEFI/BIOS boot issues.

You can start reading the following links and links from them.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by grahammechanical on 2015-08-06
And do not forget that you will have to enter the BIOS/UEFI boot system to select which drive to boot from. The internal hard disk for Windows and the external USB disk for Ubuntu.

Regards.

---

### Post by shield543 on 2015-08-09
Thanks for all your help. I will test it out and will reply with the result :)

Thanks,
-Luke

---

### Post by NathanRodriguez on 2015-08-09
If your simulation application isn't cpu intensive another option would be run it a Ubuntu running inside Windows through virtualization.

---

