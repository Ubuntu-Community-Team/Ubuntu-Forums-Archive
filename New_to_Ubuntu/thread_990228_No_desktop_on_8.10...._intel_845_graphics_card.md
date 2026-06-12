---
title: "No desktop on 8.10.... intel 845 graphics card"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by dead_man_walking on 2008-11-22
I just installed ubuntu 8.10 and when I login I just get the desktop background (no gnome menus) and my computer just stops responding.
Ram : 768 MB
Board : intel 845

---

### Post by dead_man_walking on 2008-11-23
Just wanted to let you guys know that the problem is solved
Here is the solution. make sure you can access the internet then

1. Change your session to fail safe terminal 
2. Type these two commands
3. sudo apt-get update
4. sudo apt-get upgrade

---

### Post by flameproof on 2008-11-24
I suggest, go to command line and do:

sudo apt-get remove compiz
sudo apt-get remove compiz-core

The 845 video is not really supported in 8.10 and compiz does the special effects, which 845 can't handle.

You can go to command line by doing ALT+F3 from your blank screen, and leave it with ALT+F7

Or do a F4 when you boot.

Hope it helps, it worked for me.

---

### Post by ozwaldca on 2008-12-18
> **flameproof said:**
> I suggest, go to command line and do:

sudo apt-get remove compiz
sudo apt-get remove compiz-core

The 845 video is not really supported in 8.10 and compiz does the special effects, which 845 can't handle.

You can go to command line by doing ALT+F3 from your blank screen, and leave it with ALT+F7

Or do a F4 when you boot.

Hope it helps, it worked for me.

That worked for me!  thanks i have been searching for days!!

---

### Post by MeURi on 2008-12-18
dead_man_walking, if the problem is solved, please mark this thread as [SOLVED], so other users having similar issues can benefit from these posts ;-)

---

### Post by jeffimus on 2008-12-19
> **flameproof said:**
> The 845 video is not really supported in 8.10 and compiz does the special effects, which 845 can't handle.

True, flameproof, but it's the fault of the 'intel' driver, not the 845.  The 845 could handle compiz perfectly well in hardy - rotating cube desktop, bouncy windows and everything - but that was using the i810 driver. Unfortunately with intrepid they discontinued the i810 driver leaving only 'intel'.  We need them (the xorg people) to fix 'intel' so that it works properly with the 845.

See [this thread]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/285250") to track the bug. Don't hold your breath, as there hasn't been any news on it since mid-November.

---

### Post by pluckypigeon on 2009-01-30
> **jeffimus said:**
> 
See [this thread]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/285250") to track the bug. Don't hold your breath, as there hasn't been any news on it since mid-November.

Keep your eye on this one:
[http://bugs.freedesktop.org/show_bug.cgi?id=19068]("http://bugs.freedesktop.org/show_bug.cgi?id=19068")

It's likely to be fixed there first. Unless a ubuntonian comes up with a patch.

---

