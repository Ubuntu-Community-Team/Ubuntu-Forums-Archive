---
title: "Restart fails with ubunti 8.0.4?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by zuheyr on 2008-05-04
Hello,
I just updated from Ubuntu 7.10 (I think) to 8.0.4 yesterday.
(I was *extremely* happy with 7.10 and THANK YOU GUYS). 
(uname -a info:
~$ uname -a
Linux zuheyr-laptop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux )

All went ok with the upgrade but I have 2 problems:
1-When it wakes up from "hibernate" or restart, Ubuntu hangs.
I have to reboot. This had never happened before.

2-I had to remove the proprietary nvidia gl driver after a test download because of having black windows. BUT I was not using it with version 7.
So this is probably not related to version 8.  
 
Thank you for reading.
Again THANKS to all who are involved in this great Linux version.
Regards, Zuheyr

---

### Post by drsox1899 on 2008-05-04
It seems that upgrades don't work as well as new installs.  Do you have a separate /home partition ?  If you do then you might want to try a new install instead.

---

### Post by zuheyr on 2008-05-04
Hi thank you!

No, Unfortunately no...

Regards and thanks.
Zuheyr

> **drsox1899 said:**
> It seems that upgrades don't work as well as new installs.  Do you have a separate /home partition ?  If you do then you might want to try a new install instead.

---

### Post by drsox1899 on 2008-05-04
> **zuheyr said:**
> Hi thank you!

No, Unfortunately no...

Regards and thanks.
Zuheyr

If all else fails, then copy your /home partition to some other drive (usb) and restore afterwards.

---

### Post by zuheyr on 2008-05-05
> **drsox1899 said:**
> If all else fails, then copy your /home partition to some other drive (usb) and restore afterwards.

Thank you for your help!

In addition to the other problems I mentioned I also noticed that if I do not use the computer for a while, it hangs...

I was wondering if these bugs will be fixed soon or should i really delete everything and reinstall 7.10?

Also, how can I install version 7 in a more clever way so that several ubunti versions can live together? I remember when I was installing, from a cd I made, it did not ask me for the partition...?


Many thanks and kind regards, Zuheyr

---

### Post by drsox1899 on 2008-05-05
> **zuheyr said:**
> Thank you for your help!

In addition to the other problems I mentioned I also noticed that if I do not use the computer for a while, it hangs...

I was wondering if these bugs will be fixed soon or should i really delete everything and reinstall 7.10?

Also, how can I install version 7 in a more clever way so that several ubunti versions can live together? I remember when I was installing, from a cd I made, it did not ask me for the partition...?


Many thanks and kind regards, Zuheyr

I haven't upgraded a Ubuntu install yet, but I read lots of forum posts that say that fresh installs are better than upgrades.  The reason seems to be that apps added by the user can mess about with the installed dependency sub programmes so that an upgrade doesn't always have the correct base to work with.

Also, apps installed not through the package manager are best reinstalled rather than upgraded.

Personally, I have kept my 7.10 as my "working" install and am looking at 8.04 on my experimental PC.  I'm not going to switch to 8.04 until a few months have passed.

If you have the option, I would backup all the /home files that you want to keep and do a complete fresh install.  Select to use the entire disc and let the installer work out what to do. (If you have a Windows partition then it gets more complicated).

I would start by reinstalling 7.10 from scratch, then add a new install of 8.04.  The installer will work it all out.  Then copy back your /home files into the 7.10 /home directory.

If you want the installs to share the /home directory, then ensure that a separate partition is made for /home and don't format it when you do the second install.  You will have to tell the installer to use the same partition for /home in your second install.

Personally, I would keep the installs completely separate until you decide what to do about a permanent install.

Selecting between the installs is easy at boot up time, but you might want to go into the grub menus to rename the installs so that you know which is which.  I had 6 installs on my experimental PC and kept starting the wrong one !

As you learn more about this, you will get more confident in managing the install process.  It's just different to Windows - not really more difficult.

---

### Post by Michl on 2008-05-05
The upgrade path from 7.10 was very smooth for me on three
computers.  What you are describing are not bugs in Hardy,
I would say, but something odd about the way you installed.
ALso, I found the kernel puzzling.  24-16 is the stable
Hardy kernel.

---

### Post by zuheyr on 2008-05-08
> **Michl said:**
> The upgrade path from 7.10 was very smooth for me on three
computers.  What you are describing are not bugs in Hardy,
I would say, but something odd about the way you installed.
ALso, I found the kernel puzzling.  24-16 is the stable
Hardy kernel.

Thank you guys, 
I have re-installed the 7.10 and all is perfect. 

It i svery possible I installed strangely the first time, though for the upgrade, the upgrade manager did the whole job, so I fail to see what could I have done wrong...?

I ordered the 8.0.4 cd and in some weeks I will try to install 8.0.4 as well.

Many thanks again for the help,
Regards, Zuheyr

---

