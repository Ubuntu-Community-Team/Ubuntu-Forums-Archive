---
title: "Emacs doesn't treat underscores as whitespace anymore"
date: 2013-08-15
forum: Programming Talk
---

### Post by jazzgossen on 2013-08-15
I'm using Kubuntu 13.04 and Emacs 23.4.1. Recently I have noticed that in many modes (programming modes, especially) Emacs doesn't treat underscores as whitespace. That means that if I have a variable like this: this_is_a_long_name, doing meta-d to delete only the first "this_" will delete the whole name. This is not how I want it, not how it used to be earlier, and as far as I know, not standard Emacs behaviour.

Does anybody know how to change it back? [This post]("http://www.emacswiki.org/emacs/ModeTutorial") describes how to do the opposite. 

In the scratch buffer, for example, I have the expected behaviour, but in C++-mode CMake-mode, I don't.

---

