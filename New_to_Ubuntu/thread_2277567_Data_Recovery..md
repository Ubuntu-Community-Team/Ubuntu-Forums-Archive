---
title: "Data Recovery."
date: 2015-05-09
forum: New to Ubuntu
---

### Post by itscamsgraphcis on 2015-05-09
So...

HDD Boot Sector is corrupt. PC Wouldnt boot. Made a live boot of Ubuntu, Found data on HDD (Intact). Trying to figure out how I can backup that data to my External Hard Drive, format the HDD and restore the data on to the fresh HDD. I found out about making a disk image, would this work? Using "DD" (I barely know what it is) to create a disk image of the HDD to the EHD? If so would: ```
sudo dd if=/dev/sdg1 of=/dev/sda1/diskimage.img
``` work? I think i would need to fix the Output file since /diskimage.img isnt a directory. But would this work and could I then use the Image as a "system image" in windows 7 to restore from?

Any other ways? Thanks in advance.

---

### Post by Mark Phelps on 2015-05-09
Would help if you told us what OS is on the original PC.  Any image you make with dd is unlikely to "mount" in Win7 -- as Windows uses its own proprietary format.

---

### Post by leunam12 on 2015-05-09
I would use parted magic live USB or CD. Run it live from the media instead of runnng from memory. Run Disk Cloning utility to clone your HDD to your external drive; then run the Partition Editor to format the HDD. Finally run Disk Cloning again to restore the image to the HDD. I have done it many times.

I'm assuming that you know how to burn an image to DVD or USB stick.

[http://sourceforge.net/projects/gparted/?source=recommended](http://sourceforge.net/projects/gparted/?source=recommended)

---

