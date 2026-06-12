---
title: "Shredding and reinstalling."
date: 2008-09-20
forum: New to Ubuntu
---

### Post by mczonie on 2008-09-20
I've had absolutely nothing but problems since switching to Ubuntu. I want to try shredding my entire disk and starting over from scratch, and see if that works. I understand that if I run "shred -vfz -n 100 /dev/hda" it will shred the whole disk. How do I go about reinstalling after I shred my disk? Is it just a matter of popping in the disk and following the instructions?

---

### Post by mkvnmtr on 2008-09-20
As someone that has had to reinstall a number of times because I messed up my system I don't think shredding will help. I just do a reinstall on top of the old one. Once you reformat anything on the disk is just like the random data after a shred. With 8.04 the first install never seemed right. I reinstalled and could not be happier. Have no idea why, but the updates were different than the first time so maybe the fixed something. Good luck

---

### Post by niteshifter on 2008-09-20
Hi,

No need to use shred, in particular no need to have shred make 100 passes! You'll be waiting a long, long, long time for it to complete.

From a Live CD:
```
dd if=/dev/zero of=/dev/hda bs=512
```

The above will write 0's to the disk and complete much quicker.

---

### Post by mczonie on 2008-09-20
> **niteshifter said:**
> Hi,

No need to use shred, in particular no need to have shred make 100 passes! You'll be waiting a long, long, long time for it to complete.

From a Live CD:
```
dd if=/dev/zero of=/dev/hda bs=512
```

The above will write 0's to the disk and complete much quicker.

How do I run code from a live CD?

---

### Post by mczonie on 2008-09-20
> **mkvnmtr said:**
> As someone that has had to reinstall a number of times because I messed up my system I don't think shredding will help. I just do a reinstall on top of the old one. Once you reformat anything on the disk is just like the random data after a shred. With 8.04 the first install never seemed right. I reinstalled and could not be happier. Have no idea why, but the updates were different than the first time so maybe the fixed something. Good luck

I've reinstalled several times and there's always something wrong.

---

### Post by kansasnoob on 2008-09-20
> **mczonie said:**
> I've reinstalled several times and there's always something wrong.

Like what?

Maybe we just need to fix what's wrong.

---

### Post by mczonie on 2008-09-20
> **kansasnoob said:**
> Like what?


Like this:

[http://ubuntuforums.org/showthread.php?t=923750](http://ubuntuforums.org/showthread.php?t=923750)

---

### Post by niteshifter on 2008-09-21
Hi,

From the thread you linked to:
```
top - 16:48:12 up 2 days, 21:32,  2 users,  load average: 1.83, 1.68, 1.57
Tasks: 107 total,   4 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 95.0%us,  5.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
[COLOR="Red"]Mem:    384508k total[/COLOR],   375624k used,     8884k free,      780k buffers
Swap:  1116476k total,   430332k used,   686144k free,    39100k cached
```

Yep, it's a memory problem: Not enough for Ubuntu / GNOME / Compiz and all the rest. You could try Xubuntu, it's requirements are more modest. Or add / replace RAM (1GB would be good).

---

### Post by mczonie on 2008-09-23
> **niteshifter said:**
> Hi,

From the thread you linked to:
```
top - 16:48:12 up 2 days, 21:32,  2 users,  load average: 1.83, 1.68, 1.57
Tasks: 107 total,   4 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 95.0%us,  5.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
[COLOR="Red"]Mem:    384508k total[/COLOR],   375624k used,     8884k free,      780k buffers
Swap:  1116476k total,   430332k used,   686144k free,    39100k cached
```

Yep, it's a memory problem: Not enough for Ubuntu / GNOME / Compiz and all the rest. You could try Xubuntu, it's requirements are more modest. Or add / replace RAM (1GB would be good).

Aside from taking up less memory, how does Xbuntu differ from Ubuntu?

---

### Post by mczonie on 2008-09-23
> Yep, it's a memory problem: Not enough for Ubuntu / GNOME / Compiz and all the rest. 

My CPU is a relatively recent make. It's a Dell Pentium. Is it normal for it to have that little memory? It ran Windows XP just fine.

> You could try Xubuntu, it's requirements are more modest. 

How can I get it?

> Or add / replace RAM (1GB would be good).

How can I do that?

---

### Post by bumanie on 2008-09-23
The underlying OS is the same, xfce is just a much lighter desktop environment that will operate with as little as 128mb ram.

---

### Post by crazypenguin2008 on 2008-09-23
i had some trouble with my upgrade from gusty to hardy. i had to install a few times. and tonight i had to can my upgrade of hardy to ibex after my second drive failed. so i knwo where your comming from it can be unnerving.


ram is easy to add. ill post a pic when i get home from work today of where the ram slots are on a dell intel mobo. 

i asume its a pentium III? im running a pentium III(K) in a old dell xps t500 box that i added 2 more harddrives to. ive only got 650mb of ram and i run hardy fine. for the longest time i was running gusty and hardy on this box in seperate partitions.

hope you can get it going..

good luck

---

