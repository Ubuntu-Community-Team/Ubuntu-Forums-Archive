---
title: "How to maximize window using command in TCL/TK ?"
date: 2009-05-27
forum: Programming Talk
---

### Post by tusharv on 2009-05-27
Hi All,

I am working on TCK/TK.
How can I maximize the toplevel window using command in TCL/TK ?

I have tried with ```
wm attributes window_name -fullscreen 1
```
but it gives error like ```
Error in startup script: wrong # args: should be "wm attributes window"
    while executing
"wm attributes $top -fullscreen 1"
```

Any Idea ?

Thanks,
Tusharv

---

### Post by stevescripts on 2009-05-27
Tusharv -

-fullscreen requires tcl/tk 8.5 or higher - you can check your installed version by entering 'info patchlevel' in an interactive tclsh.

That said, are you *sure* that you want a fullscreen toplevel?  Useful for splash screens and such, but ensure that you have a binding to withdraw or  destroy that toplevel, as it will take up the **entire** screen.

Hope this helps a bit.

Steve

---

