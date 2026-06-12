---
title: "Happy at final set-up, but two desktops extra, is it OK to remove them?"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by megenk11 on 2013-04-29
I am very decidedly living with Ubuntu Xfce for a long time and have a well personalized set-up.....except....
I need to remove Lubuntu and Openbox from my system, without gutting Ubuntu or running a whole new mini.iso install to my 12.10. I have only 1 GB sdram and a main 82.3 GB HDD with a 250GB HDD & 40GB HDD that I am totally blank on how to use with the GNU file system.
I enjoy the terminal interface most and use cairo-dock. I even found mesa to use my nvidia board and openGL yesterday!
I have learned that the purge command will get me in trouble as will the *, but is there a gentler way to remove lxde and openbox? It has taken me about 3 months to decide on my base software and distro needs, with an unstable system occurring every other day and causing a new install. I finally have it right except for a couple extra (desktops?, window managers?, display managers?) flavors to peel away. 
It takes me about 10 hours to customize an install.
Is this hopeless and I must re-install or can the clutter be safely removed? Help!

---

### Post by deadflowr on 2013-04-29
Look over this

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

---

### Post by megenk11 on 2013-04-29
Solved!!! I found a reference to apt-get rdepends that let me calmly take the extras out without removing the 40 or so hard gotten packages that a quick wipe out of lubuntu would have Thanks to the writers of the free pdf cosole commands!

---

### Post by megenk11 on 2013-04-29
solved!!!!!!!

---

### Post by ibjsb4 on 2013-04-29
You may want to look into a more powerful package manager. Apt-rdepends is nice, but dependencies can be checked with a mouse click with synaptic-package-manager (plus much more).

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

To install:

```
sudo apt-get install synaptic
```

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

