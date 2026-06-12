---
title: "Running Runescape"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by HaemoLacria on 2008-06-05
I used to have a problem while logging in to RuneScape. When I hit the log in button the browser did shut down completely. I found out that I had to clear the cache that Jagex puts on your pc. SO someone made some script for me which removes the cache and then make the runescape site pop-up. That all happened when I hit the icon.
For some weird reason the browser does shut down again:confused:
Does anybody know how to make such (easy) script ?

EDIT: Maybe somebody knows where the RuneScape cach file can be found on the PC. So I just can remove it everytime by myself

---

### Post by HaemoLacria on 2008-06-05
bump, please

---

### Post by HaemoLacria on 2008-06-05
GCJ PLUGIN: thread 0x8126468: NP_Initialize
GCJ PLUGIN: thread 0x8126468: NP_Initialize: using /usr/lib/classpath/gappletviewer.
GCJ PLUGIN: thread 0x8126468: NP_Initialize return
GCJ PLUGIN: thread 0x8126468: NP_GetValue
GCJ PLUGIN: thread 0x8126468: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x8126468: NP_GetValue return
Failed to create Java VM

I deleted some .log files and now this is what I see in the terminal why attempting to load RuneScape

---

### Post by HaemoLacria on 2008-06-05
Maybe ther's something wrong with my plugin

---

### Post by starcannon on 2008-06-05
I noticed that ubuntu-restricted-extras puts the goofy icedtea java on instead of the official sun-java one.

I fixed that by opening synaptic package manager, searched for jre, uninstalled the open-jdk ones, and installed the sun-java6 ones.

I think this will get you going, GL let us know how its going.

---

### Post by HaemoLacria on 2008-06-05
Thanks, I'll try it

EDIT: Synaptic Package Manager does not work:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by lazyart on 2008-06-05
Did you try what it says?```
sudo dkpg --configure -a
```

---

### Post by HaemoLacria on 2008-06-05
I did, but it does not work. I have to be a ' superuser' or something. 
Actually I'm starting to dislike Linux (slightly)

---

