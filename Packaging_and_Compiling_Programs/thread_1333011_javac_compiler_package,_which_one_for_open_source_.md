---
title: "javac compiler package, which one? for open source preferences?"
date: 2009-11-21
forum: Packaging and Compiling Programs
---

### Post by jzacsh on 2009-11-21
Hello,

I'm supposed to take some java courses soon, but I want to get a head start so that I'm comfortable w/Java @ the command line [*see why below, I did the same thing for my c++ course*].

To give myself this head start I'm [reading some basics]("http://java.sun.com/developer/onlineTraining/Programming/BasicJava1/compile.html#comp"):
[http://java.sun.com/developer/onlineTraining/Programming/BasicJava1/compile.html#comp](http://java.sun.com/developer/onlineTraining/Programming/BasicJava1/compile.html#comp)

[COLOR="Blue"]**so I ran the following**[/COLOR] (*according to those ^ instructions*)
```

$ [COLOR="Blue"]**javac ./sample.java**[/COLOR]
The program 'javac' can be found in the following packages:
 * [COLOR="Red"]openjdk-6-jdk[/COLOR] **<-- would this one be the open source choice?**
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * [COLOR="Red"]sun-java6-jdk[/COLOR]
Try: sudo apt-get install <selected package>
javac: command not found

[B][COLOR="Red"]??[/COLOR] $ sudo apt-get install openjdk-6-jdk [COLOR="Red"]??[/COLOR]
[/B]

```

If the above choice is completely preference based, then the only preference I can think of having (*and its *just* a preference*) is using open sourced stuff.

_Given my "preference",_
[LIST]
[*]what would everyone suggest I use?
[*]what do you use?
[*]Any warnings about what I'm about to pick out?
[*]maybe someone can just point me to a list summary of how these differ?
[/LIST]
thanks in advance :D !

(
_**Why I'm not just waiting for class to start**_:
[I]I'm trying to make sure I go into this course with a comfortable/familiar work flow for **writing,compiling,running at the command line.**
**I know the professor will insist that everybody use graphical IDE's for the course.** I understand such a demand from the professor, because this makes it easier for him to teach code instead of work-flow. They do the same thing in C++ courses here.
**_Lucky for me:_**
if I'm comfortable enough that I never have to ask for there help regarding my development work-flow, then the teacher will never complain if he finds me programming - say in vim via ssh on some remote machine - _as long as I only ask him questions about the language itself_
[/I])

---

### Post by SevenMachines on 2009-11-22
personally i use openjdk, as far as i remember its java6 compliant these days, passing all the relevant tests supplied by sun. of course you can always change it to the sun jdk at any point as well if you decide

---

### Post by jzacsh on 2009-11-23
> **SevenMachines said:**
> personally i use openjdk, as far as i remember its java6 compliant these days, passing all the relevant tests supplied by sun. of course you can always change it to the sun jdk at any point as well if you decide

hey, thanks for the reply. By chance (*just before you replied*) I was in a book store and read in an "ubuntu hacks"? book something along the lines of:
"openjdk is Sun's attempt at an open sourced equivalent to there own sunjdk and most of the code is actually written by Sun."

- I think its being written by Sun makes me fairly comfortable with it. If anyone else has a suggestion or tip - I'm all ears.

---

### Post by p1977p on 2009-11-25
Hi, I installed openJDK from thew repos (Karmic___ gnome) but I cannot run any programs ( tried to run a Windows program in wine)..... I get "could not start java virtual mchine". What do I do?

---

