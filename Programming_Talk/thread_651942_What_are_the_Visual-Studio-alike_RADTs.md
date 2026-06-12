---
title: "What are the Visual-Studio-alike RADTs?"
date: 2007-12-28
forum: Programming Talk
---

### Post by Majorix on 2007-12-28
Language doesn't matter, I am here to learn. I want ease of use. Like code completion (even with the GUI and all other libraries), auto-indentation, and integrated GUI designer. Just like VS for M$. I have left M$ yesterday completely, hence the request :)

---

### Post by Klipt on 2007-12-28
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)

Look for those which give their platform as 'cross platform' or 'Linux'.

---

### Post by samjh on 2007-12-28
Netbeans: [www.netbeans.org](www.netbeans.org) is the closest thing I can think of.

---

### Post by Majorix on 2007-12-28
> **Klipt said:**
> [http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)

Look for those which give their platform as 'cross platform' or 'Linux'.

That's a nice site, however there is no info on whether or not they have code-completion, GUI builder etc. Am I missing something?

> **samjh said:**
> Netbeans: [www.netbeans.org](www.netbeans.org) is the closest thing I can think of.

Why couldn't I think of it! NetBeans is a great idea! Thanks a lot. What languages can be developed in NetBeans 6.0 (and is there a deb package for that latest version) besides Java and Ruby?

Coming from a C background, and having read like 100 pages through the official Java tutorial I know most of the syntax of Java. However I need to sharpen on my knowledge of the libraries that come with it. What should be done, if anything, to get NetBeans to use Java 1.6 as the compiler/interpreter?

Also knowing Python and having read (again) like 100 pages through Programming Ruby from Pragmatic Programmers (I still have the book so I could read it more if need be) I know some of the Ruby syntax. But again the library knowledge is not very large.

But this is why I want auto completion. It's a tool that greatly reduces development time and greatly eases the work for the programmer. You don't have to memorize everything, like, you would start typing static and it would show you StaticText even though you have not even followed case convention. You can then learn many languages and not worry about libraries anymore.

Integrated GUI building is a tool I want, because it also is a programmer's best friend (sorry Ruby :p), I couldn't live without a GUI builder.

Finally, about the auto indentation, I want it because it is a tool that simplifies copy-pasting (stealing :p) code with just a click. It also helps untidy people :D

---

### Post by samjh on 2007-12-28
Netbeans can also be used for C, C++, and PHP.

For C/C++, download the C/C++ edition.  Otherwise, get the Java SE edition, then after installing Netbeans, fire it up and go to Tools -> Plugins, and select the C/C++ plugin to install it.

Take note that the Matisse GUI builder is only for Java Swing.

---

### Post by Majorix on 2007-12-28
Ouch. Seems I will be using it for Java development only then.

I am planning to download NetBeans from the repos. What exactly is the name there (as there seem to be several editions of it) and will it be using the 1.6 JDK by default or do I have to change some config?

Thanks for the interest.

---

### Post by samjh on 2007-12-28
Don't bother with the repos.

Just download from the Netbeans website.  The installer will do everything, including adding a launcher on your desktop and the Applications -> Programming menu (it also creates an *un*-installer in the installed directory for future use).  Make sure you have the sun-java6-jdk package installed *before* installing Netbeans. :)

---

### Post by Majorix on 2007-12-28
Ah, so NetBeans will use that Java-SDK? I know I am too cheap :p But I am asking this question because no matter what I did in the past I couldn't get the actual Java-SDK on my system to work with Eclipse, so I had to go with Gedit. I don't want that to happen again :)

---

### Post by MicahCarrick on 2007-12-28
If C# and .NET languages happen to be your flavor, check out monodevelop. It's one of the better native IDEs for Linux I've seen: [http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page)

That would be for use with C# and GTK primarily. Since I'm mostly a GTK+ man, I can't vouch for Java or Qt IDEs. But as far as GTK goes, that's probably the most VS like you'll find.

---

### Post by Majorix on 2007-12-28
I need a "hard" tutorial on the UI of that MonoDevelop thingy though. I couldn't even place a damn button in it in my last futile attempts :)

EDIT: This actually reminded me of IronPython. I am also looking in that.

In an effort not to bump the topic, here is another EDIT: I forgot MonoDevelop doesn't provide the auto-complete facility. I guess my best bet is Java and Netbeans. I have already installed it and will have a look after the dinner.

---

### Post by samjh on 2007-12-28
> **Majorix said:**
> Ah, so NetBeans will use that Java-SDK?

In my experience, yes. :)

---

### Post by Majorix on 2007-12-29
Thanks for all your help samjh.

I got NetBeans and Java 1.6 to work after a bit of work. I first got some "cannot find symbol" errors but I solved it.

I will now read the rest of the Java Tutorial.

Thanks again :)

---

### Post by Klipt on 2007-12-30
> **Majorix said:**
> EDIT: This actually reminded me of IronPython. I am also looking in that.

For Python RAD also consider Boa-Constructor.

---

### Post by Majorix on 2007-12-30
> **Klipt said:**
> For Python RAD also consider Boa-Constructor.

Boa Constructor didn't used to work on my Ubuntu. I have only recently installed Xubuntu and haven't tried Boa Con. on it yet. I am currently downloading in the background, and will edit this post to let you know how it went.

EDIT: It still doesn't work :(

---

### Post by quedigg on 2007-12-30
Majorix, I don't advice leaving MS stack , M$ is the easiest way to get $$ ,MonoDevelop is still not a competitor even mono is not a full implementation for .NET , so i strongly recommend the following :
[LIST=1]
[*]Groovy (scripting under JVM, stuck with Intellij IDE)
[*]Python (irrestable ! , Eric4 is one of the best IDEs
[*]Ruby (for web ,plenty of IDEs, NetBeans 6 is the best)
[*]C#-Mono (please do not expect the .NET monster here, but may be not that bad )
[/LIST]

thx

---

### Post by Majorix on 2007-12-30
Honestly, I don't neglect leaving M$. The only good thing for development it offered to me was VS, and I lately found out that NetBeans on Linux can pretty much do the same. And Java is the widest used programming language, so yeah...

I have never looked into Groovy, but I will check it.

I know Python, although I wouldn't call myself an expert.

I know rookie level Ruby.

C# I used to know quite well. That's what I used to work with on M$ VS. I have however lately become a little rusty. I have to skim through a tutorial to remember the things I used to know. But I don't like MonoDevelop, as it's very poor compared to VS, and doesn't offer code-completion (which is a big minus in my consideration). I hope they can improve it.

---

### Post by quedigg on 2007-12-30
i totally agree, C# is volatile and  you will never keep track on it , i think the intellisense  (code-completation) is very bad for migrating developers, you just get addicted to it :(

---

### Post by Klipt on 2007-12-31
> **Majorix said:**
> Boa Constructor didn't used to work on my Ubuntu. I have only recently installed Xubuntu and haven't tried Boa Con. on it yet. I am currently downloading in the background, and will edit this post to let you know how it went.

EDIT: It still doesn't work :(
Did you install it from the universe repositories? If so there must be someone you can ask on the Boa or Ubuntu dev sides to fix it...

Boa has code completion and form designer ... the only thing missing from your list is auto reindentation, since Python's indentation is fixed ;)

---

### Post by Majorix on 2007-12-31
Yes I installed it from the repos.

I would file a bug, but I don't know exactly how to. And since it is only a bug that affects a development environment I don't think they would mark it as "important" or something.

Anyways thanks a lot.

---

