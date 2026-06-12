---
title: "Repository messed up Synaptic"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by hikujk123 on 2008-05-10
I am using xubuntu hardy heron.  I was trying to install adobe acrobat reader.  I found this howto: [http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html).
As it says, I typed this in the terminal:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
I got an error when trying to sudo apt-get update, so I went to synaptic to disable this repository but got this error when I started it.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and I can't use synaptic.

How do I remove this repository/fix this problem?

---

### Post by SOULRiDER on 2008-05-10
Press
```
alt + f2
```
and type
```
gksu gedit /etc/apt/sources.list
```

Scroll down until you find lines containing medibuntu, remove them and then save.
If youre not sure what to remove, post the contents of thatf ile here and we can tell you. Remember to use the CODE tags if you decide to post it.

---

### Post by hikujk123 on 2008-05-10
# deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


Here it is.  I don't know what to delete.

---

### Post by hikujk123 on 2008-05-10
Please Help.:(

---

### Post by kansasnoob on 2008-05-10
OK, I've been here and done this ............ sort of ;^(

I was trying to use Gutsy's Medibuntu repo with Hardy but the result was similar.

Start here:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Then add the gpg key:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

If that doesn't do it then try:

sudo apt-get autoclean

If it's still broke just shoot me!

The big problem is getting rid of the wrong stuff!

---

### Post by joshsmith on 2008-05-10
hey, dont bump your threads

ok so the error message says:
Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

so there is a problem in this file. go and check it out for errors

post its contents here
the first lines is going to be screwed up, ie not looking like
deb [http://something/](http://something/) something something

then follow the proper medibuntu instructions, google medibuntu :)

as a side note, try to get into not using a pdf plugin for ff. just use the standalone viewer, it is much easier once you are used to it

---

### Post by hikujk123 on 2008-05-10
Thank you so much kansas noob.  It worked.

---

### Post by SOULRiDER on 2008-05-10
Could you please mark the thread as solved?

Thank you!

---

