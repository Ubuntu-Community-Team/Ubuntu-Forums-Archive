---
title: "Codecs, Plugins etc."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by TheSeb on 2008-07-07
So I have been messing around with a lot of music/sound and video plugins and codecs on linux. (all of which come from googled advice) 

Problem is, there are so many choices and a lot of them are crap :(
A. Some don't work at all
B. Some work in half of situation
C. Some work but quality of sound or video or both (by comparison to my Mac) is terrible

I really wish for some linux pro to come see this thread and say:

"Here noobie, as of July 2008 these HERE are the best plugins and codecs for video and sound, go HERE to download them."

Is this possible, god I hope so. I can't take anymore of this :(:confused:

---

### Post by Rocket2DMn on 2008-07-07
See the Medibuntu repositories for w32codecs (or w64codecs) and libdvdcss2 among other packages - [uhelp]community/Medibuntu[/uhelp]

---

### Post by scragar on 2008-07-07
to be quite honest I use VLC for all my media options, except for realmedia, which plays quite well in Mplayer with a plugin+codec combo.

if you desperatly want to use totem(ubuntu default) might I recomend installing:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```which are the main codecs you will need(although not all).
you will also need **libdvdread3** for DVD playback and **liblame0** for MP3 playback.


all of these can be installed simply by installing the ubuntu-restricted-extras package though(go search synaptic or run```
sudo apt-get install ubuntu-restricted-extras
```)

---

### Post by Bubba64 on 2008-07-07
> **TheSeb said:**
> So I have been messing around with a lot of music/sound and video plugins and codecs on linux. (all of which come from googled advice) 

Problem is, there are so many choices and a lot of them are crap :(
A. Some don't work at all
B. Some work in half of situation
C. Some work but quality of sound or video or both (by comparison to my Mac) is terrible

I really wish for some linux pro to come see this thread and say:

"Here noobie, as of July 2008 these HERE are the best plugins and codecs for video and sound, go HERE to download them."

Is this possible, god I hope so. I can't take anymore of this :(:confused:

This link has helped many.
[http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive](http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive)

---

### Post by BGFG on 2008-07-07
My sound works great.
If you aren't comfortable with 'sudoing' just go 
applications>>add remove and in 'sound and video', find all the GStreamer packages. Choose the ones you need.

Hope you get your stuff working.

---

### Post by Bubba64 on 2008-07-07
> **BGFG said:**
> My sound works great.
If you aren't comfortable with 'sudoing' just go 
applications>>add remove and in 'sound and video', find all the GStreamer packages. Choose the ones you need.

Hope you get your stuff working.

Make sure you have all available packages. :)

---

### Post by sirgogo on 2008-07-07
Scragar was right.

Those are basically the core of sound/video/flash/other things.

---

### Post by Bubba64 on 2008-07-07
> **sirgogo said:**
> Scragar was right.

Those are basically the core of sound/video/flash/other things.

Yes he is correct another poster mentions the gstreamer extras and libraries in add remove these are very helpful as well for ffmpeg and other reading of media types.

---

### Post by Zebadim on 2008-07-07
Hi, I have tried to install medibuntu but I keep getting this error:

- Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--21:30:15--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Is there a quick fix? How can I uninstall this package?

Thanks in advance!
N.

---

### Post by Bubba64 on 2008-07-07
> **Zebadim said:**
> Hi, I have tried to install medibuntu but I keep getting this error:

- Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--21:30:15--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Is there a quick fix? How can I uninstall this package?

Thanks in advance!
N.

Paste  cat /etc/apt/sources.list in the terminal and look in the list to see whats there, I suspect you are not inputing the medibunti addition correctly.
here is a copy of my apt source list but notice it is Gutsy I am on my laptop.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main

---

### Post by Zebadim on 2008-07-07
Hi Bubba64,

Thanks a lot for your advice! You are probably right. However, given my newbie status how can I correct this. Here is the results from the cat command:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Thanks in advance,
N

---

### Post by Bubba64 on 2008-07-07
Here is a good link that explains the process, it doesn't look like any medibuntu is in the apt source list so you just have to add it.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
So you input the source for your ditribution Hardy in the terminal then at the bottom of the distribution lists is the gpg key add that next. :)

---

### Post by Zebadim on 2008-07-07
Hi,

I have tried but I am probably doing some very naive mistake and it keeps giving error messages. Can you tell me how I can revert the whole situation and, for the moment :-), forget about medibuntu? The problem is that, now, synaptic and add/remove software are always giving me error messages?

Thank is advance,
N

---

### Post by Bubba64 on 2008-07-07
> **Zebadim said:**
> Hi,

I have tried but I am probably doing some very naive mistake and it keeps giving error messages. Can you tell me how I can revert the whole situation and, for the moment :-), forget about medibuntu? The problem is that, now, synaptic and add/remove software are always giving me error messages?

Thank is advance,
N

I am far from geek status but I will try to help, is the error message telling you to run a particular message. post the error message.

---

### Post by Zebadim on 2008-07-07
Here it is:

nuno@nuno-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo-get update
[sudo] password for nuno: 
E: Type '--21:30:15--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
nuno@nuno-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -o /etc/apt/sorces.list.d/medibuntu.list
wget: /etc/apt/sorces.list.d/medibuntu.list: No such file or directory


... I started with the first command because yesterday I did the sequence requested but there was error when introducing it.

N

---

### Post by Zebadim on 2008-07-07
Ooops there was a syntax error. I corrected it the error messsage now is:

- nuno@nuno-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -o /etc/apt/sources.list.d/medibuntu.list
[sudo] password for nuno: 
nuno@nuno-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo-get update
E: Type '--09:57:50--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

N

---

### Post by Bubba64 on 2008-07-07
What happens when you just in the terminal paste sudo apt-get update let it run then sudo apt-get upgrade then accept any upgrades offered with a y for yes, if there are no upgrades it will just show the heading that is there when you open it.
 If you want the medibuntu paste this 1st, your trying to add the key ring 1st not last
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
Then, add the GPG Key:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.

---

### Post by Bubba64 on 2008-07-07
We are jumping back and forth from trying to install the medibuntu and your saying synaptic and add remove aren't working am I correct. lets focus on that first try and open synaptic and wait for the error message and post it.

---

### Post by Elfy on 2008-07-07
You're were looking at the wrong list to start with - the error is in the medibuntu one, I'd delete the offending file and add it again. I think the medibuntu commands would just tack it on the end of the existing medibuntu list - so you would still get the error

```
 sudo rm /etc/apt/sources.list.d/medibuntu.list
```

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

If you still get an error can you paste it please.

---

### Post by Bubba64 on 2008-07-07
> **forestpixie said:**
> You're were looking at the wrong list to start with - the error is in the medibuntu one, I'd delete the offending file and add it again. I think the medibuntu commands would just tack it on the end of the existing medibuntu list - so you would still get the error

```
 sudo rm /etc/apt/sources.list.d/medibuntu.list
```

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

If you still get an error can you paste it please.

Thanks for your help man I am not a geek and if I follow the instructions everything has worked for me, but I can't really deduce another persons problems all that well. :)

---

### Post by Elfy on 2008-07-07
> I am not a geekThat'll be 2 of us then :)

I only know what I know because it's happened to me at some point, or something similar - then I'm just left at the mercy of my memory.

> I thinkThe I might be wrong bit :)

---

### Post by Bubba64 on 2008-07-07
> **forestpixie said:**
> That'll be 2 of us then :)

I only know what I know because it's happened to me at some point, or something similar - then I'm just left at the mercy of my memory.

The I might be wrong bit :)

I can never remember how I fixed stuff early on, no short term memory, and for the life of me I can't recall officer what I was doing to cause this brain damage. :)

---

### Post by lemmy15 on 2008-07-12
> **scragar said:**
> to be quite honest I use VLC for all my media options, except for realmedia, which plays quite well in Mplayer with a plugin+codec combo.

if you desperatly want to use totem(ubuntu default) might I recomend installing:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```which are the main codecs you will need(although not all).
you will also need **libdvdread3** for DVD playback and **liblame0** for MP3 playback.


all of these can be installed simply by installing the ubuntu-restricted-extras package though(go search synaptic or run```
sudo apt-get install ubuntu-restricted-extras
```)

Hello to all...my first post here.

As a total beginner with ubuntu, this thing with codecs is driving me bonkers.  I have just followed the instructions (quoted) but still have trouble getting audio for video clips at [www.bloomberg.com](www.bloomberg.com)

Oddly enough, for some video clips at [www.bloomberg.com](www.bloomberg.com), the audio works just fine.

Any ideas?  Any more information I need to provide?  Thanks in advance.

---

