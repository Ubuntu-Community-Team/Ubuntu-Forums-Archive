---
title: "Can't install XP after installing Ubuntu 7.04"
date: 2007-05-16
forum: Other OS Talk
---

### Post by opiv421 on 2007-05-16
Hey all. I've given Ubuntu a try and enjoyed my time with it however not being able to run the two programs I use the most (WoW and Newsleecher) has led back to XP for the time being... but I can't install it. Windows XP hangs when trying to install at the same spot every time, 22% at the installing network stage. My hardware is working fine, and I haven't changed anything since the last Windows install. The only explanation I can think of is that the previous Ubuntu install screwed something up? I also tried installing Vista but get an error preventing the install from finishing. I've reformatted the disk 3 times (2 quick format 1 regular). Ubuntu installs without a problem. I have no idea what could be causing this. Has anyone had similar problems or know of a solution to this? :confused:

---

### Post by TheMono on 2007-05-16
That is really odd. You didn't change something in your BIOS, did you?

---

### Post by opiv421 on 2007-05-16
Nope, nothing at all. After the first 2 times it froze I started playing with the BIOS setting seeing if enabling/disabling some options would work but have had no luck.

---

### Post by Pollywoggy on 2007-05-16
I think you might have to remove the master boot record in order to install XP.  I understand that you are trying to remove Linux by installing XP over it.

If you are trying instead for a dual-boot system, it is better to install XP first and then Linux.
The command I think you need is:

fdisk /mbr

If Linux is not installed.
Can you still boot Linux?

---

### Post by karellen on 2007-05-17
> **opiv421 said:**
> Hey all. I've given Ubuntu a try and enjoyed my time with it however not being able to run the two programs I use the most (WoW and Newsleecher) has led back to XP for the time being... but I can't install it. Windows XP hangs when trying to install at the same spot every time, 22% at the installing network stage. My hardware is working fine, and I haven't changed anything since the last Windows install. The only explanation I can think of is that the previous Ubuntu install screwed something up? I also tried installing Vista but get an error preventing the install from finishing. I've reformatted the disk 3 times (2 quick format 1 regular). Ubuntu installs without a problem. I have no idea what could be causing this. Has anyone had similar problems or know of a solution to this? :confused:

I had the exactly the same problem. the installer halted at 21-22% detecting netowrk. and I couldn't do anything. I don't think it's a linux related problem. the only I found way to fix this was to remove my ethernet card from the pc when installing xp (yes, it's laughable, but it worked), then plug in after the installation was complete. silly, I know...but it's the only solution that solved this problem for me

---

### Post by mrfelker on 2007-05-17
Since you have already formatted your hard drive several times - format it again and install XP FIRST.  It will install its bootloader in the MBR (don't have a choice with Windows).  THEN install Ubuntu and at the end of the install it will pickup your XP install and install the Ubuntu Bootloader in the MBR overwriting the XP bootloader and you will happily be able to run both OS.  If you need to access NTFS files you can do so from Ubuntu - just run Synaptic and search for "ntfs" and it will install R/W ntfs-3g driver automatically.

Enjoy

---

### Post by bks on 2007-05-17
You might try deleting the partition table and recreating it, to repair the MBR.

---

### Post by smoker on 2007-05-19
> I had the exactly the same problem. the installer halted at 21-22% detecting netowrk. and I couldn't do anything. I don't think it's a linux related problem. the only I found way to fix this was to remove my ethernet card from the pc when installing xp (yes, it's laughable, but it worked), then plug in after the installation was complete. silly, I know...but it's the only solution that solved this problem for me

i've occasionally had this problem reinstalling windows xp on customer's computers (that have never had linux installed), not sure of the exact cause, but disconnecting your internet access (remove cable, card, whatever) usually solves the problem. you can always connect and run the network wizard once the installation is complete as mentioned by karellen.

it maybe that xp doesn't have drivers for that particular network card, i think the last time it happened i had to hunt around for the correct drivers.

best of luck

---

