---
title: "my titles bars disappeared"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by poopcup on 2008-07-16
For some reason, the title bars (the ones with the folder name on the left and the minimize, maximize and close buttons on the right) on all of my windows and applications are gone. how would i go about putting them back and why do you think they disappeared in the first place?
Thanks

---

### Post by perlluver on 2008-07-16
Compiz most likely enabled.  Press alt+f2 and then type, metacity --replace.

---

### Post by overdrank on 2008-07-16
> **poopcup said:**
> For some reason, the title bars (the ones with the folder name on the left and the minimize, maximize and close buttons on the right) on all of my windows and applications are gone. how would i go about putting them back and why do you think they disappeared in the first place?
Thanks

Hi and welcome, please do not make multiple threads on the same issues
[http://ubuntuforums.org/showthread.php?p=5400285#post5400285](http://ubuntuforums.org/showthread.php?p=5400285#post5400285)
Could you give us some more info on like what you were doing when the issue started? also some specs on the system like graphics card?

---

### Post by poopcup on 2008-07-16
Sorry guys, i'm new here. 
i've been enjoying ubuntu so far, this has been my only issue. i first noticed the disappearance after plugging in a monitor (i'm a laptop user.) after having a dual monitor setup for about 5 minutes i restarted the computer and now my title bars are gone. everything else is working fine, its just a real inconvenience to not have the title bars.
Thanks

---

### Post by overdrank on 2008-07-16
> **poopcup said:**
> Sorry guys, i'm new here. 
i've been enjoying ubuntu so far, this has been my only issue. i first noticed the disappearance after plugging in a monitor (i'm a laptop user.) after having a dual monitor setup for about 5 minutes i restarted the computer and now my title bars are gone. everything else is working fine, its just a real inconvenience to not have the title bars.
Thanks

Hi and yes this happens with dual monitors sometimes, What is the model of graphics card?

---

### Post by poopcup on 2008-07-16
How do i check what model my graphics card is?
whatever it is, i'm just using the built in graphics for the laptop (an acer).

---

### Post by overdrank on 2008-07-16
> **poopcup said:**
> How do i check what model my graphics card is?
whatever it is, i'm just using the built in graphics for the laptop (an acer).

In the terminal located under application, accessories. Use the command ```
lspci
``` and look for VGA.

---

### Post by poopcup on 2008-07-16
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

---

### Post by overdrank on 2008-07-16
> **poopcup said:**
> ```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

As I had thought, I can not help with the intel graphics. :(

---

### Post by poopcup on 2008-07-16
hmmmmmm, well, any hunches?
i tried the alt-f2 thing to run metacity but click alt-f2 didnt open anything. i suppose thats a new problem

---

### Post by overdrank on 2008-07-16
> **poopcup said:**
> hmmmmmm, well, any hunches?
i tried the alt-f2 thing to run metacity but click alt-f2 didnt open anything. i suppose thats a new problem

Hi and yes when the title bars do not appear then the alt-f2 menu does not also. You may try and run it in the terminal
Are you using both monitors, and are the title bars missing on both?

---

### Post by poopcup on 2008-07-16
i was just running the dual monitor setup to test the monitor. i dont intend on setting up my computer to run dual monitor all the time. after that test run with the dual monitor, the title bars died on me. what code would i use in the terminal to open up the alt-f2 menu? 
on a sidenote, do you think uninstalling and reinstalling compiz would do the trick?

---

### Post by overdrank on 2008-07-16
> **poopcup said:**
> i was just running the dual monitor setup to test the monitor. i dont intend on setting up my computer to run dual monitor all the time. after that test run with the dual monitor, the title bars died on me. what code would i use in the terminal to open up the alt-f2 menu? 
on a sidenote, do you think uninstalling and reinstalling compiz would do the trick?

HI and you may not need to uninstall compiz. Use the command ```
metacity --replace
``` this will disable compiz and hopefully return the title bars. If this doesn't you may try and boot into recovery mode and use the xfix option to repair the xorg.

Edit
If this does work then check CCSM the advance desktop effects to insure that the window decorations is checked.

---

### Post by MatthewPlanchard on 2008-07-16
Another option might be to install the Advanced Compiz Settings package in Add & Remove, then use access it from the Menu-System-Preferences or the Control Panel. In there is an option for Window Decorators. Make sure it's checked, or check it and uncheck it.

Edit:
Just saw overdraft's edit, and yes, that's what I'm talking about.

---

### Post by overdrank on 2008-07-16
> **MatthewPlanchard said:**
> Another option might be to install the Advanced Compiz Settings package in Add & Remove, then use access it from the Menu-System-Preferences or the Control Panel. In there is an option for Window Decorators. Make sure it's checked, or check it and uncheck it.

Edit:
Just saw overdraft's edit, and yes, that's what I'm talking about.

Thanks as your description is more detailed. :)

---

### Post by pikeman47 on 2008-07-16
i've been experiencing a similar problem. when i start up firefox, the title bar is missing. this is only for firefox though. i can get the title bar to come back by turning fullscreen on and off with f11. how can i fix it to where the title bar is there all the time and won't make me manually "fix" it?

---

### Post by jacrider on 2008-07-26
I am experiencing the same issue.  Any ideas on how to resolve it?

---

### Post by namraw on 2008-08-13
to get to alt + f2 u first have to enable metacity via console....

**EDIT this is what i did to resolve**
using a google and few posts on this forum and various others....
[LIST=1]
[*]Open terminal
[*]run metacity --replace&
[*]hit alt + f2
[*]type in box : gconf-editor /desktop/gnome/applications/window_manager
[*]Run
[*]replace /usr/bin/compiz with /usr/bin/metacity ( i did this on both current and default
[*]logged out and in

that should do it .....?!
[/LIST]

---

### Post by chriswyatt on 2010-12-12
Sorry to revive an old thread but I've also got this issue.  I think it's to do with having your monitor in an above/below setup.  I find that my titlebars disappear in all applications, not just Firefox.  And that's only on the lower screen, not the screen I have configured to go above it.

Also I don't have Compiz effects enabled so it's nothing to do with that.

---

