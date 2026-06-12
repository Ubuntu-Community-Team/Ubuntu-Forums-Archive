---
title: "Error running update"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by mattywarr on 2008-04-23
Hey all :)

Getting this error when checking for updates. Any idea why?

E: The method driver /usr/lib/apt/methods/hhttp could not be found.

---

### Post by spiderbatdad on 2008-04-23
looks like an error in your /etc/apt/sources.list file...possibly. Did you install automatix or something?

Could you post your sources list?

---

### Post by mattywarr on 2008-04-23
Your absolutely right! 

Pasted in some new sources from the Help wiki and found this line

deb-src hhttp://mirror.ubuntulinux.nl/ dapper-seveas freenx

Deleted the h and it worked!

---

### Post by SOULRiDER on 2008-04-23
Yes, its supposed to be http not hhttp :P

Where did you get that by the way.. its meant to be used on Dapper, I dont think its a good idea to use it on any version other than Dapper.

There is a Gutsy repo however, if youre using Gutsy remove the dapper one and check out [http://mirror.ubuntulinux.nl/dists/gutsy-seveas/](http://mirror.ubuntulinux.nl/dists/gutsy-seveas/) it explains how to use the Gutsy one.

---

### Post by Joeb454 on 2008-04-23
Actually I used a Gutsy repo on Hardy for something...though being as Hardy was not out at the time...I figured that I didn't really have much other choice :p

---

### Post by SOULRiDER on 2008-04-23
Yeah, but Dapper and Gutsy are quite different, i mean, they could work but they can also break something.. quite badly.

---

### Post by mattywarr on 2008-04-24
I actually got the repo from a help guide on the main site for FreeNX, which is what I was trying to install - I'll add the new repo and try and run updates and see what I get.

Thanks :)

---

### Post by Zburatorul on 2010-05-01
> **mattywarr said:**
> Hey all :)

Getting this error when checking for updates. Any idea why?

E: The method driver /usr/lib/apt/methods/hhttp could not be found.

I just had the same issue, and the same solution: an extra "h" in the url.

---

