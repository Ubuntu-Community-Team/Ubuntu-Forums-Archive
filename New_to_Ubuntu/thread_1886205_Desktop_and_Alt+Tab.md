---
title: "Desktop and Alt+Tab"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by yeh on 2011-11-24
I'm not exactly new to ubuntu (used 10.04), but I'm new to unity and I don't understand a couple of things...

1. What happened to the desktop?

I have icons in my desktop folder but I don't see them on my desktop. I can't right-click on the desktop, and I can't drag my mouse to create those orange transluscent boxes anymore...

2. Alt+tab behavior

I would understand more if alt-tab switched applications and alt+~ switched windows within an application (like mac osx does). But sometimes, when I use alt+tab, I get a window of the same application. How exactly does alt+tab work now?

Thanks for answering.

---

### Post by wolfen69 on 2011-11-24
How many things do you have open when doing alt+tab?

---

### Post by yeh on 2011-11-24
Multiple applications (firefox, software center, terminal, update manager) and multiple windows within those applications (2 firefox windows, 1 software center, 2 terminals, update manager+updating dialogue).

When I alt-tab, I expected it to either always switch applications (mac) or always switch windows regardless of application (windows). I can't seeme to figure out how they do it, though.

Edit: My desktop came back some time between my last reply and now. The only thing I added to it was a chrome web app shortcut.

---

### Post by mcduck on 2011-11-24
The desktop *should* be enabled by default in Unity (not in Gnome Shell, though, keep that in mind), but if it's for some reason not working the easiest solution is to install [Gnome Tweak Tool]("apt:gnome-tweak-tool") and make sure the option to manage the desktop is enabled.

What comes to Alt-Tab, it should always switch between any windows, but if you have multiple windows from same application open it will group them together and expands to show all the windows when you switch to the application group and wait a second or two.

I'm not quite sure if it's by default set to show all windows or just windows from the current desktop. Perhaps somebody else can tell which one is the default setting, and of course you can always use the CompizConfig Settings Manager to configure the behavior you prefer.

---

### Post by yeh on 2011-11-24
Ah, I think I get it now...

If you don't wait for the pretty launcher to come up, alt+tab follows Windows behavior. If you press down on alt+tab a bit longer and wait for the launcher to come up, alt+tab follows Mac behavior.
Additionally, Alt+~ works exactly as it does on a mac, switching between windows of the same application.

The compiz settings manager is very helpful, thank you.

I'm marking this thread solved.

---

### Post by ptrakk on 2011-11-24
what if you open a terminal and run "unity --replace"

---

### Post by yeh on 2011-11-24
o.0....what just happened? Does that command restart unity or something?

---

### Post by wolfen69 on 2011-11-24
> **yeh said:**
> o.0....what just happened? Does that command restart unity or something?

Yes, which was unnecessary for you to do. :confused:

---

### Post by ptrakk on 2011-11-24
oh it was solved my bad..

---

### Post by Stovey on 2011-11-24
One other feature of alt-tab:

Tap alt-tab and release quickly, and the window behind the current one comes to the foreground (I think that's how it works.  Try it!).  This allows rapid switching between two windows.

---

### Post by yeh on 2011-11-24
Thanks for the answers!

---

