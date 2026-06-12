---
title: "Software &quot;not authenticated&quot;"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by WBL on 2008-04-27
Every time I install software, even regular Ubuntu software, it says "NOT AUTHENTICATED" and makes me click "Yes" to install anyways.  How do I stop this behavior?

-WBL

---

### Post by dondad on 2008-04-27
> **WBL said:**
> Every time I install software, even regular Ubuntu software, it says "NOT AUTHENTICATED" and makes me click "Yes" to install anyways.  How do I stop this behavior?

-WBL

You have to get the key for the offending software. Try doing a search for "key +nameofpackage" or nameofrepository.

---

### Post by daimaru on 2008-04-27
> **WBL said:**
> Every time I install software, even regular Ubuntu software, it says "NOT AUTHENTICATED" and makes me click "Yes" to install anyways.  How do I stop this behavior?

-WBL
that is kind of weird. this should only happen if you install 3rd party software from repositories which key you havent added yet. Offical ubuntu stuff should not give you this message. Check your System -> Administration -> Software sources and make sure that your using one of the *.archive.ubuntu.com servers (* being your country prefix). Or manually check in the /etc/apt/sources.list file to see what servers are being used.

---

### Post by Nano Geek on 2008-04-27
> **daimaru said:**
> that is kind of weird. this should only happen if you install 3rd party software from repositories which key you havent added yet. Offical ubuntu stuff should not give you this message. Check your System -> Administration -> Software sources and make sure that your using one of the *.archive.ubuntu.com servers (* being your country prefix). Or manually check in the /etc/apt/sources.list file to see what servers are being used.It does that to me sometimes for no good reason.

I just ignore it since I don't believe its important.

---

### Post by Solrac924 on 2008-04-27
hey asjdfwejqrfjcvm msz34rq33, did you just bang on the keyboard to get your name?! oh well, what's in a name? :tongue:

---

### Post by WBL on 2008-04-27
Everything in my /etc/apt/sources.list file *seems* to be from Canonical.  (??)

> **dondad said:**
> You have to get the key for the offending software. Try doing a search for "key +nameofpackage" or nameofrepository.

How do I do this??

Thanks in advance.

-WBL

---

### Post by daimaru on 2008-04-27
> **WBL said:**
> Everything in my /etc/apt/sources.list file *seems* to be from Canonical.  (??)
-WBL

ok that would mean that there are no ubuntu repos in there . just so you have a referenece here's my sources.list file that stuff should be in your file too, maybe just a different country code:

```
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main #Added by software-properties

deb http://de.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
[COLOR=Red]deb http://www.bashterritory.com/pytube/releases /[/COLOR]
```
never mind the pytube one (red) thats just a prog I tried for downloading youtube videos.

---

### Post by WBL on 2008-04-27
One strange thing is that I installed Medibuntu, but no medibuntu lines occur in my sources.list.  By the way, here is my sources.list:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Any help would be very, very appreciated.  :KS

-WBL

---

### Post by daimaru on 2008-04-28
well our files kinda seem the same. i also have medibutu installed and i was also wondering why it did not show up, since it showed up on gutsy and feisty after i pasted the lines form the medibutu "repository howto" part into terminal... medibuntu now just shows up on "System-> Administration-> Software sources" ??? weird. 

but i still don't get it you have all the same servers your sources.list file is complete so ??? 
is the US server down maybe? what does it say when running sudo apt-get update from terminal?`but i guess you already tried that. 

only thing you could still check is apt-key:
```
sudo apt-key list
```
check out apt-key --help for more info

here's my  list:
```
ap@alita:~$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/0C5A2783 2006-11-23
uid                  Medibuntu Packaging Team <admin@lists.medibuntu.org>
uid                  The Medibuntu Team <medibuntu@sos-sts.com>
sub   2048g/16C7105A 2006-11-23

pub   1024D/A7C6F0DF 2006-08-12
uid                  Albin Tonnerre <lut1n.tne@gmail.com>
sub   2048g/B98C88B5 2006-08-12

pub   1024D/387EE263 2004-09-17
uid                  Scott Ritchie <scott@open-vote.org>
uid                  Scott Ritchie <saritchie@ucdavis.edu>
uid                  Scott Ritchie <scott@tuzakey.com>
sub   1024g/203C857C 2004-09-17

pub   1024D/F854AFD7 2007-03-20 [expired: 2007-12-30]
uid                  Hendrik Kaju <hendrik@kaju.pri.ee>

pub   1024D/9072870B 2007-08-13 [expires: 2009-08-12]
uid                  jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>
sub   1024g/1E5C7A1D 2007-08-13 [expires: 2009-08-12]
```

but that is where my understanding of this matter ends :) so i hope someone with more knowledge picks up this thread.

---

### Post by adult swim on 2008-04-28
to authenticate the medibuntu repo run this from terminal
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

---

### Post by zvacet on 2008-04-28
@ **WBL**

Just refresh your source list with

```
sudo apt-get update
```

For Medibuntu 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

and then 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

