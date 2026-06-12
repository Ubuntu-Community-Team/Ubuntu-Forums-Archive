---
title: "New Ubuntu User with macbook pro 5,1"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by ccbeyer on 2012-05-24
Hey everyone, just joined the forums and hopefully going to start using Ubuntu in the next few days.  I got a new macbook pro last year, but kept my old one and I decided I should go ahead and put Ubuntu on my old one since im not using it for anything else.  It's an aluminum macbook 5,1 , and I'm wondering which version of Ubuntu I should install on it.  I want to make it a pure ubuntu machine, no dual boot.  I have had a little bit of experience with ubuntu and the linux command line before.  Would it be worth it to go ahead and try to get 12.04 working, or should I go to an earlier version/the last documented working version for the macbook 5,1.

Thanks!

---

### Post by lilmagnus on 2012-05-24
Welcome ccbeyer!!
I have no experience at all with Macbooks. With that said, there are a few threads already here re 12.04 and MBP 5.1...just check them out and I'd say try out 12.04. Not much to lose.

[http://ubuntuforums.org/showthread.php?t=1977764](http://ubuntuforums.org/showthread.php?t=1977764)
[http://ubuntuforums.org/showthread.php?t=1975187](http://ubuntuforums.org/showthread.php?t=1975187) <-- but this user was attempting to dual-boot; links to another howto

I assume you're referencing [this]("https://help.ubuntu.com/community/MacBookPro") which is a bit outdated in that it lists 11.10 as most recent Ubuntu release.

---

### Post by duracella on 2012-05-25
Hey ccbeyer, I actually installed ubuntu 12.04 64bit (recommended)on a macbook 5.1 two-three days ago...
Almost everything works 'out of the box', you might have some trouble with there not being a right click function on trackpad and Cheesy not finding your Webcam...

If keys for brightness not working, you need to edit /etc/X11/xorg.conf 
```
         sudo nano /etc/X11/xorg.conf      
```
and add to device section
```
[FONT=monospace]   [/FONT] Option  "RegistryDwords" "EnableBrightnessControl=1"    
```

---

