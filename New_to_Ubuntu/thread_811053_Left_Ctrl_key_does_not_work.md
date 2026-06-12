---
title: "Left Ctrl key does not work"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by O-pos on 2008-05-28
Hi, after trying to configure my multimedia keys, Left Ctrl key stopped to work. When I check with xev in terminal, here is the output of the left Ctrl:

KeyPress event, serial 31, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 775722, (-206,-41), root:(306,9),
    state 0x0, keycode 185 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 775722, (-206,-41), root:(306,9),
    state 0x0, keycode 185 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

When I checked /etc/xmodmap.conf, everything was fine there, then I even changed Control_L into Control_R for teh key 185 (My left control key), to see what would happen, but nothing happened and xev output is still the same, including still mentioning Control_L.

Neither deleting xmodmap.conf~, nor restart did not help.

Any ideas?

---

### Post by SunnyRabbiera on 2008-05-28
do you have desktop effects enabled?
Or something along those lines?
Its possible that the left control key has too much associated with it.

---

### Post by O-pos on 2008-05-30
There was some error in xmodmap.conf file, after I corrected it, now my control key works fine, but first after every restart I have to enter in the terminal xmodmap /etc/xmodmap.conf, otherwise it will not work automatically. Any ideas how to automate it? I followed one of the links here in the forum but got stuck here:
cd /etc/X11/gdm/PostLogin
bash: cd: /etc/X11/gdm/PostLogin: No such file or directory

---

