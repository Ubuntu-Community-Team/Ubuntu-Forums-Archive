---
title: "JOY!   CCSM Unity Plugin, &quot;automaximize_value&quot;"
date: 2011-06-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-06-24
Anyone notice - You can change the "Automaximize value" in CCSM's Unity Plugin now (Unity 3D 4.0.1)?


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-24-jun-2011(3)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-jun-2011(3).png")[/INDENT]


YES!!!  :D

I've been waiting for this feature, ever since Natty Alpha-1.

This allows you to set the minimum window size at which auto-maximize is triggered.

The default setting is "75", which is too small IMO.  "80" is optimal, for my rig.

Check it out!

---

### Post by lucazade on 2011-06-24
Good news..
there was a never ending bug report about it.

---

### Post by VinDSL on 2011-06-24
> **lucazade said:**
> Good news..
there was a never ending bug report about it.
Truthfully, this was the only thing that "bugged" me about Unity.

On my desktop: Launcher is on the left - Conky is on the right - and everything else is in between (resized).

The problem was, with a default "automaximize_value" of 75% I was constantly having to resize my windows.  

If I was off by "a hair", they would re-open in full-screen mode.

Grrr...

At 80%, life is good! :D


**_EXAMPLE_**


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-24-jun-2011(4)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-jun-2011(4).png")[/INDENT]


This is where I spend most of my time.

If I didn't leave a space between the browser and the Launcher, Panel, Conky, or the bottom of the screen - the next time I opened Chromium, it would be in full-screen - requiring a resizing.

Anyway, this is going to be GREAT!

---

### Post by Rasa1111 on 2011-06-24
cool!
Nice conky. :)
Sweet wall!
got a link to it?

---

### Post by VinDSL on 2011-06-24
> **Rasa1111 said:**
> cool!
Nice conky. :)
Sweet wall!
got a link to it?
Thanks!  ;)

The Conky data dump is in my sig (HOWTO).

I'm on the trot right now.

I'll give you the link to the wall, when I get home.

**[COLOR="DarkOrange"]2 HOURS LATER[/COLOR]**...

Here's the wall:  [http://www.wallpaperstop.com/3d-wallpaper/fantasy-wallpaper/3d-wallpaper-download-1005023.html](http://www.wallpaperstop.com/3d-wallpaper/fantasy-wallpaper/3d-wallpaper-download-1005023.html)

Tricks n' Tips:  I (almost) always download the highest res available, and Gimp it...

---

### Post by Rasa1111 on 2011-06-25
ah thanks very much Vin! <3

---

### Post by VinDSL on 2011-06-25
My pleasure!

"Wall Boys" gotta hang...  :D

---

### Post by fjgaude on 2011-06-25
Thanks, VinDSL... that wallpaper is truly awesome!

---

### Post by VinDSL on 2011-06-25
> **fjgaude said:**
> Thanks, VinDSL... that wallpaper is truly awesome!
You're welcome!

Those wall colors gel well with UbuOO.

Looks awesome in Expo (Workplace Switcher) also...  ;)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-25-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-jun-2011.png")[/INDENT]

---

### Post by SwedishWings on 2011-08-04
I love to have this feature, i just hate Unity's way of messing around with my windows. 

Were did you find this update? I have latest updates of 11.04, but can't see that setting in CCSM.

Btw, awesome background!

EDIT: Just realized that your post referred to Unity 4.01, and i have version 3.8.16. Is there a PPA were i can get 4.01 binaries?

Regards,
Mike

---

### Post by VinDSL on 2011-08-04
> **SwedishWings said:**
> EDIT: Just realized that your post referred to Unity 4.01, and i have version 3.8.16. Is there a PPA were i can get 4.01 binaries?
I'm running 4.6.0 in UbuOO now.

Here's the linkage:  [https://launchpad.net/ubuntu/+source/unity](https://launchpad.net/ubuntu/+source/unity)

Looks like you're using the latest version for Natty.

I'm not sure if 4.6.0 would work in Natty (or not) and I don't have any way of testing it, so...

Caveat emptor!  ;)

---

### Post by mc4man on 2011-08-04
> **SwedishWings said:**
> 

EDIT: Just realized that your post referred to Unity 4.01, and i have version 3.8.16. Is there a PPA were i can get 4.01 binaries?

Regards,
Mike
You will not be able to use O's unity build in natty, but you can take care of this quite simply if you build natty's  unity source or wait and see if a future natty update has this which is possible.

To apply the commit to create the option would be a bit of work and somewhat unnecessary, myself see no real value, I'd just raise the threshold, which is a 1 line edit, to what works for you, 0.90 would probably  do 
(the current hard coded is 0.75 as seen here, all that needs editing is the blue
#define COVERAGE_AREA_BEFORE_AUTOMAXIMIZE 0.[COLOR="Blue"]75[/COLOR]

One advantage to building in natty is one could apply a more  interesting commit that was rejected, mainly on design. I use it here with no issue
It gives you the option to minimise any windows of a group by left clicking on the launcher icon 
It's done as an option so can be used or not. (screen

If you want to build I have a patch set that will add the min. icon function and raise the max window threshold as desired

---

### Post by lucazade on 2011-08-04
> **mc4man said:**
> 
One advantage to building in natty is one could apply a more  interesting commit that was rejected, mainly on design. I use it here with no issue
It gives you the option to minimise any windows of a group by left clicking on the launcher icon 
It's done as an option so can be used or not. (screen

If you want to build I have a patch set that will add the min. icon function and raise the max window threshold as desired

I'd like to try your patch because I'm still not happy with current behaviour of minimizing windows
 only from windeco button and the bug repo seems stagnant.
Unfortunately I'd use it also on unity-2d but maybe looking at your code I could find inspiration
 and respective lines also in this version. :)

---

### Post by mc4man on 2011-08-04
> **lucazade said:**
> I'd like to try your patch because I'm still not happy with current behaviour of minimizing windows
 only from windeco button and the bug repo seems stagnant.
Unfortunately I'd use it also on unity-2d but maybe looking at your code I could find inspiration
 and respective lines also in this version. :)
It's not mine - just made into patch and adjusted some line #'s (could track down the commit and comments if interested
Did adjust for the 4.0+ unity in O, but 4.2 brought many changes and was no longer worth figuring out (the orig. author likely could but i think he was only interested in an official path

(- for natty's current source quite easy - the rules file is already set to patch (quilt) so I just put the attached folder in the debian folder, up the changelog (+nmu1) and use debuild
 (dpkg-buildpackage -rfakeroot -D -us -uc

Not sure if any value for 2d, obviously have tested on natty

---

### Post by lucazade on 2011-08-04
> **mc4man said:**
> It's not mine - just made into patch and adjusted some line #'s (could track down the commit and comments if interested
Did adjust for the 4.0+ unity in O, but 4.2 brought many changes and was no longer worth figuring out (the orig. author likely could but i think he was only interested in an official path

(- for natty's current source quite easy - the rules file is already set to patch (quilt) so I just put the attached folder in the debian folder, up the changelog (+nmu1) and use debuild
 (dpkg-buildpackage -rfakeroot -D -us -uc

Not sure if any value for 2d, obviously have tested on natty

cool.. going to try :)
thanks for sharing it.. I'll see what i'm able to take out of it.

---

### Post by mc4man on 2011-08-04
another quite different means of min.'ing windows (all on a ws) is this compiz plugin "showdesktop', ( again compiz

Don't know what it's dev plans are, if any, though found interesting.
The only direction i actually liked for unity was down.
Also had this odd effect of creating a sorta ghost like window list
 ( though by no means one
Have a post on here
[http://ubuntuforums.org/showthread.php?p=11087047](http://ubuntuforums.org/showthread.php?p=11087047)

---

### Post by tekstr1der on 2011-08-04
@mc4man: Is the patch you used for window minimization the one created by Marco Biscaro from Launchpad Bug #733349: [Minimize Application's Windows upon clicking its Launcher Icon]("http://https://bugs.launchpad.net/ayatana-design/+bug/733349")?

I've been meaning to apply this, being the single most annoying behavioral issue I've experienced with Unity, but was waiting for the Unity package to stabilize on Natty. I doubt there will be another revision landing via SRU, so I'm eager to apply this to the current 3.8.16. You said you'd adjusted for 4.0+ in oneiric. Will that have any bearing in natty if I apply your patch as is, or should I create the patch myself from his original trunk commit?

---

### Post by mc4man on 2011-08-04
> **tekstr1der said:**
> @mc4man: Is the patch you used for window minimization the one created by Marco Biscaro from Launchpad Bug #733349: [Minimize Application's Windows upon clicking its Launcher Icon]("http://https://bugs.launchpad.net/ayatana-design/+bug/733349")?

I've been meaning to apply this, being the single most annoying behavioral issue I've experienced with Unity, but was waiting for the Unity package to stabilize on Natty. I doubt there will be another revision landing via SRU, so I'm eager to apply this to the current 3.8.16. You said you'd adjusted for 4.0+ in oneiric. Will that have any bearing in natty if I apply your patch as is, or should I create the patch myself from his original trunk commit?

That's the one, the folder attached is for the current natty unity source (just extract, place in /debian folder and it will be patched if using debuild/dpkg... (needs quilt installed

As far as in O  - that's a different patch I did that worked  fine until about 4.2 where there were some significant changes in a couple of the files to be patched (I believe I did get 4.2 patched once for min, but broke scale so gave up (at that point past what I know or can figure out

I think it works just great on natty - was quite disappointed when the request to merge was whacked down solidly

---

### Post by tekstr1der on 2011-08-04
> I think it works just great on natty - was quite disappointed when the request to merge was whacked down solidly 

You and me both.

Thanks for the patch!

---

