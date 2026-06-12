---
title: "distributing an executable and library files"
date: 2006-12-01
forum: Programming Talk
---

### Post by Houman on 2006-12-01
Hi there;

When i was programming on Windows I would just put any required dlls in the directory of the executable and then just give that folder to whoever I wanted to run that program.

But in Linux how would I ahieve the same thing? my executable depends on several .so files and I am not sure if it will work if I just leave them in the executable directory. I think I have to update the library paths and run ldconfig , which is very inconvenient, what if the user has no root access?

Please let me know if you know of an easier way, 

regards

Houman

---

### Post by po0f on 2006-12-01
Houman,

Does [this](http://www.eyrie.org/~eagle/notes/rpath.html) page help you?  I remember stumbling across one that explained it a lot better, but this was all I could find today.

---

### Post by Houman on 2006-12-01
hi po0f;

Thank you for your reply. I read it and I think it will solve the problem, I will try to use it later on to see how it works.

In case anyone else is interested the solution is by using "rpath".

thanks again

Houman

---

### Post by ZuLuuuuuu on 2006-12-02
I was also wondering that thanks for replies.

---

