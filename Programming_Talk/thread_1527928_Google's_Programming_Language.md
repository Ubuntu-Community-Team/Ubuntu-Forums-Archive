---
title: "Google's Programming Language?"
date: 2010-07-09
forum: Programming Talk
---

### Post by osomphane on 2010-07-09
I know Google uses Python primarily, but I have read that they have had Ruby presentations and their Sketch Up tool has a Ruby API. Do you think that Ruby would replace Python in the future at Google or not?

---

### Post by Queue29 on 2010-07-09
> **osomphane said:**
> I know Google uses Python primarily, but I have read that they have had Ruby presentations and their Sketch Up tool has a Ruby API. Do you think that Ruby would replace Python in the future at Google or not?

Google uses C++ (following very strict guidlines) and/or Java for nearly anything. They have a crack team working on Go, a projected replacement for C++ which is being designed with concurrency and garbage collection in mind from the ground up. 

Python makes a good scripting language, useful maybe for gluing bits and pieces of things together, but any and all heavyweight lifting is going to be done with C++ or Java. 

Check out:
[http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml)

---

### Post by wkhasintha on 2010-07-10
thanx

---

### Post by osomphane on 2010-07-12
Thanks for the info, I hadn't even heard of Google Go. I looked it up really fast, but it doesn't seem to be anything big since it was announced in late of last year. Wikipedia says that Google is using it in production - wonder how accurate that is?

---

### Post by KdotJ on 2010-07-12
Im sure they are using it, since they are working on it, using it in production is great testing.

---

### Post by nmaster on 2010-07-12
> **osomphane said:**
> Thanks for the info, I hadn't even heard of Google Go. I looked it up really fast, but it doesn't seem to be anything big since it was announced in late of last year. Wikipedia says that Google is using it in production - wonder how accurate that is?

some phd's from google came to talk about it at school once.  they advertised it as python that compiles like C.  they don't use it much to my knowledge.  they definitely stick with java and c++ right now.

---

### Post by DanielWaterworth on 2010-07-12
Go is a fairly nice language to work in. They don't have a production quality optimizing compiler yet to my knowledge. Asides from that, I miss exceptions and I don't think that goroutines should be able to share information without using channels, which would allow a program to be compiled for a cluster with no extra work. Just my two cents.

Google won't use it for anything serious until it's stable and ready. The myth that it's good to make end users do software testing is plain wrong.

---

### Post by ov3rcl0ck on 2010-07-12
> **osomphane said:**
> I know Google uses Python primarily, but I have read that they have had Ruby presentations and their Sketch Up tool has a Ruby API. Do you think that Ruby would replace Python in the future at Google or not?

Nope. Google still creates APIs with python support and they have released nothing about adding Ruby to anything else. Ruby has less support all around than python so not many libraries and been exposed to Ruby.

Google made its own language that is for multitasking using microthreads. Its called golang, but its no replacement for python, seeing as the stackless python project had been implementing the same idea for much longer, and it has better benchmarks than golang. I think golang was just something google wanted to try.

Theres no major software or even semi-well known software out there thats made in golang.

Googles gonna stick to python. If the branch off I think they'll start a new language or attempt to make golang actually useful and not just a reinvention of stackless python.

For now google will keep on using C++, Java, and Python.

---

### Post by CptPicard on 2010-07-12
> **Queue29 said:**
> Google uses C++ (following very strict guidlines) and/or Java for nearly anything.

Actually, Google does use Python for server farm management/deployment kind of tasks. And that App Engine was originally written for Django was certainly interesting.

Another thing that probably is quite high on the list at Google, at least in the research sense, is functional languages; considering how much parallel processing they do (see MapReduce), they will like languages that minimize mutable state.

---

### Post by Sporkman on 2010-07-13
> **Queue29 said:**
> 
Check out:
[http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml)

That was a good read, thanks. :)

---

### Post by cb951303 on 2010-07-13
Interesting detail about Go: it's created by Ken Thompson and Rob Pike which are the guys behind the very interesting OS Plan 9.

---

### Post by ibuclaw on 2010-07-13
> **Queue29 said:**
> Google uses C++ (following very strict guidlines) and/or Java for nearly anything. They have a crack team working on Go, a projected replacement for C++ which is being designed with concurrency and garbage collection in mind from the ground up.

Actually, the way I see it, Go targeted as a replacement for C.
D on the other hand easily replaces C++.

---

### Post by louis--taylor on 2010-07-13
I thought Google employed Guido, the creator of Python? They must find Python useful.

---

### Post by CptPicard on 2010-07-13
Well, if you're creator of Python I am sure Google would be interested in hiring you even in the case when they didn't find the language useful :)

But they do -- I forgot to mention for example the Unladen Swallow project that Google has been working on. Probably to make app engine applications faster.

[http://code.google.com/p/unladen-swallow/](http://code.google.com/p/unladen-swallow/)

I heard they do have issues with it though :(

---

### Post by Queue29 on 2010-07-13
> **CptPicard said:**
> Well, if you're creator of Python I am sure Google would be interested in hiring you even in the case when they didn't find the language useful :)

But they do -- I forgot to mention for example the Unladen Swallow project that Google has been working on. Probably to make app engine applications faster.

[http://code.google.com/p/unladen-swallow/](http://code.google.com/p/unladen-swallow/)

I heard they do have issues with it though :(

The last I heard, Google stopped funding the project (though I'm sure it continues through volunteers). IIRC they weren't seeing the performance increases they were looking for.

---

