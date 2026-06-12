---
title: "Setting up apt repo"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by Drav_McDuck on 2014-07-28
Hello all,

I am new to learning Ubuntu and needed some help with setting up apt repo for offline use. I made a directory called /repo and moved the Packages.gz and Release file from the Ubuntu 12.04 LTS install dvd.  I am trying to get apache installed on this machine for testing but the system must remain offline. Can someone please help or point me in the right direction. I have searched google/bing/youtube and cannot find an answer. Any information would be greatly appreciated.

Thank you.

---

### Post by frankmorris2 on 2014-07-28
Hello,

I did this a long time ago, so please forgive my failing memory on the details. You will need to do some research on your own in the man pages (man apt-get).

There is an option for apt-get that allows to only download the packages: --download-only

The .deb files a stored in /var/cache/apt/archives/. You can then copy the files on the offline server (USB key, external drive, etc.)

You can then use apt-get to install the packages without downloading them first (option --no-download).

I hope this helps.

Have a nice day.

---

### Post by ian-weisser on 2014-07-28
> **Drav_McDuck said:**
> I am new to learning Ubuntu and needed some help with setting up apt repo for offline use.

Hmmmm. Repos are for online use.Saying you want one for offline use is rather confusing.

Otherwise, frankmorris2's directions are quite correct.

You can also use apt-zip or apt-offline packages, or Synaptic's offline script functions.

---

### Post by philinux on 2014-07-28
[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)
The other option is aptoncd

---

