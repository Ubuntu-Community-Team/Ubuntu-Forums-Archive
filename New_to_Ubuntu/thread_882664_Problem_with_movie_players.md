---
title: "Problem with movie players"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by dozd on 2008-08-07
Hi, I use Totem movie player and VLC. They worked good. But this days appears some problem. When I play movie on the screen are lines in different colors.How to fix this problem?

---

### Post by gerben1 on 2008-08-07
In Vlc you can try some other video output module:
settings->preferences->video->output modules
there you'll need to check "advanced option", it will probably be on default (which I think is Xvideo), X11 will probably work without the lines, but you'll get some "pixelate" effect OpenGl may be best if it works for you.

No clue about Totem, it seems to be one of those programs that has hardly any options at all... my usual way of handling with this is to just not use the program if it does not work satisfactorily and install something similar that does have options that you can tweak to get the program working the way you want.

---

### Post by dozd on 2008-08-07
Thanks, now is OK :)

---

