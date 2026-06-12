---
title: "Age of dynamic languages: Cobra is coming"
date: 2008-02-06
forum: Programming Talk
---

### Post by pmasiar on 2008-02-06
I just read about new language [Cobra](http://cobra-language.com/docs/why/)

Looks very interesting. Syntax is [comparable to Python](http://cobra-language.com/docs/python/), but has cool features:
- all the Python goodness: significant whitespace, lists, dictionaries, in, for operators, exception handling and garbage collection
- static typing is optional, but possible for speed
- local variables are statically typed by type inferencing
- assertions and unit tests are embedded in language (optional)
- compile-time nil (NULL) tracking

The only thing I dislike that it is for .NET. :-)

Nothing in particular is new idea, all was proven in other languages - but Cobra is first language pulling all these interesting parts together. It is **good** that there are no new features.

Looks like MSFT guys had another smart idea (after IronPython, Silverlight, and DLR in CLI). I am jealous! 

Seems like time of dynamic languages is coming: Java is little late (they ignored Jython for 10 years) but with [the Da Vinci Machine](http://openjdk.java.net/projects/mlvm/) - extending the JVM with first-class architectural support for languages other than Java, especially dynamic languages.

---

### Post by cprofitt on 2008-02-06
Looks cool to me... I gotta add hours on my clock so I can find the time to learn all this stuff... I already limit myself to no more than six hours of sleep. :)

---

### Post by lnostdal on 2008-02-06
i read your post fast and haven't had time to look at cobra or the cobra site yet .. just wanted to point out something:

* [http://www.scala-lang.org/](http://www.scala-lang.org/)
* [http://www.robert-tolksdorf.de/vmlanguages.html](http://www.robert-tolksdorf.de/vmlanguages.html)
* [http://clojure.sourceforge.net/](http://clojure.sourceforge.net/) (i find this one particularly interesting .. but i have not had time to play with it yet)

..just in case you did not know that there are many interesting languages for the jvm also :) .. there, now i can press the post quick reply button and reread your post and click on the links :)

---

### Post by fyplinux on 2008-02-07
> **pmasiar said:**
> I just read about new language [Cobra](http://cobra-language.com/docs/why/)

Looks very interesting. Syntax is [comparable to Python](http://cobra-language.com/docs/python/), but has cool features:
- all the Python goodness: significant whitespace, lists, dictionaries, in, for operators, exception handling and garbage collection
- static typing is optional, but possible for speed
- local variables are statically typed by type inferencing
- assertions and unit tests are embedded in language (optional)
- compile-time nil (NULL) tracking

The only thing I dislike that it is for .NET. :-)

Nothing in particular is new idea, all was proven in other languages - but Cobra is first language pulling all these interesting parts together. It is **good** that there are no new features.

Looks like MSFT guys had another smart idea (after IronPython, Silverlight, and DLR in CLI). I am jealous! 

Seems like time of dynamic languages is coming: Java is little late (they ignored Jython for 10 years) but with [the Da Vinci Machine](http://openjdk.java.net/projects/mlvm/) - extending the JVM with first-class architectural support for languages other than Java, especially dynamic languages.

One point: nil could never be tracked when compiling in theory, As no program can detect the run-time behavior of a program. It is like the halting problem: [http://en.wikipedia.org/wiki/Halting_problem](http://en.wikipedia.org/wiki/Halting_problem)

I am wondering how did they track nil. could they find all the nil values in the program?

---

### Post by pmasiar on 2008-02-07
> I am wondering how did they track nil.

Did you read FAQs? They differentiate between nilable and un-nilable type. String is not nilable, String? is, but you cannot assign one to another directly without checking. There is apparently whole CompSci theory underlying it.

---

### Post by Wybiral on 2008-02-08
> **pmasiar said:**
> Did you read FAQs? They differentiate between nilable and un-nilable type. String is not nilable, String? is, but you cannot assign one to another directly without checking. There is apparently whole CompSci theory underlying it.

It would probably take some getting used to. Honestly, it looks like someone took Python and tried to add static typing to it ...I'm not sure how I feel about this... I looks like it's worth giving a try though.

---

