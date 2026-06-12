---
title: "Software for PHP Developer"
date: 2014-06-11
forum: Programming Talk
---

### Post by smithveg on 2014-06-11
Any recommended software for PHP developer for scripting purpose?
I need a software that can auto detect the html and php tag in color.

---

### Post by slickymaster on 2014-06-11
I'm moving this one from Ubuntu Application Development the to the **Programming Talk** sub-forum.

---

### Post by SeijiSensei on 2014-06-11
Because I do most of my coding over SSH to remote servers, I rely on a text-mode editor called **jed**.  It's a lightweight Emacs clone with various templates to color-code the text depending on type of file.  If you are used to graphical editors, you'll probably find this an unpleasant solution since you need to know a variety of Ctrl-key combinations for most tasks.  There is a menu as well, though it's less efficient than typing, say, Ctrl-y to retrieve cut text.

Jed is in the repositories if you're curious.

---

### Post by Duncubuntu on 2014-06-13
What you are looking for is a Syntax Highlighter, or IDE. A syntax highlighter does exactly what you asked for, look into: Geany. An IDE will do that, and more (Such as debug, run, etc) but can be confusing if you are new to coding (Eclipse and Aptana Studio seem to be popular, I use eclipse from time to time). And eventually when your comfortable, get started with Emacs and VIM. Ugly, but powerful tools.

---

### Post by tuhdo1710 on 2014-06-17
Checkout my Emacs guide: [http://tuhdo.github.io/emacs-tutor.html](http://tuhdo.github.io/emacs-tutor.html)

Emacs is a powerful editor and can be an IDE in need, with 3rd party plugins. You can even use Vim in Emacs too. Emacs is user friendly once properly setup and you get used to it.

Btw, you can use GNU Global with ggtags to navigate your source code, as demonstrated in my guide. Even though I demonstrated using Linux kernel source code, but GNU Global works for PHP too.

---

