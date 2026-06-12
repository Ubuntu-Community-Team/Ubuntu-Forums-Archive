---
title: "need help to choose api"
date: 2008-05-07
forum: Programming Talk
---

### Post by Ulrik04 on 2008-05-07
Hi, I'm learning C++ at the moment, I have read a book about it and a lot of online tutorials, and have learned all the basics (functions, classes, loops, ...) and I want to begin making real applications both to Linux and Windows (I barely know anyone besides me that runs Linux, and I want them to could use it :P). Before I got Linux I was using the win32 api, but it was difficult, long and annoying (it is Microsoft after all :P). To Linux, I've been using the SDL api, and I think it's ok, but I don't know if you can make buttons and inputs and such in it. So, before I'm choosing a api to fully learn, I would hear if anyone could recommend one. I've heard about GTK+, but I don't know anything about it. I both want to make games and applications that both can compile on Windows and Linux (Mac OS would be nice too ^_^).
Please, can anybody help me choose api? :)

---

### Post by LaRoza on 2008-05-07
> **Ulrik04 said:**
> Hi, I'm learning C++ at the moment, I have read a book about it and a lot of online tutorials, and have learned all the basics (functions, classes, loops, ...) and I want to begin making real applications both to Linux and Windows (I barely know anyone besides me that runs Linux, and I want them to could use it :P). Before I got Linux I was using the win32 api, but it was difficult, long and annoying (it is Microsoft after all :P). To Linux, I've been using the SDL api, and I think it's ok, but I don't know if you can make buttons and inputs and such in it. So, before I'm choosing a api to fully learn, I would hear if anyone could recommend one. I've heard about GTK+, but I don't know anything about it. I both want to make games and applications that both can compile on Windows and Linux (Mac OS would be nice too ^_^).
Please, can anybody help me choose api? :)

For GUI's, you have several options.

They are in the sticky, but I will give a short rundown here:

[list]
[*] wxWidgets: 100% free, and meant to look native across platforms. Easy to use in Windows and Linux
[*] QT: Has everything you want as well, if this is going to be used free software, it is free.
[*] GTK+: Probably not the easiest to use for your goals. It is cross platform and free, but it was originally for C, and has been ported to C++. wxWidgets used GTK+ when it is on Linux, so it probably isn't the first one to chose.
[/list]

I recommend wxWidgets or QT.

---

### Post by Ulrik04 on 2008-05-07
I looked at wxWidgets, and it looks nice. I think I'll try that :)
Thanks for the fast reply ^_^

---

