---
title: "Python speed"
date: 2007-01-18
forum: Programming Talk
---

### Post by rekahsoft on 2007-01-18
Hi all, i am new to python and was wondering what the speed difference is compared to C++? I want to write a music/media player and was looking at python as a possable choice although i am not sure of its speed; my other language of choice for the job is C++. I know that lots of apps are written with python for linux and this does not exclude music player (ex. Listen, Exaile) so what is the performace like? I will be using GTK+ for GUI, gstreamer as the audio/video backend, and have a nice selection of databases available for use. I know that GTK+ programming in python is a just a wrapper of the GTK+ C libraries, as the same for gstreamer, but i am not as sure about the databases. Thanks for your input :)

---

### Post by Wybiral on 2007-01-18
It sounds like most of it is just going to be interfacing with those libraries... And in that case, python isn't going to be much slower than C++ (even with C++ you would just be interfacing with the libraries... So the only thing that really matters is the speed of the libraries)

The only times when python is slower than C++ are when a lot of complex math is used or when you need to manually iterate over stuff. But yeah... If your code is mostly wrapping around those libraries, then it shouldn't be much slower than C++

I've actually demonstrated this with C++ vs Python with OpenGL... When more OpenGL commands were used and less language specific stuff, they ran at about the same speed (even with a complex 3d scene)

---

### Post by rekahsoft on 2007-01-18
thanks :) btw i did read your post on python openGL ;):)

---

### Post by jblebrun on 2007-01-18
Here's a great set of benchmarks comparing various languages:

[http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

---

### Post by Wybiral on 2007-01-18
^ Those tests were all made doing really language specific stuff, so it wouldn't apply in a situation like this.

Also, if you find python to be too slow... Write a small module for it using C or C++, that way you can keep the simplicity of python and gain the speed boost of c/c++

---

### Post by maddog39 on 2007-01-18
You also have the option of compiling python into highly optimized bytecode. If you did that, you would be either matching or almost matching the performance of C++. I wrote a GUI tool to do this too btw (check sig). Plus python is alot quicker in development and what not and just easier overall. I would atleast give it a shot.

---

### Post by rekahsoft on 2007-01-18
> **maddog39 said:**
> You also have the option of compiling python into highly optimized bytecode. If you did that, you would be either matching or almost matching the performance of C++. I wrote a GUI tool to do this too btw (check sig). Plus python is alot quicker in development and what not and just easier overall. I would atleast give it a shot.

Is this done with psycho? What do you do this with? Would you point me to some tools? Do i have to code different to receive the pay out?

---

### Post by maddog39 on 2007-01-19
No, the compiling is done with the standard python compiler that is included with the language. But there arent any tools (yet, I dont think) to actually use it which is why I made a small wxPython program to use it, plus I was bored out of my mind (:D), since its just part of the standard python library. And the answer to your 4th question is no you dont. Your code will run/compile normally without any extra changes.

---

### Post by ianare on 2007-01-19
forgive me if i'm wrong, but don't all python program automatically compile to bytecode the first time run?

---

### Post by kripkenstein on 2007-01-19
> **maddog39 said:**
> You also have the option of compiling python into highly optimized bytecode. If you did that, you would be either matching or almost matching the performance of C++.

Note sure what you mean here - Python always compiles into bytecode, those are the .pyc files you see. But this doesn't run at anywhere near the speed of C++; it is in general even slower than other bytecode languages like Java (basically because Python is much more dynamic; more runtime checking).

Psyco can help with Python's speed, sometimes dramatically. It doesn't require many changes to code (but it does require a few).

---

### Post by Wybiral on 2007-01-19
Yeah... Python can't really be compiled to machine code because the dynamic typing and garbage collection would never work that way.

I don't know how the python interpreter works, but I have done a lot of research on the java JVM & JIT...

Java is able to compile the bytecode into machine code, only in certain areas of the code, and it's done at runtime (Just In Time comipiler)

The only downside to that is that it takes a lot of CPU to compile pieces of the program every time you run it (imagine if you had to compile a C program every time you ran it... EEK)

But, like I said... With python, a lot of the modules were written in C, and have already been compiled. You probably won't get much of a speed decrease if you lean as much of the program on these as possible.

---

### Post by pmasiar on 2007-01-20
> **Wybiral said:**
> Yeah... Python can't really be compiled to machine code because the dynamic typing and garbage collection would never work that way.
Wrong. Psyco, py2exe and Snakeskin are real compilers. They compile bytecode into executable.

> But, like I said... With python, a lot of the modules were written in C, and have already been compiled. You probably won't get much of a speed decrease if you lean as much of the program on these as possible.

Agree. If 90% of your code is spent inside library calls, database calls etc, difference in execution time between C and Python is negligible (max 10%) and "speed to the market" is much faster in Python.

---

### Post by Wybiral on 2007-01-20
Are you sure that "...Psyco, py2exe and Snakeskin..." aren't actually just embedding the bytecode into a small interpreter? I've seen that done before... Because compiled code simply cannot be that dynamic (especially with commands like "eval" and "exec") I can't see the code being 100% compiled into machine code without taking away some of the pythonicness of the program.

---

### Post by Wybiral on 2007-01-20
Ok, I did some research, and I was correct... Those programs don't compile it to machine code (it sounds like psyco compiles small portions into machine code, but most is still interpreted), they attach the bytecode to a "stub"

This is how Basic4GL works (one of the projects I've been working on).

The stub is like the small essential part of the interpreter that "executes" the bytecode.


Small portions of it being compiled is similar to java's JIT compiler, but it doesn't compile everything because large portions of the language simply cannot do what they do in machine code. (unlike pythons JIT, those python programs don't have to compile at runtime... EEEK, talk about a CPU gobbler...)

[http://www.python.org/pycon/2006/papers/26/4%20How%20does%20it%20work.html](http://www.python.org/pycon/2006/papers/26/4%20How%20does%20it%20work.html)
[http://www-128.ibm.com/developerworks/library/l-psyco.html](http://www-128.ibm.com/developerworks/library/l-psyco.html)

---

### Post by kripkenstein on 2007-01-20
Python CAN be compiled into 'machine code', that is, to assembly language commands. But those commands would need to implement dynamic typing, and so forth. So it would still be fairly slow. This is just the price of a dynamic language. But the benefits are worth it :)

---

### Post by Wybiral on 2007-01-20
But it would essentially still need an interpreter to be dynamically typed... It just can't happen.

I love python, I'm just saying... That's one thing you will probably never see, is a fully function python - 2 - executable compiler.

They can embed your program over a stub, and make it able to run itself... Heck, they can even compile chunks of it to speed it up a little. But they can't compile it 100% to machine code, so people saying that python can be compiled to C speeds is kindof ridiculous.

As pmasiar has mentioned, execution speed isn't always that important. And also, if you lean enough on compiled libraries, it's not going to be much slower that a compiled program leaning on those libraries. Python is a great language for a lot of things, but I can't see it doing heavily mathematical graphics or device stuff... But, when I'm not doing either of those... I generally opt for python.

Python is also a good development language, you can write everything in it for fast testing and typing... Then port it to C/C++ (with C++ it isn't even that hard to port, add some ";" and "{}"... Fill in the types, and change some commands... BAM, python into C++)

---

### Post by rekahsoft on 2007-01-20
> **Wybiral said:**
> But it would essentially still need an interpreter to be dynamically typed... It just can't happen.

I love python, I'm just saying... That's one thing you will probably never see, is a fully function python - 2 - executable compiler.

They can embed your program over a stub, and make it able to run itself... Heck, they can even compile chunks of it to speed it up a little. But they can't compile it 100% to machine code, so people saying that python can be compiled to C speeds is kindof ridiculous.

As pmasiar has mentioned, execution speed isn't always that important. And also, if you lean enough on compiled libraries, it's not going to be much slower that a compiled program leaning on those libraries. Python is a great language for a lot of things, but I can't see it doing heavily mathematical graphics or device stuff... But, when I'm not doing either of those... I generally opt for python.

Python is also a good development language, you can write everything in it for fast testing and typing... Then port it to C/C++ (with C++ it isn't even that hard to port, add some ";" and "{}"... Fill in the types, and change some commands... BAM, python into C++)

Thanks, nice to know :)

---

### Post by pmasiar on 2007-01-20
Thank you for the links. Especially IBM article about psyco was enlightening:

"Python is usually fast enough for what you want it to do. Ninety percent of the concerns that novice programmers express about the execution speed of an interpreted/byte-compiled language like Python are simply naive. "

"the right algorithm in Python will often go faster than the wrong algorithm in hand-tuned assembly"

 Well said.

> **Wybiral said:**
> Ok, I did some research, and I was correct... Those programs don't compile it to machine code (it sounds like psyco compiles small portions into machine code, but most is still interpreted), 

IIUC,  psyco does JIT (just-in-time) type inferencing on selected functions and then **compiles** binaries with proper types. 

> **Wybiral said:**
> But it would essentially still need an interpreter to be dynamically typed... It just can't happen. (...)  you will probably never see, is a fully function python - 2 - executable compiler.

Of course only interpreted can be dynamically typed. To compile, you need to know types. You can either 

[LIST]
[*]write types for time-critical modules - Optional types are discussed on and off between python developers, and if it is optional and they can pull it through, why not.
[*]Use [Pyrex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/"): "Pyrex lets you write code that mixes Python and C data types any way you want, and **compiles it into a C** extension for Python. "
[*]infer type JIT info like psyco does. Not enough effort was invested yet (comapred to java), but JIT type inferencig is mentioned on every pycon: It is another frontier of computer science,  and many PhDs cut their teeth on that - let's wait 10 years for the results. :-) I read about one such effort at planetpython (in beta now), but forgot the name - something like snakeskin, but different. ;-(
[/LIST]

> Python is also a good development language, you can write everything in it for fast testing and typing... Then port it to C/C++ (with C++ it isn't even that hard to port, add some ";" and "{}"... Fill in the types, and change some commands... BAM, python into C++)

or use pyrex, even less works and C integration is solved for you.

And for numerical processing, you can use [numpy]("http://en.wikipedia.org/wiki/Numpy") instead of rolling out your own array manipulation routines.

---

### Post by Mirrorball on 2007-01-20
> **pmasiar said:**
> 
"the right algorithm in Python will often go faster than the wrong algorithm in hand-tuned assembly"

But when you are a novice, you will choose the wrong algorithm in Python too. :P

---

### Post by pmasiar on 2007-01-20
> **Mirrorball said:**
> But when you are a novice, you will choose the wrong algorithm in Python too. :P

With python, it will take you less time to realize that your algorithm is wrong - and will be simpler to expand/change it, comparing to same rework to same algorithm implemented in C or ASM. So it is one *more* argument why Python is good for beginners: **you can make mistakes faster** :-) - so you can learn from them faster.

But I agree - any novice is just plain doomed and should just shut up and give up and learn programming like we did in old times, ground up, ASM first. **Then** they will appreciate any language :twisted:

---

### Post by maddog39 on 2007-01-21
About the earlier argument with python always being slower than C++. Umm.. doesnt anyone recall the topic where we compared a 3D app example in python and a 3D app example in C++ which were both identicle. Then we got the python example app to be nearly equal to the performance of the C++ example app. Thats where I'm coming from. Also python doesnt always make the .pyc files, sometimes for some reason PyGTK will make them, but normally they are not made at all. Well anyway, thats where I'm coming from.

---

### Post by Wybiral on 2007-01-21
Yeah, I was the one who did the particle test in C++ and python. That's actually been my point throughout this thread... If it leans on other libraries, compiled libraries, then it will basically be as fast as a compiled program. Only if you take the control away from the compiled library and try to implement too much of it in python does the speed parallel begin to drop.

Thats actually how I got the two programs to the same speed. I made OpenGL do all of the work instead of C++ OR python. Since the same library was essentially pulling the entire load in both of them, they ended up running at nearly identical speeds (even with like 20,000 particles)

Here was the post: [http://ubuntuforums.org/showthread.php?t=316601](http://ubuntuforums.org/showthread.php?t=316601)

Unfortunately for pythons side of the argument... I believe the Mesa GL libraries were mostly written in C. And when the two examples didn't lean so heavily upon OpenGL to handle the rendering, the c++ version was considerably faster. I still want other people to try it out and fill me in on their results.

---

### Post by rekahsoft on 2007-01-21
> **maddog39 said:**
> Also python doesnt always make the .pyc files, sometimes for some reason PyGTK will make them, but normally they are not made at all. Well anyway, thats where I'm coming from.

WRONG!! Python does not always make .pyc (python bytcode) files but it is the only think that does. PyGTK does not do this! Correct me if i am wrong but from what i have read, python makes the .pyc files.

---

### Post by neoflight on 2007-01-22
> **rekahsoft said:**
> WRONG!! Python does not always make .pyc (python bytcode) files but it is the only think that does. PyGTK does not do this! Correct me if i am wrong but from what i have read, python makes the .pyc files.

thats a little unclear....:roll:

---

### Post by kripkenstein on 2007-01-22
> **neoflight said:**
> thats a little unclear....:roll:

Python creates .pyc files. It doesn't always do so (I am not sure of the precise decision process it goes through - perhaps for very small files it doesn't, something like that). But in general, it compiles into bytecode and saves that as .pyc.

PyGtk has nothing to do with .pyc files (no more than any other Python module).

---

### Post by maddog39 on 2007-01-25
I could flame over rekahsoft's comment. But whatever. The point is I made the program to generate the .pyc's when they weren't generated in the first place, and my other point is that the .pyc's do greatly improve the performance of the scripts.

---

### Post by rekahsoft on 2007-01-25
> **maddog39 said:**
> I could flame over rekahsoft's comment. But whatever. The point is I made the program to generate the .pyc's when they weren't generated in the first place, and my other point is that the .pyc's do greatly improve the performance of the scripts.

Sorry, i didn't mean any harm :( If i offended you i am sorry

---

### Post by maddog39 on 2007-01-26
Naw, it just sounded kind of angry (to me anyway), thats all.

---

