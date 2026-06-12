---
title: "Why do I have to hit f-11 to see OS while in Firerfox?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-10-09
I might have accidentally hit something, but Firefox takes up the whole screen so I cant see any of the Linux OS bars unless I hit F-11. My other linux computer doesnt do this. How do I undo this f-11 thing?

---

### Post by PocketDog on 2008-10-09
F11 just tells Firefox to go fullscreen or windowed mode. Close it in windowed mode and it should re-open in the same state.

You can also change it in View - Full Screen.

Edit: Bigger problem than I thought.

[http://ubuntuforums.org/showthread.php?t=836508](http://ubuntuforums.org/showthread.php?t=836508)

Have you got the Autohide plugin installed? If not, it looks like a re-install of Firefox is your only solution :/

And another edit:

Does this fix it? (In Terminal) ```
firefox -width 1200 -height 800 &
```
(adjust the numbers for your own screen resolution). I can't replicate opening in full screen to test, I don't have Autohide installed.

I'll stop editing now ;)

---

