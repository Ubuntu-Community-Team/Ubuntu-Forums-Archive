---
title: "How do I Unstinall X/emacs and install terminal one"
date: 2006-06-23
forum: Programming Talk
---

### Post by csscll on 2006-06-23
I installed gnu emacs through synaptic and it now has the X version of emacs. When I type emacs in a terminal it starts the X version of emacs. I don't want that. I want a terminal emacs. How do I uninstall the X version and install the terminal version? Or modify the installation so it never starts the X version but loads the terminal one? Thanks.

---

### Post by toojays on 2006-06-23
You have two options: 1) Install emacs21-nox instead of emacs21. 2) Run "emacs -nw" instead of "emacs".

My experience is with GNU Emacs, but I imagine you can adapt these instructions to Xemacs.

---

### Post by wmcbrine on 2006-06-24
Or, you could undefine DISPLAY before starting it. :)

---

### Post by csscll on 2006-06-26
emacs21-nox worked. Thanks.

---

