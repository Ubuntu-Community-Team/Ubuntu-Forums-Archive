---
title: "Extracts URLs from a string, c++?"
date: 2008-12-21
forum: Programming Talk
---

### Post by BenAshton24 on 2008-12-21
Hey, I'm writing a gui program in c++ that gets images from [www.failblog.org](www.failblog.org) and displays them. I have written some code that gets the source of their xml feed ([click here]("http://feedproxy.google.com/failblog?format=xml")) and loads it into a string. I now want to extract the urls of the fail images, however there are images that aren't "fail" related and i would not like my program to download these. all fail images contain "fail.jpg" at the end of their url. I was thinking maybe some code that finds the fail.jpg and then looks back from that possition until it locates "http" (indicating the start of the url) and then it copies the url into another string. However i am completely stuck :P please help

---

### Post by SledgeHammer_999 on 2008-12-21
[http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

Use the "find" method on the string.
(you are using std::string, right?)

---

