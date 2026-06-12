---
title: "Redirecting Output"
date: 2008-02-14
forum: Programming Talk
---

### Post by RemmyLee on 2008-02-14
I was wondering if anyone could point me to some documentation for redirecting graphical output from one program to another. 

From what I understand, I'd need to make the second program, the program containing the graphical output a child process in order to do it, but I've been unable to find anything or have worded it very poorly on search engines. Any help you could provide would be appreciated.

---

### Post by CptPicard on 2008-02-14
I am not quite sure what you mean. The X protocol is network transparent (you can display the GUI on one machine while the process runs on another), but I don't think this is what you have in mind.

There really is no general way of "redirecting graphical output"... you need to hook into some kind of an API that is provided either by toolkit or the program itself.

---

