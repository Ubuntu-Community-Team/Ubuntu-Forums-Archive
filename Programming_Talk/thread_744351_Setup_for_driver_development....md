---
title: "Setup for driver development..."
date: 2008-04-03
forum: Programming Talk
---

### Post by bzamora on 2008-04-03
Hi...

I'm new to this forum and I hope this is not a bad starting question, but here goes...

I have an interest in how drivers are developed in Linux. That said, I completed a tutorial that I found at [http://www.freesoftwaremagazine.com/articles/drivers_linux](http://www.freesoftwaremagazine.com/articles/drivers_linux)

Actually, I should say, I completed the tutorial on a CentOS 5 platform. Having recently set myself up with an Unbuntu platform on my desktop system, I thought I would try the same tutorial again. I'm not even getting to first base with it on the Ubuntu platform, so I'm reaching out for some help...

I'm certain some of my issue is a lack of understanding on the structure of a Debian based Linux. Most of my work has taken place in the Red Hat environment.

Anyway, as I said, I'm following the tutorial and I can't even get the most simple starting component to compile. I thought I had done what I needed to, to obtain kernel header files and/or linux source, but I'm not even certain I did that correctly. In CentOS it was pretty easy using the yum tool. In Ubuntu it seemed like I was doing it correctly using the Synaptic package manager. Nevertheless, I'm certain I have NOT done things correctly to get myself set up.

Here is some text from my terminal session:

root@bzamora-desktop:~# pwd
/root

root@bzamora-desktop:~# ls
beacon      linux-source-2.6.22-2.6.22                linux-source-2.6.22_2.6.22-14.52.dsc    src
beacon_doc  linux-source-2.6.22_2.6.22-14.52.diff.gz  linux-source-2.6.22_2.6.22.orig.tar.gz

root@bzamora-desktop:~# cd src
root@bzamora-desktop:~/src# ls
Makefile  Makefile~  Makefile.new  Makefile.old  nothing.c

root@bzamora-desktop:~/src# cat nothing.c
#include <linux/module.h>

MODULE_LICENSE("Dual BSD/GPL") ;

root@bzamora-desktop:~/src# cat Makefile
obj-m += nothing.o

root@bzamora-desktop:~/src# make
make: *** No targets.  Stop.

root@bzamora-desktop:~/src# cd /usr/src
root@bzamora-desktop:/usr/src# ls
linux-headers-2.6.22-14  linux-headers-2.6.22-14-generic  linux-source-2.6.22  linux-source-2.6.22.tar

root@bzamora-desktop:/usr/src# uname -r
2.6.22-14-generic
root@bzamora-desktop:/usr/src# 


Anyway... the referenced tutorial does not present much information about getting set up properly for ANY environment, which in my mind is not a good way to write a tutorial. Once I was set up properly in CentOS, following the tutorial was quite easy and everything worked properly.

Can anybody here help me get my framework set up so that I can complete this tutorial on an Ubuntu platform?

Thanks,

Brett

---

### Post by gekkio on 2008-04-05
I'm not an expert on driver development on Ubuntu, but I managed to compile the first part of the tutorial this way (I've included all the steps, even the trivial ones):

```
sudo apt-get install build-essential linux-source
cd /usr/src
sudo tar xjvf linux-source-2.6.22.tar.bz2
cd linux-source-2.6.22
sudo cp /boot/config-2.6.22-14-generic .config
sudo make
sudo make modules
```

After that you should be able to compile your module with:

```
cd WHERETHEMODULESOURCEIS
make -C /usr/src/linux-source-2.6.22 M=WHERETHEMODULESOURCEIS modules
```

Two recommendations:
[LIST]
[*]You don't need to compile modules as root. Only the first part of this post (setting up the framework) needs root privileges and it can be done with sudo.
[*]You don't need to compile the whole kernel just to build a module (the headers should be enough). This however needs some Makefile magic which is beyond my knowledge (and it seems that the tutorial doesn't do it that way). I suggest you do some researching, because it's the modern way to do it. All the modules I've compiled on my Ubuntu boxes (since Ubuntu Edgy) have required only the headers. You also need to rebuild the kernel after each kernel update if you compile against the full kernel.
[/LIST]

Hope this helps. :)

---

