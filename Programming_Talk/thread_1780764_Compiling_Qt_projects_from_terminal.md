---
title: "Compiling Qt projects from terminal?"
date: 2011-06-12
forum: Programming Talk
---

### Post by carlos21 on 2011-06-12
I would like to know how to compile Qt projects (.pro) with GLib from the terminal. I've looked for the answer but could never find it.

---

### Post by cgroza on 2011-06-12
Show us the command you are using now. Maybe you are missing some flags or link targets.
Also, are you linking to GLib and Qt?

The errors would be useful too, don't forget to put them in code tags.

---

### Post by carlos21 on 2011-06-12
I usually just use qmake which works fine for my other projects that don't use GLib. I have tried linking GLib but apparently that doesn't work using the *export* command so I'm faced with the problem that glib.h is not finding it's own headers because it's looking in the wrong path.

I'm getting errors like:

```
 galloca.h: not found
```

---

### Post by cgroza on 2011-06-12
You forget to post the command you are using...

---

### Post by NovaAesa on 2011-06-12
Hey! Isn't this the same problem you posted about here [http://ubuntuforums.org/showthread.php?t=1780382](http://ubuntuforums.org/showthread.php?t=1780382) that I gave you an answer for?

---

### Post by carlos21 on 2011-06-12
> **NovaAesa said:**
> Hey! Isn't this the same problem you posted about here [http://ubuntuforums.org/showthread.php?t=1780382](http://ubuntuforums.org/showthread.php?t=1780382) that I gave you an answer for?


Yeah, actually no. A bit like that but in this thread I more or less identified the error. :/ sorry for any inconveniences

---

