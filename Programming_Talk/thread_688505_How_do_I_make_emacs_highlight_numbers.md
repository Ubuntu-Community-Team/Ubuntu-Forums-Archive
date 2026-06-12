---
title: "How do I make emacs highlight numbers?"
date: 2008-02-05
forum: Programming Talk
---

### Post by laptoplinux on 2008-02-05
Sorry for the double post on the forums, but I'm hoping that this forum will be a bit more helpful.

I'm trying to make emacs highlight numbers in a different color.  For example

a = 5

b = 3*exp(2.0)

I would like the 5, 3, and 2.0 to show up differently.

Also, I would like this to work in a language-independent way.  I have fortran 90 in mind, but would like this to work on C++, Python, etc.

Here is my current .emacs file:

```

;; .emacs

;;; uncomment this line to disable loading of "default.el" at startup
;(setq inhibit-default-init t)

;; turn on font-lock mode
(global-font-lock-mode t)

;; set scrollbar on right
(set-scroll-bar-mode 'right)




;; enable visual feedback on selections 
;; --- might have to comment this on Ubuntu to make it work right
;(setq transient-mark-mode t)

;; CUA mode-------------------------------

;; use these two if installing CUA mode manually 
;(require 'cua)
;(CUA-mode t)

;use this one if installing CUA mode on Ubuntu with
; emacs-extras.el package installed
(cua-mode)
;;----------------------------------------------


;; set cursor color to indicate input mode

(setq hcz-set-cursor-color-color "")
    (setq hcz-set-cursor-color-buffer "")
    (defun hcz-set-cursor-color-according-to-mode ()
      "change cursor color according to some minor modes."
      ;; set-cursor-color is somewhat costly, so we only call it when needed:
      (let ((color
             (if buffer-read-only "green"
               (if overwrite-mode "yellow"
                 "black"))))
        (unless (and
                 (string= color hcz-set-cursor-color-color)
                 (string= (buffer-name) hcz-set-cursor-color-buffer))
          (set-cursor-color (setq hcz-set-cursor-color-color color))
          (setq hcz-set-cursor-color-buffer (buffer-name)))))
    (add-hook 'post-command-hook 'hcz-set-cursor-color-according-to-mode)

;; highlight matching parenthesis
(show-paren-mode)


;; font selection
;; use 9x15 if in doubt.  
;; use Monospace-10 or Bitstream Vera Sans Mono-10 if Xft enabled

;(set-default-font "9x15") 
(set-default-font "Bitstream Vera Sans Mono-10") 

;; Programming auto indent
(define-key global-map (kbd "RET") 'newline-and-indent)
(add-hook 'f90-mode-hook (lambda ()
(local-set-key (kbd "RET") 'reindent-then-newline-and-indent)))

;;to manage the geometric size of initial window.
(setq initial-frame-alist '((width . 79) (height . 33)))

(setq line-number-mode t)
(setq column-number-mode t)
(setq display-time-day-and-date t)
(display-time)
(setq-default scroll-step 1)
(pc-selection-mode)
(setq line-number-mode t)
(setq column-number-mode t)
(setq display-time-day-and-date t)
(display-time)
(setq-default scroll-step 1)
(pc-selection-mode)
(mouse-wheel-mode t)
(setq x-select-enable-clipboard t)
(setq menu-bar-enable-clipboard t)


;;-----------------------color scheme stuff below
(custom-set-faces

'(show-paren-mismatch-face ((((class color)) (:foreground "white" :background "red"))))

'(font-lock-string-face ((t (:foreground "dark red"))))

)


```

What could I add to this to make the number-highlighting happen?

Thanks!

---

### Post by a9bejo on 2008-02-05
```

(add-hook 'after-change-major-mode-hook
          '(lambda () (font-lock-add-keywords 
                       nil 
                       '(("\\([0-9]+\\)" 
                          1 font-lock-warning-face prepend)))))

```

Of course, this is quite a intrusive hack. If I understand your question correctly, You want the number coloring to be always active, no matter what language-mode or other major mode you are running.
However, if you are writing a language mode for emacs,  I recommend you read this [language mode creation tutorial](http://two-wugs.net/emacs/mode-tutorial.html) and make all changes local to your new mode.

Good Luck, 
-- Ben

---

