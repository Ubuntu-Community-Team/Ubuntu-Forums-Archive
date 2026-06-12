---
title: "FAQ: Can I use instant messaging in Ubuntu?"
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
Yes, Ubuntu comes with Gaim 1.0 it supports AOL, ICQ, Yahoo, MSN and a few other chat clients.

---

### Post by nutty on 2004-10-12
I checked Gaim and MSN works on it. But somehow Yahoo messenger does not work. Is there some configuration that I need to do to get yahoo to work?

Best Wishes

---

### Post by AndersAA on 2004-10-13
since gaim does support yahoo I'd look at the gaim mailinglist for answers to that.  Could be you need an updated version, as protocols occasionaly change a bit making gaim incompatible.

---

### Post by ubuntu-geek on 2004-10-13
Check out [http://gaim.sourceforge.net](http://gaim.sourceforge.net) If I get around to it today I can build a Gaim 1.0.1 package for Ubuntu for the new version if they dont get it in the archives first ;)

---

### Post by Damon on 2004-10-15
Hmm... ./configure couldn't find glib &gt;= 2.0.0

Now, trying to figure out how to tell it where to look. :(

---

### Post by Damon on 2004-10-15
Problems I ran into and their solutions when compiling gaim 1.0.1
&lt;&lt;Keep in mind I have a "vanilla" laptop install. I'm only installing packages as they are needed.  :oops: &gt;&gt;
```
./configure
```
Two problems. glib 2.0.0 or greater was not recognized, as well as gtk greater than or equal to 2.0.0. I had to install both of these packages via Synaptic.
```
make
```
Since I so wisely ignored unix naming conventions and had the source in a directory with a space in the name (My Downloads), havoc befell all stages of make. So, as a consequence, I did the following:
```
cd ../..
mv &quot;My Downloads&quot; downloads
cd downloads/gaim-1.0.1
make clean
./configure
make
make check
sudo make install
```
Now, I have gaim-1.0.1 compiled on my ubuntu box. W00t  :lol:

---

