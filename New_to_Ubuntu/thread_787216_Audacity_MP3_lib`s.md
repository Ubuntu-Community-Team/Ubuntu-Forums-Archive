---
title: "Audacity MP3 lib`s"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Jabz.biz on 2008-05-08
Yeeeha,

I installed audacity and started editing some of my music files. And here it comes, the export to an mp3 file does not work. 

I do not have the lame mp3 lib`s. 

Although there is a button download the lib`s here, nothing happens...and I`m too much of a noob to know what to do now. :) 
Any advise? 

Thanks, Jab

---

### Post by quelx on 2008-05-08
```
sudo apt-get install lame
```

in audacity ctrl-p

Audio Files>MP3 Export Library type >Find Library **/usr/lib/libmp3lame.so.0** if it doesn't show up automagicly

---

### Post by Jabz.biz on 2008-05-09
Hi, I installed lame via terminal. But the library is not showing up in usr/lib/, I checked it. Only seconds later I ran into some other problems, which I posted here: [Other Thread]("http://ubuntuforums.org/showthread.php?p=4917435#post4917435")

Coincidence? And where can I find my library? ;) So many questions...but at least it`s not Windows.

Help is highly appreciated!

---

### Post by quelx on 2008-05-09
I don't know if it was a typing oversight but /usr/lib need the "/" in fron of it when loading the library.  It's in the root "usr" directory.

try in the terminal

```
ls -l /usr/lib/libmp3*
```

if it does show, copy and paste that path into audacity.  If not you may need to fix the apt problem you described in the other post first and re-install lame

---

### Post by Jabz.biz on 2008-05-11
I did the updates mentioned in my other post (linked above). Still, the mp3 library is missing. :( 

Any other ideas? Thanks.

---

### Post by mick.ng on 2008-10-01
Hi,I have the same problem too (installing lame to get libmp3lame.so.0)

When I type in:
```
sudo apt-get install lame
```

it shows:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate
```

---

### Post by Jabz.biz on 2008-10-01
I see. I had the same problem. The fixes from the forum did not help. a couple of days/ weeks later I was lucky and found a website, where someone had a simple deb-install for download. that worked. I tried to find the site on Google...no luck. 

Luckily I just remembered that I usually bookmark such things in del.icio.us

AND HERE WE GO:

[http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/](http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/)

This solved my problem! :) Hope it helps you too! 
If yes,...this is the first time I could be of help in this forum...what a feeling.

---

### Post by mermshaus on 2008-11-01
In Kubuntu 8.10, the following works:

```
sudo apt-get install libmp3lame0
```

I didn't test it under Ubuntu but I guess it will work as well.

---

### Post by lmm5247 on 2009-01-06
> **mermshaus said:**
> In Kubuntu 8.10, the following works:

```
sudo apt-get install libmp3lame0
```

I didn't test it under Ubuntu but I guess it will work as well.


that worked perfectly in ubuntu 8.10 thanks alot fixed my problem! =)

---

