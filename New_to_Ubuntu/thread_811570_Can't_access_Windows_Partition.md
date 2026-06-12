---
title: "Can't access Windows Partition"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by KnavishClout on 2008-05-29
I try to boot into my Windows Partition by selecting it from GRUB, but my PC just restarts.  It wouldn't be a problem, but I can't access that partition from Ubuntu.  Maybe because it is NTFS?  Does anyone know how I can access my files?

---

### Post by gdzsi on 2008-05-29
with (k)ubuntu 8.04 you should be able to mount ntfs partitions

---

### Post by Aesir09 on 2008-05-29
yes you need to mount the drive.

you should be able to do this by going to **places-->hard drive name**(click)

once found its under /media

---

### Post by KnavishClout on 2008-05-29
I apologize for not being specific.  When I click on the partition under "places" it comes up with an error message and says that it is unable to mount.

I'm using the Hardy Heron 64 bit release.

The windows partition is 32 bit Windows Server 2008.

Thanks!

---

### Post by bumanie on 2008-05-29
Could you post the message please. If we can see the message, it will be easier for someone to help you.

---

### Post by KnavishClout on 2008-06-10
I apologize about the delay, i have been away from the system for a few days.

Shen I click on Places>32.0 GB Media I get an error message that says "Cannot mount Volume".  When I click on details it says:

"$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Savely Remoe Hardware' icon in the Windows taskbar then shutdown Windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line: mount-t ntfs-3g /dev/sda1 /media/disk-0 force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1/media/disk ntfs-3g force 0 0

I'm lost.:confused:

---

### Post by Nchalada on 2008-06-10
I had this problem with my main windows drive, all i had to do was put that mount command (copy and paste) in a terminal

Tony

---

