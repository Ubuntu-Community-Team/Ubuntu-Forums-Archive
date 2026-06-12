---
title: "Unity (compiz?) broken."
date: 2011-08-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fillmont on 2011-08-07
Have been testing Alpha 3 the past few days. Things have been going well, until today. When I tried to log into regular Unity, I got a black screen, and an eventual "Compiz has suddenly shut down" error message. I selected the "restart program" option on the error message, but nothing happened. I wasn't able to bring up any sort of activity. I restarted, and now when I try to get into regular Unity, I get the desktop wallpaper, and a "full screen" nautilus. Where the global task bar should be, I get just a Nautilus task bar. 

Both Unity 2D and Gnome Shell are working fine.

Any thoughts?

---

### Post by fjgaude on 2011-08-07
Same for me but I'm sure the next update will fix this situation.

---

### Post by klim8 on 2011-08-08
The same is happening to me.

---

### Post by naga2raja on 2011-08-08
+1 for me too.. when I intall compizconfig-settings-manger and do some customization my entire panels got vanished only the Desktop screen appears.. Unable to get the global unity Menu. Then I logged in using Ubuntu classic (No effects).. even Uninstalling compiz doesn't restore my desktop..

---

### Post by x-shaney-x on 2011-08-08
Alpha 3 still working for me (and working VERY well I must say, to my suprise).

Before installing alpha 3 I did have an upgraded oneiric install which seemed to suffer the same problem as people here are describing.

In my case I deleted everything related to unity and compiz in my home folder (plus gconf stuff).
If home has nothing important, maybe try moving the home folder and see if everything works?

Failing that, have you all been altering things in ccsm?
If so, compare notes and see if a common setting is to blame.

---

### Post by brazov on 2011-08-08
Thank you for reporting the issue. I will wait a couple of days before upgrading.

Please also report when the problem is over! :-)

---

### Post by fillmont on 2011-08-08
> **x-shaney-x said:**
> Alpha 3 still working for me (and working VERY well I must say, to my suprise).

Agreed; before this most recent problem, Alpha 3 was doing very well. I was impressed.
> 
Before installing alpha 3 I did have an upgraded oneiric install which seemed to suffer the same problem as people here are describing.

In my case I deleted everything related to unity and compiz in my home folder (plus gconf stuff).
If home has nothing important, maybe try moving the home folder and see if everything works?

Failing that, have you all been altering things in ccsm?
If so, compare notes and see if a common setting is to blame.

The only edits I made in ccsm were related to opacity of the task bar and launcher, and adding mouseover zones for scale and to show desktop. 

I will say that upon mental review, I had changed the desktop background from one of the defaults to a different image. That was the last thing I had changed before turning off the machine and starting up again to find Unity/compiz broken.

---

### Post by jerrylamos on 2011-08-08
Easy fix.  Unity-2D.  

Doesn't use Compiz so doesn't get Compiz overhead.  Compiz churns away even though I'm running full screen applications.

Also, Unity-2D has nice sharp borders not the compute hungry fuzzy shading.  My eyes are blurry enough I don't need more.

Also I find "transparent screens" awfully hard to read.

Jerry

p.s.  Oh by the way, Compiz famous for bugs since Intrepid if not before.  Unity-2D doesn't get those bugs...

---

### Post by x-shaney-x on 2011-08-08
And the added bonus of 2d not stealing my 3 finger touchpad tap/middle-click the way compiz does.

Downside is there is no way to make the panel icons smaller and the old gconf settings to force the launcher to stay visible or the dash to stay full-screen no longer work :(

---

### Post by fillmont on 2011-08-08
> **jerrylamos said:**
> Easy fix.  Unity-2D.  

Doesn't use Compiz so doesn't get Compiz overhead.  Compiz churns away even though I'm running full screen applications.

Also, Unity-2D has nice sharp borders not the compute hungry fuzzy shading.  My eyes are blurry enough I don't need more.

Also I find "transparent screens" awfully hard to read.

Jerry

p.s.  Oh by the way, Compiz famous for bugs since Intrepid if not before.  Unity-2D doesn't get those bugs...

I've found that Unity 2D, for me, has had a lot more little bugs than Unity had before the current breakage. 

Metacity has also been flipping out on my lately. 

I'm using Gnome Shell now, as it is the most stable of the three desktop environments I have on Alpha 3.

---

### Post by brazov on 2011-08-09
> **fillmont said:**
> 
I'm using Gnome Shell now, as it is the most stable of the three desktop environments I have on Alpha 3.

I think that stability is not a criterion for passing a judgement on a software in alpha stage. By my experience, the default desktop of Ubuntu releases are the most stable and best supported.

@fillmont: still problems?

---

### Post by fillmont on 2011-08-09
> **brazov said:**
> I think that stability is not a criterion for passing a judgement on a software in alpha stage. By my experience, the default desktop of Ubuntu releases are the most stable and best supported.

@fillmont: still problems?

Oh, I know that stability and alpha aren't exactly synonymous. Just stating what I was using, I guess. I definitely didn't mean to seem to pass judgment at this stage. That said, I have been impressed by how stable this alpha release has been overall.

I updated through Shell, restarted, and Unity was back working again, so whatever had been broken was fixed. Pretty sweet stuff.

---

### Post by Noz3001 on 2011-08-09
I just got this after updating.

On the lightdm login screen, a duplicate "broken" Ubuntu session is there. Choosing the other "Ubuntu" session works for me.

---

### Post by internalkernel on 2011-09-23
Ahhhh... and for a second I thought I was alone out here in the wilds.

Compiz is thoroughly broken... It's okay, if you "accept the defaults" when you log in. Don't try to customize or change anything... don't even think about installing CCSM.

Judging by the start date of this thread, this issue has been around for a while. Are there any options are available? What if I don't want compiz with the unity "sauce"?

---

### Post by cariboo on 2011-09-23
> **internalkernel said:**
> Ahhhh... and for a second I thought I was alone out here in the wilds.

Compiz is thoroughly broken... It's okay, if you "accept the defaults" when you log in. Don't try to customize or change anything... don't even think about installing CCSM.

Judging by the start date of this thread, this issue has been around for a while. Are there any options are available? What if I don't want compiz with the unity "sauce"?

Try Unity 2D.

---

### Post by naikmanoj1991 on 2011-09-23
> **fillmont said:**
> Have been testing Alpha 3 the past few days. Things have been going well, until today. When I tried to log into regular Unity, I got a black screen, and an eventual "Compiz has suddenly shut down" error message. I selected the "restart program" option on the error message, but nothing happened. I wasn't able to bring up any sort of activity. I restarted, and now when I try to get into regular Unity, I get the desktop wallpaper, and a "full screen" nautilus. Where the global task bar should be, I get just a Nautilus task bar. 

Both Unity 2D and Gnome Shell are working fine.

Any thoughts?

Hey same problem here. In my system not only crash the CCSM but also other s/w too. Some one suggest me that wait for the few days...its bug.

---

### Post by cariboo on 2011-09-23
When I have an app that crashes compiz, or compiz itself crashes, it automagically restarts, and I continue on with what I'm doing.

---

### Post by internalkernel on 2011-09-23
> **cariboo907 said:**
> When I have an app that crashes compiz, or compiz itself crashes, it automagically restarts, and I continue on with what I'm doing.

I wish that were the case... however it's not. When compiz crashes, there is no restart... SegFault each and every time... with nothing that even resembles an error message. Resetting the defaults doesn't bring it back, deleting all .cache/compizconfig-1 .config/compiz-1 and .compiz-1 has in _some_ cases restored a default compiz... most times, it stays broken.

Unity 2D? I'll be honest I never considered using it since it doesn't support openGL; or am I wrong about that? If I'm going with a window manager that doesn't allow 3D effects, well, I'm going with Fluxbox... 

It's all just a tab bit frustrating since most of us have gotten very comfortable with compiz... I know I have over the years and compiz is more about productivity and functionality to me than bling. It just seems this last release of Ubuntu removed my ability to customize my desktop the way I want.

---

### Post by lucazade on 2011-09-23
> **internalkernel said:**
> Unity 2D? I'll be honest I never considered using it since it doesn't support openGL; or am I wrong about that? If I'm going with a window manager that doesn't allow 3D effects, well, I'm going with Fluxbox... 


Unity-2D started to support OpenGL/OpenGL ES from a couple of releases and it is based on QT4 libraries. You can enable with a dconf setting

```
gsettings set com.canonical.Unity2d use-opengl true

```
"Whether to render the graphics into an OpenGL viewport.  When set to false, the raster engine is used."

personally I haven't seen any noticeable difference with the backend enabled, still looking for some info about it.

---

### Post by cariboo on 2011-09-23
There a couple of things to keep in mind, the version of compiz we are using now is a complete rewrite, so it has very little in common with previous versions. As a matter of fact the main compiz developer was considering giving up on compiz, until he was hired by Canonical.

The lack of configuration options is due to the gnome developers thinking they know what is good for us :). The Ubuntu devs are giving us back some configurations options, up until a couple of weeks ago we couldn't even easily change themes with out installing gnome-tweak-tool, which depends on gnome-shell, so that would be installed too, even if we didn't want it.

Gnome 2 had a ten year run, which allowed developers all sorts of time to create configuration tools, I'm sure as time goes on developers will find itches that need scratching and give us a whole array of tools to configure the desktop the way we want it.

---

### Post by internalkernel on 2011-09-23
> **cariboo907 said:**
> Gnome 2 had a ten year run, which allowed developers all sorts of time to create configuration tools, I'm sure as time goes on developers will find itches that need scratching and give us a whole array of tools to configure the desktop the way we want it.

True true, the voice of reason... I've been chalking everything up to growing pains. At the end of the day I try not to over look what Ubuntu has done for the linux community at large. In hindsight this has been true with any major project and over time they have all surpassed their predecessors... kde4, being an example. I'm sure Ubuntu will as well; so... I won't whine much more... :D

---

