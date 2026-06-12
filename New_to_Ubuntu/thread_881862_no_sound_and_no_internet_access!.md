---
title: "no sound and no internet access!"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by endtheembargo on 2008-08-06
I have a toshiba satellite A135 laptop. I've upgraded to hardy 8.04 and now I don't have any sound, nor will my computer recognize the wireless connection. What should I do.

I am ABSOLUTELY and absolute beginner, so please keep that in mind :)

---

### Post by yragrelluf on 2008-08-06
did you upgrade or do a clean install? 
what distro were you using before?
upgrading the distro usually doesn't work out, you probably will need to download the latest .iso and clean install. i would recomend setting up an ext2 partition to use as /home, so when you reinstall an OS you will still have your files (music, pics, videos)

---

### Post by endtheembargo on 2008-08-06
I did an upgrade, from fiesty. When I upgraded I had no sound and in trying to fix it, I screwed up the computer so that I couldn't get into it. So I was advised from boot menu to select recovery mode and then xfix - which I did, and now I can get back into the computer. But now, no sound, AND no wireless....

---

### Post by endtheembargo on 2008-08-06
> **yragrelluf said:**
>  i would recomend setting up an ext2 partition to use as /home, so when you reinstall an OS you will still have your files (music, pics, videos)

That sounds good, because I am mostly afraid of loosing all of my files. How to I create that partition though?

---

### Post by yragrelluf on 2008-08-06
honestly, what I would do is make backup disks, or put your files on a flash drive or something. The next step would be to clean install, and when the partition editor shows up, select manual, and delete any existing partitions. when the entire hard drive shows up as free space then you need to make an ext3 partition for / this will hold your operating system, and should be at the beginning. The next step will be to create a partition for swap, that should be at the end. Then finally, partition the rest of the free space as ext2 to use as /home
it is up to you how big each partition will be. my computer is 160gb, and i use 5gb for swap, 55gb for /home, and 100gb for /
the partition editor on the live cd has a decent gui, so take your time and think about everything you are doing, if you do it right, you should be able to install and reinstall any OS on the / partition, without creating a new swap, or losing your files.
let me know how it goes!

---

