---
title: "Enabling Compose Key"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-05-20
I am using Ubuntu 13.10 for a while now. I would like to use the compose feature for typing some special characters. However my Compose Key (System Settings -> Keyboard -> Shortcuts -> Compose Key) seems to be disabled and I am unable to define it. When I click on Compose Key it just remains disabled. I am able to define some other disabled shortcuts by clicking on them, but there are a few (including Compose Key an Alternative Characters Key) that cannot be defined. Do I have to enable these somewhere else, and if so, where?

---

### Post by Lorin Ricker on 2014-06-16
When I upgraded to 14.04 LTS, my Compose Key also went missing (undefined) again... My first attempts to get System Settings -> Keyboard -> Shortcuts -> Typing (group) -> Compose Key showed that this CK was disabled, and no matter how I clicked on it, I could not enable it -- my personal preference is to map this to AltGr (Right Alt).

I installed Unity-Tweak-Tool and went looking for any keystroke conflict, as it seems that Alt (left &/or right) is used to shortcut-activate that silly, useless HUD thing.  Tried to deactivate or remap the HUD's definition of Alt, with limited (confusing) results... But, when I went back to System Settings -> Keyboard -> Shortcuts -> Typing (group) -> Compose Key and clicked directly on the "Disabled" word, suddenly I got a popup menu that had these choices: "Disabled, Caps Lock, Right Win, Left Alt, Menu, Right Alt, Right Ctrl" -- Exactly what I want!  I selected Right Alt for my Compose Key shortcut, and I'm back in business!

I can't reproduce what I did to that Unity HUD shortcut -- the "user interface" for these Tweak Tools is absolutely lousy, buggy even -- but I'm suspicious that all of Canonical's focus on Unity is just creating confusion and lost commitment to other (shortcut) features which "used to work."  In any event, the various System Settings and Tweak Tools, some of which have to be manually installed, are poorly and inconsistently designed, very confusing (undocumented) to use, and don't seem to work consistently or reliably. "Your mileage may vary..."

---

### Post by Impavidus on 2014-06-16
I enabled the compose key the command line way (which should work on every UI). I created a file ~/.xmodmap with```
!use xev to find keycodes
keycode 133 = Multi_key
```and called **xmodmap ~/.xmodmap** from a login script. That made my Windows key act as a compose key.

The command **xev** can give you the keycodes you need. Start xev from a terminal, hit the key you want to use as compose key and the keycode (along with other information) will be printed in the terminal.

---

