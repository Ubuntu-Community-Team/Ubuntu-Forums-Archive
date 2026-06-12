---
title: "twitter application in c++?"
date: 2010-01-16
forum: Programming Talk
---

### Post by abhilashm86 on 2010-01-16
i looked at twitter api, its simple with hitting xml or rss or atom update, my major doubt is can i do it easily with c++? 

if i want to make a front end, what should i use? 

i saw many examples in php and higher end languages, can i do it easily in c++? any one tried twitter application?

---

### Post by kwyto on 2010-01-16
I wouldn't try it in C++. It would take too much work to do graphics. A better option is MFC with Visual C++. A lot of nice functions are already created for you. Microsoft did a great job with MFC.

---

### Post by Zugzwang on 2010-01-16
> **kwyto said:**
> I wouldn't try it in C++. It would take too much work to do graphics. A better option is MFC with Visual C++. A lot of nice functions are already created for you. Microsoft did a great job with MFC.

This is a strange answer. First of all, Visual C++ is of course "C++" (as the name says). Also, what has the question to do with graphics? Probably, the author meant "GUI stuff". Then, MFC is a little bit old and, however depending on your personal preferences, not worse than for example the QT framework, that you can use with the GCC.

As far as the actual question is concerned, have a look at the Wiki: [http://apiwiki.twitter.com/Things-Every-Developer-Should-Know](http://apiwiki.twitter.com/Things-Every-Developer-Should-Know) - In section 8, there are examples of API use from the command line. If that is possible, you will have no problems doing that in C++. However, in more high-level languages, it will even be simpler (provided that you actually have knowledge of them)! But in C++, this wouldn't be troublesome either.

---

