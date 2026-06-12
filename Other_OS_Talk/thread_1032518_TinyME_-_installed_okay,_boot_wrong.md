---
title: "TinyME - installed okay, boot wrong"
date: 2009-01-06
forum: Other OS Talk
---

### Post by Ampi on 2009-01-06
I installed TinyMe on one of my partitions in my very old computer (choose TinyMe out of the Sticky posted above).

I used the LiveCD and TinyMe installed just fine. Then it says I should take out the LiveCD and restart. I do so.

This is my message:
> 
kernel (hdb1,0)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hdb1 acpi=on resume=/dev/hdb5 splash=silent vga=788
Error 15: File not found
Press any key to continue...


From here it is impossible to continue. Either I press a key where I get a nongraphical interface to choose my partitions (linux, linux-abcd (some letters), failsafe). All three give me the same Error 15.

The LiveCD itself works perfectly well. So I have no clue at all what to do. 

Any ideas?

---

### Post by Hallvor on 2009-01-06
> **Ampi said:**
> I installed TinyMe on one of my partitions in my very old computer (choose TinyMe out of the Sticky posted above).

I used the LiveCD and TinyMe installed just fine. Then it says I should take out the LiveCD and restart. I do so.

This is my message:


From here it is impossible to continue. Either I press a key where I get a nongraphical interface to choose my partitions (linux, linux-abcd (some letters), failsafe). All three give me the same Error 15.

The LiveCD itself works perfectly well. So I have no clue at all what to do. 

Any ideas?

See this thread. Perhaps is helps.

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

Don`t give up. I have TinyMe running on a spare computer, and it is a fantastic little distro.

---

### Post by Ampi on 2009-01-06
I don't give up that easily! (If I would, I wouldn't have three Linux distros ;))

Anyway, I don't understand entirely. The thread does seem to be the answer to my problem, I just cannot translate it into something I understand :(.

The thread suggests a text-based grub install from cd. Then I just follow the simple steps (language settings...ESC...partition check...NO formatting...don't install base system...)

I think I can manage the steps, I just don't know how to start the **text-based grub install**.

I already had problems figuring out the CD, but I just clicked on LiveCD and once it was done asking me questions :) I clicked the 'install TinyMe' on the desktop. That's where my previous post starts. 

I really want this distro on my old computer, so if you could give me some explanation for dummy's I'd be very happy :D

---

### Post by Ampi on 2009-01-06
got new info...

I found the grub text-based install, at least I think so...

Did everything that was suggested a couple of posts later within the thread of the link Hallvor posted. 
So I changed all my (hd1,0) to (hd0,0). Then booted again and the Error disappeared!! GREAT

But then
> 
/dev/hda1 contains file system with errors, check forced.

--- check is being done---

FAILED
*** An error occured during file system check.
*** Dropping you to a shell. The system will reboot
*** when you leave the shell.


I installed TinyMe on /dev/hdb1 (/dev/hda1 contains my home directory, didn't even touch that partition, I have that partitioned for a exactly this reason!)

So now I still have no clue what to do, but even worse, I'm scared I'm going to loose my home-dir.

---

### Post by Hallvor on 2009-01-07
> **Ampi said:**
> got new info...

I found the grub text-based install, at least I think so...

Did everything that was suggested a couple of posts later within the thread of the link Hallvor posted. 
So I changed all my (hd1,0) to (hd0,0). Then booted again and the Error disappeared!! GREAT

But then


I installed TinyMe on /dev/hdb1 (/dev/hda1 contains my home directory, didn't even touch that partition, I have that partitioned for a exactly this reason!)

So now I still have no clue what to do, but even worse, I'm scared I'm going to loose my home-dir.


OK. I assume you get a CLI after that message. Type ```
su
``` and your root password. Then try typing ```
fsck /dev/hdb1
``` and press enter to try repairing the file system and follow any on screen instructions from there. After completion, press control+D and the system should reboot as into normal mode.

---

### Post by Ampi on 2009-01-07
I DID IT!!!!!!!!!!!!!!!!!!! YIPPI!!!!!!!!!!!

Sorry for that :)

Anyway, I just found the solution you posted somewhere else on the web before, and it worked! So if I didn't, you would have helped too. Thanks!

This is my first post from TinyMe!

---

### Post by Hallvor on 2009-01-07
Congratulations! Hope you enjoy it as much as I did. :)

---

