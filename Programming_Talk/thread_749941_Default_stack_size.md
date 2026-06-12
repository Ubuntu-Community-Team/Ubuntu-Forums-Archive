---
title: "Default stack size"
date: 2008-04-09
forum: Programming Talk
---

### Post by yang on 2008-04-09
What are the default stack sizes, at least for Linux? I was able to find 128 KB for IA-64 and 64 KB for other platforms from [http://state-threads.sourceforge.net/docs/reference.html#thread_create](http://state-threads.sourceforge.net/docs/reference.html#thread_create), but I'm wondering:

[list]
[*] is this more "officially" documented anywhere?
[*] what influences this decision (I realize there may be multiple layers of defaults)? kernel config? gcc? glibc?
[*] is there a C symbol or constant that contains this value?
[*] is there anything else on the system that can show this value? (a getconf command? anything in /proc or /sys?)
[/list]

Thanks!

---

### Post by lnostdal on 2008-04-09
man -k ulimit

edit:
actually .. some of those are deprecated .. make sure you read carefully and notice what replaces them

---

