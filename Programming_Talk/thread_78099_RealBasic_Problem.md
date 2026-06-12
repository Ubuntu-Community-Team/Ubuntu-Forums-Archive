---
title: "RealBasic Problem"
date: 2005-10-17
forum: Programming Talk
---

### Post by limva on 2005-10-17
If anybody has RealBasic running on Ubuntu Linux, could you please try running the HTMLviewer and let me know if it runs OK?  When ever it gets to the LoadURL or LoadPage function it crashes.  I use Gnome.

---

### Post by Drakx on 2005-10-18
It runs fine mate just do the following.

```

$ cd /usr/lib
$ sudo ln -s libgtkembedmoz.so mozilla-firefox/libgtkembedmoz.so

```

and ensure you have thunderbird installed

```

$ cd /usr/lib
$ sudo ln -s libxpcom.so mozilla-thunderbird/libxpcom.so

```

for some eason i needs that last one out of thunderbird.

---

### Post by limva on 2005-10-22
Hi.  Thanks for the tip.  I'm having so many problems with this.

Before I got your suggestion, I switched to Fedora Core 4 in the hope that the RPM install of REALbasic would work.  Same problem there with HTMLViewer.

Now I've come back to Ubuntu and I've just downloaded REALbasic again in tgz form and extracted all files to my Desktop.  Now I can't even get REALbasic to work!  When I click it, nothing happens.  I remember the first time I had to install REALbasic using command line, but I can't find that site anymore that teaches that!

Do you have to do a correct installation to run a program in Linux?

---

### Post by Drakx on 2005-10-22
use alien to convert the rpm then install as normal :)

---

### Post by limva on 2005-10-23
Thanks Drakx.

I just found out why REALbasic is not starting.  In the root terminal, I went to the REALbasic directory and typed "ldd REALbasic2005" and it listed all the libraries it uses.  On one of the lines it says it was missing the file libstdc++.so.5

Since I've installed the new Breezy Badger version, my system only has the newer libstdc++.so.6.  Does anyone know where I can download the older file?  Or better still, can anyone send me that file so I won't have to look for it? (libstdc++.so.5 in /usr/lib)

Thanks!

---

### Post by limva on 2005-10-23
I solved my problem!

I copied the file libstdc++.so.5 into /usr/lib, but it didn't work.  REALbasic still did not run.  So I re-installed the earlier version of ubuntu and that solved the problem of REALbasic not running.  I then followed Drakx's advice and made links to libgtkembedmoz.so and libxpcom.so (both found in /usr/lib/mozilla-firefox, because I don't have Thunderbird installed) in /usr/lib and my HTMLViewer now works!

Thanks Drakx!

---

### Post by bitgroper on 2005-11-01
Hi, trying to load realbasic on BB and have no clue where to start:

exe won't run
synaptic doesn't see it
no alien on my machine...
guide lists installs for some apps, but no generic install instructions

cannot find help that works

I will write guide if I ever get this going...

---

### Post by Drakx on 2005-11-01
ok guide:

open terminal type:

```

$ sudo apt-get update
$ sudo apt-get install alien
$ sudo apt-get install libstdc++5

```

go a long to RB website, download rb.xxx.x.xx.x.rm package to home

in terminal wite

```


$ sudo alien -d rbpackagename.rpm


```

then once thats done in the same terminal type

```


sudo dpkg -i newrbpackagename.deb


```

**Not forgetting to change rbpackagename and newpackagename to real ones**

from there goto Applications>>Programming>>REALbasic 2005

To get the HTMLviewer follow the above guide

enjoy

---

### Post by bitgroper on 2005-11-01
OK, thanks
I was trying to load it on a Mac G3 400meg running ubuntu - just noticed it's too slow anyway. I have a vb app I'm trying to port to mac and linux. Thought it might be easier to debug locally. I'll try it on ubuntu PC next.

---

