---
title: "VIM Python Template Content"
date: 2009-07-27
forum: Programming Talk
---

### Post by cmnorton on 2009-07-27
I have $VIMHOME set to ~/.vim.

I have put a simple python template into ~/.vim/templates. It is called e.tpl.

I have put the following line into ~/.vimrc

autocmd BufNewFile * silent! 0r $VIMHOME/templatest/%:e.tpl

Nothing happens when I edit a python file. I'm doing something wrong, but cannot figure out what it is. If someone has an idea, I would appreciate it.

Edit:
---------------------
e.tpl is really supposed to be named py.tpl.
silent! 0r -- the '0' is a zero, not an uppercase O.

---

