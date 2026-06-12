---
title: "how to make my java program to .exe file."
date: 2009-07-16
forum: Programming Talk
---

### Post by detorresrc on 2009-07-16
Hi any one there can help me how to make my java program to become .exe file.

---

### Post by lisati on 2009-07-16
I suggest you stand by for comments to the effect that the ".exe" file format is intended for MS-DOS and Windows.

Having gotten that off my chest, by ".exe" file do you mean a stand-alone "executable" file?

p.s. I'm not a Java guru, so someone else might have to answer this.

---

### Post by detorresrc on 2009-07-16
Yes i need to make as executable file, for the deployment of my application.

---

### Post by Finalfantasykid on 2009-07-16
You could try making an executable .jar for your Java project.  That way people can just double click on the .jar file, and it will execute(though this oddly does not work for me in ubuntu :( )

EDIT:  You could also compile a super simple c/c++/.bat program, where all it does is execute the command > java -jar myprogram.jar

---

### Post by cdiem on 2009-07-16
Some of these tools: [http://viralpatel.net/blogs/2009/02/convert-jar-to-exe-executable-jar-file-to-exe-converting.html](http://viralpatel.net/blogs/2009/02/convert-jar-to-exe-executable-jar-file-to-exe-converting.html)
may be of use for you. Or maybe something like Launch4J ([http://launch4j.sourceforge.net/](http://launch4j.sourceforge.net/)). I have never used such tools, so maybe someone who has experience with them can give you a better advice (regarding which tool is better, etc).

---

### Post by c0mput3r_n3rD on 2009-07-16
The whole idea of Java is that it's platform dependent.  It runs off of the Java platform.  That's why to see the web applications or any where you might see it you need Java installed on your computer.  If you want to be able to make stand alone executable files you need find another language like C++.

---

### Post by dwhitney67 on 2009-07-16
> **c0mput3r_n3rD said:**
> ...
If you want to be able to make stand alone executable files you need find another language like C++.

Or use the Java JIT (Just In Time) compiler.  See [here]("http://www.java-tips.org/java-se-tips/java.lang/what-is-java-just-in-time-compiler.html") for a brief explanation.

In such case though, the application would suffer portability problems.

---

### Post by doas777 on 2009-07-16
'fraid you can't

---

### Post by Maheriano on 2009-07-16
You have a few options if you want an executable file, but if you want .exe specifically then no you can't. But why .exe anyway, what's the point? Here are your options if you're looking for an executable file type:
1. Create an executable .jar like someone mentioned.
2. You can execute Java files from the command line with the command line compiler javac. Just run "javac <c:\program\location\programname.java>". So if you put that line into a bat file, you can then double click on the .bat file and it'll run the Java program. You can even assign a custom icon to the .bat file so it looks presentable.

---

### Post by c0mput3r_n3rD on 2009-07-16
> **Maheriano said:**
> You have a few options if you want an executable file, but if you want .exe specifically then no you can't. But why .exe anyway, what's the point? Here are your options if you're looking for an executable file type:
1. Create an executable .jar like someone mentioned.
2. You can execute Java files from the command line with the command line compiler javac. Just run "javac <c:\program\location\programname.java>". So if you put that line into a bat file, you can then double click on the .bat file and it'll run the Java program. You can even assign a custom icon to the .bat file so it looks presentable.


You still need to java platform though. Or am I mistaken?

---

### Post by doas777 on 2009-07-16
> **c0mput3r_n3rD said:**
> You still need to java platform though. Or am I mistaken?

there si no way to run an intrepreted langague (java, python, C# etc) without a runtime installed. it;s like trying to run a mips compiled C app on an Alpha architecture.

---

### Post by c0mput3r_n3rD on 2009-07-16
Right.  So then making an executable Java program is the same is running
```

vi program.pl
#!/usr/bin/perl
:wq
chmod u+x program.pl
./program.pl

```

Java can only be as executable as that and I think that answer his question.

---

### Post by Dougie187 on 2009-07-16
What about this?

[http://www.devx.com/getHelpOn/10MinuteSolution/20430](http://www.devx.com/getHelpOn/10MinuteSolution/20430)

I have heard of compiling java into machine code before, rather than byte code. Apparently you can do this with gcj, a java wrapper for gcc. Which is in the repos if you want to use it.

Also here is another example.

[http://www.chuckcaplan.com/blog/archives/2005/07/gcj_compile_jav.html](http://www.chuckcaplan.com/blog/archives/2005/07/gcj_compile_jav.html)

Hope this helps.

---

### Post by CptPicard on 2009-07-16
It should be pointed out that in most cases, the desire to create standalone .exe's out of Java applications is the wrong way to go and just shows that it has not been properly understood how Java application installation and launching should properly be dealt with. Namely, you want to create an executable .jar or an installer that sets up appropriate launchers that run the java command...

---

### Post by Dougie187 on 2009-07-16
Well, perhaps someone writing java code really wants to compile it to machine code to get the benefit of not having to run the code in java's byte code intrepreter.

Either way, there are some benefits to be talked about in compiling java into machine code, and a standalone exe as opposed to a standard jar file. But there are some benefits to using a jar file as well.

Personally, I think it all depends on the use of the code.

---

### Post by CptPicard on 2009-07-16
> **Dougie187 said:**
> Well, perhaps someone writing java code really wants to compile it to machine code to get the benefit of not having to run the code in java's byte code intrepreter.

What is this "byte code interpreter" you speak of? :)

[http://en.wikipedia.org/wiki/Just-in-time_compilation](http://en.wikipedia.org/wiki/Just-in-time_compilation)

I fail to see much benefit in introducing what is essentially a portability problem with no obvious gain in sight.

---

### Post by Dougie187 on 2009-07-16
Maybe if the OP gets some free time some benchmarks would be interesting. I as well have never tried doing this, however I have heard from others that it speeds up java's runtime when compiled to machine code. I heard it was comparable to c/c++ once compiled to machine code. 

Either way, I was just giving him his answer, most people just said it was impossible. But I agree that it is a portability disaster, but that happens a lot. He might have a specific reason he wanted to know how to do this, and just didn't clarify it.

EDIT: BTW, I appreciate your correction. :)

---

### Post by HotCupOfJava on 2009-07-17
Applications such as JSmooth, Launch4J, and IzPack are wrapper utilities that turn your JAR into a file with the ".exe" extension on a Windows machine. They still locate and launch the JVM. On Macs, you can use MRJAppBuilder.

I have personally never used these for these reasons:

On Windows, the files with the ".jar" extension will automatically launch when double-clicked with the javaw -jar command (so you don't see a shell window).

I haven't deployed any java apps on a Mac.

On Linux, I create a simple shell script that navigates to the JAR's directory and executes the -jar command for me. I use the fully qualified pathname instead of a relative pathname, so I can launch the JAR regardless of what directory I might move the script to.

---

### Post by c0mput3r_n3rD on 2009-07-17
All-in-all.  C++ is the way to go :)

---

### Post by jespdj on 2009-07-17
> **c0mput3r_n3rD said:**
> All-in-all.  C++ is the way to go :)
Not always. If you want to write software that runs on any OS without the need to recompile it, Java would be a good choice and C++ is obviously the wrong choice.

---

### Post by nvteighen on 2009-07-17
It's completely absurd... One of the main advantages of Java is to be a highly portable programming platform (not only language) and you just want to get rid of that advantage because of the "executable fetishism". If you want a standalone executable, you have to get into platform-dependency... If you want platform-independency, you have to trade it off for depending from a virtual machine.

---

### Post by NielsBhor on 2009-07-17
Java needs JVM. Essentially, it will not run as executable. JAVA was intended to be portable.

However, JVM is different from one OS to another in term of operating. There's no need to inundate your mind in learning how to build your own programming language. I'll tell you what. Java is actually built from C++. The founders just want a way to run programs without having to re-write the whole code for different OS. As long as the machine has JVM, the JAVA code will not need be modified.

---

### Post by CptPicard on 2009-07-17
> **NielsBhor said:**
> Java is actually built from C++.

I was under the impression the native parts of the Sun JDK are in C?

Then again, this seems to be a reincarnation of the argument that higher-level languages would actually derive their features straight from some kind of lower-level "host" language, kind of piggybacking on them... think about you can get laziness for free into your random language by implementing it in Haskell, and using Haskell's lazy evaluation mechanism. It doesn't really work that way -- for example, Java's classes aren't C++ classes underneath etc...

---

### Post by c0mput3r_n3rD on 2009-07-17
> **jespdj said:**
> Not always. If you want to write software that runs on any OS without the need to recompile it, Java would be a good choice and C++ is obviously the wrong choice.

You know, I've come to see that you either like Java, and not C++, or you like C++, and not Java.  I'm sure their are people that don't fit my stereotype, but from what I've seen.  
I wnat to learn more Java.  I started picking it up and got really frustrated by how hard it was to read in user input!

---

### Post by HotCupOfJava on 2009-07-17
There is always some issue, regardless of which language you prefer. Obviously, I like Java. But, I recently wrote an application that uses the Apache Derby embedded database driver (which is implemented in Java). A recent update placed the derby.jar file in a new directory, which made the classpath I had listed in the app's manifest wrong. I had to rebuild the jar and redeploy to fix it. Not a terribly difficult thing, but annoying.

---

### Post by Dougie187 on 2009-07-18
I really don't think this ia very absurd. I mean, you don't even know what he wants to do with the code. He probably gave up reading this thread a long time ago after everyone said "It's impossible". Maybe has has a really good reason for wanting to do this. Either way, I could imagine it depending on the use of the code. Maybe he doesn't give a crap about portability, or platform independance.

---

### Post by SKLP on 2009-08-13
Why not use IKVM (ikvmc) and make your .jar into a .NET assembly (.exe)? ;-)
[http://www.ikvm.net/](http://www.ikvm.net/)

---

