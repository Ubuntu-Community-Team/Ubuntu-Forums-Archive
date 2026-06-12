---
title: "Remote Connect - Ubuntu Server"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by VFaretrajr on 2013-12-27
Hi all,

I have an interesting scenario that i'd like to see if there is an answer to. 

I am currently running an Ubuntu server (12.04 LTS) that is accessible from the outside world. Meaning - my home router is setup with dynamic DNS which is setup with an SSH port forward to my Ubuntu server - and it works perfectly. Currently, the server is has not been installed with the GUI interface and is strictly command line.

What I would like to know is if / how does one connect to the remote Ubuntu server from a windows PC where the front end can be a GUI to the Ubuntu kernel on the remote end. Basically, it's like a hybrid remote desktop. 

It's a long shot, I know but it's a n00b talking!

Thanks,
Vincent

---

### Post by cybergalvez on 2013-12-27
not a long short at all, you've already done the hard work of getting it sup and running with access through your router. If you actually want to GUI then you will have to first install one of the GUI desktop frontends, Unity, Gnome, KDE or Xfc, I personally use Gnome. Next you have to set up remote access it, I would suggest freeNX or my favorite x2Go which uses ssh for encryption. There are Windows clients for both.

---

