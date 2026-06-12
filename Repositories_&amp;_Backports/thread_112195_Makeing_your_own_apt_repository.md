---
title: "Makeing your own apt repository?"
date: 2006-01-03
forum: Repositories &amp; Backports
---

### Post by nbx909 on 2006-01-03
I'm a part of the [Nubuntu]("http://nubuntu.org") development team and i got the lucky task of figuring out how an apt repository works and how to create one for possible future implementation in nubuntu. I've googled for hours and finally decided to try asking it here.
How does an apt repository work? and How can i create my own?

Thanks in advance,

---

### Post by Seveas on 2006-01-04
[QUOTE=nbx909]I'm a part of the [Nubuntu]("http://nubuntu.org") development team and i got the lucky task of figuring out how an apt repository works and how to create one for possible future implementation in nubuntu. I've googled for hours and finally decided to try asking it here.
How does an apt repository work? and How can i create my own?

Thanks in advance,[/QUOTE]

You could look at Falcon, the software I created and use for maintaining my repository and mirrors.

---

### Post by az on 2006-01-04
Where is it?  I looked in the repositories and I googled.  I can not find it.

---

### Post by nbx909 on 2006-01-04
Yeah it would help if you gave a link to something i could use, however i've found people using it from google here is one of the sites that use it... [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/)
We have found a way to make our own repos here is the [link...]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-sources.list") The main problem is that we would have to run a cron job on every sub section in the repos that we would want to be updated and it would have to be on a debain based machine or one with dpkg installed on it. I believe our current host is running fedora core so we are running into a problem there, along with the fact that we've already eaten most of his bandwidth due to being featured on Digg.com.

---

### Post by Seveas on 2006-01-04
That repository is a mirror of mine, so no surprise it uses Falcon ;)

You can find the software in my repository or on one of the mirrors - see wiki.ubuntu.com/SeveasPackages

After looking at the nubuntu homepage I get the idea that your repository is a bit too big for Falcon, which is aimed at smaller repositories (tested to a few GB max, and may not scale well). The official debian and ubuntu archives use DAK, which is a real pain in the ass to setup, but scales to Debian/Ubuntu sized archives.

Falcon is small, easy to configure (one simple .ini file, optionally an html template) and as said before, I have no idea how good or bad it scales when facing lots of GB and lots of packages.

---

### Post by Seveas on 2006-01-04
Oh, and both dak, falcon and any other repo tool I know of require a debian setup.

---

### Post by nbx909 on 2006-01-04
hrm okay thank you.

---

