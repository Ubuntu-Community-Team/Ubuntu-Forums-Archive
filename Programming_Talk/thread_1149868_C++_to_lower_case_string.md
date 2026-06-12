---
title: "C++ to lower case string"
date: 2009-05-05
forum: Programming Talk
---

### Post by cl333r on 2009-05-05
Folks, I'm using Gtkmm, how do I convert a string to lower case?
There's Glib::ustring::lowercase but I can't figure out how to use it, any example please?

yep, thanks NintenDave, my problem was that I was mixing std::string with Glib::ustring

---

### Post by NintenDave on 2009-05-05
```
Glib::ustring upper = "HeLlO";
Glib::ustring lower = upper.lowercase();
```

---

### Post by lensman3 on 2009-05-05
What is the STL lib or the boost equivalent?  

I'm too lazy to look them up!

---

### Post by soltanis on 2009-05-06
[http://lmgtfy.com/?q=STL+strings+to+lower+case](http://lmgtfy.com/?q=STL+strings+to+lower+case)

---

### Post by salvachn on 2009-05-06
If you deal only with ASCII strings, tolower() would do. Else you can write a function by yourself ;)

---

