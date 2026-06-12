---
title: "Cannot Update"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mealmond on 2008-04-28
Hi

When I try to update in Heron, I get the following error message;

'E:Type ‘Avant’ is not known on line 62 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Anybody any ideas how to resolve it?



Thanks


Martin

---

### Post by forestpixie on 2008-04-28
You have a problem with your sources list on line 62. Post it here and we can have a look - open a terminal paste this and post the resulting output here.

```
cat /etc/apt/sources.list
```

---

### Post by mealmond on 2008-04-28
Hi 

Thanks for the response, here are the details; hope it helps.


deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
  Avant Window Navigator
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

Thanks


Martin

---

### Post by tangibleorange on 2008-04-28
```
gksu gedit /etc/apt/sources.list
```

delete line 62 (the one that says "Avant Window Navigator") and save the file.

then try to update again. you may need to restart.

---

### Post by mikewhatever on 2008-04-28
Open the file for editing with <gksudo gedit /etc/apt/sources.list> and delete the third line from the bottom saying 'Avant Window Navigator', save and exit. Then run <sudo apt-get update>.

---

### Post by OffAxis on 2008-04-28
according to this:
[http://download.tuxfamily.org/syzygy42/index.html](http://download.tuxfamily.org/syzygy42/index.html)
you'll also want to delete those two bottom lines that pertain to the avant windows manager (these)
```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

``` and replace them with these two:
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

---

### Post by mealmond on 2008-04-28
Hi

I have  done all that has been suggested and now have the following error.

I have attached a screen shot.

Thanks for the help so far.



Martin

---

### Post by forestpixie on 2008-04-28
Edit the file again as you did previously - it's trying to access the cd-rom. At the beginning of the file there is this line

> deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

Put a # at the begining of the line, save and close the editor and run

```
sudo apt-get update
```

---

### Post by mealmond on 2008-04-28
Thanks to everybody for their help, especially Forestpixie, all is now updating again.

As you may tell I'm new to Unbuntu but really enjoying, it's just learning how to fix things and also learn what I can do or cannot do.


Thanks again


Martin

---

### Post by nyscreenwriter on 2008-04-28
I can't update, use add remove, or synpatic.

Here is my error message from synpatic.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Here is my source list.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by OffAxis on 2008-04-28
you should've started a new thread; you would have gotten much quicker responses...

Your problem isn't in the file you posted /etc/apt/sources.list
it's here:
> E: Type '<!DOCTYPE' is not known on line 1 in source list **/etc/apt/sources.list.d/medibuntu.list**

Comment out the problematic line (the first line)with a # sign or post the contents of that file here or in a new thread.

---

### Post by nyscreenwriter on 2008-04-28
I don't get it, though. If it's not in the sourcelist, how do I get to a place where I can uncomment the first line?  And how do I bring up the contents of that file to post it?

---

### Post by forestpixie on 2008-04-29
You need to do exactly the same to this file as we helped the OP with his file.

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

You've tried to add medibuntu- it makes it's own sources.list

Delete all the lines in the file, save and close.

Add medibunutu - open aterminal and do these commands seperately, I assume you're running Hardy.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by nyscreenwriter on 2008-04-29
Thank you so much it worked.  Update manager is working properly I will now upgrade to 8.04.

---

