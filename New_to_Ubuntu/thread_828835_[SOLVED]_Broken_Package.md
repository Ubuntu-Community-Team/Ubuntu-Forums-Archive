---
title: "[SOLVED] Broken Package"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Bonzzai on 2008-06-14
Logged onto my computer this morning to have an error... The update manager on the task bar had a red error sign, and the following message: "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error:BrokenCount > O'This usually means that your installed packages have unmet dependences"

So I opened Synaptic Package Manager, found that the broken package is 'libsane', some sort of scanner finder? Anyway, I click to re-install it, Synaptic closes all of a sudden. The same thing happens when I click to uninstall it.

I tried another solution by opening up the terminal and typing in 'apt-get update upgrade', which didn't help at all... Got this after typing 'sudo apt-get install libsane'

```
The following packages have unmet dependencies:
  libsane: Depends: udev ( 0.88-1) but 117-8 is to be installed or
                    libkscan1 (>= 2.3.1-58) but it is not going to be installed

```

I tried installing them by typing 'sudo apt-get install udev' or libkscan1, but it wouldn't allow me D:

Thanks if you can help.

---

### Post by PmDematagoda on 2008-06-14
Post the outputs of:-
```
sudo apt-get install -f
```
and
```
cat /etc/apt/sources.list
```

---

### Post by Bonzzai on 2008-06-14
Here're the results for 'apt-get install -f'

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Segmentation fault

```

And here are the other results :]
Sorry if it's more than you needed.
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by PmDematagoda on 2008-06-14
The segmentation fault isn't a nice thing to see, try and remove the package in question with:-
```
sudo apt-get remove libsane
```
but if it gives you a place to say Y/n then post the output of that here and do not continue until you are sure that you may continue.

---

### Post by Bonzzai on 2008-06-14
Hmm, well I typed that in and got this.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  hpijs: Depends: libsane (>= 1.0.11-3) but it is not going to be installed
  hplip: Depends: libsane (>= 1.0.11-3) but it is not going to be installed
  xsane: Depends: libsane (>= 1.0.11-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by PmDematagoda on 2008-06-14
Try:-
```
sudo apt-get install --reinstall libsane
```

---

### Post by Bonzzai on 2008-06-14
Gaaah. I just got this again.

```
sudo apt-get install --reinstall libsane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsane: Depends: udev ( 0.88-1) but 117-8 is to be installed or
                    libkscan1 (>= 2.3.1-58) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by PmDematagoda on 2008-06-14
Post the output of:-
```
dpkg -C
```

---

### Post by Bonzzai on 2008-06-14
When I type that in, nothing appears, another line just appears for me to type a command :]

---

### Post by PmDematagoda on 2008-06-14
If you are willing to try something risky, try removing the package with:-
```
sudo dpkg -remove --force-depends libsane
```
and reinstall it with:-
```
sudo apt-get install libsane
```

---

### Post by Bonzzai on 2008-06-14
Well, when I first pasted the first command, it wouldn't do anything. So I replaced '-replace' with '-r'. Wow, I hope I didn't do something wrong.

Okay, well now the red error sign is a black error sign. It's letting me start it up, though. Should I install through the terminal or through the package manager? :P

---

### Post by PmDematagoda on 2008-06-14
Try opening Synaptic and see if it works, if not post the error message.

---

### Post by Bonzzai on 2008-06-14
I opened Synaptic instead of the package manager. There are three broken packages, all printer and scanner related. I'm gonna type that second command you gave me now and hope that that puts everything good as new. n_n

**Edit: ||**
Ah! Okay, well I re-installed it through the terminal, and no errors at all anymore.
Thanks bunches! :D

---

