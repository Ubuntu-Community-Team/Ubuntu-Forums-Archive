---
title: "no titlebar buttons in unity session"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-02
I found this bug report that matches what I am seeing. The titlebar buttons are not in unity 3d but they are in unity 2d and the other DE's. If you are also seeing this please add yourself to this bug.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/791081](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/791081)

Bill

---

### Post by kansasnoob on 2011-06-02
I "me-too"ed, commented, and subscribed.

I also added that bug# to the iso-tracker.

---

### Post by sparker256 on 2011-06-02
> **kansasnoob said:**
> I "me-too"ed, commented, and subscribed.

I also added that bug# to the iso-tracker.

Found another one against metacity package.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/791081](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/791081)

Bill

---

### Post by kansasnoob on 2011-06-02
So they may me dupes, I'll make a note of that.

BTW unity-2d is super buggy right now :)

You can review some of the bugs here:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

Just hover the pointer over the bug and it displays brief info, or click on it to see more.

Once alpha1 is released I'll bet a bunch of updates pour into the repos.

---

### Post by sparker256 on 2011-06-02
> **kansasnoob said:**
> So they may me dupes, I'll make a note of that.

BTW unity-2d is super buggy right now :)

You can review some of the bugs here:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

Just hover the pointer over the bug and it displays brief info, or click on it to see more.

Once alpha1 is released I'll bet a bunch of updates pour into the repos.
Yes there were dupes and this is the correct one that has been assigned to the Canonical Desktop Experience Team. Now I know it is a bug and will be fixed.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/791081](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/791081)

Bill

---

### Post by athenroy on 2011-06-02
I'm using 11.04, Classic Desktop and mine disappear if you click the little menu button on the opposite side of the window border.  Fortunately, a restart restores the Min, Max and close buttons.

---

### Post by cariboo on 2011-06-03
> **athenroy said:**
> I'm using 11.04, Classic Desktop and mine disappear if you click the little menu button on the opposite side of the window border.  Fortunately, a restart restores the Min, Max and close buttons.

If you aren't running Oneiric, this isn't the place to get help solving problems, please use the proper subforum.

---

### Post by VinDSL on 2011-06-03
You may, or may not believe this, but...

I haven't had titlebar buttons for 3-4 days, and...

I don't miss them at all!  IMO, it's an improvement.  LoL!

Maybe I'll continue running 'button-less'  :D

---

### Post by VinDSL on 2011-06-03
Oh... BTW...

When I lost my buttons, I noticed another strange thing.

I change my wallpaper frequently.  I store custom walls in ~/Pictures/Wallpaper.

Here's the weirdness...

The first time I choose a wallpaper, it works.  If I switch to another wallpaper, I can't return to ANY of the wallpapers that I've run previously.  I can't even rename the wall, or copy n' paste it, using a totally different name.

The only way I can switch back n' forth between (previously run) walls, is to move them to the wallpaper folder, in the system file area.

Heh!  Hope that makes sense...  :)

---

### Post by coffeecat on 2011-06-03
> **VinDSL said:**
> You may, or may not believe this, but...

I haven't had titlebar buttons for 3-4 days, and...

I don't miss them at all!  IMO, it's an improvement.  LoL!

Maybe I'll continue running 'button-less'  :D

I have bad news for you! :) If you run the Alpha 1 live you get titlebar buttons back again. Which is odd because my hard drive installation fully updated to the time when the alpha 1 ISO was created still doesn't have buttons. I'll install alpha1 to a spare partition later and take special note as to whether I get buttons or not.

---

### Post by sparker256 on 2011-06-03
> **coffeecat said:**
> I have bad news for you! :) If you run the Alpha 1 live you get titlebar buttons back again. Which is odd because my hard drive installation fully updated to the time when the alpha 1 ISO was created still doesn't have buttons. I'll install alpha1 to a spare partition later and take special note as to whether I get buttons or not.
You have alpha 1 with unity 3d and have titlebar buttons? I know that they are in unity 2d and gnome but not in unity 3d.

Bill

---

### Post by coffeecat on 2011-06-03
> **sparker256 said:**
> You have alpha 1 with unity 3d and have titlebar buttons? I know that they are in unity 2d and gnome but not in unity 3d.

Bill

Good point. Sorry for the misinformation. I'd forgotten that the live CD is defaulting itself to Unity 2d. If I log out (by killing the xserver with AltGr-Print-k) and in again choosing "Ubuntu" to get the 3d desktop in the live session, I don't get buttons after all.

I do get, "Sorry, the program <*whatever*> closed unexpectedly" though. :)

---

### Post by jfernyhough on 2011-06-03
Looks like this is a Compiz issue as I have the same thing, but with GNOME3 fallback + Compiz. Both Metacity and Mutter are fine (well, at least in terms of window buttons :D).

---

### Post by VinDSL on 2011-06-03
> **coffeecat said:**
> I have bad news for you! :) If you run the Alpha 1 live you get titlebar buttons back again. Which is odd because my hard drive installation fully updated to the time when the alpha 1 ISO was created still doesn't have buttons. I'll install alpha1 to a spare partition later and take special note as to whether I get buttons or not.
Heh!  I'm still running a patched & mod'ed Natty Alpha 1 install.  :D

I'm curious to see how long it will tolerate UbuOO updates, before it borks.

If it doesn't totally break by Beta 1, I'll switch over then.

Put another way, I have no interest in ISO testing, you know?  ;)

---

### Post by seeker5528 on 2011-06-03
> **VinDSL said:**
> Oh... BTW...

When I lost my buttons, I noticed another strange thing.

I change my wallpaper frequently.  I store custom walls in ~/Pictures/Wallpaper.

Here's the weirdness...

The first time I choose a wallpaper, it works.  If I switch to another wallpaper, I can't return to ANY of the wallpapers that I've run previously.  I can't even rename the wall, or copy n' paste it, using a totally different name.

That's a Gnome 3 thing, if you use the gnome-control-center background applet it only knows about the system wide wallpaper directory and your pictures directory, and it doesn't look recursively so for those of us who like to keep stuff organized it doesn't work.

The option to set the background in Nautilus seems to be MIA at the moment but if you open the wallpaper in EOG aka 'image viewer' and set the background from there that works and it gives you the option to 'open background preferences' so you can switch between zoom, stretch, scale, etc...

Later, Seeker

---

### Post by cariboo on 2011-06-03
If you click the + sigh in the lower left, you can navigate to the directory that your wallpapers are located in. See the screen shot.

---

### Post by VinDSL on 2011-06-04
> **cariboo907 said:**
> If you click the + sigh in the lower left, you can navigate to the directory that your wallpapers are located in. See the screen shot.
Yep, exactly!

The thing is, with any walls that I've previously used, the "Open" button is ghosted-out, thus it cannot be selected.

I have to copy the previously used walls to ~/usr/share/backgrounds, if I want to re-use them.  ;)

Here's a screenie showing the ghosted "Open" button, and titlebar sans buttons...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-3-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-jun-2011.png")[/INDENT]


I kinda like the button-less titlebars.  :)

---

### Post by cariboo on 2011-06-04
I'm running a fresh alpha 1 install, the button is active on my setup

---

### Post by seeker5528 on 2011-06-04
> **VinDSL said:**
> The thing is, with any walls that I've previously used, the "Open" button is ghosted-out, thus it cannot be selected.

Looks like the recent versions bring back something resembling the 2.x.x functionality.

Anything from outside of the Pictures folder that you have previously set as a background will show up when you switch to the 'Pictures Folder' view so having a grayed out open button when you are adding additional backgrounds is actually an improvement over 2.x.x.

I had to open the file manager and look to make sure no file organization was actually being harmed during the making of this movie. :p

Later, Seeker

---

### Post by scradock on 2011-06-04
> **seeker5528 said:**
> Looks like the recent versions bring back something resembling the 2.x.x functionality.

Anything from outside of the Pictures folder that you have previously set as a background will show up when you switch to the 'Pictures Folder' view so having a grayed out open button when you are adding additional backgrounds is actually an improvement over 2.x.x.

I had to open the file manager and look to make sure no file organization was actually being harmed during the making of this movie. :p

Later, Seeker

Curious - I installed afresh on May 29th, just before alpha1, and have kept updated since. I get the + active in both Pictures Folder and Wallpapers mode....

Must check how it is in my updated-upgraded-from-Lucid version of Oneiric...

---

### Post by VinDSL on 2011-06-04
> **seeker5528 said:**
> I had to open the file manager and look to make sure no file organization was actually being harmed during the making of this movie. :p
LoL!

I seem to be having a hard time describing this problem - maybe I should make a movie and put it on YouTube. :D

[LIST]
[*]The walls work fine, if they're in ~/usr/share/backgrounds


[*]The walls cannot be used more than once, if they're in ~/home


[*]The "Open" option is not ghosted in ~/usr/share/backgrounds once you use a wall - you can switch back n' forth between any & all walls freely.


[*]The "Open" option remains ghosted in ~/home, once you use a wall.  And, once you use a wall, you cannot "Open" e.g. re-open it a second time, even if you change the filename, et cetera.
[/LIST]

---

### Post by seeker5528 on 2011-06-04
> **VinDSL said:**
> LoL!

I seem to be having a hard time describing this problem

I'm still confused.

When I choose a wallpaper there is no open dialog, just thumbnails of wallpapers the background applet knows about either in the 'Wallpaper' view or the 'Pictures Folder' view.

These are the pictures that physically exist in my pictures folder

[img]http://home.comcast.net/~seeker5528/Screenshot-GB1.png[/img]

If I browse for additional wallpapers to use and choose one I have already added it looks like this

[img]http://home.comcast.net/~seeker5528/Screenshot-GB2.png[/img]

But it's not so bad that I can't 'open' a previously added wallpaper because when I switch to the 'Pictures Folder' view it remembers the wallpapers I have added from other locations and lets me choose any one of them.

[img]http://home.comcast.net/~seeker5528/Screenshot-GB3.png[/img]

This is more or less the way it worked in Gnome 2.x.x, but I don't remember in Gnome 2.x.x having any indicator that you had already added the wallpaper.

I guess the next question would be if you could select multiple wallpapers to add at once as you could in Gnome 2.x.x. Yep, you can.

Later, Seeker

---

### Post by jerrylamos on 2011-06-05
BFB doesn't show at the top left here inn daily build 5 June .iso Live, but clicking where it should be works.  No big deal just curious.

Buttons at top right such as shutdown are there but very very faint.

Windows such as Home Folder etc. have no buttons but Alt-F4 works so I'm O.K.

"persistent" is also working but may take a couple boots to straighten out with a new daily build.

Haven't found any new bugs lately (see Alpha Release Notes for known bugs) on three test pc's, just things that haven't been implemented yet.

Certainly is quick to do a zsync and boot .iso Live persistent for checking what's happening in latest daily build.  

I'm avoiding install for the moment having been burned with Natty Narwhal, and Alpha level install plus updates gets screwed up sooner or later.

Enjoy.

Jerry

---

### Post by sparker256 on 2011-06-06
This appears to be fixed so I have marked it solved.

Bill

---

### Post by VinDSL on 2011-06-07
> **sparker256 said:**
> This appears to be fixed so I have marked it solved.

Bill
Yep!

Me titlebar buttons are back, too!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-7-jun-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-jun-2011(2).png")[/INDENT]


I really preferred it without the titlebar buttons, but... whatever.

No reason to get too experimental...

---

### Post by sparker256 on 2011-06-07
> **VinDSL said:**
> Yep!

Me titlebar buttons are back, too!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-7-jun-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-jun-2011(2).png")[/INDENT]


I really preferred it without the titlebar buttons, but... whatever.

No reason to get too experimental...

You have them on the wrong side but that is just me.  :D

Ps. I did also want to thank you for your examples of what can be done with conky.

Bill

---

### Post by jerrylamos on 2011-06-07
> **sparker256 said:**
> This appears to be fixed so I have marked it solved.

Bill

Not fixed on my newer faster pc with 6 June daily build..  

6 June did have x-[] buttons on my netbook and my older Thinkpad T40.

?

I'm zsync'ing 7 June now.  Wonder what's new/fixed/broken on it.

Jerry

BTW I prefer the x-[] on the top right....

---

### Post by sparker256 on 2011-06-07
> **jerrylamos said:**
> Not fixed on my newer faster pc with 6 June daily build..  

6 June did have x-[] buttons on my netbook and my older Thinkpad T40.

?

I'm zsync'ing 7 June now.  Wonder what's new/fixed/broken on it.

Jerry

BTW I prefer the x-[] on the top right....

There is a newer version of compiz. If I remember there was a 060611 in the name and I will give the exact package as soon as I am done installing qtcreator.

```

compiz (1:0.9.4+bzr20110606-0ubuntu2) oneiric; urgency=low

  * debian/rules, debian/compiz-gnome.install:
    - generate g-c-c keybindings from new metacity package
    - don't generate schema for gconf bindings, not sure we will ship them or
      should switch to gsettings

 -- Didier Roche <didrocks@ubuntu.com>  Mon, 06 Jun 2011 17:58:54 +0200

compiz (1:0.9.4+bzr20110606-0ubuntu1) oneiric; urgency=low

  * New bug fix release:
    - Switcher window borders are not properly unmapped with
      (unity|gtk)-window-decorator (LP: #789580)
    - maximized window is displaced (LP: #772612)
    - Unity launcher gets visible while screensaver is active (LP: #771391)
    - 1 pixel icons in notification-area-applet when compiz is the windows
      manager (LP: #767095)
  * debian/patches/00_bzr_fix_apps_without_startupid.patch:
    - removed: upstream

 -- Didier Roche <didrocks@ubuntu.com>  Mon, 06 Jun 2011 16:18:08 +0200

compiz (1:0.9.4+bzr20110415-0ubuntu2) natty; urgency=low

  * debian/patches/00_bzr_fix_apps_without_startupid.patch:
    - from upstream trunk, fix crash on applications removing _NET_STARTUP_ID
      (LP: #759363)

 -- Didier Roche <didrocks@ubuntu.com>  Tue, 19 Apr 2011 11:40:43 +0200

```
Bill

---

### Post by jerrylamos on 2011-06-07
7 June daily build Live the buttons are back on all four of my test pc's ranging from new to years old.

Depending on the video card some things are a little flaky like the BFB on this radeon xpress 200 isn't visible but works.  This video runs 3D fine but of course with the Live it is running 2D.  The BFB is visible on my three other pc's.

Well, it works, so I'm O.K.

Jerry

---

