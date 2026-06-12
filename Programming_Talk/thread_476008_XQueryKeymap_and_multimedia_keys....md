---
title: "XQueryKeymap and multimedia keys..."
date: 2007-06-16
forum: Programming Talk
---

### Post by GenPFault on 2007-06-16
I'm trying to re-purpose the ideas here:
[http://insecure.org/sploits/xsecurekeyboard_fequent_query.html](http://insecure.org/sploits/xsecurekeyboard_fequent_query.html)
here:
[http://www.cs.bgu.ac.il/~orlovm/code/realkey.C](http://www.cs.bgu.ac.il/~orlovm/code/realkey.C)
and here:
[http://www.acm.vt.edu/~jmaxwell/programs/xspy/xspy.html](http://www.acm.vt.edu/~jmaxwell/programs/xspy/xspy.html)
to make a hotkey program that is immune to the full-screen lockout effect in programs like ppracer.  Unfortunately I'm having trouble getting XQueryKeymap to see all my multimedia keys.  The topmost program tends to see the most though.

Are there any low-level X mechanisms that might prevent XQueryKeymap from seeing changes in some key codes?  Note that the global KDE hotkeys for volume and such work just fine, so *some* applications can see the keys, just not while there's a full-screen app running.

---

### Post by GenPFault on 2007-06-20
Update:  Ok, the keys that the above-mentioned code snippets can't detect seem to be issuing "instantaneous" KeyPress/KeyRelease event pairs (as seen by xev).  Is there any way to tell X to stop doing this?

---

### Post by GenPFault on 2007-07-30
Alrighty, looks like it's an issue with the default old-style X keyboard driver.  Switching to the evdev driver fixes the problem.  Only gotcha is that my keyboard (a Microsoft Natural Keyboard Pro) appears as two evdev devices, one for the keyboard keys proper and one for the multimedia keys.  Here are my InputDevice sections:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "evdev"
        Option          "Name"  "Microsoft Natural Keyboard Pro"
        Option          "Phys"  "*input0"
        Option          "CoreKeyboard"
        Option          "XkbModel"      "evdev"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard 2"
        Driver          "evdev"
        Option          "Name"  "Microsoft Natural Keyboard Pro"
        Option          "Phys"  "*input1"
        Option          "SendCoreEvents"
EndSection

```

It also messes up the default xmodmap.  Here's my modified .Xmodmap file:
```

keycode 118 = Insert
keycode 144 = XF86Search
keycode 152 = XF86MyComputer
keycode 164 = XF86Favorites
keycode 174 = XF86Stop
keycode 179 = XF86AudioMedia
keycode 225 =
keycode 230 =
keycode 232 =
keycode 237 =
add mod4 = Super_L Super_R

```

Thanks to the guy on the xorg IRC channel for helping me figure this out!

---

### Post by monti on 2008-05-25
The evdev driver didn't solve my problem with immediate KeyRelease (on a small laptop (Kohjinsha SH6) with at japanese keyboard).  I've outlined my problem in [http://lists.freedesktop.org/archives/xorg/2008-May/035351.html](http://lists.freedesktop.org/archives/xorg/2008-May/035351.html).

This is definately a software problem: when I use "showkey -s" on the text console, the key doesn't send a KeyRelease immediately.

Does anyone have a clue on how to solve this?

---

