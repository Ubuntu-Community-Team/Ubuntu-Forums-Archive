---
title: "[SOLVED] Completing the conversion"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by NewNerd99 on 2008-09-19
Hi all,
      After using 8.04 for the last month on a dual boot system (Vista) I'm ready to take the plunge and convert!!
   At the moment Ubuntu runs on a small (5Gb) partition, Vista occupies the remainder of my massive 60Gb laptop HDD.
   I would like to know if there is a way I can reclaim/format the partition in which Vista resides or do I have to reinstall Ubuntu as a fresh install?
   I have had a search but nothing came up on these forums. If I have missed the thread I would appreciate a link to it.

Cheers
Chris

---

### Post by TenPlus1 on 2008-09-19
You *could* boot from your Ubuntu Live CD and use GParted to format the Vista partition as Ext3 and mark it as a /home partition so that Ubuntu will automatically use it for all your files on next reboot... (Copy contents of existing /home onto it before reboot tho)...

---

### Post by indytim on 2008-09-19
If you follow the advice above, also modify your fstab to reflect the new location of /home.

IndyTim

---

### Post by rolnics on 2008-09-19
> **indytim said:**
> If you follow the advice above, also modify your fstab to reflect the new location of /home.

IndyTim

I don't know how much knowledge the op has gain in his first month of Ubuntu and I don't want to put him down, but fstab still confuses the hell out of me and I've been using Ubuntu for over a year!

If you want to go with this option take a look at [this tutorial]("http://www.psychocats.net/ubuntu/separatehome") to create the new partition and sort out fstab file.

@op may I suggest you go with the easier option of a fresh install and create a separate /home partition as you go. 

Which ever option you take remember the number one rule. Backup any data that you want to keep!

---

### Post by NewNerd99 on 2008-09-19
Thanks guys for the replies.
As I have backed up anything of value to an external HDD, from windows as well as Ubuntu, the clean install may be the least taxing way to go.

Cheers
Chris

---

