---
title: "[SOLVED] no games in ultimate gamers edition"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by m3t3ors on 2008-05-16
ive just installed the nvidia driver for my graphics card and since i have i cant open any games. before the games were choppy but still opened?
all i know is its a geforce 128mb and works with suse 9.3 and 10.0 and mandriva 2008 powerpack fine and every other ubuntu ive used.i just cant seem to set it up
also my monitor is not listed
its a LG studioworks 700s
any help guys please

---

### Post by skymera on 2008-05-16
How did you install your drivers?

EnvyNG is awesome and included in the repos :)

```
 sudo apt-get install envyng-gtk 
```

---

### Post by m3t3ors on 2008-05-16
i installed it as root as it stated in another post on another website something like  "sh NVIDIA--------------pkg-run"
just ran the command you posted and get this error


john@john-desktop:~$ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk
john@john-desktop:~$

---

### Post by shifty_powers on 2008-05-16
try

sudo apt-get update

before you retry that command.

---

### Post by kaivalagi on 2008-05-16
> **skymera said:**
> How did you install your drivers?

EnvyNG is awesome and included in the repos :)

```
 sudo apt-get install envyng-gtk 
```

Envy is definitely the way to go...if the restricted drivers don't do it for you

---

### Post by m3t3ors on 2008-05-16
john@john-desktop:~$ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk
john@john-desktop:~
still getting the same error messgae

---

### Post by m3t3ors on 2008-05-16
got games to run but they are very choppy?

---

### Post by shifty_powers on 2008-05-16
[http://packages.ubuntu.com/hardy/envyng-gtk](http://packages.ubuntu.com/hardy/envyng-gtk)

from there you can grab the deb and all dependecnies.

tbh though all you need is the envyng-gtk deb, and double click on it. gdebi will resolve the depndencies.

---

### Post by kaivalagi on 2008-05-16
> **m3t3ors said:**
> john@john-desktop:~$ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk
john@john-desktop:~
still getting the same error messgae

Maybe you haven't got the universe repositories enabled?

If you haven't, you can add them in by running synaptic, clicking settings->repositories, then checking the appropriate checkbox (may want to check them all!)

Also, you'll need to run:

```
sudo apt-get update
```

to get an up-to-date list of available packages.

Hope that helps

---

### Post by null-cipher on 2008-05-16
I'm not sure if it would work in this case, but usually when I'm having Graphics problems, I run 
```
sudo dpkg-reconfigure xserver-xorg
```
Then just follow all the prompts.
Hope that helps.

---

### Post by m3t3ors on 2008-05-16
sudo apt-get update
just ran the command and all updates failed?

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gusty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gusty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gusty-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gusty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gusty-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gusty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
got envyng and installed it and ran it but still the graphics are choppy?

---

### Post by shifty_powers on 2008-05-16
might be silly question, but is your internet working properly from the ubuntu pc?

---

### Post by m3t3ors on 2008-05-16
> **shifty_powers said:**
> might be silly question, but is your internet working properly from the ubuntu pc?

yea using it to post replys and questions

---

### Post by shifty_powers on 2008-05-16
interesting.

could you post the contents of /etc/apt/sources.list?

---

### Post by m3t3ors on 2008-05-16
> **shifty_powers said:**
> interesting.

could you post the contents of /etc/apt/sources.list?

just get command not found

---

### Post by m3t3ors on 2008-05-16
> **null-cipher said:**
> I'm not sure if it would work in this case, but usually when I'm having Graphics problems, I run 
```
sudo dpkg-reconfigure xserver-xorg
```
Then just follow all the prompts.
Hope that helps.

just ran through the set up and still choppy graphics but thanx for advice

---

### Post by shifty_powers on 2008-05-16
heh sorry.

```
gksudo gedit /etc/apt/sources.list
```

and then copy and paste ;)

---

### Post by m3t3ors on 2008-05-16
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gusty-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gusty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gusty-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty all

---

### Post by shifty_powers on 2008-05-16
rofl.

hmm.

well thats a fairly normal sources list....

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe

# Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```

is mine.

so yours seems largely right, although i notce a number of "gusty" there ;)

try going into synaptic.

settings>repositories>

then where it says download from: click on it and choose something else than the us servers. (try the uk ones even ;))

then close and click on reload.

---

### Post by Therion on 2008-05-16
If you're using Ultimate Edition you might find more help on the [Ultimate Forums](http://forumubuntusoftware.info/index.php?sid=2703b84c1f148dfea3e9d626a4f8c5f5).  

Also, Ultimate v1.8 (32-bit) should be out any day now as well if you're interested.  The 64-bit version of Ultimate 1.8 has been out for a while but the 32-bit version is just now getting its finishing touches.

---

### Post by m3t3ors on 2008-05-16
all done but when it downloads the package information it seems to hang at 64 of the 96 packages and most of the 64 are failed?

---

### Post by kaivalagi on 2008-05-16
> **m3t3ors said:**
> all done but when it downloads the package information it seems to hang at 64 of the 96 packages and most of the 64 are failed?

Try commenting out the last entry: "deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gutsy all"
Not seen that repo before, may be bogus? Where did you get your sources.list from?

So you are running gutsy then (7.10)? I am not sure you'll find the envy package in the repo's... anyone know whether the legacy envy is in there? I'm running hardy and know nothing of Gutsy anymore! It never used to be there...

You can always download the legacy envy (for gutsy and before) from here: [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb")

Once downloaded, double click to kick off the install. Once installed run Envy and follow the instructions...you should soon have Nvidia drivers installed :)

Fingers crossed, good luck

---

### Post by m3t3ors on 2008-05-17
just did what kaivalagi suggested
but when i ran envyng i get an error and told i can veiw the log file
but i get command not found when i try to view the log file
found log file heres the result
python pulse.py nvidia 
root@john-desktop:/usr/share/envy# python pulse.py nvidia
EnvyNG - Version 1.0.1
EnvyNG ERROR: Your Operating System does not seem to be supported by Envy
also after reboot screen res is 800*600 and cant seem to change it

---

### Post by kaivalagi on 2008-05-17
> **m3t3ors said:**
> just did what kaivalagi suggested
but when i ran envyng i get an error and told i can veiw the log file
but i get command not found when i try to view the log file
found log file heres the result
python pulse.py nvidia 
root@john-desktop:/usr/share/envy# python pulse.py nvidia
EnvyNG - Version 1.0.1
**[COLOR="Red"]EnvyNG ERROR: Your Operating System does not seem to be supported[/COLOR]** by Envy
also after reboot screen res is 800*600 and cant seem to change it

You're trying to install EnvyNG, which is made for use with Ubuntu Hardy Heron (8.04) only! Try the legacy version which I linked to below. Or visit the website and see for yourself: [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

You need the Gutsy Gibbon (7.10) version I think...you're sources.list refers to gutsy rather than hardy :)

Legacy and NG compatibility from the envy site I linked to in this post:

**EnvyNG:**
Ubuntu Hardy Heron 8.04 - x86, x86_64

**Envy Legacy:**
**[COLOR="Green"]Ubuntu Gutsy Gibbon 7.10 - x86, x86_64[/COLOR]**
Ubuntu Feisty Fawn 7.04 - x86, x86_64 		
Linux Mint Daryna - x86, x86_64 		
Linux Mint Celena - x86, x86_64 		
Ubuntu Dapper Drake 6.06 - x86, x86_64 		
Ubuntu Edgy Eft 6.10 - x86, x86_64 		
Linux Mint Bianca - x86, x86_64 		
Linux Mint Cassandra - x86, x86_64 		
Debian Etch 4.0 * (read the Known Issues)

Hope that helps...

---

### Post by m3t3ors on 2008-05-18
just upgraded to 8-04? and ran envyng and GOT the graphics spot on (thanx to those who advised me on what to try) i appreciate the help guys
but on reboot i get a crash warning error
as follows
OAFIID:GNOME fast user switch applet
is this anything to worry about or important??

---

