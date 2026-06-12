---
title: "Slow downloads"
date: 2006-02-13
forum: Repositories &amp; Backports
---

### Post by eRoot on 2006-02-13
Up untill formatting my ubuntu partition and installing it again, I usually got maximum download speed (650kB/s) when downloading from repositories. But now my download speed seems to have dropped signifacantly (50-100kB/s). I'm a real Linux/Ubuntu noob and have no idea if this has got something to do with the repositories or with my settings.
If anybody has an idea or a suggestion, I'd truely appreciate that.

An example:
```
barry@box:~$ sudo apt-get install bittornado bittornado-gui
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libwxgtk2.6-0 python-wxgtk2.6 python-wxversion
Suggested packages:
  python-psyco wx2.6-doc wx2.6-examples
The following NEW packages will be installed:
  bittornado bittornado-gui libwxgtk2.6-0 python-wxgtk2.6 python-wxversion
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 5826kB of archives.
After unpacking 21.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy-backports/main bittornado 0.3.13-1ubuntu1~breezy1 [155kB]
Get:2 http://archive.ubuntu.com breezy/universe python-wxversion 2.6.1.1.1ubuntu2 [20.3kB]
Get:3 http://archive.ubuntu.com breezy/universe libwxgtk2.6-0 2.6.1.1.1ubuntu2 [2968kB]
Get:4 http://archive.ubuntu.com breezy/universe python-wxgtk2.6 2.6.1.1.1ubuntu2 [2642kB]
88% [4 python-wxgtk2.6 2033363/2642kB 76%]                          68.8kB/s 9s

```

My source.list:
```
## new repository list

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

## audacious
deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious
```

---

### Post by nickle on 2006-02-13
I have also noticed the download from the repositories is slow usually 60-70 kbyte/s.. Is that normal?
I am also failry new to ubuntu, so I have no past reference...

---

### Post by eRoot on 2006-02-14
Well, the repositories are back to normal. I haven't done anything at all, so I suspect that something was going on with the repositories. Maybe maintenance or something?
Anyway, the problem has been solved.

---

