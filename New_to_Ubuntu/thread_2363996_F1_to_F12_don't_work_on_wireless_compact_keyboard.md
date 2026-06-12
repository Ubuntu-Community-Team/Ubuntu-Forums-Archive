---
title: "F1 to F12 don't work on wireless compact keyboard"
date: 2017-06-17
forum: New to Ubuntu
---

### Post by 700ghz on 2017-06-17
[COLOR=#242729][FONT=Arial]I bought compact keyboard. F1 = Fn + 1 and F2 = Fn + 2 ... [[IMG]https://i.stack.imgur.com/lyyyn.png[/IMG]]("https://i.stack.imgur.com/lyyyn.png")But F1-F12 keys don't work on my Ubuntu 16.04. For example F1 makes brightness up. I checked keycodes of F1-F12 keys and they are invalid. So F1 returns 232 keycode (instead 67).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I tried fix it using: xmodmap -e "keycode 232 = F1 F1 F1 F1 F1 F1 XF86Switch_VT_1" But it didn't help. F1 still change brightness. I tried remap other F1-F12 keys and no results. Xmodmap works only for non functional keys.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is it possible to fix F1-F12 keys? (Swap keycodes?)
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**Xmodmap configured correct but F1 still changes brightness**:[/FONT][/COLOR]
$ xmodmap -e "keycode 232 = F1 F1 F1 XF86Switch_VT_1" # IT DON'T HELP!!

$ xmodmap -pke # everything is OK!
keycode  67 = F1 F1 F1 F1 F1 F1 XF86Switch_VT_1 F1 F1 XF86Switch_VT_1
keycode 232 = F1 F1 F1 XF86Switch_VT_1

$xev # take a look: XKeysymToKeycode = 67... F1... everything is OK again... But it still changes brightness.
KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xf5, subw 0x0, time 921326, (236,-87), root:(236,403),
    state 0x0, keycode 232 (keysym 0xffbe, F1), same_screen YES,
    XKeysymToKeycode returns keycode: 67
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

$sudo evtest # scancode === 0??
Event: time 1497517949.369064, -------------- SYN_REPORT ------------
Event: time 1497517949.458895, type 1 (EV_KEY), code 224 (KEY_BRIGHTNESSDOWN), value 0

$ setxkbmap -print
xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwerty)" };
    xkb_types     { include "complete"  };
    xkb_compat    { include "complete+ledscroll(group_lock)"    };
    xkb_symbols   { include "pc+us+inet(evdev)+capslock(swapescape)"    };
    xkb_geometry  { include "pc(pc105)" };
};

[COLOR=#242729][FONT=Arial]P.S. Also F1-F12 work properly on Windows (on this machine).[/FONT][/COLOR]

---

