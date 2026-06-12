---
title: "[SOLVED] Ubuntu 8.10 Intrepid ibex- No sound from videos"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by jack_harper2007 on 2008-10-30
I just updated my version of Ubuntu to 8.10 and came across this problem:
when i tried to view videos from sites like youtube or yahoo the videos don't have any sound :(
I can hear the music and the videos that i have in my computer just fine i just can't hear anything from sites on the net :(
Of course that i have tried to solve this problems using the obvious ways, like increasing the volume (on the computer and on the player from the sites) and tried the changing the settings on ubuntu but still nothing...

I think this is a very strange problem.... can someone help me solve this? thanks in advance :)

---

### Post by pirattrev on 2008-10-30
go to your sound manager and change the 'sound playback' and device.  if it doesn't work on the first change, try again.  If no luck, consult another suggestion. This happened to me once and doing that fixed the problem [I'd had the playback set to the OSS system and instead it worked with ALSA].

---

### Post by ww711 on 2008-10-30
> **jack_harper2007 said:**
> I just updated my version of Ubuntu to 8.10 and came across this problem:
when i tried to view videos from sites like youtube or yahoo the videos don't have any sound :(
I can hear the music and the videos that i have in my computer just fine i just can't hear anything from sites on the net :(
Of course that i have tried to solve this problems using the obvious ways, like increasing the volume (on the computer and on the player from the sites) and tried the changing the settings on ubuntu but still nothing...

I think this is a very strange problem.... can someone help me solve this? thanks in advance :)

Same here, I have audio through CD and DVD playback. Only when I vist sites such as youtube or iplayer (bbc), the video streams fine, except for no audio. Flash 9 installed is on the system. I suspect a plug-in is missing, but which one?

---

### Post by spiderbatdad on 2008-10-30
maybe go through the preferences>>sound menu and set everything to autodetect, except the device...choose your sound device.

---

### Post by nynoah on 2008-10-30
I think has more to do with problems with Flash.  I have read some stuff a little while back that people were having problems with sound and Flash with Ibex.  I would do some searches for flash related issues on Ibex, you might get your help that way.

---

### Post by ww711 on 2008-10-30
Someone else suggested installing flash 10 via synaptic...audio works now.

---

### Post by jack_harper2007 on 2008-10-30
Ok problem solved just install adobe flash 10 from synaptic :)

Thanks everyone!!! :)

---

### Post by nynoah on 2008-10-30
any time there is a problem with sound that only effects a flash type issue, its going to be a flash issue.

---

### Post by jedimasterk on 2008-10-31
Same problem. Flash 10 installed no audio with youtube videos.

---

### Post by nynoah on 2008-10-31
reinstall flash and see if that solves it.  Otherwise do a search for "Flash 8.10" and see what you get.  Flash is just a crappy thing period.  Wish websites would not use it.

---

### Post by Absolom on 2008-10-31
I have no sound at all from anything including login or avi files on my comp or anything I've tried ... I tried to go through the preferences>>sound menu and set everything to autodetect but everything was already on autodetect... I tried everything I can think of.

---

### Post by fedemw on 2008-10-31
This solved my problem

[B]sudo apt-get install adobe-flashplugin
[/B]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following packages will be REMOVED
  flashplugin-nonfree
The following NEW packages will be installed
  adobe-flashplugin
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 3927kB of archives.
After this operation, 9933kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner adobe-flashplugin 10.0.12.36-1intrepid2 [3927kB]
Fetched 3927kB in 22s (176kB/s)                                                
(Reading database ... 118440 files and directories currently installed.)
Removing flashplugin-nonfree ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 118428 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_10.0.12.36-1intrepid2_i386.deb) ...
Setting up adobe-flashplugin (10.0.12.36-1intrepid2) ...


:popcorn:

---

### Post by glendavee on 2008-10-31
I'm having same problem, no sound on iplayer, in spite of the blurb on Ibex which says this problem has been fixed.
Tried apt-get as suggested by fedemw, and got following :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
david@david-desktop:~$ 

Where do I look for adobe-flashplugin?

---

### Post by sayems on 2008-10-31
I have found that this post in the Ubuntu forum most helpful. All of my sound issues went away.

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by glendavee on 2008-10-31
Tried that, didn't work. I've checked in synaptic, and flash 10 is installed. Worked all right in Heron.....

---

### Post by fedemw on 2008-10-31
> **glendavee said:**
> I'm having same problem, no sound on iplayer, in spite of the blurb on Ibex which says this problem has been fixed.
Tried apt-get as suggested by fedemw, and got following :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
david@david-desktop:~$ 

Where do I look for adobe-flashplugin?


I think you need other repositories at /etc/sources.list

Take a look of my list and feel free to use it:

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

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
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-security multiverse

## Medibuntu - Ubuntu 8.04 "hardy" 
## Please report any bug on https://bugs.launchpad.net/medibuntu/ 
# deb http://packages.medibuntu.org/ hardy free non-free

## UFO
# 2.2.1 # deb http://trylegaldownloads.de/ubuntu hardy games 
# deb http://trylegaldownloads.de/ubuntu hardy nightly-builds
```

---

### Post by distortedstar on 2008-11-01
Installing flashplugin-nonfree worked for me.

---

### Post by fujikofujio on 2008-11-07
Bloody hell!!! Just changed my video card and installed an ultra ata controller and now I don't get no sound from any website that uses flash. WTF ubuntu wtf!!!

None of the fixes mentioned here work so far, tried both adobe-flashplugin and the nonfree one with the extra sounds option.

Mplayer works though, login logout sounds plays too... arghh!

---

### Post by coldcoffee on 2008-11-12
Although this issue is marked as solved, I would like to mention the fact that if you run a java application in a browser no other sound will work. Not even a music cd. You must close out the browser and restart it to have sound from any other source or things such as Youtube. I have had this problem ever since I started using Ubuntu with Gutsy. Had it with Hardy and now with Intrepid. 

Not that I want sound from more than one source at a time, but this is an issue that I think is long overdue on getting fixed. I love Ubuntu and have no plans on changing to another OS, but is this an issue that will ever be resolved?

Edit: Also, if I play a video file or something else with sound, then open a browser to play a java based game there is no sound in the java based game.

I am sure this issue has probably been addressed. I would be really interested in seeing some articles related to this issue. And I am certainly more than willing to talk to anyone involved with Ubuntu in talking to them about this and explain more in detail the issues I have if they would like. Can someone point me to an article or thread or any information on this issue and if anything at all is being done. I certainly don't think this is something that they are not aware of or have no plans ever to iron out is it?

---

