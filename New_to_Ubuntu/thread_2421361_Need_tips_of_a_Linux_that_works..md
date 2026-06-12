---
title: "Need tips of a Linux that works."
date: 2019-06-20
forum: New to Ubuntu
---

### Post by knabbjolf2 on 2019-06-20
Hej.
I need tips of linux distribution that works. My safehavens was puppy linux and ubuntu but as these distributions now fails I need tips of distribution that works. Iam a user and I have absolutley no interest running scripts, walk three circles backwards around my laptop, copying files and spend 3-4 days trying to get a software to do what it is supposed to do. As backup for windows I run linux and stupidly I updated my linuxes when replacing harddrive (a friend managed to activate windows media player = windows update virus found its way through my firewall and it was easier just throw away the harddrive and start from zero with a new one than wasting time trying to get the computer working efficiently). The windows 10 "update crash" took me one evening to fix, ubuntu has taken me 3 evenings now and it is about time to give up on ovebloated linuxes not working). 

All ubuntu 18.04, 18.10 and 19.04 in flavors mint, ubuntu, xubuntu and lubuntu crashes the installer when writing the grub2 efi files to efi fat32 boot patition, and/or external usb flash drive, see attached image. 

Tested Flavors : Xubuntu, ubuntu, lubuntu and mint. Versions 18.04-5, 18.04-6, 18.10, 19.4 linux mint 9 and 19.1. Iso written using rufus, several different usb drives tested, booted into live image and installed from live image. Installer ALWAYS crashing at writing grub2 files at end of install. Installed to 8gb usb flash drive in ext4 with own boot partition fat32 flagged esp and boot, installed to 20gb hard drive partition ext4 writing grub efi to the efi fat32 partition. 

As the installer crashes Im loosing the uuid and boot scripts in grub.cfg for starting the partition and yes, I can get the uuid in terminal but as allready the installer crashes I see no point wasting time testing the software the crashed installer was supposed to start. As the installer always crashing using several flavors and version I decided to give up ubuntu as they seem to have taken a path away from working distros and filling them with endless bloat far away from the rock solid 7.10 and 8.04 hence my question for a less bloated linux distribution alternative, preferably 1-2 years old as it hopefully been tested. One of the strengths with ubuntu was the synaptic installer but as ubuntu completely forgotten about this system and now launching distributions with 10-20 preinstalled programs the confusion must be deeply anchored telling me as a user to look for alternatives.


 [ATTACH=CONFIG]283460[/ATTACH]

---

### Post by dino99 on 2019-06-20
If you are not ranting, then take time to do things smoothly, following the many howtos/wikis/answered questions, like:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

As you said, 'stupidity' might be avoided as that feature is not supported, no matter which distro you use. ):P

---

### Post by TheFu on 2019-06-20
Seems you might be a great candidate for a Chromebook.

---

### Post by grenic on 2019-06-20
LOL - what are you wanting your Linux server to do?

---

### Post by Artim on 2019-06-20
A lot of people find **MX-Linux** as simple as Ubuntu (more like Xubuntu), and it runs on some hardware that Ubuntu balks on.  Like almost every other Linux distro, you are expected to be "a responsible newbie" and read the documentation for some of these hiccups you'll run into, like your UEFI situation.

---

### Post by oldfred on 2019-06-20
Usually the error you posted on grub not installing its UEFI version, is that you partitioned the hard drive without the ESP - efi system partition. 

UEFI systems use gpt partitioning, Microsoft has required vendors to install in UEFI/gpt since Windows 8 released in 2012. But users can install in the now 35 year old BIOS boot with MBR partitioning. That is available more for large companies that want all systems with same configuration.

Post this:
sudo parted -l

---

### Post by crip720 on 2019-06-23
Think Oldfred has the right answer.  You will need to make an EFI partition first, before installing on a new hard drive.  Your old hard drive probably already had an EFI partition and installs worked.  I just installed 19.04 on brand new ssd, but googled around first and found out about making an EFI partition.  Only I made it way too big.

---

