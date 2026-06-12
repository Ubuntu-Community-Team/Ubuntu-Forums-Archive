---
title: "C++/C#/Java/Python for Large Scale GUI Programming?"
date: 2008-04-30
forum: Programming Talk
---

### Post by jsmidt on 2008-04-30
I don't want to start a flamewar.  But I really could use some other opinions.

I want to start creating some GUI projects that hopefully one day will be fairly large scale with contributions of several other programmers and be around for many years.

Assuming I can pull that off, what language, between C++/C#/Java/Python, do you think would be best to use for the project.  Please be objective and specific about these concerns:

1.  Which language is best suited for a large scale GUI project?

2.  Which language will probably be most used in the future for GUI programming?

3.  Which language will be best supported in the future?

4.  Which language will be the best for cross-platform computing? (Keep future in mind.)

5.  Which language will make contributing programmers happiest to use?  

6.  Anything else I should know.  

Thanks.

---

### Post by LaRoza on 2008-04-30
> **jsmidt said:**
> 
1.  Which language is best suited for a large scale GUI project?

2.  Which language will probably be most used in the future for GUI programming?

3.  Which language will be best supported in the future?

4.  Which language will be the best for cross-platform computing? (Keep future in mind.)

5.  Which language will make contributing programmers happiest to use?  

6.  Anything else I should know.  


0. A mix. C (for example) for the intensive bits and Python (for example) for the rest.

1. My crystal balls says higher level languages

2. Java, Python, C, C++, Perl, etc (Try not to use proprietary languages)

3. Java, Python 

4. See all languages above

5. The language is not really important in this regard. OpenOffice uses Java a lot, Oblivion (a large RPG) uses C and Python. Use what works and what you are willing to learn.

* Python can be replaces with Perl and Ruby in the above list.

---

### Post by GoCool on 2008-04-30
> **jsmidt said:**
> 
1.  Which language is best suited for a large scale GUI project?


Some RAD tools which is stable. I heard of GAMBAS but never got a chance to work on it, its a.k.a Visual Basic of Microsoft.

> **jsmidt said:**
> 
2.  Which language will probably me most used in the future for GUI programming.


Specifically for GUI I am not sure, but C/C++ is the time tested language which was, will and always be there. Every one comes up with their libraries to re-use. But it's not easy to program and maintain as the bulk increases. May be JAVA then.

> **jsmidt said:**
> 
3. Which language will be best supported in the future?


You can never know unless future happens. But again C/C++ will be always there. Even though M$ is pushing C#, I am not sure whether they will create a CLR (Common Language Runtime) for Linux. But plain vanilla C/C++ is not a good GUI tool. You have to get a good IDE to go along with it, with plenty of re usable libraries. But still it wouldnt be a RAD (Rapid Application Development) tool.

> **jsmidt said:**
> 
4. Which language will be the best for cross-platform computing. (Keep future in mind.)


JAVA or Python 

> **jsmidt said:**
> 
5. Which language will make contributing programmers happiest to use? 


Depends on how they are groomed in the programming arena. But definitely a RAD tool is what programmers would like, so that they can just concentrate on the logic and not to bother about other nitty gritties.

> **jsmidt said:**
> 
6. Anything else I should know.


You may not get the perfect tool, but I am assuming, like all others you will pick up a tool which _nearly _matches your requirement and go ahead. But again as always you will come to a point where you will feel you should have chosen another tool, which is quite normal.

---

### Post by LaRoza on 2008-04-30
> **GoCool said:**
> Some RAD tools which is stable. I heard of GAMBAS but never got a chance to work on it, its a.k.a Visual Basic of Microsoft.

You can never know unless future happens. But again C/C++ will be always there. Even though M$ is pushing C#, I am not sure whether they will create a CLR (Common Language Runtime) for Linux. But plain vanilla C/C++ is not a good GUI tool. You have to get a good IDE to go along with it, with plenty of re usable libraries. But still it wouldnt be a RAD (Rapid Application Development) tool.

Depends on how they are groomed in the programming arena. But definitely a RAD tool is what programmers would like, so that they can just concentrate on the logic and not to bother about other nitty gritties.


Gambas is the last tool you'd want to use. CIL is the standard. CLR is the MS implementation of the standard. There is a Linux implementation of it also, Mono.

RAD isn't the most important part I think. The GUI and inner workings will be separate and the time to fine tune the GUI will be worth it. Also, it won't be language dependant. Glade works with GTK and many languages (same with QT, wxWidgets), so the GUI toolkit is what matters.

---

### Post by tseliot on 2008-04-30
> **jsmidt said:**
> I want to start creating some GUI projects that hopefully one day will be fairly large scale with contributions of several other programmers and be around for many years.
What will such programs do i.e. what is the purpose of such programs?

---

### Post by pmasiar on 2008-04-30
> 1.  Which language is best suited for a large scale GUI project?

The one your team knows deeply. I prefer Python.

> 2.  Which language will probably be most used in the future for GUI programming?

GUI is not computationally intensive, so despite previous advice, C/C++/Java have **least** sense here. Any hig-level language is good. I suggest Python.

> 3.  Which language will be best supported in the future?

Read [www.paulgraham.com/hundred.html](www.paulgraham.com/hundred.html) - The Hundred Year language.

> 4.  Which language will be the best for cross-platform computing? (Keep future in mind.)

Java and Python

> 5.  Which language will make contributing programmers happiest to use?  

Python, not Java. :-)

> 6.  Anything else I should know.  

Python :-)

Seriously, for fun open-source project, Python is the best choice, with possibly custom libraries in C for speed. Or Stackless Python.

---

### Post by LaRoza on 2008-04-30
> **pmasiar said:**
> 
Seriously, for fun open-source project, Python is the best choice, with possibly custom libraries in C for speed. Or Stackless Python.

Or Jython? 

I don't know how that project is coming along though.

---

### Post by Quikee on 2008-04-30
> **LaRoza said:**
> Or Jython? 

I don't know how that project is coming along though.

Great... Jython is now funded by Sun so the main developer is working full time on it.

---

### Post by pmasiar on 2008-04-30
> **Quikee said:**
> Great... Jython is now funded by Sun so the main developer is working full time on it.

I appreciate Sun finally supporting Python/Jython, but:

1) it is 10 years after Jython was created - better then nothing, but kinda too late to help Java in any significant way
2) MSFT hired Jython author to create IronPython, and has team to integrate other dynamic languages into .NET, 
3) MSFT works to make runtime better for dynamic languages (and leaving C# for libraries) - will ever Sun consider such cannibalizing of Java market?

I do like Sun supporting Python, but I am frustrated how much stronger Sun's position against MSFT might be if they were just little smarter. And I know that past performance does not guarantee future results, but it does kinda worry me... :-)

---

### Post by Mason Smith on 2008-04-30
I strongly believe in incremental development. There is Q.T which looks the same in windows and KDE and mostly Gnome. And there is GTK "The Gimp Toolkit" which uses an object oriented C but has several bindings in other languages. If developers knew the answers to those questions asked in this thread they would be ahead of the game.

---

### Post by Quikee on 2008-04-30
> **pmasiar said:**
> 
1) it is 10 years after Jython was created - better then nothing, but kinda too late to help Java in any significant way


Well how would Jython help Java anyway. It is not like Java didn't had other dynamic languages before Jython - Sun just didn't support it financially but as far as I know they did support JRuby instead. 

In the mean time also some JVM domestic languages have emerged like Groovy and Scala. Groovy is particularly interesting as it is a language similar to Python and Ruby, but the interesting part is that you can program in pure Groovy or pure Java or anything in between (Java code is also valid Groovy code which means that the learning curve for someone that already knows Java is pretty low). The bad thing is that it is currently quite slow. 

> **pmasiar said:**
> 
2) MSFT hired Jython author to create IronPython, and has team to integrate other dynamic languages into .NET,

Nice for them.. but of course I already knew that. ;)

> **pmasiar said:**
> 
3) MSFT works to make runtime better for dynamic languages (and leaving C# for libraries) - will ever Sun consider such cannibalizing of Java market?

Well.. Java is not only Sun any more as the control was taken over by a council and judging by all the fuss about Groovy and dynamic languages in general I would say that they are planning to add better support for dynamic languages into JVM.

> **pmasiar said:**
> 
I do like Sun supporting Python, but I am frustrated how much stronger Sun's position against MSFT might be if they were just little smarter. And I know that past performance does not guarantee future results, but it does kinda worry me... :-)

I am also very frustrated about it as Java could be a much better environment and than it currently is (catching up to C#), however I am optimistic. In less than a weak JavaOne (probably the biggest Java conference) will take place so most announcements about Java's future will be made there. Lets wait and see.

---

### Post by jsmidt on 2008-04-30
Thanks everyone for the input, now I have a couple more questions:

1.  Why is there not more support for C#?  I have had many people tell me the .Net framework is great.  Is the reason for no support: it is from Microsoft and is therefore bad, or are there more objective reasons to choose something else.

2.  About GTK bindings.  How much performance difference is there in a GTK program written using different language bindings?

Again, thanks in advance.

---

### Post by pmasiar on 2008-04-30
> **jsmidt said:**
> Why is there not more support for C#? 

Why should be?

We had this discussion many many times, check archives and create 'Why love/hate C#' with links to them. This way, you will earn more than current snapshot of opinions, many people are bored by this discussion and will rightly ignore it. 

Summary: C# was created by MSFT when Sun sued them for subverting Java standard. C# adds little to languages already available in FOSS, and even if language is ISO standard, libraries are not certain against patent attack. It is nice language, but in opinion of many (even if not all), not worth the risk.

---

### Post by pmasiar on 2008-04-30
> **Quikee said:**
> Well how would Jython help Java anyway.

By being more productive environment for developers? By not splitting community efforts to half a dozen almost equivalent dynamic languages?

> I would say that they are planning to add better support for dynamic languages into JVM.

MSFT is not planning - they did it, and when reading what seamless integration is possible in IronPython, I am jealous. :-)

> I am also very frustrated about it as Java could be a much better environment and than it currently is (catching up to C#), however I am optimistic. 

Stop right there! How Java is catching up to C# if it had head couple of years of  start? How come C# is ahead? And How you can be optimistic about it?

> Lets wait and see.

Yes, and then let's wait and  see some more... Dell servers are eating Sun's lunch in hardware, Linux is replacing Solaris, and C# is encroaching on Java territory. How's Sun's profit? Stock price? Will they have money to invest to community, if they haven't smarts to do it when it could make difference? 

Wait and see is the only thing we can do. :-(

---

### Post by Quikee on 2008-05-01
> **pmasiar said:**
> By being more productive environment for developers? By not splitting community efforts to half a dozen almost equivalent dynamic languages?

Yes - it would make the environment slightly more productive, but I don't think it would matter much. Other languages would happen anyway (just because they can - a Ruby fan wouldn't be happy and would start its own JVM based Ruby anyway, a "mastermind" would think that both are not enough and would create its own (dynamic) language just because he can) the same way they are emerging for CLR (Boo, IronRuby, Cobra, even Java itself ;) )

> **pmasiar said:**
> Stop right there! How Java is catching up to C# if it had head couple of years of  start? How come C# is ahead? And How you can be optimistic about it?

Sun just fell asleep and didn't evolve the language too much - which was a mistake but honestly there had no need to do it. C# just took what Java had in the beginning and evolved the language - this way all the head start was nullified. 

I am optimistic because now Java (the language) is starting to move again taking good things out of C#, which make sense for Java.
JVM will gain support for dynamic languages in Java 7 (the interesting thing is that the HotSpot JVM was at first meant for SmallTalk, which is a dynamic languages). 
With the Java environment in general liberated now it has the chance to dominate in open source world. 

Seeing also IDEs like Eclipse and NetBeans evolve in great tools for multiple languages (no matter how "great" Visual Studio currently is the design of Eclipse is just superior - you can quite easily design your domain specific language as a Eclipse plugin and ship it to the users with practically no cost except development time - no payment for licences, easy "unzip only" deployment).

> **pmasiar said:**
> Yes, and then let's wait and  see some more... Dell servers are eating Sun's lunch in hardware, Linux is replacing Solaris, and C# is encroaching on Java territory. How's Sun's profit? Stock price? Will they have money to invest to community, if they haven't smarts to do it when it could make difference? 

Wait and see is the only thing we can do. :-(

Generally I don't care about Sun as this is not about Sun at all - Java is not in Suns control any more (however they are still a big player) - there is bigger community that carve the future of Java environment.

Still.. Sun buying MySql AB and InnoTek and opening new potential fronts for making money I don't think they is any danger to go out of money for funding communities projects any time soon.

---

### Post by RIchard James13 on 2008-05-01
> **jsmidt said:**
> 2.  About GTK bindings.  How much performance difference is there in a GTK program written using different language bindings?

Nobody clicks that fast. Only when the system is doing background processing will you notice the speed difference between say a C++ program and a Python one. For the GUI language speed is pretty much moot these days.

GTK does most of the work for the program. If you go to the menu of a program and flick around real quickly that is GTK at work not the program behind it. Only when the user triggers an event that is captured does the client program become involved. A program should only capture events that it needs to work, anything spurious is a waste of code.

This is the same for any toolkit. The toolkit handles all the drawing and only sends signals to the client program that it asks for. Read up on event driven programming.

---

### Post by LaRoza on 2008-05-01
> **pmasiar said:**
> Why should be?

We had this discussion many many times, check archives and create 'Why love/hate C#' with links to them. This way, you will earn more than current snapshot of opinions, many people are bored by this discussion and will rightly ignore it. 

Summary: C# was created by MSFT when Sun sued them for subverting Java standard. C# adds little to languages already available in FOSS, and even if language is ISO standard, libraries are not certain against patent attack. It is nice language, but in opinion of many (even if not all), not worth the risk.

Good idea. The Holy Wars thread has the entry, but no link yet.

---

