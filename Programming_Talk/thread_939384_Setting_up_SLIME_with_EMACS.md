---
title: "Setting up SLIME with EMACS"
date: 2008-10-05
forum: Programming Talk
---

### Post by cindyrella on 2008-10-05
Hello all,

I'm having trouble setting up slime. I've installed slime, emacs and sbcl using the package manager. I have created the .emacs folder in my home directory, as well as created a file called "require-slime.el" containing:

```
(add-to-list 'load-path "/usr/share/common-lisp/source/slime/")
(setq inferior-lisp-program "/usr/bin/sbcl")
(require 'slime)
(slime-setup)
```

But when I type in M-x slime in Emacs, I get an error that says:

> Searching for program: no such file or directory, lisp

Please help. Thanks!
cindy

---

### Post by unutbu on 2008-10-05
Put those lines in your ~/.emacs file, rather than in require-slime.el.

See [http://common-lisp.net/project/slime/doc/html/Installation.html#Installation](http://common-lisp.net/project/slime/doc/html/Installation.html#Installation)

---

### Post by cindyrella on 2008-10-05
Ah-ha! So that's the very thing I seem not to understand: when you (and all of those instructions out there) say "put it in the ~/.emacs file" what do you mean? *Where in the file? * In its Properties Notes..? In a blank text file with a certain extension?

(Apologies in advance -- I know how dumb this question looks.)

---

### Post by unutbu on 2008-10-05
No problem: simply type 
```

emacs ~/.emacs

```
Cut and paste the lines into the body of the file, then type 
C-x C-s to save the file. Quit and restart emacs.
The ~/.emacs file will be automatically read.

(C-x is emacs notation for Ctrl-x).

---

### Post by cindyrella on 2008-10-05
Now I'm more confused.

If it isn't too much trouble, would you mind being more explicit?

Where (what window/program) do I type what (code)? Now I'm starting to wonder if .emacs is a file or a folder?

----

UPDATE:

Ah, problem solved.

Turns out that I created a FOLDER called .emacs in my home folder, and tried to put a file called "required-slime.el" in it, expecting emacs to find this file. Instead, I should have created a standalone FILE called .emacs (with the short slime code) in my home folder.

In any case. Thanks for trying to help, unutbu. Hope other newbies will find this mistake helpful in the future!

---

