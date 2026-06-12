---
title: "why should i choose java over others?"
date: 2009-08-28
forum: Programming Talk
---

### Post by docesam on 2009-08-28
i came across two high level programming languages :python and ruby.
they are cross platform,just like java. they are very productive ( a programmer can write a program using python in less than quarter the time you need to write the same program in java). they have have -more or less- all the features you need to make your life easy.

my question is : why then should me ,you and everybody sacrifice productivity and go for java instead ? what does java has that make it more favorable?

---

### Post by sloggerkhan on 2009-08-28
Go with python.

Unless you absolutely need java.

IMO.

---

### Post by kpkeerthi on 2009-08-28
> **docesam said:**
>  a programmer can write a program using python in less than quarter the time you need to write the same program in java
Thats not true. I've been programming in Java (not toy programs, real world enterprise banking & financial applications that run on UNICES and IBM Mainframes) for 10 years, since 1999. Throw me a python code and I will give you a Java equivalent in half time or less. :)

Now, back to your original question...
It depends. I would not choose Java to develop a desktop application with GUI and such. 

There are areas where Java really shines - Web-based Enterprise Application development - the J2EE umbrella of standards and tools. Python is a no match here.

---

### Post by myrtle1908 on 2009-08-28
Like kpkeerthi, I too have been programming in Java since the mid 90s mainly in the fields of web-based insurance and claims management.  For this style of mission-critical enterprise systems development JEE really has no equal.

This does not mean to say that I don't have problems (annoyances) with Java as a language.  Java is far far too *wordy*, so much so that it gives me the *****.  The package system is plain annoying and the exception system can be painful.  Java certainly is not a language one would use for prototyping.  Python on the other hand is much better suited here.  It would not be my first choice however ;)

---

### Post by Fallen_Demon on 2009-08-28
I think Java on the desktop is great and all for little apps. Maybe little games and such, but I really wouldn't use it for anything huge. Can you imagine Crysis written in Java? The thing would take 20 years to load :P But, I'll concede, J2EE has awesome power. 

My advice is don't get hooked on one language. Branch out and learn a few different ones, then choose. I prefer Python to Ruby and Java to Python, but I know people who refuse to use Java and love Ruby. It's just personal preference, use what suits the way your mind works

---

### Post by schmendrick on 2009-08-28
> **kpkeerthi said:**
> 

It depends. I would not choose Java to develop a desktop application with GUI and such. 



Interesting to hear this from an experienced Java programmer! What else would you use?

---

### Post by badperson on 2009-08-28
I'm also mroe of an immediate java programmer, I was interested in them comments about java desktop apps; I think I would basically agree, but point out that Netbeans and Eclipse are both written in java...(that statement may be making your point for you, depending on your perspective...)

I've always been curious as to why java desktop stuff never really took off. I think it's a lot better now; swing looks a lot more native, and I think the performance gap has shrunk as the jvm has gotten better and computers have gotten faster....my 2 cents. 
bp

---

### Post by sloggerkhan on 2009-08-28
> **badperson said:**
> I'm also mroe of an immediate java programmer, I was interested in them comments about java desktop apps; I think I would basically agree, but point out that Netbeans and Eclipse are both written in java...(that statement may be making your point for you, depending on your perspective...)

I've always been curious as to why java desktop stuff never really took off. I think it's a lot better now; swing looks a lot more native, and I think the performance gap has shrunk as the jvm has gotten better and computers have gotten faster....my 2 cents. 
bp

I think the issue here is that java is great if you want to work with databases, large data structures, and have many people doing parts of a large complex project. But this does not mean it is good for most user-level software.

However, when it comes working with individual aspects of a PC, for example, sound, video, 3-D, etc, while there may be bindings, the available bindings/libraries can leave a lot to be desired compared to python or mono when you want to build your desktop application, or want to interact with your OS (I can't think of anything offhand in java quite like the os module in python). So while java is a good language, and is relatively easy and consistent to program in (no variation in types across platforms, for example), I wouldn't use it as a first choice for quickly developing a piece of standalone desktop software.

I think eclipse and netbeans are good examples of this. Eclipse in particular is a really featureful and powerful IDE, but it also really bogs down lighter weight systems and has a very bloated and non-standard ui (which to be fair can be customized down somewhat). The same is somewhat true of open office. I dread having java apps on my netbook. I do not dread having python apps on it.

---

### Post by hessiess on 2009-08-28
Don't use Java, use the JVM. There are loads of good languages hoasted on the JVM besides Java itself. ie Clojure, Jruby and Jython.

The JVM can be a lot faster than the original language implementation as it does JIT compilation and a large number of other optimisations.

---

### Post by directhex on 2009-08-28
> **hessiess said:**
> Don't use Java, use the JVM. There are loads of good languages hoasted on the JVM besides Java itself. ie Clojure, Jruby and Jython.

The JVM can be a lot faster than the original language implementation as it does JIT compilation and a large number of other optimisations.

Bear in mind that whilst this is generally true, the JVM is a memory hog. You can similarly host loads of languages on the Mono JITter, where performance will be lower than Sun's JVM - but RAM consumption will be an order of magnitude lower

---

### Post by Reiger on 2009-08-28
Hmm. I would favour the JVM then for my every day needs: I can leave a Netbeans running for days without crashing -- despite the crazy and idiotic exception-prone experiments I throw at it. :P

Seriously, though the thing with the JVM is that it has a very aggressive memory allocation scheme compared to other VM's but it runs otherwise in fairly constant memory space: using Netbeans for example, the actual amount of memory used by Java is almost a constant 300MB. Not bad for a full blown IDE bearing in mind that I also have a C++/Qt app open nearly all the time as well which happily uses another 195MB and will peak much higher once I kick off a few plugins -say a youtube video: my web browser.

---

### Post by directhex on 2009-08-28
> **Reiger said:**
> using Netbeans for example, the actual amount of memory used by Java is almost a constant 300MB.

But still two or three times more than MonoDevelop. See my point?

---

### Post by doas777 on 2009-08-28
> **badperson said:**
> I've always been curious as to why java desktop stuff never really took off. 

the dream of "write once deploy everywhere" turned into "write once debug everywhere"
server apps don;t have that kind of deployment uncertainty so you only have to make sure it runs on your server platform.

---

### Post by doas777 on 2009-08-28
> **directhex said:**
> But still two or three times more than MonoDevelop. See my point?

monodevelop still has a little way to go, but the C# implementation seems to be right on. I have to agree C# is a great answer to the ops quandry

---

### Post by kpkeerthi on 2009-08-31
> **schmendrick said:**
> Interesting to hear this from an experienced Java programmer! What else would you use?

1. Java uses a lot of memory on the desktops, which is not a concern on the server.

2. Swing apps feel heavy and clunky. Part of the reason for this is Swing widgets are 100% Java components. SWT is much better as it emulates a widget only when a native counterpart is not available on the target platform. 

3. They also lack the responsiveness of other native counter parts (GTK+ or QT). 

For desktop development on Linux, I prefer GTK+ and python (pygtk).

---

### Post by raisen on 2009-08-31
Stealing your thread.. is Qt a good GUI framework for multi platforms? Are there any other good alternatives besides Java?

---

### Post by colau on 2009-08-31
> **kpkeerthi said:**
> Thats not true. I've been programming in Java (not toy programs, real world enterprise banking & financial applications that run on UNICES and IBM Mainframes) for 10 years, since 1999. Throw me a python code and I will give you a Java equivalent in half time or less. :)

Now, back to your original question...
It depends. I would not choose Java to develop a desktop application with GUI and such. 

There are areas where Java really shines - Web-based Enterprise Application development - the J2EE umbrella of standards and tools. Python is a no match here.
Why is java not for desktop application?

---

### Post by directhex on 2009-08-31
> **colau said:**
> Why is java not for desktop application?

1) It has an enormous bare-minimum footprint (i.e. you need about a hundred meg of disk space before you can run any Java apps

2) It's utterly abominable at interop with existing C libraries (i.e. if it's not in Java already, then it's pain time)

3) Swing looks like non-native *** and is clunky, alternatives introduce potential issues (e.g. java-gnome has portability issues)

---

### Post by enduser000 on 2009-08-31
If you like python try [pygtk]("http://www.pygtk.org"). It's really nice for cross-platform GUI apps and it's still python! Good luck with your search,

enduser

---

### Post by Shin_Gouki2501 on 2009-08-31
scala is very nice on the jvm :
[http://en.wikipedia.org/wiki/Scala_%28programming_language%29](http://en.wikipedia.org/wiki/Scala_%28programming_language%29)
and jruby too.
You should ask yourelf what you need , long running server precesses( use scala!) or some scriping related work (jruby!).

---

