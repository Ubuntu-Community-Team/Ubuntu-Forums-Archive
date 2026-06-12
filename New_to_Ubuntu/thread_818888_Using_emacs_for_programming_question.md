---
title: "Using emacs for programming question"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-06-04
I'm learning how to use Emacs, specifically for programming purposes.  One thing that bugs me is that when I add the shebang line, the highlighting mode does not change until I close the file and then reopen it.  Is there something I can do within Emacs to have it read in the shebang and adjust without having to restart it?  Do I just have to manually change the major mode?

---

### Post by laptoplinux on 2008-06-05
In general, Emacs uses the file extension to select the major mode and the related syntax highlighting.  So as soon as you save the file with the proper extension, the syntax highlighting should appear.  Since you are talking about a shebang line, I assume you mean shell scripts, for which the common file extension is .sh 

That said, use Meta-x <type-mode-name-here> (press Enter) to change modes on the fly.  

For example, for your shell script:

Meta-x shell-mode 

Then press enter.  

Meta is usually mapped to either pressing the Escape key and then the other button (Escape, let go, then x) or holding down Alt while pressing the other button (Alt+x).

Hope that helps!

---

### Post by laptoplinux on 2008-06-05
Sorry.  You were asking about having Emacs automatically adjust the mode.  Well, I don't know of anyway to do that offhand.  But you could just start out by naming the file with the proper extension. 

For example, at command line:

emacs path/to/yourfile.sh

or within an emacs session:

Ctrl-x Ctrl-f path/to/yourfile.sh

The file won't actually get written to disk until you manually save it.  Until then it just lives in its buffer.

---

