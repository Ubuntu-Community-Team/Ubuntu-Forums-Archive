---
title: "Compiling flac 1.3.1 installs 1.3.0"
date: 2014-12-01
forum: Packaging and Compiling Programs
---

### Post by ramicio on 2014-12-01
I am following the instructions [here]("http://www.linuxfromscratch.org/blfs/view/svn/multimedia/flac.html") and it installs version 1.3.0. I downloaded the correct archive, and have removed all traces of previously-installed versions. I did find a binary that did run as 1.3.1, but that's not what gets copied when I do a "make install". I've tried this multiple times. Also, how would I go about making it into a package so it shows up as an installed package?

---

### Post by andrew.46 on 2014-12-04
Can you show the results of:

```

andrew@ilium~$ **[COLOR="#FF0000"]flac --version[/COLOR]**
flac 1.3.1

```

And to easily integrate your new flac version into the Ubuntu package management system you could try using checkinstall...

---

### Post by ramicio on 2014-12-05
Weird. What I installed from the ubuntu repo says "1.3.0-2ubuntu0.14.04.1", which isn't even shown in the changelog to include the 1.3.1 fixes (or 1.3.0-3), but now that I've been uninstalling and reinstalling it, flac now reports itself as being 1.3.1.

---

### Post by andrew.46 on 2014-12-05
so one way or another you have the newest version :)

---

