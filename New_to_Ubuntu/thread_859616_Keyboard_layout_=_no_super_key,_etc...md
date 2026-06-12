---
title: "Keyboard layout = no super key, etc.."
date: 2008-07-14
forum: New to Ubuntu
---

### Post by ddixonr on 2008-07-14
I've had this problem for a long time now, and I thought I give it another shot. When I first installed Gutsy about a year ago, everything worked fine. After a few updates, I noticed the Super key not working. Then the "right-click key". Actually the right-click key initiates the screen saver & locks the screen.

I've tried to use different layouts, but none make any improvements. And, yes, I have tried the "Super is mapped to the Win Keys" option. I have a Toshiba Satellite A105 S4284 and currently running Hardy. In case it helps, here is the keyboard section of Xorg.conf:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Any help is appreciated. Thanks

---

### Post by Shazaam on 2008-07-14
Here is mine for comparison (8.04.1, PS/2 keyboard)...
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection
```
and...
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection
```

---

