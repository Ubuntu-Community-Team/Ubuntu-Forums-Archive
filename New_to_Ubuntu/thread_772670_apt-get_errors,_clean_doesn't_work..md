---
title: "apt-get errors, clean doesn't work."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mohnkern on 2008-04-28
Recently upgraded to Hardy.

This morning when I ran apt-get update; apt-get upgrade It told me there were updates to install, and then gave me:

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmlt-data 0.2.4.svn20071228-0.0ubuntu2 [1195kB]
Fetched 1195kB in 1s (831kB/s)       
(Reading database ... 329251 files and directories currently installed.)
Unpacking libmlt-data (from .../libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mlt/modules/lumas/PAL/luma01.pgm.png', which is also in package mlt
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried to do an apt-get clean to clean out the existing cache, and redownload it, but I'm still getting the error.

---

### Post by Oldsoldier2003 on 2008-04-28
> **mohnkern said:**
> Recently upgraded to Hardy.

This morning when I ran apt-get update; apt-get upgrade It told me there were updates to install, and then gave me:

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmlt-data 0.2.4.svn20071228-0.0ubuntu2 [1195kB]
Fetched 1195kB in 1s (831kB/s)       
(Reading database ... 329251 files and directories currently installed.)
Unpacking libmlt-data (from .../libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mlt/modules/lumas/PAL/luma01.pgm.png', which is also in package mlt
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried to do an apt-get clean to clean out the existing cache, and redownload it, but I'm still getting the error.
do another ```
sudo apt-get clean
```the go into /var/lib/dpkg/info
and delete anything in there you see that relates to the package you are having problems with

then
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

this should sort you out

---

### Post by mohnkern on 2008-04-28
The package appears to be limlt0.2.5, now I get:

dpkg: serious warning: files list file for package `libmlt0.2.5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmlt++0.2.5' missing, assuming package has no files currently installed.
329211 files and directories currently installed.)

---

### Post by Oldsoldier2003 on 2008-04-28
> **mohnkern said:**
> The package appears to be limlt0.2.5, now I get:

dpkg: serious warning: files list file for package `libmlt0.2.5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmlt++0.2.5' missing, assuming package has no files currently installed.
329211 files and directories currently installed.)

now try reinstalling libmlt++0.2.5  you may end up having to toggle back and forth between  install -f and update+upgrade but you should be wble to work it through.

out of curiousity what wierd repos do you have enabled? usually this kind of stuff only happens with unstable builds ( I've had it happen with debian unstable builds in the past)

---

### Post by mohnkern on 2008-04-28
A few unusual ones, but this all seems to be coming from Hardy Universe.

Here's what I've got now after trying several "toggles" and flips:

After this operation, 1929kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmlt-data 0.2.4.svn20071228-0.0ubuntu2 [1195kB]
Fetched 1195kB in 1s (816kB/s)       
(Reading database ... 329440 files and directories currently installed.)
Unpacking libmlt-data (from .../libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mlt/modules/lumas/PAL/luma01.pgm.png', which is also in package mlt
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmlt-data_0.2.4.svn20071228-0.0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

It looks like there may be two packages that have the same file.  Now how do I find out which packages have it in it, so I can take one out?

---

### Post by Oldsoldier2003 on 2008-04-28
I'm not real certain about which road we should proceed now, I'm checking around to see if I can garner any further advice on the easiest way to solve your package conflicts. I've got some ideas but I'm not comfortable with telling you to use the -force option

---

### Post by mohnkern on 2008-04-28
Thanks, this was a weird one, I've never seen it before.

---

### Post by Oldsoldier2003 on 2008-04-28
one thing you could try is to disable all the unofficial repos temproraily and try to sort it out again by clear the cache and info.

---

### Post by mohnkern on 2008-04-28
Well, we're definitely getting closer.  I commented out:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse



Then ran apt-get clean; apt-get update; apt-get upgrade

Then I uncommented the main and ran apt-get update; apt-get upgrade, and now I'm down to:

Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-plugins-extra_0.7.4-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


So we've traded one problem with another.

---

### Post by mohnkern on 2008-04-28
So, here's what I did:

I backed up and moved /var/lib/dpkg/info/compiz*

ran apt-get -f install
ran apt-get -f update
ran apt-get -f upgrade

It seems to have cleared all the errors.  I'm not able to run compiz, but then again, I wasn't running it anyway because I can't get the desktop effects to work with my nvidia card, but that's a problem for another day.

I'm actually ssh'd into my box from work, so I don't know whether everything's 100% okay, but it seems to be.

---

### Post by Oldsoldier2003 on 2008-04-28
> **mohnkern said:**
> So, here's what I did:

I backed up and moved /var/lib/dpkg/info/compiz*

ran apt-get -f install
ran apt-get -f update
ran apt-get -f upgrade

It seems to have cleared all the errors.  I'm not able to run compiz, but then again, I wasn't running it anyway because I can't get the desktop effects to work with my nvidia card, but that's a problem for another day.

I'm actually ssh'd into my box from work, so I don't know whether everything's 100% okay, but it seems to be.

wow thats a weird one! I'll have to file this one for future reference once we find out how it works out.

---

