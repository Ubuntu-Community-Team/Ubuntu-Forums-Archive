---
title: "Dynamic Languages for enterprise development"
date: 2008-08-25
forum: Programming Talk
---

### Post by tinny on 2008-08-25
Hello all

First off this is not a language flame war!!!

I have a genuine interest in this discussion being as productive as possible. So no noise please.

I am a J2EE developer, I have been developing J2EE applications for sometime now. Thanks to this forum (specifically about 3-4 members) I have had my eyes opened to the world of dynamic languages. Ive been doing a little bit of hacking at home with Python and I have to say I have really enjoyed it. 

We do have a very good sticky in this forum that addresses the whole language selection topic, but I believe that I have some very specific needs in a dynamic language that cannot be answered by the sticky.

For me its time to take the next step (looking to use a dynamic language for my professional development). 

Here are the contenders as I see it:

JRuby, Groovy and Jython

I am interested in a language that has good hooks into Java classes and J2EE container managed functionality so that I can leverage off the scalable APIs that J2EE offers (The various enterprise bean technologies etc...). I am also looking for a language with a very good ORM implementation (similar or better than the Hibernate annotations approach). 

Here is some further reading to get the thread started:
[http://blogs.sun.com/seapegasus/entry/groovy_jruby_jython_scala_who](http://blogs.sun.com/seapegasus/entry/groovy_jruby_jython_scala_who)
[http://www.tbray.org/ongoing/When/200x/2004/12/08/DynamicJava](http://www.tbray.org/ongoing/When/200x/2004/12/08/DynamicJava)

Some random thoughts I have:

JRuby – Very good support in NetBeans (Sun have been behind it for a while)
Jython – I have a soft spot for Jython as I will gain skills (Python) that are directly transferable to my private passion for Ubuntu. Has proper support in Django.

[http://blog.leosoto.com/2008/08/django-on-jython-its-here.html](http://blog.leosoto.com/2008/08/django-on-jython-its-here.html) (Thanks pmasiar )

Groovy – I know almost nothing about it.

(Not using the JVM / Java Application server is not an option for me right now)

So any thoughts? Id be especially interested to here posts about peoples experiences with dynamic languages in Enterprise development (In the J2EE world). I am just about to invest my time in learning one of these approaches, so id like to choose the best approach possible.

Thanks :)

---

### Post by CptPicard on 2008-08-26
Of course it's a language flamewar.

[IMG]http://media.urbandictionary.com/image/large/internet-24591.jpg[/IMG]

To be honest, no idea, never tried, but still toss some ideas in the air about "stuff I don't have experience on", from the speculative POV of Jython...

The J2EE container is going to be your biggest problem. The Java interfacing from Jython works ok from Jython to Java (and languages like Clojure), but the other way around? The whole problem is that you don't just call Java libs in J2EE development, your classes and other stuff need to be embedded pretty deep into the container, and the container will want to call into your beans, inject them into each other, instrument them with all kinds of code-generation and all the weird magic that the containers do AFAIK to run transactions across components and so on. This is going to be hard to achieve I suppose. And I can't even begin to imagine how to use annotations like they're used in J2EE.

Now, you can always write some kind of J2EE component wrappers in Java and call into your Jython side from there but that sounds ugly...

Second problem -- ORM mappers in Python at least are pure-python code, so I am not really sure how well they play along with Jython. And of course none of that is going to integrate to the container. Calling Hibernate from Jython should work, but again, I suspect you'll introduce a Jython layer between container and Hibernate that breaks all the nice persistence...

IMO you've chosen a pretty hard application domain :)

---

### Post by tinny on 2008-08-26
> **CptPicard said:**
> 
Of course it's a language flamewar.


Yes, for the members that have no idea what we are talking about. Id prefer if they didnt comment personally.

> **CptPicard said:**
> 
The J2EE container is going to be your biggest problem. 


Yep, it may be a show stopper :(

> **CptPicard said:**
> 
The Java interfacing from Jython works ok from Jython to Java (and languages like Clojure), This is going to be hard to achieve I suppose. And I can't even begin to imagine how to use annotations like they're used in J2EE.


Doesn't have to be annotations. Could be a specific ORM scheme for a specific dynamic language. (but then you lose the container managed persistance)

> **CptPicard said:**
> 
Now, you can always write some kind of J2EE component wrappers in Java and call into your Jython side from there but that sounds ugly...


... and a lot of work! Would defeat the whole reason for trying to use a dynamic language in the first place :(

> **CptPicard said:**
> 
Second problem -- ORM mappers in Python at least are pure-python code, so I am not really sure how well they play along with Jython. And of course none of that is going to integrate to the container. Calling Hibernate from Jython should work, but again, I suspect you'll introduce a Jython layer between container and Hibernate that breaks all the nice persistence...


Yes :(

> **CptPicard said:**
> 
IMO you've chosen a pretty hard application domain :)


I know, but wouldn't it be amazing if we could find a solution?

---

### Post by Quikee on 2008-08-26
From the "bunch" you mention IMHO you will have the most luck Groovy. The problem with JRuby and Jython is that they try to be compatible with Ruby and Python and at the same time want to be integrated well with the JVM which introduces some mismatches and unclean solutions. Groovy on the other hand was written for the JVM and doesn't have such problems and integrates well with Java also.

I would not try to introduce a dynamic language full blown in one step. Do it step by step. First try to replace Java with a dynamic language in test, then do it on GUI - if you have it, then slowly introduce it business logic (if you have some)...

---

### Post by tinny on 2008-08-26
Groovy and JPA :)

[http://www.curious-creature.org/2007/03/25/persistence-made-easy-with-groovy-and-jpa/](http://www.curious-creature.org/2007/03/25/persistence-made-easy-with-groovy-and-jpa/)

And WOW EJB3!!!

[http://www.infoq.com/articles/grails-ejb-tutorial](http://www.infoq.com/articles/grails-ejb-tutorial)

Fantastic!!!

---

### Post by Ruhe on 2008-08-26
As far as I know jython development was freezed for a long time, and was unfrozen only after successfull appearence of jruby.
Today by words of [Charles Oliver Nutter]("blog.headius.com") (jruby core developer) jruby runs as fast as standart MRI(Matz ruby implementation) does.
Ruby community came to decision to use [rubyspecs]("http://rubyspec.org/") - executable specifications for ruby implementations. So jruby should be 100% compatible with MRI ruby (correct me if I'm wrong).
It's really interesting to mix dinamic languages with Java.

---

### Post by tinny on 2008-08-26
> **Ruhe said:**
> As far as I know jython development was freezed for a long time, and was unfrozen only after successfull appearence of jruby.
Today by words of [Charles Oliver Nutter]("blog.headius.com") (jruby core developer) jruby runs as fast as standart MRI(Matz ruby implementation) does.
Ruby community came to decision to use [rubyspecs]("http://rubyspec.org/") - executable specifications for ruby implementations. So jruby should be 100% compatible with MRI ruby (correct me if I'm wrong).
It's really interesting to mix dinamic languages with Java.

Yeah the use of dynamic languages on the JVM is something that I find very interesting.

From what ive read so far it seems that JRuby has excellent support for the core Ruby type functionality, but is somewhat cumbersome when it comes to interfacing with the J2EE type functionality that I am looking for.

Perhaps JRuby is more suited towards the web 2.0 type application?

---

### Post by kknd on 2008-08-26
Our "small ERP" here is developed with C (backend) and Lua (user interface). Very pleasant to work with.

---

### Post by themusicwave on 2008-08-26
I'll be keeping my eye on this thread.  I too am interested in the idea of using Java with a dynamic language.

At my company I am the only software developer who has any kind of formal training or experience(I'm only 23 so I don't have much...).  This causes a lot of issues because the stuff I write is too hard for the others to understand.  I look at some Java or C# code and see a beautiful Object Oriented Pattern that makes everything elegant. They look at it and see dozens of confusing files.

Currently, this has us stuck using really dumbed down technology for most of our applications.  The problem here is this tech tends to be old, expensive and awful for doing anything sophisticated.  It's the old "it's easy to do the easy thing and impossible to do the hard thing on this platform" issue.

Currently, the other devs write VBScript and Indusoft Script(proprietary to the platform we use) and I write C# plugins to do the heavy stuff.  C# can't talk to Indusoft Script or VBScript at all and they can't talk to it.  Right now I have them talk to each other through text files, or the database.  That's really the only way.  Heck the individual scripts really can't interact in this platform.  VBScript and Indusoft Script can be mixed in the same file, but VBScript variables aren't in any way persistent in the platform. In the end we have a mess.

I am trying to move them away from this proprietary, messy expensive system to one that leverages Open Source.  I have suggested Java, but they are afraid of it because of all the OO stuff and none of them being software devs.

If I could do the "hard Stuff" in Java/C# and give them something bolted on top like Python/Ruby that could be the ticket.  They like scripting, they don't like OO or compiling or anything like that.

Heck I could even do some of the "hard stuff" in the dynamic language, I just want to leverage some Java Libraries and such I need.

So hopefully something like Jython is just what I need.  Of course now they just need to listen to me.

---

### Post by pmasiar on 2008-08-26
[http://en.wikipedia.org/wiki/Jython](http://en.wikipedia.org/wiki/Jython)

"Jython programs can seamlessly import and use any Java class. [...]Jython compiles to Java bytecode (intermediate language) either on demand or statically.

Jython also includes jythonc, a compiler that converts Python source code into Java bytecode. This allows Python programmers to write classes which can be fully utilized by a Java program."

So I am not sure, from this seems like integration is seamless both ways - otherwise Jython would be pretty useless, right?

---

### Post by pmasiar on 2008-08-26
> **Quikee said:**
> The problem with JRuby and Jython is that they try to be compatible with Ruby and Python and at the same time want to be integrated well with the JVM which introduces some mismatches and unclean solutions.

Care to provide some links? I know about Jython having problems with some issues not defined deeply enough by C-Python, which were solved by  more documentation. I am not saying you are wrong, but can you show why are you right? :-)

> Groovy on the other hand was written for the JVM and doesn't have such problems and integrates well with Java also.

Jython was written for JVM, like C-Python was written "for" another statically typed language, C. 


> **Ruhe said:**
> As far as I know jython development was freezed for a long time, and was unfrozen only after successfull appearence of jruby.

Not exactly. Jython was **ignored** by Sun for 10 years, and Sun wake up only after MSFT hired key Jython developer and let him create IronPython and adapt .NET CLR for dynamically typed languages. They realized that MSFT new strategy ("C# for libraries, dynamic languages for applications") makes sense, and might significantly weaken Java (on points of productivity). Even then, they were too proud to accept they blown it 10 years ago, and tried to support Ruby (the language competing with Python), instead of Python itself. They proved yet again that they are not software tools company and do not understand how developers think and work.

---

### Post by tinny on 2008-08-26
> **themusicwave said:**
> 
I look at some Java or C# code and see a beautiful Object Oriented Pattern that makes everything elegant. They look at it and see dozens of confusing files.


Even some very experienced people see noise with Java code (and they are probably right). 

> **themusicwave said:**
> 
Currently, this has us stuck using really dumbed down technology for most of our applications.  The problem here is this tech tends to be old, expensive and awful for doing anything sophisticated.  It's the old "it's easy to do the easy thing and impossible to do the hard thing on this platform" issue.

Currently, the other devs write VBScript and Indusoft Script(proprietary to the platform we use) and I write C# plugins to do the heavy stuff.  C# can't talk to Indusoft Script or VBScript at all and they can't talk to it.  Right now I have them talk to each other through text files, or the database.  That's really the only way.  Heck the individual scripts really can't interact in this platform.  VBScript and Indusoft Script can be mixed in the same file, but VBScript variables aren't in any way persistent in the platform. In the end we have a mess.

I am trying to move them away from this proprietary, messy expensive system to one that leverages Open Source.  I have suggested Java, but they are afraid of it because of all the OO stuff and none of them being software devs.

If I could do the "hard Stuff" in Java/C# and give them something bolted on top like Python/Ruby that could be the ticket.  They like scripting, they don't like OO or compiling or anything like that.

Heck I could even do some of the "hard stuff" in the dynamic language, I just want to leverage some Java Libraries and such I need.

So hopefully something like Jython is just what I need.  Of course now they just need to listen to me.

It really sounds like you have your work cut out for you! Good luck :) BTW: From what you have told us it sounds like you are doing the best you can with a bad situation, good on ya!


> **pmasiar said:**
> [http://en.wikipedia.org/wiki/Jython](http://en.wikipedia.org/wiki/Jython)

"Jython programs can seamlessly import and use any Java class. [...]Jython compiles to Java bytecode (intermediate language) either on demand or statically.

Jython also includes jythonc, a compiler that converts Python source code into Java bytecode. This allows Python programmers to write classes which can be fully utilized by a Java program."

So I am not sure, from this seems like integration is seamless both ways - otherwise Jython would be pretty useless, right?

The reverse direction (the other way < ) that we speak of is for things like EJB container dependency injection. (E.g. Automatically injecting a variable with an object, like a persistence manager).

Can you create Entity or Session beans with Jython? 
Can you define Hibernate entity beans in Jython?

From what ive read so far im getting the strong feeling that Groovy has much stronger support in the Java community. It even has its own JSR! [http://jcp.org/en/jsr/detail?id=241](http://jcp.org/en/jsr/detail?id=241)

I just hope that Groovy isnt going to be a bastardised dynamic language that is some sort of Java hybrid.

---

### Post by tinny on 2008-08-26
> **pmasiar said:**
> 
("C# for libraries, dynamic languages for applications")

This is a question I have had in the back of my head.

Is it a good strategy to write library's in a static language (C# / Java) and applications in a dynamic language? Or should you try and use a dynamic everywhere?

---

### Post by CptPicard on 2008-08-26
> **tinny said:**
> 
I just hope that Groovy isnt going to be a **bastardised** dynamic language that is some sort of **Java hybrid**.

:)

You obviously have been bitten...

> **tinny said:**
> 
Is it a good strategy to write library's in a static language (C# / Java) and applications in a dynamic language? Or should you try and use a dynamic everywhere?

I would be prone to assuming this but my suspicions mostly have to do with the fact that most libs in Java etc in particular are more like frameworks where the framework *calls your code* in equal measure as you actually *call into the library code*. As long as your "library" is a nice black box that you can just instantiate objects from and call them from the outside, fine. But what if you need callback objects, extension of library classes, etc...?

---

### Post by tinny on 2008-08-26
> **CptPicard said:**
> :)

You obviously have been bitten...



Yeah, hope it doesn't get infected though...

> **CptPicard said:**
> 
I would be prone to assuming this but my suspicions mostly have to do with the fact that most libs in Java etc in particular are more like frameworks where the framework *calls your code* in equal measure as you actually *call into the library code*. As long as your "library" is a nice black box that you can just instantiate objects from and call them from the outside, fine. But what if you need **callback objects, extension of library classes, etc...?**

Yeah, I think this is a very hard question to answer. Hopefully experience will answer it...

---

### Post by tinny on 2008-08-26
FYI: [http://www.perham.net/mike/log/?p=277](http://www.perham.net/mike/log/?p=277) This article is a little old but still relevant I think...

I thought the last post was interesting.

> 
#  Beaumont Muni says:
December 26th, 2007 at 2:21 pm

mperham

Correction on Groovy … it is not an interpreted language. Groovy compiles down to the byte code so every groovy class is a java class. As a result Groovy is different from Ruby and other interpreted languages in that it gives you the ability to work in both the dynamic (Groovy) environment and still have ability to integrate the static (Java) environment.

You can call Groovy a rip off of Ruby … but so what, I am glad its a rip … more power to the rippers, because without ripping there can never be any improvements. Isn’t that what technology is all about? … You have got to give people what they want. Show me a solutions where I can save time and money and leverage the large amounts of code I have spent years to develop and I will show a framework that companies will gravitate towards. Why re-learn and retool when you can still leverage the vast libraries and resources that Java provides and your learning curve is low. That translates into dollars saved for companies and individuals. understand.


---

### Post by pmasiar on 2008-08-26
> **tinny said:**
> Can you create Entity or Session beans with Jython? 
Can you define Hibernate entity beans in Jython?

You know very well I never used Jython, so I have no way knowing this. But is static language like Java can do it, why not Jython?

You say Groovy is different, it compiles. Well, jython compiles too, see wikipedia.

If you want first-hand info, ask Jython mailing list.

> From what ive read so far im getting the strong feeling that Groovy has much stronger support in the Java community. It even has its own JSR! [http://jcp.org/en/jsr/detail?id=241](http://jcp.org/en/jsr/detail?id=241)

I have strong feeling of NIH syndrome about Jython in Sun - they have hard time to admit that with Jython, Sun could have beaten MSFT in it's own game 10 years ago if only they had clue about programming.

---

### Post by CptPicard on 2008-08-26
> **pmasiar said:**
> But is static language like Java can do it, why not Jython?

IMO you are approaching this as if this were the typical language-flamewar question of whether there's some inherent "language capacity" type issue involved, but there isn't -- tinny (+ me) are just wondering about the purely technical question whether the container is able to pull all the tricks it does behind the scenes with typical Java classes (which often relies on inspecting class properties, including type information, at runtime) with dynamic code.

It's not that it couldn't be theoretically done, but whether it is doable with what we've got now :) Rewriting the entire container for a dynamic language is not the 1st order of business...

---

### Post by pmasiar on 2008-08-26
> **CptPicard said:**
> IMO you are approaching this as if this were the typical language-flamewar question 

Yes I agree, sorry for that.

It alway get my blood boiling when Java proponents are excited about features what Jython had (or was close to have) 10 years ago, but because of Sun's mismanagement, was implemented in C#/.NET platform first. And they contribute to the problem by financing smaller weaker competitors of Jython, thinking that if they ignored Jython 10 years ago, it could not by possibly something worth of support and not supporting it was right thing then and now.

I guess this is how you feel when people are warm and fuzzy about features Lisp had 30 years ago... :-)

> whether the container is able to pull all the tricks it does behind the scenes with typical Java classes (which often relies on inspecting class properties, including type information, at runtime) with dynamic code.

I have no clue what Jython can or cannot, but Python does have this inspection, and ability to modify classes on the run.

---

### Post by tinny on 2008-08-26
> **pmasiar said:**
> Yes I agree, sorry for that.

It alway get my blood boiling when Java proponents are excited about features what Jython had (or was close to have) 10 years ago, but because of Sun's mismanagement, was implemented in C#/.NET platform first. And they contribute to the problem by financing smaller weaker competitors of Jython, thinking that if they ignored Jython 10 years ago, it could not by possibly something worth of support and not supporting it was right thing then and now.

I guess this is how you feel when people are warm and fuzzy about features Lisp had 30 years ago... :-)

> whether the container is able to pull all the tricks it does behind the scenes with typical Java classes (which often relies on inspecting class properties, including type information, at runtime) with dynamic code.

I have no clue what Jython can or cannot, but Python does have this inspection, and ability to modify classes on the run.

I am looking very seriously at Jython. The thing that I like about Jython is the common (I think) skill set you get with the implementation of the Python programming language on the JVM. I love the thought of being able to code a boring website at work with Jython and then when im home hack with pure Python.

I seriously think im going to have to try both!

---

### Post by tinny on 2008-08-26
> **pmasiar said:**
> 
You know very well I never used Jython, so I have no way knowing this. But is static language like Java can do it, why not Jython?



Im not testing you pmasiar. I just thought you might be in a better position than me to find this out. :)

---

### Post by CptPicard on 2008-08-26
> **pmasiar said:**
> 
I have no clue what Jython can or cannot, but Python does have this inspection, and ability to modify classes on the run.

Sure, but the interesting question is what the *J2EE container* can or cannot do, and what it expects to find in the classes it's looking at ;)

> **tinny said:**
> I love the thought of being able to code a boring website at work with Jython and then when im home hack with pure Python.

Well, hacking a boring website at work is best done in TurboGears instead of first shoehorning Jython into a J2EE container and reinventing TurboGears inside that context ;)

---

### Post by tinny on 2008-08-27
> **CptPicard said:**
> 
Sure, but the interesting question is what the *J2EE container* can or cannot do, and what it expects to find in the classes it's looking at ;)


Transaction management. (You know, extended transactions, distributed transactions JTA stuff) Leveraging off different security providers etc... Also the app server does all that data source connection pooling for you. (How do you do connection pooling with something like Python + TG? I don't doubt that it can be done). Is Python + TG development ever done with an application server underneath it?

> **CptPicard said:**
> 
Well, hacking a boring website at work is best done in TurboGears instead of first shoehorning Jython into a J2EE container and reinventing TurboGears inside that context ;)


Yes well.... Thats not the topic here right? :)

Thats the thing I like about Groovy, it doesn't seem to be  shoehorned into the JVM.

---

### Post by CptPicard on 2008-08-27
> **tinny said:**
> Transaction management. ...

Yes yes... the Big Question being whether the J2EE container is going to be able to wire Jython objects for all that stuff as easily as it does it to Java ones, and I suspect it's not as simple.

An interesting aside... our Lisp God lnostdal (who was banned, RIP) is working on a very interesting (I'd say pretty revolutionary actually) Common Lisp web framework, and it gave me the weird idea of maybe creating a servlet that directs requests to a Clojure interpreter that runs in a Tomcat applicationcontext. :) Haven't tried that yet but it would essentially mean Lisp web apps on top of JVM, still with easy callability down to Java libraries... :)

---

### Post by tinny on 2008-08-27
> **CptPicard said:**
> 
An interesting aside... our Lisp God lnostdal (who was banned, RIP) is working on a very interesting (I'd say pretty revolutionary actually) Common Lisp web framework, and it gave me the weird idea of maybe creating a servlet that directs requests to a Clojure interpreter that runs in a Tomcat applicationcontext. :) Haven't tried that yet but it would essentially mean Lisp web apps on top of JVM, still with easy callability down to Java libraries... :)

:shock:

---

### Post by Quikee on 2008-08-27
> **pmasiar said:**
> Care to provide some links? I know about Jython having problems with some issues not defined deeply enough by C-Python, which were solved by  more documentation. I am not saying you are wrong, but can you show why are you right? :-)

I don't know where I read the discussion about this but type mismatches and integration of Java types can be tricky. The other problem is that you have two class libraries, because you have to support everything Python has and you can use everything Java has. 

> **pmasiar said:**
> Jython was written for JVM, like C-Python was written "for" another statically typed language, C.

Let me put it in another words then - Groovy was tailored for the JVM and designed to be a part of Java world (you can use Groovy classes in Java and Java classes in Groovy, you can even write Java code in Groovy - to learn its strong sides stepwise), Jython has to integrate between 2 worlds - Python and Java.

IMHO if you have experience with Python - try Jython. If you have experience with Java - try Groovy.

---

### Post by nvteighen on 2008-08-27
> **CptPicard said:**
> 
An interesting aside... our Lisp God lnostdal (who was banned, RIP) is working on a very interesting (I'd say pretty revolutionary actually) Common Lisp web framework, and it gave me the weird idea of maybe creating a servlet that directs requests to a Clojure interpreter that runs in a Tomcat applicationcontext. :) Haven't tried that yet but it would essentially mean Lisp web apps on top of JVM, still with easy callability down to Java libraries... :)

And then people argue Lisp is not for "real" work...

@tinny: Check out lnostdal's website: [http://nostdal.org/](http://nostdal.org/)

---

### Post by Ruhe on 2008-08-27
For shure, dynamic languages running on top of jvm, are superawesome!
No need to use ejb or hibernate. Why would I use them if I had [ActiveRecord]("http://wiki.jruby.org/wiki/Running_Rails_with_ActiveRecord-JDBC") (ORM from rubyonrails framework) running in jvm? 

JRuby compiles Ruby code to Java bytecode. Once complete, there's no interpretation done, except for eval calls. evaluated code never gets compiled; however, if the eval defines a method that's called enough, it will also eventually get JIT compiled to bytecode. JRuby is a mixed-mode engine.
So it's not just another ruby interpreter and not just another toy.
It's a great tool which may improve our development. And the main problem in the way jruby and other dynamic languages, I think the reluctance of many developers to use new tools, they still build spacecrafts with java.

You can find some success-stories about using rubyonrails with jruby. 
So, I believe it's the future of the enterprise programming world.

---

### Post by CptPicard on 2008-08-27
> **Ruhe said:**
> 
No need to use ejb or hibernate. Why would I use them if I had [ActiveRecord]("http://wiki.jruby.org/wiki/Running_Rails_with_ActiveRecord-JDBC") (ORM from rubyonrails framework) running in jvm? 

Err... for clustering, distributed transactions and for much more flexible data mapping, plus all the rest. ActiveRecord is trivial and very lightweight compared to Hibernate and EJB.

---

### Post by tinny on 2008-08-27
> **Ruhe said:**
> For shure, dynamic languages running on top of jvm, are superawesome!
No need to use ejb or hibernate. Why would I use them if I had [ActiveRecord]("http://wiki.jruby.org/wiki/Running_Rails_with_ActiveRecord-JDBC") (ORM from rubyonrails framework) running in jvm? 

JRuby compiles Ruby code to Java bytecode. Once complete, there's no interpretation done, except for eval calls. evaluated code never gets compiled; however, if the eval defines a method that's called enough, it will also eventually get JIT compiled to bytecode. JRuby is a mixed-mode engine.
So it's not just another ruby interpreter and not just another toy.
It's a great tool which may improve our development. And the main problem in the way jruby and other dynamic languages, I think the reluctance of many developers to use new tools, they still build spacecrafts with java.

You can find some success-stories about using rubyonrails with jruby. 
So, I believe it's the future of the enterprise programming world.

Unfortunately enterprise software development is very rarely about developing completely new systems. More often than not you are leveraging off existing functionality and infrastructure. This is where I think Groovy has the advantage. You cant go into a legacy system and just push ActiveRecord. You need to show a clear path that proves you can hook into and extend the existing standards that have been put in place (JPA etc...).

In this case I dont believe its about finding the best dynamic language / web framework. Its about finding the best solution to a very specific domain of problem (stated in the OP).

My understanding is that JRuby + Rails is very specifically tuned to small / mid sized web persistence applications at are largely independent of other systems. (this is a basic summary of what ive read). And yes JRuby + Rails is GREAT!

The other thing that Groovy has going for it is politics. As all experienced software developers know, politics more often than not will get in the way of the technically optimal solution. Groovy's JSR is a massive plus. Next time im in an architecture meeting I can just say “We should use [JSR241]("http://jcp.org/en/jsr/detail?id=241")” and my changes of gaining traction just tripled! Im not saying this is right, but it is reality. :(

---

### Post by pmasiar on 2008-08-27
> **CptPicard said:**
> Err... for clustering, distributed transactions

I remember the awe when I first read about [http://en.wikipedia.org/wiki/Two-phase_commit](http://en.wikipedia.org/wiki/Two-phase_commit) and the brains of the people who make stuff like this happen, and work transparently.

And then people who do not have even clue what it is, not even how hard it is to make it work transparently, will come and compare it to trivial stuff, like ActiveRecord ORM. 

Yes, this is hard stuff and most likely your app does not need it - but Enterprise apps do need it, and then you need it badly.

I have nothing but awe for people who can make enterprise apps work -- and nothing but laugh for people who use enterprise-level solutions for small little apps :-)

---

### Post by pmasiar on 2008-08-27
> **tinny said:**
> The other thing that Groovy has going for it is politics. As all experienced software developers know, politics more often than not will get in the way of the technically optimal solution. Groovy's JSR is a massive plus. 

Yes, but this is based on (IMHO wrong) understanding of the niche where natural selection is happening: Groovy, Jython and JRuby do not compete against each other: real competitor is .NET + silverlight with DRL running C#/IronPython. And Sun ignores that. So far every MSFT competitor who missed that was extinguished.

---

### Post by tinny on 2008-08-27
> **pmasiar said:**
>  -- and nothing but laugh for people who use enterprise-level solutions for small little apps :-)

I am working on a 10 page application now, it uses the IBM J2EE stack (not my choice). The application has over 2000 classes :( This application is a prime candidate for something like JRuby + Rails. But I have no choice

Please dont laugh at me :(

You are write pmasiar :)

---

### Post by skeeterbug on 2008-08-27
> **tinny said:**
> I am working on a 10 page application now, it uses the IBM J2EE stack (not my choice). The application has over 2000 classes :( This application is a prime candidate for something like JRuby + Rails. But I have no choice

Please dont laugh at me :(

You are write pmasiar :)

I feel your pain. Our two ASP.NET applications contain 39,136 files, and 640MB in size. This includes all css, javascripts, images, etc. The business logic alone is > 750klines of code and well over 100 files.

---

### Post by tinny on 2008-08-27
> **skeeterbug said:**
> I feel your pain. Our two ASP.NET applications contain 39,136 files, and 640MB in size. This includes all css, javascripts, images, etc. The business logic alone is > 750klines of code and well over 100 files.

A large code base can be necessary if your solving a large problem.
 
This current application im working on has about 1500 classes worth of scaffolding code!

The other day I had to add one hyperlink to a sort of header navigation menu, I had to modify five source / xml files to get it done. Crazy!

---

### Post by pmasiar on 2008-08-27
> **tinny said:**
> The application has over 2000 classes 
Please dont laugh at me :(

I don't laugh at you, I weep with you - I am in similar situation with my current app at my day job.

Seems like Java attracts this kind of overkill apps like a magnet :-(

Years ago, we struggled with spaghetti code (full of GOTO). We are bit wiser now, because we use more sophisticated pasta. 2000 classes looks like a "ravioli code" many small little objects with different stuffing, and you need to bite to find out what is inside :-)

---

### Post by LaRoza on 2008-08-27
> **pmasiar said:**
> I don't laugh at you, I weep with you - I am in similar situation with my current app at my day job.

Seems like Java attracts this kind of overkill apps like a magnet :-(


That is called "job security". Make it arcane so only you can understand it. When you retire, it is what is called "their problem".

---

### Post by tinny on 2008-08-27
> **LaRoza said:**
> That is called "job security". Make it arcane so only you can understand it. When you retire, it is what is called "their problem".

:lolflag: Totally!!!

If I ever meet /* @author XXXX XXXXX */ ill kill them!

---

### Post by nvteighen on 2008-08-28
> **pmasiar said:**
> 
Years ago, we struggled with spaghetti code (full of GOTO). We are bit wiser now, because we use more sophisticated pasta. 2000 classes looks like a "ravioli code" many small little objects with different stuffing, and you need to bite to find out what is inside :-)

And if your classes become to big, maybe are they ["Panzerotti"]("http://en.wikipedia.org/wiki/Panzerotti)?

---

### Post by Ruhe on 2008-08-28
> **pmasiar said:**
> I remember the awe when I first read about [http://en.wikipedia.org/wiki/Two-phase_commit](http://en.wikipedia.org/wiki/Two-phase_commit) and the brains of the people who make stuff like this happen, and work transparently.

And then people who do not have even clue what it is, not even how hard it is to make it work transparently, will come and compare it to trivial stuff, like ActiveRecord ORM. 

Yes, this is hard stuff and most likely your app does not need it - but Enterprise apps do need it, and then you need it badly.

I have nothing but awe for people who can make enterprise apps work -- and nothing but laugh for people who use enterprise-level solutions for small little apps :-)

I've used both ejb2 and ejb3, used them with jboss clusters.
I understand pretty good that today we cannot develop enterprise apps without 
such tools like ejb, jpa, and lots of others.

But all this could be implemented with some dynamic language compiled for jvm.
ejb3 uses lots of reflections, for example, if I'll call InitialContext for a remote bean,
I'll receive just a stub (proxy object), not bean itself.
This could be done much easier with dynamic language.

Maybe I miss something, but ActiveRecord does the same what JPA does, but in much more 
elegant way? 

And of coz' rails isn't supposed for usage in enterprise world, it has own niche.

---

### Post by tinny on 2008-08-28
> **Ruhe said:**
> I've used both ejb2 and ejb3, used them with jboss clusters.
I understand pretty good that today we cannot develop enterprise apps without 
such tools like ejb, jpa, and lots of others.

But all this could be implemented with some dynamic language compiled for jvm.
ejb3 uses lots of reflections, for example, if I'll call InitialContext for a remote bean,
I'll receive just a stub (proxy object), not bean itself.
This could be done much easier with dynamic language.

Maybe I miss something, but ActiveRecord does the same what JPA does, but in much more 
elegant way? 

And of coz' rails isn't supposed for usage in enterprise world, it has own niche.

Ref: OP

We are talking about leveraging off existing standards in the enterprise world. ActiveRecord is not an option even if it has JPA type functionality. (I dont think it does)

J2EE's strength is the software infrastructure that you get with it (JPA, JMS, JTA etc...). We are not talking about Dynamic languages being better than static ones (this thread will become unproductive as soon as we engage in the Dynamic vs Static thing). We are talking about using dynamic languages to leverage the power of standard enterprise software infrastructure. I think we all agree that using dynamic languages on top of this software infrastructure has massive potential. Now hopefully together we can find the best Dynamic language candidate to achieve this.

So far my vote is with Groovy :)

---

### Post by Ruhe on 2008-08-29
> **tinny said:**
> Ref: OP

We are talking about leveraging off existing standards in the enterprise world. ActiveRecord is not an option even if it has JPA type functionality. (I dont think it does)

J2EE's strength is the software infrastructure that you get with it (JPA, JMS, JTA etc...). We are not talking about Dynamic languages being better than static ones (this thread will become unproductive as soon as we engage in the Dynamic vs Static thing). We are talking about using dynamic languages to leverage the power of standard enterprise software infrastructure. I think we all agree that using dynamic languages on top of this software infrastructure has massive potential. Now hopefully together we can find the best Dynamic language candidate to achieve this.

So far my vote is with Groovy :)

Here is intersting reading on this theme from one the greatest computers scientists:
[http://www.martinfowler.com/bliki/GroovyOrJRuby.html](http://www.martinfowler.com/bliki/GroovyOrJRuby.html)

---

### Post by tinny on 2008-08-30
Performance

When does the performance penalty of dynamic languages on the JVM matter? I guess when the performance of a function matters you should implement it in Java code, right? (its nice to have this choice)

Apparently Groovy in particular is very slow (But improvements are coming in 1.6).
[http://www.codecommit.com/blog/java/groovys-performance-is-not-subjective](http://www.codecommit.com/blog/java/groovys-performance-is-not-subjective) (the comments below this blog entry are interesting)

Are there any generic approaches to tuning dynamically typed code? Are there any applications where a dynamic language should not be used in enterprise development? (E.g. A high load public facing web site? Maybe internet banking....etc)

---

### Post by pmasiar on 2008-08-30
> **tinny said:**
> Are there any generic approaches to tuning dynamically typed code?
smart cache: use RAM to gain speed

> Are there any applications where a dynamic language should not be used in enterprise development? (E.g. A high load public facing web site? Maybe internet banking....etc)

DB-backed website will be **always** limited by I/O, regardless of language used - so you may as well use the most productive one. If you want to spend time/money on C hackers, focus on database layer, not the app.

---

### Post by tinny on 2008-08-31
> **pmasiar said:**
> smart cache: use RAM to gain speed


Ive never used Smart Cache before. Is this [Smart Cache]("http://scache.sourceforge.net/") the proxy server software? This is not Python specific, right? A standard sort of tool...

One thing I usually do is serve static (images etc...) content from a server that is independent from the app server running my application logic. Also I usually use Apache and mod_jk for static html content, java script etc. Just another tuning tip...

> **pmasiar said:**
> 
DB-backed website will be **always** limited by I/O, regardless of language used - so you may as well use the most productive one. If you want to spend time/money on C hackers, focus on database layer, not the app.

Yep! What about web service perfomance in dynamic languages (sometimes in my applications I need to call several web services per single http request, as you probably know there is lots of integration work in J2EE applications).

Having said all this I do agree that this dynamic language performance penalty isn't a big deal. :guitar:

---

### Post by pmasiar on 2008-08-31
> **tinny said:**
> Ive never used Smart Cache before. 

Neither did I :-)

I used 'cache' as generic term, not as particular product: just suggesting to use it in a smart way.

---

### Post by tinny on 2008-11-16
UPDATE:

So time for an update on my experiences on this topic...

Because time nowadays is so limited for me I decided to explore just one of the above mentioned languages / frameworks. I decided to explore the Groovy + Grails framework.

First off ive found Groovy to be excellent, the more I use it the more it feels like what Java should be. Its been a surprisingly easy migration to Groovy for me, I guess this is because about 90% of Java syntax is valid Groovy syntax and Groovy leverage's off the Java standard class library.

Grials, grails has been a godsend for me! Grails makes both the MVC and convention over configuration approaches feel so natural (no XML!!!). GORM has been good, very easy to use mostly due to the dynamic methods generation you get from defining a Grails model (save, delete etc...). I do have one annoyance with Grails however, GSP. GSP is basically a small evolution of JSP and for me it just feels like the same old Java templating mess! It just feels a little stale.

So I started exploring what different options where available for an alternative view technology to use on Grails. First I had a look at GWT (Google Web Toolkit [http://grails.org/GWT+Plugin](http://grails.org/GWT+Plugin)) and I liked it. It looked very nice and allowed me to develop my interfaces in just plain application code, however I did have to write a lot of Java / Groovy code to get an application going...

Next, Flex on Grails! Man I think im in love ([http://grails.org/Flex+Plugin](http://grails.org/Flex+Plugin)). It is just so easy to produce attractive user interfaces using flex, plus Flex builder has a very good visual designer that actually produces good GUI code (mxml).

So here is the current generic web architecture im excited about.

[LIST]
[*]View technology: Flex 3 with Actionscript (based on ECMAScript) providing the backing code and model.
[/LIST]
[LIST]
[*]Service layer: Generic grails services exposed by BlazeDS.
[/LIST]
[LIST]
[*]Persistance: GORM
[/LIST]
[LIST]
[*]Database: MySQL
[/LIST]

So who thinks im crazy...?

---

### Post by CptPicard on 2008-11-16
Sounds good... but I would be a bit suspicious in doing my UIs in Flash.. (isn't Flex Flash?)

---

### Post by tinny on 2008-11-16
> **CptPicard said:**
> Sounds good... but I would be a bit suspicious in doing my UIs in Flash.. (isn't Flex Flash?)

Yeah I know what you mean. Flex does have a dependency on the flash runtime, but that's it. Once you start using flex it really doesnt feel like the Flash animation type tool your probably thinking of.

Adobe Flash has now become a proper rich client platform.

---

### Post by pmasiar on 2008-11-17
Bruce Eckel also votes for Flash: he says that Flash is the rich client Java once promised to be, but never really was.

---

### Post by tinny on 2008-11-17
> **pmasiar said:**
> Bruce Eckel also votes for Flash: he says that Flash is the rich client Java once promised to be, but never really was.

Yeah it really is a beautiful product. I also want to use it to put nice faces to my ugly J2EE apps (via BlazeDS).

Adobes development tools are good too. Flex Builder just works. You do have to play a few hundred bucks to get a copy, but I dont mind. I think they definitely deserve to make money from this product.

---

### Post by tinny on 2008-11-25
> **tinny said:**
> 
Next, Flex on Grails! Man I think im in love ([http://grails.org/Flex+Plugin](http://grails.org/Flex+Plugin)). It is just so easy to produce attractive user interfaces using flex, plus Flex builder has a very good visual designer that actually produces good GUI code (mxml).

So here is the current generic web architecture im excited about.

[LIST]
[*]View technology: Flex 3 with Actionscript (based on ECMAScript) providing the backing code and model.
[/LIST]
[LIST]
[*]Service layer: Generic grails services exposed by BlazeDS.
[/LIST]
[LIST]
[*]Persistance: GORM
[/LIST]
[LIST]
[*]Database: MySQL
[/LIST]

So who thinks im crazy...?

Problem :-(

So in theory the above technology match up sounds great, but in practice I have run into a show stopping issue. The problem is that the Grails Flex plugin does not auto generate Actionscript client side classes ([http://jira.codehaus.org/browse/GRAILSPLUGINS-225](http://jira.codehaus.org/browse/GRAILSPLUGINS-225)) (The client side classes that are used to interact with the exposed BlazeDS services), you have to code these classes by hand making sure that you correctly match up the class properties etc... For me this extra manual work nullifies one of the core reasons for using Grails in the first place, that is to be more productive!!!

Im still really keen on Flex and Grails and am going to persevere. The approach I now plan on taking is to expose Grails services as SOAP services ([http://www.grails.org/XFire+plugin](http://www.grails.org/XFire+plugin)) and then consume these services in Flex (Actionscript SOAP clients). The reason I have chosen SOAP is because its super easy and I have quite a lot of experience with it (Get something developed as fast as possible, optimise later).

So what do you think? Am I introducing too large a bottle neck into my system by creating an rich client that will frequently be making SOAP service calls (Remember every distributed client will be making these SOAP calls). Personally ive only ever used SOAP to intergrate back end systems.

---

### Post by Geekkit on 2008-11-25
> **tinny said:**
> For me its time to take the next step (looking to use a dynamic language for my professional development). 

Here are the contenders as I see it:

JRuby, Groovy and Jython 


I am puzzled by this statement as it almost implies that Java is not a dynamic language. I guess though your definition of a dynamic programming language and my definition of a dynamic programming language differ. Perhaps you were thinking of dynamic typed? Although that too would include Java in my books.


> **tinny said:**
> I am interested in a language that has good hooks into Java classes and J2EE container managed functionality so that I can leverage off the scalable APIs that J2EE offers (The various enterprise bean technologies etc...). I am also looking for a language with a very good ORM implementation (similar or better than the Hibernate annotations approach).

So, you're looking for a language that has:

- hooks or Java class functionality
- JEE container managed functionality
- bean technologies
- ORM support
- annotations

You want a bunch of features of JEE but you don't want to use JEE? That's rather silly.

If you want ease of use, remoting, annotations, business process management, ORM, and a whole whack of other features, look into JBoss Seam, Hibernate, Rich Faces, Exadel Flamingo (OSS alternative to Adobe Flex), and Granite Data Services (OSS alternative to Adobe LiveCycle (Flex&#8482; 2+) Data Services), and simply admit you want to use Java, that's okay.

---

### Post by tinny on 2008-11-25
> **Geekkit said:**
> I am puzzled by this statement as it almost implies that Java is not a dynamic language. I guess though your definition of a dynamic programming language and my definition of a dynamic programming language differ. Perhaps you were thinking of dynamic typed? Although that too would include Java in my books.


Dynamically typed.

> **Geekkit said:**
> 
You want a bunch of features of JEE but you don't want to use JEE? That's rather silly.


Initially this may seem to be the case (silly, this is what I once thought). But after having tried a couple of Dynamically typed languages (Python and Groovy) I fell in love. Its the small incremental productivity gains that I really enjoy about dynamically typed languages over Java (Ive coded in Java for about 9 years). You are quite right in implying that if you just go with JEE you will be fine. But for me fine isnt good enough any more. Aside from the above mentioned productivity improvements that ive found myself gaining there is another aspect of the domain of dynamically typed languages that I like, this is the culture of simplicity that seems to surround dynamically typed languages. There is nothing that frustrates me more than the huge complexity that most (well all that ive seen) JEE solutions employ into their design / architecture. Over use of design patterns, mountains of configuration, abstractions of trivial system entities, heavy weight "soft" infrastructure (application servers, enterprise service buses) etc etc...

Dynamically typed languages like Groovy and Python really do seem to have a culture of simplicity that surrounds them. E.g. Grails is the Web framework for Groovy. Grails is so much simpler to use than the other web frameworks that ive used (String MVC, Struts and yes I have used JBoss Seam).

Im tired of fighting the complexities of Java and its associated frameworks to get even the most trivial of applications developed. I just want to get the job done and after a couple of months playing with Grails I can say that I am getting a lot more done while still remaining sane and not confusing myself into a stupor.

> **Geekkit said:**
> 
simply admit you want to use Java, that's okay.


Honesty, I really would prefer not to.

EDIT: BTW yes JBoss Seam is a step in the right direction. I like how the framework leverages off EJB 3.0

---

### Post by pmasiar on 2008-11-25
> **Geekkit said:**
> Perhaps you were thinking of dynamic typed? Although that too would include Java in my books.

Just curious, what is your definition of "dynamically typed" (aka "late binding") language  that it includes Java? And which other languages are also included, and which fail?

---

### Post by CptPicard on 2008-11-25
> **Geekkit said:**
> Perhaps you were thinking of dynamic typed? Although that too would include Java in my books.

You have some weird definitions there, then. I guess if you really want to stretch, you could argue that because you can code in Java by keeping everything as Object and resolving type at runtime by instanceof, Java can be used as dynamically typed. But that's just nonsense -- nobody does that and the very idea of having the compiler in Java is that it does type-checking for you at compile time, which is the philosophical argument for the whole thing in the first place.

And as far as "[dynamic]("http://en.wikipedia.org/wiki/Dynamic_programming_language")" languages go.. Java's code is very static at runtime. From that Wikipedia list, Java does only reflection.

> 
- hooks or Java class functionality

Lots of useful Java stuff out there that could be used

> 
- JEE container managed functionality

It's a strong platform. Why not?

> 
- bean technologies

The whole bean naming convention is an attempt to bring some sort of duck-typingness to the language btw.

> 
- ORM support

Where are you going to keep your data?

> 
- annotations

XML sucks...

Interestingly, a lot of the stuff is found in Python too, excluding existing Java code and strong container.

> You want a bunch of features of JEE but you don't want to use JEE? That's rather silly.

If you want to build an Enterprise app, JEE is a very strong platform for that, but it doesn't mean you actually like to use Java as the development language on it, especially because of static typing and the culture of "doing everything twice", first in code and then in configuration. The two are not that tightly bound together. Tinny's project sounds perfectly reasonable to me.


> and simply admit you want to use Java, that's okay.

Simply admit this was bs, it's ok ;)

---

### Post by tinny on 2008-12-15
FYI: Grails and Groovy just became slightly easier to sell to the ignorant business folk.

SpringSource has acquired G2One.

Blog post from MR Spring
[http://blog.springsource.com/2008/11/11/more-weapons-for-the-war-on-complexity-springsource-acquires-groovygrails-leader/](http://blog.springsource.com/2008/11/11/more-weapons-for-the-war-on-complexity-springsource-acquires-groovygrails-leader/)

---

