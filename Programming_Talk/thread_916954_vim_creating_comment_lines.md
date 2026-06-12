---
title: "vim creating comment lines"
date: 2008-09-11
forum: Programming Talk
---

### Post by fauzie on 2008-09-11
I have a problem with vim, every time I put a comment line like

// This is a comment

And press Enter

Vim automatically put // on the next line
So it looks like this:

// This is a comment
//

This behavior is quite annoying for me as I have to delete those lines before continuing. I would like to know how to disable it.

It occurs on any language by the way ...

Thanks

---

### Post by SteelDragon on 2008-09-11
I don't know how to disable it (because I like it), but rather than backspacing or leaving insert mode to delete it, you can just press ctrl+u to get rid of it and then go on with your typing..

Good luck.

---

### Post by ilrudie on 2008-09-11
Thats odd.  My vim does not do that.  I can see how that would be annoying though.

---

### Post by fauzie on 2008-09-11
ilrudie, could you post your ~/.vimrc ??

Thanks

Ctrl-u works ... I think I can live with it ...

---

### Post by dwhitney67 on 2008-09-11
> **fauzie said:**
> ilrudie, could you post your ~/.vimrc ??

Thanks

Ctrl-u works ... I think I can live with it ...
Better to live with this... (insert into your ~/.vimrc file):
```
au FileType * setlocal comments=
```

---

### Post by ilrudie on 2008-09-12
my .vimrc is short and sweet:

syn on

---

### Post by fauzie on 2008-09-12
Ahhh, the code works!!! Thanks a lot dwhitney67!!!

---

