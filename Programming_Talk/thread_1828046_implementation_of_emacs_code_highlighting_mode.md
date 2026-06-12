---
title: "implementation of emacs code highlighting mode"
date: 2011-08-18
forum: Programming Talk
---

### Post by ceclauson on 2011-08-18
Hi all.

I'm currently working with an application-specific programming language of my own design.  The parser and back end code are written in Perl.

I'm *moderately* interested in developing an emacs mode that would do appropriate syntax highlighting.  Does anyone have any experience with this/know what this involves?  I have pretty robust parsing code already that it seems should be easy to adapt, but it is in Perl.

Thanks in advance.

---

### Post by cgroza on 2011-08-18
Do you know Emacs Lisp? If so, you can take a look at an existing mode, such as python.el and take a look at the way they do syntax highlight.
Once you get a list of the functions you need, use the Emacss' built in documentation to get an idea of how to use them.

---

