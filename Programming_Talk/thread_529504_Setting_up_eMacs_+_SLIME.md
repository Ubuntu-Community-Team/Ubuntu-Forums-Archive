---
title: "Setting up eMacs + SLIME"
date: 2007-08-19
forum: Programming Talk
---

### Post by Ryan Marcus on 2007-08-19
Hi, I'm very new to the world of eMacs, LISP, and SLIME. I took a year long course in LISP at my school, who used machines running Ubuntu.

At school, eMacs  and LISP was pre-compiled and installed for us, and I am having a bit of difficultly replicating that set up on my home machine.

If anybody could point me towards some instructions that are a bit more in-depth then adding those four lines to your .emacs file, I would be incredibly grateful.

Thanks in advance for your help.

[edit]
Ah ha! I figured it out. For anybody else in need of help:

Install xEmacs from "Add / Remove Software"
Install the packages "sbcl" and "slime" from Synaptic.
Set your ~/.emacs file to:
```

(setq inferior-lisp-program "/usr/bin/sbcl")
(add-to-list 'load-path "/usr/share/common-lisp/source/slime/")
(require 'slime)
(slime-setup)

```

---

### Post by georgiabiker on 2007-08-24
What does it mean to edit ~/.emacs?

sorry, learning lisp and also trying to set up emacs and slime. I got to that direction in the readme and didn't know what to do! so embarrassing.

thanks!

---

### Post by Ubuntist on 2007-08-24
> **georgiabiker said:**
> What does it mean to edit ~/.emacs?


The  **~**  is an abbreviation for your home directory, which contains a file called  .emacs .  So, just open up that file (or create it if it does not already exist) and edit it with your favorite editor, which is presumably Emacs or XEmacs.

By the way, files whose names begin with a  **.**  will not appear by default when you execute an  **ls**  command from the command line; you need to use the  **-a**  option to see them.  And if you're viewing a directory's contents from a GUI, you will need to turn on listing of  .  files.

---

