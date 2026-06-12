---
title: "Start emacs with window as python shell"
date: 2009-11-28
forum: Programming Talk
---

### Post by japhyr on 2009-11-28
Hi,

I am starting to use emacs for python development.  I have a .emacs file that opens emacs with two windows.  I want to have one of the windows open as a python shell.  For example, when I open a python file and execute it, a butter called Python opens, which gives error messages.  But to see that, I always have to cycle through the buffers to get to it.

What can I put in my .emacs file that will open one of my windows to the python shell on startup?

---

### Post by jpkotta on 2009-11-29
I use python-mode.el, not the built-in python.el, because I think it's better.

```

(autoload 'python-mode "python-mode.el"
  "Major mode for editing Python source." t)

```

Then I prefer ipython to the cpython interface.  ipython.el is available from the ipython website.

```

;; load ipython.el if ipython is available
(when (executable-find "ipython")
    (require 'ipython nil 'noerror))
(when (featurep 'ipython)
  (setq python-python-command "ipython")
  (autoload 'py-shell "ipython"
    "Use IPython as the Python interpreter." t))

```

```

;; make up and down arrows work in the interpreter buffer
(add-hook 'py-shell-hook
          (lambda ()
            (local-set-key (kbd "<up>") 'comint-previous-matching-input-from-input)
            (local-set-key (kbd "<down>") 'comint-next-matching-input-from-input)))

```

Then you can start the interpreter with C-c !, and execute the buffer/region/file/etc. with similar keystrokes.  C-c ! will automatically switch to the interpreter buffer in other-window if there is some other buffer there.

---

### Post by nvteighen on 2009-11-29
Thanks for the python-mode.el tip. It's really much better than the built-in mode.

---

### Post by japhyr on 2009-11-29
This is quite helpful, but I am still having one problem.  I am trying to set up emacs to start with three windows: one vertical window on the left for the program file, a python interpreter in the upper right, and a scratch window in the lower right.  I've got my .emacs file set up so emacs opens with a dired buffer on the left (which is what I want), and two scratch windows on the right.  The scratch windows are set to python mode.

The problem is, when I put the line "(py-shell)" in my .emacs file, it always starts the python interpreter in the next window.  I found a workaround by cycling back to the dired window before issuing the py-shell command in the .emacs file, but this seems pretty inelegant.  Is there a more straightforward way to do this?  I thought it had something to do with the value of "py-shell-switch-buffers-on-execute", but I can't figure out what to set that to in order to make this work.

.emacs file:
```
;; A humble, growing .emacs file.
;;  Begun 11/2009


(add-to-list 'load-path "~/elisp/")

(require 'linum)


;; Don't show splash screen at startup.
(setq inhibit-splash-screen t)

;; Turn on line numbering.
(global-linum-mode 1)


;; Set up Python environment.
(autoload 'python-mode "python-mode.el"
  "Major mode for editing Python source." t)

;; load ipython.el if ipython is available
(when (executable-find "ipython")
    (require 'ipython nil 'noerror))
(when (featurep 'ipython)
  (setq python-python-command "ipython")
  (autoload 'py-shell "ipython"
    "Use IPython as the Python interpreter." t))


;; Set up initial window layout.
;;  Large left vertical window for program file, upper right window for python interpreter, lower right window for scratch.
(split-window-horizontally)
; Open dired buffer in main window
(dired "~/Development - Pangolin/OpenLessonPlanner")
(other-window 1)
(split-window-vertically)

;; Attempt to get python shell in upper right window
(python-mode)
;(setq py-shell-switch-buffers-on-execute nil)	; Does not generate errors, but does not seem to change functionality of py-shell.
;(py-shell)

(other-window 1)
(other-window 1)
(py-shell)	; Workaround to get python shell open in upper right window.


;; Fringes (space between line numbers and text:
; (set-fringe-mode 5)


;; Get rid of gui stuff.
; (menu-bar-mode -1) 	; no menubar
; (scroll-bar-mode -1) 	; no scroll bar
(tool-bar-mode -1)	; no tool bar
```

screenshot:

---

### Post by jpkotta on 2009-11-29
You should look at [http://www.emacswiki.org/emacs/CategoryWindows](http://www.emacswiki.org/emacs/CategoryWindows), there are some packages listed there that may help you do what you want.  Also, you should play with set-window-dedicated-p.

You can learn about py-shell-switch-buffers-on-execute or any other variable with C-h v py-shell-switch-buffers-on-execute RET.  It probably doesn't control what you want.

---

### Post by japhyr on 2009-11-30
Thank you for the links and the overall help.

---

