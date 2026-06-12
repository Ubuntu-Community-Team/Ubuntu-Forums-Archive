---
title: "Desktop bleeds through in fullscreen games"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-11-16
I seem to be having a slight problem with games on Intrpid. If I play in the fullscreen, the desktop seems to bleed through, as in, I can still see the gnome-panels and icons, almost as if the window is transparent...um...any ideas?

---

### Post by handydan918 on 2008-11-16
Aliens. Definitely.
Or you have an nvidia/ati card and need the proprietary drivers...?

Nah. Aliens is better.

---

### Post by CatKiller on 2008-11-16
Alt-mousewheel is the default to make windows more transparent, I believe. It's possible that you've triggered this shortcut, and made the window translucent. If that's the case, you should be able to make it opaque with the same shortcut.

Or it could be something else entirely.

---

### Post by binbash on 2008-11-16
If you have enabled compiz : 

you have to disable compiz.

sudo apt-get install fusion-icon

---

### Post by shatteredmindofbob on 2008-11-17
> **CatKiller said:**
> Alt-mousewheel is the default to make windows more transparent, I believe. It's possible that you've triggered this shortcut, and made the window translucent. If that's the case, you should be able to make it opaque with the same shortcut.

Or it could be something else entirely.

Tried it, didn't work. 

Also, I've got a plain Intel integrated graphics chip, so I don't think it's a driver issue.

---

### Post by shatteredmindofbob on 2008-11-17
> **binbash said:**
> If you have enabled compiz : 

you have to disable compiz.

sudo apt-get install fusion-icon

But I like Compiz :( Isn't disabling kinda like killing someone because they've got a wounded arm?

---

### Post by CatKiller on 2008-11-17
Which games are they? Are they all running in Wine? Both Compiz and Wine have options that may help.

Also, you can just turn off Compiz when you're playing problematic games, and then turn it back on when you're finished. The games are fullscreen, so it's not like you're experiencing the effects while the game's running.

---

### Post by shatteredmindofbob on 2008-11-17
> **CatKiller said:**
> Which games are they? Are they all running in Wine? Both Compiz and Wine have options that may help.

Also, you can just turn off Compiz when you're playing problematic games, and then turn it back on when you're finished. The games are fullscreen, so it's not like you're experiencing the effects while the game's running.

I'm experiencing it with both Virus Killer (from the repos) and ScummVM if I put it in fullscreen mode. Works fine in a window, aside from not being very fun.

---

### Post by CatKiller on 2008-11-17
You can fiddle with the Compiz settings with CompizConfig Settings Manager (sudo aptitude install compizconfig-settings-manager).

Toggling the Unredirect Fullscreen Windows tab in the General Options plugin might help, as might looking at the options in the Workarounds plugin. The plugins that I'm aware of that affect the opacity of windows are "Opacity, Brightness and Saturation," "Opacify," and "Fading Windows." Perhaps one of these has an unhelpful configuration?

---

### Post by shatteredmindofbob on 2008-11-17
> **CatKiller said:**
> You can fiddle with the Compiz settings with CompizConfig Settings Manager (sudo aptitude install compizconfig-settings-manager).

Toggling the Unredirect Fullscreen Windows tab in the General Options plugin might help, as might looking at the options in the Workarounds plugin. The plugins that I'm aware of that affect the opacity of windows are "Opacity, Brightness and Saturation," "Opacify," and "Fading Windows." Perhaps one of these has an unhelpful configuration?

Ah, crap. Opacity, Brightness and Saturation is to blame. 

Though, I can just turn it off while gaming. 

Just in case anyone has any ideas to fix it without disabling, here's my configuration for that plug-in: 

name=gnome-panel | Tooltip | Menu | PopupMenu | DropdownMenuem 

Using it didn't seem to be a problem on Hardy.

---

### Post by Keen101 on 2008-11-17
I once had an old computer with the same problem, although it happened when watching DVD videos. Oddly enough it bleed through on Windowsxp **AND** Ubuntu. I think it was a driver issue.

---

