---
title: "Emacs org-mode indentation"
date: 2011-03-10
forum: Programming Talk
---

### Post by WhiteLion on 2011-03-10
I'm kind of new to emacs, used to use vim for simple tasks, but decided to give emacs a try because of org-mode.
I can't set auto indentation in emacs, I want what is described in this guide, but it doesn't seem to work: [http://orgmode.org/manual/Clean-view.html](http://orgmode.org/manual/Clean-view.html)
Instead of writing tabs I want emacs to automatically order what I write and indent the content, writing: (setq-default org-startup-indented t) in ~/.emacs doesn't seem to work.

---

### Post by runover_dog on 2011-10-31
It works for me...
Are you loading org with (require 'org-install)
Check [this question]("http://orgmode.org/worg/org-faq.html#load-org-after-setting-variables") in org-mode FAQ

PS: I know this post is old, but who knows, maybe someone is searching for an answer to this problem. :)

---

