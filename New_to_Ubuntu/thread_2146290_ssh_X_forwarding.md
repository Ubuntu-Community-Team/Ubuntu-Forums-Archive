---
title: "ssh X forwarding"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by T2manner on 2013-05-18
Hello

I'm trying to access an ubuntu machine  that my university has given me access to by ssh and X fowarding. 
Once I log into the machine via ```
ssh -X
``` on my netbook with ubuntu 13.04, I run ```
gnome-session
``` to try to access a graphical interface of the machine.  After this runs, the result is a horrible combination of an old gnome desktop with the current unity desktop.  It's not at all useful.

On my macbook, this runs more like what is expected:   a new window opens with the ubuntu gnome desktop.

I thought that trying to ssh on an ubuntu computer would work much better than on a macbook, so maybe I am doing something wrong?

Thanks for the help

---

### Post by HermanAB on 2013-05-18
Don't do that.  Your own machine already has a desktop.  Trying to overlay it with a remote desktop is a pointless waste of network bandwidth.

Simply run the one or two graphical programs that you want to access directly and they will run transparently on your local gnome/unity desktop.

---

