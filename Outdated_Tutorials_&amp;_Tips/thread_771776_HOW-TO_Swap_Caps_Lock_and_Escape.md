---
title: "HOW-TO: Swap Caps Lock and Escape"
date: 2008-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by timo1023 on 2008-04-27
Swapping Caps Lock and Escape can be very helpful, especially for vim users, as it reduces stress on your fingers.

Instructions for Gnome:
1. System -> Preferences -> Keyboard
2. Select Layouts tab, then Layout Options
3. Click on 'CapsLock key behavior'
4. Click on 'Swap ESC and CapsLock'

That's it.

---

### Post by telepathetic on 2008-05-09
This works except for the annoying fact that the CapsLock light is still being governed by actual CapsLock presses instead of ESC presses (which would make more sense after the remapping).  Is there anyway to get the ESC to control the CapsLock light!?  this would seem to be a bug?  where would I report it?

My ESC/CapsLock journey thus far for anyone interested in a tale of triumph and tragedy:
I actually had this working properly in Gutsy after some hack on the key mapping files I picked up from a random blog, but boy did that screw up my Hardy upgrade-- I was stuck with permanent CapsLock anytime I happened to touch that button (which by that time had become my muscle-memory's ESC button).  All my letters were all caps forever until a full reboot.  So then I decided to install Hardy from scratch, in hopes that this nice little option would work correctly.  Mostly-- but not quite.

---

### Post by davidmaxwaterman on 2009-03-22
> **timo1023 said:**
> Swapping Caps Lock and Escape can be very helpful, especially for vim users, as it reduces stress on your fingers.

Instructions for Gnome:
1. System -> Preferences -> Keyboard
2. Select Layouts tab, then Layout Options
3. Click on 'CapsLock key behavior'
4. Click on 'Swap ESC and CapsLock'

That's it.

I wonder if there's a way to, instead of *swapping* the keys, have *both* be escape. This aids in the learning the new key position in, for example, 'vi'. When they are swapped, I still keep pressing the real 'esc' key, but it does a caps lock, which is really annoying in 'vi'.

Any idea how to do that?

Max.

---

### Post by jonatin on 2009-06-18
> **davidmaxwaterman said:**
> I wonder if there's a way to, instead of *swapping* the keys, have *both* be escape. This aids in the learning the new key position in, for example, 'vi'. When they are swapped, I still keep pressing the real 'esc' key, but it does a caps lock, which is really annoying in 'vi'.

Any idea how to do that?


Under 9.04 one of the keyboard and layout options instead of "*Swap ESC and CapsLock*" is "***Make CapsLock an additional ESC***" which does the trick.

---

### Post by dvhart on 2009-07-15
> **jonatin said:**
> Under 9.04 one of the keyboard and layout options instead of "*Swap ESC and CapsLock*" is "***Make CapsLock an additional ESC***" which does the trick.

For me, this option Makes CapsLock an ESC key, and makes ESC do nothing at all.  Any ideas on what might be causing that?

---

### Post by davidmaxwaterman on 2009-07-16
> **dvhart said:**
> For me, this option Makes CapsLock an ESC key, and makes ESC do nothing at all.  Any ideas on what might be causing that?

Same for me. :/

---

### Post by dvhart on 2009-07-16
> **davidmaxwaterman said:**
> Same for me. :/

I spent TOO LONG looking into this.  Turns out the gnome-keyboard-preferences tool uses XkbOptions via the /etc/init.d/console-setup script and uses /etc/default/console-setup for configuration if you Apply Globally.  To make the option work as described in the GUI (making caps lock an ADDITIONAL Escape key - not the ONLY one) you need to edit the Xkb config file here:

/usr/share/X11/xkb/symbols/capslock

as follows:

xkb_symbols "escape" {
    key <CAPS> {        [       Escape  ]       };
    key <ESC>  {        [       None    ]       };  <-- delete this
};

So I found the fix, can someone else open a bug?  We should either change the description in the gui tool, or change the xkb file as above (I prefer the latter).  I'll try to open a bug if no-one else gets around to it.

---

### Post by xqyz on 2009-07-16
> **dvhart said:**
>  So I found the fix, can someone else open a bug?  We should either change the description in the gui tool, or change the xkb file as above (I prefer the latter).  I'll try to open a bug if no-one else gets around to it.

Thank you very much, amazing find, I love it, makes vim even better imho.

---

