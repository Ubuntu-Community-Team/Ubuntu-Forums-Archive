---
title: "Will (does) interpretted dominate compiled?"
date: 2009-11-18
forum: Programming Talk
---

### Post by MichaelBurns on 2009-11-18
I am naive, and uneducated in programming.  My understanding is that C/C++ and FORTRAN are "compiled languages" (the source code itself cannot run, but the compiled code runs on the system itself without the need to run additional applications such as an interpretter) whereas C#, perl, python, java, ... are "interpretted languages" (the source code itself runs, but it requires additional applications such as an interpretter).  This is my very basic rundown of the pros and cons.

I've been increasingly noticing the widespread use, or at least hearing the mention, of interpretted languages (especially the ones that I listed above).  This got me to wondering:

Will compiled languages fade away into the shadows of interpretted languages?  Is this already even the case, and I just don't realize it yet?

Will people eventually stop writing computer programs in compiled languages?  (Here I'm not talking about niches like hardware description, but even then ...)

Is it possible to have an entire OS and all applications running on it to be interpretted?

To what extent does proprietary software play a role (in preventing the use of interpretted language)?

---

### Post by TheBuzzSaw on 2009-11-18
> Will compiled languages fade away into the shadows of interpretted languages? Is this already even the case, and I just don't realize it yet?
In what context? I'd be very afraid of having my graphics drivers writtin in a scripting language.

> Will people eventually stop writing computer programs in compiled languages?
For user applications, maybe...

> Is it possible to have an entire OS and all applications running on it to be interpretted?
What is running the interpreter? ;)

> To what extent does proprietary software play a role (in preventing the use of interpretted language)?
This is why I refuse to accept that "all programming will move to scripting languages" ever. The last thing we need is for some big company to have perfect DRM over what applications can be run. I reserve the right to control my hardware however I like. I will not tolerate any proposal to take languages like C/C++ out of the hands of everyday developers.

---

### Post by MichaelBurns on 2009-11-18
> **TheBuzzSaw said:**
> In what context? I'd be very afraid of having my graphics drivers writtin in a scripting language.Like I said, I am naive.  Can you elaborate.  What is it that a compiled language provides for hardware drivers that a scripted language cannot (even by including something new in the scripted language)?  And anyway, isn't this just a matter of standardizing the graphics (or whatever other hardware) card interface?

> **TheBuzzSaw said:**
> For user applications, maybe...Yeah, that's what I meant for that question.  And, that's what seems to be happening, starting with videos and such on the internet.

> **TheBuzzSaw said:**
> What is running the interpreter? ;)I was thinking (naively again) that there would be no interpretter.  That is, the hardware (processor?) iself would simply understand the script.  Of course, then you could ask, "Which language?" and then, "What about all of the other languages?"  Say the hardware (processor?) understands java.  But you want to write an application in perl.  Then, someone would write a perl interpretter in java.  (I have no idea what I'm talking about, and I have probably made it obvious now.  It almost seems perverse.)

> **TheBuzzSaw said:**
> This is why I refuse to accept that "all programming will move to scripting languages" ever. The last thing we need is for some big company to have perfect DRM over what applications can be run. I reserve the right to control my hardware however I like. I will not tolerate any proposal to take languages like C/C++ out of the hands of everyday developers.Oh, that is the opposite situation to what I was thinking.  I was thinking that, since the compiled executables are just "1's and 0's", then they are easier to protect from sharing and tinkering.  If the executables are just text files that say exactly what they do, then I don't understand how a software company could get away with DRM, because all a "hacker" would need to do is to look in the script for the code that says "don't allow the user to ...", and then simply delete it, right?  I thought that this was the reason that I didn't get the source code for the MS Windows programs that I want, but instead I got the installer applications that do everything behind my back in secret using compiled executables.  I don't see how this sneeky practice could work with a scripted application.

BTW, I just want to point out that I am not trying to promote scripted languages over compiled ones.  In fact, I hate scripted languages (but I don't know why).  I just want to prepare myself, because the world never seems to work the way I think it should.

---

### Post by diesch on 2009-11-18
> **MichaelBurns said:**
> I am naive, and uneducated in programming.  My understanding is that C/C++ and FORTRAN are "compiled languages" (the source code itself cannot run, but the compiled code runs on the system itself without the need to run additional applications such as an interpretter) whereas C#, perl, python, java, ... are "interpretted languages" (the source code itself runs, but it requires additional applications such as an interpretter).  


It's a bit more complicated: The C#, Python and Java source code usually gets compiled to byte code that is then interpreted at run time; some byte code interpreters compile byte code on the fly into native code ("Just in Time Compiler", JIT). 

There are native code compilers for Java, too


> **MichaelBurns said:**
> 
This is my very basic rundown of the pros and cons.

I've been increasingly noticing the widespread use, or at least hearing the mention, of interpretted languages (especially the ones that I listed above).  This got me to wondering:

Will compiled languages fade away into the shadows of interpretted languages?  Is this already even the case, and I just don't realize it yet?


I expect native code compilers to be around for the foreseeable future but also an increase of byte code and JIT compilers and  pure interpreted languages to fade away for anything but application scripting.

---

### Post by denago on 2009-11-18
> **MichaelBurns said:**
> I was thinking (naively again) that there would be no interpretter.  That is, the hardware (processor?) iself would simply understand the script.

If the language is being run natively, and does not require an interprettter, is it still an interpretted language?

---

### Post by nvteighen on 2009-11-18
> **MichaelBurns said:**
> I am naive, and uneducated in programming.  My understanding is that C/C++ and FORTRAN are "compiled languages" (the source code itself cannot run, but the compiled code runs on the system itself without the need to run additional applications such as an interpretter) whereas C#, perl, python, java, ... are "interpretted languages" (the source code itself runs, but it requires additional applications such as an interpretter).  This is my very basic rundown of the pros and cons.

The important thing to have in mind is not whether there is another application running the code or not, but something completely different. 

1. A compiled language is one which needs to transform the source code into some kind of object code before even executing the code. In a compiled language, you can very clearly distinguish between "compile-time" and "run-time".

2. An interpreted language is one which doesn't need to do that transformation and only works in "run-time".

Ok, **then**, you have several types of compilation and interpretation processes. For instance, excepting a system's bootloader, all programs are executed by the OS, so there's always another program running yours, no matter what language you use. There's byte-compilation, which compiles to non-native object code... or languages like Python, which gets byte-compiled automatically before executing code (and always executes the bytecode). There's Lisp, which traditionally allows you to compile natively in order to save loading time, but even though the object code is native, you have to execute it from the Lisp interpreter. Perl is also compiled, but it doesn't save the object code (maybe we can consider this as an interpreted language?).

Interpreted languages are very few: awk, sed, PHP (not sure)...

What you seem to refer to is to static compilation vs. dynamic compilation. The difference is that in the later you can mix "compile-time" and "run-time". The most extreme examples of this is Forth in which you can modify code behaivor depending on what stage you are and arbitrarily start any of both at will. But usually, like in e.g. Python, Perl, Lisp, what happens is that you can define new "objects" (in its non-technical meaning... I'm not referring to OOP here) and compile them during "run-time". In C, Objective-C, C++ or Java, this is impossible: what you've compiled can't be modified.

This is very much related to static typed vs. dynamic typed discipline.

Currently, there seems to be a shift in favor of dynamically compiled/typed languages because of the flexibility they offer to the programmer. You don't have to force types from start, you can create new types on demand, etc. The issue with this is that kind of features are only possible in high-level languages, on top of a lot of abstraction from hardware. This makes code slower and less easier to optimize. On the other hand, statically compiled/typed languages can be optimized because types are known at compile-time... but it reduces flexibility and usually are low-level languages most suitable for hardware programming or very fundamental systems programming (core utilities, e.g.). Java is a weird case because of the peculiar nature of the Java Virtual Machine... you can think of Java as a high-level language compared to the real hardware, but as the lowest-level language inside the JVM... :p

---

### Post by ssam on 2009-11-18
a lot of programs use a clever mix of the two. eg jokosher and pitivi, are both written in python. but for all the heavy work i.e. the GUI and the multimedia functions, they call out to libraries writen in C (GTK and Gstreamer).

Then there is line blurring from things like JIT, compilers for interpreted languages (eg cython), and interpreters for compiled languages (eg CINT).

---

### Post by shadylookin on 2009-11-18
> **MichaelBurns said:**
> 

I've been increasingly noticing the widespread use, or at least hearing the mention, of interpretted languages (especially the ones that I listed above).  This got me to wondering:

Will compiled languages fade away into the shadows of interpretted languages?  Is this already even the case, and I just don't realize it yet?

No. Arguably things are moving away from interpreted and moving toward JIT compilation. 

> 
Will people eventually stop writing computer programs in compiled languages?  (Here I'm not talking about niches like hardware description, but even then ...)

Doubtful, interpreted languages are nothing new. 

> 
Is it possible to have an entire OS and all applications running on it to be interpretted?

Not the entire OS, but I've seen some projects that use a very small amount of asm/c and then the rest in another language. JNode I think it was called, I'm sure there's others

> 
To what extent does proprietary software play a role (in preventing the use of interpretted language)?

Proprietary software doesn't stop you from writing you own software in a language of your choice.

---

### Post by MichaelBurns on 2009-11-18
That's a lot to think about.  Thanks, y'all.

---

