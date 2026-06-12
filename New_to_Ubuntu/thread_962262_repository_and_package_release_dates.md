---
title: "repository and package release dates"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by ufis on 2008-10-29
hi,

I am looking to install sun java 6u10 on my ubuntu 8.04

the repository only carries 6u07. I know I can download the bin from sun's site and install that. But this leads me to a couple of questions:

1. If I install the bin, will apt pick up future updates to the software?

2. Is sun java 6u10 in any repository available to 8.04?

3. Is there anywhere I can look to see what is available in repositories and/or whether some package will be available in future?

Thanks

---

### Post by macogw on 2008-10-29
1. No
2. maybe?
3. Synaptic lists everything, including the versions.  There are no upgrades after an Ubuntu release though.  Er, well, no version upgrades.  There are bug fixes.  There are security fixes.  But for stability, there are not new versions added post-release.  If you want newer stuff, you use the newer version of Ubuntu.  There's a new one coming out in the next 48 hours or so.

What's different between the versions, by the way?  I don't use Sun's Java.  I use OpenJDK which is based on Sun open-sourcing Java.

---

### Post by ufis on 2008-10-29
> **macogw said:**
> What's different between the versions, by the way?

Amongst others [much improved applets](http://java.sun.com/developer/technicalArticles/javase/newapplets/index.html) and [applets that you can drag from your browser to the desktop](http://java.sun.com/developer/technicalArticles/javase/6u10_applets/). Many other improvements, but these are the main ones I am after.

Can I add the 8.10 multiverse repository to my 8.04 ubuntu and do the updates like that? Assuming that 8.10 will have sun java 6u10.
Or will this cause unwanted/unknown side effects?

---

### Post by cariboo on 2008-10-29
Sun-java 6.10 is in the Intrepid repositories, you will probably have to upgrade to Intrepid in order to use it.

Jim

---

### Post by philinux on 2008-10-29
> **cariboo907 said:**
> Sun-java 6.10 is in the Intrepid repositories, you will probably have to upgrade to Intrepid in order to use it.

Jim

Would this type of thing come through the backports?

---

### Post by cariboo on 2008-10-29
Thats a good question, we'd have to find out who is looking after the sun java port and ask if he is planning to adding it to hardy.

Jim

---

### Post by ufis on 2008-10-30
where/how can we find that information?

---

### Post by ufis on 2008-10-30
Problem solved.

After some reading I came upon [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) which led me to the request for the backport [https://bugs.launchpad.net/hardy-backports/+bug/291018](https://bugs.launchpad.net/hardy-backports/+bug/291018)

---

