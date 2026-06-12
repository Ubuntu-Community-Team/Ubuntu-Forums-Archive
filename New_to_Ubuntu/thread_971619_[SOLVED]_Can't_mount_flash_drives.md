---
title: "[SOLVED] Can't mount flash drives"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-05
I cannot mount flash drives.

For one flash drive (Memorex UFD), I have attached screen shots of the errors etc. I don't have this problem, mounting the flash drives, when I'm using my other Ubuntu machine so I don't understand what I did wrong.  I checked the "Users and Groups" and all my "User Privileges" are checked.

gparted_View.png (view using partition editor):
[INDENT]Shows that the "Memorex UFD" has:
[INDENT]filesystem: Fat16
Mountpoint: /media/cdrom0[/INDENT][/INDENT]

Cannot_mount_volume-error.png (error on trying to mount {or just inserting} the Memorex UFD:
[INDENT]Shows the error when the flash drive in inserted or when I try to mount it.[/INDENT]

media_File_Browser.png (browser view, using 'sudo nautilus'):
[INDENT]Shows the mount point, among others, of the flash drive[/INDENT]

Cannot_mount_volume_other.png (error on trying to mount a different flash drive:
[INDENT]Shows the error when I install or try to mount a different flash drive.[/INDENT]

Please help me with this problem.  I don't know what I have done that makes each "computer setup" that prevents me from administering the flash drives on one machine with no problems on the other.

Also, why is there three indicated cdrom drives in /media (cdrom, cdrom0, cdrom1) when the computer has only one?

---

### Post by pzs on 2008-11-05
We might need a bit more information. What does it do when you insert a flash drive? What is the output at the bottom of dmesg just after the drive has been inserted?

---

### Post by boof1988 on 2008-11-05
> **pzs said:**
> We might need a bit more information. What does it do when you insert a flash drive? What is the output at the bottom of dmesg just after the drive has been inserted?

I was editting the OP when you posted this... Sorry.  I hope the info gives what you need.  Thanks for the help.

---

### Post by pzs on 2008-11-05
Have you tried using the advice from this thread:

[http://ubuntuforums.org/showthread.php?t=574988](http://ubuntuforums.org/showthread.php?t=574988)

---

### Post by boof1988 on 2008-11-05
> **pzs said:**
> Have you tried using the advice from this thread:

[http://ubuntuforums.org/showthread.php?t=574988](http://ubuntuforums.org/showthread.php?t=574988)

Thanks for the link... I'm looking at it right now.

---

### Post by boof1988 on 2008-11-05
Hey Pzs,

Thanks so much for the link/help.  The problem seemed to be the same one as mine (I installed using a USB as well).

Thanks again,

:guitar:

---

### Post by pzs on 2008-11-05
No problem :)

For future reference, I solved this problem by simply typing the error message into the search box for the forums. The thread I posted was the top match. I solve almost all my Linux problems this way.

---

### Post by boof1988 on 2008-11-05
> **pzs said:**
> No problem :)

For future reference, I solved this problem by simply typing the error message into the search box for the forums. The thread I posted was the top match. I solve almost all my Linux problems this way.

I have a very difficult time finding the info I need.  I search for stuff and often don't find the right stuff.  Maybe I don't know the right words to use in the search.

I tried searching after you posted this and I still have a hard time finding things.  I assure you it is not laziness, some people (like and including me) find it very difficult and confusing when searching and sorting through the information.

Thanks again for your help and I'm trying to get better at not being confused.

:guitar:

---

