---
title: "[SOLVED] Map a button to Alt"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by gali98 on 2008-09-17
Okay so I know this is so easy, but I can't figure it out.
I am trying to map one of my laptop buttons to Alt.
The keycode is 237. When I put
"keycode 237 = Alt_L" 
in ~/.Xmodmap
and run xmodmap on it, whenever I push that button it just hits Alt. I can't hold it (which is my whole purpose in using it)

So is there another way to do this, or what am I doing wrong?

Kory

---

### Post by gali98 on 2008-09-17
Okay I have been messing with xev and found that the normal alt key when pressed sends a state of 0x00 and when depressed (keyup) has a state of 0x08.
When I press this key that I am trying to bind, I get a state of 0x08 (keyup) even though it is depressed. When I let it up, it generates no event...
Come on keyboard gurus!!! I need help :)
Kory

---

### Post by gali98 on 2008-09-17
Okay another update..
When I map it to the alt key and press that button,
I sends the 0x00(keydown) event followed by the 0x08 (keyup) event.
However I never lift up....
Something screwy is going on around here....
Kory

---

### Post by jamesrl on 2008-09-17
I think you need a quick script to autoload your file with xmod on X login.
So if you add to ~/.xinitrc a command like:

```
xmodmap $HOME/.Xmodmap
```
You could be slightly better about it by doing something like 
```

xmodmapfile=$HOME/.Xmodmap
if [ -f $xmodmapfile ]; then
  xmodmap $xmodmapfile
fi

```
as now it won't give an error message if you don't have a .Xmodmap file.

If it doesn't immediately load on the next time you startx ([Ctrl]-[Alt]-[Bkspc] to restart X), you can try a quick

---

### Post by gali98 on 2008-09-17
Okay I have come to the sad conclusion that this button does not generate a keyup code so it cannot be used :(
Oh Well case closed.
Kory
Edit: Just now saw your post.
No that is not the program. I was using the command xmodmap which does it live.
No, it was a hardware problem. Thanks so much for replying though....

---

