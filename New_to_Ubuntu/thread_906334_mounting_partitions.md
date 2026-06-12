---
title: "mounting partitions"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-31
i have windows xp installed in dualboot with ubuntu8.04.and these days,i am proud to say that i use ubuntu mostly ,it is way too faster and prettier(looks so good with all that eyecandy,compiz,emerald,GTK,etc.).but yesterday,i was working with autocad on xp.i was just playing around with a few things,and i just messed up the xp.i restarted and popped in the xp installation cd ,but booted from the hard disk into xp,so as to repair my xp.but,i saw nothing but a blank screen before me,and xp could not take over after i chose it in the GRUB.so something is wrong with xp.then i restarted and booted into ubuntu,but ubuntu did not mount any of the partitions,supposedly because they were not unmounted by xp,due to an unclean shutdown.how do i fix this,i mean i need ubuntu to mount all those partitions which xp failed to unmount.definitely,i can't boot into xp since it has gone haywire.also,is there a way to repair xp,without booting from the xp disk(because an installation of xp would wipe out my ubuntu).

---

### Post by aloshbennett on 2008-08-31
What error do you get when you try to mount manually from the command prompt?
> mount /dev/sda1
assuming there's an entry for all the partitions in /etc/fstab

---

### Post by jemate18 on 2008-08-31
> **stonecoldjha said:**
> i have windows xp installed in dualboot with ubuntu8.04.and these days,i am proud to say that i use ubuntu mostly ,it is way too faster and prettier(looks so good with all that eyecandy,compiz,emerald,GTK,etc.).but yesterday,i was working with autocad on xp.i was just playing around with a few things,and i just messed up the xp.i restarted and popped in the xp installation cd ,but booted from the hard disk into xp,so as to repair my xp.but,i saw nothing but a blank screen before me,and xp could not take over after i chose it in the GRUB.so something is wrong with xp.then i restarted and booted into ubuntu,but ubuntu did not mount any of the partitions,supposedly because they were not unmounted by xp,due to an unclean shutdown.how do i fix this,i mean i need ubuntu to mount all those partitions which xp failed to unmount.definitely,i can't boot into xp since it has gone haywire.also,is there a way to repair xp,without booting from the xp disk(because an installation of xp would wipe out my ubuntu).

What exact partitions do you want Ubuntu to mount?

___________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by stonecoldjha on 2008-08-31
well i tried using
sudo mount/media/sda1
and it said that i should force it to mount,and i forced it and other drives to be mounted.so that problem is now solved.how do i repair xp,without putting ubuntu installation at stake?

---

### Post by jemate18 on 2008-08-31
> **stonecoldjha said:**
> well i tried using
sudo mount/media/sda1
and it said that i should force it to mount,and i forced it and other drives to be mounted.so that problem is now solved.how do i repair xp,without putting ubuntu installation at stake?

I assume you have dual boot XP and Ubuntu.

After installing Ubuntu, it has written GRUB in the MBR(if you didnt choose where GRUB will be installed).

How ever, if you try to repair XP using the CD, then it will rewrite MBR and the GRUB which is the boot loader of Ubuntu will be erased. You should back up GRUB and restore it after repairing windows XP.

___________________________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by mikewhatever on 2008-08-31
Why would reinstalling XP wipe Ubuntu? If XP is on sda1, that's the only partition to be formatted.:confused:

---

### Post by jemate18 on 2008-08-31
Check this link to restore GRUB after repairing WINDOWS XP

> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

_________________________________________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by stonecoldjha on 2008-08-31
but how do i do that?yesterday i downloaded an image of super grub disk,but don't know what it is,and if it can be of any use here.how will i restore grub after repairing windows?

---

### Post by jemate18 on 2008-08-31
> **stonecoldjha said:**
> but how do i do that?yesterday i downloaded an image of super grub disk,but don't know what it is,and if it can be of any use here.how will i restore grub after repairing windows?

Click the link on my above post..

---

### Post by solaceinsilence9 on 2008-08-31
> **mikewhatever said:**
> Why would reinstalling XP wipe Ubuntu? If XP is on sda1, that's the only partition to be formatted.:confused:

Depends if you choose to reinstall XP and reformat the entire hard drive. If you choose that option it will wipe all your partitions on the hard drive. If Im not mistaken, the install CD has a partition manager on it so you can choose which partition you want. Also like mentioned above, Windows will change the Master Boot Record and get rid of the old one which has the GRUB menu installed. So even though you Ubuntu partition is still *there* you wont be able to boot into it.

---

### Post by solaceinsilence9 on 2008-08-31
> **stonecoldjha said:**
> but how do i do that?yesterday i downloaded an image of super grub disk,but don't know what it is,and if it can be of any use here.how will i restore grub after repairing windows?

...click the link above. Thats why you use the Desktop/Live CD. Once you boot from the CD it will let you run Ubuntu from the CD then you use terminal to overwrite your existing MBR and replace with the one that has GRUB on it. Once you do that youll be able to reboot your machine and the GRUB loader will come up.

---

