---
title: "Playing with Keyboad Shortcuts = Blank Screen"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by raydanator on 2008-09-28
So I was trying to install an older pc game using wine and, since it wasn't working, decided to restart and do something else. 

I couldn't eject the disc obviously, so I thought a keyboard shortcut might do the trick. But knowing nothing about what I was doing, hit all kinds of combinations: ctrl, shift, esc- ctrl, alt esc- ctrl, alt, del- you name it.

 Well, eventually it blanked out my menu. I pushed it again, (it was late, and I was stupid), and everything was gone but the wallpaper. Tempting fate once more, I pushed the combination to yield a blue screen, devoid of everything but a mouse. Whenever I did the combination, I got an X for a mouse as well. 

So, I rebooted into Xfce Session, hoping that it would erase my previous session, but it did not.

So long newb story short- I have a blank screen after login, and nothing but a mouse. What do I do? Thanks

---

### Post by fooman on 2008-09-28
> **raydanator said:**
> 
So long newb story short- I have a blank screen after login, and nothing but a mouse. What do I do? Thanks

do you at least see your wallpaper?  if so,  try pressing alt-f2 and see if it brings up a run dialog box.

if it does,  then type this into it and click run:

```
xfce4-panel &
```

and when your stuck like that...try ctrl-alt-backspace to get back to the login screen.

---

### Post by raydanator on 2008-09-29
Thanks man, that worked perfectly! I got the panel back, and edited settings so xfce controlled desktop once again. You rock!

---

