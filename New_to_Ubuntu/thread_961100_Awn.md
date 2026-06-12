---
title: "Awn"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-10-28
Okay, so How do I keep my AWN permanently on? if I restart my computer or turn it off then back on, I have to go to the AWN launcher in my panels. I want to get rid of panels compleatly and go only with the dock,so how do I put my thunderbird, picassa open office, etc. in to it? I love the whole idea of the simplicity of the dock.
By the way, I am using 8.10 (awsome)

---

### Post by pofigster on 2008-10-28
Whenever I'm reinstalling AWN I always seem to have that problem.  The first thing I'd do is to delete all the launchers from inside AWN Manager.  Then, drag the shortcuts onto the panel to add them.  This usually does the trick for me.

I assume you already have AWN in your "Sessions" manager (System-Preferences-Sessions) so that it launches when you login.

---

### Post by Paqman on 2008-10-28
Go into the AWN manager and tick the box for "start AWN automatically" (or words to that effect).

If that doesn't work add it to Sessions like pofigster says.

---

### Post by galenorama on 2008-10-28
Please Help!
I installed awn + manager, but I cant figure out how to actually get the dock to appear.
All advice appreciated.

---

### Post by aktiwers on 2008-10-28
To get it start automatically go to System => Preferences=> Sessions
Click "add" And type AWN in name.
And this command under command:
```
avant-window-navigator
```

To run it, you can also type that command in terminal or go to Applications => Accessories => Avant Window Navigator

---

### Post by AllanPoe on 2008-10-28
Applications > Accessories > Awn
System > Preferences > Awn manager

---

### Post by galenorama on 2008-10-28
Thank You, but:
When I run AWN, a small grey box appears in my upper left screen corner momentarily. It disappears after probably 1/8 of a second. Nothing else happens.

---

### Post by aktiwers on 2008-10-28
Do you have desktop effects turned on?
System => Preferences => Appearance => Visual Effects

---

### Post by galenorama on 2008-10-28
Thanks for the suggestion.
When I enable effects, the computer thinks for about 10 seconds, then gives me a dialog box:
Desktop effects couldn't be enabled.

---

### Post by Paqman on 2008-10-28
Aha! That's why you're not getting AWN, it needs the desktop effects to be running. Have you got your graphics card drivers installed? Go to System > Admin > Hardware drivers to find out.

What graphics card do you have in the mcahine?

---

### Post by galenorama on 2008-10-29
Thank you so much. You're the best.
When I run Compiz Check, it says that my Raedeon driver is blacklisted.
```

Gathering information about your system...

Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: ATI Technologies Inc Radeon RV250 [Mobility
FireGL 9000] (rev 02)
Driver in use: radeon
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [ OK ]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [FAIL]

```
Is it ok for me to ignore the blacklist?

---

### Post by galenorama on 2008-10-29
I ignored the blacklist, and it still doesn't work.

---

### Post by aktiwers on 2008-10-29
You need to enable your drivers like Paqman said. Then you can enable the effects and then run AWN :)

---

### Post by galenorama on 2008-10-30
Ok. Thanks. I'll try that.

---

### Post by galenorama on 2008-10-31
> **Paqman said:**
> Aha! That's why you're not getting AWN, it needs the desktop effects to be running. Have you got your graphics card drivers installed? Go to System > Admin > Hardware drivers to find out.

What graphics card do you have in the mcahine?
When I open Hardware Drivers, It says there are no proprietary drivers installed.

---

### Post by tjwoosta on 2008-10-31
if you cant get compiz working, cairo dock, and i think kiba dock, will work fine without compiz

---

### Post by galenorama on 2008-11-01
Thanks everyone, for all your help.
I just upgraded 8.10 this morning, and I now can enable my desktop effects. It all works great!!! : )
Thanks again!

P.S. Can someone please mark this thread as solved. I can't find out how.

---

### Post by sporkubus on 2008-11-01
Is it possible to somehow set it to make the dock appear when I press the Windows key (much like the Start menu in windows?) Also, it would be nifty to know how to do the same thing with the main menu.

---

### Post by danbar on 2008-11-01
My Awn manager has disappeared after upgrading to Intrepid!  Maybe during the upgrade i did a mistake.  

All i have is an orange/brown screen (ubuntu's) screen.  How can I have everything back?  I don't see the applications, places, system etc.......so strictly speaking I can't do a thing.

---

