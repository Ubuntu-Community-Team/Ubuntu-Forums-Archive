---
title: "How to unbind any key in TCL/TK ?"
date: 2009-04-22
forum: Programming Talk
---

### Post by tusharv on 2009-04-22
Hi All,

I am working in TCL/TK.

In my program I have bind one button with keyboard key. Now If I destroy this window it will show me the error for bind.

Lets say I have generate one window .w1 and there is one button Next, that will create another window. I have bind Alt+n key with button next. Now when I press next button I am destroying the window .w1 and creating new window .w2. Now Alt+N is already bound with Next of .w1. and I have destroyed .w1. so when I press Alt + N It will show me the error that "bad window path name .w1".

Is there any way to unbind the window when it is destroyed ?

I don't want to use withdraw here. If I use it in place of destroy then problem is not occurring, but My program is such that other contents will be affected.

So please give another better option.

Thanks,
Tushar

---

