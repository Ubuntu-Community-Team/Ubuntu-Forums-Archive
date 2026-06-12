---
title: "Is there a program like peerguardian for linux?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by videocheez on 2008-05-04
I was wondering if any is knows of a program like Peerguardian for linux.  I did use moblock with fiest and gutsy but it is not working since my upgrade to gutsy.

Any help will be appreciated.  Thanks in advance,

VC

---

### Post by iSplicer on 2008-05-04
There sure is! Heres a nice HOWTO regarding how to install it:

[http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559)

Enjoy your torrenting (or whatever it is!)

---

### Post by KaliVoid on 2008-05-04
IpBlock

howto:
[http://ubuntuforums.org/showthread.php?t=530183]("http://ubuntuforums.org/showthread.php?t=530183")

---

### Post by corstar on 2008-05-04
Or you could use Peer Guardian for Linux.
A quick search on these forums would have given you this link
[http://ubuntuforums.org/showthread.php?t=95793]("http://ubuntuforums.org/showthread.php?t=95793")

Its very easy to set up and is reliable. I've used it for a long time with no problems.

---

### Post by videocheez on 2008-05-04
> **KaliVoid said:**
> IpBlock

howto:
[http://ubuntuforums.org/showthread.php?t=530183]("http://ubuntuforums.org/showthread.php?t=530183")

Thanks so much for you suggestion.  This program looks to be pretty nice.  I will try your suggestions later on today on one computer to see how it works.  Another person suggested peer guardian for linux. Duh.  I didn't think to look for that but I think I will give ipblock a chance based on the simplicity of the guide and the fact that i like to try Linux specific applications.  
How is this program on resources?  My file sharing PC is an old P3 and I need to be careful not to bog it down.

Thanks again,

VC

---

### Post by videocheez on 2008-05-04
> **KaliVoid said:**
> IpBlock

howto:
[http://ubuntuforums.org/showthread.php?t=530183]("http://ubuntuforums.org/showthread.php?t=530183")

Okay.  I'm ready to install the version for Hardy I read to install  with gdebi.  What does this mean.  So far I have only been able to install with synaptic.  Please let me know what does install with gdebi mean.

Thx,

DS

---

### Post by wolfen69 on 2008-05-04
installing with gdebi means that if you click a .deb file, it will install for you. very easy. also, ktorrent and deluge have the ability to import blocklists that you can get from [HERE]("http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4") just unpack them and point your torrent client to the list. if you put the list in your home folder, the path would be: /home/yourname/level1.txt (level1 blocklist being the most popular)

---

### Post by KaliVoid on 2008-05-04
hi

its great on resources because you dont have to use the GUI
its auto load on boot , im using old pc too and its no bother .

the only time it stop (in my experience) is when you
disable the net card u have to restart it.

type ```
sudo ipblock -h
```
to see all the commands u will need
(all commands need "sudo")

---

### Post by videocheez on 2008-05-04
> **wolfen69 said:**
> installing with gdebi means that if you click a .deb file, it will install for you. very easy. also, ktorrent and deluge have the ability to import blocklists that you can get from [HERE]("http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4") just unpack them and point your torrent client to the list. if you put the list in your home folder, the path would be: /home/yourname/level1.txt (level1 blocklist being the most popular)

Cool. Just like clicking on a windows *.exe file. Even I can handle that.  I'm currently using azureus mainly because if its remote HTML plugin feature.  I would be interested in using one of the linux torrent clients if i can remotely upload torrents and take advantage of importing blocklists.  I have an old P3 that I use just for filesharing and I like to remotely upload torrents and use VNC to control the nicotine for music sharing and feel more comfortable with 24 x 7 iplist blocking.

Thx,

VC

---

### Post by iswa on 2008-05-04
I wonder if your original problems with moblock are related to this thread?:

[http://ubuntuforums.org/showpost.php?p=4552578&postcount=1134](http://ubuntuforums.org/showpost.php?p=4552578&postcount=1134)

There's also a really good page on the wiki regarding Moblock (forgive me if you've seen it already):

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by videocheez on 2008-05-04
> **iswa said:**
> I wonder if your original problems with moblock are related to this thread?:

[http://ubuntuforums.org/showpost.php?p=4552578&postcount=1134](http://ubuntuforums.org/showpost.php?p=4552578&postcount=1134)

There's also a really good page on the wiki regarding Moblock (forgive me if you've seen it already):

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

thanks for your advice. if i use moblock again, I will try this suggestion but I have since uninstalled it and am now using ipblock.  i think i will give this one a try for ahile.  it was very easy to install and has a nice gui for configuration

---

### Post by jre on 2008-05-06
> **corstar said:**
> Or you could use Peer Guardian for Linux.
A quick search on these forums would have given you this link
[http://ubuntuforums.org/showthread.php?t=95793]("http://ubuntuforums.org/showthread.php?t=95793")

Its very easy to set up and is reliable. I've used it for a long time with no problems.
But it's dead. No developers, no support.
I suggest IPList or MoBlock instead.

---

