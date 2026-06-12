---
title: "Python Questions"
date: 2007-12-07
forum: Programming Talk
---

### Post by Majorix on 2007-12-07
Q1: What is a good way to escape functional programming in Python? I mean, what do we use for each of filter/reduce/map respectively?

Q2: What features come and go in Python 3.0? When will it be released? Is there an official announcement or some sort I can read? I want to learn about the future of this language, as I have started using it very often.

Thanks.

---

### Post by Wybiral on 2007-12-07
1. What exactly do you mean "escape" functional programming? Those are just functions to help you use the functional idiom in Python.

2. If you get some free time, this is a good video to watch: [http://video.google.com/videoplay?docid=1189446823303316785](http://video.google.com/videoplay?docid=1189446823303316785)

There are also tons of documents online discussing the changes 3000 has planned.

---

### Post by pmasiar on 2007-12-07
1) google for "python list comprehension"

2) google for "python 3000 status"

---

### Post by Majorix on 2007-12-07
@Wybiral:
Isn't functional programming a history?

@pmasiar:
I googled for Python List Comprehension and bookmarked it for future reference. Thanks for the tip.
I also googled for Python 3000 and got to this site in the end:
[http://www.python.org/download/releases/3.0/](http://www.python.org/download/releases/3.0/)
There you can download Python 3.0a2 release, which I hope they will include in Hardy backports. But last time I checked it wasn't there. Why? Where can I ask for it to be included?

Thanks.

---

### Post by LaRoza on 2007-12-07
> **Majorix said:**
> @Wybiral:
Isn't functional programming a history?


I don't understand, functional programming is a programming paradigm, see  [http://en.wikipedia.org/wiki/Programming_paradigm](http://en.wikipedia.org/wiki/Programming_paradigm)

---

### Post by Majorix on 2007-12-07
> **LaRoza said:**
> I don't understand, functional programming is a programming paradigm, see  [http://en.wikipedia.org/wiki/Programming_paradigm](http://en.wikipedia.org/wiki/Programming_paradigm)

The very 3rd result when I google for "Functional Programming" showed a "Why Functional Programming Matters" link. I clicked it in excitement, only to see it was dated 1984. You see, nobody writes on it anymore. If you are interested, here is the link to the article:
[http://www.math.chalmers.se/~rjmh/Papers/whyfp.html](http://www.math.chalmers.se/~rjmh/Papers/whyfp.html)

---

### Post by Wybiral on 2007-12-07
Functional programming is a very powerful paradigm. I don't think it's dead at all. For rapid, reusable development FP and OOP are IMO the best way to go.

---

### Post by Majorix on 2007-12-07
OK I am not here to discuss, let's say that FP is good practice. I will try to sharpen on my skills with lambda (if I can understand it for once for god's sake) and filter/map/reduce.

But then what about Python Alpha?

---

### Post by CptPicard on 2007-12-07
"Nobody writes on it anymore" because it's pretty much a known quantity, and a useful one at that -- not only theoretically, but practically too. Some things are niftily expressed in functional terms, although not all of it.

One of the reasons why fp matters is that it's a very compact way to express Turing-complete computation, and syntactical differences are very much just syntactic sugar. It is, in many ways, easier to analyze and to prove stuff in fp. For example if you exclude value-setting operations (Scheme's set!), you get code that is easy to distribute over numerous computational nodes -- Google does that, for example.

I can't stress it enough that fp isn't just some old archaic thing that you want to "escape" from because something new is better and more "powerful"...

---

### Post by Wybiral on 2007-12-07
> **Majorix said:**
> OK I am not here to discuss, let's say that FP is good practice. I will try to sharpen on my skills with lambda (if I can understand it for once for god's sake) and filter/map/reduce.

But then what about Python Alpha?

Are you referring to the cutting of map/filter/reduce? Is so, that doesn't eliminate FP from Python. It's just that the comprehension form is more "Pythonic". FP will still be possible, in fact, with the addition of "any" and "all" it seems like they're trying to add MORE functional support.

---

### Post by Wybiral on 2007-12-07
> **CptPicard said:**
> For example if you exclude value-setting operations (Scheme's set!), you get code that is easy to distribute over numerous computational nodes -- Google does that, for example.

[MapReduce!]("http://labs.google.com/papers/mapreduce.html")

---

### Post by tyoc on 2007-12-07
> FP is good practiceIs a paradigm (a model, ...), not a practice ;).

You can also try to check Haskell for a shake of what is an actual FP programming lang.
------------------
> **Wybiral said:**
> 
 2. If you get some free time, this is a good video to watch: [http://video.google.com/videoplay?docid=1189446823303316785](http://video.google.com/videoplay?docid=1189446823303316785)
 

 hehe, cant watch it all to the moment, dinner hour end, but it is funny how I dont drop the package of wather, the packages of plastic here are called PET (by chemical components IIRC), but changing 1 leter, you can say "ey, he dnt drop the PEPs" :).

Yea, shame on me for that comment :P.

---

### Post by Majorix on 2007-12-07
I have just downloaded the source code for Python 3.0a2 and I am currently working against my own force not to install it.
*Must... resist...* :lolflag:

Help please.

---

