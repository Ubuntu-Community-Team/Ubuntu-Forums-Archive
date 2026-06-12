---
title: "ubuntu 11.04 lexmark x6170"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by klein de usa on 2011-09-23
hi 
has any one got this printer to work in 11.04, i have tried everything i can find, it finds the printer and it installs the printer but fails to print. i down loaded the rpm from lexmark and installed it different ways but nothing works and i haven't seen where anyone had tried it on 11.04? 
has anyone on 11.04 got it working ?

---

### Post by wolfen69 on 2011-09-24
An rpm will not work in ubuntu. You need to convert it to a deb file using alien.

---

### Post by klein de usa on 2011-09-24
thanks wolfen69
all ready did that, something has changed in 11.04 with cups or how usb is handled.

---

### Post by klein de usa on 2011-09-24
hi 
i found a post on linux mint forum that explains how to install the z55 driver in a 64bit system , the post is for 9.10 and i'm trying to get it to work in 11.04 and i have hit a snag, i'm hoping someone can help me out.

locate libstdc++.so. in 10.04 gives me:
 
$locate libstdc++.so.
/usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.6.0.13
/usr/lib32/libstdc++.so.6
/usr/lib32/libstdc++.so.6.0.13

locate libstdc++.so. in 11.04 gives me:

$locate libstdc++.so.
/usr/lib/libstdc++.so.5
/usr/lib/libstdc++.so.5.0.7
/usr/lib/x86_64-linux-gnu/libstdc++.so.6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14


[http://forums.linuxmint.com/viewtopic.php?f=51&t=58575]("http://forums.linuxmint.com/viewtopic.php?f=51&t=58575")

in this forum post it wants me to:

sudo mv /usr/lib/libstdc++.so.5* /usr/lib32/

for 11.04 should it be: 
sudo mv /usr/lib/libstdc++.so.5* /usr/x86_64-linux-gnu/

---

