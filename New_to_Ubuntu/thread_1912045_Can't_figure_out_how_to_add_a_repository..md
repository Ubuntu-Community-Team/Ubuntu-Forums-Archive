---
title: "Can't figure out how to add a repository."
date: 2012-01-19
forum: New to Ubuntu
---

### Post by neptune769 on 2012-01-19
Hello Everyone,
I am new to Linux. I am struggling to install Zoneminder onto Ubuntu 9.4. Zoneminder is not in the Synaptic Package Manager. I went to Software Sources, Third Party tab & Add. After that I don't know what to enter in the window for APT line.

I am using 9.4 because the Zoneminder Wiki for 9.4 seems easier for me to understand. I was totally lost with 10.4.

Any help would be greatly appreciated.

Dennis

---

### Post by Rodney9 on 2012-01-19
This page shows you how to add ppa's -
 [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


This page says it will work with Jaunty -

[https://launchpad.net/~manuel-aircable/+archive/zoneminder](https://launchpad.net/~manuel-aircable/+archive/zoneminder)

This is the ppa from that page -

deb [http://ppa.launchpad.net/manuel-aircable/zoneminder/ubuntu](http://ppa.launchpad.net/manuel-aircable/zoneminder/ubuntu) lucid main

Rodney

---

### Post by alphacrucis2 on 2012-01-19
BTW 9.04 is no longer supported.

To add a repo, the easiest way is to add the apt line via software sources in synaptic.

---

### Post by layers on 2012-01-19
First, you should know that Ubuntu 9.4 is at the end of its support-life. That means that half of the repositories do not support 9.4 anymore. [http://en.wikipedia.org/wiki/Ubuntu_(operating_system](http://en.wikipedia.org/wiki/Ubuntu_(operating_system))
if you need a proof.



Have you tried downloading it?
[http://www.zoneminder.com/downloads](http://www.zoneminder.com/downloads)

---

### Post by GregA on 2012-01-20
From their website, Zoneminder has a recent "deb" release for the Debian Unstable branch.   Since you mention you're new to Linux, Debian is the parent Linux distrobution to Ubuntu, but can be difficult to install for newbies.   So, another possibility is to install "aptosid" - - see [http://distrowatch.com/table.php?distribution=aptosid](http://distrowatch.com/table.php?distribution=aptosid)

Aptosid is a little easier to install, and the standard software repositories should include the lastes Zoneminder, which then can be installed via Synaptic.

This will still take some work, but is do-able if you're a good reader and are persistent.

Hope this helps.

---

### Post by neptune769 on 2012-01-20
Thank you all for your help & input. I will reread your posts and give it a go after work.

---

