---
title: "C: is it being replaced by C++?"
date: 2008-04-06
forum: Programming Talk
---

### Post by samjh on 2008-04-06
While browsing through the IT magazine section of a news agency store, I stumbled across an article about the future of C++.  Nothing unusual in itself, but a statement caught my eye.  It said something to the effect that C++ is finding increasing usage in embedded systems, and gave examples of military avionics and sensors.

My thinking thus far is that it is C, not C++, that is the preferred language for embedded systems.  However I admit that in recent years, the demand in my country's defence and security industries seem to point to a rise in C++ skills, while demand for C skills are decreasing.

What is the opinion of the forum members on this?  Is C++ superseding C in the embedded software market?  Will C be what Assembly has become, and C++ take its place?

If you actively use C and/or C++ professionally, what industry trends have you observed with regard to these two languages?  Where do you expect to see them in the future?

(Take note that I'm talking only about embedded systems rather than higher-level application software.)

---

### Post by lnostdal on 2008-04-06
i hope not .. C++ is a mess regardless of where it is applied IMHO .. (i use Common Lisp and C)

[http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918) (well, i happen to agree)

C is evolving .. it's not "dead" .. check out C99: [http://en.wikipedia.org/wiki/C_(programming_language)#C99](http://en.wikipedia.org/wiki/C_(programming_language)#C99)

---

### Post by slavik on 2008-04-06
the reason why C++ is not so good for embedded systems is because OO and templates add unnecessary weight to the code. thus C is better, but as far as avionics go, all flight controller and airplane controlling software is written in Ada (AFAIK in USA).

---

### Post by samjh on 2008-04-06
> **slavik said:**
> the reason why C++ is not so good for embedded systems is because OO and templates add unnecessary weight to the code. thus C is better, but as far as avionics go, all flight controller and airplane controlling software is written in Ada (AFAIK in USA).Not quite.  Ada is used in a large portion of safety-critical software around the world, but it has been offset by subsets of C and C++ since the end of the Ada Mandate in 1997.  Even with the Ada Mandate in place, the US DOD did grant a lot of exceptions to the rule.  Having said that, I like Ada for its purpose, and also find that it produces more efficient and faster programs than C++.

I agree with you about C++, that's why I think C is still better for embedded systems (with the exception of safety-critical software, for which I will pick Ada as the first preference).

---

### Post by LaRoza on 2008-04-06
There are a lot of embedded languages, Java (in many things, and part of Blu-Ray), C, Forth, Tcl, and others.

I don't think C is being replaced by C++.

---

### Post by Balazs_noob on 2008-04-06
[java]("http://www.sunspotworld.com/")
:lolflag:
they made a new JVM for this environment and
i was impressed when i saw it in action.
but maybe the propaganda is getting to me :KS

---

### Post by Aztek on 2008-04-06
As an avionics programmer for the last 2 years (in the US), I have worked on C, C++, and Ada based projects. C is more light-weight than C++ and since embedded systems rely more on real-time, structural paradigms C++ can add un-needed weight and potential problems as apposed to C (for example; we never used certain things like exception handling, since every situation must be explicitly accounted for and handled in a specific way). I think Ada is a good language and definitely very safe but in my experience there aren't many people who like it or want to learn/use it.

To answer your question; no, I do not think C++ is replacing C in embedded systems. For now, the programming styles used in embedded systems suites C very well and until that changes it will reign supreme.

---

### Post by kknd on 2008-04-06
If Java is used to mobile devices, then the small memory overhead of C++ comparing to C its nothing.

C++ have, in pratice, the same performance and memory use (checkout the famous language shootout benchmarks).

Theres some weird people that blame virtual functions and its 0,001% overhead but....

---

### Post by xlinuks on 2008-04-06
There's nothing that one could do in C and couldn't do in C++, and viceversa!
The "overhead" is rather a compiler/programmer/library issue, not to mention that OOP is easier to maintain.
The reason why C will be there for a long time, is cause there's a huge C codebase, lots of professional C programmers and so on and the benefits of migrating to C++ are not that important (but would be welcome by some people).

---

### Post by dwhitney67 on 2008-04-06
I've worked on an embedded s/w for a US DOD satellite program, and we relied on Embedded-C++ (see [http://www.caravan.net/ec2plus](http://www.caravan.net/ec2plus) for more details).  C++ offered the benefits of class inheritance.  We avoided use of STL (and homemade template classes) and virtual method/class definitions, amongst the other restrictions dictated by embedded-C++.

The project was successful... thus a case where C++ supplanted the need/requirement to use C.

---

### Post by Aztek on 2008-04-06
> **dwhitney67 said:**
> I've worked on an embedded s/w for a US DOD satellite program, and we relied on Embedded-C++ (see [http://www.caravan.net/ec2plus](http://www.caravan.net/ec2plus) for more details).  C++ offered the benefits of class inheritance.  We avoided use of STL (and homemade template classes) and virtual method/class definitions, amongst the other restrictions dictated by embedded-C++.

The project was successful... thus a case where C++ supplanted the need/requirement to use C.

Exactly, C++ can be used in embedded systems, but it requires that you set a bunch of rules for things like STL, exception handling, and OO practices. Most of this isn't needed in C and most of the things that are needed are available. That said, there are certain things in C++ that are a pain to do without in C with regards to all types of programming, including embedded systems. Things such as namespaces, built-in boolean type, const, etc. I know that some of these features have been implemented in C (like const), but many of the compilers used in embedded systems support only older C standards which still lack these features.

---

### Post by Shining Arcanine on 2008-04-06
According to Bjarne Stroustrup, C++ is not replacing C with respect to systems programming, although he seems to believe that it should:

[http://developers.slashdot.org/article.pl?sid=00/02/25/1034222&tid=156](http://developers.slashdot.org/article.pl?sid=00/02/25/1034222&tid=156)

> **Aztek said:**
> Exactly, C++ can be used in embedded systems, but it requires that you set a bunch of rules for things like STL, exception handling, and OO practices. Most of this isn't needed in C and most of the things that are needed are available. That said, there are certain things in C++ that are a pain to do without in C with regards to all types of programming, including embedded systems. Things such as namespaces, built-in boolean type, const, etc. I know that some of these features have been implemented in C (like const), but many of the compilers used in embedded systems support only older C standards which still lack these features.

If a backend for those embedded systems exists for the GNU C Compiler, newer features of C will become available upon mating it with the latest frontend. It might not be that simple due to changes across versions of GCC, but it should not be as difficult as writing a new compiler from scratch.

---

### Post by slavik on 2008-04-06
> **dwhitney67 said:**
> I've worked on an embedded s/w for a US DOD satellite program, and we relied on Embedded-C++ (see [http://www.caravan.net/ec2plus](http://www.caravan.net/ec2plus) for more details).  C++ offered the benefits of class inheritance.  We avoided use of STL (and homemade template classes) and virtual method/class definitions, amongst the other restrictions dictated by embedded-C++.

The project was successful... thus a case where C++ supplanted the need/requirement to use C.
so, you basically used C++ without the things that make it C++ and not C.

---

### Post by dwhitney67 on 2008-04-06
> **slavik said:**
> so, you basically used C++ without the things that make it C++ and not C.
Umm, yes if I understand you.  The main benefit of using C++ (over C) is class inheritance, whether using full-blown C++ or embedded-C++.

---

### Post by Aztek on 2008-04-06
> **Shining Arcanine said:**
> According to Bjarne Stroustrup, C++ is not replacing C with respect to systems programming, although he seems to believe that it should:

[http://developers.slashdot.org/article.pl?sid=00/02/25/1034222&tid=156](http://developers.slashdot.org/article.pl?sid=00/02/25/1034222&tid=156)



If a backend for those embedded systems exists for the GNU C Compiler, newer features of C will become available upon mating it with the latest frontend. It might not be that simple due to changes across versions of GCC, but it should not be as difficult as writing a new compiler from scratch.

Well I was actually referring to avionics systems, not anything that uses GCC or the like. In my experience going between different projects usually meant going to a different target compiler.

EDIT: The article below is a very interesting read and has some info on the subject at hand. Just search for "Why C matters". Note that the authors (listed at the bottom) are probably a little biased towards using Ada.
[http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html]("http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html")

---

