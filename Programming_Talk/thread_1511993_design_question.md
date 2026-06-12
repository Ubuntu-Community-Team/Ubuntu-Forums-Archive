---
title: "design question"
date: 2010-06-17
forum: Programming Talk
---

### Post by mess110 on 2010-06-17
hello

I am thinking about designing restful api for a weather station but I am curious about how exceptions are handled. I googled around a little bit but I did not find my answer.

How are exceptions supposed to be returned? As xml error or just a string or?

Thanks in advance

---

### Post by diesch on 2010-06-17
I'd use a 4xx or 5xx HTTP response code with a custom reason phrase.

---

### Post by myrtle1908 on 2010-06-17
You could also allow the consumer to choose the data interchange format via request headers eg. some clients may prefer standard HTTP error codes, some may prefer to always receive "HTTP 200 OK" with a payload in either XML or JSON.

---

### Post by mess110 on 2010-06-18
hm.. ok thank you for the advice :D

implementing..

---

