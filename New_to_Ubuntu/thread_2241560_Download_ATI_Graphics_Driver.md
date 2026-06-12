---
title: "Download ATI Graphics Driver"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by jimbob3 on 2014-08-27
i there i was wondering if anyone can help me with a problem i have with  downloading my graphics driver to a rig i am building the spec are as  follows

graphics cards saphire hd 7950 3gb boost

cpu amd sempron 11 cores

ram ddr3 dual channels 8gb

motherboard GA-990FXA-UD3

LINUX 14.4

MY PROBLEM IS WHEN IN TERMINAL I TRY TO PROMPT TO INSTALL CATALYST THIS IS WHAT I GET

warning [amd-catalyst-14.1-betav1.3-linux-x86.x86_64.zip]:  248380 extra bytes at beginning or within zipfile
  (attempting to process anyway)
file #1:  bad zipfile offset (local header sig):  248380
  (attempting to re-compensate)
  inflating: amd-driver-installer-13.35.1005-x86.x86_64.run  
  error:  invalid compressed data to inflate

Can anyone help tried evrything i know and search everywhere for a answer but nothing seems to work anyway thanks for reading

---

### Post by QIII on 2014-08-27
Hello!

(11 cores?  Did you mean 2?)

Anyway --

Is this a file you downloaded from the AMD/ATI website?

What release of Ubuntu are you using?  (Edit:  never mind -- I assume you mean Ubuntu 14.04.  Ubuntu is one distribution of Linux.  Not all Linux is Ubuntu.)

---

### Post by jimbob3 on 2014-08-27
it is and yes i meant two cores

---

### Post by QIII on 2014-08-27
Unless you absolutely must have the proprietary driver for some reason, you can use the default open source Radeon driver installed with Ubuntu.

If you really want the proprietary driver, I'd suggest installing it from the Ubuntu repository.  If you do that, when you do your normal updates and the kernel is updated, the fglrx module will be inserted back into the kernel automatically.

You can do that with the additional drivers functionality or via the command line (which is my preference.)

If you look at the wiki link in my signature, go down to "2.1. Installing via the command line"

If you use the additional drivers functionality, still read the wiki.  You still need to do

```
sudo amdconfig --initial
```

before you reboot.  This is not *supposed *to be necessary, but enough people have come here looking for help that I recommend it anyway.
[h=2][/h]

---

### Post by jimbob3 on 2014-08-27
right what i can do is copy and paste what i did to give you a better idea of what i am attemping

miner@miner-GA-990FXA-UD3:~$ sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic fakeroot libqtgui4 lib32gcc1
[sudo] password for miner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
cdbs is already the newest version.
dh-make is already the newest version.
dkms is already the newest version.
execstack is already the newest version.
fakeroot is already the newest version.
lib32gcc1 is already the newest version.
libqtgui4 is already the newest version.
dh-modaliases is already the newest version.
linux-headers-generic is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 81 not to upgrade.
miner@miner-GA-990FXA-UD3:~$ cd Downloads
miner@miner-GA-990FXA-UD3:~/Downloads$ unzip amd-catalyst-14.1-betav1.3-linux-x86.x86_64.zip
Archive:  amd-catalyst-14.1-betav1.3-linux-x86.x86_64.zip
warning [amd-catalyst-14.1-betav1.3-linux-x86.x86_64.zip]:  248380 extra bytes at beginning or within zipfile
  (attempting to process anyway)
file #1:  bad zipfile offset (local header sig):  248380
  (attempting to re-compensate)
  inflating: amd-driver-installer-13.35.1005-x86.x86_64.run  
  error:  invalid compressed data to inflate
miner@miner-GA-990FXA-UD3:~/Downloads$ 


basically i am trying to download this driver so that i can configure the two graphics to work, i am trying to mine alt crypto and i am a bit of a noob when it come to linux and using terminal commands i have also tried sudo apt-get update rebooted and after giving command two install catalyst as above is the resultcan you help

---

### Post by QIII on 2014-08-27
I already know the process.  :)

What I'm saying is that you can make this much, much easier on yourself by following the section in the wiki.

Didn't catch that you have two cards.  That is covered in the wiki, though.

```

sudo amdconfig --adapter=all --initial
```

I tried to make that section as step-by-step and easy as I could.

---

### Post by sandyd on 2014-08-27
**Moved to New To Ubuntu**

---

### Post by mastablasta on 2014-08-27
> **QIII said:**
> 

I tried to make that section as step-by-step and easy as I could.

what he is saying is stop messing with your downloaded file (which seems to be corrupted as it clearly says) and follow 2.1. in the wiki - you have install procedure in item 5.


or just use additional drivers utility in unity and do it a bit more classy via GUI

---

### Post by jimbob3 on 2014-08-27
thanks for answering, i did download catalyst latest nothing 13.1 nothing 14.6 same with all amd catalysts to many bytes in zip folder is the error but thanks anyway going to go to wiki and  see how it goes from there.

Hi mastablasta thanks for replying but have to say in all honesty you have to remember i have never used ubuntu or linux before two days ago so i really am clueless to what your trying to point out, firstly how can the downloaded file be corrupt i also tried it with ubuntu 12.10 with the same result been at it for two days trying all sorts but going too wiki and see how things go from there thanks anyway.

---

### Post by sandyd on 2014-08-27
> **jimbob3 said:**
> thanks for answering, i did download catalyst latest nothing 13.1 nothing 14.6 same with all amd catalysts to many bytes in zip folder is the error but thanks anyway going to go to wiki and  see how it goes from there.

Go to the Unity Dash, and type in "Additional Drivers", and pick the first program that comes up.

You should then be offered the opportunity to install drivers for your video card.

---

### Post by jimbob3 on 2014-08-27
Ok doing first step in wiki

 this is result
```
miner@miner-GA-990FXA-UD3:~$ lspci -vvnn | grep VGA
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] [1002:679a] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
miner@miner-GA-990FXA-UD3:~$ 
```
next step

Downloaded the latest driver catalyst for my cards

next step

check fglrx is installed
its not installed so i am now downloading and will installok folowed instrc and now have installed fglrx as follows
```
miner@miner-GA-990FXA-UD3:~$ fglrxinfo
fglrxinfo: command not found
miner@miner-GA-990FXA-UD3:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
[sudo] password for miner: 
cp: cannot stat &#8216;/etc/X11/xorg.conf&#8217;: No such file or directory
miner@miner-GA-990FXA-UD3:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-generic linux-headers-3.13.0-34 linux-headers-3.13.0-34-generic
  linux-image-3.13.0-34-generic linux-image-extra-3.13.0-34-generic
  linux-image-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-headers-3.13.0-34 linux-headers-3.13.0-34-generic
  linux-image-3.13.0-34-generic linux-image-extra-3.13.0-34-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 to upgrade, 4 to newly install, 0 to remove and 85 not to upgrade.
Need to get 61.5 MB of archives.
After this operation, 270 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-3.13.0-34-generic amd64 3.13.0-34.60 [15.1 MB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-extra-3.13.0-34-generic amd64 3.13.0-34.60 [36.8 MB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-generic amd64 3.13.0.34.40 [1,784 B]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-generic amd64 3.13.0.34.40 [2,344 B]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-34 all 3.13.0-34.60 [8,890 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-34-generic amd64 3.13.0-34.60 [712 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-generic amd64 3.13.0.34.40 [2,324 B]
Fetched 61.5 MB in 1min 37s (632 kB/s)                                         
Selecting previously unselected package linux-image-3.13.0-34-generic.
(Reading database ... 163773 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Selecting previously unselected package linux-image-extra-3.13.0-34-generic.
Preparing to unpack .../linux-image-extra-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Unpacking linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Preparing to unpack .../linux-generic_3.13.0.34.40_amd64.deb ...
Unpacking linux-generic (3.13.0.34.40) over (3.13.0.32.38) ...
Preparing to unpack .../linux-image-generic_3.13.0.34.40_amd64.deb ...
Unpacking linux-image-generic (3.13.0.34.40) over (3.13.0.32.38) ...
Selecting previously unselected package linux-headers-3.13.0-34.
Preparing to unpack .../linux-headers-3.13.0-34_3.13.0-34.60_all.deb ...
Unpacking linux-headers-3.13.0-34 (3.13.0-34.60) ...
Selecting previously unselected package linux-headers-3.13.0-34-generic.
Preparing to unpack .../linux-headers-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Unpacking linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Preparing to unpack .../linux-headers-generic_3.13.0.34.40_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.34.40) over (3.13.0.32.38) ...
Setting up linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-34-generic
) points to /boot/initrd.img-3.13.0-34-generic
 (/boot/initrd.img-3.13.0-34-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-34-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-34-generic
) points to /boot/vmlinuz-3.13.0-34-generic
 (/boot/vmlinuz-3.13.0-34-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-34-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (3.13.0.34.40) ...
Setting up linux-headers-3.13.0-34 (3.13.0-34.60) ...
Setting up linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Setting up linux-headers-generic (3.13.0.34.40) ...
Setting up linux-generic (3.13.0.34.40) ...
miner@miner-GA-990FXA-UD3:~$ sudo apt-get install fglrx fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot lib32gcc1 libc-dev-bin libc6 libc6-dbg libc6-dev libc6-i386
  libfakeroot
Suggested packages:
  dpkg-dev debhelper glibc-doc
The following NEW packages will be installed
  dkms fakeroot fglrx fglrx-amdcccle lib32gcc1 libc6-i386 libfakeroot
The following packages will be upgraded:
  libc-dev-bin libc6 libc6-dbg libc6-dev
4 to upgrade, 7 to newly install, 0 to remove and 81 not to upgrade.
Need to get 76.8 MB of archives.
After this operation, 285 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main libc6-dev amd64 2.19-0ubuntu6.1 [1,915 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main libc-dev-bin amd64 2.19-0ubuntu6.1 [69.0 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main libc6-dbg amd64 2.19-0ubuntu6.1 [3,459 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main libc6 amd64 2.19-0ubuntu6.1 [4,739 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main dkms all 2.2.0.3-1.1ubuntu5 [64.4 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main libfakeroot amd64 1.20-3ubuntu2 [25.4 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main fakeroot amd64 1.20-3ubuntu2 [55.0 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main libc6-i386 amd64 2.19-0ubuntu6.1 [2,204 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main lib32gcc1 amd64 1:4.9-20140406-0ubuntu1 [47.6 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/restricted fglrx amd64 2:13.350.1-0ubuntu2 [59.2 MB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/restricted fglrx-amdcccle amd64 2:13.350.1-0ubuntu2 [5,079 kB]
Fetched 76.8 MB in 2min 1s (631 kB/s)                                          
Preconfiguring packages ...
(Reading database ... 193384 files and directories currently installed.)
Preparing to unpack .../libc6-dev_2.19-0ubuntu6.1_amd64.deb ...
Unpacking libc6-dev:amd64 (2.19-0ubuntu6.1) over (2.19-0ubuntu6) ...
Preparing to unpack .../libc-dev-bin_2.19-0ubuntu6.1_amd64.deb ...
Unpacking libc-dev-bin (2.19-0ubuntu6.1) over (2.19-0ubuntu6) ...
Preparing to unpack .../libc6-dbg_2.19-0ubuntu6.1_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.19-0ubuntu6.1) over (2.19-0ubuntu6) ...
Preparing to unpack .../libc6_2.19-0ubuntu6.1_amd64.deb ...
Unpacking libc6:amd64 (2.19-0ubuntu6.1) over (2.19-0ubuntu6) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libc6:amd64 (2.19-0ubuntu6.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package dkms.
(Reading database ... 193384 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20-3ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking fakeroot (1.20-3ubuntu2) ...
Selecting previously unselected package libc6-i386.
Preparing to unpack .../libc6-i386_2.19-0ubuntu6.1_amd64.deb ...
Unpacking libc6-i386 (2.19-0ubuntu6.1) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a4.9-20140406-0ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:4.9-20140406-0ubuntu1) ...
Selecting previously unselected package fglrx.
Preparing to unpack .../fglrx_2%3a13.350.1-0ubuntu2_amd64.deb ...
Unpacking fglrx (2:13.350.1-0ubuntu2) ...
Selecting previously unselected package fglrx-amdcccle.
Preparing to unpack .../fglrx-amdcccle_2%3a13.350.1-0ubuntu2_amd64.deb ...
Unpacking fglrx-amdcccle (2:13.350.1-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libc-dev-bin (2.19-0ubuntu6.1) ...
Setting up libc6-dev:amd64 (2.19-0ubuntu6.1) ...
Setting up libc6-dbg:amd64 (2.19-0ubuntu6.1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Setting up libfakeroot:amd64 (1.20-3ubuntu2) ...
Setting up fakeroot (1.20-3ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libc6-i386 (2.19-0ubuntu6.1) ...
Setting up lib32gcc1 (1:4.9-20140406-0ubuntu1) ...
Setting up fglrx (2:13.350.1-0ubuntu2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
Loading new fglrx-13.350.1 DKMS files...
First Installation: checking all kernels...
Building for 3.13.0-32-generic and 3.13.0-34-generic
Building for architecture x86_64
Building initial module for 3.13.0-32-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-32-generic/updates/dkms/

depmod......

DKMS: install completed.
Building initial module for 3.13.0-34-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-34-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up fglrx-amdcccle (2:13.350.1-0ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
miner@miner-GA-990FXA-UD3:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0
miner@miner-GA-990FXA-UD3:~$
```

---

### Post by jimbob3 on 2014-08-27
ok flllowed steps 2.1 and success yay!!
but still no drivers 
followed step 3.1 
when putting in instruc to install catalyst no such file or directory so been me i went back to the first tuturial i saw and followed his instruct to install catalyst driver did not work but that was dont to the fact in my haste i forgot in this tuturial the catalyst he is using is 14.4 instead of 13.4 which i downloaded so in frustation i flung the computer against the wall and said **** it OHHH NO i didnt i went back to begining of this tuturial and type in sudo apt-get update and low and behold systemstarted downloading and i managed to catch saphire in the scrypt held my breath and the monster rebooted and i have success so thank you to every one and i might be back to get advice on how to configure my CGMINER 3.7.2

Oh the tutorial that i was speaking of is highoncoins.com 
[h=1]How to Install Ubuntu and Optimize CGMiner for Litecoin Mining Rig![/h]

---

### Post by QIII on 2014-09-03
> **jimbob3 said:**
> ok flllowed steps 2.1 and success yay!!
but still no drivers

What does this mean?  If it installed, what makes you think you have no driver?

Please stop trying to follow the other tutorial.  You have likely made a mess of your system now.

---

### Post by JKyleOKC on 2014-09-03
> **jimbob3 said:**
> Hi mastablasta thanks for replying but have to say in all honesty you have to remember i have never used ubuntu or linux before two days ago so i really am clueless to what your trying to point out, firstly **how can the downloaded file be corrupt** i also tried it with ubuntu 12.10 with the same result been at it for two days trying all sorts but going too wiki and see how things go from there thanks anyway.While everyone else has been trying to help you get through the immediate problem, this post tells me that there's a more basic underlying problem you need to address -- it comes from one of the major differences between most all flavors of Linux, and those other operating systems that come from Redmond and Cupertino.

That difference is that the two commercial systems are built to be "plug and play" to the greatest extent possible, and include all sorts of behind-the-scenes checks to hide inevitable problems such as files getting damaged during a download. In order to do so, they pretty much force setup to be the same for everybody. Linux systems, on the other hand, are designed to give the end user the maximum amount of choice in setting things up, and consequently don't have those hidden checks for damage. You have to do it yourself in most cases, although installing packages from the official repositories will guarantee at least some checking happens.

Now to answer "how can the downloaded file be corrupt" for you: Anything can happen during a download. The air conditioner next door can kick on and put a noise pulse on your cables. A gopher can nibble the insulation on wiring at a phone company junction box. It only takes a single bit getting lost to make a file unreadable. Because of this, it's a good idea to verify the accuracy of any download; we have tools to do so. Actually, though, many if not most of us don't bother to do the verification until we run into the kind of problem you've had. We then do the check, or if we're as lazy as I usually am, just download it again and compare the two versions with the "diff" utility.

Welcome to our world! It can be quite confusing during the first few weeks, but I hope you'll stick with it and come here for help whenever things get too mystifying...

---

### Post by jimbob3 on 2014-09-03
hi i have a serious issue when trying to install catalyst manually i keep getting this error

Error! Bad return status for module build on kernel: 3.13.0-35-generic (x86_64)
Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up fglrx-amdcccle (2:13.251-0ubuntu1) ...
Setting up fglrx-dev (2:13.251-0ubuntu1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
darkcoin@darkcoin-GA-990FXA-UD3:~/Downloads$ 

i am a noob to unbuntu and dont know exactly how to go about resolving  this issue, i have looked about for a solution but  with no success i  have read that it might have somthing to do with xorg and how amd wont  develope drivers that support the xorg platform can anyone help thanks.

---

### Post by lisati on 2014-09-03
Threads merged.

Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

### Post by uRock on 2014-09-03
> **sandyd said:**
> Go to the Unity Dash, and type in "Additional Drivers", and pick the first program that comes up.

You should then be offered the opportunity to install drivers for your video card.

I am wondering. Did you try what sandyd offered? I've installed drivers manually before and it is all fun and games until the next update breaks it. However, Additional Drivers has worked fine for the past 4-5 years.

---

### Post by jimbob3 on 2014-09-03
Cheers buddie i will try and stick around

thanks urock installed now i am getting problem with finalizing install.

yes oh moderator my humble appologies

tried all your sugestions and still get issues when trying to 
sudo dpkg -i fglrx*.deb

get kernel error

done that still same 

sudo dpkg -i fglrx*.deb when doing this i get a
error in kernel thanks anyway

---

### Post by Mark Phelps on 2014-09-03
Sorry, but you're flailing around doing lots of stuff -- and just getting folks confused in the process!!

WHAT you need to do is the following:
1) Remove any fglrx drivers you have installed
2) Use the Additional Drivers dialogue box to install the fglrx drivers.  Stop trying to do this using the command line.

To do 1), follow the steps for removing the fglrs drivers shown in the link: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by jimbob3 on 2014-09-03
thanks man try it out see hows goes, its the cgminer after installing repository drivers that fails to launch through the sh minenow.sh file that i create in cgminer in the cgminer folder to launch miner that fails need help with that too?

how do i go to the unity dash noob alert

---

### Post by uRock on 2014-09-03
If you have the driver installed, then maybe it is time for a new thread on how to get cgminer working.

---

### Post by jimbob3 on 2014-09-04
Noob here once i get a grip of linux it will become clearer.

---

