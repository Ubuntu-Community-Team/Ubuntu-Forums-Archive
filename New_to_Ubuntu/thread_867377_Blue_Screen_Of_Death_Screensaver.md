---
title: "Blue Screen Of Death Screensaver?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-07-22
I heard that there is a blue screen of death screensaver in ubuntu, but you have to unlock it or something, is this true? If not, is there a way to get one? Thanks.

---

### Post by Dr Small on 2008-07-22
I have never heard of this, and have never seen a BSoD screensaver for Ubuntu. I am not very xscreensaver savvy, either, but you can look around. I may be wrong.

---

### Post by northern lights on 2008-07-22
googling "blue screen screensaver ubuntu" yields [http://ubuntuforums.org/showthread.php?t=495099]("http://ubuntuforums.org/showthread.php?t=495099") as the first result...

life can be quite simple   ;-)

---

### Post by Joeb454 on 2008-07-22
I've never heard of one either, but you can get one, I had it on my Windows partition for a while, really scared some people (and got me out of doing work occasionally ;))

---

### Post by redfox1160 on 2008-07-22
> **northern lights said:**
> googling "blue screen screensaver ubuntu" yields [http://ubuntuforums.org/showthread.php?t=495099]("http://ubuntuforums.org/showthread.php?t=495099") as the first result...

life can be quite simple   ;-)

I did that, but I didn't understand what you need to download.

---

### Post by northern lights on 2008-07-22
In a terminal run ```
sudo apt-get install xscreensaver-data-extra
``` Then navigate to "System > Prefernces > Screensaver" and select "BSOD"

---

### Post by redfox1160 on 2008-07-22
> **northern lights said:**
> In a terminal run ```
sudo apt-get install xscreensaver-data-extra
``` Then navigate to "System > Prefernces > Screensaver" and select "BSOD"

thanks

---

### Post by ruhil on 2011-05-04
BSOD screensaver is no more available in xscreensaver-data-extra package. To install it all alone:
```
sudo apt-get install xscreensaver-screensaver-bsod
```

---

### Post by cariboo on 2011-05-04
This is a 3 year old thread. If you wish to start a discussion, please start a new thread, as this one is closed.

---

