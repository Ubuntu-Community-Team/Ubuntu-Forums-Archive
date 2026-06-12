---
title: "How can I auto-format code?"
date: 2007-06-24
forum: Programming Talk
---

### Post by KIAaze on 2007-06-24
I'm looking for a command-line way to auto-format all my source files.

The "indent region" feature from xemacs works well, but it would be easier if I could do it by command-line.
A GUI doing it for all source files at once would also be OK.

---

### Post by xtacocorex on 2007-06-24
There is a program called astyle which will do indenting for C/C++/C# and Java.

---

### Post by Ramses de Norre on 2007-06-24
I use eclipse for programming and can right click a project and choose "format" to format all source files.
You can modify the formatting style as you like.

---

### Post by KIAaze on 2007-06-24
> **xtacocorex said:**
> There is a program called astyle which will do indenting for C/C++/C# and Java.

Thanks! That was exactly what I was looking for. :D

What is the most common style used? gnu, ansi, linux or kr? (when using C/C++)

---

### Post by Golyadkin on 2007-06-25
I am old-school, so I go for kr (Brian Kernighan and Dennis Ritchie) which is also if I am not mistaken, what is used in the Linux kernel sourcecode.
Dennis Ritchie originally created the C programming language, and is one of the core developers of UNIX, which Linux originated from.

Also btw, it doesn't really matter which one you use, as long as you use one and use it consistently.

---

### Post by KIAaze on 2007-07-06
Another similar question:
Is there an automatic shellscript formatting program?

I tried astyle and emacs with shellscripts, but they have problems when there's no ";" at the end of lines.
One line "if then fi" statements also get reformatted into multiple lines.

astyle even renders the shellscript non-executable. :/

---

