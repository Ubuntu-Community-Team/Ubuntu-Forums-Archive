---
title: "update manager"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by shubham1 on 2011-10-08
i am trying to upgrade ubuntu throught update manager  but when net automaticaaly disconnects my full donwload stops and distroys this has happened many times i want a update manager that can pause this is stupidness.
this is not a thread of oneric ochlet

---

### Post by raja.genupula on 2011-10-08
have you tried to do update from terminal ?I have choose this as the best way.I am also suffered a lot with this GUI update manager while updating chrome.so i went to terminal to do this job.that thread of mine still unsolved.so try to go with terminal.

all the best.

---

### Post by shubham1 on 2011-10-08
> **raja.genupula said:**
> have you tried to do update from terminal ?I have choose this as the best way.I am also suffered a lot with this GUI update manager while updating chrome.so i went to terminal to do this job.that thread of mine still unsolved.so try to go with terminal.

all the best.
whats the command for terminal

---

### Post by shubham1 on 2011-10-08
terminal is really easy and usc is easy too

---

### Post by Linuxisfast on 2011-10-08
> **shubham1 said:**
> whats the command for terminal

```
sudo apt-get update sudo apt-get upgrade
```

---

### Post by raja.genupula on 2011-10-08
> **Linuxisfast said:**
> ```
sudo apt-get update sudo apt-get upgrade
```

hi small correction 
```
sudo apt-get update ; sudo apt-get upgrade
```

or you can do update and upgrade individually

```
sudo apt-get update
```

& then 

```
sudo apt-get upgrade
```


all the best

---

### Post by shubham1 on 2011-10-08
> **Linuxisfast said:**
> ```
sudo apt-get update sudo apt-get upgrade
```
this will update to 11.10
and can you tell the command for upgrading a single software using terminal

---

### Post by shubham1 on 2011-10-11
i have tried apt-get upgrade
apt-get update
apt-get dist-upgrade
and done still it is not upgraded

---

### Post by shubham1 on 2011-10-11
i have tried to upgrade to 11.10
sudo apt-get update
and then sudo apt-get upgrade
and sudo apt-get dist-upgrade
after long timne of dwowndloading still my system is not updated some users told me about these commadns i have tried to update manger but that is madness

---

### Post by dino99 on 2011-10-11
how is /etc/apt/sources.list (sudo gedit) ?

---

### Post by shubham1 on 2011-10-11
> **dino99 said:**
> how is /etc/apt/sources.list (sudo gedit) ?
```
 deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```please i dont want any further donwloads try to avoid them

---

### Post by dino99 on 2011-10-11
So when you open synaptic, is there a list of packages ready for upgrading ?
(check settings -> repos activation (main, universe, multiverse)

Or from a terminal, do you get warnings/errors when you try to upgrade ?

note: sources.list is ok

---

### Post by shubham1 on 2011-10-11
no i do not get a warning from terminal

---

### Post by Mr. Picklesworth on 2011-10-11
What do you mean by “after long timne of dwowndloading still my system is not updated”?

Does that mean it only *did* the downloading stage? There are two stages when you use apt-get, and it only starts installing packages after all of them are downloaded.

---

### Post by shubham1 on 2011-10-11
> **Mr. Picklesworth said:**
> What do you mean by “after long timne of dwowndloading still my system is not updated”?

Does that mean it only *did* the downloading stage? There are two stages when you use apt-get, and it only starts installing packages after all of them are downloaded.
apt-get is done
now when i use apt-get upgrade then it shows nothing to upgrade

---

### Post by Mustang33 on 2011-10-11
This is what I did.

Atl + F2 to get a "run" dialog and type: update-manager -d

You could also do it from a terminal prompt with: sudo update-manager -d

This will tell update manager to look for a new Distribution upgrade.  You will see it at the top when it open and just click Okay or whatever and you are off to the races...

---

### Post by 23dornot23d on 2011-10-11
Have you re-booted the computer since doing the upgrade ?

---

### Post by mikewhatever on 2011-10-11
> **shubham1 said:**
> i have tried to upgrade to 11.10
sudo apt-get update
and then sudo apt-get upgrade
and sudo apt-get dist-upgrade
after long timne of dwowndloading still my system is not updated some users told me about these commadns i have tried to update manger but that is madness

This is not at all how you upgrade an Ubuntu release.
If you want to use commands, then this is the way to go:
```
sudo do-release-upgrade
```

That said, I'd strongly recommend waiting for the final release.

---

### Post by sgage on 2011-10-11
I think you should probably consider a clean install at this point. Backup your home directory and start over with a fresh copy of the final release, which is coming out in a couple of days.

---

### Post by shubham1 on 2011-10-12
> **mikewhatever said:**
> This is not at all how you upgrade an Ubuntu release.
If you want to use commands, then this is the way to go:
```
sudo do-release-upgrade
```

That said, I'd strongly recommend waiting for the final release.
yes i did it
[http://ubuntuforums.org/showthread.php?t=1856403](http://ubuntuforums.org/showthread.php?t=1856403)

---

### Post by shubham1 on 2011-10-12
yes

---

### Post by shubham1 on 2011-10-12
> **sgage said:**
> I think you should probably consider a clean install at this point. Backup your home directory and start over with a fresh copy of the final release, which is coming out in a couple of days.
i tried it
[http://ubuntuforums.org/showthread.php?t=1853345](http://ubuntuforums.org/showthread.php?t=1853345)

---

### Post by shubham1 on 2011-10-12
> **mikewhatever said:**
> This is not at all how you upgrade an Ubuntu release.
If you want to use commands, then this is the way to go:
```
sudo do-release-upgrade
```

That said, I'd strongly recommend waiting for the final release.
yes it will come on 13 - 10 2011 that is tommorow

---

### Post by shubham1 on 2011-10-12
i tried all update manger is fullishness

---

### Post by 23dornot23d on 2011-10-12
Can you post the output .....

do 

sudo apt-get update
sudo apt-get install aptitude

[B]sudo aptitude update
sudo aptitude safe-upgrade[/B]

( these commands are only going to upgrade to whatever release you are using - but
once these have completed - we can then see what is happening with your system and we will continue from there )

start with the above ...... but show us what your output is please .......

or wait till tomorrow and do a full clean install ...... in a separate partition to try it out
first .......

---

### Post by alphacrucis2 on 2011-10-12
None of that is relevant to doing a release upgrade. Once 11.10 is officially released, update manager will offer to do the upgrade if you are running 11.04. The following command will also work AFTER the official release:

```
sudo do-release-upgrade
```

To update before the official release you are upgrading to a development version. To do that you need:

```
sudo do-release-upgrade -d
```

---

### Post by 23dornot23d on 2011-10-12
Reason I asked was to get an idea of what the system is like and any errors that may be obvious to us but not to the user ......

He can do the upgrade without checking ...... ( as you say )

He can also not bother doing a an install in a clean partition ...... 
( but once he upgrades - you can help him get his system back )
you know like me it will be impossible to do ...... if it fails again to work.

Then your only sure option of a good system is probably a clean install ....... 
or a few hours sorting out problems that may be there ........

[COLOR=Red]**but If it was my system **[/COLOR]

I like to see what the problems are before just letting the system decide for me ....... ;)

---

### Post by alphacrucis2 on 2011-10-12
> **23dornot23d said:**
> Reason I asked was to get an idea of what the system is like and any errors that may be obvious to us but not to the user ......

He can do the upgrade without checking ...... ( as you say )

He can also not bother doing it a an install in a clean partition ...... 
( but once he upgrades - you can help him get his system back )
you know like me it will be impossible to do ...... 
then your only option is probably a clean install ....... or a few hours sorting
out any problems that may be there ........

[COLOR=Red]**but If it was my system **[/COLOR]

I like to see what the problems are before just letting the system decide for me ....... ;)


Yeah definitely. You should always make sure your current release is fully updated and healthy before attempting a release upgrade.

---

### Post by shubham1 on 2011-10-12
ok

---

### Post by shubham1 on 2011-10-12
> **alphacrucis2 said:**
> None of that is relevant to doing a release upgrade. Once 11.10 is officially released, update manager will offer to do the upgrade if you are running 11.04. The following command will also work AFTER the official release:

```
sudo do-release-upgrade
```To update before the official release you are upgrading to a development version. To do that you need:

```
sudo do-release-upgrade -d
```

> **23dornot23d said:**
> Reason I asked was to get an idea of what the system is like and any errors that may be obvious to us but not to the user ......

He can do the upgrade without checking ...... ( as you say )

He can also not bother doing a an install in a clean partition ...... 
( but once he upgrades - you can help him get his system back )
you know like me it will be impossible to do ...... if it fails again to work.

Then your only sure option of a good system is probably a clean install ....... 
or a few hours sorting out problems that may be there ........

[COLOR=Red]**but If it was my system **[/COLOR]

I like to see what the problems are before just letting the system decide for me ....... ;)

> **23dornot23d said:**
> Can you post the output .....

do 

sudo apt-get update
sudo apt-get install aptitude

[B]sudo aptitude update
sudo aptitude safe-upgrade[/B]

( these commands are only going to upgrade to whatever release you are using - but
once these have completed - we can then see what is happening with your system and we will continue from there )

start with the above ...... but show us what your output is please .......

or wait till tomorrow and do a full clean install ...... in a separate partition to try it out
first .......
its good to wait till tomorow

---

### Post by vasa1 on 2011-10-12
> **23dornot23d said:**
> ...
but If it was my system

I like to see what the problems are before just letting the system decide for me ....... ;)

But why do you suggest installing **aptitude**?

---

### Post by shubham1 on 2011-10-12
> **vasa1 said:**
> But why do you suggest installing **aptitude**?
[B]aptitude i think comes by default or are you talking about gui version

[/B]

---

### Post by 23dornot23d on 2011-10-12
In my many years of using aptitude it has never let me down and I have done some
pretty crazy upgrades using it ...... 

kanotix upgrade through to 11.04
and just recently 
[[COLOR=Blue]**kanotix through to mint 11**[/COLOR]]("http://img64.imageshack.us/img64/6488/kanotixmintdebian.jpg") ..... and its documented step by step in a [**thread on here**]("http://ubuntuforums.org/showthread.php?t=1815049&page=19") .....

apt-get on the other hand has left me with so many dependency problems just doing normal upgrades = leaving the only sensible option left >>> re-install.

for people knowing the full ins and outs of dpkg ...... then they may know how to recover
but for the majority of people aptitude can save your system - with reasonably little
worry ,,,,, :)

---

### Post by shubham1 on 2011-10-12
> **23dornot23d said:**
> In my many years of using aptitude it has never let me down and I have done some
pretty crazy upgrades using it ...... 

kanotix upgrade through to 11.04
and just recently 
kanotix through to mint 11 ..... and its documented step by step in a thread on here .....

apt-get on the other hand has left me with so many dependency problems just doing normal upgrades = leaving the only sensible option left >>> re-install.

for people knowing the full ins and outs of dpkg ...... then they may know how to recover
but for the majority of people aptitude can save your system - with reasonably little
worry ,,,,, :)
ok

---

### Post by vasa1 on 2011-10-12
> **23dornot23d said:**
> In my many years of using aptitude it has never let me down and I have done some
pretty crazy upgrades using it ...... 
...
but for the majority of people aptitude can save your system - with reasonably little
worry ,,,,, :)

Thanks for clarifying!

---

### Post by shubham1 on 2011-10-12
> **vasa1 said:**
> Thanks for clarifying!
from how many years you are using apttitude

---

### Post by 23dornot23d on 2011-10-12
Well I cannot be certain on this .......

Probably 3 years ........ it was when I wanted UBUNTU which was my first upgrade from
kanotix  so possibly 2008 to 2011 ..... 

Ubuntu 8.10 is the one I still have running on one of my drives ......

I wanted to upgrade from Kanotix ( debian based ) .....  to UBUNTU ..... which I can still do.

Before that I used apt-get ...... it was only when I started losing systems back then that I changed to using aptitude ......

Its personal preference - but you should really stick with one once you decide whats best for
you ,,,, mine is through personal experience ......

If someone wants to set a challenge at upgrading from one version to the next - we could run a thread and see what problems are encountered with both.

I believe in being open and truthful and if something does not work ....... we highlight it
that way it can be fixed .......

At the moment ..... new programs get written which mean we have to start all over again .....  

If they stuck with Aptitude we would be in a great position now to upgrade

Instead we have many means to upgrade 

The least successful is ...... Partial Upgrade ...... which I have yet to hear someone praise

Full-Upgrade ..... well we are about to see how good that is ........ ;)

I will pull the links into here tomorrow ...... of the failures ....... as we get them ......

---

### Post by vasa1 on 2011-10-12
> **23dornot23d said:**
> ...
I will pull the links into here tomorrow ...... of the failures ....... as we get them ......

That's a tricky thing. When something fails, it could be for any of many reasons. What would be important is to know whether there's something fundamentally flawed as opposed to goof ups.

---

### Post by 23dornot23d on 2011-10-12
We will read through them - I always do ...... if I can help solve things I will ......

If there are things that are unavoidable through systems already being corrupt there is
not a lot we can do other than say re-install .....

But we choose through making reasonable judgments .....

If anyone disagrees with one we remove it from the list .....


This Oneiric Testing Area may get closed tonight ........ so will have to create a Fresh Thread .....
[URL="http://ubuntuforums.org/showthread.php?p=11334068#post11334068"][COLOR=Red][B]
LINK TO PROBLEMS WITH UPGRADES[/B][/COLOR][/URL] - add what are relevant here

---

### Post by vasa1 on 2011-10-12
> **23dornot23d said:**
> We will read through them - I always do ...... if I can help solve things I will ......

If there are things that are unavoidable through systems already being corrupt there is
not a lot we can do other than say re-install .....

...

I for one appreciate the help!

Off the top, what could be the reasons for things failing when an update is attempted?
An excessively tweaked 11.04?
Too many ppas?
Not caring to update/upgrade the existing release before upgrading to the new one?
Shubham1's original point ... dropped net connections at some point or the other?
Anything else?

---

### Post by 23dornot23d on 2011-10-12
Something 

I think happens but cannot be sure .....

Many users report power outages ....... ( this may happen ..... )

But from the number reported .... maybe they just get bored with waiting or just kill
the download/upgrade ...... 

This to me is a sure way to Bork the system good and proper ......

People need to be made aware it can take a long time to fully upgrade ...we are talking hours for some systems .......... 

( THEY NEED TO BE PATIENT )

If it is stopped while downloading ..... its not so bad ...... [but its not good ..... this should be avoided]
leave yourselves plenty of time ..... and also do not do it on a laptop on battery power alone ...... 

[COLOR=Red][B]but once it gets to setting up the SYSTEM ...... any ABORT 
by the user out of this will lead to a useless SYSTEM ....[/B][/COLOR]

THEN THE OPTION LEFT IS USUALLY A CLEAN INSTALL ......

---

### Post by vasa1 on 2011-10-12
I'm just wondering aloud from reading here and there ...

Download the .iso via torrent. Check md5.
Assuming the same computer is involved, mount the .iso instead of burning it to CD or USB. (I read that somewhere but can't find the link right away: something like ```
sudo mount -o loop /location_of/file.iso /media/cdrom
```).

Then, do the update pointing to the .iso.

I hope experts can flesh this out if it's workable.

My guess (totally uneducated) is that most of the time is due to downloading via the net for those of us with "substandard" net speeds and quality. A large part could be avoided by sourcing from the .iso.

Comments?

Ironically, power outages won't be an issue for me since I'm used to them and have a massive UPS/inverter on which my laptop will run for ages.

mounting .iso link: [https://help.ubuntu.com/community/NattyUpgrades#AlternateUpgrade](https://help.ubuntu.com/community/NattyUpgrades#AlternateUpgrade)

---

### Post by 23dornot23d on 2011-10-12
All sounds good in theory .... 

Easy is good ...... for the majority ...... me included .....

What you propose there is

1 ..... download the latest ISO

2 ..... mount it so it can be used to upgrade from

3 ..... upgrade from CD without a chance of losing it through a lost INTERNET connection

Sounds good to me ...... :)

---

### Post by vasa1 on 2011-10-12
> **23dornot23d said:**
> All sounds good in theory .... 

Easy is good ...... for the majority ...... me included .....

What you propose there is

1 ..... download the latest ISO

2 ..... mount it so it can be used to upgrade from

3 ..... upgrade from CD without a chance of losing it through a lost INTERNET connection

Sounds good to me ...... :)

But I'm sure there are a zillion little steps in between! Like will it be necessary to edit the sources list and replace natty with oneiric???

BTW, congrats on 2K beans!

---

### Post by CharlesA on 2011-10-12
Please don't derail threads.

---

