---
title: "[SOLVED] Transferring data to new drive"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by TheSlipstream on 2008-08-08
Not quite an Absolute Beginner any more, but this place gets more views, so what the hey.

Anyway, so my laptop HD is a 40 gig/4200rpm disk. Lameness. Me want new, 120 gig/5400rpm disk. So here's the question, can anyone tell me how I can transfer all my info from my old HD to my new one? Unfortunately, this laptop only has a CD-RW burner, but I do have access to another laptop with a DVD-RW drive that I could use if necessary. My installation has reached critical mass with about 25 gigs taken, but if I need to, I'll burn off as many CDs as it takes.

Cheers,
Slip

---

### Post by TheSlipstream on 2008-08-09
Never posted a topic on this section that didn't require a bump.

---

### Post by ercferret18 on 2008-08-09
um... try this... make sure both hard drives are in the same computer, and then, using gparted, copy all the partitions from the first disk to the second (right click, copy)

---

### Post by TheSlipstream on 2008-08-09
> **ercferret18 said:**
> um... try this... make sure both hard drives are in the same computer, and then, using gparted, copy all the partitions from the first disk to the second (right click, copy)

Sorry man, laptop. Only one disk at a time.

---

### Post by bpowell2005 on 2008-08-09
Here's what I've done:

Run to the local computer shop, and buy a USB enclosure for your new laptop hard drive (they run around $20 USD). Put the new (bigger) hard drive in the enclosure, and button it up. It should be powered by your USB port, just plug it in, and you have a 120 Gig USB drive...very nice. Then, get online and download a liveCD called "Clonezilla" it comes with Gparted as well. Burn that ISO, and boot to that OS.

Select CloneZilla, and follow the prompts to clone your 40 Gig drive onto your 120 gig.

Most likely, once it's done, you'll find that the 120 partition size has been shrunk to be identical to your 40 gig...no worries, reboot the liveCD, select Gparted, and resize the partition.

After that, swap hard drives (120 in the machine, 40 in the enclosure). Remove the liveCD and boot the laptop off of your 120 gig drive...you'll be in great shape, and you'll now have a 40 gig external drive that you can format and use for storage!

---

### Post by ercferret18 on 2008-08-09
hmm... theres this program called g4u (free) that can copy a hard drive image to an ftp server, and back, so maybe host an ftp server with the second laptop, transfer the hard drive image to the second laptop, put in the new hard drive, and transfer back. it will be fastest with ethernet

---

### Post by TheSlipstream on 2008-08-09
Ah, thanks very much, you guys. Marking as solved. :D

---

### Post by bpowell2005 on 2008-08-09
No worries! Good luck! Just follow the prompts on Clonezilla and you can't go wrong...pay attention while selecting "source" and "target" drives.

---

