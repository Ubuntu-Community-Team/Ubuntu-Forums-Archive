---
title: "What's happened to my Firefox???"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-06-15
Hi, I don't know what caused this to happen, but Firefox has disappeared from the top panel and from the Applications>Internet - it has reappeared in Applications>Other with no icon.

I tried going into Synaptic and reinstalling it and everything associated with it, that didn't work. 

The program itself still runs, I am using it now to post this.

Thanks for any help.

James

---

### Post by Ub1476 on 2008-06-15
You can use this command to see where Firefox is installed and located:

```
whereis firefox-3.0 
```

Might be it's called firefox3, or just firefox.

To add it to the panel, right click and "(custom) add application". I think the Firefox icon is located in /usr/share/pixmaps.

To add an icon to Firefox in the application menu, right click, edit menus, internet, new application. 

I'm not using Ubuntu/Gnome right now, so some instructions might be wrong.

Ps: you don't need to enter the location for the command to launch firefox, just the name (like "firefox3).

No clue what happened though.

---

### Post by Jimmy9pints on 2008-06-15
Thanks for your answer. I'll try it. 

This is a screenshot of what's happened which I have only just managed to upload.

---

### Post by Joeb454 on 2008-06-15
> **Ub1476 said:**
> You can use this command to see where Firefox is installed and located:

```
whereis firefox-3.0 
```



I think you can also use ```
which firefox
``` Which should work, and if you're running Hardy (8.04) it will give the version that came by default (which should now be RC1 I believe)

After you have done this you could try manually adding a shortcut to your panel/menu and see if that works :)

---

