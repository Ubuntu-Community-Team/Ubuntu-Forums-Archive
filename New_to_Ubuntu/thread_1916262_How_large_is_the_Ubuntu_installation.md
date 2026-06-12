---
title: "How large is the Ubuntu installation?"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-01-27
I have a 250gb HDD, and I'm thinking of allocating maybe 100gb to Ubuntu partition. I don't remember how much the installation of Ubuntu takes up, but if I remember, it's around 10GB. Is this correct?

Also, unrelated question, but when 12.04 comes around, is there anyway of keeping settings the same from 11.10? I realize you can make a separate home partition, but will this keep all programs and settings after a new install?

---

### Post by mcduck on 2012-01-27
My Ubuntu install, including all the programs I've added (but not my personal files) is around 5GB. So that would make the default install something around 3**-4 GB...

What comes to keeping settings and programs, the easiest way of course is to upgrade to new version instead of making a fresh install.

You can also either have a separate home partition, or just back up your home directory (including all the hidden files and directories within it) before making a fresh install. Either way would save all your settings, but not the programs themselves.

---

### Post by mastablasta on 2012-01-27
> **Thrashrokz33 said:**
> I have a 250gb HDD, and I'm thinking of allocating maybe 100gb to Ubuntu partition. I don't remember how much the installation of Ubuntu takes up, but if I remember, it's around 10GB. Is this correct?
about 4 - 5GB then it depedns what stuff you add.

> 
Also, unrelated question, but when 12.04 comes around, is there anyway of keeping settings the same from 11.10? I realize you can make a separate home partition, but will this keep all programs and settings after a new install?

upgrade function. it works if you keep the system more or less in vanilla state. if ou add PPA's and install themes themes then it's hard ot say how well it will go. otherwise for upgrade it's best to disable PPA before doing it and uninstall any proprietary drivers (if you are using any).

---

### Post by Thrashrokz33 on 2012-01-27
What is a PPA? Is it a desktop environment or something?

---

### Post by yetiman64 on 2012-01-27
> **Thrashrokz33 said:**
> What is a PPA? Is it a desktop environment or something?
PPAs are Personal Package Archives, they are software packages put together by individuals/groups to store packages for other users to install.
PPAs are entries that are added to your sources list (Software Sources) so your installation of the PPA package in question is always kept up to date.

If you go the upgrade route, take note of mastablasta's comments about disabling such ppas and uninstalling any proprietary drivers prior to doing the upgrade. You will likely have a much better upgrade experience by doing so.

---

### Post by 3rdalbum on 2012-01-27
Even if you do a fresh install, even without a seperate /home partition : as long as you use the "manual" option in the installer and don't elect to format the partition, your settings and user files will be preserved.

---

### Post by Kixtosh on 2012-01-27
The short answer is that an Ubuntu installation isn't very large by default. I have a small laptop with a 64 GB hard drive that I dual boot, so I had to manage space allocation quite carefully:

[LIST]
[*]Windows Vista Business alone requires 30 GB in "out of the box" state, with no additional software or user files (although this does include a trial version of MS Office 2007). This varies with automatic updates and has been as high as 35 GB!
[*]Toshiba have a 1.6 GB Toshiba System Volume that may be something to do with recovery and restore operations.
[*]Toshiba also included a 6.5 GB HDDRECOVERY volume, which is probably the Windows Recovery Volume.
[/LIST]
So you see, I wasn't left with much to work with. According to Disk Utility (System Administration Menu) I allocated:

[LIST]
[*]49 GB to Vista Business in total, to leave some room to maneuver.
[*]2.1 GB to Swap for Linux.
[*]5.5 GB for Ubuntu.
[/LIST]
When I check disk usage after six months of usage, I note that 5.5 GB is recorded as 5 GiB by System Monitor (from the System Administration Menu again). Blame the usual confusion between GB, Gb and/or GiB for the discrepancy. Only 3 GiB is used by Ubuntu and my files. I haven't added much in the way of programs to this, but I haven't removed anything either. I still have OpenOffice, Firefox, and all the other default applications of Lucid Lynx 10.04 LTS, so I would say that based on my experience at least, you need a bare minimum of:

[LIST]
[*]3 GB for Ubuntu.
[*]2 GB for saving files or documents.
[*]2 GB for Swap.
[/LIST]
You can play around with Swap a little, depending on how much RAM you have, and whether or not you use sleep mode. Generally speaking, I have never found Swap to be active on my system. You can also play around with what you want to keep for documents, but 2 GB isn't much these days. I also have an 8 GB SD card that I keep permanently available in the SD Card slot for saving large download files so that I don't worry about running out of space. 10 GB on the hard drive for Ubuntu, including Swap, seems like a fairly safe minimal number to leave you with some elbow room.

---

