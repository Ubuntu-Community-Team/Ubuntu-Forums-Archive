---
title: "How to automatically indent a  *.pas file ?"
date: 2005-04-23
forum: Programming Talk
---

### Post by Patrol on 2005-04-23
Hi ! I just finished to write a  *.pas file.
But I see that it is not well indented...
I used gvim to write it.
My program is quite long...
Is it possible to automatically indent my program with gvim?
Or is there a program to do so?

Thanks to help me.

*Sorry for my English*

---

### Post by toojays on 2005-04-24
Patrol,

I would have thought there would be a specific tool for this, but if you can't find one, you can use this script. It requires Emacs to be installed.

This script was originally for indenting Ada, but I have modified it for you so it will do Pascal. Hope it helps.```
;;; batch-pas-indent.el -- non-interactive indentation of Pascal code

;;; Based on batch-ada-indent.el
;;; Copyright (C) 1999 Samuel Tardieu.
;;; Copyright (C) 2005 John Steele Scott

;;; Typical use: define a script called "pascal-indent" containing:
;;;
;;; #! /bin/sh
;;; emacs -batch -l batch-pas-indent.el -f batch-pascal-indent "$"
;;;
;;; then call "pascal-indent *.pas" to indent your files.

;;; BUG: If a named file does not exist, this program will create it.

;; Original Author: Samuel Tardieu <sam@debian.org>
(require 'pascal)

;;;###autoload
(defun batch-pascal-indent ()
"Load each file named on the command line, and indent them as Pascal sources.
Use this from the command line, with `-batch';
it won't work in an interactive Emacs.
For example, invoke \"emacs -batch -l batch-pas-indent.el  -f batch-pascal-indent *.pas\""
(if (not noninteractive)
    (error "`batch-pascal-indent' is to be used only with -batch"))
(while command-line-args-left
  (let ((source (car command-line-args-left)))
    (find-file source)
    (pascal-mode)
    (indent-region (point-min) (point-max) nil)
    (write-file source))
  (setq command-line-args-left (cdr command-line-args-left)))
(message "Done")
(kill-emacs 0)) 
```

---

### Post by Patrol on 2005-04-24
Ok thanks a lot, I'll try it !

---

