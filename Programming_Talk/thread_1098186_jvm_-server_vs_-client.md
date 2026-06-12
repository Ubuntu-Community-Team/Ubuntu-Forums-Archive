---
title: "jvm -server vs -client"
date: 2009-03-16
forum: Programming Talk
---

### Post by DocForbin on 2009-03-16
Anyone have experience benchmarking apps using the [server and client JIT]("http://java.sun.com/docs/hotspot/HotSpotFAQ.html#compiler_types")? I'd be curious to know how much more memory was used early on, and at what point/if ever you found performance benefits.

---

### Post by DocForbin on 2009-03-18
bump

---

### Post by slavik on 2009-03-18
From some light reading I've done, server tends to be faster at repeated execution (it caches stuff) whereas client is faster at single run type things. Keep in mind is that the java you run is exactly the same on both sides.

---

### Post by DocForbin on 2009-03-18
What got me thinking about this was a link someone posted in a mono/java thread a while back.

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=javaclient&lang2=java&box=1](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=javaclient&lang2=java&box=1)

I briefly experimented with running a large app on windows 2003 server in -server mode, and never saw any performance benefits. The footprint on startup was maybe 5% larger, and the only other difference I noticed, even after running 24 hours, was the cpu spikes seemed to last a bit longer. I never actually checked when/if the JIT was actually kicking in (I believe by default it waits for 10,000 method invocations). This was a highly unscientific, anecdotal test, of course.

---

### Post by slavik on 2009-03-19
just need to give the proper jvm parameters ;)

---

### Post by DocForbin on 2009-03-19
could you elaborate a bit please :) which parameters to focus on?

---

### Post by Shin_Gouki2501 on 2009-03-19
google is your friend:
[http://java.sun.com/javase/technologies/hotspot/vmoptions.jsp](http://java.sun.com/javase/technologies/hotspot/vmoptions.jsp)

---

### Post by DocForbin on 2009-03-19
> **Shin_Gouki2501 said:**
> google is your friend:
[http://java.sun.com/javase/technologies/hotspot/vmoptions.jsp](http://java.sun.com/javase/technologies/hotspot/vmoptions.jsp)
I've read and even linked to the sun docs in the first post...  I was hoping for some real world input from folks that have experimented with hotspot tuning, particularly when invoking the server JIT.

---

### Post by Shin_Gouki2501 on 2009-03-20
OK!
Well there are diffrent approaches to hotspot "tuning".
Here is an example:
[http://developers.sun.com/learning/javaoneonline/2006/coolstuff/TS-5547.pdf](http://developers.sun.com/learning/javaoneonline/2006/coolstuff/TS-5547.pdf)
here the slides with talk(explanation):
[http://developers.sun.com/learning/j...547/index.html](http://developers.sun.com/learning/j...547/index.html)

All u need is an "java-dev" account.


I watched it some time ago but i do remember that it was crucial to generate many classes at runtime(see the benchmark from the slides). And the server option DID provide an essential boost in this case.

I hope this helps, some more ;)

---

### Post by Shin_Gouki2501 on 2009-03-24
Here is some little explanation on how the jvm optimizes for loops:
[http://www.nabble.com/Question-about-for-td22651486.html](http://www.nabble.com/Question-about-for-td22651486.html)

was the other stuff usefull to you?

---

### Post by Shin_Gouki2501 on 2009-03-25
And here yet another nice jvm optimization explanation (arround 10min)
[http://www.infoq.com/presentations/Evolving-JVM-Ola-Bini](http://www.infoq.com/presentations/Evolving-JVM-Ola-Bini)


the jvm is indeed damn nice :)

---

### Post by mehaga on 2009-03-25
[http://www.excelsior-usa.com/jetcs00007.html](http://www.excelsior-usa.com/jetcs00007.html)
[http://www.excelsior-usa.com/blog/excelsior-jet/java-vs-c-benchmark-excelsior-jet-64-scores-an-equalizer/](http://www.excelsior-usa.com/blog/excelsior-jet/java-vs-c-benchmark-excelsior-jet-64-scores-an-equalizer/)

Both a bit dated, but should answer OP's question.

---

### Post by Shin_Gouki2501 on 2009-03-26
i think those jet stuff were an AOT Compiler...nether the less interesting :)

---

### Post by cl333r on 2009-03-26
I remember Sun advertising the arrival of Java version 6 as the first version where -client performs almost as well as -server and in a few cases even outperforms it.

In short, the performance difference is striking (only) when running older versions of Java.

---

### Post by slavik on 2009-03-26
another thing to note is that some application servers will have their own JVM.

BEA (now Oracle) WebLogic, has Jrockit, while IBM's WebSphere has it's own.

---

### Post by DocForbin on 2009-03-26
> **slavik said:**
> another thing to note is that some application servers will have their own JVM.

BEA (now Oracle) WebLogic, has Jrockit, while IBM's WebSphere has it's own.
If someone tweaking hotspot performance didn't know what jvm their app was running in, that would be sad. Those don't even have permgen space.

---

### Post by mehaga on 2009-03-26
> **Shin_Gouki2501 said:**
> i think those jet stuff were an AOT Compiler...nether the less interesting :)

I've never heard of it till few days ago. Yes, it's an AOT compiler (never heard of that before either :))

But don't forget to read the comments on those tests. People involved in talk there work on JVM, JRockit, Jet... I don't understand half the stuff they talk about, but it's interesting, kind of :p

---

### Post by mehaga on 2009-03-26
> **cl333r said:**
> I remember Sun advertising the arrival of Java version 6 as the first version where -client performs almost as well as -server and in a few cases even outperforms it.

In short, the performance difference is striking (only) when running older versions of Java.

In some of the tests at the link I posted, if i remember well, client outperformed server VM. Also, a guy there, from - what was the name of apache JVM - team, asked the author to repeat the tests with some *special* parameters, which should show their VM was in fact much faster. It turned out it was actually much slower that way :) There's some other funny stuff, go see for your self.

---

### Post by slavik on 2009-03-26
"those" meaning weblogic and websphere jvms?

there are 5 pools in weblogic's jvm: eden, survivor1, survivor2, permgen, system

---

### Post by DocForbin on 2009-03-27
> **slavik said:**
> "those" meaning weblogic and websphere jvms?

there are 5 pools in weblogic's jvm: eden, survivor1, survivor2, permgen, system

not if it uses jrockit

---

### Post by DocForbin on 2009-04-16
For anyone interested, the latest Java Posse podcast is an interview with the Java Labs guys from AMD. It touches on server vs client performance a bit, and other areas of hotspot and application tuning. It's a great listen:

[http://javaposse.com/index.php?post_id=454436](http://javaposse.com/index.php?post_id=454436)

---

