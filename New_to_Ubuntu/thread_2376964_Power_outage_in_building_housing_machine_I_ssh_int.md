---
title: "Power outage in building housing machine I ssh into, now I can't open folders"
date: 2017-11-07
forum: New to Ubuntu
---

### Post by somebro on 2017-11-07
There was a power outage in the building that houses my machine running Ubuntu 16.04. I ssh into the machine and when I did so just now, all of my permissions were incorrect. I managed to fix many of them, but there is a 1TB drive I store many important files in that I cannot access. Using ls -ln, I find it's owned by root, but it also appears empty. I really hope that doesn't mean everything on there was deleted? 

I'm sorry for the lack of specificity, I'm new to Linux and I've been driving myself crazy trying to fix this for the last several hours. 

Thanks for any advice you might have!

---

### Post by HermanAB on 2017-11-08
It is likely that the disk is not mounted, so you only see the empty mount point.

---

