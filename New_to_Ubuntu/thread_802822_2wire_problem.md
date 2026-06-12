---
title: "2wire problem?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by wjtwillis on 2008-05-21
I am trying out Ubuntu for the first time and I am having problems connecting to the internet wirelessly on 8.04. There is no problem finding the network but when I try to connect my 2wire router resets and won't start working again until ubuntu stops trying to connect.
Any help is appreciated.

---

### Post by avadyn on 2008-05-21
i have the same exact problem! does anyone have a solution to this?

---

### Post by hariprs on 2008-05-21
Is your router really resets or only the DSL line goes down and resync again?

Please post more about your router configuration.

---

### Post by unicandun on 2008-05-21
I have the same problem. 

My system: Dell Inspiron E1505. Built in Wireless Card.

The router: 2Wire 1800HW "Home Portal". 

Could connect fine in Gutsy, after upgrade to Hardy every 
time I connect to the router it resets its connection, other 
computers on the same router (wired) loose internet. 

The router takes about 5 minutes to come back up. 

The Laptop connects just fine On campus and to Linksys
Wireless-G Broadband router. 

The problem only present on the 2wire! (My home router:(!!)

Please tell me if there is any more information I should post. I also left a bug report on Launchpad

Thanks!

---

### Post by wjtwillis on 2008-05-22
I can't tell if the router actually resets because the computer and router are on two different floors, but all the other computers in the house also lose the internet connection. This never happened when I was running windows XP so I am sure it is not a problem with my wireless card. 
What other info do you need?

---

### Post by avadyn on 2008-05-22
the router acts as if i unplugged it and plugged it back in. it completely resets whenever i try to connect wirelessly, wired works just fine though

---

### Post by Mr_B on 2008-05-25
I have the same problem when I try to connect to a 2wire router. The model is HomePortal 1000SW and I am connecting with a Sony Vaio VGN-C140G that connected fine running XP and Vista. My wife MacBooks connects fine. When I try to connect everyone gets disconnected including the wired connection ("network cable has been unplugged"). The normal 3 green LED turn off and the top (power) LED turns red like I just plugged the router in. I am running Ubuntu 8.04. Any ideas?

---

### Post by wjtwillis on 2008-06-01
Is there any kind of fix for this? If not I will just have to switch back to vista :(

---

### Post by anewguy on 2008-06-01
I running a 2WIRE 2708H-B and haven't had any problems going [http://ubuntuforums.org/forumdisplay.php?f=326to](http://ubuntuforums.org/forumdisplay.php?f=326to) 8.04.  Since yours is a different model, I suspect the problem lies there - maybe even with the "n" portion of things.  At any rate, you should be aware there is a bug report for this problem and I haven't seen a solution yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793")

I know that other than knowing it's probably nothing you're doing, that isn't much consolation. 

:)

---

### Post by wjtwillis on 2008-06-02
Thanks for your response. 
After reading that bug report (and doing a little searching on my own) it looks like the problem lies with hardy. I will try downgrading to a previous version to see if that works any better.

---

