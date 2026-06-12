---
title: "Partitioning"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by leilton on 2012-02-19
Sorry if this has been asked before, awful lot of threads to go thru.

Have now got used to Xubuntu, and have decided that want to install Kubuntu as a back up, however have never had to do any partitioning myself, so can I ask what may seem like a silly question to you experts out there.

When you start the install, you are asked if

A.  Replaces other Linux
B.  Use available space
C. Other

A. is a no no.   So my question is if I pick B, will the installation know how much space is required, or do I have to allocate it?

Now you see why I used Absolute Beginners Talk.

Any help will be much appreciated.

:confused:

---

### Post by jaddi27 on 2012-02-19
Have you thought about installing the Kubuntu packages on your existing system? By doing this, you would be able to use both Xubuntu and Kubuntu by selecting which one to use on the login screen. To do this, select the kubuntu-desktop package using the package manager you have installed (such as apt from the command line) - this should install all of the required packages.

If you want a separate installation, you should select either of (B) or (C). The available space option should work out how to adjust the partition sizes to fit in a new installation, but before installing just check that what it proposes in the installer looks alright. The third option, Other, will allow you to manually partition your drive to fit in the new installation. The Other option will give you the best control over how the drive is partitioned for the new install.

---

### Post by Skatertjah on 2012-02-19
I've found that when you install both KDE and another Desktop Environment (Gnome, LXDE, whatever) your menus get all jumbled up with extra software entries. It's a lot cleaner to work with 2 seperate systems although that will also introduce some annoyances depending on what you use it for.

I've always found gParted the best program to use for partitioning jobs. It can create, remove and even resize (most) partitions. If you have any free space on your harddrive you can easily create a (10GB) partition.

To install gParted open up a command line and copy this:
```

sudo apt-get install gparted

```

When you run it it will scan your harddrive for existing partitions.

Be very careful with resizing! Things can go wrong!

Always back-up your data some way or another before doing any partitioning!


Hope that helped! :D

---

### Post by leilton on 2012-02-19
> **jaddi27 said:**
> Have you thought about installing the Kubuntu packages on your existing system? By doing this, you would be able to use both Xubuntu and Kubuntu by selecting which one to use on the login screen. To do this, select the kubuntu-desktop package using the package manager you have installed (such as apt from the command line) - this should install all of the required packages.

If you want a separate installation, you should select either of (B) or (C). The available space option should work out how to adjust the partition sizes to fit in a new installation, but before installing just check that what it proposes in the installer looks alright. The third option, Other, will allow you to manually partition your drive to fit in the new installation. The Other option will give you the best control over how the drive is partitioned for the new install.


You are a genius, and it is so nice to have people like you to give us idiots a hand, however, and yes it is probably me, have installed, and very happy with same, BUT cannot get anything other than K when I start up.

Welcome screen says what do I want, and I say, in this case X, and gos direct to K.

How do I tell it which one I want.

Many many thanks for help so far

:confused:

---

### Post by leilton on 2012-02-19
> **leilton said:**
> You are a genius, and it is so nice to have people like you to give us idiots a hand, however, and yes it is probably me, have installed, and very happy with same, BUT cannot get anything other than K when I start up.

Welcome screen says what do I want, and I say, in this case X, and gos direct to K.

How do I tell it which one I want.

Many many thanks for help so far

:confused:

Yes you have guessed already, have just found the almost hidden arrow that gives me the choices I want.

Did say was an idiot,

---

### Post by oldfred on 2012-02-19
Some examples of installs with screen shots so you can follow along.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I prefer to partition in advance, but you have to do that from a Ubuntu liveCD/USB or download the gparted liveCD.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by leilton on 2012-02-19
> **Skatertjah said:**
> I've found that when you install both KDE and another Desktop Environment (Gnome, LXDE, whatever) your menus get all jumbled up with extra software entries. It's a lot cleaner to work with 2 seperate systems although that will also introduce some annoyances depending on what you use it for.

I've always found gParted the best program to use for partitioning jobs. It can create, remove and even resize (most) partitions. If you have any free space on your harddrive you can easily create a (10GB) partition.

To install gParted open up a command line and copy this:
```

sudo apt-get install gparted

```

When you run it it will scan your harddrive for existing partitions.

Be very careful with resizing! Things can go wrong!

Always back-up your data some way or another before doing any partitioning!


Hope that helped! :D
Sorry having to respond this way, kept trying to do quote, and told not enough characters.

Any way, took Jeddi27s advise and got what I want from Package Manager, and took your advise and now have a Partition Manager so can see what I have or have not.

Many thanks for your help

---

