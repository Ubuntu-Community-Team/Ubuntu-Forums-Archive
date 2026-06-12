---
title: "Can'y install programs or updates"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by kdub on 2008-05-28
Hi,
I tried to install a program-couldn't figure out how to do it. Now I get this message in adept update "The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem." After much struggle I got to this message in konsole:
"kdub@laptop:~$ gedit /etc/apt/sources.list
The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
bash: gedit: command not found
kdub@laptop:~$ sudogedit /etc/apt/sources.list
bash: sudogedit: command not found
kdub@laptop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for kdub:
sudo: gedit: command not found
kdub@laptop:~$ sudo apt-get update
E: Malformed line 57 in source list /etc/apt/sources.list (dist)
kdub@laptop:~$ "

I'm lost- can anyone guide me?
thanx
kdub

---

### Post by oldos2er on 2008-05-28
Try "sudo nano /etc/apt/sources.list"

---

### Post by OffAxis on 2008-05-28
you can also go straight to line 57 (your malformed line) with
```
sudo nano +57 /etc/apt/sources.list
```

if you need to you can put a # sign at the beginning of a line to completely comment it out (so apt won't read it). 
Then **Ctrl + X**, **Y**, and [B]Enter.

[/B]If you still need help just post the contents of the sources.list file.

---

### Post by arochester on 2008-05-28
Gedit is found in Ubuntu but can be installed and works in Kubuntu. The editor Kubuntu uses is called Kate. The command should have been "sudo kate /etc/apt/sources.list"

---

### Post by kdub on 2008-05-28
I did                                                                                                    "sudo kate /etc/apt/sources.list"                             and got this in kate deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
deb [http://home/kdub/Desktop/FTA](http://home/kdub/Desktop/FTA)
the last line is the program that is causing the problem-what do I do now?

---

### Post by drs305 on 2008-05-28
> **kdub said:**
> 
the last line is the program that is causing the problem-what do I do now?

Make it read like this for now (it's not a valid address) or just delete it:
```
# deb http://home/kdub/Desktop/FTA
```
You can make a backup copy first if you want before you make the change:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

---

### Post by Oldsoldier2003 on 2008-05-28
> **kdub said:**
> I did                                                                                                    "sudo kate /etc/apt/sources.list"                             and got
< snip>
**#deb [http://home/kdub/Desktop/FTA**](http://home/kdub/Desktop/FTA**)
the last line is the program that is causing the problem-what do I do now?
or just delete that line

---

### Post by kdub on 2008-05-28
Well!,
I've gotten this far
"
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main




File Name to Write: /etc/apt/sources.list
^G Get Help         ^T To Files         M-M Mac Format      M-P Prepend
^C Cancel           M-D DOS Format      M-A Append          M-B Backup File
I now can't figure out how to save from here. No matter what key I press it shows up on screen- also being the slow type that I am which of these commands translates to "save"
thanx,
ken

---

### Post by Maestro23 on 2008-05-28
What text editor did you use?

---

### Post by drs305 on 2008-05-28
> **kdub said:**
> Well!,

I now can't figure out how to save from here. No matter what key I press it shows up on screen- also being the slow type that I am which of these commands translates to "save"
thanx,
ken

CTRL-O then Enter should save it in nano.

Added: Then CTRL-X to exit. Guess you might need that as well ;-)

Guess you might not be using the nano command from earlier after all...

---

### Post by kdub on 2008-05-28
Tried kate but couldn't figure out how to save so went to konsole and got the afore mentioned screen.
thanx
ken

---

### Post by Maestro23 on 2008-05-28
> **kdub said:**
> Tried kate but couldn't figure out how to save so went to konsole and got the afore mentioned screen.
thanx
ken

Again, what text editor did you use?  What were the commands you typed to open the file?

---

### Post by kdub on 2008-05-28
The only things I tried were kate and konsole-whats a text editor? How do they work? where do I get one? If it has to be installed I can't do it install remove stopped working along with apt...
thanx
ken

---

### Post by Maestro23 on 2008-05-28
> **kdub said:**
> The only things I tried were kate and konsole-whats a text editor? How do they work? where do I get one? If it has to be installed I can't do it install remove stopped working along with apt...
thanx
ken

Ok. I take it you are running Kubuntu. It has a text editor called kate. This is what you use to edit files. So, in a terminal you will type the following to edit your /etc/apt/sources.list

> sudo kate /etc/apt/sources.list

Make the changes you were told to, and then save the file and exit the program(kate).

Then in terminal:

> sudo apt-get update

sudo apt-get upgrade

---

### Post by kdub on 2008-05-29
Success!!! Thank you all for your patience!
 I don't know why the brain cramp, but what you told me to do was the same as
messing with a sys.config file in some other os.
I'll be back
thanx
ken

---

