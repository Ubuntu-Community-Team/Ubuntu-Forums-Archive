---
title: "installation of ubuntu onto windows"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by openation1 on 2014-04-01
Hello everyone........... I have windows 7 and I would like to use ubuntu instead. How can I download the program under windows and use ubuntu instead? any help will be gladly apprecieated............. thank you

---

### Post by Double.J on 2014-04-01
Hi there!

Just to clarify are you looking to wipe out win7 (not usually recommended), dual boot both systems (norm) or run ubuntu from windows? This could be either a wubi (ubuntu runs inside a windows install - excellent for trial, not so great for long term use) install or a VM (runs both windows and ubuntu at the same time; lesser performance)?

also just wondering what you have been using up until now?

main thing is to back up your whole system first.

jj

---

### Post by whatthefunk on 2014-04-01
To download Ubuntu, go here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Once the file is downloaded, burn it onto a DVD.  Put the DVD in your computer and reboot.  When the computer starts up again, you will have to enter BIOS to tell the computer to boot from the DVD instead of the hard drive.  This can usually be done by pressing ESC or F2 at your computer manufacturer's splash screen.  Once the boot order is changed, simply follow the installation instructions.  Before installing, I would try it out first...this option is available before installing.

Warning: Installing Ubuntu will completely delete all data on your computer.  If you wish to keep data, make a backup of it first.  If you wish to keep Windows, look into dual booting.

---

### Post by su:bhatta on 2014-04-01
+1 whatthefunk

Installing Ubuntu using Wubi is also not recommended as the Wubi project has been abandoned.

---

### Post by Impavidus on 2014-04-02
Most computers nowadays support booting from usb. A live usb is faster than a live dvd and can be reused for other flavours/distros/releases.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Best to dual boot until you're sure you can live without Windows, unless you have a separate Windows computer available. Use Windows tools to create unallocated disk space, which is different from free disk space. Make sure you don't use all four primary partitions on an MBR partitioned drive. The installer should then offer to install Ubuntu alongside Windows. If you don't want to dual boot, just choose to use the entire drive for Ubuntu. If you know what you're doing, you can partition manually too. First run the live dvd/usb to check for any hardware incompatibilities, especially concerning graphics and wifi. These can usually be solved, but it's best to know in advance.

---

### Post by Rob Sayer on 2014-04-02
Don't totally replace windows unless you have other windows boxes.  There are some windows apps that don't have linux equivalents.  My dislike of windows doesn't change that fact.  This is why I still have a windows 7 partition on a dual boot machine, though I rarely use it.

---

### Post by Mark Phelps on 2014-04-02
If you want to continue to use Win7, don't just boot from the Ubuntu install media and charge forward ... that is a recipe for distaster.  Instead, read through the following before you begin:  

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, and you are using MBR partitioning (not GPT) that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by oldfred on 2014-04-02
In addition to all the good advice above, many or most Windows 7 systems use all 4 primary partitions with MBR(msdos) partitioning.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by boazjones on 2014-04-02
I just purchased a Windows laptop with Windows 8 on it. I chose a non-touch screen version - in order to be able to dual-boot Ubuntu 12.04 LTS.

Even though Windows doesn't 'play well with others'; I will attempt this undertaking nevertheless.

Besides, I have already prepared an appropriate launch device in order to catapult my laptop - in case things go sideways...  O_o

---

### Post by james104 on 2014-04-03
> **boazjones said:**
> I just purchased a Windows laptop with Windows 8 on it. I chose a non-touch screen version - in order to be able to dual-boot Ubuntu 12.04 LTS.

Even though Windows doesn't 'play well with others'; I will attempt this undertaking nevertheless.

Besides, I have already prepared an appropriate launch device in order to catapult my laptop - in case things go sideways...  O_o

You will have to let us know how you get on!

Its my goal this year to purchase a new laptop, I currently have ubuntu dual booted and love it! I know that when I do get a laptop it will be bundled with Win 8 installed and I really want to continue using Ubuntu alongside a windows install.

---

