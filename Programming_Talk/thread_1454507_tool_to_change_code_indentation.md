---
title: "tool to change code indentation"
date: 2010-04-14
forum: Programming Talk
---

### Post by giuspen on 2010-04-14
Hi,
It often happen to me to continue the job of collegues that use an indentation different than mine.
I use an indentation of 3 spaces while I have collegues that use 2 or 4 spaces.
Is there a tool to fix the code indentation? I use geany but it seems to me that it's not possible to do it with that.
Thanks in advance.

---

### Post by dearingj on 2010-04-14
I'm not sure, but I think CodeBlocks's code formatting plugin has the ability to do that.

---

### Post by schauerlich on 2010-04-14
Indent will do the trick. See
```
man indent
```

To do what you want:

```
indent infile.c outfile.c -i3
```

outfile.c will be overwritten, of course.

---

### Post by Milliways on 2010-04-15
astyle is a Formatter for C, C++, C#, and Java Source Code, which among other things can change indenting.
[http://astyle.sourceforge.net/astyle.html](http://astyle.sourceforge.net/astyle.html)

---

### Post by soltanis on 2010-04-15
In my experience, indent has done nothing but mess up my files. I personally have something against that tool.

---

