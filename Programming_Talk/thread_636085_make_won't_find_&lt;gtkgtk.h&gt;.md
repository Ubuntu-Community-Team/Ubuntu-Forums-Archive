---
title: "make won't find &lt;gtk/gtk.h&gt;"
date: 2007-12-09
forum: Programming Talk
---

### Post by hazel on 2007-12-09
I use a simple makefile for compiling test programs containing lines like:
```
 gcc program.c -o program `pkg-config gtk+-2.0 --cflags --libs` 
```

This worked perfectly well in Red Hat but when I do it in Ubuntu, it says it can't find the included header <gtk/gtk.h>, although pkg-config correctly reports /usr/include/gtk+-2.0 as one of the directories that should be searched for headers. Of course this means that none of my gtk functions is recognised and the compilation aborts with reams of error messages.

The strange thing is that if I copy the offending line and paste it into bash, it works normally. Obviously this is a work-around that can't easily be used with complicated multi-file programs. I have googled but can't find any reports of people having similar problems.

I am using make 3.81beta4.

---

### Post by Auria on 2007-12-09
did you install the gtk-dev or whatever it's called package?

---

### Post by Lux Perpetua on 2007-12-09
Does it work if you set SHELL to bash in your makefile?

---

### Post by Compyx on 2007-12-10
```

sudo apt-get install libgtk2.0-dev

```
should do the trick. This will install the headers needed with all of their dependencies such as the X11 headers.

---

### Post by hazel on 2007-12-10
> **Lux Perpetua said:**
> Does it work if you set SHELL to bash in your makefile?

Ah, that was what was wrong! SHELL was set to /bin/sh. I changed it to  /bin/bash and now everything works. But why didn't it before, given that /bin/sh is only a link to /bin/bash anyway?

---

### Post by geraldm on 2007-12-10
/bin/sh is not "just a link to" /bin/bash
The behavior is different, based on how the executable was called.
More information is in the usual place, see "INVOCATION"
```

man bash

```

Gerald

---

### Post by hazel on 2007-12-11
Yes, I see now. "sh" makes bash run like a Bourne shell and then it doesn't do command substitution. I tried 
```

sh
echo `pkg-config gtk+-2.0`

```
and nothing came back. 

Anyway, thanks for your help. I wouldn't have twigged that on my own.

---

### Post by geirha on 2007-12-11
In ubuntu 6.10 and higher, sh is a symlink to [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell") (used to be bash).
```
$ readlink /bin/sh
/bin/dash

```

---

