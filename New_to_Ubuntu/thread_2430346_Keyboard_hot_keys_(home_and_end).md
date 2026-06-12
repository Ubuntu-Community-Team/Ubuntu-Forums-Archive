---
title: "Keyboard hot keys (home and end)"
date: 2019-10-31
forum: New to Ubuntu
---

### Post by trex166 on 2019-10-31
Hi guys, just recently joined the community
was trying to figure out how to solve the issue of the hot keys
I'm used to press the 'end' and 'home' hotkeys to go to the end or start of the line (like in windows)
anyone knows how can I replicate it in ubuntu 18.04?
Thanks

---

### Post by Impavidus on 2019-10-31
The home and end keys are supposed to work out of the box. Any particular application where they don't work, or just everywhere? Can you run the command```
xev
```in a terminal and hit the home and end keys, then close the window? It will produce a lot of output in the terminal. The moment you hit the keys, it should produce something like```
KeyPress event, serial 34, synthetic NO, window 0x6000001,
    root 0x122, subw 0x0, time 1997646, (-273,-92), root:(321,210),
    state 0x10, keycode 110 (keysym 0xff50, Home), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6000001,
    root 0x122, subw 0x0, time 1997693, (-273,-92), root:(321,210),
    state 0x10, keycode 110 (keysym 0xff50, Home), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x6000001,
    root 0x122, subw 0x0, time 2002169, (-273,-92), root:(321,210),
    state 0x10, keycode 115 (keysym 0xff57, End), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6000001,
    root 0x122, subw 0x0, time 2002238, (-273,-92), root:(321,210),
    state 0x10, keycode 115 (keysym 0xff57, End), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

