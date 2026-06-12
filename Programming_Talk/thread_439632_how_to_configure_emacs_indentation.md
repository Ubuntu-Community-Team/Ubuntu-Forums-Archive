---
title: "how to configure emacs indentation?"
date: 2007-05-10
forum: Programming Talk
---

### Post by finer recliner on 2007-05-10
umm, so i've tried a few things already, but to no avail. how do i change the default indentation size for emacs from 8 spaces to 4?


thanks

---

### Post by ilautar on 2007-05-11
I find this usefull (also, spaces instead of tabs) - put into your .emacs:

(setq-default indent-tabs-mode nil)   ; always replace tabs with spaces
(setq-default tab-width 4)            ; set tab width to 4 for all buffers

You should check-out [http://www.emacswiki.org/](http://www.emacswiki.org/), there are some great tips over there. Take few hours of time to browse through it if emacs is primary editor of your choice.

---

### Post by finer recliner on 2007-05-11
awesome, it worked. thanks 8-)

---

