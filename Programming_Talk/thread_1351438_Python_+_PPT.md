---
title: "Python + PPT"
date: 2009-12-10
forum: Programming Talk
---

### Post by MikeVaughanG on 2009-12-10
I have a very simple (I hope) question. 

Is there a way to launch Powerpoint Presentations in Python.. ?

like..


if something==true
   launchppt

Any help is appreciated.

---

### Post by -grubby on 2009-12-10
You could use the [Subprocess](http://docs.python.org/library/subprocess.html) module to launch an external viewer.

---

### Post by Zugzwang on 2009-12-11
> **-grubby said:**
> You could use the [Subprocess](http://docs.python.org/library/subprocess.html) module to launch an external viewer.

...and in Linux, you probably want to use the command "xdg-open" to do so as it will call the "default" application for doing so. Call it using the subprocess functions as stated above.

```

xdg-open <yourpresentation.ppt>

```

---

