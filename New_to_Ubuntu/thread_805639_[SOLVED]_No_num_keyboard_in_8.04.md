---
title: "[SOLVED] No num keyboard in 8.04"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by carusoswi on 2008-05-24
Just discovered this morning that my numbers key pad is not functioning in Ubuntu.  Why?  How do I restore it?  It works fine when I boot into XP, so the problem is not mechanical in nature.

Assistance appreciated.

Caruso

---

### Post by alienexplorers on 2008-05-24
Do you have numlockx enabled? If not go into synaptic and search for numlockx and mark it to load.  Click apply. Close synaptic. Reboot.

---

### Post by philinux on 2008-05-24
> **carusoswi said:**
> Just discovered this morning that my numbers key pad is not functioning in Ubuntu.  Why?  How do I restore it?  It works fine when I boot into XP, so the problem is not mechanical in nature.

Assistance appreciated.

Caruso

Do you mean just num lock or all the numeric keys.

If the later use System>Prefs>Keyboard and make sure you have the correct type selected. Hardy remembers your numlock state.

---

### Post by carusoswi on 2008-05-24
> **philinux said:**
> Do you mean just num lock or all the numeric keys.

If the later use System>Prefs>Keyboard and make sure you have the correct type selected. Hardy remembers your numlock state.

The numlock indicator light indicates that numlock is enabled, but the keypad behaves as though it is disabled.  Arrow keys (4-6, 2-8) will move the cursor around, but I cannot enter numeric values with the keypad.  Pressing the numlock key to turn off the enabled indicator seems to disable the keypad completely.

Caruso

---

### Post by carusoswi on 2008-05-24
> **philinux said:**
> Do you mean just num lock or all the numeric keys.

If the later use System>Prefs>Keyboard and make sure you have the correct type selected. Hardy remembers your numlock state.

I have tried your suggestion.  No apparent effect.  I never touched keyboard preferences to make things work in previous versions.  Don't quite know what to make of this.  My keyboard (supplied with the system) is a Benq X120 Model A122 Extension U21 if that means anything.  I've used it with this system for 4-years.  

Caruso

---

### Post by carusoswi on 2008-05-24
> **alienexplorers said:**
> Do you have numlockx enabled? If not go into synaptic and search for numlockx and mark it to load.  Click apply. Close synaptic. Reboot.

I did not have numlockx marked for install.  Went into synaptic and clicked it, installed it, no effect.

Caruso

---

### Post by philinux on 2008-05-24
Have you access to another keyboard?

My girlfriend picked one up recently for £2.

---

### Post by diablo75 on 2008-05-24
You have mousekeys enabled.  This problem drives me crazy because it seems a lot of people have it for no good reason.

Solution:

System>Preferences>Keyboard>Mouse Keys (tab)>Uncheck that crap.

Dumbest problem I've encountered since upgrading to 8.04, I swear (besides Pulse Audio).  Sorry you had to endure it too.

---

### Post by philinux on 2008-05-24
Mouse keys is off by default.

---

### Post by diablo75 on 2008-05-24
> **philinux said:**
> Mouse keys is off by default.

Obviously it has a way of turning on and not notifying the user with a visual notification.  It's happened to me more than once.  So again, it's one of the dumbest problems I and many others have encountered.

---

### Post by carusoswi on 2008-05-24
> **diablo75 said:**
> Obviously it has a way of turning on and not notifying the user with a visual notification.  It's happened to me more than once.  So again, it's one of the dumbest problems I and many others have encountered.

Yep, that was the problem.  How that got turned on, I'll never know.  I've never been in that dialog tab before, so it wasn't me.

I can imagine why there might be an occasion where you stepped on your mouse and killed it and no other mice were around - then you might need it.  Otherwise, I cannot imagine why the feature is even there.  Besides, I thought that was the reason for the numlock key in the first place.

Anyhow, thanks, diablo, for pointing (no pun intended) in the right direction.

Caruso

---

### Post by diablo75 on 2008-05-24
> **carusoswi said:**
> Yep, that was the problem.
Sweet.  Mark the thread as solved then.

:popcorn:

You might consider voting for my little idea regarding this annoyance too:  [http://brainstorm.ubuntu.com/idea/9035/](http://brainstorm.ubuntu.com/idea/9035/)

---

### Post by carusoswi on 2008-05-25
[QUOTE=diablo75;5034656]Sweet.  Mark the thread as solved then.

Never marked a thread as solved before - hadn't noticed the tools drop down before.  Thanks for yet another tip.

Caruso

---

