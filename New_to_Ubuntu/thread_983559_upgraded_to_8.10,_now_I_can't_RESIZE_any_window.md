---
title: "upgraded to 8.10, now I can't RESIZE any window?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by gregphil on 2008-11-15
Does anyone know what setting under Kubuntu might prevent the window RESIZE handles from having any effect?  

The double click on the title bar is still able to toggle the maximize state, but when it is a normal sized window I can't find a way to resize the window.  Dragging the edges does not work, even though the cursor changes shape when on a window edge.

Also, it is very hard to MOVE a window because the fancy "eye candy" makes it act like rubber and act like the other edge is stuck to the desktop.

How can I turn this off?  I need to be able to resize windows again, and it would be nice to be able to move them a little easier.

Thank You.

---

### Post by gregphil on 2008-11-15
Ok, I FINALLY found how to turn off the problem.

It turned out to be the COMPIZ desktop effects.  The menu "System-desktop effects" has a group of "Effects Levels"  But changing the radio button would not "stick" after clicking "Apply" and "Done".  I finally tried the "No effects" button and after a few tries to "took".  Then the Kubuntu operating system worked once again.

Why is compiz even included if it breaks basic features?

Thank You.

---

### Post by epswinde on 2008-11-15
> **gregphil said:**
> 
Why is compiz even included if it breaks basic features?


Compiz isn't included in kubuntu, nor is it necessary for eye-candy under KDE.  Kwin was rewritten for KDE 4.0, and is now a fully composting window manager, and has all the other great features of kwin that compiz doesn't.

I would recommend  that you NOT use compiz, but look under system-settings > desktop.  There is a tab for desktop effects, and a way to configure each and every one (this is KDE!).

You also may also want to look under system-settings > window behavior: there's alot of configuration going on in there including ways to 'turn off' the resizing handles on windows.

Also, under KDE, alt+left click moves windows and alt+right click resizes windows (regardless of where you click in the window) so there's no need to worry about

hope this helps.

---

### Post by gregphil on 2008-11-16
Ok, should un-install compiz using a package manager?  I have is set to "no effects" and all video seems to be working as it should.

I am pretty sure I never choose to install Compiz myself, it had to be part of the standard "upgrade" to kubuntu 8.10 from kubuntu 8.04.1

The install started from a kubuntu 8.04 Live CD, and then followed the upgrades suggested by the package manager.  The step to 8.10 was a huge download, over 600 meg I think.

---

### Post by binbash on 2008-11-16
try this : 

Enable compiz.Go to workarounds plugin, untick legacy fullscreen support.And report if it is worked or not

---

### Post by epswinde on 2008-11-17
> **gregphil said:**
> Ok, should un-install compiz using a package manager?

I would say that it would be acceptable to uninstall compiz using adept. It doesn't make much sense (to me) to have it taking up space when you're not using any of its effects.  But it's not going to hurt anything if its not removed either, so that's totally up to you.

How it got there in the first place is a mystery, I've been running kubuntu since edgy, and it's never been included by default.  It's conceivable that it was installed during your upgrade process, by some error.  I usually just reinstall from a new live cd each time there's an upgrade, so I can't speak to that. 

But you really don't need it -- kwin is pretty excellent.  It has all the fun features of compiz, excepting the desktop cube, but that's coming in kde 4.2.  I find it to be every bit as good as compiz, and it's effects play much nicer with kde 4 than beryl/compiz ever did with kde 3.5.x

Upon further inspection, compiz is indeed included.  in the System-settings, look under the advanced tab, and select session manager.  Scroll down a bit untill you see the window manager section.  Make sure kwin is chosen.  things should behave much better.  hope that helps.

---

### Post by lotvx on 2009-02-05
open compizconfig settings manager  and under windows management select resize window, and it's done , i had the same problem and now is ok, the cursor keeps being a different one but works.

---

