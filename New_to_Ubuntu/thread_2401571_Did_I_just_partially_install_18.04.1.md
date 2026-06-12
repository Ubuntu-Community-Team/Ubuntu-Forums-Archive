---
title: "Did I just partially install 18.04.1?"
date: 2018-09-19
forum: New to Ubuntu
---

### Post by kate.t on 2018-09-19
Hello all!

I think I did something wrong when upgrading from ubuntu 16.04.5 to 18.04.1.

I patiently waited and watched while thousands of items scrolled by on the terminal. Finally I saw "Progress: 99%" and was excited. Shortly thereafter, I was presented with the question of whether or not I wanted to delete thousands of files no longer necessary. I was presented with three options: yes, no, and type "d" for details. A message on the terminal told me that the removal process could take hours.

Well, I wanted to know what all of this was about, so I chose "d" and a whole huge list of files and programs went zooming past on the terminal screen. At the end of the list, I was presented with a colon. I didn't know what to do with that. Hitting "enter" did nothing except bring up a small white box with the word "end" inside it. I had no idea how to get out of that list. So I thought I should try control-c to back out of that list.

I think that was the wrong move. It took me immediately to the prompt. At once I had a sinking feeling that I had cut off the end of the installation process before it finished. 

Now I appear to have 18.04.1 partially installed. When checking, I am told that I have 18.04.1 installed. However my initial screen remains exactly the same, with the same wallpaper and apparently the same Dash system. I'm not seeing the Gnome screen. Thank goodness Dash works, because when I wanted to find out what OS was installed, I could not bring up the terminal by using control-alt-T. I had to get it by using Dash.

My MS Office 2010 (which is necessary for work!) is doing just fine with Wine and PlayOnLinux. So far a lot of things are functional (well, pulseaudio won't start, but at the moment that's the least of my worries.

What do I do to fix this situation? Is there anything short of doing a clean install that I can do? The idea of having to set everything up after a clean installation makes me nauseous.

Thanks in advance for your advice!

Kathleen

---

### Post by Bashing-om on 2018-09-19
kate.t; Hello -

Show us the results - Between Code Tags - of terminal commands:
```

sudo apt autoclean
sudo apt autoremove
sudo apt clean
sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg --configure -a
sudo dpkg -C

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see what the package manager thinks .. and go from there .

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by kate.t on 2018-09-20
Hi Bashing-om!

Thanks for your suggestions. Here are the results:

```
sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-signed-image-generic 4.4.0.134.140 [2,536 B]
Del libswresample-ffmpeg1 7:2.8.15-0ubuntu0.16.04.1 [51.7 kB]
Del linux-generic 4.4.0.135.141 [1,792 B]
Del winbind 2:4.3.11+dfsg-0ubuntu0.16.04.16 [411 kB]
Del adobe-flash-properties-gtk 1:20180911.1-0ubuntu0.16.04.1 [143 kB]
Del linux-signed-image-generic 4.4.0.135.141 [2,438 B]
Del libavresample-ffmpeg2 7:2.8.15-0ubuntu0.16.04.1 [52.0 kB]
Del libswscale-ffmpeg3 7:2.8.15-0ubuntu0.16.04.1 [146 kB]
Del libdfu1 0.8.3-0ubuntu4 [48.3 kB]
Del fwupd 0.8.3-0ubuntu4 [120 kB]
Del linux-image-generic 4.4.0.134.140 [2,500 B]
Del samba-common 2:4.3.11+dfsg-0ubuntu0.16.04.16 [83.7 kB]
Del linux-headers-generic 4.4.0.135.141 [2,364 B]
Del linux-image-extra-4.4.0-135-generic 4.4.0-135.161 [36.5 MB]
Del xserver-xorg-core 2:1.18.4-0ubuntu0.8 [1,344 kB]
Del linux-headers-4.4.0-134 4.4.0-134.160 [10.0 MB]
Del xserver-common 2:1.18.4-0ubuntu0.8 [27.7 kB]
Del waterfox 56.2.3 [41.0 MB]
Del libpostproc-ffmpeg53 7:2.8.15-0ubuntu0.16.04.1 [48.9 kB]
Del linux-image-extra-4.4.0-134-generic 4.4.0-134.160 [36.5 MB]
Del initramfs-tools-bin 0.122ubuntu8.12 [9,726 B]
Del linux-headers-4.4.0-135-generic 4.4.0-135.161 [822 kB]
Del samba-common-bin 2:4.3.11+dfsg-0ubuntu0.16.04.16 [506 kB]
Del initramfs-tools 0.122ubuntu8.12 [8,628 B]
Del samba 2:4.3.11+dfsg-0ubuntu0.16.04.16 [907 kB]
Del google-chrome-stable 69.0.3497.100-1 [54.7 MB]
Del libavcodec-ffmpeg56 7:2.8.15-0ubuntu0.16.04.1 [4,087 kB]
Del linux-signed-image-4.4.0-134-generic 4.4.0-134.160 [4,014 B]
Del linux-headers-4.4.0-134-generic 4.4.0-134.160 [818 kB]
Del google-chrome-stable 69.0.3497.81-1 [54.7 MB]
Del samba-dsdb-modules 2:4.3.11+dfsg-0ubuntu0.16.04.16 [216 kB]
Del linux-headers-generic 4.4.0.134.140 [2,452 B]
Del libavutil-ffmpeg54 7:2.8.15-0ubuntu0.16.04.1 [166 kB]
Del anbox-modules-dkms 13~xenial1 [38.3 kB]
Del linux-signed-generic 4.4.0.135.141 [1,820 B]
Del libavfilter-ffmpeg5 7:2.8.15-0ubuntu0.16.04.1 [530 kB]
Del linux-signed-generic 4.4.0.134.140 [1,818 B]
Del linux-signed-image-4.4.0-135-generic 4.4.0-135.161 [4,028 B]
Del libfwupd1 0.8.3-0ubuntu4 [32.8 kB]
Del adobe-flashplugin 1:20180911.1-0ubuntu0.16.04.1 [9,769 kB]
Del linux-image-generic 4.4.0.135.141 [2,404 B]
Del linux-image-4.4.0-135-generic 4.4.0-135.161 [22.1 MB]
Del samba-vfs-modules 2:4.3.11+dfsg-0ubuntu0.16.04.16 [256 kB]
Del linux-generic 4.4.0.134.140 [1,790 B]
Del linux-headers-4.4.0-135 4.4.0-135.161 [10.0 MB]
Del libappstream-glib8 0.5.13-1ubuntu6 [101 kB]
Del libavformat-ffmpeg56 7:2.8.15-0ubuntu0.16.04.1 [810 kB]
Del libsmbclient 2:4.3.11+dfsg-0ubuntu0.16.04.16 [53.5 kB]
Del samba-libs 2:4.3.11+dfsg-0ubuntu0.16.04.16 [5,161 kB]
Del python-samba 2:4.3.11+dfsg-0ubuntu0.16.04.16 [1,061 kB]
Del linux-image-4.4.0-134-generic 4.4.0-134.160 [22.1 MB]
Del libwbclient0 2:4.3.11+dfsg-0ubuntu0.16.04.16 [30.2 kB]
Del linux-libc-dev 4.4.0-134.160 [867 kB]
Del python3-urllib3 1.13.1-2ubuntu0.16.04.2 [58.1 kB]
Del linux-libc-dev 4.4.0-135.161 [868 kB]
Del initramfs-tools-core 0.122ubuntu8.12 [44.9 kB]

```

```
sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

sudo apt clean brought up nothing; I just got the prompt again.

```
sudo apt update
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                  
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [139 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [31.4 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [56.9 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [166 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [171 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [280 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Get:13 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]   
Get:14 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:15 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [6,824 B]
Get:16 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,088 B]
Get:17 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [11.3 kB]
Fetched 1,125 kB in 3s (416 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons-small (partner/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons-small (partner/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4


```

```
 sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

```
sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

sudo dpkg --configure -a just brought up the prompt again.

And sudo dpkg -C also just brought up the prompt again.

Since I don't know what any of this really means, I am looking forward to your comments. I hope it's good news!

---

### Post by kate.t on 2018-09-20
Hello again, Bashing-om,

I just now installed Synaptic and I clicked on the button "Mark All Upgrades". The package manager thinks that there are no upgrades for me whatsoever.

I also restarted my laptop, and I still have the 16.04 desktop and Dash. Does this mean Unity is still installed?

---

### Post by Bashing-om on 2018-09-20
kate.t; Great !

looks to me like you have 18.04 fully installed. All I see to do presently is to fix that duplicate entry in the sources list files.
show us:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by kate.t on 2018-09-20
I'm glad it doesn't look tragic! 

Here are the results:

```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
     6    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
    11    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team, and may not be under a free licence. Please satisfy yourself as to
    15    ## your rights to use the software. Also, please note that software in
    16    ## universe WILL NOT receive any review or updates from the Ubuntu security
    17    ## team.
    18    deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
    19    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
    20    deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
    21    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
    29    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    30    deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
    31    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    32    
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
    39    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    deb http://archive.canonical.com/ubuntu bionic partner
    46    # deb-src http://archive.canonical.com/ubuntu xenial partner
    47    
    48    deb http://security.ubuntu.com/ubuntu bionic-security main restricted
    49    # deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    50    deb http://security.ubuntu.com/ubuntu bionic-security universe
    51    # deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    52    deb http://security.ubuntu.com/ubuntu bionic-security multiverse
    53    # deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    54    # deb https://dl.bintray.com/hawkeye116477/waterfox-deb release main # disabled on upgrade to bionic


```

```
 tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dropbox.list <==
# deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu wily main # disabled on upgrade to bionic

==> /etc/apt/sources.list.d/dropbox.list.distUpgrade <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu wily main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu wily main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to bionic

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google.list <==
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to bionic

==> /etc/apt/sources.list.d/google.list.distUpgrade <==
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google.list.save <==
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/morphis-ubuntu-anbox-support-xenial.list <==
# deb http://ppa.launchpad.net/morphis/anbox-support/ubuntu bionic main # disabled on upgrade to bionic
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main

==> /etc/apt/sources.list.d/morphis-ubuntu-anbox-support-xenial.list.distUpgrade <==
deb http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main

==> /etc/apt/sources.list.d/morphis-ubuntu-anbox-support-xenial.list.save <==
deb http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main
# deb-src http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial main

==> /etc/apt/sources.list.d/softmaker.list <==
#SoftMaker Office repository
# deb http://shop.softmaker.com/repo/apt wheezy non-free # disabled on upgrade to bionic

==> /etc/apt/sources.list.d/softmaker.list.distUpgrade <==
#SoftMaker Office repository
deb http://shop.softmaker.com/repo/apt wheezy non-free

==> /etc/apt/sources.list.d/xenial-partner.list <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb http://archive.canonical.com/ubuntu bionic partner

==> /etc/apt/sources.list.d/xenial-partner.list.distUpgrade <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb http://archive.canonical.com/ubuntu xenial partner

==> /etc/apt/sources.list.d/xenial-partner.list.save <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb http://archive.canonical.com/ubuntu xenial partner


```

Hope this helps!

---

### Post by Impavidus on 2018-09-20
> **kate.t said:**
> 
Well, I wanted to know what all of this was about, so I chose "d" and a whole huge list of files and programs went zooming past on the terminal screen. At the end of the list, I was presented with a colon. I didn't know what to do with that. Hitting "enter" did nothing except bring up a small white box with the word "end" inside it. I had no idea how to get out of that list. So I thought I should try control-c to back out of that list.

You saw the **less** program, which is a very basic program to show text in a terminal. You can use the arrow keys to scroll. Next time you see this, hit q to quit.

---

### Post by kate.t on 2018-09-20
Impavidus, hi!

Thanks for that info! Now I'm prepared should I ever come across that situation again.

You can see how much of a newbie I am. Although I must say I'm eager to learn. Generous regular posters like you are a big help in that process!

---

### Post by Bashing-om on 2018-09-20
kate.t; Hey :)

> **kate.t said:**
> Impavidus, hi!

Thanks for that info! Now I'm prepared should I ever come across that situation again.

You can see how much of a newbie I am. Although I must say I'm eager to learn. Generous regular posters like you are a big help in that process!

Help is what we do . We do understand newness - we were all new at one time .

In your present circumstances remove the source duplication:
```

sudo rm -rf /etc/apt/sources.list.d/xenial-partner.list

```

and I note that google Chrome is disabled; Do you use or intend to use that proprietary browser ?

That done, is the system stable and functional in all respects ?

[INDENT][INDENT]'buntu - workie great, last long time
[/INDENT][/INDENT]

---

### Post by kate.t on 2018-09-20
Hi Bashing-om!

It's odd that you say that Chrome is disabled; I've been using it all day. I use it for my job and need it.

No, things are not stable and functional. I keep discovering new things, although I can't tell what's from a screwed-up installation and what's from 18.04.1 being different and/or quirky.

One thing I really, really need is the ability to shift to a different keyboard layout. I'm a translator of German to English and I work from home on this laptop, constantly switching languages all day long. Until the (partial) upgrade, I was able to switch back and forth using the Windows key and space bar. And according to the "new" settings, I should still be able to do that. However, it's not working. I've had to go to the German Wikipedia website to copy and paste umlauted vowels, etc. This cannot stand! Help!

I also want to know WHY I still have a Unity desktop, although I must admit, at this point I'm scared to lose whatever functionality I have. There are other problems I'm having, but I don't want to overwhelm you all at once. ;)

---

### Post by Bashing-om on 2018-09-20
kate.t; then just yukkie for overall:(

Then ya want to enable the Google Chrome sources.list.d file:
> 
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main # disabled on upgrade to bionic

remove the '#' character at the start of the deb line. Might be prudent to also remove the comment " # disabled on upgrade to bionic " .
then update the system:
```

sudo apt update
sudo apt upgrade

```

As to desktop settings .. I have run xfce for several years now and not familiar now with any other desktop (as I just did not like unity). However, we can flounder along and see what we can work out.

What desktop do you prefer to use ?
Show us what is presently installed:
```

ls -al /usr/share/xsessions

```

we get the desktop configured, maybe the language switching will follow ?


[INDENT][INDENT]got our work cut out for us, huh ?
[/INDENT][/INDENT]

---

### Post by kate.t on 2018-09-20
Well, that's interesting.

I went into the Google Chrome file, and both things you wanted me to do are already done. ??? Somebody sneaked in and fixed that file while I was powdering my nose?

As to which desktop is installed, you'll have to tell me, since I don't know what this means:

```
ls -al /usr/share/xsessions
total 28
drwxr-xr-x   2 root root  4096 Sep 19 13:31 .
drwxr-xr-x 302 root root 12288 Sep 19 22:33 ..
-rw-r--r--   1 root root   323 May  2 00:40 ubuntu-communitheme-snap.desktop
-rw-r--r--   1 root root   247 May  2 00:40 ubuntu.desktop
-rw-r--r--   1 root root   243 May  2 00:40 unity.desktop


```

Once again, thank you!

---

### Post by kate.t on 2018-09-20
Oh, and I forgot to mention:

It's hard to know which desktop I prefer, since I've only ever used Unity. I've noticed that lots of people seem to really like Gnome and dislike Unity, so I thought I should at least try it out. It's my understanding that it's possible to restore the Unity desktop from within 18.04 if I want to have it back again later.

---

### Post by Bashing-om on 2018-09-20
kate.t; Well ,,, well 

That do say that unity is still installed .. and I can hazard a guess that the system is confused as to which components of which desktop environment to use.

Ubuntu-desktop is a meta-package in ubuntu that connects all the packages that are installed by default in a fresh ubuntu install.
18.04 has 2 environments installed by default: Xorg ( running under GDM3), and Wayland (running under Mir).
Which are you presently using ?
show us:
```

cat /etc/X11/default-display-manager
systemctl status gdm
systemctl status lightdm
echo $XDG_SESSION_TYPE
loginctl show-session c1 -p Type

```
- 'q'  to 'quit' from the systemctl display
see what we can do to re-configure. Do you want to keep unity, ? The default now is GDM3.

[INDENT]OH boy - not
[/INDENT]

---

### Post by kate.t on 2018-09-20
Here goes:

```
cat /etc/X11/default-display-manager
/usr/sbin/lightdm


```

```
gdm.service - GNOME Display Manager
   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabl
   Active: inactive (dead)


```

```
lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; indirect; vendor preset:
  Drop-In: /lib/systemd/system/display-manager.service.d
           &#9492;&#9472;xdiagnose.conf
   Active: active (running) since Thu 2018-09-20 15:08:42 MST; 1h 59min ago
     Docs: man:lightdm(1)
  Process: 1129 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-dis
 Main PID: 1132 (lightdm)
    Tasks: 5 (limit: 4915)
   CGroup: /system.slice/lightdm.service
           &#9500;&#9472;1132 /usr/sbin/lightdm
           &#9492;&#9472;1158 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm

Sep 20 15:08:42 kathleen-Lenovo-G50-70 systemd[1]: Starting Light Display Manage
Sep 20 15:08:42 kathleen-Lenovo-G50-70 systemd[1]: Started Light Display Manager
Sep 20 15:08:46 kathleen-Lenovo-G50-70 lightdm[1222]: pam_unix(lightdm-autologin
lines 1-16/16 (END)


```

```
echo $XDG_SESSION_TYPE
x11


```

```
loginctl show-session c1 -p Type
Type=x11


```

---

### Post by Bashing-om on 2018-09-20
kate.t; Ho kay .. 

running ubuntu under Xorg :) //

Let's remove unity from the equation, and make sure the ubuntu-desktop is fully installed.
reboot, and at the login screen execute ctl+alt+F2 to activate a console interface. Log into the system with username and password ( no reponse to the screen when password is entered)

now purge unity:
```

sudo apt purge unity-session unity
sudo apt autoremove

```

Now make sure that any pieces that Xorg needs are put back:
```

sudo apt install ubuntu-session gdm3

```

reboot to see the effect .. at the password screen -> gear icon at the lower right is a drop down - choose ubuntu-Xorg.

All better now ? 

[INDENT][INDENT]still with work to do ?
[/INDENT][/INDENT]

---

### Post by kate.t on 2018-09-20
Well, that was interesting.

First of all, when I first installed 16.04, I got rid of the login screen, so it doesn't show up when I reboot. I also couldn't figure out where the setting was to switch back. So I rebooted and then immediately logged out, using the gear wheel at the top right (16.04). 

I then saw a login screen with a bionic beaver on it. However, there was no gear icon at the lower right, no drop-down. 

I logged in anyway, as there was nothing else to do. I was surprised to see my wallpaper still there, but all sorts of other things changed in terms of where the icons are. I also have the lower left hand icon to show applications. It appears that I am in Gnome!

Is there another way to choose ubuntu-Xorg?

Good news! My keyboard shortcut to switch languages is working fine. Yay!

I'm going to poke around to see if everything is still here. 

Is there anything else I should be doing? Thanks!

---

### Post by Bashing-om on 2018-09-20
kate.t; Hey progress made !

I do not have a GDM3 install of 18.04 so can not compare. My choice of the DE remains as xfce4.

> 
Is there another way to choose ubuntu-Xorg?

Bet you are in Xorg now - the default boot.
```

echo $XDG_SESSION_TYPE

```
will show " x11 ". which is the Xorg environment

> 
Is there anything else I should be doing? Thanks!

Nope, just what you are doing .. play around and read the helps ... Gnome is different ( and better ) .. I must say I did play with it ... and then with the Wayland environment - I found the Wayland desktop smoother and faster - in my use case. But after all said and done I did return to the devil I know .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

