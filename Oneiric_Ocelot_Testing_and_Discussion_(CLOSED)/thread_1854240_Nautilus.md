---
title: "Nautilus"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dFlyer on 2011-10-04
Any body know of a fix for nautilus? Any time I launch nautilus (home) folder and click on a sub folder it crashes and does present a screen for a crash report?

---

### Post by alphacrucis2 on 2011-10-04
> **dFlyer said:**
> Any body know of a fix for nautilus? Any time I launch nautilus (home) folder and click on a sub folder it crashes and does present a screen for a crash report?

I am getting that. Seems to have started with recent updates though I don't recall an update to nautilus itself. Also seems to be inconsistent. Sometimes it will work and other times not.


I decided to try running it from the terminal. I get this error message when nautilus crashes:

```
Segmentation fault (core dumped)
```

---

### Post by binary00mind on 2011-10-04
> **dFlyer said:**
> Any body know of a fix for nautilus? Any time I launch nautilus (home) folder and click on a sub folder it crashes and does present a screen for a crash report?As with all releases while updating things could change in a hurry. 
Install debugging symbols (unless you already did) 

Plus there obviously could be a real bug issue, sent the automated crash report to developers. 

Out of curiosity you did not change any permissions to that subfolder?
Also go to launchpad and report as a bug (first cross reference if there is a similar issue with an existing bug#)

As long as I use Nautilus I've never had an issue as described by you. 

And last but not least, do you have installed Nautilus scripts & script manager? They can be buggy quite often. 

Meantime install KDE Krusader, the king of file managers (plus all the (not mandatory) dependencies

---

### Post by dFlyer on 2011-10-04
> **alphacrucis2 said:**
> I am getting that. Seems to have started with recent updates though I don't recall an update to nautilus itself. Also seems to be inconsistent. Sometimes it will work and other times not.


I decided to try running it from the terminal. I get this error message when nautilus crashes:

```
Segmentation fault (core dumped)
```

I will have to agree. The recent updates over the past 2 days have made things fairly unstable. The rc is due in 2 days hope they can work this out soon. I also get the same seg fault from the command line.

---

### Post by egosum87 on 2011-10-04
Same problem. Follow these bugs:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865194)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865264](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865264)

Ciao

---

### Post by mc4man on 2011-10-04
see this thread, bug linked in it
Seems to affect some, others not at all. I'm fine here in this regard on an install of yesterday updated but have seem other breakdowns recently, many of an very  inconsistent nature.
[http://ubuntuforums.org/showthread.php?t=1853865](http://ubuntuforums.org/showthread.php?t=1853865)

(I've removed some of the issues here by switching dm's, others remain

---

### Post by VinDSL on 2011-10-04
Same problem here, with the latest updates (5 minutes ago) - Nautilus seg faults...

Yesterday, Nautilus was working like a champ, and I probably updated Oneiric every 3-4 hours (main server repo).  It didn't start 2 days ago (for me).

Just saying...

EDIT

Here are a couple of weird ones for you...

For the past few days, when I clicked on an empty desktop, it would say "Desktop" in the upper left corner of the upper panel.  It was a cute parlor trick.  This no longer happens now.

Also, when I moused-over the upper panel, a Nautilus menu would appear, e.g. Nautilus was controlling the desktop.  This no longer happens either.

Heh!  Nautilus is definitely broken...

---

### Post by alphacrucis2 on 2011-10-04
For me, removing package nautilus-open-terminal seems to have stopped the seg faults so far. Weird.

---

### Post by VinDSL on 2011-10-04
> **alphacrucis2 said:**
> For me, removing package nautilus-open-terminal seems to have stopped the seg faults so far. Weird.
More strangeness!

I checked, and that package wasn't installed on my system, sooo...

I searched Synaptic for anything that had to do with Nautilus, and reinstalled them.

Then, I did a repo refresh, and a bunch of Compiz updates came flooding in.  I installed them, and did another refresh.

Finally, I did a warm boot, and everything is working fine now:

[LIST]
[*]The cute little "Desktop" title is back, in the left corner of the upper panel.

[*]The Nautilus menu pops up, when I mouse-over the upper panel.

[*]And, I surfed all over the place in Nautilus, 5-6 directories deep, with no problem(s) whatsoever.
[/LIST]

Dang it. I was hoping for a little more of a challenge.  :D

I'm gonna go see if GS is working.  I noticed it was dead in the water, before the last round of updates and reinstalls.

Wish me luck!  ;)

EDIT

GS is still broken.  It tries to load.  The upper panel comes and goes, a few times, then... nothing but a wallpaper, Conky, and 100% CPU usage.  Something is looping.

Oh, well, Unity is working fine (for a while).  Guess that'll have to do for tonight.  :)

---

### Post by mgsfan on 2011-10-04
still crashing for me even after rebooting...GS works fine here have'nt tried to open naut in unity yet

era yes nautilus is crashing for me in GS it opens but whenever I choose a sub kaboom

---

### Post by VinDSL on 2011-10-04
> **mgsfan said:**
> still crashing for me even after rebooting...GS works fine here have'nt tried to open naut in unity yet
Er...

What's still crashing?  Nautilus is crashing in GS?!?!?

---

### Post by Psychobudgie on 2011-10-04
Also crashing here with a Segfault. Has been since yesterday intermittently but since this morning is doing it consistently.

Tried reinstalling Nautilus and updating to no avail. It is however working fine when in Gnome-Desktop which would suggest the issue is not completely with Nautilus.

---

### Post by don762003 on 2011-10-04
Turning off Ubuntu one worked for me. Just open terminal and type u1sdtool -q .

Strange bug, hopefully they will have it fixed soon. If you want to start Ubuntu one again just type u1sdtool -c

---

### Post by Harry33 on 2011-10-04
> **egosum87 said:**
> Same problem. Follow these bugs:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865194)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865264](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865264)

Ciao

Yes those bugs are about nautilus-open-terminal extension being installed.
Removing the extension is a workaround.

I do not have that extension and Nautilus is working just fine in all my three Oneiric setups, all up to date.
The latest updates being:  upstart 1.3-0ubuntu10 and tzdata 2011k-1.

---

### Post by don762003 on 2011-10-04
After the updates yesterday Nautilus would crash when I tried to open any folders.
Turns out turning off Ubuntu one would fix it.

Open terminal and type u1sdtool -q 

Now try to use nautilus.

To start Ubuntu one again type u1sdtool -c

After restarting Ubuntu one the problem persists.

Also I don't have nautilus-open-terminal installed and never have it appears.

---

### Post by VinDSL on 2011-10-04
> **don762003 said:**
> Strange bug [...]
There's more than meets the eye...

Since I posted above, Nautilus has crashed twice.  Logging out/in solved the problem both times.

A couple of minutes ago, I caught mono using 102% CPU.  Hello?!?!?

For all I know, Nautilus is crashing because mono is hogging all the resources.  LoL!

I have a *feeling* many things are at play here...

---

### Post by Harry33 on 2011-10-04
There are already two threads about this.

1) [http://ubuntuforums.org/showthread.php?t=1854240](http://ubuntuforums.org/showthread.php?t=1854240)

2) [http://ubuntuforums.org/showthread.php?t=1853865](http://ubuntuforums.org/showthread.php?t=1853865)

---

### Post by coffeecat on 2011-10-04
> **Harry33 said:**
> There are already two threads about this.

1) [http://ubuntuforums.org/showthread.php?t=1854240](http://ubuntuforums.org/showthread.php?t=1854240)

2) [http://ubuntuforums.org/showthread.php?t=1853865](http://ubuntuforums.org/showthread.php?t=1853865)

Indeed! Merged with the first.

---

### Post by mgsfan on 2011-10-04
removing ubuntu-one and everything todo with it has fixed the crashing for me so far..since I don't even use it

---

### Post by philinux on 2011-10-04
Just updated via chroot and booted in. There was an update to nautilus-share package.

Nautilus fine here.

---

### Post by SpEcIeS on 2011-10-04
Problem still persists, even after reinstallation of nautilus and complimentary packages. Waiting for next package update ...

---

### Post by CaptainMark on 2011-10-04
i can say the problem is not related to the nautilus-open-terminal package, im getting the crash everytime on a fresh reformatted install

---

### Post by cor2y on 2011-10-04
Disable or close the ubuntuone client/deamon and that solves the problem.
Its an ubuntu one related issue it looks like.

---

### Post by SpEcIeS on 2011-10-04
> **cor2y said:**
> Disable or close the ubuntuone client/deamon and that solves the problem.
Its an ubuntu one related issue it looks like.

This does not seem to reflect on my rig. Created a fresh test account, without using UbuntuOne, and nautilus still crashes. Still waiting for updates ...

Edit:

**killall ubuntuone-syncdaemon** did do the trick, head a brain fart earlier. ;)

Latest update fixed the issue.

---

### Post by RPG Master on 2011-10-04
I just want to confirm that killing Ubuntu One worked for me too.

---

### Post by Harry33 on 2011-10-04
There are fixed updates for Nautilus crash issue in Launchpad now,
both nautilus-open-terminal and ubuntuone-client-gnome are updated:

- ubuntuone-client-gnome (2.0.1-0ubuntu1):
[https://launchpad.net/ubuntu/oneiric/+source/ubuntuone-client-gnome/2.0.1-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/ubuntuone-client-gnome/2.0.1-0ubuntu1)

- nautilus-open terminal (0.19-1build1):
[https://launchpad.net/ubuntu/oneiric/+source/nautilus-open-terminal/0.19-1build1](https://launchpad.net/ubuntu/oneiric/+source/nautilus-open-terminal/0.19-1build1)

---

### Post by ioca100 on 2011-10-04
After updates it works fine.Thank you.

---

### Post by professor76 on 2011-10-05
Didn't work for me. I had to remove nautilus-open-terminal again.

---

### Post by 1roxtar on 2011-10-05
My Nautilus has been furiously crashing, as well.  I thought it was just a Compiz problem, but it crashed using Unity 2D also.  I hope this gets fixed quickly.

---

### Post by Sennaista on 2011-10-05
Same here. I thought the recent updates had solved the issue but I was wrong.

---

### Post by dino99 on 2011-10-05
purge *ubuntuone* packages & related ones

---

### Post by Bowmore on 2011-10-05
Well, you just need to remove either nautilus-open-terminal or ubuntuone-client-gnome to make nautilus work, thus not the whole ubuntuone kit.

---

### Post by nicolasdiogo on 2011-10-05
try upgrading libc-bin

that was causing errors - according to the 'report crash tool'

but i have also un-installed extensions

---

### Post by VinDSL on 2011-10-06
You guys still having problems?!?!?

Talk is cheap.  Here's yet another screenie...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-6-oct-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-6-oct-2011.png")[/INDENT]


As you can see, I'm six branches deep with two UbuOne accounts bookmarked.

Everything is working fine here, and I'm not doing anything special...

---

### Post by don762003 on 2011-10-06
Everything seems to be working fine after the last updates. Although unity crashed and I had to restart.

---

### Post by SATA on 2011-10-06
> **VinDSL said:**
> You guys still having problems?!?!?

Talk is cheap.  Here's yet another screenie...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-6-oct-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-6-oct-2011.png")[/INDENT]


As you can see, I'm six branches deep with two UbuOne accounts bookmarked.

Everything is working fine here, and I'm not doing anything special...

I want your status monitor! :D

---

### Post by alphacrucis2 on 2011-10-06
> **SATA said:**
> I want your status monitor! :D

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

### Post by SATA on 2011-10-06
Yeah i got it. Tweaking it as we speak :)

I cant wait until I can re-install nautilus-open-terminal again without it crashing on me every time =/

---

### Post by SpEcIeS on 2011-10-06
The nautilus-open-terminal package is not causing any problems on this rig, so it is safe to install now. All is back in balance again. ;)

---

### Post by mc4man on 2011-10-06
> **SpEcIeS said:**
> The nautilus-open-terminal package is not causing any problems on this rig, so it is safe to install now. All is back in balance again. ;)
That may depend on what image one installed from, at least here any install prior to 10/02 _never_ had any conflict between n-o-t & the gnome client package, installs from 10/03 did & still do

Don't use ubuntuone but the removal of the ubuntuone-client-gnome packages allows n-o-t & nautilus to work, don't know if the client is totally needed for using ubuntuone


You can also do an open terminal from nautilus-actions though n-a has yet to be rebuilt for gtk3 so atm  needs to be built locally (3.1.4 source

---

### Post by SpEcIeS on 2011-10-06
Very insightful. :) This was not even considered on my behalf. The install on this rig was of the first beta class and has been running pretty fair.

---

### Post by drs305 on 2011-10-07
I have a completely updated oneiric and as of a few minutes ago nautilus continued to crash. Uninstalling *ubuntuone-client-gnome* fixed things for me.

---

### Post by CaptainMark on 2011-10-08
anyone noticed weve returned to the old mid alpha behaviour of when you open the launchers home folder it doesnt focus on the icon you just clicked but creates a new icon in the launcher, this used to bug me something chronic and has been gone for ages but now seems to be back

---

### Post by mc4man on 2011-10-08
> **CaptainMark said:**
> anyone noticed weve returned to the old mid alpha behaviour of when you open the launchers home folder it doesnt focus on the icon you just clicked but creates a new icon in the launcher, this used to bug me something chronic and has been gone for ages but now seems to be back
No - not really
Are you using a modified nautilus-home.desktop & if so where is it located.

 I have seen this happen upon occassion in the past when using a modded nautilus-home.desktop, pretty easy to fix (usually

---

### Post by CaptainMark on 2011-10-08
no i havent modified it

---

### Post by mc4man on 2011-10-08
> **CaptainMark said:**
> no i havent modified it
Don't really know then - 

You could try removing the Home folder (nautilus) icon from the launcher & then logging out/in.
When back in open the dash > more apps > installed
Find & drag the 'Home Folder' icon on to the launcher & see...

---

### Post by SpEcIeS on 2011-10-08
Nautilus periodically crashes on this rig, but not as often as last week.

---

### Post by Sennaista on 2011-10-09
Still not working properly. I usually can't even get it to run.

---

### Post by SpEcIeS on 2011-10-09
> **Sennaista said:**
> Still not working properly. I usually can't even get it to run.

Have you tried running nautilus in a fresh new account?

---

### Post by ksamuel on 2011-10-11
I tested both solution:

- killing ubuntuone doesn't solve the crashes, but does speed nautilus browsing of an order of magnitude
- removing open-terminal extensions does solve the problem if you run nautilus -q right after

---

### Post by GlennLChugg on 2011-10-11
I have found if I have 2 nautilus windows open and middle click/hold to drag a file from one window to another I will crash nautilus 1/4 times (especially if my HDD's are sleeping), what I do notice is that when it's going to work Unity will fade darker to indicate that the file can't be dragged/dropped on the Launcher bar, but this doesn't happen when it's going to crash.

---

### Post by tjeremiah on 2011-10-11
does anyone know how to change the background of any open folder?

---

### Post by SpEcIeS on 2011-10-11
Nautilus periodically crashes on first log in, but seems somewhat stable after.

---

