---
title: "I want to implement to C sources about semaphore,scheduling,monitor and etc. in OS."
date: 2005-04-25
forum: Programming Talk
---

### Post by Se7EnNi9E on 2005-04-25
I have read a "the Operating Systems" book by Nutt.

But I don't understand well.

So, I want to look for implements to C sources.

Do you know where they are?

PS. How is this book,MicroC/OS-II? Is it good?

---

### Post by Nis on 2005-04-25
[QUOTE=Se7EnNi9E]I have read a "the Operating Systems" book by Nutt.

But I don't understand well.

So, I want to look for implements to C sources.

Do you know where they are?

PS. How is this book,MicroC/OS-II? Is it good?[/QUOTE]
 A good source for everything you want to know is the Linux kernel source.  Just going through there gives a good idea about how major parts of an OS work.

I read "Operating System Concepts in Java" by Silberschatz, Galvin, and Gagne and it was a pretty good read if a little short on actual code.

---

### Post by jerome bettis on 2005-04-25
search google for nachOS

it has holes left in it on purpose for you to implement.  we used it in my operating systems class and it was actually worthwhile.  eh i just remembered in order to get it to compile on 386 linux you have to use a cross compiler, which i could never get to work.  i did it on a sparc machine running bsd ... 

also i was told that C doesn't support monitors, due to some limitation in the language, but i never understood them well enough to know why.

---

