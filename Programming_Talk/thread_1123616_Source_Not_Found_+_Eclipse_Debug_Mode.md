---
title: "Source Not Found + Eclipse Debug Mode"
date: 2009-04-12
forum: Programming Talk
---

### Post by nova47 on 2009-04-12
I'm trying to debug an error in Eclipse but every time I try to use the debug mode I get the error below saying source not found. There's a few fixes for this under Windows but I haven't been able to find anything for Ubuntu. I included a screen shot below.

[IMG]http://71.65.126.33/shared/eclipse_error.png[/IMG]

---

### Post by myrtle1908 on 2009-04-14
Do you actually have the JSE/JEE source code available on your machine?  Eclipse obviously cannot step into source files that don't exist and that is what the error is indicating.  If you do have the source code then you can configure it within Eclipse (perhaps press that 'Edit Source Lookup Path' button).

As an aside, you really shouldn't need the Java sources as the problem typically exists with your code not the Java library code itself.

---

### Post by nova47 on 2009-04-17
No I don't I'm just trying to get it to step through the execution of my program.

---

### Post by simeon87 on 2009-04-17
> **nova47 said:**
> No I don't I'm just trying to get it to step through the execution of my program.

Although it is possible to attach the original Java source so it can be viewed in Eclipse, in debugging you're trying to debug your own program so you can simply execute the program until it hits a breakpoint in your own code. If an error occurs in code that is outside your program, for example in a standard Java library, it usually means you've passed a wrong argument, such as null when it shouldn't have been null, etc.

---

### Post by VTStevenVT on 2010-05-26
Were you able to fix this, I think I am having the same issue you described.



I created a new eclipse project, made a few classes and set a break point on my main method. The first thing main does is instantiate a few of the classes I made. 

If I try to "step-into" the constructors I get "Source Not Found" and as it tries to step into Launcher.class (part of the jdk). If I hit "step-return", then "step-into" again, it steps into my class properly.

How do I configure eclipse to skip the Launcher.class stuff and just step me into my constructor?

---

### Post by nova47 on 2010-10-20
I didn't really find a solution to my problem but I discovered the cause (which is kind've the solution). I realized it was more a result of me not knowing what I was doing (got a year more of school/programming under my belt so I've gotten a bit smarter :-D). What ends up happening is that the debugger only has access to the source code on the local machine. This means that when you try to step through something like say an output to a file via FileWriter the debugger can't step through the code because it doesn't actually have access to the original source code. So what it does is just tell you the source code is not available. What I do is just skip over any lines of code from sources I didn't write (IE anything you import to use.) A smarter man above basically already said all this, I just didn't understand his response a year+ ago lol

---

### Post by cc0tx on 2011-11-04
nova47, what is the detail about what to do to just skip over any lines of code from sources you didn't write? Is there some setting in Eclipse for this?

---

