---
title: "Setting up Flash-Aid"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Dural on 2012-12-22
I am using Ubuntu 12.04 64-bit. I have a recourring problem with Flash where if I play videos on Youtube for a while eventually my whole system freezes. Sometimes I can get back to the console and restart lightdm and then login again but other times I have to power off my system in order to get everything back to normal again. Would Flash-Aid help in dealing with this? I installed the latest verion of flash with a system update and I don't want to risk messing anything up.

Hardware:
GPU - Nvidia GeForce 9800GT Mobile
Processor - Intel Core 2 Duo @ 2.40 Ghz
Drivers - Nvidia version-experimental 304 (believe these were the most recent drivers that would work on my system; think I installed them in November)

I should note that this problem happened even when I used the Nouveau drivers that were initially installed with my system. It also happened whether I used Unity2D or Gnome Classic.

---

### Post by ikt on 2012-12-22
I don't think flash should be causing x.org to freeze.

I'd recommend checking over this:

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

With regard to flash-aid helping, it may not help with the freezing but it will help in other areas, always recommend running it since there's no harm in not doing so.

---

### Post by Dural on 2012-12-22
When I open Flash-Aid in Wizard Mode, I am offered the Beta plugin for 64-bit. Then I go to the next screen and I see the following options:

> Which installed plugins you want to remove?
Gnash from repositories (/usr/lib/gnash/libgnashplugin.so)
Adobe from repositories (/usr/lib/flashplugin-installer/libflashplayer.so)


I'm worried about removing either one because I just installed the update for the latter and I don't want to risk breaking my system.

---

### Post by robsoles on 2012-12-22
removing those cannot break your system in general - removing those and not installing something to play flash files for you can break your system's ability to play flash, of course, but the operating system is not reliant on flash players to do 'regular operating system' stuff.

General rule of thumb I have observed about flash player is that the less advanced you are as a user the better off you are to have one and only one - amongst other things this practice makes it that you know for sure which flash player is giving you trouble if your flash fails... That is, the only one installed ;)

Flash Aid (by memory, been a while) should be offering to remove all previous editions/versions of (all) flash (players/plugins) and then be recommending/offering-to-install the best and most up to date match for your system that it can find.

I'll understand, and hardly hold it against you, if you don't wanna take my word for it but (1) flash-aid hasn't failed anybody I know of who just took its default offerings and (2) ikt is very probably right about it not being flash freezing xorg, it might be something flash is 'poking' which is exposing a weakness in your system but [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) is more than likely very very worth your while to read.

---

