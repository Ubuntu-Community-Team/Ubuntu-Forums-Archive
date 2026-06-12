---
title: "Updating to latest ubuntu"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by Kevzz on 2012-07-11
Just wondering if there's a way I can make sure my system is up to date, I installed ubuntu a couple of months ago and i'm not too sure if there's a newer version out. Is there a command line tool i can use to make sure i'm upto date?

---

### Post by papibe on 2012-07-11
Hi Kevzz. Welcome to the forums!

Could you post the results of these commands?
```
lsb_release -a

uname -a
```
Regards.

---

### Post by Bucky Ball on 2012-07-11
I'd stick with a stable release rather than the newest. The newest is actually bleeding edge and is the nightly build of 12.10 probably. That would not be stable. 

10.04 LTS is stable and has a year's support and 12.04 LTS has just come out and has nearly five. 

* If you are a developer or helper and you actually do want the nightly build, disregard my post. ;)

---

### Post by Kevzz on 2012-07-11
Please see below for the results on the above command lines.


kevin@ubuntu:/usr/bin$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
kevin@ubuntu:/usr/bin$ uname -a
Linux ubuntu 3.2.0-5-generic #11-Ubuntu SMP Thu Dec 15 19:06:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by blackbird34 on 2012-07-11
Yep that's the latest one, it should be perfectly all right. Five years support for your Ubuntu 12.04 LTS :D

It is recommended to keep up to date with the Update Manager (it prompts you every week) and/or by command line : 
```
sudo apt-get update && sudo apt-get upgrade
```
Happy Ubuntu-ing!

---

### Post by Kevzz on 2012-07-11
Thanks for that, everything seems to be updated now. However, I have a problem with opening up applications for example network tools, it'll open up and then close straight away and it happens

---

### Post by Bucky Ball on 2012-07-11
> **blackbird34 said:**
> Yep that's the latest one, it should be perfectly all right. Five years support for your Ubuntu 12.04 LTS :D

It is recommended to keep up to date with the Update Manager (it prompts you every week) and/or by command line : 
```
sudo apt-get update && sudo apt-get upgrade
```Happy Ubuntu-ing!

+1. Stick with 12.04 LTS and if you're updated you're good. 

Please start a new thread for your network problems and mark this one as solved, as it seems to be. You've a much better chance of getting assistance as the title of this thread has nothing to do with the new issue. ;)

PS: You upgrade to a newer release of Ubuntu.

---

