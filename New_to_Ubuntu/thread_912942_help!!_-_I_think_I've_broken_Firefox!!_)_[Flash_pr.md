---
title: "help!! - I think I've broken Firefox!! :) [Flash problems]"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by rocka on 2008-09-07
Hi all,

I am running 8.04 and all has been going fine for quite a while now.
Recently I wanted to play some .rmvb files and tried to install real player and a couple of other media player programs [VLC and Helix], none of them work with these particular .rmvb files I wanted to play.

I did some searching and came across a post here about how to install the real player using "Synaptic" instead of the "Add/Remove..." feature built in to the main menu of Ubuntu itself. Well, it worked, kind of, but with a few side effects.

Firstly let me tell you what I did to my system:
As per the instructions, I added the following lines to my /etc/apt/sources.list file
```
## UbuntuLinux Japan
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy/
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-experimental/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-experimental/
## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 5 Elyssa (stable) +++
deb http://packages.linuxmint.com elyssa main upstream import

## +++ Backports (not as stable) +++
deb http://packages.linuxmint.com elyssa backport

## +++ Community (not as stable) +++
deb http://packages.linuxmint.com elyssa community

## +++ Romeo (unstable) +++
#deb http://packages.linuxmint.com elyssa romeo

## +++ Source Repositories +++
#deb-src http://packages.linuxmint.com elyssa main upstream import
#deb-src http://packages.linuxmint.com elyssa community
#deb-src http://packages.linuxmint.com elyssa backport
#deb-src http://packages.linuxmint.com elyssa romeo
```

At first, it didn't even find Realplayer11 it only found 10, so I removed the lines relating to the "Mint" section.
Then it found a Realplayer and installed it and I was able to watch my files, after removing Helix which apparently was conflicting with the Realplayer.


Now, here is the problem:
First, my Google search has been taken over by the Mint Custom Search and I can't find out how to get the normal search back.

But here is the main problem:
It's stuffed up my flash plugin, and my audio setup somehow.

At first I had no sound at all from any application, until I turned my speakers all the way up. Then I noticed I had sound but really really quiet. Looking in /system/preferences/sound I found everything was set to "autodetect". When I changed them to "VIA 8237", most of my programs started making sounds again, at the normal volume. Movie Player, VLC, Rythmbox, all ok now. But not Firefox.

Firefox, when I try to watch Youtube vids or listen to streaming .asx files from the ABC radio etc, I get no sound [or extremely low volume sound]. Also, the video is really choppy and stops and starts. As well, as soon as I load any site that has any flash in it, the CPU usage immediately pings to 100%. It never used to be like that. Not only that, but now when I load pages with flash, anywhere there's flash all I get is a gray background with a triangle inside a circle in it, and the flash only starts when I click in that area.

I've removed the lines that I had added to my /etc/apt/sources.list, and I've also uninstalled and reinstalled Firefox. I've checked for updates, both in "Add/Remove..." and Firefox itself.

What can I do next?
How can I get my Firefox back to the normal, original version?
Can I uninstall and reinstall the Flash plugin? How?

thanks a lot for any help...
:)

---

### Post by Pro-reason on 2008-09-07
There is no need to remove the Mint repositories.  They are quite useful.

However, do not just install the latest version of everything.  Mint's versions of Firefox, in  particular, are rather annoying (as they impose a stupid Mint-themed Google search which doesn't work properly).

In Synaptic, select a package and hit Ctrl-E to “Force Version”.  From the list that comes up, make sure you don't choose a Mint version.  That's all you have to do.

Once you have forced a version, you can use “Lock Version” to make sure that it doesn't get updated if you hit “All Upgrades”.

---

### Post by rocka on 2008-09-07
ok , thanks - I have my normal search back now :)


but the flash problems still remain...

---

### Post by Pro-reason on 2008-09-07
> **rocka said:**
> ok , thanks - I have my normal search back now :)


but the flash problems still remain...

Open up Add-ons in Firefox, and go to the Plug-ins tab.  Make sure that only one Flash plug-in is enabled.

---

### Post by rocka on 2008-09-07
yes, there is only one there.
Seems I can't select on that page so I could paste here, but really, there's only one...

---

### Post by Pro-reason on 2008-09-07
> **rocka said:**
> yes, there is only one there.
Seems I can't select on that page so I could paste here, but really, there's only one...

Open Synaptic and search for Flash.  See what version of the package you have.  Try forcing a different version.  See what you can change.  Shut down Firefox each time.

---

### Post by rocka on 2008-09-07
ok, there's three there:
flashplugin-nonfree 9.0.124.0ubuntu2
libflash0c2 0.4.13-9ubuntu1
libflash-mozplugin 0.4.13-9ubuntu1

But <Ctrl-E> does nothing on any of them.

I'll try removing them and re-installing them again...

edit:
removed, reinstalled, rebooted - - still same...

---

### Post by Xiong Chiamiov on 2008-09-07
> **rocka said:**
> yes, there is only one there.
Seems I can't select on that page so I could paste here, but really, there's only one...
```

aptitude search ~nflash

```
if I remember my aptitude commands.  You might need *'s around flash.

---

