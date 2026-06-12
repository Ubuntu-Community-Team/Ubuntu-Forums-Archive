---
title: "Installing SLIME"
date: 2007-07-05
forum: Programming Talk
---

### Post by Masapena on 2007-07-05
From the SLIME-manual:

With a Lisp implementation that can be started from the command-line, installation just
requires a few lines in your ‘~/.emacs’:
(setq inferior-lisp-program "the path to your Lisp system")
(add-to-list ’load-path "the path of your ‘slime’ directory")
(require ’slime)
(slime-setup)

Question 1: How can I find '~/.emacs`? I was only able to find .emacs.d, which was a directory and behaved oddly, when I used ls in it. And how I can edit it?

Question 2: I can start my SBCL from the command-line, but I don't know it's path. How I can find it?

---

### Post by rjseagraves on 2007-07-05
Answer 1.Your ~/.emacs files doesn't exist, so you'll need to create one. The .emacs file is just a text file containing emacs lisp commands that are executed when emacs starts up.  So just create an empty text file and add the slime commands.
Answer 2. Use the "which" command, ie "which sbcl" (assuming "sbcl" is the command you issue to start SBCL).  This will return the path to the path item executed.  Notice that typically the path item is a symbolic link to the real executable, so maybe want to check this with the "file" command (so type "file /path/to/sbcl" to find out if the file is a symbolic link or real file).

---

