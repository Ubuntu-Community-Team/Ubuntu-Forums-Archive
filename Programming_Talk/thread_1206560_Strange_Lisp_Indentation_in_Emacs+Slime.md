---
title: "Strange Lisp Indentation in Emacs+Slime"
date: 2009-07-07
forum: Programming Talk
---

### Post by ajsquared on 2009-07-07
I've noticed that Emacs indents certain forms that are preceded by a "," differently than it indents it otherwise.  For example, DESTRUCTURING-BIND is normally indented like so:

```

(destructuring-bind (...) (...)
  ...)

```

However, if DESTRUCTURING-BIND is preceded by a comma, I get something like this:

```

,(destructuring-bind (...) (...)
                      ...)

```

If I remove the comma it is indented normally.  I've noticed similar behavior with LET and ECASE.  Does anyone know why this occurs and how to fix it?

I've tried putting ```
(setq lisp-backquote-indentation nil)
``` into my .emacs, but that didn't resolve my problem.  I did also try ```
(setq lisp-backquote-indentation t)
``` but again that did nothing.

If I put a space between the comma and the open parenthesis, it also indents normally:


```

, (destructuring-bind (...) (...)
    ...)

```

I installed slime and emacs-snapshot out of the repositories for Ubuntu 9.04.

---

### Post by unknownPoster on 2009-07-07
It might be useful to post your entire .emacs :)

---

### Post by ajsquared on 2009-07-07
I don't have access to my .emacs at the moment, but I will certainly put it up as soon as I can :D

---

### Post by ajsquared on 2009-07-07
Here's my .emacs
```

(add-to-list 'load-path "/usr/share/common-lisp/source/slime")
(setq inferior-lisp-program "/usr/bin/sbcl")
(require 'slime)
(eval-after-load "slime"
  '(progn
    (add-to-list 'load-path "/usr/share/common-lisp/source/slime/contrib")
    (require 'slime-fancy)
    (require 'slime-asdf)
    (slime-banner-init)
    (slime-asdf-init)
    (setq slime-complete-symbol*-fancy t)
    (setq slime-complete-symbol-function 'slime-fuzzy-complete-symbol)
    (slime-setup)))
(global-font-lock-mode t)
(setq inhibit-startup-message t)
(mouse-wheel-mode t)
(cua-mode t)
(transient-mark-mode 1)
(setq cua-keep-region-after-copy t)
(defun toggle-fullscreen ()
  (interactive)
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
	    		 '(2 "_NET_WM_STATE_MAXIMIZED_VERT" 0))
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
	    		 '(2 "_NET_WM_STATE_MAXIMIZED_HORZ" 0))
)
(toggle-fullscreen)
(add-hook 'LaTeX-mode-hook 'LaTeX-math-mode)
(line-number-mode 1)
(column-number-mode 1)
(add-hook `latex-mode-hook `flyspell-mode)
(add-hook `tex-mode-hook `flyspell-mode)
(add-hook `bibtex-mode-hook `flyspell-mode)

(add-hook 'lisp-mode-hook
          '(lambda ()
            (define-key lisp-mode-map [?\C-m] 'newline-and-indent)
            (define-key lisp-mode-map [?\C-j] 'newline)))
(setq make-backup-files nil)


```

---

