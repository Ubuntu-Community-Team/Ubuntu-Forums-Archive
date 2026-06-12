---
title: "Think Unity crashed"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by colinnn on 2011-11-17
Hey all,

I've installed ubuntu before but am still really quite new to all that and can only do the basics.

Got back to ubuntu yesterday after a 2 year hiatus and was quite pleased at the progress, however, within 15 minutes of installing it, managed to corrupt my root password shadow file (authentication token manipulation error) which i fixed by just reinstalling everything everything again.

However, think I've managed to screw up the window manager. I downloaded CCSM and started playing around with some of the settings, however, next time i booted up the laptop, i only have the title bar. ctrl-alt-T still works to bring up the terminal, however.

Attached is the screenshot.

I've looked around and no one seems to have a similar problem. I'm really quite brand new to this and am really very new to linux in general. Little help please? :) Really would like other answers than reinstalling the whole damn OS again. Thanks!

colinnn

---

### Post by Stray Wolf on 2011-11-17
It seems CCSM has a tendency of randomly disabling the "Ubuntu Unity Plugin".  Also, it gets disabled when you try to enable the desktop cube or other settings that haven't been integrated into Unity yet.  Just going to preferences in CCSM also disabled Unity.  Just reopen CCSM>Desktop>enable Ubuntu Unity Plugin.

Hope that works!

---

### Post by LukaHr on 2011-11-17
or try with this
```
unity --replace
```

---

### Post by Jacobonbuntu on 2011-11-17
....yes, but how should he get into the terminal, or ccsm, as there is an empty desktop :)

press ctrl+alt+t  , then type "ccsm" to get into the compiz settings manager, or type the other entry that was proposed

---

### Post by LukaHr on 2011-11-17
ups my bad, I forget about "ctrl+alt+"!

---

### Post by colinnn on 2011-11-19
it worked!!!

thanks everyone. sigh. no easy way to get eye candy on the newest release is there :)

---

### Post by Jacobonbuntu on 2011-11-19
good to hear!
don 't forget to mark the thread as solved :)

---

