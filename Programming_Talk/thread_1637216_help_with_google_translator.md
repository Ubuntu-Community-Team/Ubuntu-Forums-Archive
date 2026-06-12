---
title: "help with google translator"
date: 2010-12-04
forum: Programming Talk
---

### Post by c2tarun on 2010-12-04
I want to make a program that passes a parameter to google translator and receive that translation ( in C language).

here what i figured out.
if somehow we pass (to translate "no i m not ok")
```

http://translate.google.com/#**en**|**hi**|**no**%20**i**%20**m**%20**not**%20**ok**

```to address part of mozilla.
a page will be opened that'll return "no i m not ok"'s hindi translation.

--
parameters in bold are en as english and hi as hindi for english to hindi translation.
is it possible to pass this address by a c program and receive the translated parameter???

---

### Post by Wtower on 2010-12-04
I have never done such a thing in C, but I know people have dealt with this issue in php, so there must be a way. Maybe the following links can help you:

[http://googlesystem.blogspot.com/2008/03/google-launched-another-ajax-api-this.html](http://googlesystem.blogspot.com/2008/03/google-launched-another-ajax-api-this.html)

[http://www.phpclasses.org/package/3285-PHP-Translate-texts-between-idioms-using-Google.html](http://www.phpclasses.org/package/3285-PHP-Translate-texts-between-idioms-using-Google.html)

Regards

---

### Post by Some Penguin on 2010-12-04
[http://code.google.com/apis/language/translate/overview.html](http://code.google.com/apis/language/translate/overview.html)

Terms of service:
[http://code.google.com/apis/language/translate/terms.html](http://code.google.com/apis/language/translate/terms.html)

Google is somewhat picky about exploitation of their normal web front-ends and have a tendency to throw CAPTCHAs periodically.

---

### Post by c2tarun on 2010-12-04
thanks friends
this is what i worked so far.

i found this link who provides a java api to work with the translation.
now somehow i need to find a way of communication between java and C program.

my half application is almost completed in JAVA so it is impossible for me to completely change my project from C to JAVA.
if anyone can suggest me a way in which i can embedd JAVA program in C that will be thankful. (just like we embedd JAVA in HTML in JSP).

---

### Post by Wtower on 2010-12-05
Well an easy, low-programming-cost, but not so elegant way, is through the filesystem I suppose.

---

### Post by c2tarun on 2010-12-05
> **Wtower said:**
> Well an easy, low-programming-cost, but not so elegant way, is through the filesystem I suppose.


ya may b. all i need is just passing some english texts and receiving their hindi translations. i think this i can do by file handling.
but i think filehandling can slow processing of my program to a great extent. it may take hours in translating a complete package(as internet is also not very fast so i have to consider it).
any suggestions??

---

### Post by Wtower on 2010-12-06
Possibly. I believe though that the performance deterioration would come mostly from the web rather than the filesystem itself. Other than that, I agree that this is not such an elegant solution as memory collocation would be between the two processes.

---

