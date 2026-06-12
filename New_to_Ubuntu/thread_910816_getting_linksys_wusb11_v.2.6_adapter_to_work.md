---
title: "getting linksys wusb11 v.2.6 adapter to work"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by zeppelin222 on 2008-09-04
hi.
i just installed ubuntu tonight, and i am completely new to linux and ubuntu. i really have no idea what i'm doing. i'm dual booting winXP and trying to get the internet to work with ubuntu. ive read other posts but i'm such a beginner i can barely understand anything they're saying. ive read that i should install ndiswrapper, so i have the file i downloaded from the internet and brought over on a flash drive sitting on my desktop. it's called ndiswrapper-1.53.tar.tar. i have no idea what to do with it. i dont know what this program will do once i get it working, but i think i need it. anyone who is going to attempt to help me is going to have to be really simplistic. i can't undertsand ndiswrapper's installation instructions. thats how much of a beginner i am. to anyone who wants to take on the challenge of helping me, thanks in advance.

---

### Post by darrelljon on 2008-09-07
Have a look at [this guide]("http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux") (and similar ones on the same website). Be sure that your wireless adapter isn't already detected by ubuntu before you try to install ndiswrapper.

---

### Post by zeppelin222 on 2008-09-07
network manager isn't detecting anything. im not sure if it knows the adapter is there or not, but i suspect that it doesnt. thats why i got ndiswrapper, but i dont know how to install it or use it. i dont know where to get the windows driver for it either.

---

### Post by zeppelin222 on 2008-09-07
more info:
i read somewhere that there's no such thing as a .tar.tar file, and to rename it to .tar.gz. so i did. and i ran the command that was in ndiswrapper's install instructions online (tar -zxvf ndiswrapper-1.53.tar.gz) and i got this error back:

tar: ndiswrapper-1.53.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

wtf.
it appears that i can extract it just fine by double-clicking the  .tar.gz file, which opens it in an extracting program i can't remember the name of, but i dont know if this is any different from the other way, and where i should have it extract to / if it even matters where i extract it to. maybe i'm getting that error because i don't have the .tar.gz file in the right place (it's on the desktop). i dont know anything.

---

