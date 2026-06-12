---
title: "Will programming Unix/Linux programs in C# ever be a marketable skill?"
date: 2005-07-25
forum: Programming Talk
---

### Post by Hudson Hawk on 2005-07-25
I have moved over to Linux slowly over the last year after starting an MCAD (Ms Certified Applications Developer) qualificartion and after hearing about the mono project and being intrested in crossplatform C#.

I have fell in love with the idea of open source and free software (both the giving and reciving).. the idea of doing what I do to benefit every one and further the devlopment of software rather than code somthing great and never show anyone its inner workings so the next guy along has to "reinvent the wheel" and so on.

I would like to never have to boot into Windows again.... except for the fact my key employable skills are in C#.NET, ASP.NET &  ADO.NET. (also know some Java & SQL and am lerning PHP, HTML and CSS).

So was wondering what everyones oppinion on C# becoming a big player as far as crossplatform languages are councerned? Is Mono the tip of the iceberg or a drop in the ocean?

I know you are thinking:"Well you could just switch to C++" but:....
1) This course cost me a lot of money.
2) My earning potential as a .NET coder is higher (or so it seems).
3) Coding in C# is fun! and easy and i really like it and its fast results thanks to its managed nature.

Any other C# coders out there with simular hopes?

---

### Post by dataw0lf on 2005-07-25
[QUOTE=Hudson Hawk]
So was wondering what everyones oppinion on C# becoming a big player as far as crossplatform languages are councerned? Is Mono the tip of the iceberg or a drop in the ocean?
[/QUOTE]

I'm extremely eager for C# to reach it's full potential (both as a cross platform language in general, and as it's intended purpose: a Java killer [Java being a language I've always thought of as over engineered and poorly implemented, not to mention painful to work in]).  

Even moreso, I'd like to see the IronPython implementation taken further.

---

### Post by charlieg on 2005-07-25
I think it's only a matter of time before people recognise that Mono won't be persecuted by Microsoft and that it has the potential to really embed itself as a core Free Software programming tool.  Mono+IronPython would be a beautiful combination for Ubuntu.

---

### Post by Hudson Hawk on 2005-07-25
One of the bigest stumbling blocks to crossplatform C# is that even some of the people who code it proffesionaly think its a MS "product" and that MS can control and dictate its direction (some proffesional coders on my course sware blind its a Windows programming language thats just recived a shoddy "port" to linux) and thusly it will never work on other systems as MS will just change the laugages standards to scupper linux/unix/OSX/etc development.... which is just not true.

Since it was standardized it is a programming language standard just like C++ or C that no one has direct and unchallanged control over... you can download and read the C# standards in pdf format from the ECMA web site and no where does it mention windows but rather "operating sytsems" (as in more than one specific OS.)

It doesn't bode well for crossplatform C# when the people you would imagine should be in the know (i.e ppl who are paid to code C# for a living) think its a Windows specific version of Java ... and the C++ veterans tend to do little but berate it  :? (with no reason except:  "its just too easy to code with so it must be a n00b language") ... but here's hoping, hey :)

---

### Post by LordHunter317 on 2005-07-25
> **Hudson Hawk]One of the bigest stumbling blocks to crossplatform C# is that even some of the people who code it proffesionaly think its a MS "product" and that MS can control and dictate its direction[/quote]Well, it is and they can.

The standard (as in, ECMA) parts of the common language infrastructure and C# are terribly small and while a good base for a language, they aren't sufficent to make a platform.

And it's reasonably clear that MS has no intention of opening .NET any further than they already have, anytime soon.

> and thusly it will never work on other systems as MS will just change the laugages standards to scupper linux/unix/OSX/etc development.... which is just not true.Yes, but not because MS won't try, but rather that the design they've chosen would make that rather prohibitively difficult.

MS' direction isn't to make Linux eaiser to emulate them said:**
>  you can download and read the C# standards in pdf format from the ECMA web site and no where does it mention windows but rather "operating sytsems" (as in more than one specific OS.)Yes, but the standard is nothing compared to what MS offers with .NET.  The standard doesn't include ADO.NET, ASP.NET, S.W.F., or any of the other nice things about .NET development.

---

### Post by Hudson Hawk on 2005-07-25
It doesnt have to offer all the extras of .NET it a good language in its own right the simplicity of the way its structured, etc ... sure MS owns .NET and can take it where they like but C#  is standardised and most realists dont expect it to end up fully MS-a-fied on all platforms and it will need differing ways of doing certain things. 

Sure MS can change the way ADO.NET works with C#.NET (for example) over time but with the standardizaiton of C# and not ADO.NET  or ASP.NET, etc... ppl like the monoproject have clear goals and are aware of what is subject to the whims of MS and what is not.

Does it matter if 2 years down the line C# on linux uses some other non-.NET solution to provide ASP.NET(like) funcitonality? 
No of course not its like saying C++ under windows has DirectX so making C++ games on linux is a futile waste of time just becuase you cant use MSes handy-dandy -all-in-one tool kit api.

---

### Post by LordHunter317 on 2005-07-25
[QUOTE=Hudson Hawk]It doesnt have to offer all the extras of .NET[/quote]Cross-platform adoption won't happen unless it does.

Most programmers aren't going to switch if you have to learn a whole new API.  It's the same issue with C and C++ now: too much is left up to the underlying platform.

Having two completely different platform APIs isn't going to cause people to move.

C# in and of itself isn't a good enough language to encourage that.  

> Does it matter if 2 years down the line C# on linux uses some other non-.NET solution to provide ASP.NET(like) funcitonality? Yes, if your goal is to encourage and allow for **cross-platform** development and developer migration.

That means either both platforms have to use the same API, or someone has to provide a wrapper layer to account for the differences that works everywhere.

While I like C# very much, the language itself isn't enough for me to use Mono; nor is the ability to use C# with a different API enough motivation to get developers to switch.  Syntax is rather meaningless with these things.

I want Mono for ASP.NET, and ADO.NET, and things like that.  If the **API isn't the same**, there's almost no point.  MS has already demonstrated how little the language matters with the .NET platform.

---

### Post by cwaldbieser on 2005-07-25
I think LordHunter makes a valid point about the lack of libraries, though.  There are tons of interesting and free computer languages to be used, but the ones that gain traction tend to offer a boat load of core services on the platforms on which they are used.  For example, Java would not be quite so popular today if it didn't have that huge standard library that does all sorts of nice things for you.

C# on GNU/Linux may or may not become popular.  I believe that if quality libraries and frameworks are produced for it, it will attract more programmers.  For the casual programmer, these tools make tasks that would be out of reach (due to lack of experience and/or skill) a reality.

Dataw0lf's point about IronPython is also interesting.  One big criticism I have of the whole .NET platform and particularly ASP.NET, is that all the support for scripting languages virtually disappeared.  One nice thing ASP had over ASP.NET was that you could quickly diagnose problems and apply quick changes to a server in production because the development environment and production environment are the same (with respect to ASP script-- COM components are just a hassle to work with no matter how you look at it).  

In ASP.NET, the problems with "DLL Hell" were eliminated, but it seems like the flexibility offered by scripting was also thrown out the window.  For some minor changes, you still need to recompile and redeploy the software.  I think something like IronPython, where you could take advantage of the platform services without having to re-compile all the time would be of tremendous benifit.  It occurs to me that this type of feature would be even more valuable in *NIX environments were script programming is widely prevelant.

---

### Post by LordHunter317 on 2005-07-26
[QUOTE=cwaldbieser] One big criticism I have of the whole .NET platform and particularly ASP.NET, is that all the support for scripting languages virtually disappeared.[/quote]No, it didn't.  You can still write VBScript (well, VB.NET) and treat ASP.NET as ASP Classic, if you really want to.  But that's a pretty retarded way of doing things.

It throws out all of the advantages of ASP.NET.

> One nice thing ASP had over ASP.NET was that you could quickly diagnose problems and apply quick changes to a server in production because the development environment and production environment are the same (with respect to ASP script-- COM components are just a hassle to work with no matter how you look at it).  Guess what, none of that is different under ASP.NET.

ASP.NET actually makes debugging and diagonising eaiser, because it has better error abilities and far better abilities to debug web applications.

I'll take those abilities at the cost of having to recompile my code more often any day.  The slight overhead of having to rebuild a few files is more than worth it to me.

Development and production are still the same, Development just has a dressier interface now.  They're only different if you want them to be.

> In ASP.NET, the problems with "DLL Hell" were eliminated, but it seems like the flexibility offered by scripting was also thrown out the window.No, it wasn't.  It was replaced by something far more flexable and scalable.

>  I think something like IronPython, where you could take advantage of the platform services without having to re-compile all the time would be of tremendous benifit.You still would have to, because of the way the CIL works.  

If your code is in a codebehind compiled into a Assembly (DLL), you have to rebuild the DLL to test those changes.  The language (VB.NET, C#, IronPython) doesn't change that.  It's a requirement of how IIS works with CIL assemblies/DLLS.

There's no such thing as an interpreted language under the common language runtime, really (I mean in the classical sense, not in the Java bytecode sense).  Even ASP.NET pages are parsed and compiled as regular classes, then run.  It just happens the parsing and compiling occurs just-in-time, at first page access.

---

### Post by cwaldbieser on 2005-07-27
[QUOTE=LordHunter317]
Development and production are still the same, Development just has a dressier interface now.  They're only different if you want them to be.
[/QUOTE]

While that is true, in practice, it seems like ASP.NET encourages you to seperate your web app into "foo.aspx" and "foo.aspx.vb" files (or aspx.language-extension).  On a server that does not have the development tools installed on it, making changes to the "foo.aspx.vb" file will not cause the changes to take affect immediately-- a recompile is needed..

On the whole, I can see where there are many benefits to this kind of seperation, and during development, recompiling is actually pretty quick (VB6 probably had one of the worst compilers I have ever had the misfortune to work with).  However, in a support role, there are many times when the only tool at one's disposal is "notepad.exe".

That is one reason I like tools like bash or python.  The development environment and deployment are often identical.  A text editor of some sort being available is a pretty reasonable assumption on many machines.

I must admit that I don't know much about Iron Python other than the fact that it has been favorably been compared to Jython (I believe the developer of Jython left that project to work on Iron Python).  I had hoped that it would somehow work in a similar fashion.  For example, with Jython, I could write a Swing program without needing to compile a Java class.  It would be nice to be able to have a "foo.aspx.py" file that I could make changes to with a simple editor and see the results immediately in my browser.  Kind of like how the .aspx pages are automatically recompiled, I guess.

---

### Post by LordHunter317 on 2005-07-27
[QUOTE=cwaldbieser]While that is true, in practice, it seems like ASP.NET encourages you to seperate your web app into "foo.aspx" and "foo.aspx.vb" files (or aspx.language-extension).[/quote]Right, that's inherently a desirable and good thing.  Seperating code from presentation is good.

> On a server that does not have the development tools installed on it, making changes to the "foo.aspx.vb" file will not cause the changes to take affect immediately-- a recompile is needed..And the penalty of having to this on a non-development machine isn't worth talking about.  You shouldn't be changing files willy-nilly in production, and most production sites have all the codebehind files compiled into a DLL anyway, so you have to recompile by design.

---

