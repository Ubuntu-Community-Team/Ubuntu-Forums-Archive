---
title: "[SOLVED] unable to use gnome"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by ghostier on 2008-06-12
Um, I downloaded and installed this app called ubuntu tweaking or something like that. I've installed it successfully, but as soon as i run it the splash screen pops up then my desktop and every window just disappeared, I could only see my background on my screen. So i restart the computer and try to open up a gnome session again, but it just loads, shows my desktop for a second or so then disappears again. I'm using KDE4 sessions now because I can't do anything using gnome anymore.

---

### Post by MmmmJoel on 2008-06-12
Have you tried uninstalling the program?

---

### Post by ghostier on 2008-06-12
I want to use it though... I'll try anyways and get back to you

---

### Post by sdennie on 2008-06-12
One thing you can try would be run gnome tweak from KDE4.  As far as I know, gnome tweak is just a fancy interface to gconf.  KDE4 doesn't use gconf so, it's safe to run it from there.  If you are lucky, gnome tweak will either redeem itself by fixing the problem it caused or, you can look through the settings and see if you can find what problem it caused.

---

### Post by ghostier on 2008-06-12
Yea. I uninstalled that app, with great difficulty i might add because I'm clumsy at using kde, I accidentally removed my task manager widget on the bottom and cant get it back to where it was, also when I uninstaled that app using synaptic it froze when the progress bar was at its end. I had to restart because of that and then when I went to check synaptic again it was still there so I marked for removal again. This time I couldn't click the apply button so I closed synaptic and opened it up again, this time the app was nowhere to be found so I assumed it was removed.


Vor: I don't know how to use gnome tweak

---

### Post by Xiong Chiamiov on 2008-06-12
I would recommend running
```

mv ~/.gnome2 ~/.gnome2_old

```
which will rename your gnome configuration folder to .gnome2_old.  When you restart, gnome will generate a fresh gnome config for you, and you can slowly copy back files and folders until you find what was causing the trouble.

---

### Post by ghostier on 2008-06-13
Is that basically reformating the gnome, will apps, docs, files be lost?

---

### Post by RiceMonster on 2008-06-13
> **ghostier said:**
> Is that basically reformating the gnome, will apps, docs, files be lost?

GNOME will go back to the default configuration if you do that, but you won't lose any applications files, docs, etc. If you've customized GNOME, you'll have to do it again.

---

### Post by Xiong Chiamiov on 2008-06-13
> **ghostier said:**
> Is that basically reformating the gnome, will apps, docs, files be lost?
It will set GNOME back to the default configuration, but you won't lose any documents.

All of your GNOME configuration files, however, are still in the folder .gnome2_old, so they aren't really lost.  They're just in a different spot than GNOME is looking for them.  You can copy them back over, but go a folder at a time, so that you can find what it was that was causing the problem.

---

### Post by sdennie on 2008-06-13
If that is the route you take, you will probably also need to:

```

mv .gconf .gconf.old

```

A lot of gnome configuration is done via gconf so, you'd need to do that as well.

---

### Post by ghostier on 2008-06-14
Okay thanks that worked.

---

