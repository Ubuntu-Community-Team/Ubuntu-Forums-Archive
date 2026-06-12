---
title: "Rearrange files on the hard disk?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by skymera on 2008-09-11
Hello :D

Although i know fragmentation is not a problem with EXT3. Phew!
But file placement in the disk is equally important.

On XP i have a program that rearranges all my 25% most used files to the outer edge of the disk ((where access if fastest (Great for booting and common apps))

Is a similar thing available in Ubuntu? So i can move all my files needed at boot to the outer edge etc.

Having files all contiguous is great, but if the files for boot are located all around the disk, it will take longer to boot, surely?

Thanks

---

### Post by handydan918 on 2008-09-11
> **skymera said:**
> 

Having files all contiguous is great, but if the files for boot are located all around the disk, it will take longer to boot, surely?

Thanks

Doubtful, with the linux file structure. All the files needed to boot are in the same directory anyway.There is more gain in killing non-essential services to speed up boot time anyway. Although, with your hardware, I can't imagine you have to wait much more than 40 seconds...
If the boot time is really killing you, just do what I do. 
Never reboot, never shut down.
Almost made a year once, but a power outage got me.... 

:lolflag:

---

### Post by skymera on 2008-09-11
i have a 15 second boot.

And being in the same directory doesn't mean they are together on the physical disk

---

### Post by kaibob on 2008-09-11
Not precisely what you're looking for, but you may want to look at the following tip on profiling:

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

I did this and didn't notice any difference, but you're results may be better. Disabling unnecessary services is probably more important.

---

### Post by skymera on 2008-09-12
Done all that, profiling makes a lot of difference if you disable readahead at boot. :wink:

But i halved my XP boot my placing my boot files on the outer edge. I thought Ubuntu could have a similar effect is the same was done.

---

