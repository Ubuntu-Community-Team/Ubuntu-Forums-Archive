---
title: "cant download with add and remove"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Kedster on 2008-04-24
cant download with add and removeas in it wont get stuff off the repos soi went into software sources see what was goin on but then when i went to reload the repos it wouldent even do that it says
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_CA.bz2  
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by overdrank on 2008-04-24
HI and have you tried to change your server location in software sources? Also could you post your source list ```
cat /etc/apt/sources.list
```

---

### Post by LittleLORDevil on 2008-04-24
I've noticed that the repo's are really slow today due to the Hardy release that could be a part of the problem.  I had this issue earlier.

---

### Post by Kedster on 2008-04-24
kedster@kedster-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main universe restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main universe restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
kedster@kedster-laptop:~$ cat /etc/apt/sources.list



PS: wat does cat do

---

### Post by SunnyRabbiera on 2008-04-24
yeh the servers are taking a beating right now, I am using a mirror just to make my system work.
if you need to know how to change your mirrors just ask

---

### Post by Kedster on 2008-04-24
lol i just want to get a few programs running ( internal wifi amsn emerald ccsm) so if its not to had id like to no ow to use mirrors
   

lol and what does the "cat" command do

---

### Post by grannyw on 2008-04-24
u should wait with it its the sever death because of the update

---

### Post by Kedster on 2008-04-24
ok ook thanks 


bt what is the cat command do

---

### Post by Kedster on 2008-04-24
hey when wil the servers be back upp

---

### Post by bilal.17 on 2008-04-24
> **Kedster said:**
> hey when wil the servers be back upp
when all the hype of the release dies down.. it should be back to normal after a couple of days max. a week

---

