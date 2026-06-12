---
title: "&quot;search applications&quot; (unity 2d) is closing after sec"
date: 2011-06-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sartic on 2011-06-04
Is there any solution? Testing alpha 1, updated on core duo, intel vga onboard.

---

### Post by 23dornot23d on 2011-06-04
Not seen a solution yet even after upgrading - but this video is quite good in showing
what is and is not working .....

I have the same experience on my machine as is shown here ,,,, [LINK TO VIDEO]("http://www.youtube.com/watch?v=E7SF0zhZhJM&feature=uploademail")

The video is 2 days old at thee time of posting this ..... so people may already have seen it
(but I thought it looked to be a good video).

---

### Post by kansasnoob on 2011-06-04
I reported that during iso-testing:

[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/791214](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/791214)

It might help to add "it effects me too" and even a brief comment :)

---

### Post by jerrylamos on 2011-06-04
> **sartic said:**
> Is there any solution? Testing alpha 1, updated on core duo, intel vga onboard.

Alpha 1 is pretty much dead-on-arrival for me.  

I'm running daily build Live persistent here with 04 June.  A bunch of stuff works on it obviously missing some things but can function.

Jerry

---

### Post by Smithie on 2011-06-05
I have the same issue, and since my graphics card currently dislikes Ubuntu 3d, I'm stuck largely working in Gnome Classic (no effects).  Hopefully the 2d fix comes in soon.

Pentium D, nVidia 8400GS

---

### Post by novatillasku on 2011-06-05
Me too closing Applications in Alpha 1, and start with Unity 2D.But in my oneiric (natty-upgrade-oneiric) work Unity 3D and applications work fine.

---

### Post by jerrylamos on 2011-06-05
Daily Build 5 June has this same problem.  I'm trying to do ubuntu-bug but can't get a command line up while the desktop panel is active.  Ctrl-Alt-F1 gets a command line but ubuntu-bug is dependent on a graphical desktop....

Jerry

---

### Post by sparker256 on 2011-06-05
> **jerrylamos said:**
> Daily Build 5 June has this same problem.  I'm trying to do ubuntu-bug but can't get a command line up while the desktop panel is active.  Ctrl-Alt-F1 gets a command line but ubuntu-bug is dependent on a graphical desktop....

Jerry
Does Ctrl-Alt-t work?

Bill

---

### Post by jerrylamos on 2011-06-05
> **sparker256 said:**
> Does Ctrl-Alt-t work?

Bill
Sure does!  Thanks!  I tried Alt-F2, which does not, and right click to make a launcher, which does not.

Ctrl-Alt-t works!

Thanks, ubuntu-bug submitted O.K. for my problem which was Live defaulting to Unity desktop which isn't even on the .iso.  Unity 3D doesn't work on Radeon Mobility 7500 which is suppsed to default to 2D.

Jerry

---

### Post by kansasnoob on 2011-06-05
> **jerrylamos said:**
> Sure does!  Thanks!  I tried Alt-F2, which does not, and right click to make a launcher, which does not.

Ctrl-Alt-t works!

Thanks, ubuntu-bug submitted O.K. for my problem which was Live defaulting to Unity desktop which isn't even on the .iso.  Unity 3D doesn't work on Radeon Mobility 7500 which is suppsed to default to 2D.

Jerry

You know the default "fallback" is now unity-2d.

If you want the new borked panels you have to install "gnome-session-fallback".

And the actual Alpha1 defaulted everything to unity-2d AFAIK.

---

### Post by jerrylamos on 2011-06-05
> **kansasnoob said:**
> You know the default "fallback" is now unity-2d.


Daily Build 05 June Live defaulted to "Ubuntu" which was a blank red screen with only cursor on IBM Thinkpad T40 Radeon Mobility 3500.  I don't even think there is "Unity" support on the Live so that didn't make any sense at all.

Now the T40 is "blacklisted" or whatever term on Natty Narwhal so the old desktop shows up, since Unity 3D won't run on it.  For Narwhal I installed Unity 2D from Synaptic.

On Oneiric Ocelot Live what I did was Ctrl-Alt-Del which got me a drop down window to log out, logged back in as Ubuntu with the opportunity to change the desktop from "Unity" which it had selected (in error) to "Unity 2D" which in fact did come up.

So I submitted a launchpad bug since the Live defaulted to "Unity" instead of "Unity 2D" like it shuold have.  I'm on another pc now so I don't know the bug #.

Jerry

---

### Post by sparker256 on 2011-06-08
Appears to have been fixed with the latest updates. I looks like it was a qt issue that has been resolved. I was logged into my unity 2D and it was broke before I updated and after updating it is working correctly.

Bill

---

### Post by jerrylamos on 2011-06-08
8 June CD daily build Live on this pc these do not work:
BFB button
Applications launcher
Workspace launcher
Files & Folders launcher.

These do work: 
Firefox launcher
Home Folder launcher.

It's an IBM ThinkCentre 2 GHZ 1 GB with intel i845G graphics.

I can get to System Settings with the Power applet and I can get terminal to run with Ctrl-Alt-t.

Jerry

---

### Post by jerrylamos on 2011-06-08
Those buttons/launchers are in the same state of working/not working on my IBM Thinkpad T40 1.5 GHZ radeon mobility 7500.

I did get "Workspaces" up briefly a couple times note it was using the Natty "Purple Splotch" background and not the background on the screen.  "Workspaces" stopped working when I started Firefox.

We'll see what the next daily build brings.

Jerry

---

### Post by jerrylamos on 2011-06-08
Compaq 3.33 GHZ radeon xpress 200 is quite happy to run Unity 3D.

8 June Daily Build Live all the launchers and the BFB work.  See my previous posts, they don't all work on pc's that don't support Unity 3D.

Do note of course even on this Compaq Live is using Unity 2D.

Hmmmm.

Jerry

---

