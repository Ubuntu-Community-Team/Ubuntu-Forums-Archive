---
title: "Emacs ruby-mode AUTO auto-indenting"
date: 2011-09-13
forum: Programming Talk
---

### Post by endeavor_ on 2011-09-13
I'm in the process of tweaking my .emacs for Ruby, but there's one thing that I can't figure out. In emacs after I start a new block statement (function, class, etc) it doesn't automatically auto-indent after hitting Enter. After I press Enter my cursor is at the first character of the next line. I have to hit Tab once to be auto-indented. I wish I didn't have to do this for just about every line of code.  python-mode works the way I want to do without having to customize anything

Is there a way to change this so that it automatically indents without having to press Tab? This is on Ubuntu 10.04.

---

### Post by cgroza on 2011-09-13
Post the output of:
```

C-h k RET

```and 
```

C-h k TAB

```This will give us the 2 functions names those 2 keys are bind to.
I think that you will be able to advise the RET function to execute the TAB function too.

Also, have you tried getting help on #emacs on irc.freenode.net?

---

### Post by jimi_hendrix on 2011-09-13
In Emacs, by default, RET does not autoindent. C-j does autoindenting. You can bind autoindenting to RET via Elisp:

```
(define-key global-map (kbd "RET") 'newline-and-indent)
```

Throw that in your .emacs file and you should be good.

---

### Post by endeavor_ on 2011-09-14
Unfortunately that doesn't seem to change it. However you guys did help me find the correct terms to Google for and I [found the answer]("http://peter.peca.dk/art_Emacs_Ruby_Mode.html"): 
```
(add-hook 'ruby-mode-hook (lambda () (local-set-key "\r" 'newline-and-indent)))
```

Thanks!

---

