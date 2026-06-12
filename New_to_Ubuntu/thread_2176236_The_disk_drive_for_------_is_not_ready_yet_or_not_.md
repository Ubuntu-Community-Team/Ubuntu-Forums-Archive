---
title: "The disk drive for /------ is not ready yet or not present  - COMPLETE BEGINNER"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by ib2 on 2013-09-23
Hey. Im an absolute beginner, and when i mean beginner, COMPLETELY.

I searched through forums, but all i've got back is really complex answers which I have no idea on how to follow.

Basically loading up two Hard-drives and the error 'The disk drive for /home is not ready yet or not present' appear.

From here I have no clue what to do.

If anyone can give me real detailed instructions, i'd be more thank appreciative.

---

### Post by whitesmith on 2013-09-23
Sounds like you elected for a partitioned install with / on one partition (HDD) and /home on the other. Whether or not my guess is right, run the live CD, select **try**, then open a terminal and type: ```
sudo fdisk -l
``` Post the output here so we can tell what's going on. And welcome, by the way!

---

### Post by Bashing-om on 2013-09-23
ib2; Hi ! Welcome to the forum .

Panic not. Just proceed in a calm and orderly fashion. This is ubuntu, all things are fixable !

Right now we do not know the exact source of the problem. Let's do some exploratory investigation, taking note of any errors exactly. The system is really good about indicating wherein a problem lies. - once one asks the right questions of it.

Made any recent changes to your system ?
Can you boot into "recovery mode" from grub's boot menu ?
How about booting to a text login ?
Have you ran ubuntu's check file system utility "fsck" ? (must be done from an outside source [liveDVD].

Realizing you are an "new user", the above may appear daunting questions, If you can not comply we are here to guide and assist. We need to insure your file system is intact; and
Boot files are intact.
What version and distribution are you running , to allow us to further direct your actions ?

It is as simple as that .. the above will provide what we presently need to know.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by ib2 on 2013-09-23
> **Bashing-om said:**
> ib2; Hi ! Welcome to the forum .

Panic not. Just proceed in a calm and orderly fashion. This is ubuntu, all things are fixable !

Right now we do not know the exact source of the problem. Let's do some exploratory investigation, taking note of any errors exactly. The system is really good about indicating wherein a problem lies. - once one asks the right questions of it.

Made any recent changes to your system ?
Can you boot into "recovery mode" from grub's boot menu ?
How about booting to a text login ?
Have you ran ubuntu's check file system utility "fsck" ? (must be done from an outside source [liveDVD].

Realizing you are an "new user", the above may appear daunting questions, If you can not comply we are here to guide and assist. We need to insure your file system is intact; and
Boot files are intact.
What version and distribution are you running , to allow us to further direct your actions ?

It is as simple as that .. the above will provide what we presently need to know.
[INDENT][INDENT]where there are solutions there are no problems
[/INDENT]
[/INDENT]


Thanks a lot for the reply. I will reply back to this thread when i'm back on the computer with as much detail as I can. Check back to this thread tomorrow please.

---

