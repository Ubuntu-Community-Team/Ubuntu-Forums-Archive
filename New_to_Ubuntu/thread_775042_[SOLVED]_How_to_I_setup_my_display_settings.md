---
title: "[SOLVED] How to I setup my display settings?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by mysticmatrix on 2008-04-29
In Gutsy we had a tool of selecting driver to use, setting monitor setting, etc. How do I do this in Hardy?

I cannot find a item in menu regarding this. Help

---

### Post by lwvmobile on 2008-04-29
Its no longer available in Hardy by default, just make sure you install the proper driver. Generally, the restricted hardware manager does that if you have nvidia or ati, and then autoconfigs to your monitor. Then you can use screen res in preferences to change to your desired resolution if it isn't autoconfigured for you just right.

---

### Post by mysticmatrix on 2008-04-29
I have an intel onboard card and just wanted to set my monitor type correctly. The resolution applet detects it as 15" samsung while mine is a 17" monitor. Also I wanted to change my driver to i810.

BTW, why did they remove such a handy utility?

---

### Post by noynac on 2008-04-29
> **mysticmatrix said:**
> In Gutsy we had a tool of selecting driver to use, setting monitor setting, etc. How do I do this in Hardy? I cannot find a item in menu regarding this. Help

Are you talking about the Screen and Graphics tool? If so, it is located under the menu *Applications > Other.* It can also be opened by entering the following in a terminal window:

```
gksudo displayconfig-gtk
```

I believe this tool is now considered obsolete because X attempts to configure the video automatically.

---

### Post by mysticmatrix on 2008-05-01
Oh yes I found it under other section but I had to edit my menu to show it first. Thanks

---

