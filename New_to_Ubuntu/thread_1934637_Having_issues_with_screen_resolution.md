---
title: "Having issues with screen resolution"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by Melyj on 2012-03-02
Hello, I'm Mel and I am new.

My issue is I can't change my resolution, I'm using version 10.04.

From what I can tell it's an issue with my graphics card (nvidia) but after much searching I can't find how to correct.

This is all very new to me, lol.

If it's of any help I'm using the 64bit OS.

---

### Post by Jake5 on 2012-03-02
Have you tried the appearance tab? there are different themes and resolutions you can set up in there.
Sorry, your comment is a little vague and I'm not sure what the real issue at hand is, do you need to switch to 1200x1080?

---

### Post by Melyj on 2012-03-02
Hey, yes I have.

I've tried changing it through display and through the nvidia driver manager.

It can't change my resolution to anything other than 640x768 (I think that's the one).

---

### Post by Melyj on 2012-03-03
With some help from my friend I now understand the issue is that nvidia-auto-setting is overriding any manual resolution I'm trying to set.

Does anyone know any workarounds for this?

---

### Post by winh8r on 2012-03-03
Can you open a terminal (press control + alt + T )

and enter this command:

```
xrandr
```

then hit enter and copy and paste the result in your next post.

---

