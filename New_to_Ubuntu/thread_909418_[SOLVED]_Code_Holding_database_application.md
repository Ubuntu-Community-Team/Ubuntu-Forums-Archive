---
title: "[SOLVED] Code Holding database application?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by ChocolateChip_Wookie on 2008-09-03
Hello all,

I have been eyeing up the Eeepc and I was thinking to install Ubuntu on it to make it really useful. The idea of having the Eeepc is as a kind of electronic book which I can take anywhere which will hold web bookmarks, code samples and such like. My question is this...

a) Is there a (preferably) free code holding database that has index and search capabilities and works under Linux? (XP is just not an option for me)

2) The database needs to be absolutely rock solid since I am planning to put everything I do and ever intend to do in it.

3) It must handle code samples of varying lengths from little snippets to whole structures. It must handle ASP, JS, HTML, CSS, PHP, AJAX, JSON, XML, etc. In fact, everything you can think of.

Any help would be gratefully appreciated.

---

### Post by hyper_ch on 2008-09-03
bookmarks and such: just sync the browser profile.... code samples... hmmm....don't really know

---

### Post by ChocolateChip_Wookie on 2008-09-03
> **hyper_ch said:**
> bookmarks and such: just sync the browser profile.... code samples... hmmm....don't really know

Sync the bookmarks? Can you elaborate please?

---

### Post by hyper_ch on 2008-09-03
firefox for examples has a profile folder where it keeps all its file... all you'd need to do is sync the data from device 1 onto device 2

e.g.
```

rsync -avpz --delete /path/to/origin /path/to/destination

```

---

### Post by mister_pink on 2008-09-03
I suppose the obvious thing to keep code in is subversion or some other repository software

---

