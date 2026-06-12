---
title: "[SOLVED] Why won't Hulu/YouTube pop out?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-21
I'm wondering if anyone knows why Hulu and YouTube won't pop to full screen?  I have the flashplugin-nonfree installed, and I'm using Firefox 3.0.2.  Anyone else having this same problem?

---

### Post by jimmy the saint on 2008-09-21
Flash support in *nix is weak.  Not everything works.  This is just one of those things.  You may want to check your firefox settings and see if you have popups disabled.  This may work, but I kind of doubt it.  

Good Luck!

---

### Post by tarahmarie on 2008-09-21
Yeah, enabling popups for hulu and youtube didn't help.  I can get a hulu vid to pop OUT, but not to go to fullscreen.  Grr.  Thanks anyway.

---

### Post by RequinB4 on 2008-09-21
do you have libflashsupport installed?  If yes/no, try with the opposite ;P

fullscreen hulu works perfectly for me and i'm using flashplugin-nonfree, this may sound meh but make sure you're hitting the upper right fullscreen button not the pop out button.

---

### Post by tarahmarie on 2008-09-21
> **RequinB4 said:**
> do you have libflashsupport installed?  If yes/no, try with the opposite ;P

fullscreen hulu works perfectly for me and i'm using flashplugin-nonfree, this may sound meh but make sure you're hitting the upper right fullscreen button not the pop out button.

I installed libflashsupport and tried again; same diff--hitting the fullscreen button sorta flashes to fullscreen then disappears.  I'm going to try rebooting and see if that makes a difference.

---

### Post by tarahmarie on 2008-09-21
Yep, rebooting, checking for upgrades, nothing's helping.  I'm running Kubuntu 8.04, KDE 4.1.1, Firefox 3.0.2, and I have a monster system with an Nvidia GeForce 8600.  Bother.

---

### Post by Lupi on 2008-09-21
I just installed Flash (and Ubuntu for that matter :D ) but the sound in Youtube isn't working. Any idea why?

---

### Post by RequinB4 on 2008-09-22
> **Lupi said:**
> I just installed Flash (and Ubuntu for that matter :D ) but the sound in Youtube isn't working. Any idea why?

Welcome!  You know it's ok to make new threads... 

Try having only firefox open and trying again,

and then install libflash support - go to system - admin - synaptic package manager, enter your password, and install the libflashsupport package.

Then try again.

To the OP: No idea, it might be a WM issue which makes me unqualified to answer - try with/without compiz

```

metacity --replace
```
or
```

compiz --replace

```

Not both at the same time ;P

---

