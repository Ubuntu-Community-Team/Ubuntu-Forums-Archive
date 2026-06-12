---
title: "Installing Ubuntu onto an SSD partition"
date: 2017-06-27
forum: New to Ubuntu
---

### Post by petrusski on 2017-06-27
Hello,

Recently I have successfully managed to install Ubuntu onto an external hard drive. However, this is not preferable, and I would very much prefer to be able to install it onto my laptop's SSD. The laptop's main OS is Windows 10, so I am dual-booting, and in order to install I had to run Rufus on a USB and boot from there. I have created a partition on my SSD that's just under 500GBs, which I believe should be more than enough. Is there some sort of tool or software that I can download to handle this for me in a GUI, as I am very new to the Linux world, or some terminal commands to help me?
Thanks in advance.

---

### Post by Topsiho on 2017-06-27
Hi,

You write that you installed Ubuntu successfully on an external hard drive. So you know how to install Ubuntu. Installing it on the internal hard disk is not different, even if it is an SSD, except that you now want to install it next to Windows, as a dual boot, which complicates things as you don't want to loose your Windows and personal data (the personal and other data you don't want to lose you should backup anyway-NOW).
For Ubuntu, depending on what you want to use it for, 500 GB is way sufficient, for exploring Ubuntu (and Linux generally) you could install it in, let's say, 10 GB, preferably somewhat more than that.
When installing Ubuntu, you at one point get the choice to install it next to Windows, or in a continuous unallocated space (or something like that), which is what you should do.
Or else you could partition the unallocated space that you created (the 500 GB) yourself: a / partition (let's say > 8 GB, a swap partition (twice system memory), and a /home partition for your personal files (any size).
The choices that you make are definite only when the new partitions are put in place, and the actual install starts, so you can experiment up until that point, going back if necessary.
The really important thing is detecting in what partition your Windows and Windows files are located, as far as I know it is always in /sda1 (first partition in your first (or only) hard disk)  for the Windows system. And other partitions for the other files in Windows, which you should not touch (that means: NOT FORMAT) if you don't know what they contain (I don't use Windows for about 10 years now, so maybe someone else can expand on that!).

Success,

Topsiho

---

### Post by cc1984 on 2017-06-27
You wont need the command line for the install, the GUI will be the same as you used for the install on the external drive. Here are some [instructions for dual booting]("https://help.ubuntu.com/community/WindowsDualBoot"). Please do your self a favor and create a Windows recovery point and backup all your data. Many run Windows/Linux dual boot but there are some risks associated with that. If you back everything up then if you have any issues you can always restore your system.

Also, welcome to the Linux community. Don't be afraid of the command line, it is a friend you just haven't been acquainted with yet. Here is [a good read]("http://linuxcommand.org/tlcl.php/") to familiarize your self with it.

---

### Post by Mark Phelps on 2017-06-27
You're going to run into two problems doing a dual-boot install in Win10.

First, Win10 will be hibernated when you shut it down -- it does that by default.  That is most likely going to prevent the Ubuntu installer from seeing it.  If that is the case, do NOT, repeat NOT, attempt to install Ubuntu as doing so will then trash your Win10 setup.  You would need to disable Fast Startup (NOT the same as fast boot) and try the install again, hoping this time that the Ubuntu installer sees Win10.

Instructions for disabling Fast Startup in Win10:

Win10 has enabled a new hibernation process known as Fast Startup -- which is different from Fast Boot.  This is supposed to dramatically speed up the booting process, but in some PCs, it actually slows it down or causes it to hang.  This could be what is happening to your PC.
 
Disabling Fast Startup might fix the booting problem.
 
There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

Second, do NOT, repeat NOT, allow the Ubuntu installer to shrink Win10 to make room for Ubuntu.  This risks corrupting the Windows filesystem and rendering it unbootable.  Instead, you should use the Disk Management tool in Windows to shrink the OS partition to make some room.  Do NOT create a partition in that space using Windows; instead, use the Something Else option in the Ubuntu installer to manually create a partition in the unallocated space.

Good Luck

---

### Post by Topsiho on 2017-06-28
> **Mark Phelps said:**
> You're going to run into two problems doing a dual-boot install in Win10.

Second, do NOT, repeat NOT, allow the Ubuntu installer to shrink Win10 to make room for Ubuntu.  This risks corrupting the Windows filesystem and rendering it unbootable.  Instead, you should use the Disk Management tool in Windows to shrink the OS partition to make some room.


Yes, that's great advice, that I forgot to mention, sorry for that. After having done this in Windows itself, first restart Windows and see whether it does restart in the new situation, a situation that Windows should know as it created this itself.
This way the chance that you get a system that doesn't boot Windows, after installing Ubuntu next to it, is reduced.

Topsiho

---

### Post by petrusski on 2017-07-01
@Everyone who had replied: I had thought that maybe I just needed to run the installer like I did before, but wasn't sure. Thank you for clearing that up for me. However, this seems to be the root of the problem.
@Mark Phelps: I've actually already attempted this before, but here's the issue I'm running into. I've already created the 500GB partition, but for some reason when I select it and hit "install now" I get this error message:
"No root file system is defined. Please correct this from the partitioning menu."
I have no idea what this means and what it is asking me to do. Is it safe for me to just select to install next to Windows Boot Manager?

---

### Post by oldfred on 2017-07-01
All the auto install options create / (root) and swap.
If you are using Something Else and have created an ext4 partition in advance with gparted, you have to tell the installer that you want to use that partition. On the partitioning screen use the change button and select /. You may have to reselect ext4 and format.
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

While older version, install process is still the same:
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

### Post by petrusski on 2017-07-01
> **oldfred said:**
> All the auto install options create / (root) and swap.
If you are using Something Else and have created an ext4 partition in advance with gparted, you have to tell the installer that you want to use that partition. On the partitioning screen use the change button and select /. You may have to reselect ext4 and format.
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

While older version, install process is still the same:
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

Success! It took me a while to realize what you meant by selecting /, but I did it, and without screwing up my windows partition as well. Thank you all for your assistance.

---

### Post by Topsiho on 2017-07-02
Great. Congratulations.
And thanks for reporting back that you now have had success.

Topsiho

---

