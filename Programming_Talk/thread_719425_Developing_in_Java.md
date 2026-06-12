---
title: "Developing in Java?"
date: 2008-03-09
forum: Programming Talk
---

### Post by rye_ on 2008-03-09
Hi,

I intend to start learning java coming from a C/C++, ruby background for use as a multi-purpose web/ desktop app developing language.

My question is; why do I see so few discussions on java on the ubuntu forums?
Are there significant limitations of the language that I am unaware of?

Thanks for your comments

Ryan

---

### Post by Zugzwang on 2008-03-09
Well, you're seeing so few Java threads because there are so many Python threads. ;) That language is preferred by a lot of the posters here because a lot of people are finding it easier to use than C/C++/Java/Whatever. Also Python is used for a lot of the Ubuntu specific stuff and since this is a Ubuntu forum...

For your purpose, Java should be just fine. In fact, it is more or less a matter of taste. Others might of course disagree.

---

### Post by a9bejo on 2008-03-09
> **rye_ said:**
> 
Are there significant limitations of the language that I am unaware of?


Java is both the name of a language and a software platform.  Java as a software platform is very powerful and also popular. But until a few years ago, it was a proprietary technology, so there were only a few incomplete implementations preinstalled on GNU/Linux Desktops systems.  Now that Java is licensed under GPL, expect it to be used far more in the free software community.  On the server side, Java is already used to drive most(?) of the applications out there.  

As a language, Java is still very popular and often used. But there are also design decisions that turned out to be not so clever (like a incomplete OOP design, no operator overloading, checked exceptions).  Also, Python/Ruby/Haskell/Lisp/Erlang/Io  are all more abstract languages than Java.  And because of the idea to [OptimizeLater](http://c2.com/cgi/wiki?OptimizeLater), you might want to write most of your code in the most abstract language you find.

> **rye_ said:**
> My question is; why do I see so few discussions on java on the ubuntu forums?


Language popularity  (and anything else) follows group dynamics , and these boards are very python-centric.  There are other communities that like to talk about Haskell all day. But that does not necessarily mean that the other languages are worse.

---

### Post by xlinuks on 2008-03-09
"Limitations" (compared to native C on Linux):
1) Java is not installed by default
2) In Java  you can't access a lotta things, it has only the "basic set" of features ( no file type checking (soft links/file blocks..), pour desktop integration, (very) pour system tray support..)
3) Application startup takes a while, espacially the cold start.
4) Every java application RAM usage = java_platform_RAM_usage + your_application_RAM_usage which is no less than 10-15MB.
5) Even though Java in some cases is roughly as fast as unoptimized C, its swing GUI is IMO still slow (but  you won't notice that on a core 2 duo machine).
6) The java applications (like any other languages that have a VM behind them) tend to consume more CPU cause the VM in the background is using the CPU to "compile and optimize" which is still usually slower than what gcc/g++ compiles, it also uses the HDD to "cache" and other side effects.
7) Whatever else comes to mind
But I find developing in Java a lot easier (than in a native language, although I'm only learning C++/Gtk2), a random reason would be that the java compiler usually issues understandable error messages like "a semicolon is expected at the end of such and such line", while the g++ compiler yields IMO pretty unclear messages in such a case (and in many other cases).

---

### Post by pmasiar on 2008-03-09
All said above is true, and there is more:
- Java was designed/intended for Enterprise kind of systems, where hundreds of programmers work under control of project managers according to specifications. Free software works best for small self-organized teams which do not have specifications, but explore in code (agile process).
- Java deliberatedly reinvented the whole platform, not using anything (being independent of) Windows and Unix. So for Java web application, you cannot use Apache web server (you need Tomcat), you cannot use your familiar C libraries (you need Java's), etc. Same for tools: Java has own Make, editors, everything. So free software developer need to learn a lot to become productive. Language syntax itself is simple, but libraries are byzantine.
- Statically checked exceptions turned out rather stupid idea.
- Java was build about idea of cross-platform binaries. Free software does not have that problem - you always have source and can recompile for native binaries. So Java solves problem what Free software does not have :-)
- Java is not that grand. If you use Python+C instead, you develop faster, and your code runs faster.

---

### Post by gnuman on 2008-03-09
> **rye_ said:**
> Hi,

Are there significant limitations of the language that I am unaware of?

Ryan

As you have probably seen by now, Python has many fans here, including me.

That said, I must say that Ubuntu has been my favorite OS for programming Java. If you're just starting with Java, use the JDK with a good text editor and you'll be fine.  Later, if you want to use a big IDE, they're here too.

I had to learn Java for my job.  I like it, overall, but I LUV Python. :)

---

### Post by LaRoza on 2008-03-09
Of course, you can use Python on the Java platform if you want, with Jython.

---

### Post by glok_twen on 2008-03-09
i had wondered the same thing recently and concluded based on reading a lot of comments here plus doing some research:

- java is on the order of magnitude of c++ for development complexity (altho one can argue java makes things a bit easier by packaging up all the libraries ones needs)
- c++ typically performs better
- if you want the speed of development and ease of maintenance from a more abstract language, you need to move away from java anyhow, so why not go to python (or php/ror for a web app)

i think as indicated above if you want to build a so-called enterprise class app with a lot of distributed computing pieces java is the way to go. for example, this is a fascinating site on high performance architectures. this link describes the ebay architecture in particular. note how they use jsp's and a distributed data access layer. this is the classic space where python would probably be too slow and c++ while quick enough might be a little more dicey to build and maintain:

[http://highscalability.com/ebay-architecture](http://highscalability.com/ebay-architecture)

also buried deep in the following interview is one persons view on why not java. it boild down to the arguments listed above but it's an interesting watch anyhow:

[http://www.infoq.com/news/2008/02/vinoski-qcon-interview](http://www.infoq.com/news/2008/02/vinoski-qcon-interview)

---

### Post by rye_ on 2008-03-09
Thanks for all your comments.
Would you say then that since I'm already comfortable with ruby (being similar to the much touted python) that I'm better sticking with it?

After all the apps I'd develop would be small to medium only, with 5-10 people involved. 

Ryan

---

### Post by a9bejo on 2008-03-09
> **rye_ said:**
> 
Would you say then that since I'm already comfortable with ruby (being similar to the much touted python) that I'm better sticking with it?


Yes.  And if you are still interested in running your Program on Java, have a look at [JRuby](http://jruby.codehaus.org/) .

---

### Post by LaRoza on 2008-03-09
> **rye_ said:**
> Thanks for all your comments.
Would you say then that since I'm already comfortable with ruby (being similar to the much touted python) that I'm better sticking with it?

After all the apps I'd develop would be small to medium only, with 5-10 people involved. 

Ryan

Perl, Ruby, Python and Tcl fulflill overlapping roles (one could through PHP in there, but it is rarely used outside of servers).

If you know one, there is little reason to learn another. Some people do switch, but most people will stick with what they know the best.

I was going to mention JRuby as well, but I don't know how developed it is.

---

### Post by LaRoza on 2008-03-09
> **glok_twen said:**
> i had wondered the same thing recently and concluded based on reading a lot of comments here plus doing some research:

- java is on the order of magnitude of c++ for development complexity (altho one can argue java makes things a bit easier by packaging up all the libraries ones needs)
- c++ typically performs better
- if you want the speed of development and ease of maintenance from a more abstract language, you need to move away from java anyhow, so why not go to python (or php/ror for a web app)

i think as indicated above if you want to build a so-called enterprise class app with a lot of distributed computing pieces java is the way to go. for example, this is a fascinating site on high performance architectures. this link describes the ebay architecture in particular. note how they use jsp's and a distributed data access layer. this is the classic space where python would probably be too slow and c++ while quick enough might be a little more dicey to build and maintain:

Java has the advantage over C++ in that its binaries are cross platform, and there are many places where Java is used in devices. Blu-Ray is one of them, it uses Java and is a requirement of the specification.

There was an excellant study comparing the develop of Java and Tcl apps, but alas, I forget the link. It is on the Tcl site/wiki somewhere, perhaps someone else will be able to find it.

---

### Post by pmasiar on 2008-03-09
> **rye_ said:**
>  since I'm already comfortable with ruby (being similar to the much touted python) that I'm better sticking with it?

After all the apps I'd develop would be small to medium only, with 5-10 people involved. 

It depends what you want to develop (what kind of application), and what rest of your team will prefer. Yourself, if you know Ruby, you can switch to Python over one weekend, differences are small.

Python has bigger community and more libraries. Someone mentioned RoR (Ruby on Rails) as argument for Ruby, but it was true 3 years ago: since then, (much bigger) Python community developed 2 or 3 web app frameworks comparable to Rails: Django and TurboGears (and possibly Pylons - but TG 2.0 is based on Pylons). 

RoR is rumored as hard to deploy efficiently. Python has some complete GPL/BSD applications, like TinyERP or Satchmo web store.

---

