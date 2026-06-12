---
title: "sbcl is playing bad"
date: 2009-11-19
forum: Programming Talk
---

### Post by Elcid247 on 2009-11-19
hi im using ubuntu 9.10, it was the RC release and i've been updating ever since.

is there a compatibility problem with sbcl and swank? i cant get neither slime nor cusp to work with sbcl.

cusp gives me the "cannot connect to lisp instance" error and eclipse hangs if for like ever and then i find my processor with 50% usage, all by sbcl like its gone into some sort of an infinite loop.

and emacs just shows "Lisp ELDoc Slime (Not connected)"

trying sbcl toplevel in the terminal works just fine.

i purged sbcl, slime and swank, deleted the .deb files from /var/cache/apt/archives and reinstalled them.

still the same thing.

was ubuntu actually packed with conflicting versions? or is it just me? or what?

am i stuck with building another version from source here?

---

### Post by Cl0ud9 on 2009-11-19
I have had no problems getting sbcl to work with emacs and slime and I use the versions found in the Ubuntu 9.10 repositories. I'll post my .emacs, it's nothing special but maybe you will see something that helps.

```

;;; Lisp (SLIME) interaction
(setq inferior-lisp-program "/usr/bin/sbcl")
(add-to-list 'load-path "~/.slime")
(require 'slime)
(slime-setup) 

(show-paren-mode 1)
(add-hook 'lisp-mode-hook '(lambda ()
      (local-set-key (kbd "RET") 'newline-and-indent))) 


;; Use colors to highlight commands, etc.
(global-font-lock-mode t)
;; Disable the welcome message
;;(setq inhibit-startup-message t)
;; Format the title-bar to always include the buffer name
(setq frame-title-format "emacs - %b")
;; Display time
(display-time)
;; Make the mouse wheel scroll Emacs
(mouse-wheel-mode t)
;; Always end a file with a newline
(setq require-final-newline t)
;; Stop emacs from arbitrarily adding lines to the end of a file when the
;; cursor is moved past the end of it:
(setq next-line-add-newlines nil)
;; Flash instead of that annoying bell
(setq visible-bell t)
;; Remove icons toolbar
;;(if (> emacs-major-version 20)
;;(tool-bar-mode -1))
;; Use y or n instead of yes or not
(fset 'yes-or-no-p 'y-or-n-p)

```

---

### Post by Elcid247 on 2009-11-20
well i got it working on emacs following the [guide]("http://common-lisp.net/~lnostdal/writings/sbcl.html") referred to in [this]("http://ubuntuforums.org/showthread.php?t=806719") post

now i just need to figure out how to get it working with cusp.

there is a way in the properties to configure cusp to use a custom sbcl binary and a custom initialization file, i just need to know which file it is :D


dam broken packages! :@

---

