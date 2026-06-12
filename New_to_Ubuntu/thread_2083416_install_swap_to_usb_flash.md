---
title: "install swap to usb flash"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by crip720 on 2012-11-12
I am going to install Ubuntu 10.04 on a Toshiba A20 satellite laptop.  This is an old laptop with only 512mb ram.  During install, can I install the swap partition to a USB flash drive?  I want to do this, so when Ubuntu needs more ram it can use the flash drive instead of the hard drive for swap.  Will this work, and will the speed be faster, than having swap on the hard drive[4200rpm IDE].  There does not seem to be an option to boot from USB in the Bios.  Thank you for any ideas.  Colin

---

### Post by Cheesemill on 2012-11-12
This isn't a good idea, flash drives are ***a lot*** slower than hard drives.

---

### Post by Lars Noodén on 2012-11-12
It's doable but much slower.  Flash is very, very slow to write and not much better for reading.  What are your options about adding more RAM?  One of the best ways to perk up old machines is adding more RAM.

---

### Post by cwsnyder on 2012-11-12
When you install for a boot from a flash thumb drive, you are normally directed to use swap on the hard disk or no swap at all, because using swap on a flash memory will kill the flash memory in a very short period with all of the reads and writes.  With your laptop, the recommendation would normally be to use a 1G or smaller swap partition on your hard drive.

You could also use the Plop boot manager on CD to boot from a thumb drive as an alternative, if you can boot from CD.  This works even if your BIOS does not support booting from thumb drive.  You might even consider using a USB hard drive and Plop boot manager to boot from an external drive.

---

### Post by crip720 on 2012-11-12
Thanks for your reponses.  Was just an idea I had.  I will mark this as solved.

---

### Post by Slim Odds on 2012-11-12
> **Cheesemill said:**
> This isn't a good idea, flash drives are ***a lot*** slower than hard drives.
For WRITEs they are slower... for random reads they are a lot faster.

---

