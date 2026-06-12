---
title: "battery died during update"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Paul VW on 2008-11-02
I have a laptop running ubuntu and windows vista, during the last update I did I did not realise the laptop was not plugged in, and it went dead halfway through the update. Now when I boot up ubuntu I get as far as the log in screen, and then once you log in, I am left with a black white screen.

what's the best thing to do, re-install from a disk?

I dont want to loose windows as well!

---

### Post by scragar on 2008-11-02
firstly, try pressing **ctrl+alt+F1** to get a command line login, once your on run these commands:
```
sudo -i **## go root temp**
dpkg-reconfigure -a **## have dpkg find broken packages**
apt-get install -f **## fix any broken packages**
exit **## return to normal user**
exit **## log out**
```then press ctrl+alt+F7 to return to the gui and try logging in again.

---

### Post by pitchdiesel on 2008-12-08
I had the same thing happen.. except I can't even get to the login screen. I tried using a Windows recovery CD and after it partitions the disk and then restart it goes to a black screen. Trying to boot from the Ubuntu CD gives me the start screen with start or install and other options and then none of them work... my CD-ROM will read it fine up until that point where it'll start skipping.

---

### Post by nmz787 on 2008-12-16
check out my solution to this problem here:

[http://ubuntuforums.org/showthread.php?t=1011717&highlight=battery+died+solution](http://ubuntuforums.org/showthread.php?t=1011717&highlight=battery+died+solution)

---

