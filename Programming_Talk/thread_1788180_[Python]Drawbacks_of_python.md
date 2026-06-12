---
title: "[Python]Drawbacks of python"
date: 2011-06-22
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
No offence to python lovers...actually i am quite a python lover myself...but i wanted to know are thre any serious drawbacks of python which may drag it behind in the race of best programming language... :)

---

### Post by NovaAesa on 2011-06-22
It's very slow compared to some other languages, especially compiled languages such as C, C++, and Java.

---

### Post by GenBattle on 2011-06-22
Speed; due to it's interpreted nature python is fairly slow. Projects like PyPy aim to change this, but for the most part it's definitely one of the slower languages.

Fragmentation; just browse through a range of Python libraries and you'll find some still using python versions as old as 2.4, while others work with 2.6 or 2.7, and some even support 3.0 or 3.1.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
Its not that slow....yes because it is an interpreted language it is slow...but come on....i wont call it very slow...this can be removed by implementing the slow code in Cython or Jython.....i want to know any other drawback..i wont consider this a serious one..!!

---

### Post by Tony Flury on 2011-06-22
I would suggest that one of Python's massive strengths also can be a weakness.

Python has a considerable number of libraries available to it - ranging from image and media processsing to Internet connectivity and web services (and everything in between). This gamut of libraries is clearly a great boon, but as alluded too by GenBattle that the massive range of libraries also gives a great deal of inertia to the adoption of new versions - note the number of libraries still not available fully for v3, which in turn limits the new versions mainstream adoption.

---

### Post by kagov on 2011-06-22
> **Dhiraj Thakur(Invincible) said:**
> Its not that slow....yes because it is an interpreted language it is slow...but come on....i wont call it very slow...this can be removed by implementing the slow code in Cython or Jython.....i want to know any other drawback..i wont consider this a serious one..!!
 
In comparison to other languages it is. However speed *isn't* everything (unless of course you need it to be fast)

---

### Post by r-senior on 2011-06-22
The Python interpreter is not a default install on Windows.

It's not currently a player in the mobile device arena.

Depends on your definition of "best" but the above make it more of a niche language than C, C++, C#, Java (and perhaps even Objective-C).

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
> **r-senior said:**
> The Python interpreter is not a default install on Windows.

It's not currently a player in the mobile device arena.

Depends on your definition of "best" but the above make it more of a niche language than C, C++, C#, Java (and perhaps even Objective-C).
why not.....i hv heard of python for s60 mobile devices.....yes python is not installed on windows by default but jre,c,c++ compilers r also not installed on win by default.....

---

### Post by StephenF on 2011-06-22
Dynamic typing can make updating your code tedious. In C you can alter a data structure and at compile time the inconsistencies will be flagged up as errors, consequently informing the programmer to update specific parts of the code.

In Python any code not updated will fail at run time. Extensive testing is required to find all the points of failure.

---

### Post by simeon87 on 2011-06-22
It's not slow because of the fact that it's interpreted, it's slow because of the implementation. PyPy is Python written in Python so if that's making it faster then it's due to the implementation. Java and JavaScript are both interpreted as well but due to JIT compiling it's still fast.

Of course compiling a language is faster but being an interpreted language doesn't have to mean that it's "slow".

---

### Post by cgroza on 2011-06-22
> **simeon87 said:**
> It's not slow because of the fact that it's interpreted, it's slow because of the implementation. PyPy is Python written in Python so if that's making it faster then it's due to the implementation. Java and JavaScript are both interpreted as well but due to JIT compiling it's still fast.

Of course compiling a language is faster but being an interpreted language doesn't have to mean that it's "slow".
There are projects that aim to bring JIT to python. I guess in a matter of years, the python world would look very much different than today.

---

### Post by Reiger on 2011-06-22
There are a few points in Python which I think are somewhat less fortunate:

Indentation/scoping falls apart at the seams. There are various corner cases, which IMO should simply not be there. Go solves this by having strict indentation restrictions, other languages by having explicit block delimiters but Python has got neither.

A lot of emphasis on implicit conventions rather than explicit ones. This makes a lot of static analysis harder or sometimes impossible. For large projects static typing is a big win as that allows tools to offer semantically meaningful operations.

A somewhat awkward mix between freedom to do whatever you like on one hand (no modifiers on variables disallowing direct access, making input validation harder to verify), versus kludges to get a semblance of prototyping (the natural extension of duck typing) in the language that doesn't actually work. You can't do something like JavaScript's:
```

String.prototype.say = function() {
  alert(this.toString());
};

"Hello world".say(); // alert's "Hello world".

```

Alternatively I was told that a Lisp style multiple dispatch might work. Python has neither which for a language relying on duck typing is a bit of a shame.

---

### Post by lykwydchykyn on 2011-06-22
> **StephenF said:**
> Dynamic typing can make updating your code tedious. In C you can alter a data structure and at compile time the inconsistencies will be flagged up as errors, consequently informing the programmer to update specific parts of the code.

In Python any code not updated will fail at run time. Extensive testing is required to find all the points of failure.

I'll agree with this.  Flexibility is a double-edged sword.

Deploying stuff to Windows can be a pain, especially if you're using non built-in libraries.

---

### Post by cgroza on 2011-06-22
Still, it is the third most used language in the Linux OSes.

---

### Post by doas777 on 2011-06-22
pyWin install/config is too much for me to ask non-technical folks to go through, so I have never considered deploying a python app to non-managed users. java or .net are easy enough (send them a download link).

I personally don't like the loose/implied typing. I rather like python as a language, but i am always less sure of my code then when working with strong-typed languages. I also hate that it reduces the value of coding-assistance tools (contextual auto-complete). I have top-shelf tools for .net/java/C++, but I feel like I'm working with stone knives when writing in python. the langague is strong, but the tools feel flimsy.

---

### Post by lykwydchykyn on 2011-06-22
> **doas777 said:**
> pyWin install/config is too much for me to ask non-technical folks to go through, so I have never considered deploying a python app to non-managed users. java or .net are easy enough (send them a download link).

If I'm deploying to Windows users, I usually just use py2exe or cx_freeze to make an executable.  Of course, that may not work well for public distribution depending on licensing, but for a work environment it performs acceptably.

The situation could definitely use some improvement, though.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
Python is an ever developing language ... i believe more users will get attracted to this beautiful language in years to come..... :)

---

### Post by ziekfiguur on 2011-06-22
> **Dhiraj Thakur(Invincible) said:**
> why not.....i hv heard of python for s60 mobile devices.....yes python is not installed on windows by default but jre,c,c++ compilers r also not installed on win by default.....

jre is not installed by default, but there hardly exist any windows machines without it, because every major browser has a java plugin. 
C/C++ compilers are not installed by default, but they are not needed to run C or C++ programs, only to make them, so it's no problem that they're not installed.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
> **ziekfiguur said:**
> jre is not installed by default, but there hardly exist any windows machines without it, because every major browser has a java plugin. 
C/C++ compilers are not installed by default, but they are not needed to run C or C++ programs, only to make them, so it's no problem that they're not installed.
Using py2exe or pyinstaller we can make an exe file of the python script too...so thats not a problem...and as for java pluging....once u install python on win u can do anything...not to mention many linux distros now by default include python...

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
> **ziekfiguur said:**
> jre is not installed by default, but there hardly exist any windows machines without it, because every major browser has a java plugin. 
C/C++ compilers are not installed by default, but they are not needed to run C or C++ programs, only to make them, so it's no problem that they're not installed.
Using py2exe or pyinstaller we can make an exe file of the python script too...so thats not a problem...and as for java plugin....once u install python on win u can do anything...not to mention many linux distros now by default include python...

---

### Post by ajackson on 2011-06-22
> **ziekfiguur said:**
> jre is not installed by default, but there hardly exist any windows machines without it, because every major browser has a java plugin. 
C/C++ compilers are not installed by default, but they are not needed to run C or C++ programs, only to make them, so it's no problem that they're not installed.

Not to mention most of the C++ runtimes aren't installed by default either. The nay-sayers will say "but the application installer takes care of that", well that same application installer can install the dependencies of python programs as well.

There are very few programs that can work without dependencies but in windows-land the installation of them is usually hidden from the user so they don't realise they exist.

---

### Post by cgroza on 2011-06-22
> **ajackson said:**
> not to mention most of the c++ runtimes aren't installed by default either. The nay-sayers will say "but the application installer takes care of that", well that same application installer can install the dependencies of python programs as well.

There are very few programs that can work without dependencies but in windows-land the installation of them is usually hidden from the user so they don't realise they exist.
+1

---

### Post by llanitedave on 2011-06-22
> **Dhiraj Thakur(Invincible) said:**
> Its not that slow....yes because it is an interpreted language it is slow...but come on....i wont call it very slow...this can be removed by implementing the slow code in Cython or Jython.....i want to know any other drawback..i wont consider this a serious one..!!

From my experience it seems to be in the same general speed range as Mozilla's Javascript engine.  It's not really "slow" on modern computers, it just isn't blazingly fast like compiled languages are.

---

### Post by cgroza on 2011-06-22
Speed is rarely an issue in programming applications. The question is not "Is it fast?", the question is "Is it fast enough?".

---

### Post by unknownPoster on 2011-06-22
> **cgroza said:**
> Speed is rarely an issue in programming applications. The question is not "Is it fast?", the question is "Is it fast enough?".

Especially in the case of majority of most end-user applications. Barring poor algorithm design, the speed bottleneck will almost always be waiting for user-input. No language can get around that.

---

### Post by stchman on 2011-06-22
Noting what Windows lacks as far as compilers runtime environments, etc., is not a shortcoming.  Heck Windows comes with pretty much nothing OOB.

---

### Post by doas777 on 2011-06-23
> **stchman said:**
> Noting what Windows lacks as far as compilers runtime environments, etc., is not a shortcoming.  Heck Windows comes with pretty much nothing OOB.
true, but when deploying an app, dependencies become a primary concern, and can be the difference between success and failure for your application.

---

### Post by JupiterV2 on 2011-06-23
> **doas777 said:**
> true, but when deploying an app, dependencies become a primary concern, and can be the difference between success and failure for your application.

This is exactly why I'm starting to take to the idiom of static linking. Yes, it makes for a larger program. Yes, that makes updating said program take more bandwidth. However, the pros are pretty considerable. No worry of a library update introducing a bug not previously existing in your program. No dependency hell. No worry that a prior, existing bug, in a library needs to be updated if your program doesn't take advantage of that particular feature. There are pros/cons to both sides but I'm starting to think the advantages of static linking outweigh the cons...I'm not 100% decided yet though.

---

### Post by Reiger on 2011-06-23
> **JupiterV2 said:**
> This is exactly why I'm starting to take to the idiom of static linking. Yes, it makes for a larger program. Yes, that makes updating said program take more bandwidth. However, the pros are pretty considerable. No worry of a library update introducing a bug not previously existing in your program. No dependency hell. No worry that a prior, existing bug, in a library needs to be updated if your program doesn't take advantage of that particular feature. There are pros/cons to both sides but I'm starting to think the advantages of static linking outweigh the cons...I'm not 100% decided yet though.

Well the con is that you run like Windows does on 5 year old hardware instead of like Linux does on the same. Static linking doesn't just mean a larger disk foot print, it means a larger memory and cache foot print as well. Imagine if each GTK or Qt app statically linked all underlying libs, then consider how many you run on a typical Gnome/KDE desktop. *shudder*

---

