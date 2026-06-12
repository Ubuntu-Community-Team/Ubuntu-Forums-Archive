---
title: "Xemacs coding system error"
date: 2009-04-16
forum: Programming Talk
---

### Post by maitrebart on 2009-04-16
I installed xemacs (21.4.21-1ubuntu3.1) from synaptic.

When I compare 2 text files (ediff-buffers), I get the following error:

No such coding system: emacs-internal

Does any "xemacser" have any clue how to fix this error?

Here are the packages installed:

xemacs21
xemacs21-basesupport
xemacs21-bin
xemacs21-gnome-mule
xemacs21-mule
xemacs21-mulesupport
xemacs21-support

---

### Post by maitrebart on 2009-04-16
Found this on the net:

[http://tracker.xemacs.org/XEmacs/its/issue494](http://tracker.xemacs.org/XEmacs/its/issue494)

As indicated in the solution, setting the variable ediff-coding-system-for-write to 'raw-text fixed the problem.

I have no clue what is a coding system nor how many of them actually exist, but it seems that raw-text is one of them!

---

### Post by mike-g2 on 2010-09-23
I realize this is an old thread, but surprisingly I've run into this same problem with 10.04. For anyone else wondering, this fix still works.

For those who are less xemacs savvy, the way to fix this is to modify your .xemacs/custom.el file so that it reads something like this,
```

(custom-set-variables
 '(TeX-force-default-mode t)
 .
 .
 .
 '(ediff-coding-system-for-write 'raw-text)
)

```
You will need to recompile this file if you have a custom.elc in your .xemacs folder.  You can do this within xemacs by opening the custom.el file  and then choosing "Recompile" under the LISP menu.

Mike

---

