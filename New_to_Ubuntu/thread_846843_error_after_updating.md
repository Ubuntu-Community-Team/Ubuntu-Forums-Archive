---
title: "error after updating"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by broekskw on 2008-07-01
can some one help me get this fixed up

every time there is a update i get this error

whats up and how would i correct this

thanks

---

### Post by ChameleonDave on 2008-07-01
Do this at a command-line terminal:

```

cat /etc/apt/sources.list

```

and paste the results here.

---

### Post by broekskw on 2008-07-01
here is the past for that command

broekskw@broekskw-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://ftp.debian.org](http://ftp.debian.org) etch main
deb [http://ftp.debian.org](http://ftp.debian.org) etch main
broekskw@broekskw-desktop:~$ 

thabks

sure would be nice if i could read all that:lolflag:

---

### Post by ChameleonDave on 2008-07-01
OK.  Type (or paste) this into a terminal:

```
sudo *nano* /etc/apt/sources.list

```

That will open that file for editing.  You may put your favourite text editor instead of *nano*, e.g. *gedit*, *kate*, *vim*...  

```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://ftp.debian.org etch main
deb http://ftp.debian.org etch main
```

See those lines at the end?  Disable them by putting a hash sign in front of each one, like this:

```

#deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb http://ftp.debian.org etch main
#deb http://ftp.debian.org etch main

```

Save and close.

Then enter this on the command line:

```

sudo apt-get update

```

Then try to install what you want to install.

---

### Post by broekskw on 2008-07-01
not to sure as "  Put your favourite text editor instead of nano.??

do i just cut and past what you have on this post??

thanks and sorry for all the questions

---

### Post by ChameleonDave on 2008-07-02
> **broekskw said:**
> not to sure as "  Put your favourite text editor instead of nano.??

do i just cut and past what you have on this post??

thanks and sorry for all the questions

There are various text editors available for Linux.  One is *nano*, which works from within the terminal.  It's very nice and lightweight.  I used this in my example.  You may prefer an editor that opens in its own graphical window.  The default one for Ubuntu running GNOME is *gedit*.  The default for Kubuntu (which I use) is *kwrite* or *kate*.  Xubuntu users have *mousepad*.  Real nerds use *vim* or *emacs*.

Use any of these to edit the file.  It's a personal preference.

---

