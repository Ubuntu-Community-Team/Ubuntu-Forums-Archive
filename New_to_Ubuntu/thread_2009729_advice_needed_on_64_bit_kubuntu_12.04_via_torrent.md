---
title: "advice needed on 64 bit kubuntu 12.04 via torrent"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by zirgut on 2012-06-24
Someone has advised to get 64 bit kubuntu 12.04 via torrent to help solve my problems of sound loss and also issues with running in low graphics mode. I have no idea what 64 bit kubuntu 12.04 via torrent is and whether this is a good idea for me and what the advantages and disadvantages may be. Can anybody , in a nutshell, enlighten me?
Thanks

---

### Post by raja.genupula on 2012-06-24
this is the link you actually need [http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download).

there is no relation with sound issues and other issues with type of downloading a version . 

give me these details :

1 What are the specifications and bit type of your system ?
2 open terminal and type lspci

---

### Post by zirgut on 2012-06-24
Hi Raja
This is what came up
adrian@adrian-Dell-DM051:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1)
03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
03:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)

---

### Post by raja.genupula on 2012-06-24
is your system suitable for KDE environment , i have asked specifications also . mention them .

---

### Post by zirgut on 2012-06-25
Hi Thanks for getting back. You are talking to a complete non computer person who sometimes struggles to find the on-off button in the morning! The computer is a Dell and I think has a total hard drive of 160 GB. I did partition the hard drive with help about 18 months ago to install Ubuntu. There is also a very slow windows 7 installed.On Ubuntu it shows a 95GB file system.  Where do I find out about the bit system?

---

### Post by sudodus on 2012-06-25
I think he meant that you specify CPU type and speed, RAM size and graphics card (and maybe a little bit more).

You can find out about that with
```
sudo lshw > lshw.txt
```

(and attach the file lshw.txt to a reply)

Maybe you should also post the output of

```
glxinfo | grep -i opengl
```

or get info about graphics from the GUI program ***hardinfo***, look at the section about Display

---

### Post by Strangenessness on 2012-06-25
My first post! Yeah dude, It would help greatly if you know what Cpu you are running aswell as total memory etc, just general specs... Just wondering are you running onboard graphics or a separate card, same with sound aswell on board or separate?  Either way what would be your specs there aswell?
:p

---

### Post by raja.genupula on 2012-06-25
> **zirgut said:**
> Hi Thanks for getting back. You are talking to a complete non computer person who sometimes struggles to find the on-off button in the morning! The computer is a Dell and I think has a total hard drive of 160 GB. I did partition the hard drive with help about 18 months ago to install Ubuntu. There is also a very slow windows 7 installed.On Ubuntu it shows a 95GB file system.  Where do I find out about the bit system?

open system monitor there you will find the details i need , i mean this [IMG]http://i.stack.imgur.com/AewTU.jpg[/IMG]

---

### Post by SeijiSensei on 2012-06-25
I suggest you simply download and burn the Kubuntu 12.04 CD-ROM from [http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/).  With a Core2Duo processor you can use the 64-bit "AMD" version.  

Burn the CD and boot from it.  Then choose "Try Ubuntu" when the choice appears.  You'll now be running off the CD and making no changes to the installed software on your hard drive.  See how audio works with 12.04.

---

### Post by zirgut on 2012-06-25
> **raja.genupula said:**
> open system monitor there you will find the details i need , i mean this [IMG]http://i.stack.imgur.com/AewTU.jpg[/IMG]
Hi,
You are going to love me for this but where do I find system monitor. I am on ubuntu 12.04. Spent half hour searching but could not find.

---

### Post by Paqman on 2012-06-25
> **zirgut said:**
> Hi,
You are going to love me for this but where do I find system monitor. I am on ubuntu 12.04. Spent half hour searching but could not find.

Hit the Windows key and start typing the word "system" and it'll find it.

---

### Post by zirgut on 2012-06-26
Thanks for every ones help. The output from sudodus suggestions is as follows
1. PCI Sysfs
2. OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:
 Then from looking on my windows OS I found this under operating system:
Intel(R) Pentium R D CPU 2.80 Ghz 2.79 GHz
Installed memory (RAM) 1.00 GB
32-bit Operating System. I did know that I did not have a dual core processor but did not know that was what decided the bit business.So presumably I cannot run a 64 bit Kubuntu 12.04 via torrent.

---

### Post by Paqman on 2012-06-26
Right, so you're running in a virtual machine? That changes everything! Your sound and video problems are likely to be configuration issues within VMWare.

Have you tried running Ubuntu from the CD? You may find your sound problems are magically fixed, and you'll probably get better video performance too.

You can run a 64-bit OS by the way. Your chip is 64-bit [according to Intel]("http://ark.intel.com/products/27512/Intel-Pentium-D-Processor-820-(2M-Cache-2_80-GHz-800-MHz-FSB)").

---

### Post by zirgut on 2012-06-26
Hi 
Thanks for that suggestion. It is easy when you know how.
Release 12.04 (precise) 32 bit
Kernel Linux 3.2.0-25-Generic
GNOME 3.4.1

Hardware
Memory 1000.0 MiB
Processor Intel Pentium(r) D CPU 2.80GHz x 2
System Status
Available disk space 42.5 GiB

---

### Post by zirgut on 2012-06-26
Hi,
So are you saying I should stay with Ubuntu 12.04 but download it on to a cd. I just upgraded from the previous version so do not currently have a CD. That would be easier than going the Kubuntu route?
Thanks

---

### Post by Paqman on 2012-06-26
If you're running the OS in VMWare and you're having trouble with some hardware (eg: sound and video) then the problem is highly likely to be with VMWare, as this is what controls access to the hardware for any operating system running within it.

Switching to Kubuntu is highly unlikely to make any difference, as it's the same system as Ubuntu, just with a different desktop.

---

### Post by zirgut on 2012-06-26
Ok,
Many thanks for this. It has been a an interesting diversion and I have  learnt a lot. The sound problem arose when I inadvertently deleted some  files and I was trying to find a way of restoring those files. That is  another thread though. 'loss of sound'. Perhaps I will try reviving that thread and see where it gets me before taking up your suggestion. Appreciatively yours.
zirgut

---

### Post by SeijiSensei on 2012-06-27
Do you have a reason for using a virtual machine?  The fact that you didn't mention this at the beginning tells me you didn't set this up yourself.  Why not just install Ubuntu directly onto the machine?  Do you have other operating systems you're also booting up in separate virtual machines on the same hardware?

---

### Post by zirgut on 2012-06-27
Hi,
Thanks for your interest.
I am beginning to feel out of my depth. This all started in trying to fix my problem of not having any sound and I posted on General help and a member advised using kubuntu 12.04 via torrent. Don't know what it is and don't know the difference between a virtual machine and a non-virtual machine. Just want my sound back. Ubuntu is stored directly on the machine and I also run Windows 7. I believe the correct term is that the hard drive is partitioned, although I am not completely sure about this as there has been some messing about with different upgrades. Anyb pointers where I can go for a few quick tutorials on these terms would also be useful!
Appreciatively
zirgut

---

### Post by SeijiSensei on 2012-06-28
Let's go back to basics, then.  First forget about the word "torrent;" it's just a method of distributed the Ubuntu software.  Next, did you try my [earlier suggestion]("http://ubuntuforums.org/showpost.php?p=12052737&postcount=9") of burning the Kubuntu CD and using the "Try Ubuntu" option to run off the CD and test your audio?  Please give that a try and let us know if the audio system works when running off the CD.  Kubuntu plays a short sequence of musical tones when it starts up.  If you hear the tones, you should have audio.

---

### Post by zirgut on 2012-06-28
Hi,
Thanks for reminding me.I have not tried that yet. Will give it a go and get back to you.

---

