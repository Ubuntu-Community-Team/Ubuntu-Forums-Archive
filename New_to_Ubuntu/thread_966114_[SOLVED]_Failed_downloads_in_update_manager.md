---
title: "[SOLVED] Failed downloads in update manager"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by mundo on 2008-11-01
When I run Update Manager it keeps failing on the intrepid Translation-en_GB packages. How can I get these to not fail?

---

### Post by inportb on 2008-11-01
Perhaps you should try again in a few hours or next day. My updates have been smooth though, so this might be a transient issue.

---

### Post by germanix on 2008-11-01
I do not know why it is failing in your case, but check out this link to make sure you are updating correctly.
[http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server)

---

### Post by bumanie on 2008-11-01
Go to software sources and click on the arrow in the window where your server is mentioned. Click on other and a scan will follow that will choose the best server for you - often a local server, rather than the main server. They are often not as heavily utilised and downloads are often less problematic.

---

### Post by stimpack on 2008-11-01
Mine fails on this too, I remember during install it failed and said to remember to set your language, which I have done now.

But still get translation-en_GB errors on apt.

---

### Post by Kevbert on 2008-11-01
You may also need to run in terminal 
```
sudo apt-get install -f
sudo dpkg --configure -a
```to repair any damaged or partially installed packages on your PC.

---

### Post by petronell on 2008-11-01
I think there may have been an issue on the UK server today.

I had some updates fail this morning on my Ibex install. Tried running update manager again a couple of hours later and all worked as normal.

Are you still seeing this failure?

daveR

---

### Post by mundo on 2008-11-01
> **Kevbert said:**
> You may also need to run in terminal 
```
sudo apt-get install -f
sudo dpkg --configure -a
```to repair any damaged or partially installed packages on your PC.

This appears to have done the trick, many thanks.

---

