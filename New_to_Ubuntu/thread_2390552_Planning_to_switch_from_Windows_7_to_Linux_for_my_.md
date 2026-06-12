---
title: "Planning to switch from Windows 7 to Linux for my HP G62 Notebook"
date: 2018-04-30
forum: New to Ubuntu
---

### Post by gho87 on 2018-04-30
I'm currently using windows 7 on both my desktop and laptop. Uncertain about what to do, I would like to prepare on how to change/migrate from Windows to Linux. From what I heard, Ubuntu MATE or Linux Mint is good for newcomers of Linux.

I recently bought a laptop HP G62 Notebook because I was told that I can switch to Linux on one device before doing so as well on my desktop computer. However, I see that HP software is supported on Windows; I'm unsure whether HP software is supported on Linux.

I thought about trying Linux out before actually installing it. Also, I would like to learn how to prepare, so I can avoid encountering a crash while using Linux. suggestions or anything like that?

---

### Post by pantazi on 2018-04-30
I'm a relative newcomer to Linux too and not a young 'un either!

I tried Ubuntu 14.04 on an aging HP 6920S running Vista and soon found that the Linux system ran faster and smoother than when the laptop was new.

Ok, there's a few quirks but usually can be overcome with a little research, plus the helpful folk on this forum.

I wouldn't worry too much regarding the HP software, I found it was pretty useless. Now I'm running Ubuntu 16.04 LTS on an HP Elitebook and have persuaded my wife to use the same on her Lenovo Thinkpad. Both are blindingly quick compared to running Windows and have all the necessary programmes with no bloatware.

Load from USB or blank DVD and run it alongside W7 for a while, I'll guarantee, like me, you'll soon erase Windows and embrace Linux.

---

### Post by SeijiSensei on 2018-04-30
The first issue you need to decide is how tied you are to Windows-only software.  LibreOffice is a decent substitute for Microsoft Office, but it has a much different interface (no "ribbons"). If you must share documents with people using MS, you probably need to run Windows as well. Only you can know how important Windows is to your way of computing.

There are two options you could try if you want to give Ubuntu a test drive.

1) Create a bootable CD or USB with an Ubuntu distro, then choose "Try Ubuntu" when offered that option after booting.  You'll be running entirely off the installation device with no changes made to the existing system.  You'll have the option to mount the partitions on your hard drive if you want to examine how well, say, LibreOffice does with a complicated MS Word document on your machine.

2) Install a copy of [VirtualBox]("https://www.virtualbox.org/") for [Windows]("https://download.virtualbox.org/virtualbox/5.2.10/VirtualBox-5.2.10-122406-Win.exe") and use it to create a virtual machine.  Then install Ubuntu into the VM.  (You don't even need to create a boot medium for this task, as VirtualBox will install directly from an ISO disk image.)  The drawbacks are that the VM won't have direct access to the video hardware, so if you want to play games on Linux this isn't always the best approach. You'll need at least 4 GB of memory to take this approach.  I usually allocate 1.5 G to the Ubuntu VM and leave the rest for Windows.

I like the KDE desktop myself, but it has traditionally been a bit more resource-intensive than other desktop environments.  I suspect the differences are less these days.  One nice thing about using virtual machines is that you can create a number of them and try out different Linux distributions.

---

### Post by sp40140 on 2018-04-30
Before you make the switch, you need to be clear on few things such as:
Why do you want to make the switch?
What applications / software are mandatory for you. (ie. I am fulltime linux user but I do need MS Office once in a while even though there is a good substitute available in linux, and for that I use Win7 in virtual env). So, you need to be aware of this or it can cause lots of frustration. However, most of the software in windows world have couterparts in linux. But you should make list and research are ask around. This is the biggest concern for making the switch.

Other thing is hardware compatibility for device drivers. As you have bought the laptop after consulting with someone about linux, I assume you have this covered.

HP software is practically useless. It mostly comes in use when you call HP for support. And for device drivers and such. That can easily be ignored as you can find same information online very easily.

Actual installation is straight forward. And besides there are very good tutorials to be found all over the internet from this forum to youtube and on and on.

---

### Post by gho87 on 2018-05-05
Here are the [hardware specifications]("https://support.hp.com/us-en/product/hp-g62-300-notebook-pc-series/4247529/model/4308552/document/c02511486"). I hope they are good for one of Ubuntu flavors.

I intend to switch from Windows 7 to Linux when Microsoft stops supporting Windows 7 by 2020. Also, I predict that web browsers will stop supporting it as Google Chrome did to 32-bit Linux, Windows XP and Vista in 2016.

---

### Post by Odisej on 2018-05-06
I wouldn't worry too much.

Before installing you can try out Linux as a live ISO image. Both Ubuntu and Mint will allow you to try the system out first. Pay attention to wi-fi and graphics as you do so. If they work as they should you should install the system. You can set dual booting so that you retain Windows 7 and install Linux as well.

If by HP software you mean the bundled software that comes with the computer: there is no reason to worry. You will not miss it. If you mean printer/scanner software you should not worry as HP has quite good support for the Linux OS.

As you see there are many Linux distributions. Choose one that is the most to your liking. For example: if you are used to the way Windows do things and are reluctant to try something completely different choose a distro that is the most similar to Windows. I am told Linux Mint with Cinnamon desktop (their default) is quite good for making the transition. If on the other hand you feel adventures you can try out xubuntu, for example, fast Linux distro with lightweight desktop environment (even lighter than Ubuntu  MATE).  

I wouldn't recommend installing the latest ubuntu yet as it is totally fresh and there tend to be bugs. Linux Mint is based on Ubuntu 16.04 and is therefore much more stable.

In any case do not be afraid to try Linux out.

---

### Post by oldfred on 2018-05-06
Most Windows 7 systems are BIOS with MBR partitioning and use all 4 primary partitions.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
sudo Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by monkeybrain20122 on 2018-05-06
> **gho87 said:**
> I'm currently using windows 7 on both my desktop and laptop. Uncertain about what to do, I would like to prepare on how to change/migrate from Windows to Linux. From what I heard, Ubuntu MATE or Linux Mint is good for newcomers of Linux.

I recently bought a laptop HP G62 Notebook because I was told that I can switch to Linux on one device before doing so as well on my desktop computer. However, I see that HP software is supported on Windows; I'm unsure whether HP software is supported on Linux.

I thought about trying Linux out before actually installing it. Also, I would like to learn how to prepare, so I can avoid encountering a crash while using Linux. suggestions or anything like that?

What is HP software? What does it do? Need more details.

---

### Post by gho87 on 2018-05-06
> **monkeybrain20122 said:**
> What is HP software? What does it do? Need more details.
A lot of software branded with "HP", like HP Support Assistant, HP BIOS, etc. And I've not yet installed a printer into a laptop.

---

### Post by wildmanne39 on 2018-05-06
I have run Ubuntu on several HP laptop's and when you install Ubuntu you will not have the HP software but it is not needed in Ubuntu, that is a windows software and mainly bloatware and of not much use imo.

---

### Post by monkeybrain20122 on 2018-05-06
> **gho87 said:**
> A lot of software branded with "HP", like HP Support Assistant, HP BIOS, etc. And I've not yet installed a printer into a laptop.

Mostly crapware that you don't need. They only slow down Windows.

---

### Post by gho87 on 2018-05-20
I found out that the [HP BIOS that I'm using]("https://support.hp.com/us-en/drivers/selfservice/swdetails/hp-g62-300-notebook-pc-series/4247529/model/4308552/swItemId/ob-93590-1") does not support Linux. Must I install Ubuntu MATE first and then change to another boot loader, or is it the other way around?

Moreover, I have to change/switch [software drivers]("https://support.hp.com/us-en/drivers/selfservice/hp-g62-300-notebook-pc-series/4247529/model/4308552") for better compatibility with Linux as those drivers are meant for Windows 7. From what I've read, a Linux kernel can automatically detect laptops, like this one. Right?

---

### Post by mörgæs on 2018-05-20
> **gho87 said:**
> I found out that the [HP BIOS that I'm using]("https://support.hp.com/us-en/drivers/selfservice/swdetails/hp-g62-300-notebook-pc-series/4247529/model/4308552/swItemId/ob-93590-1") does not support Linux.

How did you get to that conclusion from the link provided?

My experience is that older HP's work well with GNU/Linux. New HP hardware is turning increasingly hostile and I would recommend other brands.

---

### Post by gho87 on 2018-05-20
> **mörgæs said:**
> How did you get to that conclusion from the link provided?

My experience is that older HP's work well with GNU/Linux. New HP hardware is turning increasingly hostile and I would recommend other brands.
Oh... I'm not sure whether I was right or wrong about HP BIOS F.27. The webpage about the HP BIOS doesn't mention Linux as part of "System requirements", but I must have not known that older BIOS versions can work okay with Linux. Does HP BIOS F.27 work well with Linux, or do other Linux-compatible boot loaders work all right without glitches, bugs, vulnerabilities, or anything like that?

---

### Post by kerry_s on 2018-05-20
make a live installer & try it, you don't need to install just test your hardware, see how it works.

---

### Post by mrdc76 on 2018-05-20
> **gho87 said:**
> Oh... I'm not sure whether I was right or wrong about HP BIOS F.27. The webpage about the HP BIOS doesn't mention Linux as part of "System requirements", but I must have not known that older BIOS versions can work okay with Linux. Does HP BIOS F.27 work well with Linux, or do other Linux-compatible boot loaders work all right without glitches, bugs, vulnerabilities, or anything like that?

The version of the computer's BIOS is irrelevant to the functions of Linux. Computer manufacturers in general do not advertise Linux-compatibility, unless their computers ship with Linux (and most of them do not).

---

### Post by gho87 on 2018-05-21
> **kerry_s said:**
> make a live installer & try it, you don't need to install just test your hardware, see how it works.
I burned a DVD with Ubuntu MATE, booted the DVD, and tried it out without installing it.

The BIOS works well with it; I just had to go to one of booting menus to boot the DVD. Also, the video graphics works almost well, though I see a few icons at the bottom-right corner missing. The touchpad works well also; I can scroll a window only when I double-pointed (another way of saying "double-clicked") a scrollbar. I could not scroll a window down/up while sliding my finger around the right edge of the touchpad, the same way I successfully did at Windows 7.

The Firefox browser and the Wi-fi work also.

Unsure about the audio as I've not tested it yet.

---

### Post by kerry_s on 2018-05-21
touch pad has to be setup for edge scrolling. control center-> mouse or just mouse from the menu. 2 finger scroll is the setup in all linux versions.

vid sounds like you need drivers, there's an app for that in the menu's there.

---

