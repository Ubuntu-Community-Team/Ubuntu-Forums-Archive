---
title: "broken filter?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by WriteGirl on 2008-11-24
I stumbled upon a page with ten things that you should do after installing ubuntu. It seemed to be good and had comments agreeing with the suggestions, so I tried to get medibuntu using this code.

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

When I tried to run it, it told me I had unmet dependencies, and now every time I try to get new updates, there's a red circle with a line through it on the top panel and I get an error message saying I need to run the broken filter before I do anything. 

What went wrong? 

(here's the website I got it from, if that helps at all. [http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html))

---

### Post by taurus on 2008-11-24
What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by WriteGirl on 2008-11-24
With the first one, it only asks me for my password, and nothing that I can see happens. For the second one, I got this long thing, starting with a series of lines beginning with"Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg" and then lines beginning with " gn [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US " eventually, it tells me that it failed to the the cdrom and it ends with saying that some files failed to download, and they have been ignored or replaced with old files.

---

### Post by taurus on 2008-11-24
Looks like you have mixed releases in your /etc/apt/sources.list.  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

You can cut the text by highlighting it with the right button of the mouse and paste it in your message with the little scroll bar.

---

### Post by WriteGirl on 2008-11-24
I upgraded to hardy heron about a week before I did that, but I didn't have any problems before then

```
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by Furat on 2008-11-24
System -> Administration -> synaptec 

in the left panel click on broken 
remove or reinstall all the broken package

---

### Post by taurus on 2008-11-24
Edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, the one with cdrom in it, to comment it out.

Then, replace the word **hardy** with the word **intrepid** since you are running Intrepid now, not Hardy anymore.

Your new /etc/apt/sources.list should look something like this.

```

**[COLOR="Blue"]#[/COLOR]**deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ **[COLOR="Blue"]intrepid[/COLOR]**-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ **[COLOR="Blue"]intrepid[/COLOR]**-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu **[COLOR="Blue"]intrepid[/COLOR]** partner
deb-src http://archive.canonical.com/ubuntu **[COLOR="Blue"]intrepid[/COLOR]** partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```
Save it and close down gedit window.  Then from a terminal, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by WriteGirl on 2008-11-24
I have no idea what happened. I was running the two programs you had, and the first one worked fine, but halfway through the second, my computer screen went black. I waited to see if it would come back, it didn't and then I shut it off. When I tried to turn it back on, it stayed black, I heard the air fan thing for about ten seconds and then it shut off again.

---

