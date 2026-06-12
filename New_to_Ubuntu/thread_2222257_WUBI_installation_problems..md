---
title: "WUBI installation problems."
date: 2014-05-05
forum: New to Ubuntu
---

### Post by gordon99 on 2014-05-05
I am trying to get into Ubuntu 12.04 via WUBI. It seems to download OK though it takes a time when it gets to the 'expanding' section of the installation. However, it gets there eventually.
When booting up (dual boot with Windows 7) a message appears that indicates a problem with '\proc\mounts'  or some such wording. It then gets to a log in page but nowhere can I enter the password I have provided during the WUBI installation process.
After a brief delay the desktop appears but down at the bottom it says 'Ubuntu 13.10, or something very similar, and not 'Ubuntu 12.04'.
When I try to get a wireless connection the wireless key on my laptop will not switch on. My wireless router is listed but when I click on to it I am asked for a 'root password' and not for the wireless security key.
Could somebody kindly let me know what might be going wrong with the installation process? i should add that I have done one uninstall and a re-install with the same results.

---

### Post by TheFu on 2014-05-05
Wubi is dying thanks to UEFI and GPT disks.  I think 12.04 is the last release with it.  Best to move on, partition for / and swap (logical partitions are fine) and perform a normal install.

So ... first, is your machine using either UEFI or GPT?

---

### Post by monkeybrain20122 on 2014-05-05
WUBI is no longer supported and good riddence IMO. It was basically a marketing gimmick from a time when Ubuntu was not well known, it was a demo rather than something for serious use. If you really want to give Ubuntu a try have the courtesy to treat it on the same footing as Windows and give it its own partition. :) If you run Ubuntu inside Windows you are not really using Linux, I cringe when I hear people saying they 'dual boot' while they are actually running WUBI.

---

### Post by Mark Phelps on 2014-05-05
>  If you run Ubuntu inside Windows you are not really using Linux, 

While that statement is true, using WUBI is NOT "running inside Windows".  The "inside Windows" part is the installation, and while it does create a single file (root.disk) inside a Windows filesystem partition, when you run Ubuntu via Wubi, your are running Ubuntu by itself, NOT "inside Windows".

And, BTW, while I'm not personally a fan of WUBI, it was a useful way to allow people to experience Ubuntu first-hand without the risk of trashing their systems due to partitioning mistakes.

---

### Post by claracc on 2014-05-06
> **gordon99 said:**
> I am trying to get into Ubuntu 12.04 via WUBI. It seems to download OK though it takes a time when it gets to the 'expanding' section of the installation. However, it gets there eventually.
When booting up (dual boot with Windows 7) a message appears that indicates a problem with '\proc\mounts'  or some such wording. It then gets to a log in page but nowhere can I enter the password I have provided during the WUBI installation process.
After a brief delay the desktop appears but down at the bottom it says 'Ubuntu 13.10, or something very similar, and not 'Ubuntu 12.04'.
When I try to get a wireless connection the wireless key on my laptop will not switch on. My wireless router is listed but when I click on to it I am asked for a 'root password' and not for the wireless security key.
Could somebody kindly let me know what might be going wrong with the installation process? i should add that I have done one uninstall and a re-install with the same results.


Where have you downloaded the wubi .iso installation?. It is weird, you obtain at the end an ubuntu 13.10.

Here, you have a link to download the wubi 12.04 iso installation: [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/), at the end, there is a wubi filesystem archive, there you can select Pc(intelx86)wubi which is fir 32 bits or 64-bitPc(Amd64)wubi which is for 64 bits.

Here, you have aguide to do the installation: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by mastablasta on 2014-05-06
it's best if you donwload iso separatelly, verify the md5 sum hash and then put it in same folder as wubi and use it in install.

also i suggest (if you have a good enough mashcine) you try a newer version in virtualbox instead of messing arround with wubi: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

virtualbox is also a safe way to explore linux, but it does need RAM (at leats 2GB, 4 GB for good performance) and a modern CPU.

---

### Post by gordon99 on 2014-05-06
Thanks all for your replies. The odd thing is I downloaded WUBI about 5 weeks ago and it worked as I might have expected though I cannot remember which site I took it from. This time I know I downloaded WUBI twice from CNET which I understand to be a reliable site for downloads. You may well think 'why is he downloading again when he had a perfectly good working program'. Well it's a hard luck story. I thought I would like a proper edition of Ubuntu on its own partition so I borrowed a new edition of the Ubuntu book from the public library and with it came a brand new Ubuntu 12.04 installation disk. I started the installation but when I got as far as the hard disk partitioning i found the book was not quite following the disk and I was getting out of my depth. I therefore cancelled the installation but my screen went black and I was unable to get anything to boot. Thinking it was due to something I had done that I could sort out myself I tried Windows recovery disks, installation disks, hard re-sets and everything I could find, all to no avail. I then took the laptop, a HP Compaq Presario, to a repairer who found the graphics card had become unsoldered. A not uncommon event with AMD processors he said. Still wanting to try Ubuntu i thought I would go back to simple WUBI. Mastablasta, I am afraid I do not understand some of the terms you are using. However, I get the message that I should leave WUBI alone now and try other sources

---

### Post by Vladlenin5000 on 2014-05-06
To put it simply, mastablasta just suggested - again - a standard installation instead of the WUBI "demo". For that you need installation media, either a DVD burned using the ISO* you downloaded or a USB flash memory* (usually faster).

* An ISO file is a common CD/DVD image file intended to be used by some CD/DVD burning software to create an exact copy of the original media. There are a few free Windows utilities that can do that; in a standard Ubuntu installation you already have everything you need.

** In order to make a bootable USB drive you can use Unebootin in Windows; in Linux you have many other options including also Unebootin.



Now, partitioning during the installation process can be tricky if you want to keep Windows - I think you do at least for the moment - and create a dual-boot system. And, adding to the trickiness, most laptops from major brands have reserved partitions for system recovery and you don't want to mess with those unless you're sure you can.  Example: ACER laptops shipped with Vista or Seven usually had 4 primary partitions - A recovery partition at the beginning of the HDD, a "drive C:" partition, a "drive D:" partition and lastly a small partition containing the recovery software kit only - and, as such, you can't install anything else because 4 primary partitions is the limit for old MBR drives. What I usually did was using ACER software from Windows to create a set of recovery DVDs that can recover the original factory image in a bare metal HDD, then deleted the last partitions and shrink the "drive D:" with Windows native tools. Then - and only then - it's possible to install a second OS. Ubuntu will automatically use the unallocated space at the end of the drive to create its own partitions provided the correct option - along Windows xxx - has been selected.

---

### Post by gordon99 on 2014-05-07
Vladlelin5000, I think I will have a similar problem to that which you describe. My notebook, a HP Compaq Presario CQ56, has 4 primary partitions as I understand it. One is called System, one is 'C' drive, the third is a Recovery section and the last one is for HP-Tools.
Some contributors advise shrinking the 'C' drive partition and deleting HP-Tools to make space for Ubuntu. I can see that shrinking the 'C' drive partition would not present a problem as I have plenty of spare space. However other contributors say DO NOT delete the HP-Tools partition as it contains a BIOS recovery tool which might be needed. It seems this particular laptop is designed to prevent a second OS being installed. Any further thoughts on my predicament?

---

### Post by mastablasta on 2014-05-07
> **gordon99 said:**
> Vladlelin5000, I think I will have a similar problem to that which you describe. My notebook, a HP Compaq Presario CQ56, has 4 primary partitions as I understand it. One is called System, one is 'C' drive, the third is a Recovery section and the last one is for HP-Tools.
Some contributors advise shrinking the 'C' drive partition and deleting HP-Tools to make space for Ubuntu. I can see that shrinking the 'C' drive partition would not present a problem as I have plenty of spare space. However other contributors say DO NOT delete the HP-Tools partition as it contains a BIOS recovery tool which might be needed. It seems this particular laptop is designed to prevent a second OS being installed. Any further thoughts on my predicament?

i too have one HP.

here is what i did:
1. prepare a USB with Kubuntu (in your case it will be Ubuntu i guess) using linuxliveUSB (you can also use unetbooting both are good) - instead of USB you can also create live DVD.
2. defragment the drive 2 times (second time is really fast). this will put occupied disk sectors together and on beginnign of partition. reducing the chance of loosing any data on resizing partitions
3. create backups - i used HP tool to create restore disk. but i also used Redobackup (another ubutnu based linux distro) to easilly create an image of whole disk onto external hard disk.
4. now on to installing:
4.1. use mini partition wizzard tool (home version is free) to turn windows (C:\) partition into secondary (logical, extended) partition
4.2. resize the widnows/system (C:\) partition and create free unformatted disk space (this will be where you will install the new OS). if you have space make it at least 30 GB. if not then 10 -15 GB will do.
4.3. boot into windows and run checkdisk (the command is chkdsk /r but there is also a GUI somewhere in accessories or untilities ro disk tools whatever they are...)
4.4. now you are ready! boot the new os and start install. select to install to largest free disk space. the rest of process is explained in installer


the issue i had is that install to largest empty disk space didn't appear. if this happens you need ot use "something else" option, go to free disk space and create a / partition (root) formatted as ext4 and a /swap partition formatted as swap. then you need to make sure grub is put on /dev/sda

the rest is again instructed by installer (password user name, select region, keyboard click next etc...).

edit: just one more thing - if you have enough ram and boot into "try it" mode and then click to install - you can surf the web troubelshoot any issues during install either on forums or on IRC channel (where chat is more in real time).

---

