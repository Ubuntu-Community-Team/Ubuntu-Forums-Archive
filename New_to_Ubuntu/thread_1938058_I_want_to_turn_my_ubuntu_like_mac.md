---
title: "I want to turn my ubuntu like mac"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by rushikesh988 on 2012-03-09
hello freinds,
I want to make my linux to feel like a mac ..
I have used mac for linux before but Now I its not working I think this is because of unity ..may be ubuntu has changed its file structure  .

so if anybody knows how to make it happen ?? please tell me

---

### Post by 3rdalbum on 2012-03-09
> **rushikesh988 said:**
> hello freinds,
I want to make my linux to feel like a mac ..
I have used mac for linux before but Now I its not working I think this is because of unity ..may be ubuntu has changed its file structure  .

so if anybody knows how to make it happen ?? please tell me

That was an old Gnome 2 thing. Since the switch to Gnome 3 and Unity the theme has not been updated to work on the newer desktops. There is less interest in it now that Linux has it's own distinctive look.

---

### Post by Rodney9 on 2012-03-09
Pear OS is a French Ubuntu-based desktop Linux distribution. Some of its features include ease-of-use, custom user interface with a Mac OS X-style dockbar, and out-of-the-box support for many popular multimedia codecs.

[http://www.pear-os-linux.fr/](http://www.pear-os-linux.fr/)

---

### Post by sleepingdragon on 2012-03-09
[http://sourceforge.net/projects/macbuntu/](http://sourceforge.net/projects/macbuntu/)

---

### Post by albert s on 2012-03-09
why,?
would be my first question,.

---

### Post by cbanakis on 2012-03-09
Just pay Canonical about $3,000.  (Just like a Mac then)
LOL J/K

First you will want to get a dock app.
Either Cairo Dock, or Docky.  (I recommend Cairo)
There are more I'm sure, but those are the ones I've used.
(Both are in the Software Center)

Then, setup your dock to start with Ubuntu.
Reboot your computer a couple times to make sure its loading by itself.
(this is important, because once you disable the Unity dock, your computer will be hard to navigate without a dock)

Then, you will need "CompizConfig Settings Manager" (In Software Center)
You will use this to get rid of that pesky unity thing.

In terminal run 
compiz-manager --replace &
Your desktop will probably do a bit of flashing and refreshing.

Then uncheck the box that says "Unity" in the Compiz Settings Manager.

From there, you should be able to stumble through all the Dock, and Compiz settings, until your satisfied.

If you screw up your Compiz settings to the point that you no longer know how to undo what you did...

You can run...
```
gconftool-2 --recursive-unset /apps/compiz-1

unity --reset
```

that should reset everything back to defaults, (Except for the dock you added)


hope this helps

---

