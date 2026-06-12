---
title: "Acer &quot;eco&quot; button and linux keymapping..."
date: 2010-02-15
forum: Programming Talk
---

### Post by matchett808 on 2010-02-15
hi all...
I have an acer aspire 5738....thus far i have not found out how to make it's eco button work.... I have found this in dmesg though...:
[this is when i pressed the key to "on"]
[17306.104573] atkbd.c: Unknown key pressed (translated set 2, code 0x8a on isa0060/serio0).
[17306.104580] atkbd.c: Use 'setkeycodes e00a <keycode>' to make it known.
[17306.111914] atkbd.c: Unknown key released (translated set 2, code 0x8a on isa0060/serio0).
[17306.111920] atkbd.c: Use 'setkeycodes e00a <keycode>' to make it known.
[this is when i pressed the key to the "off" position]
[17326.333779] atkbd.c: Unknown key pressed (translated set 2, code 0x8b on isa0060/serio0).
[17326.333786] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.
[17326.340648] atkbd.c: Unknown key released (translated set 2, code 0x8b on isa0060/serio0).
[17326.340655] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.


now....I understand that this may bit a bit of a silly question but...i want to map they key to a script to - turn off wifi, mute and reduce brightness to 10% i reckon i can sort most of this out on my own except for how to actually launch the script (ie. link it to the button??)

Thanks in advance....

---

### Post by matchett808 on 2010-02-18
bump

---

### Post by rory526 on 2011-01-05
This might be helpful: [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

...or poke around with System>Preferences>Keyboard Shortcuts maybe?

---

