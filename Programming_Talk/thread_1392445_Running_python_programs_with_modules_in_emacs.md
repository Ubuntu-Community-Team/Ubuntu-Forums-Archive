---
title: "Running python programs with modules in emacs"
date: 2010-01-28
forum: Programming Talk
---

### Post by japhyr on 2010-01-28
Hi,

I am learning to program python using emacs, and I am having trouble getting imports to work.  I have two files in the same directory, a.py and b.py.  a.py is simply "import b", and b is just "print 'This is b'.

If I run the program from a terminal, it works.  If I run a.py from emacs using C-c C-c, I get an import error.  I think the error relates to this message "working on region in file /tmp/python-10497FCV.py..."  It seems emacs might be looking in this tmp file for b, but b is somewhere completely different.  The terminal runs the program from the cwd, and doesn't have this problem.

How do I set emacs up to import properly?

---

### Post by cyberslayer on 2010-01-28
Add
(setenv "PYTHONPATH" ".")
to your .emacs

---

### Post by diesch on 2010-01-28
Use C-c C-l (python-load-file) instead of C-c C-c (python-send-buffer) to actually use your file instead of just sending the buffer's content to python.

python-send-buffer writes the buffer to a temp file in /tmp and runs it there - and then b.py isn't in the current dir anymore.

---

### Post by japhyr on 2010-01-28
Issuing the command "python-load-file" returns a message "No Match".  I have python.el installed, and the relevant part of my .emacs file is:
```
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

;; Set PYTHONPATH
;;  python-load-file not defined, may need to address this
(setenv "PYTHONPATH" ".")
```

Adding the setenv does not change the C-c C-c behavior either.  Is there a way to add the command python-load-file?  I am running emacs 22.2.1 on ubuntu 9.04, installed through synaptic.

---

### Post by cyberslayer on 2010-01-28
python.el and python-mode.el are totally different.  python.el is the default mode that comes with Emacs and I know the PYTHONPATH hack works with it (at least in Emacs 23).  C-c C-l also works in Emacs 23.  Your .emacs is setup to use python-mode.el instead of python.el so you could try just using python.el instead by removing the autoload.  If you do that then replace
(setq python-python-command "ipython")
with
(setq python-python-command "ipython -cl")
(setq python-command python-python-command)

You could also try using Emacs 23 since it has been released.

---

### Post by japhyr on 2010-01-31
I have changed my .emacs file a little bit to use python.el with ipython instead of python-mode.el, and things work a little better.  C-c C-l now loads the file.  This always works the first time I load a particular file, but sometimes it seems not to load a file again if I haven't changed anything significantly enough.  Is there a different command to reload the file?

I am trying to stick with emacs 22.  The relevant part of .emacs now looks like this:
```
;; Set up Python environment.

;; load ipython.el if ipython is available
(when (executable-find "ipython")
    (require 'ipython nil 'noerror))
(when (featurep 'ipython)
  (setq python-python-command "ipython -cl")
  (setq python-command python-python-command)
  (autoload 'py-shell "ipython"
    "Use IPython as the Python interpreter." t))


;; Set up initial window layout.
;;  Large left vertical window for program file, upper right window for python interpreter, lower right window for scratch.
(split-window-horizontally)
; Open dired buffer in main window
(dired "~/Development - Pangolin/OpenLessonPlanner")
(other-window 1)
(split-window-vertically)

;; Start python interpreter in upper right window
(other-window 1)
(other-window 1)
(run-python)
```

---

### Post by cyberslayer on 2010-02-01
If you don't make changes to the file python will just use the .pyc file which was previously generated.

Pretty sure you don't need this part:
(autoload 'py-shell "ipython"
    "Use IPython as the Python interpreter." t))
as I believe it is for python-mode.el.

If you don't want emacs23 because you want a package, the emacs-snapshot package contains emacs23 which is installed as the emacs-snapshot command.

---

### Post by japhyr on 2010-02-09
I've been using C-c C-l for the last week, and it has been working.  But I've been noticing lately that if I change an imported module without changing the parent module, running C-c C-l does not always use the modified imported module.  I have reverted to developing in emacs, but switching to a terminal to run the file each time I make changes.

Is there a way to get emacs to reload modified modules each time I load the parent module?  Do I have to use the python reload function during development to force this, or is there a way I can set emacs to reload all modules during development?

---

