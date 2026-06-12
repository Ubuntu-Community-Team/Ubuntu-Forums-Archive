---
title: "Keyboard Shortcuts Not Functioning"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-08-03
I really haven't a clue about this one, earlier today I noticed that basic keyboard shortcuts weren't working, things like CTRL + V, CTRL + C etc. Oddly certain shortcuts that I have set myself (Getting CTRL + ALT + Delete to open Gnome System Monitor) still work. They were working fine before, but just aren't today, and I haven't a clue what i've done to 'turn them off' as it were. Any ideas? Google didn't pull anything up unfortunately.

---

### Post by Xiong Chiamiov on 2008-08-03
Are application-specific shortcuts working (eg, ctrl+u to view source in Firefox)?  Can you copy+paste by selecting text, then middle-clicking?

---

### Post by Jack Bonner on 2008-08-03
> **Xiong Chiamiov said:**
> Are application-specific shortcuts working (eg, ctrl+u to view source in Firefox)?  Can you copy+paste by selecting text, then middle-clicking?

No, the application shortcuts aren't working either, and I don't have a middle click function on my mouse.

---

### Post by red_Marvin on 2008-08-03
I've noted that when switching my keyboard layout (to dvorak-se) the keymapping of the keys combined with alt etc. still uses the qwerty layout, you might want to check that out depending on what kind of layout you use.

---

### Post by Jack Bonner on 2008-08-03
> **red_Marvin said:**
> I've noted that when switching my keyboard layout (to dvorak-se) the keymapping of the keys combined with alt etc. still uses the qwerty layout, you might want to check that out depending on what kind of layout you use.


I just checked it out, it's still on the setting I changed it to, and It's only ever been on that setting.

---

### Post by Jack Bonner on 2008-08-03
Slight nudge

---

### Post by red_Marvin on 2008-08-03
You could always run xev (in a terminal), it gives a lot of info on what keys you type etc, so you should be able to see if the error is that the key combinations aren't generated/detected correctly, or if it's something else.

---

### Post by andersRson on 2008-08-10
I'm having this same problem - it seems that all special keys (ctrl, alt, shift...) stop working. I haven't figured out why or how to fix it, but logging out and then back in works. 
[edit]
Additionally, when this happens I have also observed that applications tend to crash a lot. Firefox crashes as soon as i type something anywhere, terminals ditto. I tried to start gdmsetup, and it just crashed as soon as it's windows showed up.
[/edit]
It is really annoying.
It seems to happen when I've been working for a few hours at least.
If anyone knows anything, I'd be grateful.

---

### Post by red_Marvin on 2008-08-10
Maybe you can find something useful from either *dmesg* or *cat .xsession-errors*

---

