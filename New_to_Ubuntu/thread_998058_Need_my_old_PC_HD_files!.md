---
title: "Need my old PC HD files!?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by RickFAA on 2008-11-30
Hi!
My old (2003) Windows XP sp1 and motherboard died, so I build a new one.
I have a AMD 6000(3.0GHz), 2Gb ram and 250G HD.
I put in 8.04LTS and it works good.

But - I need to put my old files in to new HD.
How to I do this?
(My old HD was 80G but had 10g's of files)

Thanks,
RickFAA

---

### Post by oilchangeguy on 2008-11-30
install the old drive in the new computer as a slave. make sure to change the jumper setting. and copy your files to your new drive.

---

### Post by mapes12 on 2008-11-30
> install the old drive in the new computer as a slave. make sure to change the jumper setting. and copy your files to your new drive.

and make sure your BIOS is set to boot from your UBU drive because your windoze HDD may still have an in tact bootable MBR which means your system may get confused where to boot.

If in doubt, boot from a Ubu Live CD, then mount the windoze HDD and move your files using the command line to your Ubu /home directory.

---

