---
title: "Why to love/hate C#"
date: 2008-08-21
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-08-21
> **pmasiar said:**
> 

You may consider starting "Why I love/hate C#" 

at pmasiar's request because there is so much arguement about C# in another thread

---

### Post by LaRoza on 2008-08-21
Well, you have to give a reason for loving it! That is the point of the thread ;)

---

### Post by slavik on 2008-08-21
it is made by Microsoft, meaning there will be a job that will need it ...

---

### Post by skeeterbug on 2008-08-21
> **slavik said:**
> it is made by Microsoft, meaning there will be a job that will need it ...

Money is good huh? After all, I don't live in my parents' basement. :)

---

### Post by jimi_hendrix on 2008-08-21
i like it for its easy form development and it has a clear syntax

---

### Post by LaRoza on 2008-08-21
> **jimi_hendrix said:**
> i like it for its easy form development and it has a clear syntax

Its syntax is a basic C style syntax, and isn't seen as clear except by those who originally learned such a syntax. So everyone else, it is an ugly syntax that is needless verbose (all those {} and ;)

C# was made (originally) by Microsoft to compete with Java because Microsoft lost a lawsuit to Sun when they tried to not follow the Java standards (Microsoft can't follow standards without trying to take it over or introduce non standard elements, if you don't believe me, IE has been behind in web standards while Microsoft has introduced IE only technologies, the MS XML based document format used by Office 2007 is not the same format they had standardised, and a perfectly function XML based format exists already (ODF))

C# has some features that Java doesn't have, as it was made after and learned from the past. 

For cross platform development, Java is Java and is almost fully open source. C# is "cross platform", but is standard libraries in Microsoft implementation (the original) is different from the standard that is open. For anything other than Windows development, C# is behind in use for Java, Python, Perl, Ruby, C++, C, and many others and brings nothing essentially new, although open source projects do use it a bit.

(This is the "hate" part, although I don't hate it)

---

### Post by pmasiar on 2008-08-21
> **jimi_hendrix said:**
> at pmasiar's request because there is so much arguement about C# in another thread

Just to make it clear, I completely ignore C# and have no use for it, discussion was about comparing features of Python (which is my preferred language) to C#, and was off-topic in that thread.

IMHO C# is proprietary extension of Java (with some features done better than Java) running on proprietary platform .NET (yes I know about mono, but it seems to be always trying to catch up, and never does, and it's patent status is unclear). 

Even if MSFT has this interesting idea to have dynamic language (IronPython Ruby) for top layer and static language (C#) for libraries running on same virtual engine (idea developed with Jython on JVM decade ago), my problem with C# is not language itself (which is close enought to java to be boring) but .NET library.

I cannot see myself to dedicate couple years of my life to become expert in .NET, knowing well that I, my apps and my knowledge will be shackled to MSFT upgrade treadmill. I can grudgingly accept Java, since it is GPL now, but "just say no to .NET".

I know that IronPython and C# works perfectly for some, and good for them. It does not work for me for reasons stated.

I'll let you know when I will be looking for a job and will be so desperate I'll accept even C# :-)

---

### Post by wil on 2008-08-21
The main weakness to me is the boxing/unboxing issues, which negatively impacts performance.

If it could do pointers this would not be an issue. (Yes I know about "by ref")

It looks beautiful and elegant.
It is an improvement on C/C++ because it makes it more difficult to write spaghetti code. (an advantage for a beginner)

OT: In my opinion C or a subset of C++ is still the best but requires more skill to design the initial framework.

Edit: The other thing I really hate is the Garbage Collection. If programs have to run for months at a time memory becomes a problem. To prevent this objects have to then be manually be cleared and garbage collection called, the rules are not simple.

---

### Post by tinny on 2008-08-21
If you want to do C# development properly be prepared to put your hand in your pocket.

Use C# spend lots of money!

Visual Studio $$$
Team Foundation Server $$$
Windows Server $$$
SQL Server $$$

This is one of the reasons for me that developing in C# is a different proposition to Java.

In Java I can do all of the above (better) with out spending any money.

---

### Post by tinny on 2008-08-21
> **wil said:**
> The main weakness to me is the boxing/unboxing issues, which negatively impacts performance.

Edit: The other thing I really hate is the Garbage Collection. If programs have to run for months at a time memory becomes a problem. To prevent this objects have to then be manually be cleared and garbage collection called, the rules are not simple.

Your a C guy right? :)

Garbage Collection just works, or are you saying there is a bug in the.Net runtime.

The rules of Garbage Collection are simple. If an object has no reference associated with it it will be Garbage Collected (can be a little more complicated when using static, but its still quite simple). With High level programming languages you really do have to trust the the runtime.

However you do sometimes have to be careful with collections.
[http://www.ibm.com/developerworks/java/library/j-jtp11225/index.html](http://www.ibm.com/developerworks/java/library/j-jtp11225/index.html)

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> If you want to do C# development properly be prepared to put your hand in your pocket.

Use C# spend lots of money!

Visual Studio $$$
Team Foundation Server $$$
Windows Server $$$
SQL Server $$$

This is one of the reasons for me that developing in C# is a different proposition to Java.

In Java I can do all of the above (better) with out spending any money.

Visual Studio is worth it (my boss knows someone at MS, we get it for 90 bucks anyways. My last employer purchased two licenses when I requested it, no questions asked).

Team Foundation Server, and SQL Server are optional. SQL server is still less expensive than Oracle, and we use SVN and trac instead of foundation server. You can go without a windows server if you want (there are express editions for free of SQL server, and an embedded web development server for ASP.NET in Visual Studio).

The tools are pretty cheap considering the profit we are getting from selling the software. Express editions are available for students and hobbiests, though I have no experience with the express editions, with the exception of SQL server express.

The ORM tool we use is around $150 USD, and has *fantastic* support (Also supports multi DB's, Oracle, MySQL, Postgres). In fact, MySpace uses it. LLBLGen Pro is the name of it.

I could see a small start-up going with Java or a LAMP stack though. It makes sense in a lot of cases where starting capital is severely limited. I see the value in the tools I use though, and we are willing to pay for them.

---

### Post by tinny on 2008-08-21
> 
Visual Studio is worth it 


It is worth the money I guess, but its the only viable choice of IDE for professional C# development. With Java development we have at least three. NetBeans, Eclipse and Intellij (two are free).

> You can go without a windows server if you want

I thought that IIS was limited in the number of sessions (10 from memory) it could accepted when not using a server edition of windows...?

---

### Post by LaRoza on 2008-08-21
> **skeeterbug said:**
> Visual Studio is worth it (my boss knows someone at MS, we get it for 90 bucks anyways. My last employer purchased two licenses when I requested it, no questions asked).

Team Foundation Server, and SQL Server are optional. SQL server is still less expensive than Oracle, and we use SVN and trac instead of foundation server. You can go without a windows server if you want (there are express editions for free of SQL server, and an embedded web development server for ASP.NET in Visual Studio).

The ORM tool we use is around $150 USD, and has *fantastic* support (Also supports multi DB's, Oracle, MySQL, Postgres). In fact, MySpace uses it. LLBLGen Pro is the name of it.


Glad things work for you, but remember his is a Linux forum ;)

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> It is worth the money I guess, but its the only viable choice of IDE for professional C# development. With Java development we have at least three. NetBeans, Eclipse and Intellij (two are free).



I thought that IIS was limited in the number of sessions (10 from memory) it could accepted when not using a server edition of windows...?

Sharpdevelop is very good (I haven't tried monodevelop in a long time). I think there was an eclipse based C# editor out there as well. I wouldn't downgrade from the best though. :)

For development, Visual Studio includes an embedded web server to debug your ASP.NET applications. I think IIS on XP is limited in concurrent session though I have never used it.

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> Glad things work for you, but remember his is a Linux forum ;)

Read the thread title.

---

### Post by tinny on 2008-08-21
> **LaRoza said:**
> Glad things work for you, but remember his is a Linux forum ;)

skeeterbug does have a good point. It doesnt take as long to get setup with C# VS etc.. as it does with say Java, Eclipse and an app server etc...

M$ rave about this, "Total cost of ownership".

(I was a C# dev for 1yr)

So this extra tool set cost is somewhat negated by the time saved (time is money).

The other thing I dont like about C# is that it is quite poorly represented in the open source world (at least for supported open source, E.g. Java has the apache foundation and others).

---

### Post by tinny on 2008-08-21
> **skeeterbug said:**
> Sharpdevelop is very good


From what ive seen it does look good, but I cant see it being used that commonly in a professional organization, IMO.

> **skeeterbug said:**
> 
For development, Visual Studio includes an embedded web server to debug your ASP.NET applications.

We have will this and more in the Java world ;)

---

### Post by LaRoza on 2008-08-21
> **tinny said:**
> skeeterbug does have a good point. It doesnt take as long to get setup with C# VS etc.. as it does with say Java, Eclipse and an app server etc...

M$ rave about this, "Total cost of ownership".

(I was a C# dev for 1yr)

So this extra tool set cost is somewhat negated by the time saved (time is money).

MS says that because they get the money ;)

Like I said, I have nothing against the tools themselves.

> 
The other thing I dont like about C# is that it is quite poorly represented in the open source world (at least for supported open source, E.g. Java has the apache foundation and others).
It is a recent member, so it is behind in numbers. It has to have some killer features to catch up (and I don't think it will)

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> From what ive seen it does look good, but I cant see it being used that commonly in a professional organization, IMO.
That is because in the professional organization you go for Visual Studio, hands down. :)

> 
We have will this and more in the Java world ;)

Double edged sword. Think of it as Python's one way of doing it vs Perl's many ways of doing it. You also have to consider why nobody bothers making and IDE for C#. Maybe it is because VS meets the demand?

---

### Post by tinny on 2008-08-21
> **LaRoza said:**
> MS says that because they get the money ;)

Like I said, I have nothing against the tools themselves.


LaRoza, total cost of ownership is a valid thing to **consider**. The problem is it usually is a very hard thing to prove until its too late.

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> skeeterbug does have a good point. It doesnt take as long to get setup with C# VS etc.. as it does with say Java, Eclipse and an app server etc...

M$ rave about this, "Total cost of ownership".

(I was a C# dev for 1yr)

So this extra tool set cost is somewhat negated by the time saved (time is money).
I have a buddy that went with a MSDN subscription and Windows Small Business server. He runs a mom and pop shop (literally). He couldn't be more happy with his setup. I tried getting him to do some Python with me on side projects, but it is a no go.

> 
The other thing I dont like about C# is that it is quite poorly represented in the open source world (at least for supported open source, E.g. Java has the apache foundation and others).

Have you checked out [http://codeplex.com/?](http://codeplex.com/?) Google code also has C# libraries (here is mine: [http://code.google.com/p/payment-processor/](http://code.google.com/p/payment-processor/)). I understand where you are coming from though.

---

### Post by LaRoza on 2008-08-21
> **tinny said:**
> LaRoza, total cost of ownership is a valid thing to **consider**. The problem is it usually is a very hard thing to prove until its too late.
Well, my languages of choice are C and Python. My editor is Vim and sometimes Gedit and I use the gcc compiler. Although RAD tools for Linux are not really VS level, they are pretty good, and for other kinds of development, I don't see the developer community suffering.

---

### Post by tinny on 2008-08-21
> **LaRoza said:**
> Well, my languages of choice are C and Python. My editor is Vim and sometimes Gedit and I use the gcc compiler. Although RAD tools for Linux are not really VS level, they are pretty good, and for other kinds of development, I don't see the developer community suffering.

LaRoza, your focus is the open source world right? If so then "total cost of ownership" is a mute point :)

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> LaRoza, total cost of ownership is a valid thing to **consider**. The problem is it usually is a very hard thing to prove until its too late.

I agree completely. With my deployed applications, I can turn on tracing for real time feedback, I can look at performance monitors and see how many cache hits, sessions, pageviews/sec, etc are happening in my ASP.NET applications, per application pool. I can turn on the performance monitors for SQL server, and check requests, locks, etc there as well. It isn't a free solution, but it is invaluable to have these great features available to me.

---

### Post by LaRoza on 2008-08-21
> **tinny said:**
> LaRoza, your focus is the open source world right? If so then "total cost of ownership" is a mute point :)

"moot", and yes :-)

---

### Post by tinny on 2008-08-21
> **skeeterbug said:**
> I agree completely. With my deployed applications, I can turn on tracing for real time feedback, I can look at performance monitors and see how many cache hits, sessions, pageviews/sec, etc are happening in my ASP.NET applications, per application pool. I can turn on the performance monitors for SQL server, and check requests, locks, etc there as well. It isn't a free solution, but it is invaluable to have these great features available to me.

We have all this in the Java world ;)

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> We have all this in the Java world ;)

They build performance monitors around everything?

I have netbeans installed at home. I honestly don't know where to start. EJB documentation is massive and there are so many options. Where did you start if you were originally C#?

---

### Post by tinny on 2008-08-21
> **skeeterbug said:**
> They build performance monitors around everything?

I have netbeans installed at home. I honestly don't know where to start. EJB documentation is massive and there are so many options. Where did you start if you were originally C#?

I wasn't originally C#.

I was Java > C# > Java.

If your a C# guy you will probably want to take an IDE type approach to learning J2EE (and there is nothing wrong with this approach).

NetBeans.org has some great learning trails. Id recommend these...
[http://www.netbeans.org/kb/trails/web.html](http://www.netbeans.org/kb/trails/web.html)
[http://www.netbeans.org/kb/trails/java-ee.html](http://www.netbeans.org/kb/trails/java-ee.html)

Also have a look at this
[http://www.javapassion.com/](http://www.javapassion.com/) (Free Java training)

---

### Post by jcwmoore on 2008-08-21
I like object and collection initializers, not that they are impressive, just some hand wavy compiler tricks.  I Love LINQ, i don't know if that exists in a non .NET language, but that is a very powerful tool.  I hate to say it, but MS did something right with LINQ...  

That's the pluses, 

I hate the "var" keyword and inferred types.  That has no business in a Strongly typed language (personal opinion).  I also don't like paying up for MS products, but my company gives me the laptop, and the MSDN subscription, and pays my salary, so I'll continue writing C# for them.

---

### Post by tinny on 2008-08-21
> **LaRoza said:**
> "moot", and yes :-)

:oops:

Ummmm..... no..... I..... was telling you to shut up :lolflag:

Trust me im better at coding than forum posting, only just though :)

---

### Post by tinny on 2008-08-21
> **jcwmoore said:**
> I like object and collection initializers, not that they are impressive, just some hand wavy compiler tricks.  I Love LINQ, i don't know if that exists in a non .NET language, but that is a very powerful tool.  I hate to say it, but MS did something right with LINQ...  


LINQ is good.

DLINQ [is just ORM]("http://weblogs.asp.net/jambrose/archive/2005/10/04/426618.aspx"), in Java we have the JPA spec and many implementations (Hibernate etc...). Im pretty sure other languages have ORM.

XLINQ, I dont know much about XLINQ (XML querying using objects, right?).

---

### Post by Alasdair on 2008-08-21
[QUOTE=jcwmoore]I hate the "var" keyword and inferred types. That has no business in a Strongly typed language (personal opinion).[/QUOTE]
What does type-inference have to do with strong typing? Precisely nothing, that's what. :)

Before discussing type systems every coder should A) learn Haskell/ML or similar, or B) read this article: ["What To Know Before Debating Type Systems"]("http://www.pphsg.org/cdsmith/types.html"). While I'm sure there are plenty of reasons to hate this 'var' keyword, type-inference not having a place in a strongly typed language is certainly not one of them.

---

### Post by LaRoza on 2008-08-21
> **tinny said:**
> 
Ummmm..... no..... I..... was telling you to shut up 

Good catch :-)

> 
Trust me im better at coding than forum posting, only just though :)

Hope so. I hope you don't code anything explosive or movable...

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> LINQ is good.

DLINQ [is just ORM]("http://weblogs.asp.net/jambrose/archive/2005/10/04/426618.aspx"), in Java we have the JPA spec and many implementations (Hibernate etc...). Im pretty sure other languages have ORM.

XLINQ, I dont know much about XLINQ (XML querying using objects, right?).

I have been using the ORM called LLBLGen Pro since 04. [http://www.llblgen.com/](http://www.llblgen.com/)

His support amazes me. Also, I can turn on tracing and see the queries being generated as well. His designer and template languages are top notch too!

.NET has a clone of Hibernate (NHibernate), which I think works with Mono as well. [http://www.mono-project.com/Database_Access](http://www.mono-project.com/Database_Access) I stayed away from Hibernate, because of all the XML config files. LLBLGen generates the DAL for me.

---

### Post by jcwmoore on 2008-08-21
> **Alasdair said:**
> What does type-inference have to do with strong typing? Precisely nothing, that's what. :)

Before discussing type systems every coder should A) learn Haskell/ML or similar, or B) read this article: ["What To Know Before Debating Type Systems"]("http://www.pphsg.org/cdsmith/types.html"). While I'm sure there are plenty of reasons to hate this 'var' keyword, type-inference not having a place in a strongly typed language is certainly not one of them.

good article, i guess i should have though about what i was writing a little more.   I wrote most of a complier (in OCaml) that did that exact function, 

var *name* = *expression*

so you are right, type inferencing has nothing to do with strong typing, the complier is figuring out the type for you.  it is just a personal preference, i don't type inferencing in C#.

---

### Post by doas777 on 2008-08-21
Visual studio is about the only reason I keep a windows box around (that and a few games). 

I like C# because I switch between java and .net daily, and it;s just easier to keep it straight. 

I won't defend the morality or ethics of the company that makes it, but using it is what i get paid to do, and frankly, it takes me about half the time to produce a working system. It does what it's supposed to do, and so do I.

---

### Post by nickgaydos on 2008-08-21
Err a little off question here, but how do you say C#? Do you say it C POUND or something else :P

---

### Post by LaRoza on 2008-08-21
> **nickgaydos said:**
> Err a little off question here, but how do you say C#? Do you say it C POUND or something else :P

C Sharp.

Read the wikipedia article (see my wiki)

---

### Post by nickgaydos on 2008-08-21
> **LaRoza said:**
> C Sharp.

Read the wikipedia article (see my wiki)
Ahh thanks. The only real programming/scripting I did was DOS

---

### Post by tinny on 2008-08-21
> **LaRoza said:**
> Hope so. I hope you don't code anything explosive or movable...

I do code for bank accounts, money is not important right?

---

### Post by doas777 on 2008-08-21
nothing to see here

thanks,
frank

---

### Post by LaRoza on 2008-08-21
> **tinny said:**
> I do code for bank accounts, money is not important right?

"Ok! Ok! I must have, I must have put a decimal point in the wrong place 
or something. Shoot. I always do that. I always mess up some mundane 
detail."

"Oh! What is this fairly mundane detail, Tinny?!!!!!"

---

### Post by cprofitt on 2008-08-21
> **tinny said:**
> If you want to do C# development properly be prepared to put your hand in your pocket.

Use C# spend lots of money!

Visual Studio $$$
Team Foundation Server $$$
Windows Server $$$
SQL Server $$$

This is one of the reasons for me that developing in C# is a different proposition to Java.

In Java I can do all of the above (better) with out spending any money.

I will make my own post here, but MS actually offers free versions of C# and SQL server so it is possible to develop at a low cost.

---

### Post by cprofitt on 2008-08-21
**Love:**

C# was very accessible for me to learn. There were plentiful books and a multitude of good websites. I like the syntax (while I can appreciate that others do not - it is far better to me than VB.Net)

C# allowed me to quickly transfer winform knowledge to webforms and websites; which I have not found to be true in other languages yet (though they may exist)

C# allowed me to leverage my Microsoft Partner program membership (had this due to being a windows AD admin) as well.
[B]
Hate:[/B]

I dislike that I spent so much time learning/using it when I could have learned a truly open language like Python and augmented it with C.

---

### Post by tinny on 2008-08-21
> **PrivateVoid said:**
> I will make my own post here, but MS actually offers free versions of C# and SQL server so it is possible to develop at a low cost.

To a point, read the fine print.

---

### Post by tinny on 2008-08-21
> **LaRoza said:**
> "Ok! Ok! I must have, I must have put a decimal point in the wrong place 
or something. Shoot. I always do that. I always mess up some mundane 
detail."

"Oh! What is this fairly mundane detail, Tinny?!!!!!"

:lolflag:

Your completely right! If its simple and mundane I may stuff it up, If its complicated and interesting I usually do quite well.

---

### Post by cprofitt on 2008-08-21
> **tinny said:**
> To a point, read the fine print.

I have and agree that people need to read the fine print. With the Partner Program (anyone can join for $300 first year / $200 every other year) you get access to the dev tools for 'real' use -- though not the big money ones. You also get ten licenses of Windows XP/Vista, 1 server 2003/8 license, 1 SQL Enterprise license, 1 Exchange license and many other products.

Not as inexpensive as Linux based development, but not the uber expense that team studio or MSDN costs either.

---

### Post by pmasiar on 2008-08-21
> **skeeterbug said:**
> I have netbeans installed at home. I honestly don't know where to start. EJB documentation is massive and there are so many options. Where did you start if you were originally C#?

See? Can you imagine that for someone used to Java/netbeans, C#/VS/.NET is equally massive and impenetrable blob of info, like Java world is for you?

So which one is intuitive, Java or .NET? Who is wrong? Or how you both can be right?

---

### Post by skeeterbug on 2008-08-21
> **pmasiar said:**
> See? Can you imagine that for someone used to Java/netbeans, C#/VS/.NET is equally massive and impenetrable blob of info, like Java world is for you?

So which one is intuitive, Java or .NET? Who is wrong? Or how you both can be right?

No, because in .NET you generally have one technology to work with (example, ASP.NET). You aren't forced to make a huge decision as to which web framework is better. 

[http://www.java201.com/resources/subjects/web_application_frameworks.html](http://www.java201.com/resources/subjects/web_application_frameworks.html)

12 listed there for Java. You are a Python "one way of doing it" kinda guy. Does 12 different web frameworks sound intuitive to you?

---

### Post by cprofitt on 2008-08-21
> **skeeterbug said:**
> No, because in .NET you generally have one technology to work with (example, ASP.NET). You aren't forced to make a huge decision as to which web framework is better. 

[http://www.java201.com/resources/subjects/web_application_frameworks.html](http://www.java201.com/resources/subjects/web_application_frameworks.html)

12 listed there for Java. You are a Python "one way of doing it" kinda guy. Does 12 different web frameworks sound intuitive to you?

Most likely why Python is what I am learning now after C#.

---

### Post by slavik on 2008-08-21
The one thing that people can't rag on that is a microsoft product is .NET ... why do you think Vista is so crappy? (No, seriously, all the good people were on the .NET project).

besides that, I really don't see that much different between Java/JVM and C#/.NET besides the fact that they call things differently (System.out.println vs. Console.write)

---

### Post by cprofitt on 2008-08-21
> **slavik said:**
> The one thing that people can't rag on that is a microsoft product is .NET ... why do you think Vista is so crappy? (No, seriously, all the good people were on the .NET project).

besides that, I really don't see that much different between Java/JVM and C#/.NET besides the fact that they call things differently (System.out.println vs. Console.write)

I agree .Net is a very good framework.

---

### Post by pmasiar on 2008-08-21
You are changing topic (it was how hard is to learn different API) and missing opportunity to learn, but it's your choice. Let's talk about choosing frameworks instead:

> **skeeterbug said:**
> No, because in .NET you generally have one technology to work with (example, ASP.NET). You aren't forced to make a huge decision as to which web framework is better. 

...because MSFT did the decision for you? 

I understand why too much choice is frustrating ("More is less"), but is no choice even better? One size fits all?

Python had more than a dozen frameworks 3 years ago, now it has 2 (Django and Turbogears), focused for different approaches. Yes, situation with java is embarrassing and frustrating.

I'll still take "chose one from these few" over "one size fits all".

---

### Post by LaRoza on 2008-08-21
> **pmasiar said:**
> 
I'll still take "chose one from these few" over "one size fits all".

But you do have a choice! You can use .NET 2.0 or .NET 3.0, on Windows 2000, Windows XP or Windows Vista. It is entirely up to you!

---

### Post by alternatealias on 2008-08-21
> **wil said:**
> The main weakness to me is the boxing/unboxing issues, which negatively impacts performance.

If it could do pointers this would not be an issue. (Yes I know about "by ref")

It looks beautiful and elegant.
It is an improvement on C/C++ because it makes it more difficult to write spaghetti code. (an advantage for a beginner)

OT: In my opinion C or a subset of C++ is still the best but requires more skill to design the initial framework.

Edit: The other thing I really hate is the Garbage Collection. If programs have to run for months at a time memory becomes a problem. To prevent this objects have to then be manually be cleared and garbage collection called, the rules are not simple.

If you use generics, then there is no boxing done.

C# also has pointers.

---

### Post by tinny on 2008-08-21
> **slavik said:**
> The one thing that people can't rag on that is a microsoft product is .NET ... why do you think Vista is so crappy? (No, seriously, all the good people were on the .NET project).

besides that, I really don't see that much different between Java/JVM and C#/.NET besides the fact that they call things differently (System.out.println vs. Console.write)
[B]
Language:[/B]
There are definitely alot of nontrivial language differences between Java and C#.

I found this article to be very informative.
[http://www.25hoursaday.com/CsharpVsJava.html](http://www.25hoursaday.com/CsharpVsJava.html)

**Runtime:**
[B]
.Net[/B]
1. .Net is JIT complied.
2. Uses a the common language runtime (CLR) to deliver multiple languages for the one runtime.
3. .Net has very strong integration into the windows OS.

**HotSpot JVM**
1. Java is now JIT complied by default (I think it has only recently become default?) used to be interpreted by default.
2. I dont think that third party languages are compiled straight into Java byte codes. I think they are essentially implemented in Java??? (Jython, JRuby etc...)
3. The JVM tries hard but unfortunately doesn't have the level of OS integration that .Net has.

**Class Libs**

IMO the .Net and Java class libraries are WAY different.

---

### Post by tinny on 2008-08-21
> **skeeterbug said:**
> No, because in .NET you generally have one technology to work with (example, ASP.NET). You aren't forced to make a huge decision as to which web framework is better. 

[http://www.java201.com/resources/subjects/web_application_frameworks.html](http://www.java201.com/resources/subjects/web_application_frameworks.html)


1+

The J2EE space is really fragmented! There are soooo many ways of doing one thing. However in the .Net world you pretty much do it the one way.

---

### Post by tinny on 2008-08-21
> **LaRoza said:**
> But you do have a choice! You can use .NET 2.0 or .NET 3.0, on Windows 2000, Windows XP or Windows Vista. It is entirely up to you!

:lolflag:

> **pmasiar said:**
> 
I understand why too much choice is frustrating ("More is less"), but is no choice even better? One size fits all?

Python had more than a dozen frameworks 3 years ago, now it has 2 (Django and Turbogears), focused for different approaches. Yes, situation with java is embarrassing and frustrating.

I'll still take "chose one from these few" over "one size fits all".

I wish Java would consolidate the best frameworks.

> **alternatealias said:**
> If you use generics, then there is no boxing done.

C# also has pointers.

:confused:

As of version 5 Java has auto boxing.

[PHP]
    	List<Integer> list = new ArrayList<Integer>();
    	list.add(2);
[/PHP]

---

### Post by skeeterbug on 2008-08-21
> **pmasiar said:**
> You are changing topic (it was how hard is to learn different API) and missing opportunity to learn, but it's your choice. Let's talk about choosing frameworks instead:

I use Python and Ruby regularly, I am not missing any opportunity to learn.

> 
...because MSFT did the decision for you?

I understand why too much choice is frustrating ("More is less"), but is no choice even better? One size fits all?

Their package is offers a compelling solution. I think someone tried doing an MVC framework in .NET. 3.5 offers MVC, I haven't used it yet so I can't comment.


> 
Python had more than a dozen frameworks 3 years ago, now it has 2 (Django and Turbogears), focused for different approaches. Yes, situation with java is embarrassing and frustrating.

I'll still take "chose one from these few" over "one size fits all".

Pylons, Turbogears, webpy, Django, and Zope. I am sure there are still others. You could say turbogears and pylons are merging, but the are still seperate and pylons is less opinionated. I am glad TG is finally switching to SQLAlchemy, I use that heavily along side my C# customer portal software (SQLObject never felt right for some reason). It is by far the superior ORM for Python.

---

### Post by tinny on 2008-08-21
> **skeeterbug said:**
> 
Their package is offers a compelling solution. I think someone tried doing an MVC framework in .NET. 3.5 offers MVC, I haven't used it yet so I can't comment.


MVC is common place in a few languages.

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> But you do have a choice! You can use .NET 2.0 or .NET 3.0, on Windows 2000, Windows XP or Windows Vista. It is entirely up to you!

You still have choices over ORM, javascript libraries, server side control suites, etc. The framework provides caching, viewstate, session, security and role providers (which you can implement your own very easily), a template language, and all of the other classes in the .NET framework. I can put my business logic or middle tier on a different application server and communicate to it through XML web services or remoting.

---

### Post by pmasiar on 2008-08-21
> **tinny said:**
> 3. The JVM tries hard but unfortunately doesn't have the level of OS integration that .Net has.

But being OS-independent was the selling point for Java back in 95! Everybody wanted to be independent from Windows (the sucky Win3.11 and win'95, and good old MSDOS 5.0), Linux was just emerging and dozen different unices were wighting each other.

Now, question of platform is solved: there are two, Windows and Linux (with sprinkling of BSD). Java is the monkey in the middle, extra efforts needed to deal with each platform.

Of course .NET has tight integration with C#: because it can afford to ignore Linux world.

---

### Post by skeeterbug on 2008-08-21
> **pmasiar said:**
> But being OS-independent was the selling point for Java back in 95! Everybody wanted to be independent from Windows (the sucky Win3.11 and win'95, and good old MSDOS 5.0), Linux was just emerging and dozen different unices were wighting each other.

Now, question of platform is solved: there are two, Windows and Linux (with sprinkling of BSD). Java is the monkey in the middle, extra efforts needed to deal with each platform.

Of course .NET has tight integration with C#: because it can afford to ignore Linux world.

Write once debug everywhere right? ;)

---

### Post by tinny on 2008-08-21
> **pmasiar said:**
> But being OS-independent was the selling point for Java back in 95!

Yeah, you cant have it both ways.

---

### Post by tinny on 2008-08-21
> **skeeterbug said:**
> Write once debug everywhere right? ;)

I have a massive bug on my PC at work, it goes by the name Vista ;)

> 
You still have choices over ORM, javascript libraries, server side control suites, etc. The framework provides caching, viewstate, session, security and role providers (which you can implement your own very easily), a template language, and all of the other classes in the .NET framework. I can put my business logic or middle tier on a different application server and communicate to it through XML web services or remoting.


When I did .Net development we used web services and remoting to achieve a distributed enterprise model. IMO the EJB (or Spring Bean) approach is far better. @skeeterbug, you should have a look at [Spring .Net]("http://www.springframework.net/") if its as good as Spring for Java you'll love it.

---

### Post by skeeterbug on 2008-08-21
> **tinny said:**
> I have a massive bug on my PC at work, it goes by the name Vista ;)

I am still on XP for my development machine. Waiting for SP2 of Vista... maybe...

---

### Post by pmasiar on 2008-08-21
> **skeeterbug said:**
> Write once debug everywhere right? ;)

Well, C# is write once run on Windows only...

I am aware that C#, as heir to Java, added couple new cool features, which Java considered unimportant then (and adding them now). If choice was only between C# and Java, it would be hard (slavery or inferiority). But I can reject both.

BTW you can too: Try IronPython for parts where agility and flexibility is more important than speed (about 80% of the code)

---

### Post by skeeterbug on 2008-08-22
Apparently my posts are being edited by forum staff now, because editing out ******* isn't enough I guess.

---

### Post by LaRoza on 2008-08-22
> **skeeterbug said:**
> Apparently my posts are being edited by forum staff now, because editing out ******* isn't enough I guess.

If you wish to contest a mod's actions (in this case, not mine of course), you can do so in the Resolution Centre. Don't do it on this this thread.

---

### Post by CptPicard on 2008-08-22
> **pmasiar said:**
> If choice was only between C# and Java, it would be hard (slavery or inferiority). But I can reject both.


IMO you'll be hard pressed ignoring both for large enterprise development. Python simply doesn't cut it there yet -- how do I do a distributed transaction?

I steer clear of C# threads simply because I don't have a proper opinion, never having tried C# or even looked into it in any substantial detail, but it would seem to me that Java wins in this simply because of its multiplatformness. EJB3 looks solid too.

Then again, Java's crossplatform solution is to essentially to simply completely hide the host platform. It really turns all OSes into "The Java Platform", and if you want something from the host OS, it's going to require some hacking to get break out of the Matrix ...

---

### Post by tinny on 2008-08-22
> **CptPicard said:**
> 
I steer clear of C# threads 


I thought you'd be smart enough to use Threads in C# :KS

> **CptPicard said:**
> 
EJB3 looks solid too.


:)

> **CptPicard said:**
> 
if you want something from the host OS, it's going to require some hacking to get break out of the Matrix ...


```

Runtime runTime = Runtime.getRuntime();
process = runTime.exec("gksu apt-get update");
etc...

```

Or use JNI

---

### Post by pmasiar on 2008-08-22
> **CptPicard said:**
> IMO you'll be hard pressed ignoring both for large enterprise development. Python simply doesn't cut it there yet -- how do I do a distributed transaction?

I was wearing my FOSS developer hat at the time. Of course, my job is hacking Java - but I am trying my options to break free, while still remain in academia. I like it here.

---

### Post by tinny on 2008-08-22
This is what I hate the most about C#, we are really talking about .Net right!?!?! **Embrace, Extend, Extinguish**. 

Embrace = J# (I believe this cost then 1 billion dollars when they lost a lawsuit from Sun)
Extend = C#
Extinguish = They failed....

---

### Post by jviscosi on 2008-08-22
I don't love C#, but as I work in a Microsoft shop, it's about the closest I can get to Java here.  It's a pretty good Java knockoff, actually, and although there are a number of Java features that I miss (like checked exceptions and anonymous inner classes) there are also things in C# that I would like to see in Java.

Anyway, at least it's not VB.NET.  We have an old VB.NET site here that somebody else wrote and I have to maintain, and it makes my eyes bleed just to look at it.

---

### Post by tinny on 2008-08-22
> **jviscosi said:**
> Much as I hate to say anything nice about MS, you can get "Express" versions of Visual Studio that are free and are functional enough to use for actual work-related development.  (I've been using Visual Web Developer Express at work for a couple of years now.)  You can also get an "Express" version of SQL Server that will serve adequately as a backend.  I will say without reservation (or actual evidence) that the only reason these products exist is because of competing OSS programs.


Only free to a point. You really have to read the fine print. Basically if your project becomes a success, then they want you to put your hand in your pocket.

---

### Post by raul_ on 2008-08-22
> **skeeterbug said:**
> Visual Studio is worth it 

Am I the only one who feels Visual Studio is absolutely horrible to work with? I don't say this because it's a Microsoft product, I don't really care about that "Microsoft is evil" cult, but I've been forced to work with it for a couple of times (mainly in machines with Windows environment only, and I must admit that in the end, using Visual Studio is more appealing than writing code in notepad).

Although, I'll honestly say that I never took the time to understand Visual Studio, and maybe I just confuse it with my feeling when programming on Windows, being a guy that has always developed in Linux (and Eclipse on Windows, but it's very similar when maximized)

---

### Post by jimi_hendrix on 2008-08-22
> **tinny said:**
> Only free to a point. You really have to read the fine print. Basically if your project becomes a success, then they want you to put your hand in your pocket.

remind me that when i compile my big project to use mono

---

### Post by jimi_hendrix on 2008-08-22
> **raul_ said:**
> Am I the only one who feels Visual Studio is absolutely horrible to work with? I don't say this because it's a Microsoft product, I don't really care about that "Microsoft is evil" cult, but I've been forced to work with it for a couple of times (mainly in machines with Windows environment only, and I must admit that in the end, using Visual Studio is more appealing than writing code in notepad).

Although, I'll honestly say that I never took the time to understand Visual Studio, and maybe I just confuse it with my feeling when programming on Windows, being a guy that has always developed in Linux (and Eclipse on Windows, but it's very similar when maximized)

i like visual studios on my windows partition (dont use C# much anymore...but i still like it (probably because im too new to not realize its faults)) and i like the rapid text completion and the compiler/debugger that catches syntax errors and warnings before compile time

---

### Post by raul_ on 2008-08-22
> **jimi_hendrix said:**
> i like visual studios on my windows partition (dont use C# much anymore...but i still like it (probably because im too new to not realize its faults)) and i like the rapid text completion and the compiler/debugger that catches syntax errors and warnings before compile time

Yeah those are nice features, but again, every other IDE has them, including the Windows version of Eclipse, and you don't have to pay for it. I'm not against payed software, but when they don't offer anything other than it's (free) competitors, I think it's unfair with it's "clients"

Of course, this can't be extrapolated to Vista vs Linux, because Vista offers features that Linux or OS X don't have, and vice-versa. Not really on the topic, but just before someone tries to go off-track

---

### Post by jimi_hendrix on 2008-08-22
heh i didnt pay for mine...except for whatever was in the fine print (i probably owe my hello world to MS) plus the author of the first book i got used VS so i thought i might as well use the same IDE

---

### Post by tinny on 2008-08-22
> **jimi_hendrix said:**
> heh i didnt pay for mine...except for whatever was in the fine print (i probably owe my hello world to MS) plus the author of the first book i got used VS so i thought i might as well use the same IDE

Have you seen [SharpDevelop]("http://sharpdevelop.net/OpenSource/SD/")?

Can someone please talk about Mono. 

Ill kick it off, whats Monodevelop like compared to VS?

What compatibility level is Mono currently at? (3.5?)

Have they implemented the "[System.Management]("http://www.csharpcorner.com/UploadFile/karthik_mascon/IntroSystemManagementWMI07202005030155AM/IntroSystemManagementWMI.aspx?ArticleID=843cbea4-03f7-4a7b-b507-59a041cba68d")" namespace yet? Can they? I really enjoyed interfacing with WMI by using this namespace, this would be great on Linux... Not WMI but some other OS interface scheme. Does Mono have the scope to introduce any Linux specific API's???

---

### Post by LaRoza on 2008-08-22
> **tinny said:**
> 
Ill kick it off, whats Monodevelop like compared to VS?

What compatibility level is Mono currently at? (3.5?)


Never used Monodevelop or VS, but [http://en.wikipedia.org/wiki/Mono_(software)#Current_status_and_roadmap](http://en.wikipedia.org/wiki/Mono_(software)#Current_status_and_roadmap)

---

### Post by alternatealias on 2008-08-23
> **tinny said:**
> Have you seen [SharpDevelop]("http://sharpdevelop.net/OpenSource/SD/")?

Can someone please talk about Mono. 

Ill kick it off, whats Monodevelop like compared to VS?


It works pretty well, but has a ways to go still imho (mostly in the area of refactoring features). That said, it is progressing very rapidly and already does most of he common features that I (and probably most people) need.

> **tinny said:**
> 
What compatibility level is Mono currently at? (3.5?)


Mono's C# compiler supports all of the latest (3.0) language features.

See [http://www.mono-project.com/CSharp_Compiler](http://www.mono-project.com/CSharp_Compiler) for more details.

I'm pretty sure that Mono 1.9 (latest) supports all of the .NET 2.0 APIs at the very least (they have full Windows.Forms 2.0 support, for example) and I believe that they have at least some of the 3.5 libraries implemented, but I don't /think/ that the 3.5 API is complete (but I could be wrong).


> **tinny said:**
> 
Have they implemented the System.Management namespace yet?


From what I can gather reading [http://www.mono-project.com/Mono_Project_Roadmap](http://www.mono-project.com/Mono_Project_Roadmap), the answer seems to be "no":

> 
 Windows-specific APIs

These are APIs that are very tied to the Windows platform and do not map to Linux or Unix:

    * System.Management 


> **tinny said:**
> 
Can they?


Apparently not, as the API is very Windows-specific.

> **tinny said:**
> 
I really enjoyed interfacing with WMI by using this namespace, this would be great on Linux... Not WMI but some other OS interface scheme. Does Mono have the scope to introduce any Linux specific API's???

I'm guessing that you mean Linux-specific Management APIs.

You'd have to ask the Mono developers about this one.

---

### Post by tinny on 2008-08-23
> **alternatealias said:**
> 
Apparently not, as the API is very Windows-specific.


I think that they may have there own Mono specific API's.
[http://www.go-mono.com/docs/](http://www.go-mono.com/docs/)

Im guessing that these libs are specific to Mono...?
# Mono Libraries
# Gnome Libraries
# Mozilla Libraries
# Novell Libraries

---

### Post by kjohansen on 2008-08-24
the biggest disadvantage to monodevelop right now is the lack of a functioning debugger.  there was a debugger, then it was broken by some framework changes but should be back soon (end of year maybe i hear)

this is the only reason I still dual boot, so I can use VStudio to debug my .net apps.

---

### Post by tinny on 2008-08-24
Id be interested to know if there is anyone here that has worked on or knows of a live web site that is built on mono ASP.NET?

Id also be interested to know if you can truly just run your .Net code on mono and vice versa. Is there much effort involved in the migration?

---

### Post by jimi_hendrix on 2008-08-24
mono is ok...only problem i have with it is that for one of the challenges i had to use ```
using System.Net
``` and it says it didnt exist on my machine but laroza tried my code and it compiled

---

### Post by Smygis on 2008-08-24
> **tinny said:**
> 



```

Runtime runTime = Runtime.getRuntime();
process = runTime.exec("gksu apt-get update");
etc...

```

Or use JNI

Oh my fckin god. Thank the lord of whaterver that i chose Python instead of C#/Java. You wrote runtime FIVE times in a row. How reciculus is that. Thats like brainfuck or something.
RunTime rUNtIME runtime(RUNTIME.rUnTiMe);
runTIME = RUNtime(runTime, runtime);

---

### Post by kjohansen on 2008-08-24
> **tinny said:**
> Id be interested to know if there is anyone here that has worked on or knows of a live web site that is built on mono ASP.NET?

Id also be interested to know if you can truly just run your .Net code on mono and vice versa. Is there much effort involved in the migration?
Ive developed a couple of applications in windows and run them on mono without a problem.  Console and windows forms applications.  I had a little trouble running the windows forms application since i hadnt installed the mono winforms component yet.

None of them used any weird apis though.  Just some collections/generics and file operations.

---

### Post by pbpersson on 2008-08-24
> **LaRoza said:**
> 

C# was made (originally) by Microsoft to compete with Java because Microsoft lost a lawsuit to Sun when they tried to not follow the Java standards (Microsoft can't follow standards without trying to take it over or introduce non standard elements, if you don't believe me, IE has been behind in web standards while Microsoft has introduced IE only technologies, the MS XML based document format used by Office 2007 is not the same format they had standardised, and a perfectly function XML based format exists already (ODF))

Microsoft is all about competition - they do not care about humanity or the planet, they just want to win.  They cannot follow standards, they need to "change" them so they will only work with Microsoft products.  You can use their products to develop software, but it will only work on Windows.

So....as a developer, do I want to follow one company that has tunnel vision and can only see their reality, or do I want to follow dozens of companies who are creating far better products that DO follow standards and will allow my software creations to run on any computer on the planet?

Here is a direct quote from the Visual Studio packaging: "J#.NET is not a tool for developing applications intended to run on a Java Virtual Machine.  Applications and services built with J#.NET will only run in the .NET Framework"

This my friends is the tale wagging the dog.  It is the perfect example of a huge software giant shooting themselves in the foot for all the world to see.  This entire practice of Microsoft - pretending that Windows comprises the entire world and that all of IT revolves around the WinTel environment - I think it makes them look VERY foolish.

In my opinion, the Microsoft Corporation and anyone who marries themselves to their solutions are painting themselves into a corner and severely limiting their choices.

---

### Post by LaRoza on 2008-08-24
> **pbpersson said:**
> In my opinion, the Microsoft Corporation and anyone who marries themselves to their solutions are painting themselves into a corner and severely limiting their choices.

Interestingly, that is exactly what Microsoft wants to happen!

---

### Post by jviscosi on 2008-08-27
> **tinny said:**
> Only free to a point. You really have to read the fine print. Basically if your project becomes a success, then they want you to put your hand in your pocket.

Ha, I took that part of my post out because I saw that somebody had already made the same point, but you were too fast for me.  Anyway, we don't resell the stuff we write, so I don't think we have to worry about it.  I'll have our nonexistent legal department check the license, though.  ;-)

---

### Post by sakabato on 2008-08-30
let me make my points

C# (and not .net) is 100% ECMA standard language and anyone is free to implement it without royality. So it does not belong to Microsoft although the main driver for the specification is Microsoft.

So called pattent discussions covers .NET and mono frameworks but a language is not the same as a framework although C# is tightly bundled with .NET and mono

Currently latest C# 3.0 specification is 100% implemented on mono (only at SVN for the time being)

You can develop C# Web or thick client applications with all open source tools meaning: C#  + Apache + mysql/postgresql is a common scenario + Monodevelop (has even a gui debugger on SVN now)

So C# is not for windows only and as you know even ubuntu comes with a C# application out of box: tomboy

---

### Post by Can+~ on 2008-10-24
> **sakabato said:**
> let me make my points

C# (and not .net) is 100% ECMA standard language and ...

So is the ISO/ECMA "standard" [Office Open XML]("http://en.wikipedia.org/wiki/Office_Open_XML"), and we all know how it got there *cough*LOBBY*cough*.

---

### Post by cszikszoy on 2008-10-24
> **tinny said:**
> Id be interested to know if there is anyone here that has worked on or knows of a live web site that is built on mono ASP.NET?

Id also be interested to know if you can truly just run your .Net code on mono and vice versa. Is there much effort involved in the migration?

Wikipedia uses mono + ASP.NET for their search engine.

And yes, an executable compiled in visual studio on my windows machine will run completely natively with the mono framework on my linux machine, and vise versa.  As long as the developer of the application does not make stupid assumptions about the operating system (things like hard coding the directory separator character, which is / on unix but \ on windows), there will be no problem with code portability.  Also, since GTK now builds on windows, it opens the door for linux apps to be 100% "drag and drop" compatible with windows.

---

