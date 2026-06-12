---
title: "Help test the compiz prerelease!"
date: 2011-08-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by castrojo on 2011-08-18
I'm looking for some brave souls to test the latest compiz!

[http://www.omgubuntu.co.uk/2011/08/brave-compiz-prerelease-testers-wanted/](http://www.omgubuntu.co.uk/2011/08/brave-compiz-prerelease-testers-wanted/)

---

### Post by rburkartjo on 2011-08-18
okay i am game added the ppa

---

### Post by rbrick49 on 2011-08-18
ok castro I will give it a shot I cant break unity anymore than it is on my computer

---

### Post by lucazade on 2011-08-18
Is this bug already fixed?

"Don't use this PPA for another few hours. There's a crash on startup if you have certain windows open and fix for that is still stuck in the build queue" by Sam Spilsbury (the man behind compiz)

---

### Post by mc4man on 2011-08-18
Pretty much not testable here - causes an immediate 'nautilus' crash which results in unity plugin not loading properly (among other things

Unfortunately the crash points to this bug which a current issue in the default 11.10 and can be caused by any number of things randomly,  - nautilus, compiz, update-manager, synaptic, gdebi, ccsm, ect. ect. 
The .crash's are typically named after the failing process though all will go here - 
[https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/507062](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/507062)

At least here, with the normal compiz, a crash involving the above is pretty rare at this point, maybe once every few days if that. (a 'day' typically involves a dozen or more restarts

---

### Post by ventrical on 2011-08-18
> **castrojo said:**
> I'm looking for some brave souls to test the latest compiz!

[http://www.omgubuntu.co.uk/2011/08/brave-compiz-prerelease-testers-wanted/](http://www.omgubuntu.co.uk/2011/08/brave-compiz-prerelease-testers-wanted/)


Ok... I'm game. Lets fix this bug!

---

### Post by ventrical on 2011-08-18
Here's my first snapshot.

---

### Post by ventrical on 2011-08-18
> **castrojo said:**
> I'm looking for some brave souls to test the latest compiz!

[http://www.omgubuntu.co.uk/2011/08/brave-compiz-prerelease-testers-wanted/](http://www.omgubuntu.co.uk/2011/08/brave-compiz-prerelease-testers-wanted/)


I live one mile south of the Joe, across the river :)

Installed Compiz from the settings in the link, then, I got struck by lightning twice (POWER Outage).

 PC is OK .. but Compiz seems to be benign - won't do anything but ask to resolve dependencies .. etc..


Acer Aspire 3620

---

### Post by ventrical on 2011-08-18
I got the Zoom Desktop finally working. There are some awesome effects. Some of the plasmoid transparent screens come right through the plasmoids (sort of like a 3d effect) when you zoom in on an Icon.

I'll see if I can get a screen shot of this. I could never get it working with Natty... it kept busting.

---

### Post by ventrical on 2011-08-18
No screenshot but sent a bugreport.  The <super> key does not seem to be affected like it is in Unity 2D.

---

### Post by rbrick49 on 2011-08-18
so no compiz for me it tells me compiz held back

---

### Post by budluva04 on 2011-08-18
well this compiz ppa totally borked my laptop, crash upon login everytime, i lost unity and can't use my system, i'm having a hell of a time reverting these changes...anyone else with this problem?

---

### Post by rbrick49 on 2011-08-18
> **budluva04 said:**
> well this compiz ppa totally borked my laptop, crash upon login everytime, i lost unity and can't use my system, i'm having a hell of a time reverting these changes...anyone else with this problem?
all I am getting is a nautlis screen nothing no unity

---

### Post by rbrick49 on 2011-08-18
@budluva04 there is a problem with the 86x64 build it is saying on the website another day or two before compiz is ready for 86x64 systems

---

### Post by cariboo on 2011-08-18
> **budluva04 said:**
> well this compiz ppa totally borked my laptop, crash upon login everytime, i lost unity and can't use my system, i'm having a hell of a time reverting these changes...anyone else with this problem?

The easy way to revert is to use ppa-purge. You'll have to install ppa-purge in recovery mode, then run:

```
ppa-purge ppa:unity-team/compiz-testing
```

---

### Post by mc4man on 2011-08-19
Decided to try again after seeing the ppa had some unity packages also which didn't show before.
Initially no difference, basically compiz is running, window deco is borked and the unity plugin will not be enabled.
 To get semi-functional you need to get into ccsm, unset everything and then re-enable at least the basics & unity

At least up here, window placement is weird, the location bar is colored based on bg_select, the buttons don't function and the cursor is way off from where it 'clicks'

This is an interesting error - 
> libcompizconfig: dlopen: /usr/lib/compizconfig/backends/libgsettings.so: cannot open shared object file: No such file or directory
Will have to look for anything that is reportable

Edit - after a little fooling with - 
can't get the default window deco, there is degrading of 'action' buttons, (screen), not sure where changes made in ccsm are saved, gconf shows what I had previously, not currently,  cursor is way off and windows always open buried in panel
(switched to centered to stop that.

---

### Post by Xgen on 2011-08-19
Tested on a 64 bit system and everything seems normal here. Unity would not enable until I restarted the computer and then it requested to enable a bunch of plugins when I reenabled unity. As mentioned in previous posts, I also had to reset my compiz configurations. I don't notice anything different with my custom theme/icons.

---

### Post by x-shaney-x on 2011-08-19
Not sure what's going on here.
I'm on 64-bit and word was it would take a day or two sort out the packages right?
Well I just upgraded and all the compiz stuff was updated but still no unity or usable desktop running.
I still have gnome-shell running fine so I can login to that.
I hate to say it but it seems so typical of compiz these days

---

### Post by P-I H on 2011-08-19
Tried the new Compiz version with fglrx, Catalyst 1.8, activated. Got a crash directly after login. Reported this bug Bug #829574.

---

### Post by castrojo on 2011-08-19
> **P-I H said:**
> Reported this bug Bug #829574.

Hmm is this number right? I can't seem to find it.

---

### Post by hugmenot on 2011-08-19
Doesn’t work with classic session

```
$ compiz-decorator 
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
compiz (decor) - Warn: failed to bind pixmap 0x2000616 to texture
compiz (decor) - Warn: failed to create decoration for subproperty 0x8bf83e8 on window 0x15a
^Z
[4]+  Stopped                 compiz-decorator
$ bg
[4]+ compiz-decorator &
$ gcalctool 
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct

```

---

### Post by ventrical on 2011-08-19
Just got the major compiz update.

All well here .. working Unity,Unity 2D and gnome Shell.

Some interesting effects. Not as smooth as Linux Mint.

---

### Post by JerecDrak2 on 2011-08-19
I've just updated everything but when trying to log in to a Unity 3D session, all I get is the panel across the top with a Nautilus menu bar. There are no indicators at all in the panel and there's no dock. The Dash does not appear when pressing the super key either, all I can do is open a Nautilus window using the menu.

Are there any logs that I can post to a bug to help resolve this?

On a sidenote, everything works fine in an Ubuntu 2D session (not that I'd expect that to change since it doesn't use Compiz!)

---

### Post by SushiR on 2011-08-19
Got the same problems as mc4man, which is annoying, BUT when I sorted most of the issues out, compiz is now MUCH snappier than the older version. I'm running Oneiric on a Samsung N150 nebook if it is of any interest...

---

### Post by mc4man on 2011-08-19
> **JerecDrak2 said:**
> I've just updated everything but when trying to log in to a Unity 3D session, all I get is the panel across the top with a Nautilus menu bar. )
The most likely cause of that is that while compiz is running the unity plugin has been disabled
If you open ccsm you can enable it though it could require some patience to do so. (just stick it out, if need be do a log out/in and continue till at least the min. is enabled

---

### Post by JerecDrak2 on 2011-08-19
I managed to get a terminal open to get ccsm running and disabled/re-enabled Unity, but the animation plugin disabled itself and now I have no window decorations and all windows open in the top left corner.

I also tried running unity --reset (which was handy when things went wrong in Natty) but it just crashes. Hopefully an update will smooth some of this out!

---

### Post by P-I H on 2011-08-19
> **castrojo said:**
> Hmm is this number right? I can't seem to find it.

Now it should be OK.

---

### Post by mc4man on 2011-08-19
> **JerecDrak2 said:**
> I managed to get a terminal open to get ccsm running and disabled/re-enabled Unity, but the animation plugin disabled itself and now I have no window decorations and all windows open in the top left corner.

I also tried running unity --reset (which was handy when things went wrong in Natty) but it just crashes. Hopefully an update will smooth some of this out!
Then go just back into ccsm and enable things you need like window deco, place, move  ect.

What can prove useful in these cases if you have a good idea what should be enabled and any possible conflicts is in ccsm to go 
preferences > plugin list, disable auto plugin sorting and enable/disable as you see fit.
When done re-enable the auto plugin sorting and wait out the compiz reset. (or after a few just do a log out/in

When auto sorting is disable compiz will remain stable will you're doing your changes. Do note that in that mode conflict resolution does not take place

---

### Post by ventrical on 2011-08-19
I had to go into Unity 2D to disable UnityPlugin because it borked up the system pretty good for Unity 3D. However, after unticing Unity Plugin  from CCSM in Unity 2D and then enablingit again I was able to get my desktop and general functions back .. so .. again.. here I am again dancing the same dance that I did with Natty.

I would propound that perhaps devlopers of compiz could somehow create a multitasking <super> or dual <super> field macro where it can be toggled for the Unity dash and compiz functions (or have seperate keys),
ie;alt<u> for Unity sidebar. or can we do this ourselves already with the tools we have ?

---

### Post by jerrylamos on 2011-08-20
Why test the compiz pre-release when the regular one is busted all over?  I've got more compiz bugs than I can handle as is.....

When I want to get something done I crank up Unity-2D so I don't get unexpected Compiz crashes.  Unity-2D nice and crisp and fast and easy to read.  Even runs.  And no Compiz overhead.

But we're testing so I run Compiz if the frequency of crashes isn't too high.

Jerry

---

### Post by ventrical on 2011-08-20
I crashed Unity completely (could not even drag and drop or minimize) so I logged on using FVWM-Crystal and used synaptic to remove compiz and unity (just tic compiz and it will remove unity) then I re-installed compiz and Unity and now have control of my Unity 3D desktop back.

  Not sure if it will help anybody .. just reporting in.

---

### Post by ventrical on 2011-08-20
[http://www.youtube.com/watch?v=ifcopwQZVeE](http://www.youtube.com/watch?v=ifcopwQZVeE)


I finally got 'wobbly windows ' to work in Unity 3D!!!!!!!!!!!!!!! :)

YeaaaY!

:)

---

### Post by ventrical on 2011-08-20
The Wall/Expo effect works really great too. I couldn't get this with Natty.

[http://www.youtube.com/watch?v=4tC0XE-xVQE](http://www.youtube.com/watch?v=4tC0XE-xVQE)

---

### Post by ventrical on 2011-08-21
I was trying to do a process to reduce CPU usage and I got this neat effect wibbling and wobbling in an expo window (only have static screen shot.)

---

### Post by bcbc on 2011-08-22
For some reason, my windows title bars are not displayed. 

My experience:
1. setup ppa
2. update
3. desktop appeared, nothing else (no unity dock, etc)
4. switched to 2d
5. installed compiz config settings manager. Noted that unity plugin was not selected. Selected.
6 logout and login on 3d
7 works now, but no window titles.
[bug 830851]("https://bugs.launchpad.net/bugs/830851")

---

### Post by castrojo on 2011-08-22
> **bcbc said:**
> [bug 830851]("https://bugs.launchpad.net/bugs/830851")

Woo thanks for tagging it correctly!

(There should be a new upload today or tomorrow)

---

### Post by ventrical on 2011-08-22
Ok now.

---

### Post by ventrical on 2011-08-22
I was getting the same thing - no titles- and I had to close the windows from the dock.

Nice work.

---

### Post by beew on 2011-08-22
Interesting that you get so many testers. I thought that people who are still running 10.04 presumably do so because they put stability as their top and probably only consideration (so they don't want surprises. :))

---

### Post by ventrical on 2011-08-22
I am absolutely amazed at how stable Oneiric is. Compiz is lickity-split (that means super fast) and nimble.. more nimble than in 10.04 in my opinion - but I still think Lucid is rock solid for working in the trenches.

---

### Post by bcbc on 2011-08-22
> **ventrical said:**
> Ok now.
Mine's a little better - I can see my browser tabs at least. But still missing the 'tops'.

---

### Post by bcbc on 2011-08-22
> **bcbc said:**
> Mine's a little better - I can see my browser tabs at least. But still missing the 'tops'.
If I enable the "Window decoration" from Effects, I see my windows title bar again.

Edit: I see it, the minimize, maximize and close are on the right, and they don't work. And the system is crawling now. So... not really fixed.

---

### Post by bcbc on 2011-08-24
Since yesterdays updates (not fixed with today's updates) I don't get 3d unity anymore - just a blank desktop, and a bar across the top with some drop down menus, no indicators on the right. 2d works fine.

---

### Post by budluva04 on 2011-08-25
> **bcbc said:**
> Since yesterdays updates (not fixed with today's updates) I don't get 3d unity anymore - just a blank desktop, and a bar across the top with some drop down menus, no indicators on the right. 2d works fine.

go to the file drop down, open a new tab, navigate to /usr/bin and launch gnome-terminal...open ccsm and click the unity plugin box...

i assume that with the new compiz updates today that somehow the unity plugin crashes on login and that is the easiest way i found to fix it...you can then sudo killall nautilus after to get back to a regular desktop

---

### Post by ventrical on 2011-08-25
> **bcbc said:**
> If I enable the "Window decoration" from Effects, I see my windows title bar again.

Edit: I see it, the minimize, maximize and close are on the right, and they don't work. And the system is crawling now. So... not really fixed.


Actually I have Windows Decorations disabled on the machine that is working good with Windows Titles.

What I did was uninstall compiz and then reinstall it. I'm not sure if that will work for you. There was also a patch .. and that seemed to work for me.

---

### Post by mc4man on 2011-08-25
There is nothing much in that ppa atm other than 2 plugins packages (same bzr as O's, maybe some different defaults, no matter there.
If you are updated then you're back to using O's compiz packages

---

### Post by rbrick49 on 2011-08-25
Hi folks it was working ok as soon as I installed fglrx from the repos it went to the dogs,is fglrx causing me these problems or what
regards ron

---

### Post by bcbc on 2011-08-25
> **budluva04 said:**
> go to the file drop down, open a new tab, navigate to /usr/bin and launch gnome-terminal...open ccsm and click the unity plugin box...

i assume that with the new compiz updates today that somehow the unity plugin crashes on login and that is the easiest way i found to fix it...you can then sudo killall nautilus after to get back to a regular desktop

Thanks for the hint. It didn't work so easily for me (severe borkage?) but you were right that the unity plugin had crashed. But somehow after a lot of tweaking (complaining about conflicting and invalid settings) it is back now (and doesn't crash on login). But I'll remember that workaround for the future.

> **mc4man said:**
> There is nothing much in that ppa atm other than 2 plugins packages (same bzr as O's, maybe some different defaults, no matter there.
If you are updated then you're back to using O's compiz packages
Yes, there were two packages (I ran the ppa-purge after I had got 3D working again).

---

### Post by ventrical on 2011-08-26
A surprise effect from a compiz bug???

[http://www.youtube.com/watch?v=qyGZrGzXOyA](http://www.youtube.com/watch?v=qyGZrGzXOyA)

---

### Post by mc4man on 2011-08-26
looks like you're just rotating a 2 sided 'cube'

---

### Post by ventrical on 2011-08-26
hehe .. yeah ..but with the water effect- the other side comes out with these streaks .. sort of like a radiance...

  How do I get four or more sides ? :)

-

---

