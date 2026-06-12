---
title: "KDE offline installation"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by illegal on 2013-02-15
Hi,
I am on Ubuntu 12.04. I want to install KDE. Is the deb file for this available for download? I am facing some issues when I try the apt-get method.

Can someone link me the .deb file for KDE installation please?

Many thanks :)

---

### Post by tartalo on 2013-02-15
KDE is not one .deb but lots of them. I never tried but perhaps you can install it from the Kubuntu CD.

[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)

I guess it would be something like this:

```
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
```

Anyway, if you want KDE I'd recomend that you install directly Kubuntu, not KDE on top of Ubuntu, you will get a cleaner installation.

And if you are merely curious, try it from the live CD without installing anything.

---

### Post by ptn107 on 2013-02-15
If you have Ubuntu 12.04 installed with all the latest updates applied I can give you the link to the kde debs in just a minute.  The debs compressed are 179mb.

---

### Post by ptn107 on 2013-02-15
or in the meantime you can use [_this script_]("https://www.dropbox.com/s/agw9i4v0st35wo7/get-kde-precise") to download the debs and install kde yourself.

---

### Post by illegal on 2013-02-15
> **tartalo said:**
> KDE is not one .deb but lots of them. I never tried but perhaps you can install it from the Kubuntu CD.

[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)

I guess it would be something like this:

```
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
```

Anyway, if you want KDE I'd recomend that you install directly Kubuntu, not KDE on top of Ubuntu, you will get a cleaner installation.

And if you are merely curious, try it from the live CD without installing anything.

Hi,
Since my internet connection is faulty, I am thinking of downloading the .deb(s) on another machine and transferring it to mine manually and installing and hence the apt-get method won't work :(

---

### Post by illegal on 2013-02-15
> **ptn107 said:**
> or in the meantime you can use [_this script_]("https://www.dropbox.com/s/agw9i4v0st35wo7/get-kde-precise") to download the debs and install kde yourself.

Download all the .debs, store it in a particular folder and running **dpkg -i *.deb** would get KDE installed?

> **ptn107 said:**
> If you have Ubuntu 12.04 installed with all the latest updates applied I can give you the link to the kde debs in just a minute.  The debs compressed are 242mb.
That would be great! :) Waiting for it :D

---

### Post by ptn107 on 2013-02-15
Still transferring to Dropbox.  I'll post the link when it's ready ~40 minutes.  I got the size down to 179mb by changing compression options.


...and yes, sudo dpkg -i *.deb will install them.

---

### Post by tartalo on 2013-02-15
> **illegal said:**
> Hi,
Since my internet connection is faulty(...) apt-get method won't work :(
No no, I was proposing using the Kubuntu CD as the source for the packages, not the internet. "apt-cdrom add" adds the CD as a source: [https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

Downloading the packages and installing them with dpkg would work too as long as you have all the dependencies, they will appear as locally installed packages and I'm not sure if the signature gets verified with this method, but it should work too.

---

### Post by ptn107 on 2013-02-15
Download [_here_]("https://www.dropbox.com/s/l3857hnu361og7e/kde-debs-precise.tar.bz2").

---

### Post by illegal on 2013-02-16
> **ptn107 said:**
> Still transferring to Dropbox.  I'll post the link when it's ready ~40 minutes.  I got the size down to 179mb by changing compression options.


...and yes, sudo dpkg -i *.deb will install them.
Thanks a lot :) I am travelling right now; will get a stable internet connection after ~35 hrs ;) Hope your db link won't expire :) Btw, does it contain all the dependencies too? :o
And after doing the dpkg -i *.deb, a restart would bring the KDE selection option on the login page?

> **tartalo said:**
> No no, I was proposing using the Kubuntu CD as the source for the packages, not the internet. "apt-cdrom add" adds the CD as a source: [https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

Downloading the packages and installing them with dpkg would work too as long as you have all the dependencies, they will appear as locally installed packages and I'm not sure if the signature gets verified with this method, but it should work too.
Hmm. Looks like ptn107 has uploaded the debs. I would be preferring the offline method as of now, so will be giving it a shot :) Thanks man :)

---

### Post by ptn107 on 2013-02-18
It includes all the dependencies for an install which does not already have kde or any kde apps installed prior.  I do believe though after a restart you must choose kde as the login session.  I don't think it will default to kde until you log into it for the first time.

---

