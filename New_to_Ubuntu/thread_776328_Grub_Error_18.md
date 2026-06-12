---
title: "Grub Error 18"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by DBrocks on 2008-04-30
Hey guys. Just did a fresh install of Hardy on my new 500 GB disk I bought. Now, on the boot, I recieve the error: "Grub error 18". How can I resolve this?

Thanks!!!

~Dan

---

### Post by martrn on 2008-04-30
Grub Error 18 is a cylindrical boundary problem whereby you can not the whole of your disk in one foul swoop because of some cylindrical calculation of your hard disk.

Have you checked to see if the BIOS recognized your hard drive as 500GB not some other size.  Is your hard drive PATA or SATA ?

Have you used a drive in your computer of more than the 137 GB (some kind of BIOS hard drive size limitation quirk.)

Is there a BIOS update fix from your motherboard manufacture to get around the 137GB hard drive size quirk ?

---

### Post by jimv on 2008-04-30
I'm kinda going off what that last guy said...you could try reinstalling onto a smaller partion....like 50 gigs for an Ubuntu partition and then 450 for a storage partition.

---

### Post by anewguy on 2008-04-30
martrn is right - there is a limit to what your BIOS can address.  Many of us remember back to when this was a common problem and overlay software was used to make it work.  As far I know, there is no overlay software that runs in Linux.  I had this same problem with just an 80gig driver - my BIOS wouldn't recognize anything about 32gb.  Unless your motherboard is old, I doubt yours is that low - probably more in the 137gb range that martrn mentioned. As they mentioned, check for a BIOS update for your motherboard.  If none is available, your choices become more limited.  On my computer, even when I made several smaller partitions on the drive, the BIOS still said that the overall geometry of the disk was still too large.  On my particular motherboard, it actually required a reflash of the BIOS to one lower level than that which was on the board.

good luck!!  :)

---

### Post by DBrocks on 2008-04-30
Thanks alot guys. Also, I've also read something interesting: Grub error 18 means that the partition is too large for the bios to handle. So, I am creating a 50 MB Partition for /boot. (originally, grub was installed on the same partition as everything else). Apparently, 500 GB is too much for my MOBO to handle (it's a dell 233 Mhz :popcorn:, but works great as a file storage medium!). I will keep you guys updated! Thanks

~Dan

---

