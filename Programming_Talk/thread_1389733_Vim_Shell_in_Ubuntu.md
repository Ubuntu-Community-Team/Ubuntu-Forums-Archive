---
title: "Vim Shell in Ubuntu?"
date: 2010-01-24
forum: Programming Talk
---

### Post by kogger on 2010-01-24
I tried to install vimshell using the instructions at [http://www.phrison.com/compile-vim-with-vim-shell/]("http://www.phrison.com/compile-vim-with-vim-shell/"), but when I tried to run it there was an error about a buffer overflow detected, a large stack trace printed, and the program aborted.

Anybody have any advice on how to get it installed? I'm running Vim 7.2 on Karmic.

---

### Post by distortedskies on 2010-02-22
had the same problem, you need to define _FORTIFY_SOURCE=1 when configuring. so you would do something like:

```
CFLAGS='-D_FORTIFY_SOURCE=1' ./configure --prefix=/usr ...your other configure flags
```

I believe this was fixed at 7.2.044 so if you use the svn source instead of the 7.2 release sources you shouldn't have a problem.

---

### Post by distortedskies on 2010-02-22
The vimshell patch for 7.2 doesn't apply cleanly to anything in svn. I have modified the patch and tested against the current svn. You can find the patch here [http://github.com/ihnenm/vim-patches]("http://github.com/ihnenm/vim-patches")

---

