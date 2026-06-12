---
title: "Error:Dependency not satisfiable:w32 codecs"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by faron45 on 2008-12-01
Darn !!! Now what ?? I'm sorry guys.Hellllllllllppppppppppppppppp !! Maybe I should just instal vlc ?? Zalbor says "I recommend VLC, which has its own codecs for everything and is a very good player as well.

---

### Post by halitech on 2008-12-01
what exactly is it saying?

---

### Post by binbash on 2008-12-01
did you add medibuntu repo to your sources.list ?

---

### Post by faron45 on 2008-12-01
Halitech-THAT IS exactly what's it's saying when I tryn to install the non free codecs

Binbash-Yes.At least I thought I did.Maybe I should reboot ?? Hmmmmmmm.Hope you guys didn't give up on me-"service was unavailable".

---

### Post by jamesrl on 2008-12-01
make sure you have the relevant medibuntu lines in your repository list /etc/apt/sources.list:
> deb [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid free non-free
deb-src [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid free non-free
with intrepid replaced by hardy if you are on 8.04
Then run
```
sudo apt-get update
```

---

### Post by faron45 on 2008-12-01
James ... Ehhhhhhh ?? I've been to that page already & downloaded "hardy".Tried to install  & this is the message I got  " Error:Dependency not satisfiable:w32 codecs" Now what ?

---

### Post by halitech on 2008-12-01
you don't "go to a page" to download anything. You will be doing this either in the command line or in synaptic but we need to make a change (I'm guessing) in your sources.list file. open a terminal and post the output of
```
cat /etc/apt/source.list
```

---

### Post by faron45 on 2008-12-01
Results I get are " no such file or directory"

---

### Post by halitech on 2008-12-01
sorry, should have been sources.list

```
cat /etc/apt/sources.list
```

---

### Post by faron45 on 2008-12-01
Holy moly ! This is what I got-#deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by halitech on 2008-12-01
okay, so you didnt do the steps in post 5 above.

run```
gksu gedit /etc/apt/sources.list
```
at the bottom, add these 2 lines
```
deb http://packages.medibuntu.org hardy free non-free
deb-src http://packages.medibuntu.org hardy free non-free 
```

replace gedit with whichever text editor you use

---

### Post by faron45 on 2008-12-01
Okay my friend.....this is what I got.....bobby@cybertek:~$  gksu abiword /etc/apt/sources.list
Wrong Grammar|com/community/UpgradeNotes for how to upgrade to |
 LowOff 25 HighOff 73 
Wrong Grammar|#deb cdrom:[Xubuntu 8.|
 LowOff 0 HighOff 21 
Wrong Grammar|04.|
 LowOff 22 HighOff 24 
Wrong Grammar|1)]/ hardy main restricted |
 LowOff 66 HighOff 92 
Wrong Grammar|com/ubuntu/ hardy main restricted |
 LowOff 29 HighOff 62 
Wrong Grammar|com/ubuntu/ hardy main restricted |
 LowOff 33 HighOff 66 
Wrong Grammar|## Major bug fix updates produced after the final release of the |
 LowOff 0 HighOff 64 
Wrong Grammar|com/ubuntu/ hardy-updates main restricted |
 LowOff 29 HighOff 70 
Wrong Grammar|com/ubuntu/ hardy-updates main restricted |
 LowOff 33 HighOff 74 
Wrong Grammar|B.|
 LowOff 5 HighOff 6 
Wrong Grammar|## team, and may not be under a free licence.|
 LowOff 0 HighOff 44 
Wrong Grammar| Please satisfy yourself as to |
 LowOff 45 HighOff 75 
Wrong Grammar| Also, please note that software in |
 LowOff 35 HighOff 70 
Wrong Grammar|## universe WILL NOT receive any review or updates from the Ubuntu security |
 LowOff 0 HighOff 75 
Wrong Grammar|## team.|
 LowOff 0 HighOff 7 
Wrong Grammar|com/ubuntu/ hardy universe |
 LowOff 29 HighOff 55 
Wrong Grammar|com/ubuntu/ hardy universe |
 LowOff 33 HighOff 59 
Wrong Grammar|com/ubuntu/ hardy-updates universe |
 LowOff 29 HighOff 63 
Wrong Grammar|com/ubuntu/ hardy-updates universe |
 LowOff 33 HighOff 67 
Wrong Grammar|B.|
 LowOff 5 HighOff 6 
Wrong Grammar|## team, and may not be under a free licence.|
 LowOff 0 HighOff 44 
Wrong Grammar| Please satisfy yourself as to  |
 LowOff 45 HighOff 76 
Wrong Grammar| Also, please note that software in  |
 LowOff 35 HighOff 71 
Wrong Grammar|## multiverse WILL NOT receive any review or updates from the Ubuntu |
 LowOff 0 HighOff 68 
Wrong Grammar|## security team.|
 LowOff 0 HighOff 16 
Wrong Grammar|## Uncomment the following two lines to add software from the 'backports' |
 LowOff 0 HighOff 73 
Wrong Grammar|## repository.|
 LowOff 0 HighOff 13 
Wrong Grammar|B.|
 LowOff 5 HighOff 6 
Wrong Grammar| software from this repository may not have been tested as |
 LowOff 7 HighOff 65 
Wrong Grammar|## extensively as that contained in the main release, although it includes |
 LowOff 0 HighOff 74 
Wrong Grammar|## Also, please note that software in backports WILL NOT receive any review |
 LowOff 0 HighOff 75 
Wrong Grammar|## or updates from the Ubuntu security team.|
 LowOff 0 HighOff 43 
Wrong Grammar|## Uncomment the following two lines to add software from Canonical's |
 LowOff 0 HighOff 69 
Wrong Grammar|## 'partner' repository.|
 LowOff 0 HighOff 23 
Wrong Grammar|canonical.|
 LowOff 21 HighOff 30 
Wrong Grammar|com/ubuntu hardy partner |
 LowOff 31 HighOff 55 
Wrong Grammar|canonical.|
 LowOff 25 HighOff 34 
Wrong Grammar|com/ubuntu hardy partner |
 LowOff 35 HighOff 59 
Wrong Grammar|com/ubuntu hardy-security main restricted |
 LowOff 27 HighOff 68 
Wrong Grammar|com/ubuntu hardy-security main restricted |
 LowOff 31 HighOff 72 
Wrong Grammar|com/ubuntu hardy-security universe |
 LowOff 27 HighOff 61 
Wrong Grammar|com/ubuntu hardy-security universe |
 LowOff 31 HighOff 65 
deb [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free
deb-src [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free
 gksu abiword /etc/apt/sources.list
deb [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free
deb-src [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free

---

### Post by halitech on 2008-12-01
you don't want to use Abiword for this, it does some strange things to text files. are you using Xubuntu?

---

### Post by faron45 on 2008-12-01
Yes-Xubuntu

---

### Post by halitech on 2008-12-01
ok, change gedit to mousepad

```
 gksu mousepad /etc/apt/sources.list
```

---

### Post by faron45 on 2008-12-01
Okay,Hali-when I enter this- gksu mousepad /etc/apt/sources.list-I get this-~$ deb [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free
bash: deb: command not found

---

### Post by halitech on 2008-12-01
you should get a window popping up that has all your repos listed in it. maybe try just ```
gksu mousepad
``` and then see what happens.

---

### Post by faron45 on 2008-12-01
Okay-when I enteer this-gksu mousepad-I get mousepad open

---

### Post by halitech on 2008-12-01
ok, now go file - open and browse to /etc/apt and select sources.list

then add the previous 2 lines

---

### Post by unutbu on 2008-12-01
<snip>

---

### Post by faron45 on 2008-12-01
Okay Hali-when I go to sources list I get "medibuntu list " I'm sorry my friend...where am I supposed to "add" those 2 lines to ?

---

### Post by halitech on 2008-12-01
unutbu had posted a link on adding the multimedia codecs, might be easier to use that info

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

basically select which version you have (don't worry about Ubuntu.xubuntu/kubuntu) and follow the commands.

---

### Post by faron45 on 2008-12-01
I have already done this but,I will try again.But,I believe I'm gonna give this up for a little while.I'm starving & we've been at this for hours ! Thanks very much everybody.Hopefully,I/we'll get this figured out.Hali-I'm pretty sure the repositories are installed.It's the codecs that I'm having problems installing now...........

---

