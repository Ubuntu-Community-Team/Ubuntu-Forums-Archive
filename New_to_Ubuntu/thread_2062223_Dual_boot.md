---
title: "Dual boot"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by Heyutwo on 2012-09-24
I installed Ubuntu on an older Vista Dell computer (AMD) partitioned for three logical drives and one additional physical drive (1) from a defunct machine for storage use only.  I created a 26 G empty area on the primary drive (0) for the Ubuntu install.  Things went well except that although I chose “alongside” the  dual boot menu never appeared and machine boots to Ubuntu all the time.  The C: partition with the Vista OS is ok and I can even access it with Ubuntu and move files with no problems.  I want that dual boot feature on my network where the machine is configured with Vista to cohabit with five other machines.  I have trouble with configuring Ubuntu into the network for two unrelated reasons.   
 Actually, I really want to be able to boot to C: drive in Vista occasionally and despite my growing admiration for Ubuntu, I still want to be able to revert (on that machine) to Windows.  
 My question is how do I go about getting that dual boot feature now without putting my successful Ubuntu installation at risk.  I've done lots of tweaking on it and would hate to lose it.  I suspect that what might have happened ??? is that the Ubuntu install selected the (1) drive for the dual boot instead of the (0) drive.  Being an old (really old) computer tech I have a sad history of messing with master boot records and hate to get into that again.  Besides, I only understand hardware and leave software for smarter fellows.
I had already reinstalled after removing the extra (1) drive to avoid confusing the install wizard.

---

### Post by Pand5461 on 2012-09-24
Looks like the bootloader is misconfigured. 
In a similar situation, I ran ```
sudo update-grub
``` and it found Windows loader and added it to the boot menu.

---

### Post by Heyutwo on 2012-09-24
Thanks for your reply.  I tried that and;
 

 It did put an update on the screen which had as the last line:
 Found Windows Vista (loader) on /dev/sda3
 I then tried it but still had no display selection on the screen and it went to Ubuntu again so that didn't change it.   
 

 But if the first device is physical drive 0 and the dvd drive is the second then that would put the Windows loader on the drive that I removed thinking it was the cause of the problem, so I would need to get that loader on the first physical sata drive and I don't know how to do that...yet
 I'm out of my element here.  
  I think I need to get with it with Ubuntu terminal commands to learn how to do that.  
 If you or anyone gives me a terminal command or a way to do that I would definitely not look for someone to blame if I really screw it up.

---

### Post by oldfred on 2012-09-24
You should have a good backup especially of /home as all your user settings are in /home.

If you want a gui, you can download this to your liveCD or USB.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Or manually:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

