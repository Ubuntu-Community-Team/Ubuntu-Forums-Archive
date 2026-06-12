---
title: "install on second hard drive"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wildmanne39 on 2011-06-02
Hi, I am installing from usb stick I have windows 7 and ubuntu natty on first disk, I want to install 11.10 in second disk, do I install grub to the disk I am installing 11.10 on or does it have to take the place of the grub I have installed on my other drive for natty and win 7? Thanks in advance for your help, it is much appreciated.

---

### Post by oldfred on 2011-06-02
I would install it to your second drive. Leave your working system configured to work. You can run a sudo update-grub on your working system & it will find your new install also. But if grub2 is on the second drive it will let you boot it also.

I have three copies of grub2, some different versions on each of my three drives all booting by default different installs. I default to the install with the one I consider my working install. I have the beta just default to sda where I have XP which I use very little now.

---

### Post by wildmanne39 on 2011-06-03
> **oldfred said:**
> I would install it to your second drive. Leave your working system configured to work. You can run a sudo update-grub on your working system & it will find your new install also. But if grub2 is on the second drive it will let you boot it also.

I have three copies of grub2, some different versions on each of my three drives all booting by default different installs. I default to the install with the one I consider my working install. I have the beta just default to sda where I have XP which I use very little now.
HI, thank you very much for your help, I installed on the second drive, but I also have a few files on that drive from natty backed up on one small partition, when I rebooted and hit escape all I got was the grub error, I was looking over my material for reinstalling grub, I guess because the first partition had the natty files it was probably looking for grub there, I am about to reboot with the usd drive and run the commands to see where it is looking for grub at. I can still boot natty, after I thought about it I figured since I have to hit escape to choose which drive I want to boot from then I should not have a problem with grub2 on both drives, is that thinking right?
Thanks a lot for your help I know you have a lot of experience with booting issues,I appreciate any advice you have to offer.

---

### Post by oldfred on 2011-06-03
If you did manual install, you should have had a combo box with a choice of sda & sdb with the full drive hard ware names. It may show partitions but do not use those.

If you can boot your current system, you can run a update-grub and it should let you boot your new install. Then from the new install you can just do a install to sdb.

Boot Natty from sda.
sudo update-grub

That should add Oneiric to your menu.

Then boot Oneiric and from it.
sudo grub-install /dev/sdb

You may have to run this to make sure it reinstalls to sdb.
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If not sdb's hard drive:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by wildmanne39 on 2011-06-03
> **oldfred said:**
> If you did manual install, you should have had a combo box with a choice of sda & sdb with the full drive hard ware names. It may show partitions but do not use those.

If you can boot your current system, you can run a update-grub and it should let you boot your new install. Then from the new install you can just do a install to sdb.

Boot Natty from sda.
sudo update-grub

That should add Oneiric to your menu.

Then boot Oneiric and from it.
sudo grub-install /dev/sdb

You may have to run this to make sure it reinstalls to sdb.
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If not sdb's hard drive:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitionsHi, thank you, your instructions are perfect, I followed them and had no problems. I appreciate the help this is the first time for me to test from the alpha stage so I am on a learning curve, it has gotten so easy to install ubuntu I have not had any real problems in about three years, so I am rusty. Thanks again.:)

---

### Post by oldfred on 2011-06-03
Glad it worked, I have not had to use commands with Oneiric.

But with Oneiric at Alpha I would expect a lot of breakages. I have only loaded liveCD so far and It crashes, but I need the nVidia drivers to make video better and that is not easy with liveCD.

---

