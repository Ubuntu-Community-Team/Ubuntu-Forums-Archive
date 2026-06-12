---
title: "text 2 speech"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by TechDragon on 2008-09-28
Hello,

I need an easy to use, text to speech program that can read web pages as well as documents

Ideas, suggestions?

---

### Post by Cl0ud9 on 2008-09-28
May not be the best, but for documents try espeak.
```

espeak -f <text file>

```

man espeak for more information.

---

### Post by cariboo on 2008-09-28
You can set up Orca to do text to speech. Press Alt-F2 and enter:

```
orca -s
```

This will bring up the Orca setup menu. You can setup how the program treats text as well as other assistive technologies. Orca is installed by default.

Jim

---

### Post by rennau80 on 2010-07-20
this tool can convert ascii (and html is also ascii) or pdf to an mp3 audio file (see entry #19):
_[http://ubuntuforums.org/showthread.php?t=1364786&page=2](http://ubuntuforums.org/showthread.php?t=1364786&page=2)_

if you want to use that tool for an html file simply rename your html file from website.html to website.txt and then call that tool via for example:


[FONT=monospace]./pdf2mp3.py -v en -f website.txt -o website.mp3[/FONT]
and an mp3 is being created. :)

---

