---
title: "hard drive missing suddenly"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-28
So when i first installed winxp i did not have the drivers to partition more than 128gb of space, leaving the other 32gb unpartitioned. it was onto this i installed ubuntu, so in ubuntu showed my 128gb partition and /fileserver on 32gb area. Until about yesterday. the 128gb part just disappeared!i need to be able to access it w/o restarting the computer and going to winxp, because from the winxp i cant access the ubuntu files!

---

### Post by riven0 on 2008-04-28
Does Ubuntu recognize the hard drive anymore? What is the output of this command: **sudo fdisk -l**

---

### Post by Zopiac on 2008-04-28
> **riven0 said:**
> Does Ubuntu recognize the hard drive anymore? What is the output of this command: **sudo fdisk -l**

well im on another comp. now, because im installing 8.04 :) but i ,anaged to open a terminal window also entered that command; i cant copy/paste and dont want to type the whole thing so here goes:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
(line)
(line)
(line)
(blank)
  Device  Boot  Start       End        Blocks     Id  System
dev/sda1   *        1     16709    (really big #)  1 HPFS/NTFS
dev/sda2        16710     19457           (big #)  7 LINUX
zopiac@zopiac:~$

that enough? obviously it detects it...but thats all i can make out :P

EDIT: Spacing is mangled, boot aligns with * and a blank, start aligns with 1 and 16710, end is 16709 and 19457, blocks the #s,  id 1 and 7, and system with hpfs/ntfs and linux

(i think the 1 and 7 are right...forgot to add them earlier)

---

### Post by Tatty on 2008-04-28
Its still sitting there happily.  Can you post your /etc/fstab

---

### Post by Zopiac on 2008-04-28
> **Tatty said:**
> Its still sitting there happily.  Can you post your /etc/fstab

uhm not really. should i look for anything specific in it?    i think my comps gonna restart soon because of the installation, so idk.

---

### Post by Tatty on 2008-04-28
oh are you re-installing 8.04 onto the machine youre struggling with?  If so then it will probably sort it out for you.  If not then post back

---

### Post by Zopiac on 2008-04-28
> **Tatty said:**
> oh are you re-installing 8.04 onto the machine youre struggling with?  If so then it will probably sort it out for you.  If not then post back

not reinstalling, but yeah :P restarting now....

...BOOM its there. However, it says i dont have privileges to mount the volume.




what

---

### Post by Zopiac on 2008-04-29
bump, i need answers!

---

### Post by Zopiac on 2008-04-29
So this is what it says when i try to open my hard drive.

Cannot mount volume.

You are not privileged to mount the volume 'Zopiac128_160'.

---

