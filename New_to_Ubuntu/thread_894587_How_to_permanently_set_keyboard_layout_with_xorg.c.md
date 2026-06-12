---
title: "How to permanently set keyboard layout with xorg.conf"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by eragon100 on 2008-08-19
Hi guys!

How do I permanently select us international with dead keys as a layout in xorg.conf, (so ´ + e creates an accented e), because the setting isn´t remembered when I set it in keyboard preferences? I have already tried to do it myself, so this is my current xorg.conf keyboard section:

Now what is the name for the layout us international with dead keys, instead of just us international?

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "intl"
EndSection

---

### Post by anthropoidster on 2008-08-19
This works for me:

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "intl"
    Option         "XkbOptions" "lv3:ralt_switch"

Hope it helps...

---

### Post by eragon100 on 2008-08-19
That only makes the right alt key the dead key, I want to be able to use ´ + e to make an e with an accent, and shift + ´ + u to make an umlaut, etc. What do I have to type in to be able to do that?

---

