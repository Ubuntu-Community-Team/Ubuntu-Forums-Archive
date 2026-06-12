---
title: "full screen videos go transparent?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Rukaru on 2008-08-16
I'm not sure when this started...but I don't like it.  If I watch a video on youtube and make the video fullscreen, it will be like 50% transparent.  I am wondering if it has something to do with compiz.  I got new plugins, but all the new ones are off.  the opacity plugin is also off.  I do have special opacity settings in the general options of the settings manager, but they should not be making these videos transparent.  Anyone know what the problem is?

Update: Okay, it seems it did have something to do with the special opacity settings, which are placed in the general options plugin for compiz.  I got rid of the special settings, which should make it completely opaque. Of course, nothing is that easy for me.  now, the windows won't even go full screen.  I can see it flash up full screen (no longer transparent), but the full screen instantly disappears.  Strange, no?

---

### Post by Rukaru on 2008-08-16
And btw, it may have nothing to do with compiz.  Is there a way to check?

---

### Post by sharks on 2008-08-16
have u enabled compiz? 
just right click on desktop---apperances---visual effects and turn them to none.
then play the video and check.

---

### Post by Rukaru on 2008-08-16
> **sharks said:**
> have u enabled compiz? 
just right click on desktop---apperances---visual effects and turn them to none.
then play the video and check.

Okay, it is compiz that is causing the problem.  It didn't happen after I turned it off.  It's back on now and the problem is back.  Any ideas on what specifically may be causing the problem?

---

### Post by Rukaru on 2008-08-16
Before anyone asks, this problem only seems to be with videos put in full screen (like on youtube).  Making the windows themselves fullscreen will not cause the problem.  It only seems to be videos.

---

### Post by Rukaru on 2008-08-16
Okay, I just figured it out.  Now there's another problem.  See the update in the first post.

---

### Post by Juhla Mokka on 2008-08-18
Is there a fix? I have the same problem: I cannot make videos full screen,  the full screen window just flashes once and disappears.

I think I will go to the Desktop Effects forum and see if anything can be done about compiz/advanced desktop effects. It used to cause OpenOffice spreadsheets to crash as well.

:-k

---

### Post by life-on-mars on 2008-10-07
It's the Qt Window Fix in the Compiz Workarounds plugin.

The problem also affects games and other applications that run in fullscreen mode.

---

### Post by CarpKing on 2008-10-12
> **life-on-mars said:**
> It's the Qt Window Fix in the Compiz Workarounds plugin.

The problem also affects games and other applications that run in fullscreen mode.

I too have this problem, and disabling this setting causes the full screen windows to flash up and quickly disappear, much like the OP.

EDIT:
I can make things a little better by leaving the setting in place but changing the dropdownmenu match in "General Options--> Opacity Settings" to 99 (100 makes it disappear as before).  If I could find the title match for the fullscreen window, maybe I could set it as an exception, but any clicks outside cause the window to disappear.

---

