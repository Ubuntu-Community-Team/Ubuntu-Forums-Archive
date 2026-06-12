---
title: "Lost Grub/Windows after Power Failure"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by KSabre93 on 2011-11-23
I have a very similar problem. I would create my own thread but I'm new to the site and haven't figured out how to. I have a laptop with Windows Vista and about a month ago created a partition for Ubuntu. I messed up a few things with Ubuntu (system settings etc.) and being a noob with Linux decided to start from scratch and reformat the Ubuntu partition for a re-install. However, when the formatting was 42% done I accidentally tugged out the power lead which caused the laptop to instantly power off (battery problems). When I restarted my machine I got the Error: no such partition. grub rescue > command prompt. This sucks because I know I have an unharmed partition with a perfectly functional Windows operating system that I can't get to because Ubuntu has decided to take over my machine with its grub booter or whatever it is. The frustration is almost too much and I'm not a great computer wiz. I'm currently using Ubuntu via the bootable USB drive I used to install it in the first place.

---

### Post by drs305 on 2011-11-23
KSabre93,

Welcome to the Ubuntu Forums.

I've moved your post to its own thread. Normally you go to the forum you are interested in posting in and click the "New Thread" button at the top left of the screen.

To address your problem:

Since you are already in Ubuntu, if the Windows boot flag and folders/files are intact, you can partially install another bootloader to restore Windows.

Open a terminal and run the following. There will be messages stating that 'lilo' is not configured - don't worry about them.

I will assume you have one drive and it is 'sda'. If it is designated something else, change the command:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Reboot and hopefully you will have Windows back.

---

### Post by Mark Phelps on 2011-11-23
The info provided by drs305 should be sufficient to get you booting again.

However, if it does not work, you can then try the steps outlined in the boot-repair link below:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

