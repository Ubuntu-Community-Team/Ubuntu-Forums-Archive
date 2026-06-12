---
title: "Debugging C/C++ code in Vim?"
date: 2007-07-28
forum: Programming Talk
---

### Post by fd9_ on 2007-07-28
It's seems like Vim is a very popular text editor, and I hear about programmers working with it... but how do developers debug programs in something like Vim? How do you set breakpoints, watch memory, etc, like you can do so easily in Visual Studio?

---

### Post by Modred on 2007-07-28
I've never actually used Vim for debugging, but there are [some](http://www.vim.org/scripts/script.php?script_id=663) [scripts](http://www.vim.org/scripts/script.php?script_id=1954) that provide integration with existing debuggers.  I can't speak from personal experience as to how well any of these scripts work. Search for debug in the [scripts page](http://www.vim.org/scripts/script_search_results.php) to find more.  In short, there is built in functionality that I'm aware of and different scripts may provide varying levels of integration and usefulness.

I generally do my debugging directly through the command line using gdb.

---

### Post by aquavitae on 2007-07-28
> **fd9_ said:**
> It's seems like Vim is a very popular text editor, 
Exactly - Its a text editor.  There are plenty of extensions to make it do more, but basically its just an editor, not an IDE, and doesn't come with support for a debugger.  As far I know, the debuggers in all IDE's in linux are just frontends for gdb, which, as Modred says, can be used from the command line.  I have to admit, I've never managed to get into it properly on the command line - too many options!  But I think there are some gui frontends around for it that make it simpler, and that you could use in conjunction with vim (but not necessarily through vim)

---

### Post by nitro_n2o on 2007-07-28
you can run any command within Vim without having to exit  
to run gcc just type ```
!gcc %
``` the % will be replaced with file name and you don't have to leave Vim 
the same holds for any command you want to execute

---

