---
title: "What is the keyboard shortcut for MouseKeys?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-11
I know how to get to it through the menus.  I'd like to know if there's a keyboard shortcut out there for it too.... Because then, I want to remove it.

Thanks!

---

### Post by diablo75 on 2008-07-12
I thought I'd bump this thread and see if anybody has yet found a solution to this problem:

Mousekeys.  Seems like an innocent feature, right?  Until it enables itself without the user being notified about it.  They eventually have to discover that their keypad once again won't enable the number-lock and instead, moves the mouse cursor around.  This has probably happened to me about 10 times since upgrading from 7.10 to 8.04, and the only "solution" I've been given elsewhere is to manually disable it via the keyboard settings/accessibility settings.

I don't call that a solution.  I call that a cheap lazy band-aid.  It'd be nicer if I knew WHY this feature decides to turn on without warning.  And perhaps what keyboard shortcut causes this to happen so that the same shortcut could be used to disable it.

---

### Post by Paddy Landau on 2009-05-17
I had the same problem, pressing an unknown keyboard combination that kept turning it on.

I found the combination.

Ctrl-Shift-NumLock

---

### Post by XCan on 2009-05-17
> **diablo75 said:**
> I thought I'd bump this thread and see if anybody has yet found a solution to this problem:

Mousekeys.  Seems like an innocent feature, right?  Until it enables itself without the user being notified about it.  They eventually have to discover that their keypad once again won't enable the number-lock and instead, moves the mouse cursor around.  This has probably happened to me about 10 times since upgrading from 7.10 to 8.04, and the only "solution" I've been given elsewhere is to manually disable it via the keyboard settings/accessibility settings.

I don't call that a solution.  I call that a cheap lazy band-aid.  It'd be nicer if I knew WHY this feature decides to turn on without warning.  And perhaps what keyboard shortcut causes this to happen so that the same shortcut could be used to disable it.

I know that this happens to me usually to the target VNC machine (althogh haven't tried this much in Jaunty since they flunked vnc+compiz) after having worked a while through vnc. Anyway, the remedy is quite easy, go to System->Preferences->Keyboard ->Acessibility and uncheck "Accessibility features can be toggled...".

---

### Post by diablo75 on 2009-05-18
> **XCan said:**
> I know that this happens to me usually to the target VNC machine (althogh haven't tried this much in Jaunty since they flunked vnc+compiz) after having worked a while through vnc. Anyway, the remedy is quite easy, go to System->Preferences->Keyboard ->Acessibility and uncheck "Accessibility features can be toggled...".

That's new!  I'll keep an eye on my system and complain some more if it doesn't work out, but I have a feeling this might just do the trick.  We'll see.  As you said, there's that vnc+compiz bug that's still being worked out right now (at least disabling compiz on the target fixes it for now).

---

### Post by ravi_d on 2009-06-23
I found the keyboard shortcut that turns mouse keys on and off.

Ctrl+Alt+Shift+NumLock

---

### Post by Paddy Landau on 2009-06-24
> **ravi_d said:**
> I found the keyboard shortcut that turns mouse keys on and off.

Ctrl+Alt+Shift+NumLock
You don't need the Alt.

[http://ubuntuforums.org/showthread.php?p=7295922#post7295922](http://ubuntuforums.org/showthread.php?p=7295922#post7295922)

---

### Post by kliklik on 2009-06-25
And you don't need Ctrl.. On my system, Shift+NumLock toggles Mouse Keys.

---

### Post by Paddy Landau on 2009-06-25
> **kliklik said:**
> And you don't need Ctrl.. On my system, Shift+NumLock toggles Mouse Keys.
It gets simpler and simpler! :D

---

