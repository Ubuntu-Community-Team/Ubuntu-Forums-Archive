---
title: "Problem with Ububntu Software Centre"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by samsdad on 2012-02-01
I'm running Ubuntu 10.04 on my laptop.

I'm not very teckie and since I installed I have only really used it to access the internet through Firefox.

The first problem I need to sort is that when I go to the software centre I don't get any listings just the familiar 'egg timer' equivalent.

If I go to the' Installed software' then 'software updates' I get

 p, li { white-space: pre-wrap; }  The package list needs to be rebuilt.
 This should have been done by the backend automatically.


If I go to system/administration/synaptic package manager (though I don't know why I went there I get



E: Type ‘See’ is not known on line 2 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


Clearly there is something corrupted but as a new user I don't know what it is or how I put it right.


Can anyone help please?

---

### Post by Double.J on 2012-02-01
Hi there! Welcome to the forums. Synaptic is saying your repository list has an error in it. 

Open a terminal with CTRL+ALT+T and paste in the following
```
gksudo gedit /etc/apt/sources.list
``` and paste the output in a reply (highligh and click on the # symbol to put in the CODE quotes :)

All the best!

---

### Post by raja.genupula on 2012-02-01
give us the output of 
cat /etc/apt/sources.list

copy the terminal code and paste here .

Thank you .

---

### Post by samsdad on 2012-02-01
Thanks for the help

I think this is what you asked for.

I hope it makes more sense to you than it does to me.

deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
 See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
 newer versions of the distribution.

deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

 Major bug fix updates produced after the final release of the
 distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team. Also, please note that software in universe WILL NOT receive any
 review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team, and may not be under a free licence. Please satisfy yourself as to
 your rights to use the software. Also, please note that software in
 multiverse WILL NOT receive any review or updates from the Ubuntu
 security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

 Uncomment the following two lines to add software from the 'backports'
 repository.
 N.B. software from this repository may not have been tested as
 extensively as that contained in the main release, although it includes
 newer versions of some applications which may provide useful features.
 Also, please note that software in backports WILL NOT receive any review
 or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
 Uncomment the following two lines to add software from Canonical's
 'partner' repository.
 This software is not part of Ubuntu, but is offered by Canonical and the
 respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed restricted main multiverse universe

------------------------------

---

### Post by cortman on 2012-02-01
Whoa! It looks like your whole sources.list file got "uncommented". Bash and a couple other programming languages use a hash mark (#) at the beginning of each line they don't want the program to execute. In your case, you need to add hash mark to the beginning of each line NOT begknning with "deb". That way the software center doesn't try to find repo information fromthe comments.

---

### Post by wolfen69 on 2012-02-01
Your list is not uncommented properly

It should look like this:

#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
#See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
#newer versions of the distribution.

#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

##Major bug fix updates produced after the final release of the
##distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

##N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
##team. Also, please note that software in universe WILL NOT receive any
##review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

##N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
##team, and may not be under a free licence. Please satisfy yourself as to
##your rights to use the software. Also, please note that software in
##multiverse WILL NOT receive any review or updates from the Ubuntu
security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

##Uncomment the following two lines to add software from the 'backports'
##repository.
##N.B. software from this repository may not have been tested as
##extensively as that contained in the main release, although it includes
##newer versions of some applications which may provide useful features.
##Also, please note that software in backports WILL NOT receive any review
##or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
##Uncomment the following two lines to add software from Canonical's
##'partner' repository.
##This software is not part of Ubuntu, but is offered by Canonical and the
##respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed restricted main multiverse universe

Notice how I added "#" to some lines. Copy the list above and do:

```
gksudo gedit /etc/apt/sources.list
``` and delete what's in there, and paste the list above in there. Close and save. Then
```
sudo apt-get update
```

Report back.

---

### Post by samsdad on 2012-02-02
I've done what you suggest and the result is below

david@david-laptop:~$ sudo apt-get update
E: Type ‘security’ is not known on line 28 in source list /etc/apt/sources.list
david@david-laptop:~$ 

Sorry to be a moaner but is Ubuntu always this difficult? In 17 byears of using a rival OS (no names) I haven't had to do this kind of thing. And I won't even start to tell you about my failure to get wi-fi!

Anyway your help really is appreciated. What next?

---

### Post by raja.genupula on 2012-02-02
look for the below line and do the changes and update again .

```
##multiverse WILL NOT receive any review or updates from the Ubuntu security team.
```

arrange it like that 

or

```
##multiverse WILL NOT receive any review or updates from the Ubuntu 
##security team.
```

All the best.

---

### Post by samsdad on 2012-02-02
Wow

When things happen in Linux they really happen in a dramatic way. It takes me back to my DOS days. Lots of code and then a long download.

Everything seems to be working.

I'm even tempted to have another go at wireless.

Thanks so much for your help

David

---

