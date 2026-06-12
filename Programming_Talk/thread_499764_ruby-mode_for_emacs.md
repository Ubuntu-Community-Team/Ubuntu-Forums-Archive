---
title: "ruby-mode for emacs"
date: 2007-07-13
forum: Programming Talk
---

### Post by finer recliner on 2007-07-13
can anyone help me install ruby-mode for emacs?

i've tried a couple things, but nothing is working thus far.

i followed the instructions on this site (despite it being intended for the windows version of emacs)
[http://sodonnell.wordpress.com/2007/06/21/emacs-ruby-foo/](http://sodonnell.wordpress.com/2007/06/21/emacs-ruby-foo/)

i've downloaded ruby-mode.el from the Ruby source distribution as directed and placed it in /usr/share/emacs/site-lisp
i even gave it execute priveledges.

i then added these lines to my .emacs file:
```
; loads ruby mode when a .rb file is opened.
(autoload 'ruby-mode "ruby-mode" "Major mode for editing ruby scripts." t)
(setq auto-mode-alist  (cons '(".rb$" . ruby-mode) auto-mode-alist))
(setq auto-mode-alist  (cons '(".rhtml$" . html-mode) auto-mode-alist))
```

i also tried installing ruby1.8-elisp package from the repos. 

when i load up a .rb file, emacs says it loaded ruby mode, but i dont see any syntax highlighting :( 
any help is appreciated. i like the functionality of emacs, but i always have trouble customizing it.

---

### Post by McNils on 2007-07-13
You must turn on font-lock-mode. Try M-X font-lock-mode after you have opened a ruby file. Look at this page on how to customize this behaviour. [sunsite.ualberta.ca/Documentation/Gnu/emacs-21.1/html_chapter/faq_5.html#SEC75]("http://sunsite.ualberta.ca/Documentation/Gnu/emacs-21.1/html_chapter/faq_5.html#SEC75")

---

### Post by finer recliner on 2007-07-13
enabling global-font-lock-mode in my .emacs file:
```
	

(global-font-lock-mode 1)

```

makes all kinds of pretty syntax colors appear. yay! thanks :)

---

