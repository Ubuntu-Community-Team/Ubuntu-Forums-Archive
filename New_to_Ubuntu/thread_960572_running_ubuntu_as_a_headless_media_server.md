---
title: "running ubuntu as a headless media server?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by mynameischainsaw on 2008-10-27
hey guys, i just installed ubuntu 8.04 on an old hp laptop I had laying around in the hopes I could VNC into it, set up torrents, run freeNAS in a vm, and serve up videos/pictures/and music to my ps3.  I want this set up to be headless, and my hope is to do all the controlling of the computer through my macbook.  I've gotten VNC all set up, but I have a few questions from a stupid beginner:

1.)  is there anyway I can bypass the 'another user wants to VNC in, allow or deny?' pop up box in Ubuntu?  its a pain to have to run to the other room and hit 'allow' everytime i want to VNC in.  Is there a better way to take control of the computer?

2.)  is there a simple way to set up mediatomb to transcode everything for the ps3?

thanks in advance.

---

### Post by Xiong Chiamiov on 2008-10-28
If you're going to use it as just a media server, the better way is to use something like Ubuntu Server, keep the GUI off of the machine, and share your drives via NFS.  You can then mount them just like normal drives, and it will be considerably faster.

All administration can be done via ssh, which will force you to learn the terminal.

---

