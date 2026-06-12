---
title: "java - Access to Members"
date: 2008-06-20
forum: Programming Talk
---

### Post by Geir102 on 2008-06-20
Hi! I'm learning java. And I've read that declearning evrything public is not a good idea.. Can any one tell my way? Is it a securety risk?

---

### Post by mike_g on 2008-06-20
Its for encapsulation. Its not specifically a security risk; the basic idea behind it is to reduce bugs. It does tend to bring a lot of verbose code with it as well with all those 'get', 'set' function. It took me a little while to get the point of it all.

---

### Post by Geir102 on 2008-06-20
tanks:popcorn:

---

### Post by MacUntu on 2008-06-21
It's more about design than encapsulation I'd say. Objects don't need to know more about other objects than necessary. 

Every object has its function, its responsibility. Other objects only need to know that those functions/responsibilities exist but nothing about their implementation or the objects inner structur.

---

### Post by [h2o] on 2008-06-23
I found this article to be an eye-opener regarding abstraction and setters/getter-functions in Java: [http://www.javaworld.com/javaworld/jw-09-2003/jw-0905-toolbox.html](http://www.javaworld.com/javaworld/jw-09-2003/jw-0905-toolbox.html)

---

