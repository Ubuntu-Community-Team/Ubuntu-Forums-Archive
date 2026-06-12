---
title: "[SOLVED] Where is k9copy ?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-11-13
I tried to upgrade to Intrepid 8.10. But with too many issues I decided to revert back to Hardy 8.04.1 . Now I can't find K9Copy in either the System>Admin>SynPkgMgr - Add/Remove & receive an Invalid operation k9copy when I try to retrieve it on a terminal page. Can someone tell me whai I need to do to re-install the program. Thanks

---

### Post by taurus on 2008-11-13
There is a k9copy, version 1.2.3-0ubuntu1.  What happens if you try to install it from a terminal?

---

### Post by CoCoKnots on 2008-11-13
"receive an Invalid operation k9copy when I try to retrieve it on a terminal page".

---

### Post by taurus on 2008-11-13
What was the exact command that you ran?  Also, can you post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by CoCoKnots on 2008-11-13
sodo apt-get k9copy Is this not correct ?

---

### Post by taurus on 2008-11-13
```
sudo apt-get update
sudo apt-get **install** k9copy
```

---

### Post by CoCoKnots on 2008-11-13
It did the update OK... But when I tried the apt-get... this came up:
E: Couldn't find package k9copy

---

### Post by taurus on 2008-11-13
Here is what I got when I ran it on my machine.

```

sudo apt-get install k9copy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  vamps
The following NEW packages will be installed:
  k9copy vamps
0 upgraded, 2 newly installed, 0 to remove and 11 not upgraded.
Need to get 1596kB of archives.
After this operation, 3305kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by CoCoKnots on 2008-11-13
> **taurus said:**
> What was the exact command that you ran?  Also, can you post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

OK Taurus, This is what I have... Does this look correct to you ?


cocoknots@cocoknots-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main universe #Added by software-properties

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

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main universe #Added by software-properties
cocoknots@cocoknots-laptop:~$

---

### Post by taurus on 2008-11-13
> **CoCoKnots said:**
> 
cocoknots@cocoknots-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main universe #Added by software-properties

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

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Blue"]#[/COLOR] deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
[COLOR="Blue"]#[/COLOR] deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
[COLOR="Blue"]#[/COLOR] deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
[COLOR="Blue"]#[/COLOR] deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main universe #Added by software-properties
cocoknots@cocoknots-laptop:~$

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # (four of them) in blue.  Save it and close gedit window.  Now, see if you can install k9copy with

```
sudo apt-get update
sudo apt-get install k9copy
```

---

### Post by CoCoKnots on 2008-11-13
I have 5 (five) lines with 1# in fornt of it... Should I remove all five lines ?


# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main universe #Added by software-properties

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

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main universe #Added by software-properties

---

### Post by taurus on 2008-11-13
> **CoCoKnots said:**
> I have 5 (five) lines with 1# in fornt of it... Should I remove all five lines ?

What 5 lines?  Remove only the ones, #, in blue.

> # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main universe #Added by software-properties

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

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
**[COLOR="Blue"]#[/COLOR]**deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
**[COLOR="Blue"]#[/COLOR]**deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
**[COLOR="Blue"]#[/COLOR]**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
**[COLOR="Blue"]#[/COLOR]**deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main universe #Added by software-properties

---

### Post by CoCoKnots on 2008-11-13
OK... Thanks. My copy from the terminal did not show them in blue. Thanks for sending the printout.

---

### Post by CoCoKnots on 2008-11-13
OK, I removed the 4 lines & saved.

I then ran the two sudo commands & this is what I got...

cocoknots@cocoknots-laptop:~$ sudo apt-get install k9copy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package k9copy
cocoknots@cocoknots-laptop:~$ 


I don't understand where k9copy has gone. It simply didn't come in during this install of Hardy... It's almost like it didn't read something it was suppose to during the install process.

---

### Post by taurus on 2008-11-13
I am going to give you my version and see if that cures the problem.

From a terminal, backup your original /etc/apt/sources.list first.

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
Now, you should see an empty/blank gedit window.  Cut and paste the following lines to it.

```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse

```
Save it and close down gedit window.  Now run

```
sudo apt-get update
sudo apt-get install k9copy
```

---

### Post by CoCoKnots on 2008-11-13
Something isn't right here...

This is what I see going on. Which isn't what I see on your screen.

cocoknots@cocoknots-laptop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.orig
[sudo] password for cocoknots: 
cocoknots@cocoknots-laptop:~$ 


I didn't have the opportunity to type in the gksudo command you have.

---

### Post by taurus on 2008-11-13
> **CoCoKnots said:**
> Something isn't right here...

This is what I see going on. Which isn't what I see on your screen.

cocoknots@cocoknots-laptop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.orig
[sudo] password for cocoknots: 
cocoknots@cocoknots-laptop:~$ 

I didn't have the opportunity to type in the gksudo command you have.

There is nothing wrong.  The first command, sudo mv blah blah..., just renamed your original /etc/apt/sources.list to /etc/apt/sources.list.orig.

Now, type in the second command to edit the new /etc/apt/sources.list which should be a new file.

```
gksudo gedit /etc/apt/sources.list
```

p.s.  Each line is a separate command which means you have to hit ENTER before you can type in the next command.

---

### Post by oldos2er on 2008-11-13
"I removed the 4 lines & saved."

 You were only supposed to remove the comment marks (#), not whole lines.

---

### Post by CoCoKnots on 2008-11-13
Great... That worked. Without a PhD in programming,can you give me an idea of what happened here ?

---

### Post by SuperSonic4 on 2008-11-13
Basically a # before a line tells ubuntu to ignore it
Since your source lines had a # at the front apt ignored them
By removing the # it means apt reads them and can find k9copy

---

### Post by taurus on 2008-11-13
You probably didn't have enough repos in your original /etc/apt/sources.list.  You can see how many repos I have in my/your /etc/apt/sources.list now vs your original in /etc/apt/sources.list.orig.

---

### Post by CoCoKnots on 2008-11-13
OK... Now that I've screwed up & removed the entire line instead of just the #... Now what do I need to do ? (...If Anything) ?

---

### Post by SuperSonic4 on 2008-11-13
Post 15 tells you what to do :)

---

### Post by taurus on 2008-11-13
You can continue to use the version of /etc/apt/sources.list that I sent you.  Don't worry about what you did to your original version, /etc/apt/sources.list.orig, because the system doesn't even care if it's there.  Synaptic/apt-get/apt/adept will only read /etc/apt/sources.list.

---

### Post by CoCoKnots on 2008-11-13
Thanks taurus for all the help... 'Time to rest a little before addressing the next issue.

---

