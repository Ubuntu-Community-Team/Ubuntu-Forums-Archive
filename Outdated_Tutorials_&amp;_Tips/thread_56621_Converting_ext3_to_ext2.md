---
title: "Converting ext3 to ext2"
date: 2005-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Erucolindo on 2005-08-13
I had a hard time finding out about this subject so i decided to share what i have learned. This worked perfect for me but you're probibly safer of making a backup and create a new partition.

First, make sure the partition you are about to convert isn't mounted, that can cause data-loss!

Now, open up a terminal and type:

```
sudo tune2fs -O ^has_journal /dev/hdxx
``` 

This turns off the journalizing flag on the partition.
Next thing to do is run e2fsck:

```
sudo e2fsck /dev/hdxx
``` 

Since the filesystem no longer has a journal the check assumes the filesystem is ext2 and cleans it up and, voila, you got yourself a ext2 partition  :) 

Note: the e2fsck took a loooong time for me.


PS. I can't take credit for this, it was someting i found on the web (can't remember were though.

---

### Post by novice_forever on 2007-02-23
Nice hint, but I also had to edit /etc/fstab (ext3 -> ext2) to be able to log in again.

---

### Post by Barko1 on 2008-12-12
Bumping an old thread for another newb question, so forgive me if I broke a rule...

I wish to switch to ext2 for increased performance on an old comp.  I'm not sure how to unmount the harddrive.

I am only running fluxbuntu, and apparently I can't unmount while I'm running it.  When I exit the GRUB loader to the command line, no commands go recognizes?

do I need an ubuntu live CD if I wish to unmount the only hard drive I have? 

thanks

edit:
ok i just figured it out as soon as I finished typing it.  I need to log in as recovery mode.


edit2:
sorry, according to drive info it still says I run an ext3 system.  is that normal?

---

### Post by Xbehave on 2009-03-07
you need to edit /etc/fstab at the same time as doing this. you should definatly do it from a livecd though.

---

