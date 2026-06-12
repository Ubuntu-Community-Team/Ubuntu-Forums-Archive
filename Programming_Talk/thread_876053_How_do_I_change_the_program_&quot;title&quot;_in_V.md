---
title: "How do I change the program &quot;title&quot; in Visual Studio?"
date: 2008-07-31
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-31
I wrote a C++ console program in Visual Studio for Windows.  Up in the top left hand corner, there is the title of the program.  By default, I think it says something like "C++ Program".  How do I change this title to something else?

---

### Post by henchman on 2008-08-01
if my assumption is right and you are using the win32-api to code your program, you may have fun using the [SetWindowText]("http://msdn.microsoft.com/en-us/library/ms633546(VS.85).aspx") function :)

---

