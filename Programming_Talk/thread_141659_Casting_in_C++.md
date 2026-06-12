---
title: "Casting in C++"
date: 2006-03-08
forum: Programming Talk
---

### Post by mdh on 2006-03-08
Hello everyone,

In the C++ books that I refer to, explanations for type casting is often vauge and confusing. So, I thought I might ask the gurus for a clear and succinct explanation. Here are my questions

* What is the difference between dynamic_cast and static_cast 
* When do you prefer one of these to the other 
* Why should these cast operators be prefered over C-style casts

---

### Post by AngryPanda on 2006-03-08
Here's a good lil' article that covers C++ various casting mechanisms. I found it insightful, anyway.

[http://www.informit.com/articles/article.asp?p=397657&rl=1]("http://www.informit.com/articles/article.asp?p=397657&rl=1")

---

### Post by hod139 on 2006-03-08
[This is a pre]("http://www.informit.com/guides/content.asp?g=cplusplus&seqNum=134&rl=1")[FONT=Verdana][tty good guide]("http://www.informit.com/guides/content.asp?g=cplusplus&seqNum=134&rl=1") explaining the differences between the 4 C++ casts "[/FONT]static_cast, const_cast, reinterpret_cast, [FONT=Verdana]dynamic_cast" and also why the C-style casting is bad.

In addition to the articles reasons for why C-style casting is bad, I would also add that you can't search for a C-style cast in exisiting source code. Using the new C++ style casts, you can easily search for them.

If you still have specific questions about the differences after reading the article just post back and someone can hopefully answer.

**Edit:**  Wow, same article.  Looks like I'm just too slow.
[/FONT]

---

