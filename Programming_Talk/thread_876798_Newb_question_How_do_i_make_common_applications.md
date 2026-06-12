---
title: "Newb question: How do i make common applications?"
date: 2008-08-01
forum: Programming Talk
---

### Post by Pasty-Flawss on 2008-08-01
I'm new to programming and i was wondering how do i make a common application like lets say... Msn messenger or any other program that you can download.

I know python and I'm using the toolkit Tkinter. Yet when i compile it, it only makes a .py. I know if i use py2exe it will turn it into an exe (im on a windows at the moment). But this still isn't really a proper application.

Maybe i'm going down the wrong path learning python etc. if I want to make applications so i'm asking how do i make applications?

I know the answer is probably easily found through google but i don't know what to search (I have tried)

Thanks.

---

### Post by henchman on 2008-08-01
Well I believe you can write proper applications in python + tkinter :) 

With python you can create GUIs and you have OS independent network access, so you could create your own MSN Messenger :)

Many projects in the Open source world are created with python, especially for ubuntu. But if you mean how to create programs for windows which, for example, can be sold - then i would recommend using C++ with a GUI / All purpose toolkit like Qt, GTK+ or wxWidgets... 

a more easier approach would be using Java - it is ad-hoc compiled when executing the program, just like eg. python, but the java vm is more widespread than the python one.

if you would like to have more specific answers you have to give a more specific question :>

---

### Post by Pasty-Flawss on 2008-08-01
I thought C++ lacked platform independence?

And java's nice but i just cant understand why EVERYTHING has to be in a class? but i might continue to learn that.

But if C++ can write nice windows programs which can be sold then i might continue to learn that.

---

### Post by henchman on 2008-08-01
> I thought C++ lacked platform independence?

well there is such a thing called [c++ standard lib]("http://en.wikipedia.org/wiki/C%2B%2B_standard_library") which "should" be avail on all c++ compilers. If you stick to functions from this library and/or libraries which do the same, then your code will be OS independent, you just have to compile it again for every platform (either in eg. VisualStudio under Windows and G++ under Ubuntu, or [cross compile]("http://en.wikipedia.org/wiki/Cross_compile"))

---

### Post by Pasty-Flawss on 2008-08-01
So it's kind of useless for what i want to use it for if everytime someone downloads it they have to compile it? because the average user has no idea what a compiler is?

By application i mean the many applications that are distributed across the web that you just download install and run. For example Limewire or Msn messenger as i said before

---

### Post by tinny on 2008-08-01
C/C++, Java, Python, C# are all just fine.

The answer to your question will change depending on the problem you are trying to solve.

E.g (just a guide)
Writing a Windows only desktop application = C# or C/C++
Writing a Windows / Linux desktop application = Java, Python
Writing a small Web application = PHP, Python, Java etc...
Writing a banking system = Java, C# 

As a beginner you really first just need to learn the fundamentals, what are data types, functions / methods, data structures etc... These fundamentals are common to all programing languages.

BTW, Tip: You are obviously interested in Linux (thats why your here), so stick with Python if you want to write applications for the Linux desktop. The Linux community are very pro Python.

> 
For example Limewire or Msn messenger as i said before


Limewire, written in Java 
MSN messenger, written in C# I think???

---

### Post by Pasty-Flawss on 2008-08-01
Thanks for your help. tinny :)

I just have one more question. How do i turn a .py into an application like limewire or msn? do i use a toolkit IDE like Tkinter then convert it into an exe(if i wanted windows) with py2exe or something? Because when i compile a python code it just saves it as a .py and someone who downloads it who doesnt have python cant use it?

---

### Post by CptPicard on 2008-08-01
This is once again the strange newbie misconception that a "real application" is some .exe you download of the internet :)

There's nothing wrong with distributing source, and it doesn't make the application any less real. If you want to, you can use py2exe but it is a very suboptimal solution... on Linux, you just make a distribution package for the package manager, and that handles files into correct places and dependencies, such as the python runtime environment.

---

### Post by dje on 2008-08-01
> **Pasty-Flawss said:**
> Thanks for your help. tinny :)

I just have one more question. How do i turn a .py into an application like limewire or msn? do i use a toolkit IDE like Tkinter then convert it into an exe(if i wanted windows) with py2exe or something? Because when i compile a python code it just saves it as a .py and someone who downloads it who doesnt have python cant use it?

the backup app in my sig is just a .py file but it is packaged as a debian package so it looks like a "real application", it installs linbaku.py to /usr/bin

dje

---

### Post by tinny on 2008-08-01
> **Pasty-Flawss said:**
> Thanks for your help. tinny :)

I just have one more question. How do i turn a .py into an application like limewire or msn? do i use a toolkit IDE like Tkinter then convert it into an exe(if i wanted windows) with py2exe or something? Because when i compile a python code it just saves it as a .py and someone who downloads it who doesnt have python cant use it?

I know very little about Python specifically.

But py2exe looks like what you want.

Have you seen this guide?

[http://www.py2exe.org/index.cgi/Tutorial](http://www.py2exe.org/index.cgi/Tutorial)

I just tried it and it works for me! Now im one of those smart Python guys ;)

---

### Post by tinny on 2008-08-01
> **CptPicard said:**
> This is once again the strange newbie misconception that a "real application" is some .exe you download of the internet :)

There's nothing wrong with distributing source, and it doesn't make the application any less real. If you want to, you can use py2exe but it is a very suboptimal solution... on Linux, you just make a distribution package for the package manager, and that handles files into correct places and dependencies, such as the python runtime environment.

I think the OP should replace "real" with "usable by a human without a computer science degree".

---

### Post by Pasty-Flawss on 2008-08-01
Lets say i wanted to write a program for windows (because it is more popular) And it was a simple auto clicker or macro system or some sort of simple program that people might use.

How would i turn a .py into something that can be easily downloaded and installed and run straight from  download (no need to compile anything) like this one for example: [http://www.brothersoft.com/automouseclicker-25176.html](http://www.brothersoft.com/automouseclicker-25176.html)

How would i get this .py into a nice GUI program like this?

---

### Post by Pasty-Flawss on 2008-08-01
> **tinny said:**
> I know very little about Python specifically.

But py2exe looks like what you want.

Have you seen this guide?

[http://www.py2exe.org/index.cgi/Tutorial](http://www.py2exe.org/index.cgi/Tutorial)

I just tried it and it works for me! Now im one of those smart Python guys ;)

I've used py2exe it works kind of alright but when you get all the dlls and tcl into the folder it comes to around 4 mb when compressed. I sent this to a friend and he couldnt open it saying that it was blocked because it is potentialy harmful.

He is a complete noob and there problably was an easy way to unblock it but even still I don't think thats what im looking for

---

### Post by tinny on 2008-08-01
@CptPicard, I think the OP is looking for a professional way to package a Python application for Windows. I guess it doesnt matter if the "installed" result is a *.py.

Is there a Python equivalent of [Advanced Installer - Java]("http://www.advancedinstaller.com/java.html")?

---

### Post by cszikszoy on 2008-08-01
I would look into Mono (c#) and mono-develop.  You can compile programs to be compatible with windows and linux without changing a line of code.  There are videos of someone compiling a program in mono-develop, running it natively on linux, then transferring the executable to a windows machine and running it natively as well.

Mono-develop also provides a visual-studio type of editor that can quickly and easily create GTK applications.

Quite a few people here aren't too fond of Mono, and you'll hear complaints about "microsoft technology", but c# is quite an easy language, and very similar to python.  A couple of ubuntu apps are written in Mono, including Beagle, Banshee, F-Spot and Gnome-Do.

More info here: [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by tinny on 2008-08-01
> 
but c# is quite an easy language, and very similar to python


WOW!

You better edit that post before the "Dynamic Syntax" club come for you! :)

They are similar in the fact that they both involve text and are used to write software.

---

### Post by cszikszoy on 2008-08-01
> **tinny said:**
> WOW!

You better edit that post before the "Dynamic Syntax" club come for you! :)

They are similar in the fact that they both involve text and are used to write software.

lol... let them come!

To a beginner anyways, the differences between the two may not matter as much.  Python is dynamically typed, where c# is more statically typed, but with c# you can do some interesting things such as boxing and unboxing.

This is from wikipedia:
```
int foo = 42;         // Value type.
object bar = foo;     // foo is boxed to bar.
int foo2 = (int)bar;  // Unboxed back to value type.

```

---

### Post by tinny on 2008-08-01
> **cszikszoy said:**
> lol... let them come!

To a beginner anyways, the differences between the two may not matter as much.  Python is dynamically typed, where c# is more statically typed, but with c# you can do some interesting things such as boxing and unboxing.

This is from wikipedia:
```
int foo = 42;         // Value type.
object bar = foo;     // foo is boxed to bar.
int foo2 = (int)bar;  // Unboxed back to value type.

```

A trivial example. Give up! :lolflag: They are WAY different.

---

### Post by cszikszoy on 2008-08-01
> **tinny said:**
> A trivial example. Give up! :lolflag: They are WAY different.

OK I will surrender on only one condition, you read this article: [http://wesnerm.blogs.com/net_undocumented/2005/07/dynamic_typing_.html](http://wesnerm.blogs.com/net_undocumented/2005/07/dynamic_typing_.html)

But either way, I would still advocate learning a statically typed language over a dynamically typed one to a beginner.  It's much easier to find mistakes, and prevent stupid programming errors, such as adding an integer to a boolean by mistake.

---

### Post by CptPicard on 2008-08-01
> **cszikszoy said:**
> 
But either way, I would still advocate learning a statically typed language over a dynamically typed one to a beginner.  It's much easier to find mistakes, and prevent stupid programming errors, such as adding an integer to a boolean by mistake.

You're new here so you probably don't know that this has been discussed to death here, but ... what exactly does static typing really bring to the table especially to a beginner? Just more hurdles to jump across really. A beginner should learn the really important concepts first -- stuff like logic and program flow.

Your addition of boolean and integer will be caught at runtime, and you'll get to fix it then...

---

### Post by cszikszoy on 2008-08-01
> **CptPicard said:**
> You're new here so you probably don't know that this has been discussed to death here, but ... what exactly does static typing really bring to the table especially to a beginner? Just more hurdles to jump across really. A beginner should learn the really important concepts first -- stuff like logic and program flow.

Your addition of boolean and integer will be caught at runtime, and you'll get to fix it then...

I'm certainly not new here.  I've been reading the PT forum about every day for the last year and a half.  I don't post often, but I don't think that makes me "new".  I actually respect most of the things you have to say around PT, so I was a little taken aback by your attempt to insult me.

Either way though, I come from an engineering programming background.  Most of what we (as engineers) learn is statically typed languages, ASM, C, C++.  I've programmed quite a bit in dynamically typed languages recently, specifically perl and php.  I see the advantages, but I feel that beginners sometimes need that rigidity.  Statically typed langauges forces you to think about the variables you are using, and the types of those variables.  It is easy to loose sight of the exact type of a variable in a dynamically typed language.  I understand learning the concepts, but the concept of an int and an uint is just as much at the heart of programming as is a for and while loop.

I don't really want to get into it because I read enough of this in the [[MegaThread] Highlevel v. Lowlevel Programming Languages]("http://ubuntuforums.org/showthread.php?t=851794") thread, which I've been subscribed to for the past 2.5 weeks.

---

### Post by tinny on 2008-08-01
> **cszikszoy said:**
> OK I will surrender on only one condition, you read this article: [http://wesnerm.blogs.com/net_undocumented/2005/07/dynamic_typing_.html](http://wesnerm.blogs.com/net_undocumented/2005/07/dynamic_typing_.html)

But either way, I would still advocate learning a statically typed language over a dynamically typed one to a beginner.  It's much easier to find mistakes, and prevent stupid programming errors, such as adding an integer to a boolean by mistake.

Thanks for posting that article, it promises alot doesnt it! "The End of the Cold War Between Programming Languages", now wouldn't that be nice ;)

---

### Post by cszikszoy on 2008-08-01
> **tinny said:**
> Thanks for posting that article, it promises alot doesnt it! "The End of the Cold War Between Programming Languages", now wouldn't that be nice ;)

If only we could all live in a world of harmony... or something.

---

### Post by tinny on 2008-08-01
> I'm certainly not new here.  I've been reading the PT forum about every day for the last year and a half.  I don't post often, but I don't think that makes me "new".  I actually respect most of the things you have to say around PT, so I was a little taken aback by your attempt to insult me.


Im sure it wasnt meant as a put down. 

> 
Either way though, I come from an engineering programming background.  Most of what we (as engineers) learn is statically typed languages, ASM, C, C++.  I've programmed quite a bit in dynamically typed languages recently, specifically perl and php.  I see the advantages, but I feel that beginners sometimes need that rigidity.  Statically typed langauges forces you to think about the variables you are using, and the types of those variables.  It is easy to loose sight of the exact type of a variable in a dynamically typed language.  I understand learning the concepts, but the concept of an int and an uint is just as much at the heart of programming as is a for and while loop.


I agree with you here. I to feel that the rigidity of statically typed languages is good for beginners. But hey thats just my blue collar programmer opinion.

> 
I don't really want to get into it because I read enough of this in the [[MegaThread] Highlevel v. Lowlevel Programming Languages]("http://ubuntuforums.org/showthread.php?t=851794") thread, which I've been subscribed to for the past 2.5 weeks.


So you would have learnt that to be part of this forum requires thick skin and you not to mention the J word. :) So having said that I really think we should move on before this becomes another ridiculous "MegaThread".

---

### Post by CptPicard on 2008-08-01
> **cszikszoy said:**
> I actually respect most of the things you have to say around PT, so I was a little taken aback by your attempt to insult me.

Gah... seems like everyone is trying to get me infractions these days :p I am rather taken aback at being misinterpreted in this fashion. ;)

No, it was not an attempt at insult, I just looked at your post count and figured that because it's something that has been discussed to death, it is likely you're new enough. That's all. :)

Now, so that nothing is left to be read wrong in this post:

:lolflag: :popcorn: :KS 8-)

EDIT: and to the actual point... yes, I can see where you're coming from with the argument. IMO I prefer removing as much cruft as possible for n00bs, and I'm sure you can appreciate that approach as well.

---

### Post by pmasiar on 2008-08-01
> **Pasty-Flawss said:**
> I've used py2exe it works kind of alright but when you get all the dlls and tcl into the folder it comes to around 4 mb when compressed. I sent this to a friend and he couldnt open it saying that it was blocked because it is potentialy harmful.

Don't bother with py2exe. ActiveState has nice professional Python installer, which "just works" (tm). Rest of your installer could be (for simple app) just unzip code, or install libraries using ez_install.py. 

EasyGUI is **the** simplest GUI on the market. Or learn pygame and do some simple games.

---

### Post by mssever on 2008-08-01
> **cszikszoy said:**
> I've programmed quite a bit in dynamically typed languages recently, specifically perl and php.  I see the advantages, but I feel that beginners sometimes need that rigidity.  Statically typed langauges forces you to think about the variables you are using, and the types of those variables.  It is easy to loose sight of the exact type of a variable in a dynamically typed language.
I don't know Perl, but I do know PHP. PHP's type system is a mess. It's a poor example of what dynamic typing could be. See Ruby and Python for much better examples. Besides, in Ruby, who cares if some number is a Fixnum or a Bignum? From a practical point of view, it doesn't matter at all. It's simply an internal implementtion detail. That's what duck typing is all about.

---

### Post by pmasiar on 2008-08-01
> **cszikszoy said:**
> OK I will surrender on only one condition, you read this article: [http://wesnerm.blogs.com/net_undocumented/2005/07/dynamic_typing_.html](http://wesnerm.blogs.com/net_undocumented/2005/07/dynamic_typing_.html)


I did, so surrender now. :-)

One obvious problem with that approach is, why we need type info: for performance, right? So providing type info should be optional, for parts where we need performance - and even then, it is more reliably inferred at runtime.


> But either way, I would still advocate learning a statically typed language over a dynamically typed one to a beginner.  It's much easier to find mistakes, and prevent stupid programming errors, such as adding an integer to a boolean by mistake.

You confuse weak typing with dynamic typing.

Perl and Javascript are weakly types, and will cast incompatible types to compatible for such operations. Python will report an error, because it is strongly dynamically typed.

Type info adds little safety for price of huge inconvenience, code like:

```

ArrayList snpFields = new ArrayList();
HashMap oldRow = (HashMap) resIter.next();
String oldSnps = oldRow.get("SNPS").toString();

```

How much simpler could Java be if they thought of "typecasting assignment", casting right side to known type of left side:

```

ArrayList snpFields := new();
HashMap oldRow := resIter.next();
String oldSnps := oldRow.get("SNPS");

```

---

### Post by Pasty-Flawss on 2008-08-01
> **cszikszoy said:**
> I would look into Mono (c#) and mono-develop.  You can compile programs to be compatible with windows and linux without changing a line of code.  There are videos of someone compiling a program in mono-develop, running it natively on linux, then transferring the executable to a windows machine and running it natively as well.

Mono-develop also provides a visual-studio type of editor that can quickly and easily create GTK applications.

Quite a few people here aren't too fond of Mono, and you'll hear complaints about "microsoft technology", but c# is quite an easy language, and very similar to python.  A couple of ubuntu apps are written in Mono, including Beagle, Banshee, F-Spot and Gnome-Do.

More info here: [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

Sweet, looks like what i'm looking for. I'll give it a go. I already know a fair amount of C++ and i heard C# is similar.

---

### Post by tinny on 2008-08-01
> 
> But either way, I would still advocate learning a statically typed language over a dynamically typed one to a beginner. It's much easier to find mistakes, and prevent stupid programming errors, such as adding an integer to a boolean by mistake.


:shock: Herritic :lolflag:

---

### Post by cszikszoy on 2008-08-01
> **Pasty-Flawss said:**
> Sweet, looks like what i'm looking for. I'll give it a go. I already know a fair amount of C++ and i heard C# is similar.

C# is quite similar, think c++ without pointers, essentially.  I mean it's more complicated than that, but that was one of the main goals of the c# project.

Although, I can't say I'm particularly fond of this ostracization of pointers (refer to what I said earlier about coming from an engineering programming background).

---

### Post by Pasty-Flawss on 2008-08-02
Mono's great. But i've got this huge bug. When i'm editing the GUI when i make a menu bar and then make a new menu it crashes when i save. Do you know how to resolve this?

---

### Post by LaRoza on 2008-08-02
> **cszikszoy said:**
> C# is quite similar, think c++ without pointers, essentially.  I mean it's more complicated than that, but that was one of the main goals of the c# project.

C# is more like Java with pointers. C# was meant to compete with Java because Microsoft was unable to get a (death) grip on Java (and was successfully sued for trying)

---

