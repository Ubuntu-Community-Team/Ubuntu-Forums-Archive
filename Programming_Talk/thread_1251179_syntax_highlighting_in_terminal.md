---
title: "syntax highlighting in terminal"
date: 2009-08-27
forum: Programming Talk
---

### Post by ssam on 2009-08-27
quite often i need to look at bits of code on the terminal, and want to see them syntax highlighted. it would be great to have something that would take code on stdin and output highlighted code. eg:
```

$ cat foo.c | highlight
$ tail foo.py | highlight
$ bzr diff | highlight
$ make | highlight

```
i know there are wrappers like colordiff and colormake, but surely there could be a general one.

does anything like this exist?

---

### Post by stroyan on 2009-08-27
You could try vimpager.
It is a vim wrapper that uses vim to act like less, with the addition of vim's color syntax highlighting.
[http://www.vim.org/scripts/script.php?script_id=1723](http://www.vim.org/scripts/script.php?script_id=1723)

---

### Post by ssam on 2009-08-28
thanks that seems good.

---

