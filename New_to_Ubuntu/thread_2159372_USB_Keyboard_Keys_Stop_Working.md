---
title: "USB Keyboard Keys Stop Working?"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by abexman on 2013-07-02
So this is strange. My Dell USB keyboard keys stop working in Ubuntu 12.04 at times. Cannot seem to figure out a way to bring them back. All the character keys seem to not be working but the "movement" keys work like alt-tab, arrows etc. But if I open a text editor and hit "qwertyuiosdfghj", nothing shows? The only place I seem to be able to enter characters is if I goto a lock screen (characters dont enter into the password field there) then goto to "switch user", I can then enter a username and password but get back to the original login, where I cannot enter characters? Is there some way to prevent this and/or fix this without rebooting? Thanks!

---

### Post by tgalati4 on 2013-07-02
Look in dmesg for keyboard errors:

```
dmesg | tail -50
```

I would suspect a bad cable or a failing USB port.  Examine the cable for worn spots and try moving it around.  Try it on another machine, perhaps a Windows machine and see how it behaves.

---

### Post by abexman on 2013-07-03
Wow! It was just the number lock key. Never seen that behavior before - a number lock that actually locks the rest of the keyboard! Doh!

---

