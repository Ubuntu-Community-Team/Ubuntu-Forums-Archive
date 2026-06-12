---
title: "Dual booting out of an external ssd"
date: 2020-05-08
forum: New to Ubuntu
---

### Post by angupesa0611 on 2020-05-08
So, as it turns out, I have a laptop running windows 10. However, I really need a linux machine for my future career. Nonetheless, I use some stuff on windows that I also need (like fusion 360) which I believe don't work on linux. Furthermore, I really don't have the money to buy a new pc. So i was wondering, is it possible for me to dual boot ubuntu out of an external ssd and use that same ssd as the storage for the ubuntu machine, without having to erase anything from my windows machine or internal ssd?

What I want exactly is to configure the boot priorities in the laptop so that when it turns on and it has the ssd connected, it boots to that ssd that has ubuntu and uses only the external ssd memory as normal storage (so it cant see nor affect the internal memory). And when that external ssd is not conected, it just boots to the internal ssd and uses that as usual. I know booting through an usb drive is really slow, but still... its a lot cheaper than buying another machine!

Will doing something like this cause any problems?
Is it possible at all?
How?

---

### Post by grahammechanical on 2020-05-08
It seems to me that you want to do something like this:

[https://askubuntu.com/questions/606171/how-should-i-install-ubuntu-onto-a-new-ssd-drive-with-windows-7-on-my-old-hard-d](https://askubuntu.com/questions/606171/how-should-i-install-ubuntu-onto-a-new-ssd-drive-with-windows-7-on-my-old-hard-d)

We should always expect problems if we do something like this just once or twice. Problems become rarer the more experience we get. It has been a couple of years since I last put in an install of Ubuntu. I would have to be very careful to avoid problems. I do not own a modern machine with a UEFI motherboard settings utility. So, as experenced as I am in installing Ubuntu, I have done it many times over the last 13 years, I would hit problems installing and dual booting with Windows on a modern machine.

Treat the SSD as a second hard drive and make sure that you install Ubuntu to the SSD. Here are the install instructions. Pay attention to section 6.

[https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview)

Section 6

[https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#6-allocate-drive-space](https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#6-allocate-drive-space)

Do not select Erase disk and install Ubuntu. I repeat, do not select that top option. The install procedure will overwrite your Windows installation. You must select Something Else. Choosing the Something Else option should give you the ability to direct the installer to put Ubuntu on your SSD. 

Others will need to give more advice relative to a UEFI motherboard

Regards.

---

### Post by oldfred on 2020-05-08
Yes you can. With UEFI a bit more tricky.
I regularly put full installs onto flash drives, but those have been slower loading and real slow writing. More for emergency use or a test install.
I did a full install to my old SSD in a caddy and it was almost as quick as internal drive. I used to think USB3 was part of the bottleneck, but actually very little.

With a full install to an external drive, you must partition in advance using gpt partitioning. Main issue is a very old bug in Ubuntu's Ubiquity installer that only installs grub to first drive, usually the internal drive. Many suggest unplugging internal drive which can be difficult for laptop or most UEFI have a setting to disable a drive which may work.
You can install directly and run the work around, I have posted or copy /EFI/ubuntu folder from internal drive to external drive. 
You can in UEFI then set Ubuntu as first boot option and Windows as second. But if Ubuntu booting from internal that will not work.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

At minimum you want an ESP - efi system partition and / (root) which is a default install. Many add either /home and/or data partition(s) depending on size of drive. 

You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Depending on size of external drive 100 to 500MB for ESP and if not large just one ext4 partition for / (root). If larger drive then 25 to 30GB for / and rest for /home and/or data partition(s).

---

