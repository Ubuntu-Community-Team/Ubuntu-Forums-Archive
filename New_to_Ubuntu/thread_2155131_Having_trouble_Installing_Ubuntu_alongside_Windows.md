---
title: "Having trouble Installing Ubuntu alongside Windows 7"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by jtalley24 on 2013-06-17
Hello all, new to the forums here, and to ubuntu (12.10) and I'm having quite a bit of trouble installing ubuntu alongside windows 7.  First, on windows 7, i shrunk my "C:" partition that had ~650 gb down 550 and left 150 gb of unallocated space for installing ubuntu.  I then booted off the ubuntu install disc, chose the new 150 gb patition for installation of ubuntu, formatted the filesystem as Ext4 journaling, and then mounted it at "/" (first option, this may be the issue).  I chose bootlader dev/sda ATA something 750 gb, not the install location.  Then it installed and said everything was complete, and i tried to restart, and it takes me to a boot menu where when i select ubuntu, it says "gave up waiting for root device".  and i cannot go further (i've tried entering "exit" here after waiting 15 seconds, no luck). I'd like to use ubuntu alongside windows and switch back and forth, so i tried booting into windows 7 and some "disk read error" (i dont think that's the exact quote) and press ctrl alt delete to restart, no luck.  I'm running on the install disc for ubuntu right now, and all help is greatly appreciated.

---

### Post by jtalley24 on 2013-06-17
Bump, I really need help on this one guys.  I have successfuly installed ubuntu on the 150 gb partition.  I can't dual-boot, however.  I start up my computer and when i click f9 to access boot option, I am presented with "efi file" and "hard dive" (not exact) and I go to hard drive, this takes me to a purple screen that i believe is affiliated with my ubuntu install that presents "Ubuntu" "Advanced options for ubuntu"  "windows environment sda/2" (this is a 199 mb partition that existed before ubuntu install process "Windows recovery dev/sda3" (this is the 550 gb),  I believe that is all of them.  Thanks.

---

### Post by newb85 on 2013-06-17
Boot from the install disc again. Install and run Boot-Repair.

---

### Post by jtalley24 on 2013-06-17
@newb85, which install disc are you referring to?  I do not have a windows 7 install disc, my computer came with it preloaded.  All of my data is on the dev/sda3 partiiton (550gb) i just can't boot into it.....

---

### Post by jtalley24 on 2013-06-17
*bump*

---

### Post by jtalley24 on 2013-06-17
Pleaaassseee

---

### Post by newb85 on 2013-06-17
The Ubuntu install disc. 

Forum guidelines say you should wait 24 hours before bumping.

---

### Post by jtalley24 on 2013-06-17
This is an urgent case, but thanks for letting me know

---

### Post by newb85 on 2013-06-17
Did you run Boot Repair from the Ubuntu install disc?

---

### Post by jtalley24 on 2013-06-17
Yes, it seems to have helped as I can get as far as "windows failed to start" and telling me to do repairs by inserting the install disc that I dibt have for windows.  Running boot repair again to see if it detects anything.  I believe it is an issue with my windows partitions being dynamic and not basic when I originally shrank c: . anyway to change them back to basic in Ubuntu?  Thanks again.

---

### Post by oldfred on 2013-06-17
Boot-Repair is not installed in Ubuntu installer, but easily can be added. Or you can download a liveCD with Boot-Repair and other repair tools.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by jtalley24 on 2013-06-17
Thank you for your help, I was able to mount the original necessary install files for windows 7 onto a cd, boot from it and repair back to normal with no data loss, successfully dual-booting.

---

