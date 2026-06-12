---
title: "Installation"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by LAKingsFan on 2012-05-10
Hello everybody! I am new to the Linux world. I just got done building my first computer and have been using windows for a couple weeks now. It has always been my goal to use and learn a Linux system. Well I went to the Ubuntu website and downloaded the OS in 64-bit version. I use windows 64-bit so I thought I would do the same? Well I changed the boot order to CD/ROM and it loaded the CD. It got to the menu asking If I wanna Try Ubuntu without installing, Install Ubuntu, check disk for flaws etc. Anyway anytime I hint enter on any of these it freezes up. I have tried all options and restarted the process many times. Any advice would be much appreciated!

---

### Post by daslinkard on 2012-05-10
Have you checked the md5 hash to make sure the iso is not corrupted? Have you tried a different CD? What steps have you taken in getting Ubuntu to boot?

---

### Post by Utkarsh Ray on 2012-05-10
Similar was the case for me.
Does it stays freezed?
Try waiting for a bit more time and see what happens. But first of all do you want to replace Windows or dual-boot?
Replacing is very easy but most likely you won't like it.
What is your Windows version?
Assuming W7.
1. use 'create and format hard disk partitions' and make a new partition. Try resizing one of the drives.
(you can type it in the search box in start menu)
2. If install doesn't proceed even after waiting for it. Start Windows, and in the CD, open wubi.exe and do as 3-4
3. If it doesn't run from drive, mount the ISO file in windows (use magiciso, daemon tools etc.). After mounting the ISO, open wubi.exe ('install' option in autorun)
4. Click on help with booting with CD-ROM
5. Proceed as instructed.
6. Restart system with CD in the bay (there will be a prompt in wubi installer.)

This should do it, however I advise you to use 32-bit version if you are new. It can be installed within windows and is good for learning the basics. If you screw something up, it wouldn't hurt the system.

---

### Post by Utkarsh Ray on 2012-05-10
> **daslinkard said:**
> Have you checked the md5 hash to make sure the iso is not corrupted? Have you tried a different CD? What steps have you taken in getting Ubuntu to boot?

Good point.
Use winmd5sum for it and obtain MD5 hashes from the website.
Sometimes using a Rewritable CD makes these happen.

---

### Post by LAKingsFan on 2012-05-10
I apologize for my lack of knowledge on the subject, but I am not sure on how to check the md5 hash to see if the iso is corrupted. I haven't tried anything else, but the steps Utkarsh Ray posted look like a place to start.

---

### Post by LAKingsFan on 2012-05-10
Thank you for your help! I am using windows 7 and would like to dual-boot. 

I have created a partition already, but thanks for the heads up! I am going to try all the steps you recommended.

---

### Post by sadaruwan12 on 2012-05-10
OK, Welcome to Linux!

For you I say if you can use the torrent download to download the image 'cos it's the safest way to get the file with out corrupting. Once you get that could you find a 2 or 4 Gb pendrive create a bootable usb from that you can use UNETBOTIN for that.

CD method is old now a pron to get errors so better try the USB way.

Torrent of [Ubutnu64]("http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-amd64.iso.torrent")

Ubuntu [Installation guide]("http://www.ubuntu.com/download/help/install-ubuntu-desktop")

[Softpedia Version]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml")

---

### Post by Utkarsh Ray on 2012-05-10
> **sadaruwan12 said:**
> OK, Welcome to Linux!

For you I say if you can use the torrent download to download the image 'cos it's the safest way to get the file with out corrupting. Once you get that could you find a 2 or 4 Gb pendrive create a bootable usb from that you can use UNETBOTIN for that.

CD method is old now a pron to get errors so better try the USB way.

Torrent of [Ubutnu64]("http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-amd64.iso.torrent")

Ubuntu [Installation guide]("http://www.ubuntu.com/download/help/install-ubuntu-desktop")

[Softpedia Version]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml")

Yes, torrents almost always get downloaded correctly, but remember to use official and trusted torrents like in the link above.
Making a USB start-up key is good option.
Firstly read this [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

But I think USB Startup Creator isn't available in 64-bit CD.

---

