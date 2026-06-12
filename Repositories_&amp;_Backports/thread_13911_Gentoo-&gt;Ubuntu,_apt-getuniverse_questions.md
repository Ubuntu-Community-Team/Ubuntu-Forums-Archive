---
title: "Gentoo-&gt;Ubuntu, apt-get/universe questions"
date: 2005-02-03
forum: Repositories &amp; Backports
---

### Post by shimp999 on 2005-02-03
Hi!
I've used Gentoo Linux for the past year or so and I decided to give Debian a try.  I really only used Gentoo for the package management (compiling everything gets old after a while), but I figured I'd try Debian again with its new installer and all.  Debian was nice, apt was nice, I stumbled across Ubuntu, wondered what all the rave was, downloaded the installer and here I am, loving it :p

I have a few questions though...I've searched the forums and can't quite find the answer.

1)  I followed these instructions here: [Use Ubuntu and Debian repositories](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.7453904394) 
Everytime I load Synaptic I get a message box with:  No priority (or zero) specified for pin.
Is this something I should worry about?

2)  When I enable "universe" in my /etc/apt/sources.list, is this equivalent of added Debian Sarge (testing) repositories to my list?  If not, how would I do that.

Thanks!

---

### Post by unperson on 2005-02-05
Welcome to Ubuntu!

I'm far from an expert, but here's my 2 cents.  First, let me make a general comment.  As I understand it, Ubuntu is based off of a snapshot of the Debian unstable repository.  So all this business of using Ubuntu with Debian packages may not make a lot of sense, since any Debian package should be available in Ubuntu in either the universe or multiverse repositories, unless it's newer than the last snapshot or you want a newer version than what's in Ubuntu.  So make sure you really need these packages before you try to use them.  Using package from the current unstable repository might work (maybe), but would likely lead to a lot of unsatisfied dependancies.

If you need newer versions of things, you could also try the "unstable" version of Ubuntu, Hoary Hedgehog.  Or, if you just want a select few packages, you could see if they're available through Warty backports.

[http://www.ubuntulinux.org/wiki/BreakMyUbuntu/view?searchterm=backports](http://www.ubuntulinux.org/wiki/BreakMyUbuntu/view?searchterm=backports)

Now in case that doesn't work, on to answer your specific questions:

1)  I don't have any experience with apt-pinning personally, but check out these two pages:

[http://www.ubuntulinux.org/wiki/PinningHowto/view?searchterm=debian%20repository](http://www.ubuntulinux.org/wiki/PinningHowto/view?searchterm=debian%20repository)
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

2)  As I said, universe and and multiverse make up the bulk of what was in the debian unstable repository at the time of the freeze, so if you enable those repositories you should be able to get the software you want.

Hope that helps,

Nick

---

### Post by llamakc on 2005-02-05
I too came from Gentoo and I'm running Hoary. Here is my /etc/apt/sources.list:
 
  #start
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
 
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
 
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
 #end
 
 I'm not sure if Ubuntu pins the same way that Debian did. Somebody more knowledgeable should come along.

---

### Post by shimp999 on 2005-02-09
I figured it out, did a lot of digging around and reading.  I too am running Hoary and here's my /etc/apt/sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) testing main contrib non-free
deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) testing main contrib non-free

deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./

To make sure there weren't any conflicts between Ubuntu repositories and Debian, I made an /etc/apt/preferences and put this:

Package: *
Pin: origin security.ubuntu.com
Pin-Priority: 1001

Package: *
Pin: origin archive.ubuntu.com
Pin-Priority: 1001

Works pretty well, ubuntu packages always get priority and if there's a certain package I want from Debian, I can pull it.  Although I get this error during apt-get update:

W: GPG error: [http://ftp.us.debian.org](http://ftp.us.debian.org) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

Although everything works fine otherwise...

---

