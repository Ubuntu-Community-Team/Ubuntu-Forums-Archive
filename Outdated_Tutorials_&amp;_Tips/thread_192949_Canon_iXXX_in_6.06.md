---
title: "Canon iXXX in 6.06"
date: 2006-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by cafn8ed on 2006-06-09
I added this into to another older thread, but this may be easier for people to find.

I own a Canon i860 printer and on older Ubuntu distros I was able to get it working by following the directions in this thread:
[Canon iXXX howto]("http://www.ubuntuforums.org/showthread.php?t=10540")

When I upgraded to Dapper Drake (Ubuntu 6.06), my printer stopped working.  The fault lies in a png library that's required for the printer driver to run, and which is no longer provided in the 6.06 repositories (libpng.so.2).  Luckily, there's another library that works as a substitute, you just need to make a link to it using the name that the printer driver is looking for.  To get things working, here are the necessary steps:

First, make sure you're really missing libpng.so.2:

1) ```
ls /usr/lib/libpng.so.2
```

If you see this: "ls: /usr/lib/libpng.so.2: No such file or directory", then proceed.  If ls actually finds the library on your system, you should stop now and go looking for another solution.

2) ```
sudo apt-get install libpng10-0
```
(Ubuntu may say you already have this installed.  That's ok.)

3) ```
sudo ln -s /usr/lib/libpng10.so.0 /usr/lib/libpng.so.2
```

That should do it.  Try printing another page.  In my case, it worked right away, with no need to restart CUPS or anything else.

---

### Post by legolas on 2006-06-16
/$ sudo apt-get install libpng10-0
Reading package lists... Done
Building dependency tree... Done
Package libpng10-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libpng10-0 has no installation candidate


Hmm.  No luck here.

---

### Post by Matchless on 2006-06-16
[QUOTE=cafn8ed] 

2) ```
sudo apt-get install libpng10-0
```
(Ubuntu may say you already have this installed.  That's ok.)

[/QUOTE]

Only libpng12-0 is available on the dapper repos, does this work as well?

---

### Post by dyrer on 2006-06-18
this solution is for i386, is it working on x64

---

### Post by mandragor on 2006-06-19
This howto is slightly incomplete, or did not work for me. The only alterations
you will need are to add repositories for the libtiff and libpng libraries.
Everything is explained here: 
[https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b](https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b)

Send me a PM if something is unclear. Happy printing.:mrgreen: 
(and BIG thanks to cafn8ed, who's work my guide is based on)

---

### Post by legolas on 2006-06-19
That is using the BJC 7000.  I am using them and the quality is really bad.  I mean really bad.  I was hoping for something besides using those drivers.

---

### Post by mandragor on 2006-06-23
Check the link in my previous post, it contains instructions to use the original
Canon drivers. I still can't get it to print in grayscale, but the quality is pretty good.

---

### Post by Acesomeone on 2006-06-23
How does one know which of the drivers to use? I've got a i905D, but no clue which one to try?

---

### Post by legolas on 2006-06-28
[QUOTE=mandragor]This howto is slightly incomplete, or did not work for me. The only alterations
you will need are to add repositories for the libtiff and libpng libraries.
Everything is explained here: 
[https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b](https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b)

Send me a PM if something is unclear. Happy printing.:mrgreen: 
(and BIG thanks to cafn8ed, who's work my guide is based on)[/QUOTE]

I have a Japanese Pixus 560i.  I did everything that the post said.  It went real smoothly.  I went to print 20 pages of a document and it petered out on the 8th page-just stopped right in the middle and did not start again.  I tried to print it again and it wouldn't start up.  What would cause this kind of behavior?  Any sugguestions or thoughts would be greatly appreciated.  Thanks

---

