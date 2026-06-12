---
title: "Syntax Highlighting editor for ARM assembler"
date: 2010-03-05
forum: Programming Talk
---

### Post by dubref on 2010-03-05
Curious if anyone has come across .lang file for ARM assembler.

If not gedit, then what editors do have syntax highlighting for ARM?

Staring at plaintext is hurting my eyes. :)

---

### Post by pbrane on 2010-03-05
You can write your own .lang for ARM. Have a look at */usr/share/gtksourceview-2.0/language-specs*. I copied c.lang to a local directory and modified it for .BZW files. It's not hard to do. Just choose one of the lang files that seems closest to what you may need. Then just copy your new and renamed arm.lang file back to */usr/share/gtksourceview-2.0/language-specs*.

---

### Post by diesch on 2010-03-05
Chances are that Emacs or vom have support for ARM assembler. As I don't do assembler programming I can't check it.

---

