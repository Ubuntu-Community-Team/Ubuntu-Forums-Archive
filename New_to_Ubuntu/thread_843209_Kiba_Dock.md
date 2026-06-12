---
title: "Kiba Dock"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by BluePlum on 2008-06-28
So i installed [COLOR="Red"]Kiba-Dock[/COLOR], Everything went fine ( i hope ) and I'm hap with it. But my kiba-systray doesn' work and my icon-editor.
```

kiba-systray
bash: kiba-systray: command not found

icon-editor
bash: icon-editor: command not found

```

I found it doesn't work when i was trying to et my [COLOR="Red"]kiba-dock[/COLOR] to look like this [http://www.youtube.com/watch?v=rSZtTo1lXP8](http://www.youtube.com/watch?v=rSZtTo1lXP8) . How did he do it!!!!

---

### Post by iaculallad on 2008-06-28
> **BluePlum said:**
> So i installed [COLOR="Red"]Kiba-Dock[/COLOR], Everything went fine ( i hope ) and im hap with it. But my kiba-systray doesn' work.
```

kiba-systray
bash: kiba-systray: command not found
```

I foundi oesn't work when i was trying to et my [COLOR="Red"]kiba-dock[/COLOR] to look like this [http://www.youtube.com/watch?v=rSZtTo1lXP8](http://www.youtube.com/watch?v=rSZtTo1lXP8) . How did he do it!!!!

Instead of kiba-systray, try:

```
kiba-dock
```

---

### Post by BluePlum on 2008-06-29
Did you read the post? or was it hard to understand?

---

### Post by angry_johnnie on 2008-06-29
Typing **kiba-** in a terminal and then pressing the tab key twice will bring forth all the possible commands that start with "kiba-".

What I got was this:

kiba-dock            kiba-icon-editor.py  kiba-systray.py

So, it looks like what you're looking for is kiba-icon-editor.py, or kiba-systray.py.

I'm using an older version of kiba-dock, but if neither of those work for you, you could always try kiba- + tab + tab to see what your options are.

---

### Post by spiderbatdad on 2008-06-29
I think waht you are seeing is the result of the Akamaru package and the kiba-plugins. Akamaru allows for those "physics."

There is an old kiba thread here:[http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba-dock](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba-dock)

---

### Post by BluePlum on 2008-07-07
Yeah i have an Akamaru folder in my kiba dock folder. So i guess it wont work for me?

---

