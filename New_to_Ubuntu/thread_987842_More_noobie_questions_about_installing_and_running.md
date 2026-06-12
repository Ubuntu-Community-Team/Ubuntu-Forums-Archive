---
title: "More noobie questions about installing and running off of two hard drives"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by shawshawshaw on 2008-11-19
I got Ubuntu to run via the "trial run" option - I installed it on my D: drive

is it possible to keep windows xp (which is on c:) and do a full install of Ubuntu on the D: drive?  aka a dual boot?

Also: while I was in Ubuntu, I could access my files on my C: drive, but I could not access any of my D: drive files. I tried to find a place where I could just type "C:" or "D:" (like a location bar) but I couldnt find it.  Any ideas?  

sorry to be noobie...

---

### Post by Maverick1712 on 2008-11-19
Hey,

Yes, a dual boot is possible, and quite common. What will happen is that a program called GRUB will be installed, and this will display a menu that will let you choose which OS to boot into.

I'm not sure what the trial run option is, as I have not used it. One thing to note, if you are going to install Ubuntu onto D:, remove any files that are on D: and move them to C:. The reason is when installing a new OS, it is typically recommended to partition the drive. The first time I installed Ubuntu was in this way and I lost about 60 gigs of videos and music files.

You will not see anywhere that you can type a drive letter, as drive letters are a windows feature. Instead, your drives are "mounted" to a location in the filesystem. A little research should help you find out where (I used to know, but since switching over entirely to Ubuntu, I can't for the life of me remember). Hope this helps clarify some things.

Cheers,
Adam

---

### Post by shawshawshaw on 2008-11-20
so get the Grub and get the stuff I currently have on drive D: off of there?  shouldn't be a problem.  It's a new Maxtor 500 gb hard drive I just got.  Any suggestion on partition numbers?  I'm sure there must be a way to get to files on drive D: if I could get to C: - thanks for the advice!

---

### Post by Maverick1712 on 2008-11-20
GRUB will actually be installed when you install linux. Can you currently boot into your windows system? You should be able to access D: from there (assuming the trial run option didn't delete anything, can't say if it does)

As far as partitions go, the overwhelming feedback I got from this question when I first started was to have a seperate partition for /home and for /. /home is where all of the user files will be kept as well as a lot of configuration options. If this is a seperate partition, it makes upgrading the OS a lot easier, as it will not be a fresh configuration each time. Currently on both my machines /home and / have about the same size. And don't forget to make a swap partition. I forget how big this should be in relation to your RAM, but I'm sure wikipedia will have more to say on it.

Cheers,
Adam

---

### Post by caljohnsmith on 2008-11-20
You might find either of these tutorials helpful, because they lead you through the installation process step-by-step and also include lots of screen shots of what to expect:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)
[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Let me know if that helps.

---

