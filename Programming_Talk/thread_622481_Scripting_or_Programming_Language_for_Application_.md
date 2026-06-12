---
title: "Scripting or Programming Language for Application Development?"
date: 2007-11-24
forum: Programming Talk
---

### Post by Majorix on 2007-11-24
OK first off make myself clear by explaining what a scripting language and what a programming language is.
Scripting languages are Python, Ruby, Javascript etc, which are generally not compiled but instead interpreted.
Bigger programming languages are those like C/C++, Java, C#, etc.

So my question is, which of these two divisions should one direct himself, if he wants to develop applications for Linux and Windows, and do some scripting for 3D studios?

Please note that I am not belittling Python or Ruby by not calling them programming languages, in fact I love them, but we all know that they aren't as fast as C.

Thanks.

---

### Post by tyoc on 2007-11-24
Being fast or not doesnt make a programming language bigger or lesser.

Are you sure that python is not compiled?? and that is interpreted? In fact you can "interpret" C code with tcc ;)...

---

### Post by LaRoza on 2007-11-24
> **Majorix said:**
> OK first off make myself clear by explaining what a scripting language and what a programming language is.
Scripting languages are Python, Ruby, Javascript etc, which are generally not compiled but instead interpreted.
Bigger programming languages are those like C/C++, Java, C#, etc.


What about Java (it is interpreted by the JRE)? Or Python compiled? Or a C interpreter?

I would go for Python + C. They both are extensive, crossplatform, mature, and widely used languages. You can write Python modules in C, so you can use the speed of C when it is needed, but Python for everything else.

Python is used for many games (Oblivion and many others) and C is everywhere is GNU software.

---

### Post by NightCrawler03X on 2007-11-24
> **Majorix said:**
> OK first off make myself clear by explaining what a scripting language and what a programming language is.
Scripting languages are Python, Ruby, Javascript etc, which are generally not compiled but instead interpreted.
Bigger programming languages are those like C/C++, Java, C#, etc.

So my question is, which of these two divisions should one direct himself, if he wants to develop applications for Linux and Windows, and do some scripting for 3D studios?

Please note that I am not belittling Python or Ruby by not calling them programming languages, in fact I love them, but we all know that they aren't as fast as C.

Thanks.
The only people who can answer your question are programmers.
You don't need to tell us what a programming language is.

I recommend C over C++ any day.
But, assembler is probably the best choice for just about anyone.

But you want to be able to port the code among different platforms, so assembler is a big no no. Just use C.
I would recommend C++, but the cons of using it are too great (e.g. lack of decent abstract capabilities, frequent memory leaks (code has to be *perfect* in this sense, the list is too large)

As for Java, yes and no. If speed is not a major concern, and you want highly portable code, yes. If this is the case, but speed IS a concern, then no.

---

### Post by LaRoza on 2007-11-24
> **NightCrawler03X said:**
> 
I recommend C over C++ any day.
But, assembler is probably the best choice for just about anyone.

I prefer C over C++ also.

Assembler is not the best choice for someone wanted to write code for Linux and Windows, like the OP.

---

### Post by LaRoza on 2007-11-24
> **tyoc said:**
>  In fact you can "interpret" C code with tcc ;)...

Thanks for letting me know of tcc. I see it works for Windows and Linux and can compile (link and assemble) anywhere, and interpret

It looks quite useful. Thanks.

---

### Post by Majorix on 2007-11-24
Assembler is crap. You write hundreds of lines of code just to say "Hello World".

I didn't know Python could be compiled. What is a tool to do that?

And I thought C was only used in developing the kernel, and the rest was done with Python, hence this topic, am I wrong then? And no matter how fast the compiler is, it will take ages to compile a big project. There are even cartoons of programmers playing games with each other while the code is compiling. I would post that cartoon but don't have the link saved.

---

### Post by HermanAB on 2007-11-24
"Assembler is crap. You write hundreds of lines of code just to say "Hello World"."

There is something called a Macro Assembler.  All modern assemblers can do that.  Lots of important code is still written in assembler.

However, the important thing to remember is to use the right tool for the job.

---

### Post by LaRoza on 2007-11-24
> **Majorix said:**
> Assembler is crap. You write hundreds of lines of code just to say "Hello World".

I didn't know Python could be compiled. What is a tool to do that?

And I thought C was only used in developing the kernel, and the rest was done with Python, hence this topic, am I wrong then? And no matter how fast the compiler is, it will take ages to compile a big project. There are even cartoons of programmers playing games with each other while the code is compiling. I would post that cartoon but don't have the link saved.

Assembler is used in the Linux kernel, bootloaders and some applications. It is usually used inline with C. Hello world doesn't take much to write in Assembly, and is easy to understand.

Freeze, and Python itself can compile Python code. You usually compile it to byte code (like Java).

```

; nasm filename.asm -f elf
; ld filename.o -o hw

section .data
 hello: db 'Hello world!',10
 len: equ $-hello
 
section .text
 global _start
 
_start:
 mov eax,4
 mov ebx,1
 mov ecx,hello
 mov edx,len
 int 80h
 
 mov eax,1
 int 80h

```

C:

```

/*gcc filename.c -o hw*/

#include <stdio.h>
int main(int argc,char ** argv)
{
    printf('%s","Hello world");
    return 0;
}


```

The C code is more confusing and more than half the size of the NASM code. I wouldn't write the NASM code as I posted it, I would use a function to do it, this would shorten the code, if the function where included in the file (like the C's printf).

---

### Post by Majorix on 2007-11-24
Are you sure that Assembler code makes more sense? The C code is perfectly familiar to me and is much shorter, and you can compile it on any processor. But please, let's not discuss Assembler here, as it is slightly off-topic.

About Python... When I search for "python freeze" on Synaptic I get no results. And I don't know how exactly to convert python code to bytecode using python itself. Can you please explain? Thanks.

---

### Post by LaRoza on 2007-11-24
> **Majorix said:**
> Are you sure that Assembler code makes more sense? The C code is perfectly familiar to me and is much shorter, and you can compile it on any processor. But please, let's not discuss Assembler here, as it is slightly off-topic.

About Python... When I search for "python freeze" on Synaptic I get no results. And I don't know how exactly to convert python code to bytecode using python itself. Can you please explain? Thanks.

C code is familar to you, true, but you don't know how it works (possibily). The assembly code makes perfect sense if you are familiar with it, in fact, Assembly programmers can read almost any assembly language. A C programmer would have problems with PHP's for loops, even though PHP is a C syntax language.

NASM and other Assembly languages are more cross platform than others.

Freeze ships with Python: [http://wiki.python.org/moin/Freeze](http://wiki.python.org/moin/Freeze)

Open a terminal and navigate to the directory with the code you want to compile to byte code, open an interactive session and import the program, a *.pyc file is created that is runnable with the Python interpreter.

That will run the program, to do it otherwise:
> 
import py_compile

py_compile.compile("mymodule.py")


---

### Post by LaRoza on 2007-11-24
For more: [http://effbot.org/zone/python-compile.htm](http://effbot.org/zone/python-compile.htm)

---

### Post by NathanB on 2007-11-24
> **LaRoza said:**
> Assembler is used in the Linux kernel, bootloaders and some applications. It is usually used inline with C. Hello world doesn't take much to write in Assembly, and is easy to understand.

```

; nasm filename.asm -f elf
; ld filename.o -o hw

section .data
 hello: db 'Hello world!',10
 len: equ $-hello
 
section .text
 global _start
 
_start:
 mov eax,4
 mov ebx,1
 mov ecx,hello
 mov edx,len
 int 80h
 
 mov eax,1
 int 80h

```

The C code is more confusing and more than half the size of the NASM code. I wouldn't write the NASM code as I posted it, I would use a function to do it, this would shorten the code, if the function where included in the file (like the C's printf).

Just link directly to C's library like so --
```

; nasm -f elf -o uftw.o uftw.asm
; gcc -s -o uftw uftw.o
extern exit
extern printf
global main

section .data
	mesg:	db	"Ubuntu FTW!", 10, 0

section .text
main:
	push mesg
	call printf
	push DWORD 0
	call exit

```

Another option is to make use of NASM's impresive macro capabilities --

[http://luxasm.cvs.sourceforge.net/luxasm/luxasm/_nasm/include/](http://luxasm.cvs.sourceforge.net/luxasm/luxasm/_nasm/include/)

---

### Post by slavik on 2007-11-25
would it help if I told you that large companies involved with stock trading use C++ and Java?

would it help if I said that large banks still use software written in COBOL on mainframes?

would it help if I told you that at least one mission critical OS has all of its main parts in C?

would it help if I told you that just about every engineer writes nuclear explosion simulation calculations in FORTRAN?

would it help you if I told you that most (if not all) the research into programming a quantum computer is done in Haskel?

should I continue?

There is a right tool for every problem.

When I see:
map { $_++ } @array;

I know exactly what's going on.

Writing large software in one language or another (from the same class/type) is not somehow inherently easier (the Python folks would like you to believe that, that is the feeling I get from these forums). C can be just as object oriented as Java.

Here's how to pick a language:
1. Make a list of languages that you know about that would fit this task.
2. Pick the one you are most comfortable with.

---

### Post by LaRoza on 2007-11-25
> **slavik said:**
> 
Here's how to pick a language:
1. Make a list of languages that you know about that would fit this task.
2. Pick the one you are most comfortable with.

This leaves no room for learning a language. Sometimes spending some time with a reference learning a new language is worth the time.

If one doesn't have a lot of experience, finding another language may be the best solution.

---

### Post by Balazs_noob on 2007-11-25
well i think if you want to have a tool for every job
then you need C, Java, Python...

C for something that really needs speed .....
(i know some C but i never really liked it,
and i don't really need for the stuff i do)

Java if you want to write cross-platform Programs and
you want to be 100% sure that it will work on Linux
and Win .. ( of course if you really want to then you can
write something that is not cross-platform with Java  )
and if you want to work as a Programmer Java has
a lot of jobs...

and i think if you read any thread here you heard about
Python a lot ;)

---

### Post by slavik on 2007-11-25
> **LaRoza said:**
> This leaves no room for learning a language. Sometimes spending some time with a reference learning a new language is worth the time.

If one doesn't have a lot of experience, finding another language may be the best solution.
sure, learning a new language is nice when you **have time** :)

---

### Post by LaRoza on 2007-11-25
> **slavik said:**
> sure, learning a new language is nice when you **have time** :)

If someone asks about learning, I assume they have the time.

---

### Post by LaRoza on 2007-11-25
> **Balazs_noob said:**
> well i think if you want to have a tool for every job
then you need C, Java, Python...


You can scrap Java there, it doesn't do anything the other can't. Using C is the safest way to do anything, every system will have a C compiler (it is a prerequisite to survival) and has a well defined stanard.

---

### Post by Balazs_noob on 2007-11-25
> **LaRoza said:**
> You can scrap Java there, it doesn't do anything the other can't. Using C is the safest way to do anything, every system will have a C compiler (it is a prerequisite to survival) and has a well defined stanard.

you can't scrap Java ;) at least if you want a job as a
Programmer... almost everywhere you go they ask for
Java or .Net and .Net doesn't have great compatibility with Linux :)

there are a few jobs with c/c++ too but not so many
as with Java and .Net

but if the OP has no plans of becoming a professional
programmer then he can scrap Java
:lolflag:

---

### Post by Klipt on 2007-11-25
> **LaRoza said:**
> C:

```

/*gcc filename.c -o hw*/

#include <stdio.h>
int main(int argc,char ** argv)
{
    printf('%s","Hello world");
    return 0;
}


```

The C code is more confusing and more than half the size of the NASM code. I wouldn't write the NASM code as I posted it, I would use a function to do it, this would shorten the code, if the function where included in the file (like the C's printf).

Is this less confusing?

```

#include <stdio.h>
int main()
{
    printf("Hello world");
    return 0;
}


```

---

### Post by Kadrus on 2007-11-25
I suggest using C..that's my opinion...and a little bit of Python will be helpful along the way..

---

### Post by ankursethi on 2007-11-25
Use Python for most of the program, and recode the processor intensive parts in C for speed improvements. Your program will run as fast as any Java/Mono(.NET) program, or even faster.

I've always felt that C and Python go together. I take satisfaction from the fact that no matter what I'm forced to learn for the sake of good grades at school, or for a job somewhere, I can still continue my programming with C+Python.

That said, Ruby and Python are pretty much interchangeable (not syntactically or paradigm-wise, but in terms of what you can do with them and how fast).

---

### Post by tyoc on 2007-11-25
> C can be just as object oriented as Java.Yes, there is gnome and related, also asm can be as OO like you want and can do (even if you dont want to code all all the way, with help of macros or modifiying directly the code), also remember that OO is a paradigm that mean a "way of do things", and not being more or less, you can always work with our tool in a certain way, also there are other proofs like: [http://students.ceid.upatras.gr/~sxanth/lwc/]("http://students.ceid.upatras.gr/%7Esxanth/lwc/") yes it translates C++ to C ;)... and that is a very nice way if you only have a C compiler, but no C++ hehe.

Also I remember a quote (thought now I dont like much) that say something like "OO is a state of mind" then you put your mind in that state, and with tht you can go on in the lang of choice.

> you can't scrap Java :wink: at least if you want a job as a
Programmer... almost everywhere you go they ask for
Java or .Net and .Net doesn't have great compatibility with Linux :smile:Where I live I only have found 3 references to python in a page that has job proposals, none of them request Python for do the job (like half month of that) only some like "if you know some bash, perl, python, awk, etc would be nice". Im working on BREW for mobile devices now in C, but there is a part of web development in that company that I can use Python/django at less (hope to start be taked into account for help in that job).

Also I think at less MS doesnt have crosscompatibility with .NET (fact they app only support Windows), cross compatibility is done in mono, not in MS .NET (take them as products).

> Assembler is crap. You write hundreds of lines of code just to say "Hello World".You are using the wrong tool for the so common hello world thingy :P... you know asm is master the internals, not write trivial code :D hehe, also there is SIMD, wich is a lot more for optimization... also you need to target a device. In fact, there are assemblers writed in assembler, or in C, there are complete OS writed in asm, there are complete 3D games writed in asm and so on... there exist a lot of programming folklore out there, never stop yourself from learning a new lang... even I have learned a little about a lang called TXL (that perhaps some of you can argee that is not a "programming lang") only for have fun doing something different :P.


> it will take ages to compile a big project. There are even cartoons of programmers playing games with each other while the code is compiling.

Yes but only the first time (ie no obj of a prior compile) or after a clean, and only if is really big... normally you will have enough experience if you work in such a big project. Also you can do other things than "play" ;)... is not a fact, is only something to make you laugh.

---

### Post by tenmillionmilesaway on 2007-11-25
When choosing a language for application development I would go for the one that has the best tools for it,  by that I mean best IDE's, best libraries and best documentation.

All this talk of Java being slow is pointless, it is easily fast enough for almost any job.  I would bet that your main bottleneck will be the database anyway.  Its funny how you never hear python is too slow for X.

> you can't scrap Java  at least if you want a job as a
Programmer... almost everywhere you go they ask for
Java or .Net and .Net doesn't have great compatibility with Linux

I totally agree, when I was looking for a job i didn't see the words python or ruby anywhere, everything was Java or .net (with some c/c++).

If you really like python and ruby then you could look at [groovy]("http://groovy.codehaus.org") which has lots of nice features, including being totally compatible with Java and running on the JVM. so instead of calling C from python you call Java from groovy.

---

### Post by LaRoza on 2007-11-25
> **Klipt said:**
> Is this less confusing?

```

#include <stdio.h>
int main()
{
    printf("Hello world");
    return 0;
}


```

It is the same thing, and I didn't find it confusing, just that the C code didn't really say what it was doing, whereas the NASM code was easy to find out what was happening.

---

### Post by Majorix on 2007-11-25
I am currently skimming through a C tutorial, trying to remember C. I will use it to write Python modules that need to execute fast. But how exactly do I do it? Can someone please explain?

---

### Post by LaRoza on 2007-11-25
> **Majorix said:**
> I am currently skimming through a C tutorial, trying to remember C. I will use it to write Python modules that need to execute fast. But how exactly do I do it? Can someone please explain?

[http://docs.python.org/api/api.html](http://docs.python.org/api/api.html)

My wiki, and the Python site (which is linked to in my wiki) will have the answers to most questions.

---

### Post by Balazs_noob on 2007-11-25
hmmm.... if i remember you haven't mentioned yet what
kind of apps you want to program [Majorix]("http://ubuntuforums.org/member.php?u=252579") ;)
or you just want to learn general programming ??

---

### Post by LaRoza on 2007-11-25
> **Balazs_noob said:**
> hmmm.... if i remember you haven't mentioned yet what
kind of apps you want to program [Majorix]("http://ubuntuforums.org/member.php?u=252579") ;)
or you just want to learn general programming ??

> 
So my question is, which of these two divisions should one direct himself, if he wants to develop applications for Linux and Windows, and do some scripting for 3D studios?


It was a vague question and I assume it was for general programming.

For Linux, C is a must, and for Ubuntu, Python is recommended. So C and Python is the best pair. The widespread use and power of Perl makes it a very good choice for learning.

---

### Post by Balazs_noob on 2007-11-25
i did a little research ....
**monster.co.uk :**
Java jobs 957
.NET (C#) jobs 855
C/C++ jobs : 661
Python jobs 75
Ruby jobs 22
at Ruby + Python they also require pearl and other
languages

i have also searched at monster.de and at American sites
mostly i got the same results ....
this is the job market today....
and i have chosen Java because it will be fully open source soon,
i like to program in it ;) , great IDE-s, fully cross-platform, great for
mobile development (J2ME, sonly on Android) and i have never
experienced speed issues... ( i don't know how could they mess up Azureus 
that badly :S )

and after Python 3000 will come out i will start that too, because making
small sites in Java is a mess :D

---

### Post by LaRoza on 2007-11-25
There is a difference between "Getting a corporate job programming" and "Developing applications for WIndow and Linux". If you want a job, learn .NET, Java. The OP didn't ask about that.

The criteria I gathered:

* The language(s) must work on WIndows and Linux
* They must be good for developing applications on both.

Given these two, C (which is used for almost everything in Linux) and Python (which is used for almost everything else, along with Perl) are the best choices.

With these two languages, you get a pair which work together, and can handle almost any level of programming in Linux and Windows, yet work equally well in either.

---

### Post by tyoc on 2007-11-25
Also for example, there are jobs where there is perl or perhaps python... one of them I found was on a human gnome, but I don't know bioinformatics and related things... if not I will apply, thought I went fine at interview in other areas, hehe. They have said me that they work on perl and a some python.

---

### Post by pmasiar on 2007-11-29
If you want boring job as enterprise programming drone, .NET or Java is your best bet.

If you want interesting job in web app startup, Python or Ruby is better. 

And the best thing is to learn some science (chemistry, engineering, biology etc) and Python, so you can do your own programming.

---

### Post by slavik on 2007-11-29
> **Balazs_noob said:**
> i did a little research ....
**monster.co.uk :**
Java jobs 957
.NET (C#) jobs 855
C/C++ jobs : 661
Python jobs 75
Ruby jobs 22
at Ruby + Python they also require pearl and other
languages

i have also searched at monster.de and at American sites
mostly i got the same results ....
this is the job market today....
and i have chosen Java because it will be fully open source soon,
i like to program in it ;) , great IDE-s, fully cross-platform, great for
mobile development (J2ME, sonly on Android) and i have never
experienced speed issues... ( i don't know how could they mess up Azureus 
that badly :S )

and after Python 3000 will come out i will start that too, because making
small sites in Java is a mess :D
consider any unix/linux administrator job as requiring Perl/Python/Ruby

---

### Post by pmasiar on 2007-11-29
Also, every Python hacker worth his salt knows that best Python jobs (the one posted by companies with clue) are posted on  python.org mail list.

---

