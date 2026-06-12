---
title: "Running and compiling Visual Basic program in Linux"
date: 2008-03-13
forum: Programming Talk
---

### Post by kaktustopol on 2008-03-13
Hi,
I was wondering if someone knows how I can run existing program, which was written in Visual Basic in Windows (i have .exe file) in Linux. I read a lot about mono online, and i am not sure if that's what I need. 
Also, I might need to modify the source code of the program and compile it again, so I'll need a compiler as well.
I don't have much experience with Visual Basic, so I am not sure how that all works.
Any help will be appreciated.
Thanks,

---

### Post by nanotube on 2008-03-13
if you have the exe, you can just run that using wine (winehq.org, package "wine" in repos)

but, depending on what the program does, you may be better off just finding a prog with equivalent functionality in the repos.

---

### Post by deepclutch on 2008-03-13
a VB like implementation available for Linux is called "gambas" check it out!:D

---

### Post by kaktustopol on 2008-03-13
Thanks a lot for your replies, I am gonna check it out

---

### Post by LaRoza on 2008-03-13
Also, Visual Basic is for Windows and is meant to be run on Windows. So even if you can get it working on Linux, I suggest you try to use a better language in the future.

---

### Post by schmendrick on 2008-03-14
another at least theoretical option:
depending on how the program was built the other option would be to get the IL source code of the program by fetching it with the the .NET Reflector or an equivalent program. then you have the IL/Basic/C# code and you could recompile it with mono or gambas (though i dont know the later) under linux if there are no windows.forms involed.

---

