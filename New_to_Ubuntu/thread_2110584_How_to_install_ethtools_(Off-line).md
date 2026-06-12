---
title: "How to install ethtools (Off-line)"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by msinfo on 2013-01-30
hi experts,
i have dual boot system with Win7 and Ubuntu 11.04.
before problem internet was working fine on both OS.
two days ago, som cable problem occured, which cable guy troubleshooted by replacing faulty RJ45 connector.
from that point internet is working fine on Win7 but not on Ubuntu.
i have checked IPV4 settings of Ip, DNS, Net mask, they are same on both side.
when i ping default gateway from Win7 it gives response, but from Ubuntu it fails.

what i tried : 
disconnected cable for while.
deleted connection and remade connection on ubuntu

If you go through [http://ubuntuforums.org/showthread.php?t=2104427](http://ubuntuforums.org/showthread.php?t=2104427) , then you will see one person asked me to install ethtool to further investigate issue.

i have downloaded 4 files of version 3.7 from,
[http://www.kernel.org/pub/software/network/ethtool/](http://www.kernel.org/pub/software/network/ethtool/)

Since I am coming from Windows Environment, kindly show me steps  to install from stand -alone executable file on Ubuntu.
What is .exe equivalent in Ubuntu

regards : msinfo

---

### Post by ACubed10 on 2013-01-30
> **msinfo said:**
> hi experts,
i have dual boot system with Win7 and Ubuntu 11.04.
before problem internet was working fine on both OS.
two days ago, som cable problem occured, which cable guy troubleshooted by replacing faulty RJ45 connector.
from that point internet is working fine on Win7 but not on Ubuntu.
i have checked IPV4 settings of Ip, DNS, Net mask, they are same on both side.
when i ping default gateway from Win7 it gives response, but from Ubuntu it fails.

what i tried : 
disconnected cable for while.
deleted connection and remade connection on ubuntu

If you go through [http://ubuntuforums.org/showthread.php?t=2104427](http://ubuntuforums.org/showthread.php?t=2104427) , then you will see one person asked me to install ethtool to further investigate issue.

i have downloaded 4 files of version 3.7 from,
[http://www.kernel.org/pub/software/network/ethtool/](http://www.kernel.org/pub/software/network/ethtool/)

Since I am coming from Windows Environment, kindly show me steps  to install from stand -alone executable file on Ubuntu.
What is .exe equivalent in Ubuntu

regards : msinfo

a .exe equivalent in Ubuntu would be a .deb. Hopefully someone has an answer for you

also have you tried upgrading to 12.04 or 12.10? possibly might fix broken network driver?

---

### Post by msinfo on 2013-04-22
Hi,
Thanks to those, who tried answering.
Don't know how, but when today, I boot machine in Ubuntu OS, I could use, my Internet connection perfectly.
This is second time, when a Ubuntu problem, has been solved automatically, without any change in settings, or software.
Note: I was trying to install ethtool, to diagnose my internet connection problem, but now, it  has been auto solved. Don't know how?

---

### Post by schragge on 2013-04-22
With a working internet connection you can install *ethtool* with all the usual methods: Ubuntu Software Center, Synaptic Package Manager, apt-get, aptitude etc. I'll try to show how to do this without internet. However, note that for old unsupported releases like yours URLs in */etc/apt/sources.list* should point not to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) or its mirrors, but to *[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)*.

On a network-connected machine, download the deb package for your  release and architecture from  [http://old-releases.ubuntu.com/ubuntu/pool/main/e/ethtool/](http://old-releases.ubuntu.com/ubuntu/pool/main/e/ethtool/) (or from  [http://archive.ubuntu.com/ubuntu/pool/main/e/ethtool/](http://archive.ubuntu.com/ubuntu/pool/main/e/ethtool/) for currently  supported releases).
In your case (Ubuntu 11.04), it's probably either [ethtool_2.6.37-1_amd64.deb]("http://old-releases.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.37-1_amd64.deb") (64-bit) or [ethtool_2.6.37-1_i386.deb]("http://old-releases.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.37-1_i386.deb") (32-bit).
In terminal, you can display the native architecture of your system with ```
dpkg --print-architecture
```

Then install the downloaded package on the target system either by clicking on it in file manager or, in terminal, with
```
sudo dpkg -i path/to/folder/with/the/package/ethtool*.deb
```

---

### Post by msinfo on 2013-04-22
I never hoped, I would get a complete answer after what I wrote in my previous reply.
But, thanks[**[COLOR=#000000] schragge[/COLOR]**]("http://ubuntuforums.org/member.php?u=1783515") 	 [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG] I got necessary info, and I tried that by installing ethtool offline. It worked.
Once again thanks Schragge! :P

---

