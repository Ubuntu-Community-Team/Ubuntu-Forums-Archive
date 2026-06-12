---
title: "How do I add a python script to Conky?"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by Arcanist on 2011-10-08
Hi, I am trying to add a python script to Conky. I used ConkyWizard to set up my Conky configuration. I am trying to install [http://code.google.com/p/lyricsdownloader/downloads/detail?name=conkybanshee.py]("http://code.google.com/p/lyricsdownloader/downloads/detail?name=conkybanshee.py") ConkyBanshee, a script that shows what music is currently playing. I have added a title "Now Playing" and under that I would like the script to be run (see  screenshot below). Any help would be appreciated. :)


~Arcanist.

---

### Post by arzali on 2011-10-08
Hi Arcanist,
you can use execpi [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
example:
```
{execpi 10 conkyBanshee --template=/home/username/.Conky/conkyBanshee.template}
```

10 is the interval conkyBanshee is executed.

---

### Post by Arcanist on 2011-10-09
> **arzali said:**
> Hi Arcanist,
you can use execpi [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
example:
```
{execpi 10 conkyBanshee --template=/home/username/.Conky/conkyBanshee.template}
```

10 is the interval conkyBanshee is executed.

Thanks! :)

After figuring out where to put the code I managed to get it working. After that, I had to change some settings so the text wouldn't go out of the window.

Thanks again, Arcanist.

---

