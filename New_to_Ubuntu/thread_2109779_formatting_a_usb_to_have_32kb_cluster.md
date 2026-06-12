---
title: "formatting a usb to have 32kb cluster?"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by lolful64 on 2013-01-28
Format a usb to have a 32kb cluster?

How do I do this? (remember this is the absolute beginner section, im not a computer programmer, nor a ubuntu master)

---

### Post by Bashing-om on 2013-01-28
lolful64; Hi !

If I am not too mistaken, the utility "fdisk" will permit formatting with alternate blocks.
see:
```
 man fdisk
``` to start with.
Google and DuckDuckGo are your friends for additional tutorials.
[INDENT][INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tgalati4 on 2013-01-28
There are some switches in mkfs.msdos:

       -s sectors-per-cluster
              Specify the number of disk sectors per cluster.  Must be a power of 2, i.e. 1, 2, 4, 8, ... 128.

       -S logical-sector-size
              Specify the number of bytes per logical sector.  Must be a power of 2 and greater than or equal to 512,
              i.e. 512, 1024, 2048, 4096, 8192, 16384, or 32768.

```
man mkfs.msdos
```

I would expect breakage.  Some USB flash controllers will only work at the default cylinder, heads, sector size.  Changing the cluster ratio might mess up read and write access due to timing, buffer, and other issues due to the limited drive controller.

Let us know what works for you.  Why do you need this?

---

### Post by mapes12 on 2013-01-29
What are you trying to achieve? USB sticks can be a problem, particularly the larger ones that are formatted to exFat which requires a special ubu package to manage them properly. I'm lazy and plug mine into a windoze machine and then format them with the HP USB Format Tool. 

Here's an Ubu thread I found:-

[http://ubuntuforums.org/showthread.php?t=1983349](http://ubuntuforums.org/showthread.php?t=1983349)

and this may help:-

[http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm](http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm)

---

