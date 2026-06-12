---
title: "Problems with windows in Ubuntu"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2008-09-26
So this just happened yesterday. I can't see the top of the windows (where the title and the buttons are) Also I can't get AWN to launch, I have it set up to launch at startup but it doesn't come up. I tried starting it from the accessories menu but it doesn't respond.

Alt+tab doesn't work and neither does the desktop switcher, is there anything I can do to fix this? Thanks in advanced guys

---

### Post by TadeoDiaz on 2008-09-26
I don't know if its really a solution but if i launch compiz fusion icon and reload the window manager everything goes back to normal

---

### Post by shifty_powers on 2008-09-26
did you by any chance have some updates yesterday?

---

### Post by TadeoDiaz on 2008-09-26
I think there were, not entirely sure though.

---

### Post by Tatty on 2008-09-26
Are you running emerald?

Try this to see if you get your window borders back:

```
metacity --replace
```

If this brings back your borders (which it should), then go back and re-enable compiz:

```
compiz --replace
```

If it does not work, then please post any error messages you are getting.

Also try starting awn from the terminal and see if any error messages appear:
```
avant-window-navigator
```

---

### Post by TadeoDiaz on 2008-09-26
I am using compiz and emerald as the window decorator (via the compiz fusion icon)

Once I launch the compiz fusion icon and reload the window manager I not only get my window borders back but I also get AWN back

---

### Post by davidryder on 2008-09-27
That has happened to me before. I just logged out and logged back in.

---

### Post by TadeoDiaz on 2008-10-02
> **Tatty said:**
> Are you running emerald?

Try this to see if you get your window borders back:

```
metacity --replace
```

If this brings back your borders (which it should), then go back and re-enable compiz:

```
compiz --replace
```

If it does not work, then please post any error messages you are getting.

Also try starting awn from the terminal and see if any error messages appear:
```
avant-window-navigator
```

Sorry it took a while to respond (was in the middle of exams when this happened)

Every time I restarted my window borders were gone and AWN was unresponsive

I replaced metacity as you suggested and it worked so I replace compiz and it seems to have gone back to normal (even after restart everything seems to be working fine)

Here is the terminal output:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

Thank you so much for all your help guys, it is really appreciated!

---

