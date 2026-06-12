---
title: "xemacs js2-mode in 10.04"
date: 2010-09-26
forum: Programming Talk
---

### Post by jethro1138 on 2010-09-26
Hi there,

I'm trying to get js2-mode going in xemacs (since javascript-mode doesn't handle jquery very well). I installed the js2-mode package, but xemacs doesn't see it. I got it to see it by adding these lines to my ~/.xemacs/custom.el: 

```

(autoload 'js2-mode "js2" nil t)
(add-to-list 'auto-mode-alist '("\\.js$" . js2-mode))

```

And symlinking /usr/share/emacs/site-lisp/js2-mode/js2.el to /usr/share/emacs/site-lisp/js2.el. 

Which I think is wrong, but hey, at least it finds it now. 

However, it won't load it. When I meta-x js2-mode, it says "Malformed list: :foreground" and goes back to fundamental mode.

When I try to byte compile it, it gives a crazy amount of errors and results in the same error. 

Anyone have ANY idea what I might be doing wrong here? Or even better, how to fix it?

---

