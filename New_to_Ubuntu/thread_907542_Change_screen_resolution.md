---
title: "Change screen resolution"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by tc101 on 2008-09-01
I just got around to installing Hardy.  It seems fine so far, but now
there are lots of things about basic setup that I have forgotten.

First, I want the resolution much smaller.  I went to
System/Preferences/Screen Resolution and the smallest resolution is
800x640, to which it is already set.  Only other resolutions are
640x480, 400x300 and 320x240.  How do I get other resolutions?

---

### Post by overdrank on 2008-09-01
> **tc101 said:**
> I just got around to installing Hardy.  It seems fine so far, but now
there are lots of things about basic setup that I have forgotten.

First, I want the resolution much smaller.  I went to
System/Preferences/Screen Resolution and the smallest resolution is
800x640, to which it is already set.  Only other resolutions are
640x480, 400x300 and 320x240.  How do I get other resolutions?

Hi and are you using a nvidia graphics? Is so have you installed the drivers for the card?

---

### Post by tc101 on 2008-09-01
> Hi and are you using a nvidia graphics? Is so have you installed the drivers for the card?  

I think I am using nvidia, and I did not install any drivers.  I just did the basic ubuntu install from a CD.  How do I install nvidia graphics?

---

### Post by overdrank on 2008-09-01
> **tc101 said:**
> I think I am using nvidia, and I did not install any drivers.  I just did the basic ubuntu install from a CD.  How do I install nvidia graphics?

Hi and the first place to look would be system, administration, hardware drivers.

---

### Post by Masoris on 2008-09-01
Run this:
```
gksu displayconfig-gtk
```
And change your display setting.

---

### Post by tc101 on 2008-09-01
> gksu displayconfig-gtk

That let me select my monitor, the Dell E228WEP widescreen.  I'm going to restart and tell you if it took.

---

### Post by tc101 on 2008-09-01
Something is messed up now.  There are a bunch of strange lines and patterns on the screen and the computer is unusable.  I am logging in from another computer to ask this.  How do I get back to a usable screen?

---

### Post by kjohansen on 2008-09-01
from the login screen you can select the gnome failsafe as the desktop manager from the options drop down.  then you can change settings back to the defualt while you find drivers.

---

### Post by tc101 on 2008-09-01
I don't get the login screen.  I am not sure if that is because I set it to auto login or because the monitor goes bad before the login screen comes up.

The screen is OK for a few seconds when the system first loads, but then the unusable screen comes up.

Isn't there some way I can reset to the default earlier in the process of booting up?

---

### Post by propwashz on 2008-09-02
cntrl-alt-backspace should kick you back to the login screen

---

### Post by tc101 on 2008-09-02
Thanks.  I am learning a lot.

---

### Post by tc101 on 2008-09-02
I tried ctrl-alt-bksp and the login screen comes up, but I can't see the part that would let me set gnome failsafe.  My guess is that this is because the screen is at such a low resolution everything is so big and the part where you set gnome failsafe is down in a corner that is not visible on the screen.

I tried ctrl-alt-F1 which lets me go directly into terminal mode, but then, when I enter:

gksu displayconfig-gtk

I get: GTK-Warning, cannot open display.

I should have backed up by xorg.config, so I could just move the old one back in, but I didn't back it up.  Is there anything I can do now?  I could just reinstall the system, back up xorg.config first thing, and then start playing with it again using the new things I have learned here.  However, it will take over an hour to reinstall, so if there is a better way please tell me about it.

---

