---
title: "Executing code in emacs"
date: 2011-08-02
forum: Programming Talk
---

### Post by George Darvehn on 2011-08-02
Does anyone know how to execute code using emacs? i'm coding scheme btw.

---

### Post by nvteighen on 2011-08-03
Execution of code is managed by the language mode that's been loaded. *Usually* though the keystroke for loading is C-c C-l, and the one for compiling is C-c C-c, but e.g. that doesn't work with python-mode.

There's a good Scheme-integration mode for Emacs called Quack. You can install it from the emacs-goodies-el package in the repos, but it needs some further configuration (via M-x customize, IIRC). It's compatible with all major Scheme implementations.

---

