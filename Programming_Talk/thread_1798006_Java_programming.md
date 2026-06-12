---
title: "Java programming"
date: 2011-07-05
forum: Programming Talk
---

### Post by Drenriza on 2011-07-05
I'm intersted in learning a program that is cross platform (windows, os x, linux) in where i can make programs, scripts, and can work with HTML.

So i stumbled upon Java. So far it seams to have what i look for, and thats how i ended up here.

Is their anyone who know some good java PDF,s explaining basics on getting started with Java. I've spent some time with C# (.NET), but it's not really cross platform. Linux you need Mono and don't think their is a solution for OS X.

Also if any know some good tutorials on Netbeans (the IDE i use) or online java tutorials don't hesitate to throw in a link :p

Thanks all on advance.
Kind regards.

---

### Post by Simian Man on 2011-07-05
> **Drenriza said:**
> I've spent some time with C# (.NET), but it's not really cross platform. Linux you need Mono and don't think their is a solution for OS X.


Not so!  Mono runs fine on OSX and is very well supported on Linux with a great IDE (Monodevelop) and bindings to most major Linux APIs.  Since you already know C#, and it's a more powerful language, I'd suggest sticking with that.

---

### Post by pafoo on 2011-07-05
If I was you, I would go with python. They come pre-installed on all *nix OS's and can do everything that you want. I have been getting the impression that java is going the way of the dinosaur, tho im sure alot of java programmers would disagree! Plus after coming from
C# you might find you will love the nice breath of fresh air with python's readability. PLUS your not paying homage to Oracle =)

---

### Post by stchman on 2011-07-05
I say go with Java.  It's a great language that does so much.

Java 6 API
[http://download.oracle.com/javase/6/docs/api/](http://download.oracle.com/javase/6/docs/api/)

I use Netbeans and it is a very good IDE.  Since you have had some experience with C#, Java will be a really good fit.

---

### Post by stchman on 2011-07-05
> **pafoo said:**
> If I was you, I would go with python. They come pre-installed on all *nix OS's and can do everything that you want. I have been getting the impression that java is going the way of the dinosaur, tho im sure alot of java programmers would disagree! Plus after coming from
C# you might find you will love the nice breath of fresh air with python's readability. PLUS your not paying homage to Oracle =)

No way is Java going away.

Problem with Python is it's interpreted while Java is compiled.  There is a huge speed difference in computational power between an interpreted and compiled language.

As far as readability I find Java more readable, but that is just an opinion.

---

### Post by pafoo on 2011-07-05
> No way is Java going away.

Problem with Python is it's interpreted while Java is compiled.  There is a huge speed difference in computational power between an interpreted and compiled language.

As far as readability I find Java more readable, but that is just an opinion.

Well you cant forget that pretty much all of pythons built in modules are built in C for that speed issue :)

IMHO unless you are building a HUGE program, with today's standard resources I don't see interpreted languages being as much of an issue as they were 5-10 years ago. Some python programmers even say that it can easily be used for those large projects. But that debate is above my head

---

### Post by cgroza on 2011-07-05
> **stchman said:**
> No way is Java going away.

Problem with Python is it's interpreted while Java is compiled.  There is a huge speed difference in computational power between an interpreted and compiled language.

As far as readability I find Java more readable, but that is just an opinion.
Java is interpreted, it is compiled to bytecode which is then interpreted to a virtual machine.
Same goes with Python, the interpreter generates bytecode automatically, although you can specify it to do it.

---

### Post by jmartrican on 2011-07-05
Drenriza,

There is tons of free information online.  Instead of concentrating on learning, concentrate on accomplishing a project.  You will learn along the way, it is the best way to learn.  

you can start with this....
[http://download.oracle.com/javase/7/docs/api/index-files/index-1.html](http://download.oracle.com/javase/7/docs/api/index-files/index-1.html)
of for java 6
[http://download.oracle.com/javase/6/docs/api/index-files/index-1.html](http://download.oracle.com/javase/6/docs/api/index-files/index-1.html)

Netbeans IDE is pretty cool.  That is what I use.  I have not tried Eclipse.  I was so impressed with netbeans (coming from vi) that I just stuck with it... I should try others.  Its got a learnign curve but as long as you are getting your hours of programming in and working on a project, you will grow and get better and better.

thanks
jose

---

### Post by Drenriza on 2011-07-06
Thanks for all the great replies.

So this mean, if i program something in C# .net or ASP.NET then i can port it to a linux platform. Would i be able somehow to create a .deb package then?

---

### Post by Drenriza on 2011-07-06
Anyone who can tell me what the pros and cons are C# ASP.NET versus Java?

That would be terrific.

---

### Post by PaulM1985 on 2011-07-06
For standard desktop app development, I don't really see too much difference between the two.  I use C# at work and Java at home.  I am fine with both.

One advantage of C# is being able to use it with C++.  There are ways of calling C++ code from C#, which means that there are loads of libraries available to you.  It can be really useful if you want to use a library and there are C++ versions but no C# versions.

As for web development, I like using Java and JSP.  I don't know of the C# equivalent.

Paul

---

### Post by Simian Man on 2011-07-06
> **cgroza said:**
> Java is interpreted, it is compiled to bytecode which is then interpreted to a virtual machine.
Same goes with Python, the interpreter generates bytecode automatically, although you can specify it to do it.
Any decent Java implementation these days uses Just In Time compilation to compile the byte code to machine code.  This does give it a speed advantage over Python which, as far as I know, is interpreted.

> **Drenriza said:**
> Anyone who can tell me what the pros and cons are C# ASP.NET versus Java?
One advantage of C# is that you already know it.  Another is that it is very well supported on Linux and a lot of great Linux applications are written in C# like Banshee, F-Spot, Gnome-Do, Pinta, and Tomboy.

C# also has lots of language features that Java does not have like operator overloading, structs, tuples, properties, default parameters, and lambda functions.

Also, in my opinion, the .Net framework is a much better designed class library than Java's.  For an example, just look at how complicated it is to read from stdin in the two languages :).

I don't know much about the web side of things either.  I've just used PHP for the limited web stuff I've done.  But for general purpose programming, C# beats Java hands down in my opinion.

---

### Post by cgroza on 2011-07-06
> **Simian Man said:**
> Any decent Java implementation these days uses Just In Time compilation to compile the byte code to machine code.  This does give it a speed advantage over Python which, as far as I know, is interpreted.
.
Python has a JIT implementation too (Psyco, PyPy), I think the static typing of java is a major factor for it's speed.

---

### Post by Drenriza on 2011-07-06
So lets say i write a program / script in C# on my laptop or desktop computer. What is necessary on a Linux machine to be able to run the program?

I found something here [http://mono-project.com/DistroPackages/Debian](http://mono-project.com/DistroPackages/Debian) but i dont know if this is the part of Mono that allows me to execute a C# program on a Linux machine.

Can you start a C# program / script in the cron job? Or do you need a bash script to be in the cron job that then calls the C# program / script.

Thanks on advance.

---

### Post by cgroza on 2011-07-06
Yes, you need mono, which is the open source implementation of C#.

Not familiar with cron jobs but I am sure it is possible, with a little help from bash.

---

### Post by pafoo on 2011-07-06
You can run any script you want in cron. As long as you specify the interpreter in the script or in cron.

If you want to just run the script with our calling the interpreter just enter it in the 1st line of the script.

ex 

#!/usr/bin/python or #!/usr/bin/perl

example cron entry

01 05 * * * /usr/bin/python pythonrules.py 1>/dev/null 2>&1

which will run the script at 5:01am. everyday.

I hope your installing all this 3rd party programming stuff only on a home box  =)

---

### Post by Drenriza on 2011-07-07
> **pafoo said:**
> 

#!/usr/bin/python or #!/usr/bin/perl

example cron entry

01 05 * * * /usr/bin/python pythonrules.py 1>/dev/null 2>&1

which will run the script at 5:01am. everyday.

So how would you call the script, if it was a C# program?
01 05 * * * /usr/bin/mono program.exe 1>/dev/null 2>&1  ???

What do you mean with > I hope your installing all this 3rd party programming stuff only on a home box  =) Why wouldnt you install mono on a server? To understand the .NET framework. So far i've just installed mono dev on my local machine.

---

### Post by Drenriza on 2011-07-07
Curious.

Lets say that i program something in C# for Linux. And all of a sudden i need to execute a Linux command from C#, written in C or C++ or other. Is that possible? If so, how do you do so?

---

### Post by PaulM1985 on 2011-07-07
I think this is the sort of thing you are looking for.
[http://www.dreamincode.net/forums/topic/31107-system-calls-in-c%23-the-2nd/](http://www.dreamincode.net/forums/topic/31107-system-calls-in-c%23-the-2nd/)

Beware, if you are looking to use linux system calls, you are going to lose your cross compatibility.

If there is a specific library you want to use that has been written in C/C++ you could write managed C++ wrapper to use it.

What sort of things where you looking to call?

Paul

---

### Post by Drenriza on 2011-07-07
Not 100% what to call.

But can you from C# call Linux commands/scripts written in bash or awk. Let them run and take their output and import it to C#, to handle it?

Or from C# execute a C++ or C script / command, and take the output the C++ or C script / command gives, import it to C#, to handle it?

Im couries to know if C# can, "communicate (execute other language scripts) " with other languages then just itself. Dont know if you know what i mean, kinda hard to set words on.

---

### Post by nvteighen on 2011-07-07
> **Drenriza said:**
> Not 100% what to call.

But can you from C# call Linux commands/scripts written in bash or awk. Let them run and take their output and import it to C#, to handle it?

Or from C# execute a C++ or C script / command, and take the output the C++ or C script / command gives, import it to C#, to handle it?

Im couries to know if C# can, "communicate (execute other language scripts) " with other languages then just itself. Dont know if you know what i mean, kinda hard to set words on.

I don't know anything about C#, but if C# has some procedure called system() (or whatever) that runs shell commands, then you can run anything that runs on a shell.

But using such a solution is usually the least recommended one. Usually, the best is to get a library that does the job (and most programs in the FOSS world are written as a backend library called by some frontend). You may get some issues to find true C# libraries given the bad reputation of the language (you know, MS...) so you may have to get either bindings or implement bindings for C and C++ libraries (How good is C#'s Foreign Function Interface?). If no libraries are available, you could use the POSIX API to communicate with another process via a pipe (which gives some control, but not to the extent of an API) or using the equivalent to C's system() to execute a program in a new shell (but renouncing to any forms of communication save getting the program's exit code).

---

### Post by PaulM1985 on 2011-07-07
Like I said earlier.

Step 1: Get the C/C++ library.
Step 2: Write a wrapper for it ([http://en.wikipedia.org/wiki/Managed_Extensions_for_C%2B%2B](http://en.wikipedia.org/wiki/Managed_Extensions_for_C%2B%2B) [http://en.wikipedia.org/wiki/C%2B%2B/CLI](http://en.wikipedia.org/wiki/C%2B%2B/CLI)) in managed C++.
Step 3: Call your wrapper from C#

Paul

EDIT:
I have done this sort of thing quite a few times at work so that I can use our old libraries with our new C# code.

---

### Post by Drenriza on 2011-07-07
> **PaulM1985 said:**
> Like I said earlier.

Step 1: Get the C/C++ library.
Step 2: Write a wrapper for it ([http://en.wikipedia.org/wiki/Managed_Extensions_for_C%2B%2B](http://en.wikipedia.org/wiki/Managed_Extensions_for_C%2B%2B) [http://en.wikipedia.org/wiki/C%2B%2B/CLI](http://en.wikipedia.org/wiki/C%2B%2B/CLI)) in managed C++.
Step 3: Call your wrapper from C#

Paul

EDIT:
I have done this sort of thing quite a few times at work so that I can use our old libraries with our new C# code.

Im glad for your experience. But im very noob at coding. When you say words like wrapper, i'm like O.o with a pinch of ":( me no comprende"

So if you have links to all of this, i would be very glad. 
And yes i see the two wrapper links :p

---

### Post by Simian Man on 2011-07-07
Drenriza, what exactly do you want to do?  You can run other commands with "System.Diagnostics.Process.Start("whatever");" (though this is not portable and rarely done in practice).  There are lots of [Mono bindings]("http://www.mono-project.com/Libraries") already in existence for libraries you may need.  You can also interact with other applications using D-Bus.

It is very unlikely that you will need to write bindings yourself when you're just starting out :).

---

### Post by Drenriza on 2011-07-07
> **Simian Man said:**
> Drenriza, what exactly do you want to do?  You can run other commands with "System.Diagnostics.Process.Start("whatever");" (though this is not portable and rarely done in practice).  There are lots of [Mono bindings]("http://www.mono-project.com/Libraries") already in existence for libraries you may need.  You can also interact with other applications using D-Bus.

It is very unlikely that you will need to write bindings yourself when you're just starting out :).

Thanks for the info.

I don't want to do something specific. I'm just trying to figure out what my options are :p

---

### Post by PaulM1985 on 2011-07-07
When I say "write a wrapper", this means write the bit of code in between the C++ lib and your C# app.

Say you have a C++ lib which contains a class called MyClass with functions A(), B() and C() in it.

You would create a managed C++ library and include your C++ lib as a dependency.

In your managed C++ library you would create a class called MyClassManaged which would look something like this:

```

#pragma once
#using <mscorlib.dll>

// includes for your library

__gc class MyClassManaged
{
public:
	MyClassManaged()
        {
            m_pMyClass = new MyClass();
        }

	~MyClassManaged()
        {
            delete m_pMyClass;
        }

        void A()
        {
            m_pMyClass->A();
        }

        void B()
        {
            m_pMyClass->B();
        }

        void C()
        {
            m_pMyClass->C();
        }
private:
	MyClass* m_pMyClass;
};

```

You can then use MyClassManaged in C#, allowing you to use the C++ MyClass.

What do you want to do?  Like Simian Man says, your library probably already exists.  I wouldn't recommend doing anything like this unless you need to.  Look around and make sure that the lib definitely doesn't exist before you do this.

Paul

---

