---
title: "Im groovy, why arent you?"
date: 2008-12-28
forum: Programming Talk
---

### Post by tinny on 2008-12-28
I like [Groovy]("http://groovy.codehaus.org/") and have managed with great difficulty to sell it into the organization I work for and its working out really well (we do enterprisey software development).

So why dont more people use it? Im interested in hearing about peoples difficulties with the uptake of this language.

I like it because its basically just dynamic Java and allows me to do almost whatever I want without needing to stick to Java's strict verbose ways. 

The only argument I had to fight against in selling it into my organization was that it has a perception of being just a toy and not a "real" language. "How can serious software development be done with a language named Groovy?" (a quote from a CIO of a very prominent australasian insurance company)

These perceptions bug the hell out of me and have become so prevalent in my industry that they are becoming truth.

If Groovy had a different name I think things would be very different.

Perhaps Java++?

---

### Post by wmcbrine on 2008-12-28
Honestly I don't see how the name "Groovy" is any sillier than "Java". We're just more used to the latter.

And people who think like that should be confined to marketing.

---

### Post by Mr.Macdonald on 2008-12-28
When I first heard of groovy I was disturbed by the name. But when I heard that it was written and interpreted in java I felt terrible. Java just isn't as good as c. And if you want a dynamic language use lisp python. I haven't tried groovy but those beat any doublely interpreted language anyday (java -> groovy). Its great for you to use just I don't plan on using it.

---

### Post by CptPicard on 2008-12-28
> **Mr.Macdonald said:**
> But when I heard that it was written and interpreted in java I felt terrible.

Groovy is compiled to Java bytecode just as Java itself is. That bytecode is then JIT-compiled just any other bytecode that runs on the JVM. Groovy is *not* "interpreted in Java" in the sense you seem to imagine. Actually, Groovy bytecode has a good chance of being faster than Python bytecode, as the JVM JIT-compilation is very good.

> Java just isn't as good as c.

Apples and oranges, apples and oranges.... this is a completely random statement that depends on what you want out of a language, and could spawn a language war all on its own.

> 
 And if you want a dynamic language use lisp python.

The whole point of Groovy is to get a dynamic language on top of the crossplatform JVM plus the ability to use Java libraries...

> 
I haven't tried groovy but those beat any doublely interpreted language anyday (java -> groovy)

Java is not even "singly" interpreted, as even that is bytecode compiled. Python on the other hand goes through a similar parse -> compile -> run bytecode pipeline.

I imagine that by "beating" languages you talk about runtime speed.. I have not seen benchmarks, but I would guess Groovy's performance is adequate. I am more interested in how the language itself "works", and in that department I have some issues with the language's design as it has been specifically written to go down well among Java coders... but to be honest that kind of criticism would go way above the level of the post I'm responding to here :)

---

### Post by tinny on 2008-12-29
> **CptPicard said:**
> Groovy bytecode has a good chance of being faster than Python bytecode, as the JVM JIT-compilation is very good.


Actually the micro benchmarks ive seen show Groovy 1.5 to be several orders of magnitude slower than Python. The 1.6 release of Groovy is about optimization. But as you know this is of little importance really.

> **CptPicard said:**
> 
I am more interested in how the language itself "works", and in that department I have some issues with the language's design as it has been specifically written to go down well among Java coders... 

Please go on. 

To be honest I do find myself reverting back to my Java ways on occasion when an expando would have been the way to go for example.

> **Mr.Macdonald said:**
> When I first heard of groovy I was disturbed by the name. But when I heard that it was written and interpreted in java I felt terrible. Java just isn't as good as c. And if you want a dynamic language use lisp python. I haven't tried groovy but those beat any doublely interpreted language anyday (java -> groovy). Its great for you to use just I don't plan on using it.

Case in point. Perception ;-) You have not used it, dont plan to, completely misunderstand it, yet feel qualified to pass judgment.

> **wmcbrine said:**
> Honestly I don't see how the name "Groovy" is any sillier than "Java". We're just more used to the latter.

And people who think like that should be confined to marketing.

Maybe its just isolated to my industry, but more often than not its the bean counters, project managers and marketers that choose the technologies in my "enterprisey" systems. Its amazing how warm and fuzzy a IBM or Oracle salesman can make you feel. E.g. "you brought me a really nice dinner, your technology suite must be quality" or "look at the quality of their brochures..." 

Its no surprise to me that programmers for the most part dont really care about the name, but if you cast your net wider to the other professions that influence the software industry...

---

### Post by Cracauer on 2008-12-29
The name definitely hurts.

And people wearing ties never get dynamically typed languages. Assuming they get the idea of two different languages sharing the same backend. You can't expect them to get the idea that the Java VM can be used from a different language. That's one and the same for them.

Anyway, and yes the name hurts. Anything "cute", or "Free" and whatnot is a big problem. Also was for FreeBSD (compared to NetBSD).

---

### Post by nvteighen on 2008-12-29
Groovy... It isn't that bad as "Ruby on Rails" (Is Ruby a train?) or "IronPython" (a silly rhyme) or "Squeak"... Even "Python" sounds silly to me.

The best programming language name, IMO, is "Clojure", as it takes advantage of a clever orthographic change to represent the phoneme /3/, to also make it clear it is a JVM language and also, to tell it is a pure-functional programming language. It's amazing how much it is implied in such a simple word play.

---

### Post by Quikee on 2008-12-29
We never tried to adopt Groovy but some other "section" in our company did for a while in one project. They said Groovy was nice and the Eclipse plugin for Groovy is also good, so they started to use it for some parts of the project. 

But once the project grew and many groovy files were produced working with Eclipse became very slow and it compiled very long (so they have said). This was the reason why they dropped Groovy and rewritten those parts in Java. The name "Groovy" however was never the problem.

---

### Post by pmasiar on 2008-12-29
I think the name is "revenge of the marketoids" because the obvious correct name - JavaScript - was taken by completely unrelated language for marketing reasons. 

Suits without clue are always the deciders, for worse  or worse (there is no 'better' in that situation). The only solution is to work in a small company, which is forcing to "beat the averages" - see Graham's essay. What possibly might work is to evangelize test-driven development and agile methods - there is no way to prove to a suit that some languege is better, but they do care about measurable financial process.

---

### Post by tinny on 2008-12-29
> **pmasiar said:**
> 
What possibly might work is to evangelize test-driven development and agile methods - there is no way to prove to a suit that some languege is better, but they do care about measurable financial process.

We have been trying to shoe horn TDD and agile methods in your Java stacks for a long time now. Its a real pain because as you know Java code stands up like a towering steel structure that is not easily refactored.

The first step for me was to introduce Groovy as a testing language. JUnit is built right in and expando's take care of object mocking.

Next I introduced Grails to develop a prototype to be used as a sales tool. The bean counters loved the fact that when the project was accepted we didnt have to start over and could instead evolve our prototype.

As this project progresses im hoping to demonstrate the long term productivity gains. We are currently half way through Sprint one of the project and have nearly completed all planned sprint one story cards!

---

### Post by kavon89 on 2008-12-30
I'm not cool enough to be Groovy.

---

### Post by bobrocks on 2008-12-30
> **tinny said:**
> We have been trying to shoe horn TDD and agile methods in your Java stacks for a long time now. Its a real pain because as you know Java code stands up like a towering steel structure that is not easily refactored.


I'm afraid I don't know, can you expand a bit more as to why java code is not easily refactored?  I can't say I have noticed this trait.


As to why corporations don't adapt groovy, it's probably more to do with training, available resources, performance, clout etc more than the fact it is called groovy.  It's the same reason companies don't just jump ship to other languages all the time and stick with Java/c/c++/perl even if another language could be a little better for task X.  

If you have 30 people in your company and they all write Java, you start a new project in Groovy with 3 people, that prototype is then accepted and the customer comes on board wanting it soon.  You then have 27 people who don't know the language that can't come straight on board and help you.  It's not like you just need to learn the syntax for loops and things you need to understand the language, how it is used to solve problems, what works fast what is slow.  If you start cold with a bunch of people who have never used a language in anger I am willing to bet at least 10pence that your first project or two will not be well written or in any way consistent.

Then there is resources, say there is too much work coming in and you need to bring in new developers/contractors, what chance do you have of bringing in Groovy people that have any real experience that you don't have to train yourself?

Then there is performance, I haven't followed it much this year but last time I looked at groovy, all floating point calculations were done as BigBecimal and then converted to Double(object not primitive) which meant numeric computation was very slow and memory intensive.  This may not matter in your project but if performance is important you may end up writing 90% in java and then what have you gained from all this outlay?

If you are selling your product the term Java will have more clout, it is universal now, if you say the software is written in Groovy then most people probably have no idea that language even exists.


And after all of this to fly in the face of what I just said, in the new year we are doing an interface into one of our systems that does not have performance requirements and the non-functional spec has the word groovy at the top under possible language choices.

---

### Post by tanxiaojing on 2008-12-30
Are you a lover of sports? If your answer is yes, keep going. It is a good habit; it will keep you healthy and fit.
  In order to enjoy your sports, you need some good quality sportswear. However the high cost may keep you from enjoying the sports. Don’t worry. From now on, we will solve the problems for you. We are one of the Chinese sportswear trading company; we sell all kinds of sportswear at the reasonable price.
  More details please click [http://www.nikeboss.com]("http://www.nikeboss.com")
  I really hope you can find what you need.
MSN: [http://nikeboss@live.com]("http://nikeboss@live.com")

---

### Post by tinny on 2008-12-30
> **bobrocks said:**
> I'm afraid I don't know, can you expand a bit more as to why java code is not easily refactored?  I can't say I have noticed this trait.


This is something I only really noticed once I started playing with dynamic languages (Have you tried Python, Ruby or Groovy?). Think of your standard Java web application. Now you have just spent 2 months coding and then the customer changes some requirements, with your standard Java web app you now need to modify a bunch of XML, delete / modify interfaces then recreate your nice OO structure etc... Also the volume of Java code you write tends to be much greater than Groovy for example. Now I do admit that modern IDE's help a lot, but if you just think about the Java language it does very little to help you out in this exercise.

But really this is something you need to see for yourself. Have a play with Groovy and you will soon see what I mean.

> **bobrocks said:**
> 
As to why corporations don't adapt groovy, it's probably more to do with training, available resources, performance, clout etc more than the fact it is called groovy.  It's the same reason companies don't just jump ship to other languages all the time and stick with Java/c/c++/perl even if another language could be a little better for task X. 
 

Yep it is true that some will think this way. But in my opinion this is no excuse for not using the best tools available. If a company chooses to not invest in its people they are not worth working for. After all software is about technology and technology doesn't age like wine does. E.g .net has pretty much murdered the Dephi guys.

> **bobrocks said:**
> 
If you have 30 people in your company and they all write Java, you start a new project in Groovy with 3 people, that prototype is then accepted and the customer comes on board wanting it soon.  You then have 27 people who don't know the language that can't come straight on board and help you.  It's not like you just need to learn the syntax for loops and things you need to understand the language, how it is used to solve problems, what works fast what is slow.  If you start cold with a bunch of people who have never used a language in anger I am willing to bet at least 10pence that your first project or two will not be well written or in any way consistent.


About 80% of Java syntax is valid Groovy syntax and Groovy leverages fully from the standard Java class library. You can ignore the dynamic features of Groovy and just use it for its syntax sugar and this would probably be fine for someone who is just learning the language. To be honest with you I would be embarrassed to work with a bunch of developers that couldn't pick up Groovy in a couple of days. 

BTW im not advocating the use of Groovy for everything. E.g. A team of 20+ developers on a Groovy (Grails) project would freak me out.

> **bobrocks said:**
> 
Then there is performance, I haven't followed it much this year but last time I looked at groovy, all floating point calculations were done as BigBecimal and then converted to Double(object not primitive) which meant numeric computation was very slow and memory intensive.  This may not matter in your project but if performance is important you may end up writing 90% in java and then what have you gained from all this outlay?


Yeah, they haven't optimized the Language yet. I use it for web applications (Grails) so this isnt a big deal for me. Being human im most likely to be the biggest performance issue in the system :-)

> **bobrocks said:**
> 
If you are selling your product the term Java will have more clout, it is universal now, if you say the software is written in Groovy then most people probably have no idea that language even exists.


Yes this is the perception, even though Groovy uses the same platform as the Java language. Also the same app servers, third party API's etc.  

> **bobrocks said:**
> 
And after all of this to fly in the face of what I just said, in the new year we are doing an interface into one of our systems that does not have performance requirements and the non-functional spec has the word groovy at the top under possible language choices.

Congratulations :-)

---

### Post by bobrocks on 2008-12-30
> **tinny said:**
> This is something I only really noticed once I started playing with dynamic languages (Have you tried Python, Ruby or Groovy?). Think of your standard Java web application. Now you have just spent 2 months coding and then the customer changes some requirements, with your standard Java web app you now need to modify a bunch of XML, delete / modify interfaces then recreate your nice OO structure etc... Also the volume of Java code you write tends to be much greater than Groovy for example. Now I do admit that modern IDE's help a lot, but if you just think about the Java language it does very little to help you out in this exercise.

But really this is something you need to see for yourself. Have a play with Groovy and you will soon see what I mean.


I use python as glue too bring together all of our automated performance testing systems, generate structured reports and handle telling people when performance has dropped after a checkin.  I quite enjoyed learning python doing this but I never had that eureka moment people seemed to get writing python after java. I used to use perl then php for web development work many years back.  My own web stuff is in django, so yes I have played with them.  

Saying that using dynamic languages will make a new requirement change easier is not a metric you can really measure.  It completely depends on your code, what tools you are using and what kind of change it is.  If you have an oo structure in java or groovy you are still going to have to change your bases and fix the strucure if it is that fundamental a change.  And depending on what you are using xml for if you are using groovy ontop of your java api's you may have to change your xml anyway.  I find java code very easy to refactor because it gives you the features to forcefully hide the implementations details away behind an interface.  We also use OSGi which gives us even more.

> 
Yep it is true that some will think this way. But in my opinion this is no excuse for not using the best tools available. If a company chooses to not invest in its people they are not worth working for. After all software is about technology and technology doesn't age like wine does. E.g .net has pretty much murdered the Dephi guys.


I agree that companies should invest in its people, but I can't agree with you that Groovy is a worth while investment as I don't believe just now that it is.  There is quite a few languages coming on the JVM that can use the java standard libraries, scala, clojure being two big ones.  I see them picking up steam and aclaim from technology sites and developers that I follow.  There is a lot of talk about Clojure exploding this year.  I hear nothing about groovy, I have no reason to believe that groovy will stick around or pick up any real momentum for companies to adapt it and make an investment in it's viability.  There is a lot of companies that get themselves in trouble jumping around languages looking for some magic bullet and never finding it, perl to java to php to ruby to where?  I think there has to be some middle ground where you can train your developers to be better developers in their current language.  

> 
About 80% of Java syntax is valid Groovy syntax and Groovy leverages fully from the standard Java class library. You can ignore the dynamic features of Groovy and just use it for its syntax sugar and this would probably be fine for someone who is just learning the language. To be honest with you I would be embarrassed to work with a bunch of developers that couldn't pick up Groovy in a couple of days. 

BTW im not advocating the use of Groovy for everything. E.g. A team of 20+ developers on a Groovy (Grails) project would freak me out.


I haven't actually used groovy properly to argue this against it but I equate a big diference between picking up a language and effectively using a language.  

> 
Yeah, they haven't optimized the Language yet. I use it for web applications (Grails) so this isnt a big deal for me. Being human im most likely to be the biggest performance issue in the system :-)


:) It's usually us in whatever language we are using, but it doesn't help to get the langauge adopted.

> 
Congratulations :-)


We will see, it might not even be me that works on it.  It wasn't me that sugested it :) (I suggested python as we won't need any of our api's for access and I really like matplotlib)

---

### Post by tinny on 2008-12-30
> **bobrocks said:**
> I use python as glue too bring together all of our automated performance testing systems, generate structured reports and handle telling people when performance has dropped after a checkin.  I quite enjoyed learning python doing this but I never had that eureka moment people seemed to get writing python after java. I used to use perl then php for web development work many years back.  My own web stuff is in django, so yes I have played with them.
  

If it was your money being spent what would you use? django? (ive had a little play with django and thought it was cool)

> **bobrocks said:**
> 
And depending on what you are using xml for if you are using groovy ontop of your java api's you may have to change your xml anyway.


Spring wiring. I should clarify the XML comment I made. Ive been using Grails for my web dev. The thing ive noticed with dynamic languages is that they tend to have a culture of simplicity that surrounds them. Grails is a good example of this. Grails forces you to use convention over configuration and has a really good plug-in system.

IMO Grails is easier to use than Spring MVC for example.

Culture of simplicity:

Python > django, TG
Ruby > Rails

> **bobrocks said:**
> 
I agree that companies should invest in its people, but I can't agree with you that Groovy is a worth while investment as I don't believe just now that it is.  There is quite a few languages coming on the JVM that can use the java standard libraries, scala, clojure being two big ones.  I see them picking up steam and aclaim from technology sites and developers that I follow.  There is a lot of talk about Clojure exploding this year.  I hear nothing about groovy, I have no reason to believe that groovy will stick around or pick up any real momentum for companies to adapt it and make an investment in it's viability.  There is a lot of companies that get themselves in trouble jumping around languages looking for some magic bullet and never finding it, perl to java to php to ruby to where?  I think there has to be some middle ground where you can train your developers to be better developers in their current language.  


I think the Groovy hype is actually being eclipsed by the hype for Grails.

I dont think that Groovy is the best Dynamic language around. As I think I said in my OP it feels like "Dynamic Java" to me, a sort of natural evolution of the Java language. I look at Groovy as Java with dynamic features.

Groovy has this on its side:

It has a JSR [http://jcp.org/en/jsr/detail?id=241](http://jcp.org/en/jsr/detail?id=241)

[http://blog.springsource.com/2008/11/11/more-weapons-for-the-war-on-complexity-springsource-acquires-groovygrails-leader/](http://blog.springsource.com/2008/11/11/more-weapons-for-the-war-on-complexity-springsource-acquires-groovygrails-leader/)

> **bobrocks said:**
> 
I haven't actually used groovy properly to argue this against it but I equate a big diference between picking up a language and effectively using a language.  


True

At the moment I would only use Groovy for Grails web apps, Swing applications or a enterprise testing language.

---

### Post by pmasiar on 2008-12-30
> **tinny said:**
>  (about refactoring Java code) This is something I only really noticed once I started playing with dynamic languages (Have you tried Python, Ruby or Groovy?). Think of your standard Java web application. Now you have just spent 2 months coding and then the customer changes some requirements, with your standard Java web app you now need to modify a bunch of XML, delete / modify interfaces then recreate your nice OO structure etc... Also the volume of Java code you write tends to be much greater than Groovy for example. Now I do admit that modern IDE's help a lot, but if you just think about the Java language it does very little to help you out in this exercise.


I also have noticed that, and as I see it, it is because IDE provides lots of help **to generate new code** but little help (and less intuitive) when **refactoring existing code**. IntelliJ IDEA was better than eclipse in this regard. KLOC - Lines of code is not asset but liability, because you need to maintain them - but IDE (and verbose languages like Java) pretend that the more lines you have, the better off you are - which is in my experience, far from truth.

---

### Post by tinny on 2008-12-31
BTW bobrocks, thanks for your input.

---

