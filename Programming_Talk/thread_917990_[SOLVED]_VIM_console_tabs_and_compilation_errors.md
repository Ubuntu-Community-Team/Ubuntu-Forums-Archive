---
title: "[SOLVED] VIM console tabs and compilation errors"
date: 2008-09-12
forum: Programming Talk
---

### Post by Belerophon on 2008-09-12
Hi.

I use vim, with tabs, to program in c, c++.
What I find annoying in vim is that, when I type "make" and if my project has errors, when make finishes the tab which was open is replaced for a tab with a file which has the first compilation error.

well...let me try to explain with a visual guide:

suppose I have a project with 2 files, which are open in vim in different tabs, and I am editing the second:

------------------------------------
| first.c | **_second.c_** | Makefile |
------------------------------------

suppose that an ERROR of some kind exists IN THE "first.c" file, and suppose that I type in ":make". Obviously, gcc gives me the error saying that it is the "first.c" file. What happens when I hit "ENTER" and return to vim is this:


---------------------------------
| first.c | **_first.c_** | Makefile |
---------------------------------

It seems like vim gets the output from gcc, and tries to "assist" me opening the file where the first error is.
This does not assist me....!!

Can anyone help me, explaining how can I change this behaviour?

Thanks

---

### Post by Belerophon on 2008-09-20
*bump*....

---

### Post by Belerophon on 2008-10-27
Well, for whom ever may be interested:

- this was a really silly question in the end. ":make" isn't really an external command. It is more than that. It runs make and a few more things, and that's why vim shows us the file with error in the end. ":make" is an internal command of vim.

So, if we want to avoid that behaviour, we just have to run the real make program --- ":!make", which tells vim to run the EXTERNAL program named "make".


Thanks.

---

