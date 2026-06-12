---
title: "Am I using Unity ?"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gnurfos on 2011-09-18
In system settings, I have "force fallback mode" to ON (I did not set it so voluntarily).
However, I have the launcher, and fancy effects when changing workspaces.
But I can't find how to configure the launcher, or anything unity-related (except keyboard shortcuts).

---

### Post by garvinrick4 on 2011-09-18
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
Above is one link I had around to using Unity.

---

### Post by Gnurfos on 2011-09-18
Thanks, I did not have ccsm installed. How can it run without settings :) Is everything stored in text files somewhere, and the manager is just a fancy editor for those ?

---

### Post by garvinrick4 on 2011-09-18
> Is everything stored in text files somewhereIn my signature there is two sites, one is a pdf book that explains file system and such.
the other is guide for installing and explanations of all sorts of things Ubuntu.
[COLOR=Red]
You have jumped into a Beta install of version not released yet, tough to learn in  a system that still has breakage and tons of upgrades.[/COLOR]
10.04 LTS or 11.04 might be a better choice, but you enjoy your Ubuntu. Welcome to Forums.

---

### Post by Gnurfos on 2011-09-18
Sorry my question was not well phrased, but it was only about Unity, not Ubuntu in general.
Do you mean that in the release version of Oneiric, ccsm will be installed by default ? Or (that's another version of my question), is there some other way to change Unity settings ?

---

### Post by garvinrick4 on 2011-09-18
> **Gnurfos said:**
> Sorry my question was not well phrased, but it was only about Unity, not Ubuntu in general.
Do you mean that in the release version of Oneiric, ccsm will be installed by default ? Or (that's another version of my question), is there some other way to change Unity settings ?
I gave you the only Unity link I had around.
Do not touch the settings in CCSM it is the most asked question in these Forums it seems.
"I screwed around with CCSM and I cannot get my install to work anymore"

Just install what you want as apps, anything you want in launcher when it is open right
click on icon in launcher and tell it to stay in launcher. 
Settings are opened in upper right icon where you logout and shutdown and such.
Many ways to do things in Unity must read up and use a learning curve like we all did,
just like any operating system that is new to a user.

---

### Post by Gnurfos on 2011-09-18
I just wanted to customize the launcher, not complicated stuff.
> **garvinrick4 said:**
> when it is open right click on icon in launcher and tell it to stay in launcher. 
This was not powerfull enough for me, and/or not always working (though I wanted quite simple things: just an icon to run a command).

Now indeed I'm screwed. But I just installed ccsm and ran it. Inside, I only changed one keyboard shortcut, and then reverted it (really nothing else, I knew it was dangereous, I just wanted to see what's configurable when it's stable). I still have the wall, and luckily the keyboard shortcut to launch a terminal, but the launcher/dash/pannel are gone, and I have no idea how to fix this.

I really changed nothing, so do you think just uninstalling ccsm could do ? Or is there a way to revert whatever might have changed, or to investigate the problem ?

Thanks.

---

### Post by garvinrick4 on 2011-09-18
Try running these one at a time in a terminal, I have not screwed up CCSM in a long time. 
This is a fix I read and not used in practice. (just because I do not want to screw around with ccsm and break it) they say it works.
```
Unity --reset
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
 
```

---

### Post by garvinrick4 on 2011-09-18
I remember a time back in 11.04 alpha I did the screw around with CCSM thing.
Had to use a Live USB and see what the settings were in CCSM on it and write
them down and hand reset my CCSM. Last a messed with it.
I think I just told you it would break your machine? Good luck and enjoy.

OH, yes you can always get to a terminal with ctrl/alt/F1 thru ctrl/alt/F6 and ctrl/alt/F7 gets you back to desktop.
If you get into the tty and cannot get out run
```
sudo /etc/init.d/lightdm restart
```
to get back to login screen. Later Rick

---

### Post by Gnurfos on 2011-09-18
unity --reset restores the launcher etc (I lost my customization but that's not a big deal), but never returns. If I kill / ctrl-C it, bad things happen.

I think I will leave out unity for a while until it becomes more polished, but how do I get out ? In "system settings", I already have "forced fallback on", and I can't get to the login screen (I turned on autologin at install time, and now even editing /etc/lightdm/lightdm.conf does not seem to have any effect).

Thanks for your help so far, and any further hint !

---

### Post by garvinrick4 on 2011-09-18
Go to tty ctrl/alt/F1 and do the lightdm restart code I gave you.
I really do not know what is going on with some of your config files now.
Good luck partner and you have a great day.

---

### Post by dino99 on 2011-09-18
[http://www.upubuntu.com/2011/09/configure-ubuntu-1110-to-automatically.html](http://www.upubuntu.com/2011/09/configure-ubuntu-1110-to-automatically.html)

you can be logged as "gnome" if you install gnome-shell, and as "classic" if gnome-session-fallback is installed (select which you want when you set password  with lightdm)

---

### Post by Gnurfos on 2011-09-18
I finally escaped !
A problem was, I did not have any session chooser (autologin was on, and tweaking ligthdm.conf did not turn it off). I managed to run enough of unity (with --reset) to get into the "system settings" and turn off autologin there, and it worked.

Now selecting "ubuntu 2d" is a fine option: I even have my old launcher/pannel settings back. I just lost the fancy wall desktop switcher, I can leave without that :)

Maybe I'll try 3d again, but later ...
Thanks for the help !

---

### Post by garvinrick4 on 2011-09-18
No problem, enjoy your Ubuntu and have a nice day.

---

### Post by cariboo on 2011-09-18
Click the power button in the top right corner and select System Settings->User Accounts and turn off automatic login there.

It doesn't sound like Unity is really your problem. If you have little to no experience using a Linux distribution, I'd really suggest using an LTS (10.04) version until you get familiar with the way things work.

---

### Post by Gnurfos on 2011-09-19
> **cariboo907 said:**
> Click the power button in the top right corner and select System Settings->User Accounts and turn off automatic login there.


That's what I did, but I cannot understand why editing lightdm.conf did not work.

> **cariboo907 said:**
> It doesn't sound like Unity is really your problem. If you have little  to no experience using a Linux distribution
I ran on an old Debian before, don't know if that counts. So I have some experience with things crashing here and there, but not to such a worrying level :)

---

### Post by cariboo on 2011-09-19
> **Gnurfos said:**
> That's what I did, but I cannot understand why editing lightdm.conf did not work.


I ran on an old Debian before, don't know if that counts. So I have some experience with things crashing here and there, but not to such a worrying level :)

The best tip I can offer then, is to backup your configuration files before making any changes, that way you can revert when things go wrong. :)

---

### Post by Gnurfos on 2011-09-19
> **cariboo907 said:**
> The best tip I can offer then, is to backup your configuration files before making any changes, that way you can revert when things go wrong. :)

I try to, when making risky changes. The problem I had in this case (a classic problem, at least for me) is to identify the said files, for a given change.

Another unclean thing, but that one seems specific to Unity (or Compiz), was the notion of "making changes" (it broke without me feeling I really changed anything).

---

