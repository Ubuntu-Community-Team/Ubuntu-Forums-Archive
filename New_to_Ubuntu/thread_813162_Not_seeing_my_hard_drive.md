---
title: "Not seeing my hard drive"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Dark006 on 2008-05-30
I'm trying to install Ubuntu 8.04. Every time I select "install" and it gets to the partition part, it doesn't see my hard drive. I try to hit next and it gives an error. 

I've checked the integrity of the disc and it always passes. I've even tried formatting my HDD (with DBAN) with no results.

Any ideas?

---

### Post by quelx on 2008-05-30
in the live CD open a terminal (**Applications** > **Accessories** > **Terminal** 

type
```
sudo fdisk -l
``` <enter>

and post the output

---

### Post by Dark006 on 2008-05-30
I tried that command, nothing was displayed.

---

### Post by gmjs on 2008-05-30
It isn't a Western Digital IDE drive by any chance?

I'm having the exact same problem at the moment.  The BIOS detects the drive and reports the right capacity, but the (debian- in this case) installer doesn't have a driver for it.

I'm using the WD1200JB.

I'm keen to find an answer too!

---

### Post by Duck2006 on 2008-05-30
Can you see the drive in gparted or parted magic? You can run gparted from the ubuntu live cd.

---

### Post by Dark006 on 2008-05-30
> **Duck2006 said:**
> Can you see the drive in gparted or parted magic? You can run gparted from the ubuntu live cd.

Nope, I just tried that. 

**gmjs** I think my HDD is a Westerned Digital. I know its IDE for sure.

---

### Post by gmjs on 2008-05-30
Yeah - I think we are just very, very unfortunate.  There's another thread that says adjusting the jumper settings worked for them, but it hasn't made a difference here.

[http://ubuntuforums.org/showthread.php?t=798956&highlight=WD1200JB]("http://ubuntuforums.org/showthread.php?t=798956&highlight=WD1200JB")

---

### Post by Dark006 on 2008-05-30
I just double checked my HDD, its a 160 Gb Western Digital WD1600JB. I just had XP and SUSE on there before I decided I wanted to switch to Ubuntu.

---

### Post by Dark006 on 2008-05-30
Thank you **gmjs** and **others** that replied. It turns out it was the jumper on the HDD that was affecting it! Thank you all!

---

### Post by gmjs on 2008-05-30
I just wish it solved the problem for me too!

---

