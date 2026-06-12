---
title: "difference between JITs and AOTs"
date: 2008-07-27
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-27
to quote wikipedia :
> This, briefly, compiles intermediate code into binary code for a native run while the intermediate code is executing, which may decrease an application's performance. Ahead of time compilation eliminates the need for this step by performing the compilation before execution rather than during execution.

how does that speed up the process for AOTs ? its doing the same thing as JIT , the only differnce that seems to me is that JIT does it parallely while AOT is doing it serially....but still the amount of work done is the same before we actually get the output.

---

### Post by Reiger on 2008-07-27
Well if I read it correctly JIT incurs overhead for having to do expensive compiling operations for virtually every statement, such as trapping errors. However with AOT you only need to perform such statments once.

Consider pseudo code:
JIT:
```

for all statements as statement do:
read statement;
call compiler;
compile statement;
run statement;
return output_of statement;
exit compiler;
end

```

AOT:
```

call compiler
for all statements as statment do:
read statement;
compile statement;
add_statement to program
end

run program;

```

---

### Post by dribeas on 2008-07-27
> **Reiger said:**
> Well if I read it correctly JIT incurs overhead for having to do expensive compiling operations for virtually every statement, such as trapping errors. However with AOT you only need to perform such statments once.

Not really, binaries from classes compiled JIT (Just In Time) are kept in memory. What you suggested in your post is how VMs work when they are not compiling (not JIT, not AOT).

With AOT you get a native executable at once, and then you just run the native code as many times as you want. Pretty much the same as you do with C/C++, once compiled you have a program that just runs. Now, with JIT, compilation is done each time you run the program, and the compiled binary are discarded after the run.

   David

---

### Post by dexter.deepak on 2008-07-28
> **dribeas said:**
>  Now, with JIT, compilation is done each time you run the program, and the compiled binary are discarded after the run.

   David

what i have read is that JIT often caches the compiled binaries, but still it has got the power to discard it depending on the security policies. 
i seem to agree to reiger, but need some more comments,

---

### Post by samjh on 2008-07-28
> **dexter.deepak said:**
> how does that speed up the process for AOTs ? its doing the same thing as JIT , the only differnce that seems to me is that JIT does it parallely while AOT is doing it serially....but still the amount of work done is the same before we actually get the output.

AOT basically produces system-dependant code which is be executed natively by a runtime.

JIT has the VM convert system-independent bytecode into executable code on-the-fly.

AOT results in better application start-up performance and memory usage.  However because the code is system-dependant, it cannot be optimised for a specific machine at runtime, so some special cases may run slower than if JIT is used.  The code produced by an AOT compiler is generic for a particular platform.

JIT is more cross-platform because the resultant bytecode is not system-dependant, but the requirement for a VM and the JIT compilation itself results in a memory hit.  On the flip-side, a JIT compiler can perform optimisations specific to the machine running the VM, so some special cases may result in better performance than AOT compiled execution.

---

### Post by pmasiar on 2008-07-28
> **samjh said:**
> JIT compiler can perform optimisations specific to the machine running the VM, so some special cases may result in better performance than AOT compiled execution.

Not only that; JIT has better info that AOT what is happening at the runtime, wrt polymorphisms and other cool tricks: [Dynamic Languages Strike Back](http://steve-yegge.blogspot.com/2008/05/dynamic-languages-strike-back.html). It is just so much simpler to optimize at runtime than ahead of runtime, and compilers are getting smarter and faster.

---

### Post by dexter.deepak on 2008-07-29
thanks a lot to all of you for responding , but i have yet a dangling confidence...
> **samjh said:**
> AOT basically produces system-dependant code which is be executed natively by a runtime.

JIT has the VM convert system-independent bytecode into executable code on-the-fly.

 and this is what i read in wikipedia about jit:

> At the time the bytecode is run, the just-in-time compiler will compile some or all of it to native machine code for better performance

---

### Post by samjh on 2008-07-30
I'm not sure what you mean by "confidence".

In a nutshell, AOT is "ahead of time".  That is, compiled before execution.  JIT is "just in time".  That is, compiled during execution.

---

### Post by dexter.deepak on 2008-07-30
> **samjh said:**
> In a nutshell, AOT is "ahead of time".  That is, compiled before execution.  JIT is "just in time".  That is, compiled during execution.
i got that point. 

i will retry to state my doubt.
you say , that JIT has the VM convert SYSTEM-INDEPENDENT bytecode into executable code on-the-fly.
while the wiki says ;
the just-in-time compiler will compile some or all of it to native machine code (which i suppose is SYSTEM-DEPENDENT)

---

### Post by pmasiar on 2008-07-30
> **dexter.deepak said:**
> i got that point. 

i will retry to state my doubt.
you say , that JIT has the VM convert SYSTEM-INDEPENDENT bytecode into executable code on-the-fly.
while the wiki says ;
the just-in-time compiler will compile some or all of it to native machine code (which i suppose is SYSTEM-DEPENDENT)

System-independent bytecode is **input** of the JIT compiler. native code is the output. Still confused? :-)

---

### Post by dexter.deepak on 2008-07-30
> **pmasiar said:**
> System-independent bytecode is **input** of the JIT compiler. native code is the output. Still confused? :-)
yes i am.
this is what samjh had to say about jit :
> JIT is more cross-platform because the RESULTANT BYTECODE is NOT system-dependant

1. he says the resultant (output) to be bytecode, and you say bytecode to be the input.
2. if the native code is output (as you said), how can it be system-independent (as samjh says).

pardon me this time, if i am being irresistibly STUPID :)

---

### Post by samjh on 2008-07-31
> **dexter.deepak said:**
> yes i am.
this is what samjh had to say about jit :


1. he says the resultant (output) to be bytecode, and you say bytecode to be the input.
2. if the native code is output (as you said), how can it be system-independent (as samjh says).

pardon me this time, if i am being irresistibly STUPID :)

I should have been clearer.

Let's take Java as an example.

If you compile a Java source file using javac, it produces system-independent bytecode.

When that bytecode is executed using the java runtime, the Hotspot VM will convert that system-independent bytecode into native machine code.



Now, an example of AOT.  Let's say... Visual Basic 6 (legacy, not .NET):

You compile the source using the Visual Basic compiler.  The resultant code is system-dependent.  In fact, it will seem like native machine code.

When you execute it, VB runtime is used to execute the "compiled executable".

---

### Post by Parthasarathi on 2011-04-25
[COLOR=black][FONT=Verdana]**Hi,**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Sorry to jump into the forum without any prior notice...![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I was reading through the series of explanation exchanged so far...It explains very well, however there is one very particular area where I seems to be confused!:confused:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I want to address this problem from the very root...**the Question whether “there is any real necessity of using the AOT concept”** from a **Procedural Language (PL)** and **Object Oriented (OOP) Programming Language** perspective. Say for e.g., after writing a program in the above two types of languages, if we do not consider the added facility and intricacies and complexities of OOP(s) from a programming view, then the overall and general flow of program synthesis can be captured as follows:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]A.    [/FONT][/COLOR]****[COLOR=black][FONT=Verdana]Common phase for [1] PL (e.g. “C” Language) and [2] OOPL (e.g. “JAVA”, where AOT and JIT works):[/FONT][/COLOR]**[COLOR=black][FONT=Verdana] Compilation.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]B.    [/FONT][/COLOR]****[COLOR=black][FONT=Verdana]Output of “Compilation”:[/FONT][/COLOR]**[COLOR=black][FONT=Verdana] 1) PL – Object Code and 2) OOPL (e.g. “Java”) – Applet code. – Both of these are **intermediate code which cannot be executed immediately** by the runtime environment. However the intermediary code generated through the compilation of JVM is much more robust (flexible enough for adjusting itself with different platforms) and hence can be used between multiple platforms, where as the intermediary code generated by PL compiler lacks that technology of flexibility and hence cannot be used by the different runtime time sub-routines available in different cross platform environment. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]     [/FONT][/COLOR][COLOR=black][FONT=Verdana]To say it in a simple way, maybe the inter-code conversion complexities increases so much [/FONT][/COLOR][COLOR=black][FONT=Verdana]that the “Runtime Sub-routine” is not sufficient enough to handle the conversion of “Object Code” [/FONT][/COLOR][COLOR=black][FONT=Verdana](generated out of compilation of PL program) to respective platform dependent code single-[/FONT][/COLOR][COLOR=black][FONT=Verdana]handedly, on the contrary which is actually required and a must, to make the language appears to be working like a platform [/FONT][/COLOR][COLOR=black][FONT=Verdana]independent program.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]C.    [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]If you look into the above point the procedural language could have acted as a platform independent Language, only the problem is that they are not equipped to do so, perhaps because of the fact that there is no dadicated VM (Like JVM for JAVA) available for them to aid them into the process.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]D.    [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]However PL do reflects the ability of faster execution, since there is no in-between conversion happening when the file is getting executed under the supervision of runtime module, however at the cost of not being able to run on cross platforms.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]We have moved into JIT compilation environment knowingly the pros and cons of its “Run-Time Phase” to enjoy the scope of “Platform Independency” - for which the “conversion” process is a much required step that needs to be there to make OOP language appears to be a platform independent one. So we have agreed to trade “System Time and Storage” against “Platform Independency”, the sacrifice seems “Even” as it is for a greater cause.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]If we compromise “Platform Independency” then the existing PL could have served the purpose. We could have easily created a perfect “Object Oriented Programming Environment” just by introducing certain specific standard characteristics of present Object Oriented Language like Inheritance, Polymorphism etc.  For Example we have in C++.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My question is, “**Why**” after moving **One-Step Ahead** (Through Implementation of JIT Compilation concept) we are **Moving Two Steps Back **[By implementing **AOT** (Ahead Of Time Compilation) which demands compilation and generation of machine dependent code in the very begning] to grab an already existing facility (Reduce Latency and Saving Runtime) which has been considered obsolete and has been discarded at the cost of a much bigger purpose i.e. “Platform Independency”.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]if we have to consider factors like Storage Limitation and System Latency against the liberty of enjoying Platform Independency, performance of which (System Time and Storage Limitations) are only awaiting to be crossed by next frequent up-gradation of Microprocessors and storage capacitors, then I think that we should try to increase scope within JIT environment to make it more robust, instead of selecting the obsolete technology once again.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Please confirm my understanding.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]Thanks & Regards,[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Parthasarathi Chatterjee[/FONT][/COLOR]

---

### Post by jespdj on 2011-04-27
> **Parthasarathi said:**
> 
**[COLOR=black][FONT=Verdana]B.    [/FONT][/COLOR]****[COLOR=black][FONT=Verdana]Output of &#8220;Compilation&#8221;:[/FONT][/COLOR]**[COLOR=black][FONT=Verdana] 1) PL &#8211; Object Code and 2) OOPL (e.g. &#8220;Java&#8221;) &#8211; Applet code. &#8211; Both of these are **intermediate code which cannot be executed immediately** by the runtime environment. However the intermediary code generated through the compilation of JVM is much more robust (flexible enough for adjusting itself with different platforms) and hence can be used between multiple platforms, where as the intermediary code generated by PL compiler lacks that technology of flexibility and hence cannot be used by the different runtime time sub-routines available in different cross platform environment. [/FONT][/COLOR]

Java does not compile to "applet code". It compiles to **byte code**, which is platform-independent and cannot be executed directly by the CPU. C normally compiles to native machine code, which can be directly executed by the CPU.

This all has nothing to do with whether the programming language is procedural or object oriented. Note that C++ is also object oriented, yet it compiles to native machine code just like C. There are even ways to compile Java directly to native machine code instead of byte code.

> **Parthasarathi said:**
> 
**[COLOR=black][FONT=Verdana]C.    [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]If you look into the above point the procedural language could have acted as a platform independent Language, only the problem is that they are not equipped to do so, perhaps because of the fact that there is no dadicated VM (Like JVM for JAVA) available for them to aid them into the process.[/FONT][/COLOR]

As I said, whether a language compiles to byte code or native code does not have anything to do with whether it is a procedural language or an object oriented language. Note that there are also compilers and virtual machines for plain C or C++ ([LLVM](http://llvm.org/) for example).

> **Parthasarathi said:**
> 
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]D.    [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]However PL do reflects the ability of faster execution, since there is no in-between conversion happening when the file is getting executed under the supervision of runtime module, however at the cost of not being able to run on cross platforms.[/FONT][/COLOR]

A program that is compiled ahead-of-time is not necessarily faster than a program that is compiled just-in-time and running on a virtual machine. A JIT compiler can do sophisticated profile-based optimization that a normal AOT compiler can't do, and can therefore in principle generate faster machine code. Whether an AOT compiled program or a JIT compiled program runs faster is almost impossible to predict, because it depends on many details.

It is not so simple that you can say JIT is always slower than AOT and so you cannot conclude that JIT is "one step ahead, two steps back".

---

