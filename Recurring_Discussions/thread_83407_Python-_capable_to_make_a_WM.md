---
title: "Python- capable to make a WM?"
date: 2005-10-28
forum: Recurring Discussions
---

### Post by commodore on 2005-10-28
I'm not a programmer, but I have thought about learning it for a long time. I really like python although I don't know much about it. I'd like to know what is python capable of. I know it's good for interfaces and scripting. I have seen applications programmer in python. But can python be used to program something like a window manager? Not that I'd like to program a WM. I know kernel is in C so I don't know if this is thinkable.

---

### Post by majikstreet on 2005-10-28
[QUOTE=commodore]I'm not a programmer, but I have thought about learning it for a long time. I really like python although I don't know much about it. I'd like to know what is python capable of. I know it's good for interfaces and scripting. I have seen applications programmer in python. But can python be used to program something like a window manager? Not that I'd like to program a WM. I know kernel is in C so I don't know if this is thinkable.[/QUOTE]
/me wants to know the same thing.

---

### Post by jmonteiro on 2005-10-28
Have you heard about Ununumium? It is an entire OS (in fact an Kernel) completly writen in Python. No other language, no C, no C++: just Python.

If it is possible to make an kernel with Python, why not an WM? Yes, it is possible :)

* The Ununumium webpage is: [http://unununium.org/]("http://unununium.org/")

---

### Post by Kimm on 2005-10-28
They have some interesting points in their Introduction page. I'm interested to see how the project turns out.

By they way..
How the heck did they write a kernel in Python? did they write a compiler for it or what? Or have they not yet realized its an interpreter language? (j/k) :-P

---

### Post by commodore on 2005-10-29
> The language of Unununium is Python. This is not to say that programs are written in Python and **the kernel is in C**

I still like python :)

---

### Post by sas on 2005-10-29
[QUOTE=commodore] But can python be used to program something like a window manager? Not that I'd like to program a WM. I know kernel is in C so I don't know if this is thinkable.[/QUOTE]

If someone _really_ wanted to, it'd be possible. There's pyGTK hooks, you could make a GTK based window manager, might be slow or something though...

---

### Post by Markpy on 2005-10-29
There is a Python Window Manager - [PYWM]("http://pywm.sourceforge.net/") which wraps around FLWM.

---

### Post by commodore on 2005-10-29
[QUOTE=Markpy]There is a Python Window Manager - [PYWM]("http://pywm.sourceforge.net/") which wraps around FLWM.[/QUOTE]

:D

Has anyone tried Blender? It would be cool if someone would make a WM like that. In Blender you can add panels, change the size, and location of them and the scale of the content in the panels and other kewl stuff.

---

### Post by jmonteiro on 2005-10-29
[quote=Markpy]There is a Python Window Manager - [PYWM]("http://pywm.sourceforge.net/") which wraps around FLWM.[/quote]

Woa, I will install and give a try! Do anybody here have already tested it?

---

### Post by commodore on 2005-10-30
I definetly want to test it. It has some very interestin features. If they had more people with skills in other things like art they would make a very nice WM.

In PYWM you can make you're desktop as big as you want cause you can pan!

---

### Post by Drakx on 2005-10-30
I believe that there is an entire os wiritten in python cannot remember the name of it though, do a serch on the forums youll find it :)

---

### Post by commodore on 2005-10-30
Ok, I downloaded PYWM. I'm ready to install, but I have some questions:
* how do get PYWM to start on startup instead of Metacity?
* can I use GNOME apps like Nautilus with it?

---

### Post by ov3rcl0ck on 2009-05-04
Totally, you can access C functions and methods with ctypes in python and use pyglet(opengl) to display the desktop. The thing is you can use C, C++, Java, etc. in python by using a wrapper. Heres a link to a window manager done in python [http://code.google.com/p/samurai-x/](http://code.google.com/p/samurai-x/) (still in development).

---

### Post by regomodo on 2009-05-04
Yep. [Tinywm]("http://incise.org/tinywm.html") has it's code there. It's written in C or python. The python version uses python-xlib module.

[PHP]# TinyWM is written by Nick Welch <mack@incise.org>, 2005.
#
# This software is in the public domain
# and is provided AS IS, with NO WARRANTY.

from Xlib.display import Display
from Xlib import X, XK

dpy = Display()
root = dpy.screen().root

root.grab_key(XK.string_to_keysym("F1"), X.Mod1Mask, 1,
        X.GrabModeAsync, X.GrabModeAsync)
root.grab_button(1, X.Mod1Mask, 1, X.ButtonPressMask,
        X.GrabModeAsync, X.GrabModeAsync, X.NONE, X.NONE)
root.grab_button(3, X.Mod1Mask, 1, X.ButtonPressMask,
        X.GrabModeAsync, X.GrabModeAsync, X.NONE, X.NONE)

while 1:
    ev = root.display.next_event()

    if ev.type == X.KeyPress and ev.child != X.NONE:
        ev.window.circulate(X.RaiseLowest)
    elif ev.type == X.ButtonPress and ev.child != X.NONE:
        ev.child.grab_pointer(1, X.PointerMotionMask|X.ButtonReleaseMask,
                X.GrabModeAsync, X.GrabModeAsync, X.NONE, X.NONE, X.CurrentTime)
        attr = ev.child.get_geometry()
        start = ev
    elif ev.type == X.MotionNotify:
        #while(XCheckTypedEvent(dpy, MotionNotify, &ev));
        xdiff = ev.root_x - start.root_x
        ydiff = ev.root_y - start.root_y
        ev.window.configure(
            x = attr.x + (start.detail == 1 and xdiff or 0),
            y = attr.y + (start.detail == 1 and ydiff or 0),
            width = max(1, attr.width + (start.detail == 3 and xdiff or 0)),
            height = max(1, attr.height + (start.detail == 3 and ydiff or 0)))
    elif ev.type == X.ButtonRelease:
        dpy.ungrab_pointer(X.CurrentTime)[/PHP]

---

### Post by hessiess on 2009-05-05
> **commodore said:**
> :D

Has anyone tried Blender? It would be cool if someone would make a WM like that. In Blender you can add panels, change the size, and location of them and the scale of the content in the panels and other kewl stuff.

Ratpoision, stumpwm, Ion...

---

### Post by Kilon on 2009-05-05
> **Drakx said:**
> I believe that there is an entire os wiritten in python cannot remember the name of it though, do a serch on the forums youll find it :)

PyCorn is an OS written on python , and as the author claims " Device drivers, file systems, network protocols can all be implemented in Python with no C or assembler code" 

[https://launchpad.net/pycorn](https://launchpad.net/pycorn)
[http://linux.softpedia.com/get/System/Operating-Systems/Other/Pycorn-40554.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Other/Pycorn-40554.shtml)


I guess it is only a matter of time before a full blown python os is developed.

---

### Post by regomodo on 2009-05-05
> **Kilon said:**
> I guess it is only a matter of time before a full blown python os is developed.

Well, i'm slowly building little apps in PyQt4 that could easily be part of a DE. If only I could concentrate on one at a time. So far I have the makings of:
[LIST=1]
[*]RAW Image viewer
[*]Image Viewer
[*]PDF Viewer
[*]amarok clone
[*]Webbrowser (I attempted a multitabbed browser but it was a pain)
[*]networkmanager
[*]disk usage display
[*]gphoto2 frontend
[*]ffmpeg frontend
[*]pyparallel frontend
[*] Python Imaging Library im-editor
[/LIST]

The image viewers and gphoto2 frontend are practically done with the webbrowser ~60% done. I'm moving back to England after traveling for 6months and project ideas floating around in my head are getting quite frustrating.

---

### Post by soltanis on 2009-05-05
Yes, Python could write a WM. The question is, would you use it (it'd be a little sluggish).

On how they wrote the python kernel, I believe they bootstrap the system with assembler, so it isn't just python (unless there were a hardware python interpreter, you'd need to use assembler somewhere); then they somehow load a python interpreter and get to work.

---

### Post by wenren on 2009-05-06
> **Kilon said:**
> PyCorn is an OS written on python , and as the author claims " Device drivers, file systems, network protocols can all be implemented in Python with no C or assembler code" 

[https://launchpad.net/pycorn](https://launchpad.net/pycorn)
[http://linux.softpedia.com/get/System/Operating-Systems/Other/Pycorn-40554.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Other/Pycorn-40554.shtml)


I guess it is only a matter of time before a full blown python os is developed.

I don't think there will ever be a "full blown python os." The problem here is that, as the PyCorn site admits, it is an "interpreted" operating system. To have a full Python OS, you would essentially have to replace the entire kernel with Python; to do that, there could be no interpreter; and for that to happen Python would need to be compiled.

So is a full Python OS possible? Not unless you write a compiler. But at that point, could it even be considered Python? I doubt it. This is the same problem faced by other languages, such as Java.


Speaking of WMs, these at least don't always need a compiler, as seen with PYWM. My favourite WM, besides KDE, is XMonad. Very fast, very flexible, and very customizable. It is written in Haskell, which may be either interpreted or compiled.

---

### Post by eye208 on 2009-05-06
> **sven.hakonsson said:**
> So is a full Python OS possible? Not unless you write a compiler.
Thank you for injecting some common sense into this thread. The current Python hype makes many people forget that Python is not a programming language, but a scripting language.

---

### Post by mssever on 2009-05-07
> **eye208 said:**
> Thank you for injecting some common sense into this thread. The current Python hype makes many people forget that Python is not a programming language, but a scripting language.
I suppose I really should ignore this, but I had some time to waste, so I'll post.

There's no such thing as a scripting language that isn't a programming language. You can only write programs in programming languages. And a script is merely a poorly-defined type of program.

Since there exist applications that are written in Python, Python is clearly a programming language.

---

### Post by simeon87 on 2009-05-07
> **eye208 said:**
> Thank you for injecting some common sense into this thread. The current Python hype makes many people forget that Python is not a programming language, but a scripting language.

You feel that the mighty title "programming language" can only be used for your favorite language and not for something - in your eyes - inferior as Python?

In addition to the argument presented by the previous poster, Python is expressive enough to write what you want (i.e., it's not like SQL or so).. including *programs* (hence the name programming language). It's not limited to scripts or glue code.

---

### Post by CptPicard on 2009-05-07
If it's Turing-complete, it's a programming language. I see eye208 is engaging in his flamebaiting again... :)

Anyway, the entire thread has the typical "but can it be used to write an OS/WM" noobishness all over it. Learn to write programs in general, then choose a tool you need when you have specific technical requirements. The "whether Python can be used to write an WM" question is completely dependent on what kind of communication you need to be doing with the X server and what you have to link against, nothing else. I haven't really done any X stuff, but as the WM is just another X client, the answer should apparently be "yes".

---

### Post by eye208 on 2009-05-07
> **mssever said:**
> There's no such thing as a scripting language that isn't a programming language. You can only write programs in programming languages. And a script is merely a poorly-defined type of program.

Since there exist applications that are written in Python, Python is clearly a programming language.
Explaining the difference between a program and a script is actually very simple:
[list][*]A **program** controls the behavior of a **machine**.
[*]A **script** controls the behavior of a **program**.[/list]
In the case of Python applications, the program is always the Python interpreter, which is written in C. There is no such thing as "a program written in Python" until either of the following happens:
[list][*]Someone implements a Python compiler.
[*]Someone builds a machine that executes Python bytecode.[/list]
Until then, Python applications are scripts, not programs, and there will be no operating system written in Python.

---

### Post by benj1 on 2009-05-07
> **eye208 said:**
> Explaining the difference between a program and a script is actually very simple:
[list][*]A **program** controls the behavior of a **machine**.
[*]A **script** controls the behavior of a **program**.[/list]
In the case of Python applications, the program is always the Python interpreter, which is written in C. There is no such thing as "a program written in Python" until either of the following happens:
[list][*]Someone implements a Python compiler.
[*]Someone builds a machine that executes Python bytecode.[/list]
Until then, Python applications are scripts, not programs, and there will be no operating system written in Python.

so what is a python *script* is a script controlling a program controlling a machine?

does that also mean that c source code is a script for the compiler? 

python is an interpreted language.

---

### Post by simeon87 on 2009-05-07
> **eye208 said:**
> Explaining the difference between a program and a script is actually very simple:
[list][*]A **program** controls the behavior of a **machine**.
[*]A **script** controls the behavior of a **program**.[/list]
In the case of Python applications, the program is always the Python interpreter, which is written in C. There is no such thing as "a program written in Python" until either of the following happens:
[list][*]Someone implements a Python compiler.
[*]Someone builds a machine that executes Python bytecode.[/list]
Until then, Python applications are scripts, not programs, and there will be no operating system written in Python.

So Java is a scripting language? The only difference being that you perform the compile step explicitly for Java and implicitly for Python but in both cases, the source is compiled to byte code which is executed.

---

### Post by ajackson on 2009-05-07
> **eye208 said:**
> Explaining the difference between a program and a script is actually very simple:
[list][*]A **program** controls the behavior of a **machine**.
[*]A **script** controls the behavior of a **program**.[/list]
In the case of Python applications, the program is always the Python interpreter, which is written in C. There is no such thing as "a program written in Python" until either of the following happens:
[list][*]Someone implements a Python compiler.
[*]Someone builds a machine that executes Python bytecode.[/list]
Until then, Python applications are scripts, not programs, and there will be no operating system written in Python.
hahahahahahahahahaha
[deep breath]
hahahahahahahahahaha

By that definition there are **no** programming languages.

Can C run without first being compiled? No, therefore it is a script for a C compiler.
Can Java run without being compiled and then interpreted? No so it is a script for the compiler and then that compiled stuff is a script for the interpreter.
Can Python be ran without an interpreter? No, so it is a script for the interpreter.
Can assembly be ran without being compiled? No so that also is a script.

Just think the Linux kernel is just a collection of scripts.

Thanks for the laugh.

---

### Post by eye208 on 2009-05-07
> **benj1 said:**
> does that also mean that c source code is a script for the compiler?
Actually yes, but only as far as preprocessor instructions and macros are concerned. The compiler does not execute the logic described in the C program.

---

### Post by Kilon on 2009-05-07
> **eye208 said:**
> Explaining the difference between a program and a script is actually very simple:


[list][*]A **program** controls the behavior of a **machine**.


[*]A **script** controls the behavior of a **program**.[/list]

In the case of Python applications, the program is always the Python interpreter, which is written in C. There is no such thing as "a program written in Python" until either of the following happens:
[list][*]Someone implements a Python compiler.
[*]Someone builds a machine that executes Python bytecode.[/list]
Until then, Python applications are scripts, not programs, and there will be no operating system written in Python.

And there is no such thing as C program as it is all assembly code. LOL

You are a funny guy

Again according to your reasoning a plugin is nothing more than a script , LOL

Of course this is nonsense since plugins are libraries (DLLs , etc)  and regular programming code. 

Also almost all programs are meant to run inside an OS , so  according to your insane reasoning all programms are in true form SCRIPTS!!! lol

There is no big divide between scripting and programming . For me the whole distinction is fundamentally flawed because there so many different kinds of scripting and programming which is impossible to Draw a line between the two. 

Any programming language can be used as a scripting language , for example Java has been used as a scripting language in many games.

---

### Post by ajackson on 2009-05-07
> **eye208 said:**
> Actually yes, but only as far as preprocessor instructions and macros are concerned. The compiler does not execute the logic described in the C program.

Thank you for confirming that C is not a programming language (by your definition of a programming language of course).

Edit: Missed the laugh part due to laughing too hard. The compiler doesn't execute the logic of the program but it translates it into machine code equivalents. The C code logic is **never** ran, just interpreted/compiled.

---

### Post by eye208 on 2009-05-07
> **simeon87 said:**
> So Java is a scripting language?
No, it's a programming language. There are compilers for Java (e.g. GCJ), and there are machines that execute Java bytecode (e.g. the Jazelle CPU).

---

### Post by CptPicard on 2009-05-07
This is a pretty meaningless distinction from the program's perspective... Turing-completeness is such a fundamental property that a programming language really doesn't "know or care" whether it runs on hardware or, say, in an a VM or interpreter. Running "straight on hardware" is not special when computation is concerned (I can hack up a CPU emulator in python for machine code binaries, and vice versa, a stored-program can serve essentially as an extension of hardware), and therefore, at least when discussing about things formally, anything that is Turing-complete is a "programming language" just fine, as the class of problems that is solved remains the same.

The definition up there is very much informal and wrong in the sense that it is very rare to hear of the vague category of "scripting" languages as being discussed as *distinct* from "programming" languages  -- this usually only comes from the crowd who have some ideological affinity to hardware. They are an (intuitively defined) subset, certainly...

---

### Post by ajackson on 2009-05-07
> **eye208 said:**
> No, it's a programming language. There are compilers for Java (e.g. GCJ), and there are machines that execute Java bytecode (e.g. the Jazelle CPU).
Erm in Java the compiler converts the Java code to byte code and the interpreter runs that byte-code.

In Python the code is converted to byte-code on the fly (the pyc files) and that byte-code is then ran. The only difference is that Python does it in one stage and Java two.

So which machines can run C code if that is a further requirement?

---

### Post by eye208 on 2009-05-07
> **CptPicard said:**
> This is a pretty meaningless distinction from the program's perspective...
Most of the time, yes. But when it comes to questions such as "Can I write an OS in language X?", the answer is always No if X is a scripting language.

This has nothing to do with Turing-completeness. Turing-completeness requires a machine. You can simulate Turing-complete machines in software, but their bytecodes have no meaning outside the simulation.

I don't know why some people here get emotional about this. The distinction between programming and scripting (Feel free to call it "simulated programming".) is essential to answer the question at hand. Writing an operating system in Python requires a compiler or a Python-aware machine, otherwise there is nothing to operate.

---

### Post by CptPicard on 2009-05-07
A further refinement to what ajackson and me are aiming for is to understand that any "middleware", be it a compiler or VM or whatever, between your programming language and the CPU is a kind of Turing-complete extension layer of the hardware that provides a mapping from a language that is more suitable for *programming* (that is: "giving a formal specification of a computation" -- a "program") to a language that is more suitable to driving the hardware (CPU instructions). That's all it is, and it's essentially transparent and fully maintains the class of problems that can be solved.

It's also worth remembering that even native-compiled stuff make a lot of use of "runtime" in the form of libraries, so running other software as "hardware extension" alongside yours is a totally natural occurrence.

"Guiding execution by data" is also not all that strange, data structures, as the most trivial example, do that all the time. If you're allowing for evaluable data structures, you get "scripts" as discussed here, and when you generalize further it's just a small hop to Lisp. Lisp allows you to "fix" your even runtime-built syntax trees into compiled code, by the way, if that is a huge requirement :)

---

### Post by ajackson on 2009-05-07
> **eye208 said:**
> I don't know why some people here get emotional about this.
I suppose amused can be classed as an emotional state but no-one is getting emotional about this (well you seem to be getting frustrated).

> **eye208 said:**
> Writing an operating system in Python requires a compiler or a Python-aware machine, otherwise there is nothing to operate.
So does C not require a compiler or C-aware machine? Python has a compiler, where do you think those pyc files come from?.

---

### Post by Kilon on 2009-05-07
> **eye208 said:**
>  Writing an operating system in Python requires a compiler or a Python-aware machine, otherwise there is nothing to operate.

Writting an OS in any language requires First determination and patience. I agree with captain pickard here.

OS development is no easy feat . 

Second there are no rules how will be accomplished with python, 

Maybe for example one can develop a special version of python VM which could support itself outside any OS. Afterall python is open source ;) 

Or Maybe one could build the foundation on C and the rest on python. (See pyCorn )  

Or maybe .....

---

### Post by ajackson on 2009-05-07
> **eye208 said:**
> This has nothing to do with Turing-completeness. Turing-completeness requires a machine. You can simulate Turing-complete machines in software, but their bytecodes have no meaning outside the simulation.
You've said that Java is a programming language, here you seem to be saying it is not because "their byte-codes have no meaning outside the simulation". The Java interpreter is pretty much a virtual machine, so not a real machine.

So is Java a programming language, it has a compiler but operates on a virtual machine?

Is Python a programming language, it also has a compiler and also operates on a virtual machine (it's interpreter)?

The main difference between Python and Java is the Java compiler and interpreter are separate while the Python compiler and interpreter are combined. If one is a programming language the other must be and you have already stated that Java **is** a programming language.

Might I suggest a bit of reading (not wikipedia though) to broaden your knowledge.

---

### Post by bapoumba on 2009-05-07
Time to remove your subscriptions :)

---

### Post by Mehall on 2009-05-07
There's a Haskell Window Manager. If you want it, you can make it, regardless of language, provided it's Turing Complete. (technically speaking)

---

### Post by eye208 on 2009-05-08
> **ajackson said:**
> You've said that Java is a programming language, here you seem to be saying it is not because "their byte-codes have no meaning outside the simulation". The Java interpreter is pretty much a virtual machine, so not a real machine.
Which part of post #31 didn't you understand?

---

### Post by simeon87 on 2009-05-08
> **eye208 said:**
> Which part of post #31 didn't you understand?

Post 31 describes borderline cases that you're using to justify your flawed definition; we're obviously talking about the use of Java through the JVM.

---

### Post by eye208 on 2009-05-08
> **simeon87 said:**
> Post 31 describes borderline cases that you're using to justify your flawed definition
First, the definition is not mine. Second, if you consider it flawed, you have to explain why.

---

### Post by ajackson on 2009-05-08
> **simeon87 said:**
> Post 31 describes borderline cases that you're using to justify your flawed definition; we're obviously talking about the use of Java through the JVM.
You are wasting your time, every time people correct eye208 he changes his argument. By his own definition C is not a programming language because the only thing that runs C code is a C compiler and all that does is turn it from C into suitable machine-code.

Even his example in post 31 shows that Java is not a programming language (by his definition) as the CPU he mentions runs the byte-code, not the Java code, it again needs to be processed before it can be ran.

So unless you code directly in machine-code all you are doing (by eye208s definition) is writing scripts.

---

### Post by eye208 on 2009-05-08
> **ajackson said:**
> the only thing that runs C code is a C compiler
I have never seen a C compiler executing code. Have you? CptPicard would say: The C compiler is not a Turing-complete machine, not even a virtual one. If you program a loop in C, the compiler doesn't execute it. The CPU does.

C is basically a portable, human-readable description of machine code. In fact you can switch to assembly language anywhere in the source code. C bytecode _is_ machine code. You can point the CPU at it and have it execute the program. What happens if you point the CPU at Python bytecode? Segmentation fault! Python bytecode is not executable. It's not a program but a script to control a program.

And that's why it's impossible to write an operating system in Python.

---

### Post by Kilon on 2009-05-08
> **eye208 said:**
> 

C is basically a portable, human-readable description of machine code. 




no it is not , only assembly code is. 

C encapsulates in one statement several machine code statements the same as python. Each high language moves further away from machine code structure. In summary C has alot more similarities with Python that it does to assembly and machine code.

---

### Post by eye208 on 2009-05-08
> **Kilon said:**
> no it is not , only assembly code is. 

C encapsulates in one statement several machine code statements
Are you familiar with the term "macro assembler"?

---

### Post by ajackson on 2009-05-08
> **eye208 said:**
> C is basically a portable, human-readable description of machine code.
No it is a programming language that gets converted into machine code by a compiler. There is a big difference.

> **eye208 said:**
> C bytecode _is_ machine code.
:lolflag:
You really believe that don't you?

> **eye208 said:**
> What happens if you point the CPU at Python bytecode? Segmentation fault! Python bytecode is not executable. It's not a program but a script to control a program.
OK now you have previously stated that Java is a programming language. What happens if you point the CPU at Java byte-code? Yep Segmentation fault!

Therefore you have now contradicted yourself (again) because if the CPU barfs when pointed at byte-code the language that produced that byte-code is not a programming language (your own definition).

Now lets say you compiled a C program, sorry script, for a PPC CPU, what would an i386 CPU do if you tried to run that C "bytecode"? I think it would segfault. Does that mean that C still isn't a programming language?

There may be a CPU that can run Java byte-code but there are many that can't, does that mean that Java is only a programming language for that particular chipset and just a scripting language for every other chipset?

Oh and nice to see you changed your argument (again). Do yourself a favour and stop digging.

---

### Post by ajackson on 2009-05-08
> **eye208 said:**
> Are you familiar with the term "macro assembler"?
Are you familiar with the term "changing argument"?

---

### Post by Kilon on 2009-05-08
> **eye208 said:**
> Are you familiar with the term "macro assembler"?
macro assembler is still million miles closer to machine code compared to C code. 

Next argument .

---

### Post by ajackson on 2009-05-08
> **Kilon said:**
> Next argument .
Oh it will change, don't worry.

---

### Post by Kilon on 2009-05-08
> **ajackson said:**
> Oh it will change, don't worry.

I hope , I need a good laugh.

---

### Post by eye208 on 2009-05-08
> **Kilon said:**
> macro assembler is still million miles closer to machine code compared to C code.
The only significant difference between a compiler and a macro assembler is the amount of code that gets wrapped in parameterized macros.

---

### Post by ajackson on 2009-05-08
> **Kilon said:**
> I hope , I need a good laugh.
Told you :)

---

### Post by Kilon on 2009-05-08
> **eye208 said:**
> The only significant difference between a compiler and a macro assembler is the amount of code that gets wrapped in parameterized macros.

And because the amount is BIG (wrapped by the C compiler) , so is the significance. 

Next argument.

---

### Post by ajackson on 2009-05-08
OK now we've deviated away slightly can we get back to why Java is a programming language and Python isn't.

Eye208s last set of definitions stated that if a CPU segfaults when presented with Python byte-code it means Python isn't a programming language.

So if a CPU segfaults when presented with Java byte-code then that must make Java a scripting language. However if the CPU segfaults because of trying to run C code compiled for a different chipset doest that in turn make C a scripting language?

C is not machine code, a C compiler turns C code into machine code. 

Java is not machine code, a Java compiler turns Java into byte-code. With the exception of the CPU designed to directly run Java byte-code (how does it cope with non-Java stuff?) you need to run it using the interpreter which produces machine code on the fly.

Python in not machine code, the Python interpreter first compiles the source (pyc files) and then creates machine code on the fly.

Therefore C, Java and Python are **all** programming languages. The can also all be used as scripting languages (see [tcc]("http://bellard.org/tcc/") for C as a scripting language).

---

### Post by Elfy on 2009-05-08
This thread started in 2005, I assume the Op has question answered.

The end is just another roundabout.

---

