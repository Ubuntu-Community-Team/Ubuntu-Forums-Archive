---
title: "system is slower. what could be  the reasons"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by milanvora2 on 2008-05-28
I'm noticing that the system is much slower now than a month back when i first installed ubuntu. It's realyl not that abd, but the beast is not flying like it did on the first few days.

What could be the possible reason:

a) I have some kde tools that I'm using which are slowing down 
gnome 

b) I have much more packages installed than at start as i was trying out software

c) I have more files on my hdd  (i copied 20g of photos and music on my 320gb hdd) ucrrent usage approx 60gb

d) Graphic performance has been slower (new drivers) i'm using ati fglrx

e) Other unknow reason

What would you recommend:

1) new clean install  (i'd however have to setup nfs, samba ... )
2) other solution

Thanks for sharing your experience

---

### Post by Joeb454 on 2008-05-28
Are you running Desktop Effects? (i.e. Compiz Fusion)

---

### Post by sayakb on 2008-05-28
a. and b. are the most probable reasons. Graphics won't unnecessarily "slow down" and that too winthin just a month. Get rid of unwanted packages.. Or do a clean install and install only that much you need. If you want to test some package, download and install it, use it, and if you find it useless, **purge** it by:
```
sudo apt-get purge packagename
```Actually it's not about the KDE tools, its the KDE libraries that were installed while installing those KDE apps which may be numerous.
Also try this before you take any permanent measures:
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install localepurge
sudo localepurge
```All in a row.

---

