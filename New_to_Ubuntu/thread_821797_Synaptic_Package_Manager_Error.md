---
title: "Synaptic Package Manager Error"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by artfart91 on 2008-06-07
Hi, im new to linux so i don't know how to fix this myself.
when i try to open the synaptic package manager, i get an error that reads as follows:


E: Type 'wget' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


I can't open it or download anything from it so if anyone has a solution please share it with me.
Thanks in advance!

---

### Post by perce on 2008-06-07
> **artfart91 said:**
> Hi, im new to linux so i don't know how to fix this myself.
when i try to open the synaptic package manager, i get an error that reads as follows:


E: Type 'wget' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


I can't open it or download anything from it so if anyone has a solution please share it with me.
Thanks in advance!

apparently you have a corrupted source list. Please attach the file /etc/apt/sources.list and someone will tell you what to do.

---

### Post by wolfen69 on 2008-06-07
do
```
cat /etc/apt/sources.list
```

---

### Post by perce on 2008-06-07
> **wolfen69 said:**
> do
```
cat /etc/apt/sources.list
```

or use the attach option in the forum to attach the file to your post

---

### Post by Oldsoldier2003 on 2008-06-07
the command

```
sudo nano +56 /etc/apt/sources.list
```
will open the file at line 56 ready to edit. 

Place a # there to comment the line (or ctrl +K to delete the line if you feel brave ).

then ctrl+x to exit 
y to confirm modified buffer
enter to save

this will correct the errant line.

next
```
sudo apt-get update
sudo apt-get upgrade
```
if you get any more errors please post them along with the return of
```

cat /etc/apt/source.list
```

---

### Post by artfart91 on 2008-06-07
allright i fixed the error on line 56 and now it says:


E: Type 'sudo' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and i tried to attach /etc/apt/sources.list and it said it was an invaild file.

---

### Post by Oldsoldier2003 on 2008-06-07
> **artfart91 said:**
> allright i fixed the error on line 56 and now it says:


E: Type 'sudo' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and i tried to attach /etc/apt/sources.list and it said it was an invaild file.

```
cat /etc/apt/sources.list
```

then copy and paste it into a reply on this thread we can take a look at it and point out the errors

---

### Post by artfart91 on 2008-06-07
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
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
#wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O- 

 sudo apt-key add -

sudo apt-get update

deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main




here you go

---

### Post by Oldsoldier2003 on 2008-06-07
> **artfart91 said:**
> #deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
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
[B][COLOR="Red"]#wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O- 

 sudo apt-key add -

sudo apt-get update

deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main[/COLOR][/B]




here you go
all the lines I marked in [COLOR="Red"]**bold red**[/COLOR] should be deleted and then you will be ok

---

### Post by artfart91 on 2008-06-07
ok i did what you said...
now it says this:


E: Type 'http://packages.dfreer.org' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by drs305 on 2008-06-07
> **artfart91 said:**
> ok i did what you said...
now it says this:


E: Type 'http://packages.dfreer.org' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

It looks like you didn't delete the line. The last line mentioned in post #9 (and in your repo) contains a reference to **gutsy**. You could try changing it to **hardy** to see if it works or just delete it /put a comment symbol (#)  in front of that line.

---

### Post by Oldsoldier2003 on 2008-06-07
> **artfart91 said:**
> ok i did what you said...
now it says this:


E: Type 'http://packages.dfreer.org' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I meant all the lines, the forum didnt bold red the url :/

```
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
``` should be the second to the last line in your list. the last line should be blank.
Sorry for the confusion

---

### Post by artfart91 on 2008-06-07
> **Oldsoldier2003 said:**
> I meant all the lines, the forum didnt bold red the url :/

```
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
``` should be the second to the last line in your list. the last line should be blank.
Sorry for the confusion

YES!!!! thank you!!!!
got it back working!!!!:):):)

---

