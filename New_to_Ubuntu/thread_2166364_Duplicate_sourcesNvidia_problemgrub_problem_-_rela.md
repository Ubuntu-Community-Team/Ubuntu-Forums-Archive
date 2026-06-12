---
title: "Duplicate sources/Nvidia problem/grub problem - related?"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by Crossbow on 2013-08-08
For montns I've been getting this error when I run apt-get update. I've tried searching it and mainly found that it shouldn't be a problem. I'mnot so sure, though, because I have no idea what it is. Going to /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_binary-i386_Packages did not avail me anything - I didn't see anything duplicated, and if I did I would be afraid to mess with it anyway. :confused: 

```
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

I have no idea if this could be related to my ongoing Nvidia problem, which is that if I try to change to any NVIDIA above 173 I lose my GUI completely. (The Nvidia website said I should be using 310.) Yes, I have searched that. I must have read a dozen threads on it and tried uninstalling and reinstalling several versions of Nvidia while trying to get World of Warcraft to play. (I finally gave up on that and cancelled my account.) 

The GUI problem is probably related to the grub problem I haven't figured out. All the advice I can find regarding *that* is that I'm supposed to add "quiet splash" somewhere, but the line I'm supposed to add it too doesn't look like any of the examples. Yes, there are several threads on that. No, they have not helped because I don't seem to have the lines that I'm supposed to change. 

Here's a photo, from a few weeks ago, but it's pretty much looked like this for the last two distros: 
[http://img.photobucket.com/albums/v97/Crossbow/grub_zps5133df0b.jpg](http://img.photobucket.com/albums/v97/Crossbow/grub_zps5133df0b.jpg)

Ubuntu 13.04 (raring)
Kernel 3.8.0-27-generic
Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz

---

### Post by oldfred on 2013-08-09
I do not think sources list is related to nVidia unless perhaps you had used one of the ppas to add custom nVidia drivers.

Did you run the suggested?
sudo apt-get update

I might run the set of updates, just to make sure everything is current.
       #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

Installing many copies or versions of nVidia can create confusion. Generally best to know which video card you have and whether is uses one of the legacy drivers or the newer ones. Then just install from the repository the version you prefer. I tend to install the most current even though my card is older. Only a few with very new nVidia cards that have not made a new drive into the repository may need to use a ppa or directly download from nVidia.

---

### Post by Crossbow on 2013-08-10
Running sudo update is what get me the error in the first place. I will try the ones you suggest.

ETA: Ran all those commands. No change. Same error. 

Also, I see that I don't have the "additional drivers" option in my settings even though the software center tells me it is installed. What's that about?

---

### Post by Bashing-om on 2013-08-10
Crossbow; Hi !

Regretful that you are having such problems.
Forum policy - keeps things organized - one problem to the thread ... open as many threads as needed. 
Here I will address the duplication issue only as other issues are not related.
To that end, post the output of terminal commands:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/

```

Additional advise pending.
[INDENT][INDENT]where there are solutions there are no problems[/INDENT][/INDENT]

---

### Post by grahammechanical on 2013-08-10
Hi

First you will not find an Additional Driver utility in System Settings (in 13.04) but try opening Software and Updates which is in system Settings and then opening the Additional Drivers tab. Allow time for the utility to search for drivers.

As regards Grub you have entered Grub edit mode and you need to scroll down to see all the lines of parameters. Look at the bottom of the box and just outside the bottom right corner is an arrow pointing downward. That means there is more to see. And you should see something like

> fi
linux  /boot/vmlinuz-3.8.0-26-generic root=UUID= lots of numbers and letters ro vt_handoff.

it should look like

> ro quite splash vt_handoff

That will remove all those boot messages that you are seeing. I think that will only work for that one boot session. To make it permanant you will have to edit some Grub configuration files. 

Regards.

---

### Post by Crossbow on 2013-08-11
> **Bashing-om said:**
> Crossbow; Hi !

Regretful that you are having such problems.
Forum policy - keeps things organized - one problem to the thread ... open as many threads as needed. 
Here I will address the duplication issue only as other issues are not related.
To that end, post the output of terminal commands:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/

```

Additional advise pending.
[INDENT][INDENT]where there are solutions there are no problems[/INDENT][/INDENT]

Sorry, I know you're not supposed to put multiple issues in a thread but I have no idea if the issues could be connected. For all  I know it's the same issue!

I currently am not able to log in but I will try that as soon as I can.

---

### Post by Bashing-om on 2013-08-11
Crossbow; Hey .. good to hear from ya.
A sources.list is a source.list .. so yes .. the result will be relevant if you post the results from the guest account....
I expect that resolving this issue to be straight forward ...

For my future reference .. you can not now boot into the 1st user account ?

Remains to be seen.

[INDENT][INDENT]noth'n but a thing
[/INDENT][/INDENT]

---

### Post by Crossbow on 2013-08-11
> **Bashing-om said:**
> Crossbow; Hey .. good to hear from ya.
A sources.list is a source.list .. so yes .. the result will be relevant if you post the results from the guest account....
I expect that resolving this issue to be straight forward ...

For my future reference .. you can not now boot into the 1st user account ?

Remains to be seen.

[INDENT][INDENT]noth'n but a thing
[/INDENT][/INDENT]

No I can't. I seem to have somehow deleted something when I was purging Wine. I have a thread for that here: [http://ubuntuforums.org/showthread.php?t=2166865]("http://ubuntuforums.org/showthread.php?t=2166865") The "login loop" seems to be common problem but none of the recommended fixes have worked. I think there is a missing piece I need to install but I don't know what. 
 

Here are the results. Am I supposed to have all that stuff from previoius distros in there? If not, how do I get rid of them? 

```

guest-ZEsY44@anna-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ raring-security universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-security multiverse
# deb-src http://archive.ubuntu.com/ubuntu raring main
# deb-src http://archive.ubuntu.com/ubuntu raring main
# deb-src http://archive.canonical.com/ubuntu raring partner
deb http://us.archive.ubuntu.com/ubuntu/ raring restricted
# deb-src http://archive.ubuntu.com/ubuntu/ raring main restricted
guest-ZEsY44@anna-desktop:~$ ls -la /etc/apt/sources.list.d/
total 176
drwxr-xr-x 2 root root 4096 Aug 11 08:49 .
drwxr-xr-x 6 root root 4096 Aug  8 21:22 ..
-rw-r--r-- 1 root root  138 Aug 11 09:26 bumblebee-stable-raring.list
-rw-r--r-- 1 root root  138 Aug 11 09:26 bumblebee-stable-raring.list.save
-rw-r--r-- 1 root root   80 Aug 11 09:26 dropbox.list
-rw-r--r-- 1 root root   80 Jun  9 16:50 dropbox.list.distUpgrade
-rw-r--r-- 1 root root   80 Aug 11 09:26 dropbox.list.save
-rw-r--r-- 1 root root  112 Aug 11 09:26 firefox-stable.list
-rw-r--r-- 1 root root  112 Jun  9 16:50 firefox-stable.list.distUpgrade
-rw-r--r-- 1 root root  112 Aug 11 09:26 firefox-stable.list.save
-rw-r--r-- 1 root root  176 Jun  9 16:50 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 Aug 10 12:04 google-chrome.list.save
-rw-r--r-- 1 root root  176 Aug 11 09:26 karmic-partner.list
-rw-r--r-- 1 root root  175 Jun  9 16:50 karmic-partner.list.distUpgrade
-rw-r--r-- 1 root root  176 Aug 11 09:26 karmic-partner.list.save
-rw-r--r-- 1 root root  176 Aug 11 09:26 lucid-partner.list
-rw-r--r-- 1 root root  176 Jun  9 16:50 lucid-partner.list.distUpgrade
-rw-r--r-- 1 root root  176 Aug 11 09:26 lucid-partner.list.save
-rw-r--r-- 1 root root  306 Aug 11 09:26 medibuntu.list
-rw-r--r-- 1 root root  306 Jun  9 16:50 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root  306 Aug 11 09:26 medibuntu.list.save
-rw-r--r-- 1 root root   80 Aug 11 09:26 playonlinux.list
-rw-r--r-- 1 root root   80 Jun  9 16:50 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root   80 Aug 11 09:26 playonlinux.list.save
-rw-r--r-- 1 root root  204 Aug 11 09:26 ubuntu-wine-ppa-natty.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root  204 Aug 11 09:26 ubuntu-wine-ppa-natty.list.save
-rw-r--r-- 1 root root  204 Aug 11 09:26 ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  204 Aug 11 09:26 ubuntu-wine-ppa-oneiric.list.save
-rw-r--r-- 1 root root  204 Aug 11 09:26 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  204 Aug 11 09:26 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root  220 Aug 11 09:26 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  220 Jun  9 16:50 ubuntu-x-swat-x-updates-precise.list.distUpgrade
-rw-r--r-- 1 root root  220 Aug 11 09:26 ubuntu-x-swat-x-updates-precise.list.save
-rw-r--r-- 1 root root  200 Aug 11 09:26 xorg-edgers-ppa-quantal.list
-rw-r--r-- 1 root root  134 Jun  9 16:50 xorg-edgers-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root  200 Aug 11 09:26 xorg-edgers-ppa-quantal.list.save
-rw-r--r-- 1 root root   68 Aug 11 09:26 xorg-edgers-ppa-raring.list
-rw-r--r-- 1 root root   70 Aug 11 09:26 xorg-edgers-ppa-raring.list.save
-rw-r--r-- 1 root root  214 Aug 11 09:26 yannubuntu-boot-repair-quantal.list
-rw-r--r-- 1 root root  148 Jun  9 16:50 yannubuntu-boot-repair-quantal.list.distUpgrade
-rw-r--r-- 1 root root  214 Aug 11 09:26 yannubuntu-boot-repair-quantal.list.save
guest-ZEsY44@anna-desktop:~$ 

```

---

### Post by oldfred on 2013-08-11
Everything looks like it is raring or commented out except this line in sources.

 > deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

I do not think you should have any of the old stuff. I think this is part of why I usually suggest clean installs as then things are automatically housecleaned. 
As with any editing of files, you need to have a good backup as if you accidentally delete something you should not then you create even bigger issues.

You can do this if you want to use gui, but with sudo you have to be extremely careful to not delete anything that system does need.
gksu nautilus

---

### Post by Bashing-om on 2013-08-12
Crossbow:

+1 on oldfred's observation/advise ... I see in that entry the term "precise" should be changed to "raring" ... and I would strongly advise us to look at those "partner" entries in the "sources.list.d" directory and probably delete them as well. -the source of the duplication error ?-
And, what in the world is "karmic-partner.list.distUpgrade" still hanging about for ?
let us see:
```

cat /etc/sources.list.d/karmic-partner.list
cat /etc/sources.list.d/karmic-partner.list.distUpgrade

```
Should we not consider removing those obsolete entries and update "Wine" and "x-swat" ??

[INDENT][INDENT]will cross the next bridge when we get to it[/INDENT][/INDENT]

---

### Post by Crossbow on 2013-08-13
I don't really know where to change those. In the repositories, they're all listed but not checked. 

Before I do a clean install, I need to really clean out Dropbox so I can back up what I really want to save. I have automated backup set up but it's been full for a while. Because, as I said, I'm an idiot. 

```
ro quite splash vt_handoff 
```

Well, I've got the pretty startup page now, which is progress, I suppose.

---

### Post by Bashing-om on 2013-08-13
Crossbow; Hey ...

Do I understand correctly that you are not able to boot to the desktop ?
Do this and advise on what results:
 A graphics driver problem is a reasonable assumption.

Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Version 13.04  --12.04 locations differ->Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

And remaining yet to do -> software sources and 3rd party sources.

[INDENT][INDENT]lesson: be kind to your ubuntu
[/INDENT][/INDENT]

---

### Post by Crossbow on 2013-08-13
> **Bashing-om said:**
> Crossbow; Hey ...

Do I understand correctly that you are not able to boot to the desktop ?
Do this and advise on what results:
 A graphics driver problem is a reasonable assumption.

Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Version 13.04  --12.04 locations differ->Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

And remaining yet to do -> software sources and 3rd party sources.

[INDENT][INDENT]lesson: be kind to your ubuntu
[/INDENT][/INDENT]

- I am not able to boot to the desktop except as "Guest." I started a separate thread for that [here,]("http://ubuntuforums.org/showthread.php?t=2166865") as that problem came later. 
- Actually it always goes to the grub menu after BIOS. I have no idea what I did to make that happen but I'm OK with it since I've been spending so much time in recovery mode. 
- So would that be "quiet splash nomodeset"?

Thanks!

---

### Post by Bashing-om on 2013-08-13
Crossbow; Yeah,

If you insert that term "nomodeset" that disables Kernel Mode Setting to force the use of a base graphics driver. You should at that point be able to access the GUI under degraded graphics state and see what "additional drivers" has to say.  "So would that be "quiet splash nomodeset"?" yep that will do it.
On your other thread .. I have responded there also... 
Several problems but all small ones, should be able to work through them and get ya back in shape.

[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT]

---

### Post by Crossbow on 2013-08-24
So I tried removing all the old stuff from the repositories in Synaptic and I guess it worked. 

```
anna@anna-desktop:~$ sudo cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner

deb http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ raring-security universe
# deb-src http://archive.ubuntu.com/ubuntu raring main
# deb-src http://archive.ubuntu.com/ubuntu raring main
deb http://us.archive.ubuntu.com/ubuntu/ raring restricted
# deb-src http://archive.ubuntu.com/ubuntu/ raring main restricted
anna@anna-desktop:~$ 

```

But when I update I still get the exact same duplicate message. I may have removed too many. I don't know. I don't even know if that was the way to do it. I see something from Precise is still in there.

---

### Post by Bashing-om on 2013-08-24
Crossbow; Hey ...

I did not see any duplications  within that file .. another "directory" to be examined is "/etc/apt/sources.list.d"
```

 ls -la /etc/apt/sources.list.d

```
Post that output back for further advise.

And yes on the "precise"; in the text editor change "percise" to "raring" :
I hope you made a backup of the sources.list file before you made the other changes.
```

gksudo gedit /etc/apt/sources.list

```

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-08-24
Everything is raring except this line which is still there.

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

---

### Post by Crossbow on 2013-08-24
OK, I got the precise changed to raring. No, I didn't make a backup. I thought since I have this thread bookmarked I would be able to just copy 'em from when I posted them earlier. No? 

Here are the results from that last one:

```

anna@anna-desktop:~$ sudo ls -la /etc/apt/sources.list.d
[sudo] password for anna: 
total 112
drwxr-xr-x 2 root root 4096 Aug 24 15:59 .
drwxr-xr-x 6 root root 4096 Aug 17 21:00 ..
-rw-r--r-- 1 root root    0 Aug 24 16:01 bumblebee-stable-raring.list
-rw-r--r-- 1 root root    0 Aug 24 16:01 bumblebee-stable-raring.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 dropbox.list
-rw-r--r-- 1 root root   80 Jun  9 16:50 dropbox.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 dropbox.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 firefox-stable.list
-rw-r--r-- 1 root root  112 Jun  9 16:50 firefox-stable.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 firefox-stable.list.save
-rw-r--r-- 1 root root   67 Aug 24 18:31 gnome3-team-gnome3-raring.list
-rw-r--r-- 1 root root   67 Aug 24 18:31 gnome3-team-gnome3-raring.list.save
-rw-r--r-- 1 root root  176 Jun  9 16:50 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 Aug 10 12:04 google-chrome.list.save
-rw-r--r-- 1 root root  119 Aug 24 18:31 karmic-partner.list
-rw-r--r-- 1 root root  175 Jun  9 16:50 karmic-partner.list.distUpgrade
-rw-r--r-- 1 root root  119 Aug 24 18:31 karmic-partner.list.save
-rw-r--r-- 1 root root  118 Aug 24 18:31 lucid-partner.list
-rw-r--r-- 1 root root  176 Jun  9 16:50 lucid-partner.list.distUpgrade
-rw-r--r-- 1 root root  118 Aug 24 18:31 lucid-partner.list.save
-rw-r--r-- 1 root root   66 Aug 24 18:31 medibuntu.list
-rw-r--r-- 1 root root  306 Jun  9 16:50 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root   66 Aug 24 18:31 medibuntu.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:02 playonlinux.list
-rw-r--r-- 1 root root   80 Jun  9 16:50 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:02 playonlinux.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-natty.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-natty.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-oneiric.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  220 Jun  9 16:50 ubuntu-x-swat-x-updates-precise.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-x-swat-x-updates-precise.list.save
-rw-r--r-- 1 root root   72 Aug 24 18:31 ubuntu-x-swat-x-updates-raring.list
-rw-r--r-- 1 root root   72 Aug 24 18:31 ubuntu-x-swat-x-updates-raring.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 xorg-edgers-ppa-quantal.list
-rw-r--r-- 1 root root  134 Jun  9 16:50 xorg-edgers-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 xorg-edgers-ppa-quantal.list.save
-rw-r--r-- 1 root root   68 Aug 24 18:31 xorg-edgers-ppa-raring.list
-rw-r--r-- 1 root root   70 Aug 24 18:31 xorg-edgers-ppa-raring.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:00 yannubuntu-boot-repair-quantal.list
-rw-r--r-- 1 root root  148 Jun  9 16:50 yannubuntu-boot-repair-quantal.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:00 yannubuntu-boot-repair-quantal.list.save
anna@anna-desktop:~$ 
```

---

### Post by Bashing-om on 2013-08-25
Crossbow; Hey ..

somewhat limited as I have no experience with "Wine" .. but this for sure .. those old PPAs need to be removed !
```

sudo rm /etc/apt/sources.list.d karmic-partner.list

``` as one instance .. remove all of them in the same manner.

Now I do not know what would result in this instance:
> 
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-wine-ppa-precise.list
 by editing "precise" to "raring"
Nor, do I know the function of:
> 
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-precise.list.distUpgrade

I would suggest though, at the least, to remove all other instances of the related PPAs

then run:
```

sudo apt-get update
sudo apt-get upgrade

```
seeing what the status is now ...

[INDENT][INDENT]try try again[/INDENT][/INDENT]

---

### Post by oldfred on 2013-08-25
I do not have bumblebee nor dropbox, but do have chrome, Firefox, and wine installed from repository. 
I stopped using medibutu several versions ago when Ubuntu offered the extras on install.
This is from my clean install of 12.04.

This is all I have.

```
fred@fred-Precise:~$ sudo ls -la /etc/apt/sources.list.d
[sudo] password for fred: 
total 16
drwxr-xr-x 2 root root 4096 Oct  1  2012 .
drwxr-xr-x 6 root root 4096 Jul 19 22:44 ..
-rw-r--r-- 1 root root  148 Jul 19 23:15 yannubuntu-boot-repair-precise.list
-rw-r--r-- 1 root root  148 Jul 19 23:15 yannubuntu-boot-repair-precise.list.save

```

---

### Post by Jonathan Precise on 2013-08-25
Hello!

Try adding this to your software-sources:

```
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu ***YOUR_CODENAME_HERE*** main
```

If you are using ubuntu 13.04, use raring instead of "your_codename_here".

Then run:

```
sudo apt-get update
sudo apt-get install grub-customizer
```

This will install grub-customizer.

Run it by typing:

```
sudo grub-customizer
```

Then in the "general settings" tab, in 'kernel parameters', make sure you have "quiet splash" (without quotes) in there. Make sure "Generate recovery entries" is checked. Save, then exit.

That should fix grub.

---

### Post by Crossbow on 2013-08-31
> **Jonathan Precise said:**
> Hello!

```
sudo grub-customizer
```

Then in the "general settings" tab, in 'kernel parameters', make sure you have "quiet splash" (without quotes) in there. Make sure "Generate recovery entries" is checked. Save, then exit.

That should fix grub.

OK, it says: 

```
mode=1 #=1 splash quiet normal=1
```

Is that correct?

---

### Post by Crossbow on 2013-08-31
Well, I changed normal to nomodeset. That fixed my login problem. Still have that same "duplicate" issue.

---

### Post by Jonathan Precise on 2013-08-31
> **Crossbow said:**
> OK, I got the precise changed to raring. No, I didn't make a backup. I thought since I have this thread bookmarked I would be able to just copy 'em from when I posted them earlier. No? 

Here are the results from that last one:

```

anna@anna-desktop:~$ sudo ls -la /etc/apt/sources.list.d
[sudo] password for anna: 
total 112
drwxr-xr-x 2 root root 4096 Aug 24 15:59 .
drwxr-xr-x 6 root root 4096 Aug 17 21:00 ..
-rw-r--r-- 1 root root    0 Aug 24 16:01 bumblebee-stable-raring.list
-rw-r--r-- 1 root root    0 Aug 24 16:01 bumblebee-stable-raring.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 dropbox.list
-rw-r--r-- 1 root root   80 Jun  9 16:50 dropbox.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 dropbox.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 firefox-stable.list
-rw-r--r-- 1 root root  112 Jun  9 16:50 firefox-stable.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 firefox-stable.list.save
-rw-r--r-- 1 root root   67 Aug 24 18:31 gnome3-team-gnome3-raring.list
-rw-r--r-- 1 root root   67 Aug 24 18:31 gnome3-team-gnome3-raring.list.save
-rw-r--r-- 1 root root  176 Jun  9 16:50 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 Aug 10 12:04 google-chrome.list.save
-rw-r--r-- 1 root root  119 Aug 24 18:31 karmic-partner.list
-rw-r--r-- 1 root root  175 Jun  9 16:50 karmic-partner.list.distUpgrade
-rw-r--r-- 1 root root  119 Aug 24 18:31 karmic-partner.list.save
-rw-r--r-- 1 root root  118 Aug 24 18:31 lucid-partner.list
-rw-r--r-- 1 root root  176 Jun  9 16:50 lucid-partner.list.distUpgrade
-rw-r--r-- 1 root root  118 Aug 24 18:31 lucid-partner.list.save
-rw-r--r-- 1 root root   66 Aug 24 18:31 medibuntu.list
-rw-r--r-- 1 root root  306 Jun  9 16:50 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root   66 Aug 24 18:31 medibuntu.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:02 playonlinux.list
-rw-r--r-- 1 root root   80 Jun  9 16:50 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:02 playonlinux.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-natty.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-natty.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:02 ubuntu-wine-ppa-oneiric.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  204 Jun  9 16:50 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  220 Jun  9 16:50 ubuntu-x-swat-x-updates-precise.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 ubuntu-x-swat-x-updates-precise.list.save
-rw-r--r-- 1 root root   72 Aug 24 18:31 ubuntu-x-swat-x-updates-raring.list
-rw-r--r-- 1 root root   72 Aug 24 18:31 ubuntu-x-swat-x-updates-raring.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:01 xorg-edgers-ppa-quantal.list
-rw-r--r-- 1 root root  134 Jun  9 16:50 xorg-edgers-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:01 xorg-edgers-ppa-quantal.list.save
-rw-r--r-- 1 root root   68 Aug 24 18:31 xorg-edgers-ppa-raring.list
-rw-r--r-- 1 root root   70 Aug 24 18:31 xorg-edgers-ppa-raring.list.save
-rw-r--r-- 1 root root    0 Aug 24 16:00 yannubuntu-boot-repair-quantal.list
-rw-r--r-- 1 root root  148 Jun  9 16:50 yannubuntu-boot-repair-quantal.list.distUpgrade
-rw-r--r-- 1 root root    0 Aug 24 16:00 yannubuntu-boot-repair-quantal.list.save
anna@anna-desktop:~$ 
```

Please post the outputs of:

```
cd /etc/apt/sources.list.d
cat ubuntu-wine-ppa-natty.list
cat ubuntu-wine-ppa-oneiric.list
cat ubuntu-wine-ppa-precise.list
```

That should give us some info about the duplicates.

---

### Post by Crossbow on 2013-09-07
> **Jonathan Precise said:**
> Please post the outputs of:

```
cd /etc/apt/sources.list.d
cat ubuntu-wine-ppa-natty.list
cat ubuntu-wine-ppa-oneiric.list
cat ubuntu-wine-ppa-precise.list
```

That should give us some info about the duplicates.

Those returned nothing. I took you literally but maybe there was something else I was supposed to enter? 


```

anna@anna-desktop:~$ cd /etc/apt/sources.list.d
anna@anna-desktop:/etc/apt/sources.list.d$ 
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-natty.list
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-oneiric.list
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-precise.list
anna@anna-desktop:/etc/apt/sources.list.d$ 

```

---

### Post by Bashing-om on 2013-09-07
Crossbow; Hello again.

May I offer a bit of direction.
The "cd" command is to Change Directory from your Present Working Directory. In this case you will Change to the directory "sources.list.d" located on the path "/etc/apt/ -> from the top directory / (root) - subdirectory /etc - sub sub directory /apt. Now your command line can "see" all that is within the directory "sources.list.d" directly. 
Now it is desired to see the contents of the files requested by Jonathan .. the "cat" -for Concatenate - will do this nicely.
so: 1st in terminal:
```

cd /etc/apt/sources.list.d

```
Now you are setting directly able to "look" at all the files within the "sources.list.d" directory.
now do in terminal:
```

cat ubuntu-wine-ppa-natty.list
cat ubuntu-wine-ppa-oneiric.list
cat ubuntu-wine-ppa-precise.list

```
One line at a time .. to print the contents of the files ubuntu-wine-ppa-natty.list, ubuntu-wine-ppa-oneiric.list, and ubuntu-wine-ppa-precise.list to your screen.
copy and paste back here for perusal.

[INDENT][INDENT]continued advise pending
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-09-07
I think all those are from old installs. (part of why I prefer clean installs but that is another issue). 
I do not use bumblebee you may may need that. Are any of the other current PPA's or all all the rest old things you once added. Generally when you upgrade it is best to remove all old PPAs and then re-add the one's you need after upgrade. Not all the time are older PPA available with a new version. And that is where the errors come from.

This is all I have as I added Boot-Repair PPA.

fred@fred-Precise:~$ sudo ls -la /etc/apt/sources.list.d
[sudo] password for fred: 
total 16
drwxr-xr-x 2 root root 4096 Oct  1  2012 .
drwxr-xr-x 6 root root 4096 Sep  5 08:36 ..
-rw-r--r-- 1 root root  148 Jul 19 23:15 yannubuntu-boot-repair-precise.list
-rw-r--r-- 1 root root  148 Jul 19 23:15 yannubuntu-boot-repair-precise.list.save

---

### Post by Crossbow on 2013-09-14
> **Bashing-om said:**
> Crossbow; Hello again.

May I offer a bit of direction.
The "cd" command is to Change Directory from your Present Working Directory. In this case you will Change to the directory "sources.list.d" located on the path "/etc/apt/ -> from the top directory / (root) - subdirectory /etc - sub sub directory /apt. Now your command line can "see" all that is within the directory "sources.list.d" directly. 
Now it is desired to see the contents of the files requested by Jonathan .. the "cat" -for Concatenate - will do this nicely.
so: 1st in terminal:
```

cd /etc/apt/sources.list.d

```
Now you are setting directly able to "look" at all the files within the "sources.list.d" directory.
now do in terminal:
```

cat ubuntu-wine-ppa-natty.list
cat ubuntu-wine-ppa-oneiric.list
cat ubuntu-wine-ppa-precise.list

```
One line at a time .. to print the contents of the files ubuntu-wine-ppa-natty.list, ubuntu-wine-ppa-oneiric.list, and ubuntu-wine-ppa-precise.list to your screen.
copy and paste back here for perusal.

[INDENT][INDENT]continued advise pending
[/INDENT][/INDENT]

Still nothing: 

```
anna@anna-desktop:~$ cd /etc/apt/sources.list.d
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-natty.list
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-oneiric.list
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-precise.list
anna@anna-desktop:/etc/apt/sources.list.d$ 

```

---

### Post by Jonathan Precise on 2013-09-14
> **Crossbow said:**
> Still nothing: 

```
anna@anna-desktop:~$ cd /etc/apt/sources.list.d
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-natty.list
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-oneiric.list
anna@anna-desktop:/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-precise.list
anna@anna-desktop:/etc/apt/sources.list.d$ 

```

That means those PPAs are no longer used. Proceed to removing them:

```
cd /etc/apt/sources.list.d
rm ubuntu-wine-ppa-natty.list
rm ubuntu-wine-ppa-oneiric.list
rm ubuntu-wine-ppa-precise.list
```

---

### Post by Jonathan Precise on 2013-09-14
I see the duplicates:

> ```
guest-ZEsY44@anna-desktop:~$ cat /etc/apt/sources.list# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


**deb http://us.archive.ubuntu.com/ubuntu/** raring main **restricted**
deb-src http://us.archive.ubuntu.com/ubuntu/ raring restricted main multiverse universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates restricted main multiverse universe #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu karmic partner


deb http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ raring-security universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-security multiverse
# deb-src http://archive.ubuntu.com/ubuntu raring main
# deb-src http://archive.ubuntu.com/ubuntu raring main
# deb-src http://archive.canonical.com/ubuntu raring partner
**deb http://us.archive.ubuntu.com/ubuntu/ raring restricted**
# deb-src http://archive.ubuntu.com/ubuntu/ raring main restricted
```

Please remove the second bold line, as it is a duplicate.

---

### Post by Crossbow on 2013-09-14
> **Jonathan Precise said:**
> That means those PPAs are no longer used. Proceed to removing them:

```
cd /etc/apt/sources.list.d
rm ubuntu-wine-ppa-natty.list
rm ubuntu-wine-ppa-oneiric.list
rm ubuntu-wine-ppa-precise.list
```

OK, did that. Thanks. It didn't solve my problem but good to get that junk out of there.

---

### Post by Crossbow on 2013-09-14
> **Jonathan Precise said:**
> I see the duplicates:



Please remove the second bold line, as it is a duplicate.

Hi, I'm sorry, I know I should know how do remove that, but I don't. :(

---

### Post by oldfred on 2013-09-14
If you are in your system.

 # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

---

### Post by Crossbow on 2013-09-14
> **oldfred said:**
> If you are in your system.

 # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

THANK YOU THANK YOU THANKYOU! That did it! Marking solved.

---

