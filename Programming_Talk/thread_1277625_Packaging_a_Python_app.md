---
title: "Packaging a Python app"
date: 2009-09-28
forum: Programming Talk
---

### Post by gbablon on 2009-09-28
Hey all,

Coming back to this forum after a very speedy reply to an earlier post got me through a first Python hurdle.

I'm working on a Python, GTK / Glade app. The app is nearing completion, and I want to compile / package it into a single file for easy distribution. At the moment, the app consists of a number of files (the Glade configuration files, the Python script, and some C files in the /src/ folder) and I'd like to bring that all together into one, easily executable but [ideally] not modifiable file. Also, the app makes use of the MySQLdb library which isn't available on most standard Linux setups, but I'd really like to be able to distribute the app without any external dependencies.

If this was Windows, I'd be making an exe.

It's Linux though, so I still need to learn.

Any ideas? Thanks for your help.

---

### Post by -grubby on 2009-09-28
Maybe you should try [CX Freeze](http://cx-freeze.sourceforge.net/)?

---

### Post by benj1 on 2009-09-28
well you could make a .deb, theres instructions in one of the stickies or let python do it with a setup script [http://docs.python.org/distutils/setupscript.html#setup-script]("http://docs.python.org/distutils/setupscript.html#setup-script").

---

