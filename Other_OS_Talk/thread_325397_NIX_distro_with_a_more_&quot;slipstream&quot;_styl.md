---
title: "*NIX distro with a more &quot;slipstream&quot; style of upgrading?"
date: 2006-12-25
forum: Other OS Talk
---

### Post by jtfolden on 2006-12-25
Hey all,

After years of trying and trashing (within a week later) various Linux distros, I finally tried Ubuntu this year and have had it running for 2 months on a secondary system here. It's not perfect and doesn't seem ready to replace my main OS anytime soon but it's quite usable for most tasks and I've not run into any show stopping issues.. HOWEVER;

Up until now I'd never stuck with Linux long enough to understand the whole "assembled" release cycle method for distros like Ubuntu... It seems like a particular version and it's repositories is assembled and then "frozen" (except for minor bug fixes) for release. The user is then stuck with that snapshot, more or less, until the next version is released months later.

The problem here for me is that I like having access to the "latest and greatest" when it comes to frequently used apps to take advantage of bug fixes AND new features. If I have to resort to compiling it on my own then it sort of defeats the purpose of using a distro with easy to use package managers.

Are there any distros where apps and updates are provided in a 'constant flow' or more slipstream style method of updating rather than having to wait 6-12 months for a new major release? I've head mentioned of both FreeBSD and Debian Unstable but don't know much about either and don't have a complete understanding of their methods after reading a bit  around the 'net. FreeBSD Seems more suited to server use. I know Ubuntu pulls packages from 'Debian Unstable' but I'm unclear if you can actually run 'Debian Unstable or if it even provides app updates in the way I am looking for?

If you haven't noticed yet, I tend to ramble on :mrgreen: but I'll stop now!

Thanks,
John

---

### Post by cilynx on 2006-12-25
Debian.  Run "unstable" or "testing".  They both update constantly.  Only "stable" freezes into releases.
Just to set your mind at ease, I've run Debian Unstable on "less important" production servers for 10 years.  I have had only one single incident of system difficulties due to a newly installed update.
[http://www.debian.org/releases/unstable/](http://www.debian.org/releases/unstable/)

Ubuntu is a more happy / corporate / frozen version of Debian.  I've heard rumors than Feisty is going to continue on as "Ubuntu Unstable" even after the next release.  Many of us want this type of "release cycle".  We'll have to see...

---

### Post by RAV TUX on 2006-12-25
> **jtfolden said:**
> Hey all,

After years of trying and trashing (within a week later) various Linux distros, I finally tried Ubuntu this year and have had it running for 2 months on a secondary system here. It's not perfect and doesn't seem ready to replace my main OS anytime soon but it's quite usable for most tasks and I've not run into any show stopping issues.. HOWEVER;

Up until now I'd never stuck with Linux long enough to understand the whole "assembled" release cycle method for distros like Ubuntu... It seems like a particular version and it's repositories is assembled and then "frozen" (except for minor bug fixes) for release. The user is then stuck with that snapshot, more or less, until the next version is released months later.

The problem here for me is that I like having access to the "latest and greatest" when it comes to frequently used apps to take advantage of bug fixes AND new features. If I have to resort to compiling it on my own then it sort of defeats the purpose of using a distro with easy to use package managers.

Are there any distros where apps and updates are provided in a 'constant flow' or more slipstream style method of updating rather than having to wait 6-12 months for a new major release? I've head mentioned of both FreeBSD and Debian Unstable but don't know much about either and don't have a complete understanding of their methods after reading a bit  around the 'net. FreeBSD Seems more suited to server use. I know Ubuntu pulls packages from 'Debian Unstable' but I'm unclear if you can actually run 'Debian Unstable or if it even provides app updates in the way I am looking for?

If you haven't noticed yet, I tend to ramble on :mrgreen: but I'll stop now!

Thanks,
John

Sabayon/Gentoo and rPath

---

### Post by jtfolden on 2006-12-25
> **cilynx said:**
> Debian.  Run "unstable" or "testing".  They both update constantly.  Only "stable" freezes into releases.
Just to set your mind at ease, I've run Debian Unstable on "less important" production servers for 10 years.  I have had only one single incident of system difficulties due to a newly installed update.
[http://www.debian.org/releases/unstable/](http://www.debian.org/releases/unstable/)


Thanks. :-) Now the question is, how do I make the jump to "sid"? Do I just install the latest stable release and then change the sources.list to start pulling from the "unstable" / "Testing" repositories?

John

---

### Post by cilynx on 2006-12-25
You could do that (I probably would) or you can try out the new installer which will give you a "testing" system which you can then upgrade to unstable if you want

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by jtfolden on 2006-12-26
> **cilynx said:**
> You could do that (I probably would) or you can try out the new installer which will give you a "testing" system which you can then upgrade to unstable if you want

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)


Okay, installing using the Testing Net CD. Edited the sources.list to add the sid repositories and the dist-upgrade went just fine... Everything seems to be running well. However, it appears that a great majority of the GNOME/Gtk packages (2.14) even in unstable are behind those available with Edgy. I was under the impression that Feisty pulled it's packages from Debian unstable but it (Feisty) already has 2.17.x dev releases.


John

---

### Post by 3rdalbum on 2006-12-26
I hear that Ulteo is going to use rolling updates too.

---

### Post by manmower on 2006-12-26
Arch has a rolling release system, and is fairly bleeding edge. Works great for me... I've had very few issues so far and when they occur solutions are usually in the news/forum/wiki within hours.

---

