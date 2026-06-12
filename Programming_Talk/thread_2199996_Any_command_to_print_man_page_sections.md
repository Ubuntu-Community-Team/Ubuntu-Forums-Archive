---
title: "Any command to print man page sections?"
date: 2014-01-17
forum: Programming Talk
---

### Post by kangaba on 2014-01-17
Hi,
is there any param for "man" to print the section numbers with their description ([example]("http://www.december.com/unix/ref/mansec.html")), or any standalone command?

---

### Post by steeldriver on 2014-01-17
Not sure exactly what you're asking, but that information is in the man page for man itself - so the command

```
man man
```

will show it

```

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

```

---

### Post by TheFu on 2014-01-17
What have you tried already? What were the results?

There are different manpage formats - more than I would have believed possible.
I would specify the section wanted and redirect the output as ASCII to a file, then edit away the parts I didn't want to send to a printer.
nroff, groff are the commands we used to do this years ago.  These have different filters to handle different inputs.

Something like this:
 **gunzip -c  passwd.5.gz | groff -T ascii |more**
seemed to work.

---

### Post by ofnuts on 2014-01-17
Funny you ask that, since the man pages were meant to replace the hardcopy documentation...

If you intend to print pages, there are utilities around to convert them to some fancier formats (man2html)

---

### Post by kangaba on 2014-01-17
Yes it's ironic..  "man man" is good enough, problem solved, though issuing "man" on "man" reminds me of the Inception movie.

---

