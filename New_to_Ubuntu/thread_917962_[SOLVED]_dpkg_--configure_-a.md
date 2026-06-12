---
title: "[SOLVED] dpkg --configure -a"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by speedzor on 2008-09-12
hi,

I keep getting the following error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

I get this every time I try to install a program (virtualbox, wine, etc).
And when I enter this command, my terminal is stuck for hours at the following rule:

```
jeroen@jeroen-laptop:~$ sudo dpkg --configure -a
Instellen van acidlab (0.9.6b20-22) ...
```

how can I fix this?
speedzor

---

### Post by perlluver on 2008-09-12
> **speedzor said:**
> hi,

I keep getting the following error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

I get this every time I try to install a program (virtualbox, wine, etc).
And when I enter this command, my terminal is stuck for hours at the following rule:

```
jeroen@jeroen-laptop:~$ sudo dpkg --configure -a
Instellen van acidlab (0.9.6b20-22) ...
```

how can I fix this?
speedzor

Nevermind, I read to fast, not sure why it is stuck.

---

### Post by SunnyRabbiera on 2008-09-12
By chance are you running desktop effects?

> **perlluver said:**
> In a terminal, run sudo dpkg --configure -a.  That should take care of it.

he said he tried that, but lets see if he is running effects first.

---

### Post by speedzor on 2008-09-12
I don't think I am, but to be sure: how can I check this?

---

### Post by SunnyRabbiera on 2008-09-12
> **speedzor said:**
> I don't think I am, but to be sure: how can I check this?

Right click on your desktop and Select "change desktop background"
and go to the last tab, it will tell you if you run effects or not...
I know it sounds silly now, but your terminal issue might be related to a bug I had under hardy.

---

### Post by perlluver on 2008-09-12
> **speedzor said:**
> I don't think I am, but to be sure: how can I check this?

Go to System>Preferences>Appearance, the last tab Visual Effects see if it says enabled or disabled.

---

### Post by Elfy on 2008-09-12
thewre was a similar thread a while back (maybe) with acidlab problems - there appears to be a bug

[https://bugs.launchpad.net/ubuntu/+source/acidlab/+bug/235827](https://bugs.launchpad.net/ubuntu/+source/acidlab/+bug/235827)

The poster in that one gave up and reinstalled - it might need a forced removal but not too sure atm

---

### Post by speedzor on 2008-09-12
well, no visual effects were enabled.

I'd rather wait a little bit with reinstalling, maybe another option can be found.

---

### Post by SunnyRabbiera on 2008-09-12
> **speedzor said:**
> well, no visual effects were enabled.

I'd rather wait a little bit with reinstalling, maybe another option can be found.

alright, making sure as I encountered an error when using the gnome terminal and desktop effects when using hardy.

---

### Post by Elfy on 2008-09-12
oh yes - wait indeed.

It has just worked for someone else - but it tooka while to complete in the first place, it's certainly not necessary to reinstall.

---

### Post by speedzor on 2008-09-12
So how did this person solved this?
At your link I can't find any comments or something like that..

---

### Post by Elfy on 2008-09-12
Different person speedzor - installed it from scratch and it did so, but did take a while to complete.

There were no comments at the link

---

### Post by speedzor on 2008-09-12
What do you mean by installing it from scratch?
And what do I have to do?

---

### Post by Elfy on 2008-09-12
He installed the program from start and it installed for him without error. There have been as I have said problems recently with the program it seems.

Until I'm sure what you can do to solve it I can't give any other reponse. In the meantime can you open a terminal and run this and post the output here please.

```
cat /etc/apt/sources/list
```


Edit - can you also try 

```
sudo aptitude purge acidlab
```

---

### Post by speedzor on 2008-09-12
```
jeroen@jeroen-laptop:~$ cat /etc/apt/sources/list
cat: /etc/apt/sources/list: No such file or directory

jeroen@jeroen-laptop:~$ sudo aptitude purge acidlab
[sudo] password for jeroen: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
Reading extended state information      
Initializing package states... Klaar
Building tag database... Klaar      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jeroen@jeroen-laptop:~$ 

```

---

### Post by Elfy on 2008-09-12
can you post the sources list - post14

and run 

```
sudo dpkg -C
```

post the output of both please

---

### Post by speedzor on 2008-09-12
```
jeroen@jeroen-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://be.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://be.archive.ubuntu.com/ubuntu/ hardy universe
deb http://be.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://be.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://be.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
jeroen@jeroen-laptop:~$ 

```

```

jeroen@jeroen-laptop:~$ sudo dpkg -C
[sudo] password for jeroen: 
De volgende pakketten zijn uitgepakt maar nog niet geconfigureerd.  Ze
moeten geconfigureerd worden met dpkg --configure of de menu optie
Configureren in dselect om ze te laten werken:
 libsoup2.4-1         an HTTP library implementation in C -- Shared library
 libgksu2-0           library providing su and sudo functionality
 eject                ejects CDs and operates CD-Changers under Linux
 language-pack-gnome-en GNOME translation updates for language English
 python-libxml2       Python bindings for the GNOME XML library
 libglib2.0-0         The GLib library of C routines

The following packages need to do processing triggered by other
package(s).  This processing can be requested with
dpkg --triggers or the configure menu option in dselect:
 libc6                GNU C Library: Shared libraries

De volgende pakketten zijn slechts half geconfigureerd, waarschijnlijk
wegens problemen tijdens de eerste keer configureren.  Het
configureren zou opnieuw moeten gebeuren met dpkg --configure <pakket>
of de menu optie Configureren in dselect:
 acidlab              Analysis Console for Intrusion Databases

The following packages have been triggered, but the trigger processesing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 libc6                GNU C Library: Shared libraries

jeroen@jeroen-laptop:~$ 

```

---

### Post by ibuclaw on 2008-09-12
Hello speedzor,

I have been playing in VMWare and I believe I have successfully reproduced your problem.

Can you just confirm something for me first?

[EDIT]
Actually, all that is required is this:

```
sudo gedit /var/lib/dpkg/info/acidlab.postinst
```
And put at the top (BEFORE . /usr/share/debconf/confmodule)
```
exit 0
```
Then run:
```
sudo dpkg --configure -a
```
again.

Which luck, that should result in a successful ending and the end of your dpkg issue.
Now, just purge the app.
```
sudo aptitude purge acidlab
```
And, if you get the following:
```
dpkg - warning: while removing acidlab, directory `/etc/acidlab' not empty so not removed.
```
During installation, then remove that directory manually.
```
sudo rm -r /etc/acidlab
```

Regards
Iain

---

### Post by speedzor on 2008-09-17
thanks man!
This worked perfectly!
Great job you did there!

---

### Post by Elfy on 2008-09-17
Glad that's worked for you - I'll put a link on the other thread as well and the bug.

---

