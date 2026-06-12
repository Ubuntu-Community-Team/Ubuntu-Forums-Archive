---
title: "Dual boot with Vista"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by josef4 on 2014-04-02
Hi Folks !!

I am totally new to Linux (and Ubuntu !!!) but I am excited to start learning about it since over the years I have heard a lot from those loyal to Linux about how good it is, and I have a friend who gives high praise to Ubuntu. So, I am making the jump. I want to get my feet wet by setting up a 'dual boot'. Currently I have Windows Vista installed on my PC and I would like to install Ubuntu also onto my PC. From what I understand I should be able to boot my PC and encounter a prompt that will allow me to choose which operating system to start up.

Can someone confirm if I my thinking is valid (dual boot possibility)? Also, should I choose the latest Ubuntu version? Exactly which file do I download, and how do I set up the dual boot?


My thanks to all of you !!!!


Josef

---

### Post by slickymaster on 2014-04-02
> **josef4 said:**
> Hi Folks !!

I am totally new to Linux (and Ubuntu !!!) but I am excited to start learning about it since over the years I have heard a lot from those loyal to Linux about how good it is, and I have a friend who gives high praise to Ubuntu. So, I am making the jump. I want to get my feet wet by setting up a 'dual boot'. Currently I have Windows Vista installed on my PC and I would like to install Ubuntu also onto my PC. From what I understand I should be able to boot my PC and encounter a prompt that will allow me to choose which operating system to start up.

Can someone confirm if I my thinking is valid (dual boot possibility)?

Yes, it is. [Here]("https://help.ubuntu.com/community/WindowsDualBoot"), you'll find everything you need to know on how to set up your computer in order to dual boot Ubuntu and Windows.
> **josef4 said:**
> Also, should I choose the latest Ubuntu version?
Coming April, 17th, there will be the release of Ubuntu Trusty Tahr, which is a Long Term Support (LTS) version, meaning that it will receive a 5 years support.
> **josef4 said:**
> Exactly which file do I download, and how do I set up the dual boot?
My thanks to all of you !!!!
Josef
Again, please refer to the link I provided you in my answer to your first question.

_**EDIT:**_ And be very welcome not only to the forums but also to the *buntu world.

---

### Post by sotiris2 on 2014-04-02
If you gave us your system specifications you would get some suggestions regarding which version will run best on your system. Also make sure you read the guides and if you don't understand something ask **before** installation. You will save your self hassle and time from unnecessary mistakes. Especially make sure you understand partitions. Lastly before starting backup your personal files and remember that even during installation in ubuntu you can pop firefox and come here to ask about what *option c* does and which you should choose.. (just have an ethernet cable plugged, even if you normally use wifi and keep the computer far from the rooter I would do the installation next to the rooter with cable plugged).

---

### Post by mastablasta on 2014-04-02
or ask in IRC channel for a faster response

---

### Post by Warren Hill on 2014-04-02
One nice feature of all the *buntu variants.  [Ubuntu]("http://www.ubuntu.com/download/desktop"), [Kubuntu]("http://www.kubuntu.org/getkubuntu/download"), [Xubuntu]("http://xubuntu.org/getxubuntu/"), [Lubuntu]("http://lubuntu.net/"), etc. is that they will all run from a live USB.  So you can try them all without installing then go for the one you want.

Ubuntu is the most popular but needs a reasonably powerful PC. Similarly Kubuntu needs a reasonably powerful PC but has the KDE desktop instead of Unity. Xubuntu and Lubuntu will work on older hardware.

Full details on creating a USB and installing are here: 
[h=1][[SIZE=2]Installation/[/SIZE]]("https://help.ubuntu.com/community/Installation/FromUSBStick")[SIZE=2][FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick?action=fullsearch&value=linkto%3A%22Installation%2FFromUSBStick%22&context=180")[/SIZE][/h]                 
You can easily dual boot with any version of Windows prior to Windows 8.  If you have windows 8 or 8.1 however see:

[h=1][SIZE=2][Installing Ubuntu on a Pre-Installed Windows 8 (64-bit) System (UEFI Supported)]("http://askubuntu.com/q/221835/107450")[/SIZE][/h]

---

### Post by josef4 on 2014-04-02
Hello Everyone,

My thanks to all for the useful and interesting suggestions you provided. I feel I have a lot of good stuff to start with.

It probably isn't a major consideration but I realize I should have described my computer system. I have a Gateway PC with an AMD processor (I think it's a dual-core, but nothing fancy),  my OS is Windows Vista, I have 3 GB of memory, and a 250 GB hard drive with about 150 GB free space.

Again,  many thanks to you all for getting me started !!!

Josef

---

### Post by gigix85 on 2014-04-03
Any flavour of Ubuntu 12.04 should run on that, although probably Xubuntu or Lubuntu will feel noticeably faster and responsive. 150 GB is more than enough in terms of space.

---

### Post by mastablasta on 2014-04-03
to make the installer recognise the free space it needs to be unformatted, you can do that in windows disk manager (make partition smaller). be sure to run disk defragmentation first before doing any partition movement. run it twice (second time will be fast). after shrinking the disk parittion to create empty unformatted disk space, run a checkdisk from windows. you can then proceed with install. computer will likely run any version you choose. make sure you try it in live session first to see if all devices work well. and also to see if you like the graphical interface.

live session loads the whole os into RAM so it will be slower than propper install later on.even if it runs a bit slower it will let you know if there are any issues with external hardware (wi-fi, printer, camera, graphics...). most drivers in linux are included in kernel (core of the OS) but some devices (for legal reasons) have extra drivers available externaly- more on how to install additional drivers in linux: [http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)

---

