---
title: "about firefox 3b5"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-01
meaning that it is beta...could that mean that has some security issues or something except some bugs from time to time?
also will it be automatically updated or i'll wait until next release?**

---

### Post by bilal.17 on 2008-05-01
it will be automatically updated, and since as you pointed out its still a beta, it does have some bugs. One of them is that it takes up a lot of the cpu [http://ubuntuforums.org/showthread.php?t=744485]("http://ubuntuforums.org/showthread.php?t=744485"). It may suit your needs, so i would try it out, but if it doesn't work well, then id go back to firefox 2 or a different browser.

---

### Post by Bothered on 2008-05-01
Firefox 2 is still in the repositories if you want to use the current stable version until version 3 is released (firefox-2 package).

---

### Post by vishzilla on 2008-05-01
Firefox 3b5 was considered quite stable for a beta hence the devs have included it by default in 8.04. I feel 3b5 is better than FF2 anytime. You shouldn't be worried unless you are having any crashes.

---

### Post by gjtoth on 2008-05-01
There are a couple of other bugs besides the cpu usage.  Freeze-ups and crashes are frequent.  It is clearly not ready for primetime.  I switched back to 2.xxx However, in doing so, my Thunderbird fails to open up 2.xxx when a link is clicked.  I'm still working on this little glitch though.

---

### Post by Paqman on 2008-05-01
> **lunaluna said:**
> 
also will it be automatically updated or i'll wait until next release?**

All software that's in the repos (which means everything on your machine, ideally) gets updated automatically. That's one of the cool things about Ubuntu.

Of course, there's not telling when the final version of Firefox comes out. They haven't set a date. We might still be using the beta when Intrepid comes out in six months.

---

### Post by lunaluna on 2008-05-01
ok thnx
and..what about updates (security) will there automatically updated?

---

### Post by Nepherte on 2008-05-01
By default, you will get update notifications when new updates are available for any package you have installed that is in the repositories.

---

### Post by Myglaren on 2008-05-01
> **gjtoth said:**
> There are a couple of other bugs besides the cpu usage.  Freeze-ups and crashes are frequent.  It is clearly not ready for primetime.  I switched back to 2.xxx However, in doing so, my Thunderbird fails to open up 2.xxx when a link is clicked.  I'm still working on this little glitch though.

I have been running Ff3b5 on Gutsy and Vista for a few weeks now and on both platforms it has been completely trouble free.

I did the online update, more from curiosity than need, and HH is great, dead solid, as is Firefox 3.

---

### Post by muteXe on 2008-05-01
> **Myglaren said:**
> 
I did the online update, more from curiosity than need, and HH is great, dead solid, as is Firefox 3.

But some banks do not currently suppost FF3 as a browser.

---

### Post by Paqman on 2008-05-01
> **muteXe said:**
> But some banks do not currently suppost FF3 as a browser.

They're just being conservative. They (quite sensibly) probably have a policy of not supporting beta software.

You can install FF2, it's in the repos.

---

### Post by muzel on 2008-05-01
> **gjtoth said:**
> There are a couple of other bugs besides the cpu usage.  Freeze-ups and crashes are frequent.  It is clearly not ready for primetime.  I switched back to 2.xxx However, in doing so, my Thunderbird fails to open up 2.xxx when a link is clicked.  I'm still working on this little glitch though.
@gjtoth: Hi, quite clear - thunderbird is looking for firefox, but now there is firefox-2...
Open "about:config" in TB, type "http", and change (or insert) the lines:
network.protocol-handler.app.http
network.protocol-handler.app.https
from (maybe) /usr/bin/firefox to /usr/bin/firefox-2

(Or, create a symlink...)

HTH, muzel

---

### Post by muteXe on 2008-05-01
> **Paqman said:**
> They're just being conservative. They (quite sensibly) probably have a policy of not supporting beta software.

You can install FF2, it's in the repos.

Yup that's what I did. All good again now :)

---

### Post by Myglaren on 2008-05-01
> **muteXe said:**
> But some banks do not currently suppost FF3 as a browser.
Mine has no problem with it.  They did issue warnings about it and the OS not being supported but it has always been fully functional.  Only ever use the Ubuntu machine and Firefox to make purchases on the net, or to use internet banking.  Wouldn't trust the Vista machine with that.

---

### Post by muteXe on 2008-05-01
It worked for other bank accounts, just not for my main one.
I too only do internet banking on my linux machines.  I don't trust MS OS's for that :)

---

### Post by lunaluna on 2008-05-01
..but beta is beta... so how will i be able to know if an new version is availiable?
or a security issue is fixed/discovered? 

generally where can i find about main securities for browsers?

---

### Post by Myglaren on 2008-05-01
Automatic updates will take care of the new versions.  There will be no further updates until the final release, according to the Firefox development teams notice.
Security issues are usually publicised very quickly by [Slashdot](http://slashdot.org/) and its sister publication [The Register](http://www.theregister.co.uk/)

---

### Post by Paqman on 2008-05-01
> **lunaluna said:**
> ..but beta is beta... so how will i be able to know if an new version is availiable?


Ubuntu will let you know. Ubuntu updates ALL your software for you. Whenever a new version or Firefox is put into the repos, you get the option to install it.

---

