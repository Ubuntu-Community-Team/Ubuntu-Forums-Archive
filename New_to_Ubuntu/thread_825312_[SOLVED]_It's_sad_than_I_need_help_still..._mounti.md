---
title: "[SOLVED] It's sad than I need help still... mounting windows partition"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by 449 on 2008-06-10
All I want to do is be able to access the files on my windows partition from Ubuntu. I've tried everything I could find ,but I've had no luck successfully mounting it. Just ask me to post more info if you need it; because I have no clue what it would be.

:confused:

Thanks for the help!

---

### Post by me208 on 2008-06-10
you might have tried this but
```
sudo mount -f /dev/"Windoze"
```
where "Windoze"is the dev loaction of the NFTS partition

---

### Post by logos34 on 2008-06-10
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Joeb454 on 2008-06-10
If you want to Automount it - May I shamelessly suggest the link at the bottom of my sig?

I use it to automount my Vista partition (loads of music, it just saves space this way :p)

---

### Post by lswb on 2008-06-10
Are you running a dual boot system, with different partitions on a single hard drive? 
Is your windows partition FAT32 or NTFS? What have you tried so far? I guess you know that the mount command must be run with sudo or from a root shell, and the same goes for editing fstab. Have you looked at the man pages for mount and fstab? Do you know what device is assigned to the windows partition in the /dev directory? 

I guess this seems like a lot of questions, but post back with what you do know.

---

### Post by 449 on 2008-06-10
> **Joeb454 said:**
> If you want to Automount it - May I shamelessly suggest the link at the bottom of my sig?

I use it to automount my Vista partition (loads of music, it just saves space this way :p)

Thanks ;)

---

