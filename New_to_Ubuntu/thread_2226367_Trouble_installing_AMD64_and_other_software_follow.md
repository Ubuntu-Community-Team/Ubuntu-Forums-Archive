---
title: "Trouble installing AMD64 and other software following Ubuntu 14.04 reinstall"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by drkem99 on 2014-05-26
I managed to stupidly brick my Dell XPS13 laptop (wiped boot partition while wiping and formatting SD cards - never use powerful software while half asleep!) and had to do a clean install of Ubuntu 14.04 last week, Since that time, I have had a horrible time reinstalling software. Downloads marked AMD64 that previously installed on my Intel laptop _with 14.04_ will no longer install due to 'incorrect system architecture'. Software that previously installed and worked flawlessly (TrueCrypt) reinstalls but will not operate. I'm slowly rebuilding what I can but I'm so frustrated I'm about to wipe the damn thing again and install Windows. I am open to any suggestions because I'm out of airspeed, altitude, and ideas.

---

### Post by Ubi_one_2014 on 2014-05-26
how did you do a clean install

during installation you have to choose for a NEW installation, rather then an upgrade/restore/whatever option

---

### Post by deadflowr on 2014-05-26
Post the output for 
```
uname -a
```

---

### Post by drkem99 on 2014-05-27
Thanks to all for offers of help. I went back and checked my system info. I had used an old netbook to download and burn a Ubuntu Live CD and managed to get a 32-bit install. When I downloaded the 64-bit version of Ubuntu 14.04 LTS and did a clean install, everything went smoothly.

Live and learn, I guess. Good thing I don't make a living doing IS work...

---

### Post by deadflowr on 2014-05-27
> **drkem99 said:**
> Thanks to all for offers of help. I went back and checked my system info. I had used an old netbook to download and burn a Ubuntu Live CD and managed to get a 32-bit install. When I downloaded the 64-bit version of Ubuntu 14.04 LTS and did a clean install, everything went smoothly.

Live and learn, I guess. Good thing I don't make a living doing IS work...

Live and learn, quite so.
That was my figuring, though.
Which is what the command I gave would have done. List the arch version.
x86_64 would have meant 64-bit, but i386,i586,or i686 would have meant 32-bit.
ftr

If the problems solved, please [mark this thread as solved.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

