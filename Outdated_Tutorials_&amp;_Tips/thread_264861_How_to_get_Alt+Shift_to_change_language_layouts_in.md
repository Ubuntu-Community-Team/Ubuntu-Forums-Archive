---
title: "How to get Alt+Shift to change language layouts in KDE"
date: 2006-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by dresnu on 2006-09-25
I've been having this question for a long time and finally found a solution today so I decided to describe how I made it.
Using Kxkb (System Settings->Regional & Accessibility Keyboard Layout) didn't work with the alt+shift combination and the default ctrl+alt+K is just lame because it doesn't cycle; when reaching the last keyboard layout it stays there.
So if you want a fast way of changing languages without having to click everytime on the kxkb applet you have to... disable kxkb altogether! I don't know why but this little program seems to be a little buggy (for now) and messes up keymappings.
So if you have two or more languages to set you can write down their keymaps (you can see these in kxkb, before disabling it :-D) and edit directly your xorg.conf putting these two lines under the keyboard Section:```
Option          "XkbLayout"     "keymap_1,keymap_2,ecc.."
        Option          "XkbOptions"    "setxkbmap -option grp:alt_shift_toggle"

```
As an example here is mine with the italian keymap as second language:```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us,it"
        Option          "XkbOptions"    "setxkbmap -option grp:alt_shift_toggle"
EndSection

```
The second line inserted sets the shortcut to be alt+shift.
So apply these changes in xorg.conf make sure kxkb is disabled ("Enable keyboard layouts" unchecked) and restart X.
You should be able to cycle through keymaps without problems.
The only drawback is that you might not know which language you 're using because there won't be any applet showing it, but this, at least for me that I have just two layouts, is a smaller problem than having to click everytime on the kxkb applet.

Cheers ;-)

---

