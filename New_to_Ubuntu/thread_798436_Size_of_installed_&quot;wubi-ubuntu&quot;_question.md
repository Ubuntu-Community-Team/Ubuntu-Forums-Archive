---
title: "Size of installed &quot;wubi-ubuntu&quot; question"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by redoak on 2008-05-18
I was surprised to find that 10 GB of my "C" partition was taken up by the installation of "wubi-ubuntu." There had been 65% of a 25 GB partition "free" that went to 25% free after the installation. I removed "wubi-ebuntu" and the free space went back to 65%. 

Why would "wubi-ubuntu" require more HDD space than Windows "XP," which runs some 6 GB?

{redoak}

---

### Post by shifty_powers on 2008-05-18
depends on how you set up wubi.

by the sounds of it, you set wubi to set up a 10gig partition for ubuntu, which windows will see as a single file. seems lik that wubi preallocates that space to the file, even if you havn't, (and in all likelihood haven't), used all of that space by installing ubuntu.

when you boot into ubuntu, the partition will only show as x amount being used ;)

---

### Post by .nedberg on 2008-05-18
Yes, wubi preallocates the space. So if you give Ubuntu 10GB in Wubi, that space will be used on the drive. It is not used in the Ubuntu install, but Windows cannot see/use it.

---

### Post by redoak on 2008-05-18
This was a "wubi" installation made automatically to my "C" drive.

I did no allocating of space on my HDD. I am taking about a 25GB already existing partition holding "XP," Ws "Office" and many other programs and utilities that totally only take up some 8 GB, hence the 65% +/- of space unused before Ubuntu was installed via "wubi."

Thanks for the replies, {redoak}

---

### Post by .nedberg on 2008-05-18
Have a look here: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

In the first screenshot you see the installation size. If you set it to 10GB, it will take 10GB from your drive. Some of this will not be "used", only blank space, unusable to Windows. In Ubuntu you will see that a lot of the space is still free.

---

### Post by redoak on 2008-05-18
Many thanks for the added info. 

What would be a minimum size to use for Ubuntu for decent performance/expansion? 

Fortunately, I have saved the installation files and can "go around the horn" once again with little difficulty.

{redoak}

---

### Post by .nedberg on 2008-05-18
If you are just testing Ubuntu and don't need to install additional programs or storing files in your /home, I think you could get away with as little as 4GB.

The default install size in Wubi is 8GB, I would recomend that or at least 6GB. I think I recal reading that a wubi-install cannot be resized. So if you fill it up you have a problem...

---

### Post by redoak on 2008-05-18
Again, many thanks. I'll go with 6 GB. If I see any deterioration in my "XP," I'll add some GBs to the "C" partition. I don't like to "mess around" with partitions, unless really necessary.

I am 78 years "young" and reasonably efficient with "XP," so I thought I would undertake a Linux program. However, I needed to move slowly, hence my choice of "wubi." 

No doubt I am going to be pestering the good folks here at the Forums from time to time.

{redoak}:)

---

