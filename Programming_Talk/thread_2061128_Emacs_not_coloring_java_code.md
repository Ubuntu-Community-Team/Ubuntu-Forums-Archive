---
title: "Emacs not coloring java code"
date: 2012-09-21
forum: Programming Talk
---

### Post by PotatoDumplings on 2012-09-21
When I first installed ubuntu, Emacs would provide coloring on my java code to denote variables and so forth.  Since, that feature has stopped working.  When I ssh into another computer and use its version of Emacs, the coloring works fine.  Removing and reinstalling Emacs hasn't had any effect.  Any ideas what might be going on?

---

### Post by schauerlich on 2012-09-21
Does syntax highlighting still work for other languages? What about in the shell itself, or other programs run from the same terminal? Might you have disabled ANSI colors on your terminal emulator? Also, post your ~/.emacs file (or perhaps ~/.emacs.d/init.el)

---

### Post by PotatoDumplings on 2012-09-22
It also didn't color python code when I tried that.  The gedit program does color code.

---

### Post by spjackson on 2012-09-22
> **PotatoDumplings said:**
> When I first installed ubuntu, Emacs would provide coloring on my java code to denote variables and so forth.  Since, that feature has stopped working.  When I ssh into another computer and use its version of Emacs, the coloring works fine.  Removing and reinstalling Emacs hasn't had any effect.  Any ideas what might be going on?
If removing and reinstalling hasn't fixed it, then it's probably something in your personal emacs config. Rename ~/.emacs and see whether that fixes it. If so, then you know that it's something in that config.

Are you running emacs in its own window or in a terminal? If you are running it in a terminal then there are additional possible causes. e.g. emacs might be aliased to emacs --color=never . You could try emacs --color=always . Does your terminal support color outside of emacs? e.g. does ls ouput color?

---

