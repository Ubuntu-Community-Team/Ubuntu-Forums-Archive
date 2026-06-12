---
title: "[SOLVED] Compiz-free dock"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by sbussy89 on 2008-05-19
I am running Ubuntu in VBox so I can't run compiz... is there a dock like AWN that I can use without compz?  If not, am I right in saying that I cannot run compiz in VBox?

---

### Post by sam_delta on 2008-05-19
see [http://ubuntuforums.org/showthread.php?t=799368](http://ubuntuforums.org/showthread.php?t=799368)

sam

---

### Post by angry_johnnie on 2008-05-19
**If** you are using Hardy (8.04), it's a lot easier.

Hit Alt+F2 and type

```
gconf-editor
```
and then press enter.

Find  **Apps > Metacity > General**

Check the box that says **compositing_manager**

and that's it! :-)

Now metacity can be used as a compositing window manager, which means you can run AWN or kiba-dock without having to enable compiz.

---

### Post by sbussy89 on 2008-05-19
First response didn't quite work... it blocked out a bar about as wide as the dock across the entire bottom of the screen.  Second response worked perfectly though... Thanks :)

---

### Post by vishzilla on 2008-05-19
I guess SimDock doesnt require Compositing

---

### Post by lostlinuxkiwi on 2008-05-19
i use wbar on a laptop that i cant run compiz on because of video card issues.

its really light weight and there is a GUI configuration editor available for it now so you dont have to do it all through the command line and you can change the icons.

only thing is you will need a little script to get it to autostart but thats not hard.

---

