---
title: "Encrypted, calendared journal program : ejourn"
date: 2006-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by DustoneGT on 2006-07-09
I spent quite a bit of time looking on the net for a good journal program
that lets me click on a date on a calendar and put journal entries.

What I found:
[http://www.public.iastate.edu/~chris129/code/ejourn/](http://www.public.iastate.edu/~chris129/code/ejourn/)

How to get it running in Ubuntu:

1.Click on the download link at the top and download the latest build.

The autopackage works perfectly so I used that because I am a n00b and I am not good at building from source, but you can build from source if that floats your boat better :).

2.Once installation is complete you can run the program by opening a terminal and typing ejourn-gui.

3.This is not a very good solution for long-term daily use....so let's add
an icon to your panel for it.

Right click on your panel and click on +Add to panel

Click on Custom application launcher at the top

Under Name and Comment fields type whatever you want to call it,
Under command type ejourn-gui.

Click on the button that says 'no icon', and select whatever icon you want
I used the gedit icon because it has a pen and a pad but use whatever.

Guides for using the program after installation can be found at:
[http://www.public.iastate.edu/~chris129/code/ejourn/Users/out/index.html](http://www.public.iastate.edu/~chris129/code/ejourn/Users/out/index.html)

Happy Journaling!

---

### Post by ryu kun on 2006-10-01
to insall the downloaded autopackage you may need to make it executable by

```
chmod -x <packagefilename>
```

---

### Post by GMFTatsujin on 2007-09-18
This is one of my bread-and-butter applications.  The autopackage did not work for me, so I compiled it from scratch ...

The only hitch was that I had to install some -dev packages for the compilation to work: libgtk2.0-dev and libgcrypt11-dev.  Otherwise the compilation bombed out with lots of missing libraries and syntax errors.

After installing those, it was a quick make install, according to the instructions in the README.  I guess all that compiling and relinking in Gentoo finally paid off. :)

---

