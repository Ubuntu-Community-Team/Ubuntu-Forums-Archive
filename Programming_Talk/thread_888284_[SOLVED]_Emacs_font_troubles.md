---
title: "[SOLVED] Emacs font troubles"
date: 2008-08-13
forum: Programming Talk
---

### Post by joesmoe10 on 2008-08-13
Hey,
I'm using emacs 23 on Ubuntu 8.04 and I can't seem to get Consolas to appear.  I have Consolas installed, I use it with gnome terminal and gvim but emacs substitutes some ugly proportional font in for it.  Here's what I have in my .emacs

```
(set-default-font "-*-Consolas-normal-r-*-*-14-97-*-*-c-*-iso8859-1")  
```

Thanks
joe

---

### Post by Jessehk on 2008-08-13
Try something like this:

**~/.Xresources**
```

Emacs.font: Consolas-11
emacs.FontBackend: xft

```

followed by

```

xrdb -merge ~/.Xresources

```

Assuming you've got a development version of Emacs with xft support; otherwise, delete that line.

---

### Post by joesmoe10 on 2008-08-13
thanks, worked perfectly
Do you know why the .emacs set-default-font didn't work?

---

### Post by Jessehk on 2008-08-13
No clue. I've only been using Emacs for a few months. :)

---

### Post by unutbu on 2008-08-13
I also use .Xdefaults to set my emacs font:```

Emacs*Font: Monospace-12:antialias=True
```

However, I've also found that this works:```

(set-default-font "Bitstream Vera Sans Mono-14")
```
when added to .emacs. I wish I understood the format for these ttf font strings -- I have no clue. However, since the above works, I wonder if this might also work:
```

(set-default-font "Consolas-11")
```

---

### Post by shifty2 on 2008-08-13
If your using emacs 23 there is an option to set the font through the menus - press C-c C-f and you will get a gtk font dialog box.

If you can get your font from there you should be able to do, as said earlier, (set-default-font "terminus-8") (for example).

---

