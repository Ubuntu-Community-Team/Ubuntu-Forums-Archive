---
title: "Is it just me or...."
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Rifester on 2011-08-12
Is Unity 2D a crap load better then Unity?   All of a sudden everything is more sharp, clear, and running stellar in Unity 2D.  Been running Unity since it's beginning and can't seem to understand this...

---

### Post by akand074 on 2011-08-12
I've only seen images of Unity 2D.. maybe I'll login to it and test it. But Unity seems to be slow and laggy since the new update. Still an alpha though, things aren't likely the way they are meant to be. We'll see as time progresses.

---

### Post by Johnb0y on 2011-08-12
> **akand074 said:**
> I've only seen images of Unity 2D.. maybe I'll login to it and test it. But Unity seems to be slow and laggy since the new update. Still an alpha though, things aren't likely the way they are meant to be. We'll see as time progresses.

+1 

:popcorn: while waiting... :D

---

### Post by Johnb0y on 2011-08-12
p.s. [akand074]("http://ubuntuforums.org/member.php?u=840786") loving the pic! epic! 

:KS for you! :P

---

### Post by Rifester on 2011-08-12
I have occasionally logged into 2D just for fun, but right now it seems to be running well and more polished.   Maybe just a weird point in development, I don't know, just found it interesting.

---

### Post by 3rdalbum on 2011-08-13
Funnily enough, I've been using Unity 2D too. On my desktop, if I use normal Unity it sometimes does something to the graphics card, and the computer won't boot up again until I take out the graphics card or leave the power supply turned off overnight.

Unity 2D is so similar to Unity 3D that I barely notice an operational difference, but it doesn't cause the graphics card problem.

---

### Post by t1497f35 on 2011-08-13
+1
Unity 2D is also more intuitive, i.e. the right-click menu in 2D over an item shows an option called "remove item" which is more straightforward than the confusing "Keep in Launcher" label with a checkmark in Unity 3D.

---

### Post by VinDSL on 2011-08-13
Maybe, it's better than it used to be.

I'll restart, and check it out.

---

### Post by VinDSL on 2011-08-13
Hrm...

Not too shabby!  ;)

The Launcher icons are gargantuan, and it only has 4 workspaces (I normally run 9) but... not bad.

Definitely consumes less memory.  CPU usage is about the same.

Hold on, let me run GtkPerf...

WoW!  Runs circles around Unity 3D!

```

GtkPerf 0.40 - Starting testing: Sat Aug 13 03:41:53 2011

GtkEntry - time:  0.07
GtkComboBox - time:  3.88
GtkComboBoxEntry - time:  3.07
GtkSpinButton - time:  0.23
GtkProgressBar - time:  0.21
GtkToggleButton - time:  2.13
GtkCheckButton - time:  0.29
GtkRadioButton - time:  0.44
GtkTextView - Add text - time:  1.44
GtkTextView - Scroll - time:  0.49
GtkDrawingArea - Lines - time:  1.53
GtkDrawingArea - Circles - time:  2.31
GtkDrawingArea - Text - time:  0.61
GtkDrawingArea - Pixbufs - time:  0.12
 --- 
Total time: 16.83

```

Unity 3D scores mid-20s these days, on this machine.

I'll bet this would be great on my netbook!

---

### Post by lucazade on 2011-08-13
> **VinDSL said:**
> Hrm...

Not too shabby!  ;)

The Launcher icons are gargantuan, and it only has 4 workspaces (I normally run 9) but... not bad.

Definitely consumes less memory.  CPU usage is about the same.

Hold on, let me run GtkPerf...

WoW!  Runs circles around Unity 3D!

```

GtkPerf 0.40 - Starting testing: Sat Aug 13 03:41:53 2011

GtkEntry - time:  0.07
GtkComboBox - time:  3.88
GtkComboBoxEntry - time:  3.07
GtkSpinButton - time:  0.23
GtkProgressBar - time:  0.21
GtkToggleButton - time:  2.13
GtkCheckButton - time:  0.29
GtkRadioButton - time:  0.44
GtkTextView - Add text - time:  1.44
GtkTextView - Scroll - time:  0.49
GtkDrawingArea - Lines - time:  1.53
GtkDrawingArea - Circles - time:  2.31
GtkDrawingArea - Text - time:  0.61
GtkDrawingArea - Pixbufs - time:  0.12
 --- 
Total time: 16.83

```

Unity 3D scores mid-20s these days, on this machine.

I'll bet this would be great on my netbook!

..and if you disable also the compositor manager (gconf-editor > /apps/metacity/preferences/compositor_manager false) you should gain more fps.
you'll lack real transparency but the netbook will fly, especially scrolling in ff and chromium.

---

### Post by VinDSL on 2011-08-13
> **akand074 said:**
> I've only seen images of Unity 2D...
Here's another one...  :D


[INDENT](Click to expand)

[[img]http://vindsl.com/images/Screenshot at 2011-08-13 03:55:38(650x520).png[/img]]("http://vindsl.com/images/Screenshot at 2011-08-13 03:55:38.png")[/INDENT]


Looks about the same as 3D, except for the icon size.

Okay, I'm gonna go play some online flash games, and see how they fare.  ;)

---

### Post by sgage on 2011-08-13
Can you rearrange the order of icons in the launcher now?

---

### Post by VinDSL on 2011-08-13
> **lucazade said:**
> ..and if you disable also the compositor manager (gconf-editor > /apps/metacity/preferences/compositor_manager false) you should gain more fps.
you'll lack real transparency but the netbook will fly, especially scrolling in ff and chromium.
I really need to update my netbook.  I'm running Mint 7 on it now, which was orphaned (like) a year or two ago.

I might try that tomorrow.  Thanks!  :)

---

### Post by VinDSL on 2011-08-13
> **sgage said:**
> Can you rearrange the order of icons in the launcher now?
I *think* it's simply picking up the order from my 3D install.

Dittos for the wallpaper, Conky config, et cetera.  ;)

---

### Post by lucazade on 2011-08-13
> **sgage said:**
> Can you rearrange the order of icons in the launcher now?

yes, you can
click and hold for 1 or 2 sec then you can move the launcher icon.

---

### Post by VinDSL on 2011-08-13
> **lucazade said:**
> yes, you can
click and hold for 1 or 2 sec then you can move the launcher icon.
Confirmed.

---

### Post by ratcheer on 2011-08-13
> **Rifester said:**
> Is Unity 2D a crap load better then Unity?   All of a sudden everything is more sharp, clear, and running stellar in Unity 2D.  Been running Unity since it's beginning and can't seem to understand this...

I wouldn't know. My system will not run Unity, only 2D. But yes, 2D is looking great.

Tim

---

### Post by Rifester on 2011-08-13
2D is definitely running better here...   Can you guys add new items to the Unity bar?   I cannot currently add new applications.

---

### Post by cgroza on 2011-08-13
> **Rifester said:**
> 2D is definitely running better here...   Can you guys add new items to the Unity bar?   I cannot currently add new applications.
Yes, just start your application, right click on it and select keep in launcher.

---

### Post by Rifester on 2011-08-13
I have a few applications that automatically go to full screen and can  not be minimized without closing the program.    I cannot find a way to  add them to the bar in the development version.

---

### Post by mc4man on 2011-08-13
> **Rifester said:**
> I have a few applications that automatically go to full screen and can  not be minimized without closing the program.    I cannot find a way to  add them to the bar in the development version.
I don't  use unity-2d that much but I believe it uses the same favorites list/settings as unity 3d
So 2 additional  choices to add to the launcher would be to use either gsettings or dconf-editor

(if you had a usable unity login then you could just login, find the .desktop(s) & drag onto the launcher
Then they should show up in 2d's launcher

---

### Post by d3v1150m471c on 2011-08-13
IMHO, simple is always better. no need for all the fancy graphics. see the blackbox link below ;-)

---

### Post by fjgaude on 2011-08-13
> **lucazade said:**
> ..and if you disable also the compositor manager (gconf-editor > /apps/metacity/preferences/compositor_manager false) you should gain more fps.
you'll lack real transparency but the netbook will fly, especially scrolling in ff and chromium.

Hi, Luca! compositing_manager false makes little difference with my Poulsbo box, 2D, 11.10, about 355 sec true 317 when false, using gtkperf. Now my main Intel i5 box does the 100-times tests in 12 seconds with false.

Just thought you might like to know!

---

### Post by x-shaney-x on 2011-08-13
I also think 2D is generally better.
And especially because it doesn't hijack my 3 finger tap like compiz does :)
Downside is not being able to change launcher size or make dash full-screen :(

---

### Post by fjgaude on 2011-08-13
> **x-shaney-x said:**
> I also think 2D is generally better.
And especially because it doesn't hijack my 3 finger tap like compiz does :)
Downside is not being able to change launcher size or make dash full-screen :(

Well, it all depends on your graphics driver, hardware. I can take the dash to full screen by clicking on the right, bottom widget of the lenses.

I can't yet use 3D on the Dell mini, but can on my main box, though I still run 11.04 until 11.10 is released, or the Beta is very stable.

---

### Post by x-shaney-x on 2011-08-13
> **fjgaude said:**
> I can take the dash to full screen by clicking on the right, bottom widget of the lenses.

Yes I can do that but I meant to keep it full-screen all the time rather having to click the widget every time.
I can keep it full screen in Unity 3D

---

### Post by fjgaude on 2011-08-13
> **x-shaney-x said:**
> Yes I can do that but I meant to keep it full-screen all the time rather having to click the widget every time.
I can keep it full screen in Unity 3D

Without being full-screen you cannot see all the icons?

---

### Post by x-shaney-x on 2011-08-13
Yes, I can see everything normally in either view.  I just prefer it to open full-screen :)

---

### Post by fjgaude on 2011-08-13
Okay, and I don't like it that Chromium always comes up full screen even when I set it to the size I wish. It does this when leaving its desktop and then coming back.

Well, likely as Oneiric matures many options more will be available to us.

---

### Post by akand074 on 2011-08-13
I had decided to go back to gnome-shell on release of Oneiric. But Unity is developing really well that I'm back to undecided. Even for low resource computers, Unity 2D is really very impressive. I guess I'll see by the late betas with Gnome 3.2. Very impressed. Luckily moving between gnome-shell and Unity is a matter of logout/login to new DE.

---

### Post by jerrylamos on 2011-08-13
Unity-2D doesn't use Compiz.  On -3D Compiz buzzes away using up processor cycles and memory even if I'm running applications full screen like right now.

Compiz chews up lots of resources with shading.  My eyes are fuzzy enough, I like nice sharp clear images like my digital photos.  -3D has fuzzy edges.

Unity-3D with Compiz does transparent windows which are very hard for my eyes to read.

So I put Unity-2D on my two test pc's that can run -3D, and also put it on my two test pc's where Compiz fancy code doesn't run.  I choose to actually install -2D instead of letting Ubuntu default.

I might add I don't like Mac's either, and keep finding ordinary things that are very hard for Mac to do.

Jerry

---

### Post by x-shaney-x on 2011-08-13
Well according to htop and gnome system monitor, gnome shell, unity 2d and unity 3d all use almost exactly the same amount of resources when checked on idle and with a web browser open with multiple tabs.

Though after using the laptop for over an hour I do see much bigger differences with compiz eating more memory over time.

The only compositing I need are shadows since it's much more pleasant and adds nicer separation between open windows and since I can do that in 2d I would be happy to stick with it.

---

### Post by VinDSL on 2011-08-13
> **jerrylamos said:**
> On -3D Compiz buzzes away using up processor cycles and memory even if I'm running applications full screen like right now.> **x-shaney-x said:**
> After using the laptop for over an hour I do see much bigger differences with compiz eating more memory over time.
I'm surprised nobody has started a new thread about this...

One of the updates I performed, in the past 48 hours, has caused a regression in Compiz.  It's back to chewing up resident memory mercilessly.

When I first booted up, Compiz was using 86M.  5 hours later, it's up to 130M, and it will keep climbing until I (ahem) restart Ubu.

Guess I'll go see if anybody has updated this long-standing bug in Launchpad.

---

### Post by t.rei on 2011-08-15
It's definately compiz what makes unity 2d so much better than unity. Compiz 0.9+ is just unstable, slow and buggy. Right now it decided to start segfaulting on me. Not reproducable, right now but always resulting in a "no keyboard-input and no focus" desktop, forcing me to reboot. Also, anything that uses 3d acceleration will have serious performance issues that are not around when using openbox, unity-2s, ... anything BUT COMPIZ.

I truely hope these severe issues get sorted out within the next 59? days. ;)

---

### Post by mc4man on 2011-08-15
> **t.rei said:**
> It's definitely compiz what makes unity 2d so much better than unity. Compiz 0.9+ is just unstable, slow and buggy. 

I truly hope these severe issues get sorted out within the next 59? days. ;)
I'd guess if compiz is going to be 'fixed' more likely will take 6+ months (you can also add unity-panel and probably lightdm to that mix

---

### Post by x-shaney-x on 2011-08-15
Compiz only seemed to go so flaky once it was paired with unity, never had trouble with compiz before.
I would be in favour of them dumping compiz but if it is to stay then unity preferences need to be taken out of CCSM and put into an application of it's own and installed by default.

Anyone who does install CCSM just to be able to change things in unity is going to be tempted to fiddle with other things which can render their desktop unusable at worst and at best just be faced with compiz crashing as soon as anything is altered.

That isn't just something for the future, that is something that needs to be sorted by 11.10 release in my opinion.

---

### Post by cariboo on 2011-08-16
Compiz was completely re-written for Natty, it is nowhere near the same as in previous versions. Sam was at the point where he was going to quit maintaining compiz, until he was hired by Canonical to redo it so that Unity could run as a plugin.

---

### Post by Harry33 on 2011-08-16
Very often the problems with compiz (slowness, stickyness, high CPU) are co-existing problems with proprietary drivers (but also with bad state open source drivers), all what is related to 3D.

In addition to that, mutter (metacity based) window managers also suffer slowness related to 3D.
Gnome-shell has very little 3D properties, but it still runs slower than gnome-panel (pure metacity).

---

### Post by cariboo on 2011-08-16
Speaking of memory usage, I see Alberto has removed GL from cairo again for us nvidia users.

---

### Post by fjgaude on 2011-08-16
> **cariboo907 said:**
> Speaking of memory usage, I see Alberto has removed GL from cairo again for us nvidia users.

Compiz memory useage, hmmm... in 11.04 it's been about 90 Mib, the same as in 11.10. I am using the integrated Intel video chip that's part of the Core i5 CPU. The memory doesn't change that much as shown in System Monitor, going from one desktop to another, with two browsers and a total of eight tabs open.

Issues are likely caused by the video drivers associated with ATI and Nvidia, eh?

Note: after playing around doing everything I could think of the memory for Compiz went up to 108 MBs.

---

### Post by lucazade on 2011-08-16
> **fjgaude said:**
> Compiz memory useage, hmmm... in 11.04 it's been about 90 Mib, the same as in 11.10. I am using the integrated Intel video chip that's part of the Core i5 CPU. The memory doesn't change that much as shown in System Monitor, going from one desktop to another, with two browsers and a total of eight tabs open.

Issues are likely caused by the video drivers associated with ATI and Nvidia, eh?

Note: after playing around doing everything I could think of the memory for Compiz went up to 108 MBs.

If I remember compiz should receive a dietary treatment removing a part of the default plugins and functions. I hope this will happen and could help to make compiz a lightweight window manager. Do we need another beryl?! :)

---

### Post by x-shaney-x on 2011-08-16
I vote branching it off as a unity thing (Compizity?) and do away with the more not so useful eyecandy plugins and maybe some of the different switchers etc.
Of course they would remain an installable option but I think a cut-down compiz is the way forward.

---

