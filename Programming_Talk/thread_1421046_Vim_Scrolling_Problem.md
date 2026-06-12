---
title: "Vim Scrolling Problem"
date: 2010-03-03
forum: Programming Talk
---

### Post by gniss on 2010-03-03
Sometimes plain old '**vim** *filename*' works fine.

However other times  CTRL-F and CTRL-B don't work correctly; they scroll one line at a time rather than one screen.

Any idea what is going on and how to fix?

---

### Post by dwhitney67 on 2010-03-03
I've never heard of this problem, nor witnessed it myself.  Perhaps there is something set in your ~/.vimrc file that is causing this?

If you think this may be the cause, temporarily rename your .vimrc to another filename (eg. .vimrc.bak), and see if the problem you have described continues.

---

### Post by gniss on 2010-03-03
Thanks, I tried that but it didn't fix it. I am doing this to a server through SSH, maybe that and the fact that it is intermittent is a clue.

---

### Post by LKjell on 2010-03-04
Should be the server's vimrc not yours then. What about space bar does it scroll?

---

