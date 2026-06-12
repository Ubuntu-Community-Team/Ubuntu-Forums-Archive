---
title: "update manager error"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by divishobana on 2012-04-15
hi 
 i am new to ubuntu.when i tried to open ubuntu software center it is not opening update error is coming. like these 
'E:Malformed line 57 in source list /etc/apt/sources.list (dist parse)'
because of these i am unable to install new software to ubuntu
please help me as soon as possible

---

### Post by oboedad55 on 2012-04-15
> **divishobana said:**
> hi 
 i am new to ubuntu.when i tried to open ubuntu software center it is not opening update error is coming. like these 
'E:Malformed line 57 in source list /etc/apt/sources.list (dist parse)'
because of these i am unable to install new software to ubuntu
please help me as soon as possible

Please post your sources.list so we can see which line is causing the error. Did you add repos or change the defaults?

---

### Post by divishobana on 2012-04-20
hi..
  how to get source list in ubuntu?what command we should use for that please tell me everythink in detailed manner

---

### Post by ubudog on 2012-04-20
Hi, to view the sources.list file, you can run this command in a terminal: 
```
sudo cat /etc/apt/sources.list
```

Post the output of that here.  ;)

---

### Post by divishobana on 2012-04-20
hi......
this is my source code 



# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.com/oneiric](http://archive.canonical.com/oneiric) partner
deb-src [http://archive.canonical.com/oneiric](http://archive.canonical.com/oneiric) partner

---

### Post by ubudog on 2012-04-20
I've commented out line 57 and its block, if you can run: 
```
gksu gedit /etc/apt/sources.list
```

Select everything (CTL + A), and delete it, then paste this updated version: 
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#deb http://extras.ubuntu.com/ubuntu oneiric main
#deb-src http://extras.ubuntu.com/ubuntu oneiric main
#deb http://archive.canonical.com/oneiric partner
#deb-src http://archive.canonical.com/oneiric partner
```

Then, run:
```
sudo apt-get update
```

After that, you should be able to open Software Center. 

Although you may be missing the third-party repository.  

Best of luck!

---

### Post by divishobana on 2012-04-21
hi.........
  thanks a lot.thank you so much now everythink is working.actually what problem was occured in ubuntu?how to avoid these things?please tell me what mistake i have made?

---

### Post by ubudog on 2012-04-21
Well, it appears the block and line 57 weren't constructed correctly:

It was: 
```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/oneiric partner
deb-src http://archive.canonical.com/oneiric partner
```

And I believe it should have been: 
```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/**ubuntu** oneiric partner
deb-src http://archive.canonical.com/**ubuntu** oneiric partner
```

Did you recently add any sources in Software Sources?

---

### Post by raja.genupula on 2012-04-21
@ubudog
         My friend i have not spotted there whats got corrected , please mark it for me

---

### Post by ubudog on 2012-04-21
> **raja.genupula said:**
> @ubudog
         My friend i have not spotted there whats got corrected , please mark it for me

Check the post, I made it bold.  ;)

---

### Post by divishobana on 2012-04-24
hi...
   actually i tried to install skype in ubuntu after that only this problem occured

---

