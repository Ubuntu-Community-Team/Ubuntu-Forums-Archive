---
title: "JVM vs .NET/Mono"
date: 2013-05-13
forum: Programming Talk
---

### Post by BluNova on 2013-05-13
What do you prefer and why?

I prefer JVM as it has better cross platform support, is properly opensource (I know mono is but it's playing catch up all the time), and I like JavaDocs

---

### Post by King Dude on 2013-05-13
I'm not especially familiar with JVM, but I don't care for Java as a language, for various reasons. But then again, I'm new to the idea of JVM, so I'm not sure and I'll remain neutral until I'm able to decide for myself.

---

### Post by Leuchten on 2013-05-13
The jvm has many non-java languages available for it, groovy, clojure, and scala among them.

I love the jvm because it has scala, and because it is fast on all platforms, unlike the clr.

---

### Post by King Dude on 2013-05-13
I've never heard of groovy or clojure. Are there any more well known languages in JVM?

---

### Post by spjackson on 2013-05-14
It depends what you mean by "well known". There are certainly many more [languages for the JVM]("http://en.wikipedia.org/wiki/List_of_JVM_languages").

---

### Post by King Dude on 2013-05-14
Well, I think of well known languages as in languages derived from the C language family, or Python, Pascal, Fortran, Assembly, etc.

There is a grey area on what exactly counts as well known, but I can imagine that more people use C, among other languages, than groovy.

---

### Post by Leuchten on 2013-05-15
Considering groovy is very similar to java, I think it qualifies as a c language family derivative.

Scala/groovy/clojure, don't need to be super ubiquitous to be useful thankfully because they all can interoperate with java and its huge ecosystem.

---

### Post by King Dude on 2013-05-15
The more well-known the language is the better when it comes to Open Source software, namely Ubuntu. That's why C, C++, Python, and Lua is commonly used to develop software in the Open Source development community.

I finally was able to check out that above link, and have decided that JVM is better than what I had expected. However, I'm not sure how to compare it to .Net and Mono, performance wise.

---

### Post by trent.josephsen on 2013-05-15
I'm not sure that (the idea that more well known is better) holds water. Learning a language is easy compared to using it; as a developer, I'd rather learn a new language that will let me do a better job in the end than use a language I already know and contract a severe case of pattern-itis. As a project owner, it's better for me to use the language that is best suited for the task, especially when that task is a specific one.

I'd expect language popularity to be bigger in a corporate closed-source environment, when developers are not self-selected for interest in the project and are consequently less motivated (and in some cases less competent) to put in additional effort. But that's just off the top of my head; I don't have numbers.

---

### Post by King Dude on 2013-05-15
It's not a matter of learning a language, it's a matter of experience. If you've been programming in C++ for five years, chances are you will have more of the experience needed to know how to assess problems and tasks with C++ efficiently than a language you had just learned, assuming the language is not a derivative of the C programming family.

You can learn a language and its syntax easily, you're right in that sense, but you need experience to utilize it in programs.

With that in mind, a well known language will logically bare more experienced programmers than a lesser known programming language, even if the lesser known language is better suited for the task.

---

### Post by trent.josephsen on 2013-05-16
That doesn't follow logically... unless you assume there's a positive correlation between *how well known a language is* and *how experienced its users are*. If anything I'd expect the reverse to be true. If fifty million people know C++, how many have more than five years of experience? Fifteen million? Ten? Languages like C++ and Java are flooded with tyros every year because they're popular in first-year CS classes (and the AP program for Java). Many of those who learn it never go beyond superficial knowledge. A language like Clojure is more likely to be used to solve real problems than printing stars and diamonds in your terminal. There's also a talent aspect: people may learn C++ because it was taught in school, but Clojure would be more likely to attract dedicated amateurs. If the difference between good programmers and average programmers really is a factor of 10-100, those amateurs are exactly the people you want to attract to your project.

I also don't think you're accounting for the differences between languages. Five years is enough to teach you pretty much everything there is to know about Lua, or make you a knowledgeable rookie at C++. (The truly hard stuff, good design, takes much longer and is, mostly, language-agnostic.) Even in the corporate world, if I'm looking for people with five years of experience, the language they know is probably less important than what kind of projects they worked on. (Except to HR, who run the equivalent of "grep -lR C++ resumes/").

---

### Post by King Dude on 2013-05-16
The mindset of a programmer before he or she learns a language first inquires "Which programming language should I learn?" While it's likely they will choose the language they assume is more fit for the purpose, if the languages were virtually identical in purpose and performance, chances are they will select the language that they have been exposed to the most. If a language is well known, the aspiring programmer will more likely be exposed to that language than a lesser known language, therefor will likely decide to learn the well known language. Assuming the programmer does not discontinue learning the language, nor discontinue using the language, it will be likely that they will have more experience in that language than any other language later down the road.

Mind you, nobody is the same. This is just what I'd expect, but there very well could be someone who has been exposed to a lesser known language more than other, more well known languages. There's always an exception.

---

### Post by slickymaster on 2013-05-16
> **King Dude said:**
> ... However, I'm not sure how to compare it to .Net and Mono, performance wise.

Actually, you can. Check out [The Computer Language Shootout]("http://benchmarksgame.alioth.debian.org/"), they compare numerous languages, and VMs, including [Mono and JVM]("http://benchmarksgame.alioth.debian.org/u32q/benchmark.php?test=all&lang=csharp&lang2=java&box=1").

---

### Post by slickymaster on 2013-05-16
IMHO, when choosing one over the other, there are several aspects that should be take into account:

[LIST]
[*]Performance Tools available (even 3rd party tools)
[*]Cross platform compatibility
[*]Libraries (especially 3rd party libraries)
[*]Cost
[*]Total Cost of Ownership (TCO)
[*]Development process (Easiest/Fastest)
[/LIST]

---

