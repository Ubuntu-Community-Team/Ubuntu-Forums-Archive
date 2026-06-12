---
title: "Not able to run sudo apt-get update"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by bseaam on 2013-12-05
Hello,
I am running Ubuntu Server 12.10 on an old Dell computer. About a year ago I had everything working well, decided to do a fresh install and am now having problems.

I am trying to install software through ```
sudo apt-get install *softwareName*
```, however I get the error message ```
E:Unable to locate package *softwareName*
```.  I have read other forums and posts and have checked my ```
 /etc/apt/sources.list 
``` file and all the sites/archives are uncommented.  I have successfully pinged Google (using the ip address 74.125.225.180) so I am connected to the internet.  As a result, I figured I needed to update my system (I don't think I ever did after initial installation). I have tried ```
sudo apt-get update
``` many times and always receive the same message: 

```
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease


Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease


Err [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease


Err [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg
  Temporary failure resolving 'archive.canonical.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg
  Temporary failure resolving 'extras.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease


Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease


Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease


Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/quantal/InRelease)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/InRelease)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/InRelease](http://security.ubuntu.com/ubuntu/dists/quantal-security/InRelease)


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/quantal/InRelease](http://archive.canonical.com/ubuntu/dists/quantal/InRelease)


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/InRelease](http://extras.ubuntu.com/ubuntu/dists/quantal/InRelease)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg)  Temporary failure resolving 'extras.ubuntu.com'


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/quantal/Release.gpg](http://archive.canonical.com/ubuntu/dists/quantal/Release.gpg)  Temporary failure resolving 'archive.canonical.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.
```

From what I understand, my server cannot reach the websites, however it is connected to the internet. My guess is that this is also why it cannot download software. As a result, I believe my server is having trouble resolving domain names. 

This is extremely frustrating as I cannot add any software to the server.... any ideas as to why this is happening are extremely welcome! 
Thanks!

---

### Post by fantab on 2013-12-05
Try changing the Update server. 'Software Center' -> Edit ->Software sources -> select another server.

Then run the following:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

Post errors, if any.

---

### Post by codenine75a on 2013-12-06
I think v12.10 is unsupported somehow as a default install.  I understand maybe it is an "unstable" version of 12.04.  To make it easy without messing with the configurations files too much I recommend to use v12.04 or v13.10.  I know that error because I have a copy of version 10.10 64-bit on DVD and I cannot upgrade it at all because it is not supported anymore.  I blame the linux ratrace for keeping up with the Jones'

---

### Post by philinux on 2013-12-06
Post your sources list please.

---

### Post by fantab on 2013-12-06
12.10 had 18months support and it is still in support upto April 2014.

---

### Post by bseaam on 2013-12-06
Thanks for the replies,

@Fantab, Nothing changed when I did apt-get update, wasn't able to completely remove everything because there was a directory there though.

@philunix, This is my sources.list file:

```
# deb cdrom:[Ubuntu-Server 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted


#deb cdrom:[Ubuntu-Server 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
```

---

### Post by steeldriver on 2013-12-06
Can you dig or ping the addresses it's complaining about? e.g.

```
dig us.archive.ubuntu.com
```

---

### Post by bseaam on 2013-12-06
The following is what happens when I ping or dig:

```
$ dig us.archive.ubuntu.com
; <<>> DiG 9.8.1-P1 <<>> us.archive.ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached
$ ping us.archive.ubuntu.com
ping: unknown host us.archive.ubuntu.com



```

It seems like I am not able to access sites via url, however I am able to via ip address...I'm not sure why though

---

### Post by steeldriver on 2013-12-06
So it looks like your system is unable to reach a DNS server - is this a real server box (no GUI, networking defined via /etc/network/interfaces) or are you using the GUI-based network manager?

What do

```

ls -l /etc/resolv.conf

cat /etc/resolv.conf

```

say?

---

### Post by newb85 on 2013-12-06
Sounds like a problem with your DNS server.

---

### Post by bseaam on 2013-12-06
Is there a way to fix this DNS server problem? 

@steeldriver Yes, it is a dedicated server box. There is no GUI interface. I only access it using ssh through PuTTY. Here are the two outcomes of those code segments:

```
$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 29 Nov 29 00:48 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

$ sudo cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```

---

### Post by steeldriver on 2013-12-06
... please clarify whether you are using /etc/network/interfaces or network manager

---

### Post by bseaam on 2013-12-06
I am using /etc/network/interfaces. I have set it to be static and always connect to the same local port on my router for port forwarding to work. The following is what my /etc/network/interfaces file look like:


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.1.25
netmask 255.255.255.0
gateway 10.0.1.1

```

---

### Post by steeldriver on 2013-12-06
Try adding a dns-nameservers entry e.g. for OpenDNS

```

# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.1.25
netmask 255.255.255.0
gateway 10.0.1.1
**dns-nameservers 208.67.222.222 208.67.220.220**

```

You can substitute Google DNS servers (8.8.8.8  and 8.8.4.4) or your local DNS server (maybe the same as your router, if it is set up as a forwarding DNS server). You will need to restart the networking service for the changes to take effect.

---

### Post by philinux on 2013-12-06
Earlier the links in post one were giving error but are now up. Try updating again.

---

### Post by bseaam on 2013-12-06
It worked! It worked! I added the google DNS servers and it I was successfully able to update! Thanks so much for all the help!

---

### Post by kulen19 on 2013-12-10
> **bseaam said:**
> It worked! It worked! I added the google DNS servers and it I was successfully able to update! Thanks so much for all the help!

Great :) Please select "Thread tools" and set this thread to "SOLVED".

---

