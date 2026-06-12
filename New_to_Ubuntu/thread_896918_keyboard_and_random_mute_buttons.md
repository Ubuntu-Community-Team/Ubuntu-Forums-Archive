---
title: "keyboard and random mute buttons"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by wonderingwhy on 2008-08-21
I seem to randomly be able to mute with the touch of a button, and it's not obvious which button it is I've used to mute. 

Is there a way to identify which keys have mute attached to them. Also is it possible to identify which keys unmute.

I'm using LogiTech LX710 Wireless keyboard.

Thanks

---

### Post by tech9 on 2008-08-21
not sure why it would mute as you would have to setup the keybaord shortcut...

but it wouldn't hurt to setup a shortcut for it to turn it back on by key stroke.

goto System>Preference>Keyboard Shortcuts

under sound - click on the shortcut's asci code and click new accelerator - you can setup the shortcut from there.

---

### Post by django0909 on 2008-08-21
You can assign new keys to different things by hitting alt+f2, and typing:

```
gksudo gconf-editor
```

It should be fairly self-explanatory, if it isn't, post back and we can help.

Also, does your keyboard have a mute key across the top? I'm assuming you aren't already hitting that.

-django

---

### Post by wonderingwhy on 2008-08-21
Thanks chaps, will have a look 
:KS

---

