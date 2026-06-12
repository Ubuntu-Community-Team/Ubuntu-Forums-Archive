---
title: "build-essential missing"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by kivitarus on 2008-09-10
Hi, I have typed in```
sudo apt-get install build-essential
``` to get gcc, as I am missing it at the moment, however i get this :

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential
```

I have read in other posts that this command would help install gcc
Anyone know how to get this package please?
Also, how do i know which system i'm running ? (Kubuntu,xubuntu, edubuntu etc?)
Thanks in advance.

---

### Post by jerome1232 on 2008-09-10
try updating your database
```
sudo apt-get update
sudo apt-get install build-essential
```

If update comes back with errors please post them when you reply

---

### Post by kivitarus on 2008-09-10
Ok thanks, I've entered it, and all, the update went fine, but the build-essential file is still missing, with the same error 

Reaing package... Done
Building Dependency... Done
E: Couldn't find package build-essential

---

### Post by jerome1232 on 2008-09-10
interesting, can you post your sources.list file?

just paste the output of this command if your not sure how to view that file

```
cat /etc/apt/sources.list | less
```

---

### Post by kivitarus on 2008-09-10
Ok here it is:

```
deb http://update.eeepc.asus.com/1.6 common main
deb http://update.eeepc.asus.com/1.6 p1000 main
deb http://update.eeepc.asus.com/1.6 en main
```

I'd also like to ask how i can copy the data from the terminal? Just wondering to make it easier, as Ctrl C doesn't work (I typed this sources.list out)

---

### Post by Rolcol on 2008-09-10
> **kivitarus said:**
> Ok here it is:

```
deb http://update.eeepc.asus.com/1.6 common main
deb http://update.eeepc.asus.com/1.6 p1000 main
deb http://update.eeepc.asus.com/1.6 en main
```

I'd also like to ask how i can copy the data from the terminal? Just wondering to make it easier, as Ctrl C doesn't work (I typed this sources.list out)

You're missing ubuntu's repositories which is why you can't find build-essential.  I don't know the exact sources.

To copy from the terminal, you can highlight the text and then click your middle mouse button where you want to paste.  Or: Highlight > Right Click > Copy.

---

### Post by jerome1232 on 2008-09-10
> **kivitarus said:**
> Ok here it is:

```

deb http://update.eeepc.asus.com/1.6 common main
deb http://update.eeepc.asus.com/1.6 p1000 main
deb http://update.eeepc.asus.com/1.6 en main
```

I'd also like to ask how i can copy the data from the terminal? Just wondering to make it easier, as Ctrl C doesn't work (I typed this sources.list out)

... that's it? Wow that isn't right at all... (btw ctrl+shift+c copies ctrl+shift+v pastes, also if you just highlet text in terminal, go over to firefox and middle click it will paste whatever you highlighted)

mine looks like this: This is a default version btw, I would copy everything but the first line

```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
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
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

so don't copy:

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted

You need to edit your sources.list, paste mine in excluding that first line, save, then update and install build-essential.
ubuntu
```
gksudo gedit /etc/apt/sources.list
sudo apt-get clean
sudo apt-get update
sudo apt-get install build-essential
```

kubuntu
```
kdesu kate /etc/apt/sources.list
sudo apt-get clean
sudo apt-get update
sudo apt-get install build-essential
```

xubuntu
```
sudo mousepad /etc/apt/sources.list
sudo apt-get clean
sudo apt-get update
sudo apt-get install build-essential
```

the only difference between the three is the text editor we are using, so it's not going to hurt to try and see which one works since you don't know which one you have.

---

### Post by ThrobbingBrain66 on 2008-09-10
Here is the sources.list for Hardy.  If you are running a previous version, replace all the "hardy" references to feisty, gutsy, etc....

```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - i386/ 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

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
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

To get your OS info, check the System tab of the System monitor:
```
gnome-system-monitor
```

---

### Post by jerome1232 on 2008-09-10
> **ThrobbingBrain66 said:**
> Here is the sources.list for Hardy.  If you are running a previous version, replace all the "hardy" references to feisty, gutsy, etc....

```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20080222)]/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

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
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

To get your OS info, check the System tab of the System monitor:
```
gnome-system-monitor
```

The only problem with that is **gnome**-system-monitor will be in Ubuntu only, not xfce not kde.

---

### Post by kivitarus on 2008-09-10
Great, it seems to have worked! thanks very much! :)
It was very helpful, I'm basically just trying to get synaptic package manager working and get into desktop mode,going through all this. 
Thanks again!

---

### Post by t0p on 2008-09-10
Kivitarus, are you running ubuntu?  Your original sources list suggests to me that you're still running the original xandros operating system on your eeepc.  Xandros and ubuntu are both linux, but there are differences.

I'm not trying to get rid of you, but you'll find more xandros and eeepc specific help at, for example, [http://eeeuser.com]("http://eeeuser.com").

---

### Post by kivitarus on 2008-09-10
Uhm, I'm not exactly sure which one i'm running but 

kubuntu

Code:
kdesu kate /etc/apt/sources.list
sudo apt-get clean
sudo apt-get update
sudo apt-get install build-essential

This mentioned previously by jerome1232 works for me, so I think I got kubuntu, I only just got my eee pc today, and everything is basically at the factory's settings, but thanks for the tip. Or is there any way I can find out what I'm using?
Thanks

---

### Post by jerome1232 on 2008-09-10
Well actually that just means you are running KDE, any linux distro can run KDE.

I'm not familiar with KDE so I don't know where to find the system info.

I know lsb_release -a shows vendor info on Ubuntu, not sure if that is Ubuntu specific or not.

```
lsb_release -a
```

---

### Post by kivitarus on 2008-09-10
Yes, that command works, it doesn't have any info on if it is Xandros or not though, nevertheless, I've got my problem fixed, :) thanks :D

I've however got a new problem, I have followed [HTML]http://www.downloadsquad.com/2007/11/06/eee-pc-tips-a-crash-course-in-linux/[/HTML] to get into full desktop mode, 
However, I can't seem to get ksmserver working or something, its just not showing the full desktop icon to log me into it. Any ideas please? (Should I be making a new thread for this?)
Thanks in advance

---

### Post by jerome1232 on 2008-09-10
I believe you actually are running xandros and I think you should undo the changes we assisted you with on your sources.list file, although xandros appears to be debian based, so apps from Ubuntu repositories will work, I really think you should use xandros repositories.

I just kinda assumed you had followed some tut and mucked your sources.list file up. (like did cat > text) and it deleted everything except the new stuff you added.

---

### Post by kivitarus on 2008-09-10
Hmm.. I see.. Thanks, so should I try and undo everything? AS I can't actually even open file manager anymore :s Is there a way?
Ty

---

### Post by kivitarus on 2008-09-10
Hmm actually it's fine, Thanks for the help once again :)

---

