---
title: "[SOLVED] can not use update manager or terminal to update"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by hazman on 2008-08-26
can use update manager or terminal to update as i get
E:TYPE"deb' is not known on line 49 in source list/etc/apt/source.list,E:the list of sources could not be read.

---

### Post by Crafty Kisses on 2008-08-26
Looks like you're going to have to remove line 49 from you sources list.

---

### Post by kellemes on 2008-08-26
> **hazman said:**
> can use update manager or terminal to update as i get
E:TYPE"deb' is not known on line 49 in source list/etc/apt/source.list,E:the list of sources could not be read.

Please post /etc/apt/sources.list

---

### Post by perlluver on 2008-08-26
You can get into the sources, in a terminal, ```
gksu gedit /etc/apt/sources.list
```

---

### Post by hazman on 2008-08-26
how do i do that

---

### Post by perlluver on 2008-08-26
To post the output, Applications>Accescories>Terminal, cat /etc/apt/sources.list, and post the output here.

---

### Post by kellemes on 2008-08-26
> **hazman said:**
> how do i do that

Hit ALT-F2 and enter the command *perlluver* has given.
Now post the hole text of the file in this thread.

---

### Post by Scunge on 2008-08-26
Can you post what line 49 is, as well as a few around it; it might just be a typo or something? Or indeed, post the whole file if you like.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by kellemes on 2008-08-26
> **perlluver said:**
> To post the output, Applications>Accescories>Terminal, cat /etc/apt/sources.list, and post the output here.

Or like so.. ;-)

---

### Post by perlluver on 2008-08-26
And now I realize this is Xubuntu, so scrap those places, press Alt+f2 and type cat /etc/apt/sources.list, and post the output.

---

### Post by hazman on 2008-08-26
wayne@ubuntu:~$ cat /etc/apt/sources.list
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
wayne@ubuntu:~$

---

### Post by kellemes on 2008-08-26
Delete the bottom line..
```
&#8220;deb http://www.getautomatix.com/apt edgy main&#8221;
```

You don't need it and is the one giving you crap.

from terminal..
```
gksudo gedit /etc/apt/sources.list
```
and delete the line, safe file.

---

### Post by perlluver on 2008-08-26
> 

“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”


This line is causing the problems, so Alt+f2, and then sudo gedit /etc/apt/sources.list, and remove that line.

---

### Post by hazman on 2008-08-26
nothing happened it just went off and did nothing

---

### Post by perlluver on 2008-08-26
What went off and did nothing?

---

### Post by kellemes on 2008-08-26
> **hazman said:**
> nothing happened it just went off and did nothing

Don't know what you mean..

Try from a terminal window..
```
sudo apt-get update
```

Any strange messages? Or does everything seem fine?

---

### Post by hazman on 2008-08-26
yes did nothing

---

### Post by kellemes on 2008-08-26
> **hazman said:**
> yes did nothing

You mean the following line did nothing?
```
gksudo gedit /etc/apt/sources.list
```

Try the following.. (forgot you're on Xubuntu)

```
gksudo mousepad /etc/apt/sources.list
```

---

### Post by perlluver on 2008-08-26
Re post the output of cat /etc/apt/sources.list

---

### Post by hazman on 2008-08-26
thank you you are a star that done the trick THANK YOU

---

