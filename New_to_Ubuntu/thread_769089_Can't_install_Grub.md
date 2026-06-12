---
title: "Can't install Grub"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Twizzle on 2008-04-26
I had Hardy and XP running on a dual boot setup with no problems. I wanted to reinstall XP but keep Hardy and after reading and posting here I saw guides on how to do it so I installed XP as normal (leaving my Hardy install which is on a different disk alone), then booted to the Live CD and did the following:

sudo grub
find /boot/grub/stage1 (it said hd1,2)
root (hd1,2)
setup (hd1) (this is what one guide said to do)
quit

it did not work, so I went back into Live CD and did the above again. This time the output of find..... was hd0,2 so I did:
root (hd0,2)
setup (hd0)

but that did not work so as I did not have much going on in my Hardy install, I decided to reinstall from scratch.

So in goes the Live CD, I manually choose my partitions (keeping the same location for / as the first install and for the swap file) and the only difference being my /home on a different partition. I asked it to to format the partitions leaving my XP install alone.

Installation went ok, so I reboot and.... straight to XP!

Why has Grub not installed and how do I get it back?

---

### Post by gjoellee on 2008-07-26
have you tried reinstalling grub in synaptec?

---

### Post by Alldan on 2008-07-26
Download Super Grub Disk from here:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
It is a livecd so burn it, boot from it and then select to boot from ubuntu partition (safe) or  reinstall original ubuntu grub from ubuntu partition.
I think this is the easiest method
Good luck!

---

### Post by bumanie on 2008-07-26
> sudo grub > root (hd1,0) > setup (hd0) > quitAssuming xp is on the primary drive, first partition and that ubuntu is on the secondary drive, first partition. This can be done from the live cd.

---

### Post by Elfy on 2008-07-26
This is only a guess guys but as the thread is 3 months old and 5 days ago the op was having a problem with twinview - this has probably been sorted :D

---

### Post by bumanie on 2008-07-26
> **forestpixie said:**
> This is only a guess guys but as the thread is 3 months old and 5 days ago the op was having a problem with twinview - this has probably been sorted :D

Didn't even look at the date! Very observant forestpixie.

---

### Post by Elfy on 2008-07-26
> Very observant forestpixieFirst drink - ask me later :lol:

But all power to gjoellee for digging up an old unanswered post and trying to help :D

---

### Post by gjoellee on 2008-07-26
If anyone gets this problem it the person might get it solved here...

---

### Post by Elfy on 2008-07-26
Hundreds of people get the problem - it would appear though that very few know searches still work outside of windows ;)

Though you should know that you can't reinstall grub with synaptic - either the setup from the livecd or using supergrub should do the job.

---

