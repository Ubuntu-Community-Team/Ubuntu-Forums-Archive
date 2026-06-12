---
title: "Emacs :  abbrev mode"
date: 2008-02-28
forum: Programming Talk
---

### Post by geenux on 2008-02-28
Hello.
I'm a new emacs user and I have problems whith my emacs configuration.
I'm trying to call a skeleton named "for-skel" when I write "_for" in a buffer. 
I did the skeleton:
> (define-skeleton for-skel
  "Insert a for loop"
  nil
  "for(int i=0;i<" _ ";i++)\n{\n\n}\n")

It work when I call it with M-x for-skel.
I've read a lot of things about abbrev-mode but all I tried failled...

thanks a lot.

---

