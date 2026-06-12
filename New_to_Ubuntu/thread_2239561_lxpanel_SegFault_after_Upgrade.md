---
title: "lxpanel SegFault after Upgrade"
date: 2014-08-14
forum: New to Ubuntu
---

### Post by Sanctimonious_Ape on 2014-08-14
New to Linux, but used SCO UNIX :oops: many years ago for some specialized tasks and so am not entirely afraid of the command line (and am reasonably comfortable with 'vi' as a result).  After trying several distros, I recently settled on Lubuntu 14.04 32bit for performance reasons (laptop is about 10 years old -- about as long ago as I last used SCO).  Been installing various things over the past few weeks to try them out, some of which have required adding PPAs and I'm afraid one of those has potentially screwed me up: after being prompted to perform a routine software update this morning followed by a reboot, my lxpanel crashed and wouldn't restart.

I was able to get the Openbox menu to appear and thus start my browser and terminal, but all attempts thus far at restarting my panel result in a SegFault.

Tried:
1. Copying default panel config:
```
cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
```

2. Restarting lxpanel:
```
lxpanelctl restart
```

3. Rebooting again.

4. Reinstalling lxpanel (including lxpanel-core, which for some reason wasn't installed) via Synaptic.  Still SegFaults when attempting to start:
```
$ lxpanel

** (lxpanel:4253): WARNING **: terminal lxsession-default-terminal isn't known, consider report it to LibFM developers
Segmentation fault (core dumped)
```

Short of reinstalling the whole OS, I don't know what else to try to recover from this.  My PPA list is below should anything jump out as having caused the problem.  I'm hoping something does and that I can remove it, perform an apt-get dist-upgrade/update or somesuch, and have my problem fixed.

Please don't construe any of the above to mean I know what I'm doing - I just know how to use Google.  I understand computers (having started with a VIC-20), but know very little about Linux.  Thank you anyone who takes the time to read this and contribute a solution.


PPA List:
```
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/appgrid-stable-trusty.list:deb http://ppa.launchpad.net/appgrid/stable/ubuntu trusty main
/etc/apt/sources.list.d/appgrid-stable-trusty.list.save:deb http://ppa.launchpad.net/appgrid/stable/ubuntu trusty main
/etc/apt/sources.list.d/chrome-remote-desktop.list:deb http://dl.google.com/linux/chrome-remote-desktop/deb/ stable main
/etc/apt/sources.list.d/chrome-remote-desktop.list.save:deb http://dl.google.com/linux/chrome-remote-desktop/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/lubuntu-dev-lubuntu-daily-trusty.list:deb http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu trusty main
/etc/apt/sources.list.d/lubuntu-dev-lubuntu-daily-trusty.list.save:deb http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu trusty main
/etc/apt/sources.list.d/lubuntu-dev-staging-trusty.list:deb http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu trusty main
/etc/apt/sources.list.d/lubuntu-dev-staging-trusty.list.save:deb http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu trusty main
/etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

```

---

### Post by vasa1 on 2014-08-14
Well, with the "dev" and "daily" and "staging" ppas you've installed, crashes/bugs etc shouldn't surprise. I'd suggest doing a clean re-install and then going easy on the ppas. And do you really need Appgrid?

What are you planning to use your computer for?

---

### Post by Sanctimonious_Ape on 2014-08-14
I don't recall installing those PPAs - I believe they came installed, but not enabled.  I may have enabled staging while testing something, but I know better than to enable dev.  Appgrid has been uninstalled (not impressed, but LUbuntu's Software Center is slightly more barebones than I'd prefer so I'm open to suggestions on that one), but I never removed the Appgrid PPA.

Is there no way to roll back the "upgrades" or remove certain repositories and apt-get a functioning LXDE setup?  I realize I probably could have reinstalled from scratch by now, but am trying to learn from my mistake rather than pretending it never existed.

As for what I am using the PC for:  general use, but I definitely want secure remote access over the internet because my job takes me away from home a lot yet my family needs access to the PC as well so I can't take it with me.

---

### Post by Sanctimonious_Ape on 2014-08-14
So based upon a direction hinted at in your reply, I've removed appgrid* and lubuntu-dev* from /etc/apt/sources.list.d/ and performed:
```
# apt-get update
# apt-get dist-upgrade
# apt-get autoremove (recommended by the previous step)

```

Seems to have installed a different kernel (3.13.0.32 was removed, says .33 and .34 are installed - not sure why the .33 is there).  Not sure if this is a good thing, as the kernel I'm now running while experiencing these problems is listed as .34 (per uname -r).  Backing up my files and rebooting to see what happens.   If you have any further advice on rolling back, please let me know.  Thanks!

---

### Post by Sanctimonious_Ape on 2014-08-14
Okay, so I threw caution to the wind and rebooted.  Logged in and same thing: no panel.  Logged out, switched to "LXDE" instead of default LUbuntu profile/config (having forgotten about that possibility until now) and it worked.  Logged out, switched back to "Lubuntu" - no panel.  Started it manually and it came up looking like it did under the "LXDE" profile so I killed it.  I copied my original ~/.config/lxpanel/Lubuntu/panels/panel file back into place, set ownership and chmod as the original's were set,  fired up lxpanel again and it crashed just like the first time.  Must be something wrong with my config file.

I told it to go ahead and report the error (are these saved somewhere in text form so I can copy and paste it here?).  Going to see if it'll start the panel up automatically if I switch back to the default panel config and re-login (it seemed to no longer try starting upon login after the first crash).

---

### Post by Sanctimonious_Ape on 2014-08-14
Spoke too soon.  After the crash under the my original "panel" file, the default one no longer worked as well.  Re-login, login under "LXDE", nor reboot helped.  I'm gonna have to write this off as having royally trashed my install and redo (not looking forward to figuring out how to reinstall everything I wanted that wasn't in Ubuntu's sanctioned software repositories again).  Thought there'd be an easy way to roll back, but I wasn't able to find it in a reasonable amount of searching.  Thanks for taking the time to try to help, vasa1.

---

### Post by linbu on 2014-08-14
Sanctimonious_Ape,

You are not alone!

This same thing has happened to me immediately after the software update & reboot early today. Got the same exact error messages you show.

Was able to open PCManFM and under the Advanced setting I changed the default terminal to "xterm %s". Result on reboot was that my panel was restored for about 10 seconds then just went away again. The extreme right and left ends "ony" of the panel seemed to have a stacked look, as though there were two ends of the panel. Rest of panel was good looking.

CLI command $ lxpanel resulted in:
Segmentation fault (core dumped)

I too would like my panel back.

Hank

---

### Post by linbu on 2014-08-14
When this first happened I tried:

lxpanelctl restart

and had no reaction

I then tried:

lxpanel

and made a copy of the output;

$ lxpanel

** (lxpanel:3196): WARNING **: terminal lxsession-default-terminal isn't known, consider report it to LibFM developers

** (lxpanel:3196): WARNING **: launchbar: desktop entry does not exist


** (lxpanel:3196): WARNING **: launchtaskbar: can't init button


(lxpanel:3196): Gdk-CRITICAL **: IA__gdk_window_get_screen: assertion 'GDK_IS_WINDOW (window)' failed

(lxpanel:3196): Gdk-CRITICAL **: IA__gdk_screen_get_system_colormap: assertion 'GDK_IS_SCREEN (screen)' failed

(lxpanel:3196): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(lxpanel:3196): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.23/gdk/gdkpixbuf-drawable.c:1249: Source drawable has no colormap; either pass in a colormap, or set the colormap on the drawable with gdk_drawable_set_colormap()
Segmentation fault (core dumped)

Hank

---

### Post by Sanctimonious_Ape on 2014-08-14
Initially was getting something similar to just the first line or two of your output (wish I'd saved it somewhere or that there was a log I could refer to).  Now I'm logged into "LXDE" profile and just tried the command again and got a mouthful in return as well:

```

 root@MyPC:~# lxpanel &
[1] 5419
root@MyPC:~# 
** (lxpanel:5419): WARNING **: terminal lxsession-default-terminal isn't known, consider report it to LibFM developers

** (lxpanel:5419): WARNING **: launchbar: desktop entry does not exist


** (lxpanel:5419): WARNING **: launchtaskbar: can't init button


(lxpanel:5419): Gdk-CRITICAL **: IA__gdk_window_get_screen: assertion 'GDK_IS_WINDOW (window)' failed

(lxpanel:5419): Gdk-CRITICAL **: IA__gdk_screen_get_system_colormap: assertion 'GDK_IS_SCREEN (screen)' failed

(lxpanel:5419): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(lxpanel:5419): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.23/gdk/gdkpixbuf-drawable.c:1249: Source drawable has no colormap; either pass in a colormap, or set the colormap on the drawable with gdk_drawable_set_colormap()

(lxpanel:5419): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(lxpanel:5419): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(lxpanel:5419): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

[1]+  Segmentation fault      (core dumped) lxpanel

```

Wish I had the time to play with this, but if I'm gonna need to reinstall everything I've been working on setting up the past few weeks then I don't.  I've backed up my files and am headed to either one of XUbuntu, Mint 17 XFCE, or SolydX32 - I'll refamiliarize myself with them with the additional knowledge I now have and decide from there.  Good luck!

---

### Post by vasa1 on 2014-08-14
> **Sanctimonious_Ape said:**
> ...
Wish I had the time to play with this, but if I'm gonna need to reinstall everything I've been working on setting up the past few weeks then I don't.  I've backed up my files and am headed to either one of XUbuntu, Mint 17 XFCE, or SolydX32 - I'll refamiliarize myself with them with the additional knowledge I now have and decide from there.  Good luck!
I don't recall installing those PPAs - ***I believe they came installed, but not enabled.***This simply isn't true :)

I'm sure you'll do well with Mint or SolydX32. All the best.

---

### Post by Sanctimonious_Ape on 2014-08-15
In other words: "Get lost, kid!"  Well, sorry... ain't happening (at least not just yet).

Those OSs were listed in order of preference and that preference is due to the apparent support level.  I'm starting with Ubuntu derivatives because they've got the most support, but once I'm more comfortable maybe I'll move on.   I've tried several more distros than those in the past looking for *someone* who set things up with a Windows power-user in mind, and am frankly flabbergasted not to have found a single one that makes it easy for such a user to slip into Linux.  High on my list were things like:

1. Matching keyboard shortcuts (Lubuntu came closer than others), and yes I know I can reconfigure them - although I have yet to find a way to limit an action occurring only when the Super key is released so I can use it just like Windows does (Super-E triggers only the file manager, but Super by itself triggers the panel menu - best I could seem to manage was to cause BOTH to trigger under Linux).

2. A file manager that used strictly base-2 measurements (i.e. MiB & GiB) for REAL file size measurements rather than the base-10 (MB, GB rebranded) counts that marketing departments LOVE because it makes their storage devices sound larger than they really are.  Windows XP doesn't buy into that crap, and I don't believe later versions did either.  Another win for Lubuntu there.  I ran into a bug on a Mint distro that used Brasero to burn disks - it knew DVDs could only hold 4.37GiB of data, but counted my files using base-10 and thought my 4.2GiB collection was far too big for a 4.37GiB disc because 4.2GiB = 4.7GB.  Brasero would have users *waste* at least a few hundred MiB of disk space per DVD due to this stupidity.  Can't imagine the wasted space on a BlueRay disk...

3. GUI apps set up to make it easy to do the less frequently performed tasks such as tracking down the source of problems like the one that started this thread (rather than having to remember which of the many places to look to find answers).  Windows has Admin menu items that made this easy.  I shouldn't have to learn ***how to even find** all the info* that I need to even have a clue what the problem might be ***before I even work on the problem itself***.  Maybe something like this exists and I'm unaware of it, but a quick look through my freshly-installed Xubuntu's menus doesn't reveal any such thing that I can discern - there are exactly TWO items in my "System" menu, neither of which address this issue or even allow me to look at logs (assuming I even had a clue which ones to look at).

I may well be making an ass of myself here, but I don't really care.  I've heard "this will be the year of the Linux desktop" year after year and it still hasn't happened, despite Red Hat and - more directly - Canonical's best efforts and now I think I know why.  People shouldn't have to spend more time learning how to do things they are only going to do once in a blue moon than they do actually using the computer normally.  That may be an exaggeration, but right now I'm not thinking it much of one.

Regardless, I'm determined to stick this one out for the time being.  Maybe I'll make myself more valuable to employers for knowing both Windows and Linux.  Maybe my experiences and willingness to make an ass of myself to prove a point about usability might make a difference.  Maybe...  but probably not.

What can I say - I'm a dreamer...

---

### Post by linbu on 2014-08-15
Fixed, for me anyway, today with a "Lubuntu Software Update" at noon EDT.

Thanks to any Administrators, Moderators, viewers, members here who may have passed the word to the powers that be.

Sorry, this is not my thread and so I can not mark it solved.

Thanks :-)

Hank

---

### Post by vasa1 on 2014-08-15
> **linbu said:**
> Fixed, for me anyway, today with a "Lubuntu Software Update" at noon EDT.

Thanks to any Administrators, Moderators, viewers, members here who may have passed the word to the powers that be.

Sorry, this is not my thread and so I can not mark it solved.

Thanks :-)

HankHi, if you have any problems in future may I suggest that you start your own thread in the subforum you think most appropriate.

---

### Post by Sanctimonious_Ape on 2014-08-15
Sorry for my late night frustrated ranting (although I stand by my basic  points).  I really **do** appreciate the help you *tried* to  offer, so I will mark this thread "solved" to indicate as much.  Thanks again.

---

