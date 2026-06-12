---
title: "microsoft wireless laser kayboard and mouse 6000 help"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by ferronica on 2008-11-02
just installed ubuntu 8.10 gnome 64bit, facing keyboard problem using microsoft wireless laser kayboard and mouse 6000 V.2.0 combo volume up & down, play/pause, next track,mute etc etc.... are not working, same keyboard worked on ubuntu 8.04 32bit without any problem please help me out:confused::confused::confused:

---

### Post by ferronica on 2008-11-26
need help!!! sorry for bump:confused::confused::confused:

---

### Post by SunnyRabbiera on 2008-11-26
well I am not surprised the media keys are not working, those things never did me any good anyhow and its all a click of a mouse anyhow to turn up volume and such

---

### Post by ferronica on 2008-11-26
new kernel update or release for ubuntu 8.10 gnome 32bit support multimedia keys??

---

### Post by nhasian on 2008-11-26
can you configure your multimedia keys with System/Preferences/Keyboard Shortcuts?  when i installed 8.10 for some reason the button to increase audio didnt function on my keyboard by the one to lower audio did.  I just went to the keyboard shortcuts and fixed it in there.

---

### Post by ferronica on 2008-11-29
nothing worked, tried manually from System/Preferences/Keyboard Shortcuts no luck :(

---

### Post by fenrisswolf on 2008-11-30
Did  you try going to system settings/regional and language/keyboard layout?

Changing the default keyboard layout to "**Evdev-managed keyboard**" restores function to the "special" keys on some microsoft keyboard models.  After that, see if your keys work.  If not, try re-setting the keyboard shortcuts again, as the keys may be active but not mapped.  

If this still fails, I'm not sure what else to suggest.  You might want to fiddle with the keyboard layout settings and see if there is one that works better than others  with your perticular keyboard model.  (Just pay attention to your "default" setting in case something essential stops working and you need to go back to it later.)

---

### Post by ponderworks on 2008-12-19
Okay, here is a work around that will sacrifice the + - * keys on your numeric keyboard....

1. Go to System, Preferences, Keyboard shortcuts

2. Click shortcut for Mute and change it to "*" **ON THE NUMERIC KEYS** set

3. Repeat the procedure for the Volume Up and Volume Down using the "+" and "-" keys **ON THE NUMERIC KEYS** set

You should now be able to use those keys until they issue a patch for this keyboard on v8.10

---

### Post by ferronica on 2008-12-19
i know it will work :( but not in that way

---

### Post by fenrisswolf on 2008-12-21
Hmm.  It seems to be a kernel issue. 
There are [people working]("http://bugzilla.kernel.org/show_bug.cgi?id=11759") on it, and there's a patch [[COLOR="DarkOrange"]**here**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/281993") (with instructions and helpful links on the thread, even) that **MAY** take care of the issue, but the process involves rebuilding the kernel to apply the patch.  (I am not sure I want to go to that much trouble to try it, and some have reported it did not work for them, so YMMV.) 

If you are comfortable doing all that, and absolutely sure you can't live without the disabled keys until the next working kernel is finally released, go for it.  

Otherwise, I'd wait until a more permanent fix is implemented.

---

### Post by ferronica on 2009-01-01
its really buggy release 8.10

---

### Post by ferronica on 2009-01-26
anyone one who can solve our Keyboard issue :(

---

