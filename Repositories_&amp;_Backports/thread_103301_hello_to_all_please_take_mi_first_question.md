---
title: "hello to all// please take mi first question"
date: 2005-12-13
forum: Repositories &amp; Backports
---

### Post by sds012002 on 2005-12-13
hi there.

Please, I need somebody to help me. 

I want to get a net with 15 machines that works on Ubuntu Hoary. But my internet connection ys too slowly. (64K thru proxy server).

When I install Apt-cacher to make a local repository, broken packages that can´t be fixed makes me to find other way.

I'm trying with Debmirror, and today i can update one of the PCs but on other machines into the net, with the same sources.list file, synaptic says that can't aquire packages from the local repository, and the dialog says "error 403"

What can i do? what's the problem?Can you help me.

Thank you for help!!!!

---

### Post by anil_robo on 2005-12-14
Though I'm not an expert (yet), I'm sure someone will answer your question soon. In the meanwhile, you can try one thing:

When you use apt-get command, the files are downloaded to "/var/cache/apt/archives/"

I think you were able to use apt-cacher to download one app, you should copy that from /var/cache/apt/archives/ folder from that successful computer to the same directory of all other computers. This "may" solve your problem.

I'm sorry if this doesn't work - please let me know so that I can learn from you! :)

---

### Post by aysiu on 2005-12-14
You can try this:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

