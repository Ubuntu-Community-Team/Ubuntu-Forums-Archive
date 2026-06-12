---
title: "/etc/network/interface and network manager"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by s1337m on 2008-06-21
I am trying to set up WPA on Ubuntu 8.04.  Tutorials I have come across say to edit /etc/network/interface to achieve this... but the thing is if I do that network manager no longer lists networks.  For example,

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

states that

2. Open "/etc/network/interfaces":
Quote:
sudo gedit /etc/network/interfaces
The content should look similar to this:
Quote:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp 


BUT my interfaces file just has the first two lines and doesnt mention wlan0.  If i add the bottom two lines network manager no longer lists wireless networks.  Does this mean if I edit the interfaces file I can no longer get network manager and have to connect through the command line (which i really dont want to do)?

---

### Post by lisati on 2008-06-21
Some soultions suit some people better than others; you'll probably find that you still have *some* control over your network through the GUI network manager.

(I used the tutorial at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) and still have some degree of control)

---

### Post by s1337m on 2008-06-21
> **lisati said:**
> Some soultions suit some people better than others; you'll probably find that you still have *some* control over your network through the GUI network manager.

(I used the tutorial at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) and still have some degree of control)

Thanks for the response.  We are both looking at the same tutorial, so how did you maintain some control over your network?  Does it list your wireless networks?

---

### Post by wariskampar on 2008-06-22
just posting because i'm interested with this subject. In my case, at first I was struggling to get the wireless working (i/m using ipw2200 driver) up to the point I give it up all together. However recently, out of curiosity I tried it once again and quite surprisingly it was working. I maybe wrong but I think the kernel update (from 18 to 19) sorts up the problem. I'm using default Hardy Heron Network Manager to establish connection.

edit; earlier I used wicd which somebody told me is the best alternative for Network Manager but I can not find ways to use it correctly.

---

