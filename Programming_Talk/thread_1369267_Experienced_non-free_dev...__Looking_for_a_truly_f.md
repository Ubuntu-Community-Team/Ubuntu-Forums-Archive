---
title: "Experienced non-free dev...  Looking for a truly *free* language/libraries"
date: 2009-12-31
forum: Programming Talk
---

### Post by Linux_Lurker on 2009-12-31
Hello All,

I want to contribute to free and open-source software(I haven't decided exactly what I want to contribute though, LOL).  I dare say that I'm pretty good with C#/.NET, coming from a corporate environment, but I want to avoid Monodevelop and C#, after reading GNU's warning about the dodgy "promise" that Microsoft made regarding C#, and the legally embattled aspects of the Mono .NET implementation.

I checked out Java, I don't think I'd have any problems picking it up quickly, but I'm confused about whether it's considered "free as in speech" or not at this point.  If someone can point me to free/non-legally-embattled IDEs/Libraries/compilers, I would appreciate it.

I also have made a token attempt at learning C++, however, my initial impression is that it's somewhat of a step backwards from Java or C#.  I'm sure that there are plenty of good C++ libraries, and that most are probably free, but I'm not really sure where to start.

I'm open to other suggestions, provided they have a robust, stable IDE, and good libraries.

Thanks

---

### Post by shadylookin on 2009-12-31
> **Linux_Lurker said:**
> Hello All,

I want to contribute to free and open-source software(I haven't decided exactly what I want to contribute though, LOL).  I dare say that I'm pretty good with C#/.NET, coming from a corporate environment, but I want to avoid Monodevelop and C#, after reading GNU's warning about the dodgy "promise" that Microsoft made regarding C#, and the legally embattled aspects of the Mono .NET implementation.

I checked out Java, I don't think I'd have any problems picking it up quickly, but I'm confused about whether it's considered "free as in speech" or not at this point.  If someone can point me to free/non-legally-embattled IDEs/Libraries/compilers, I would appreciate it.

I also have made a token attempt at learning C++, however, my initial impression is that it's somewhat of a step backwards from Java or C#.  I'm sure that there are plenty of good C++ libraries, and that most are probably free, but I'm not really sure where to start.

I'm open to other suggestions, provided they have a robust, stable IDE, and good libraries.

Thanks

java has been open sourced, but open source apps written in java are few and far between(at least in my experience)

However I wouldn't really let the GNU guys persuade you to give up C#. Since the software patent system is so screwed up almost every trivial thing has been patented. The odds are pretty high that no matter what you do you're infringing on a patent

---

### Post by Can+~ on 2009-12-31
> **Linux_Lurker said:**
> I checked out Java, I don't think I'd have any problems picking it up quickly, but I'm confused about whether it's considered "free as in speech" or not at this point.  If someone can point me to free/non-legally-embattled IDEs/Libraries/compilers, I would appreciate it.

Languages itself are always free, the difference lies between the interpreter/compiler. In that sense sun-java JRE/JDK were closed source, but they now are moving towards a more OSS friendly environment. (Take a look at sun-java6-<stuff> vs openjdk-6-<stuff>)

> **Linux_Lurker said:**
> I also have made a token attempt at learning C++, however, my initial impression is that it's somewhat of a step backwards from Java or C#.

In the sense of abstracion, yes. C++ deals with pointers and memory management that you never see in Java, nor C# (Both garbage-collected languages). And C/C++ has a huge collection of libraries available as [FONT="Courier New"]apt-get install libsomething[/FONT]. The core language doesn't include many things.[/QUOTE]

> **Linux_Lurker said:**
> I'm open to other suggestions, provided they have a robust, stable IDE, and good libraries.

That's pretty much Java: Eclipse/Netbeans are great and robust IDEs, and have a big collection of included libraries.

On the other hand, doing a move from C# to Java is pretty much closing your knowledge to fully OO languages. It's good to have a change, make things fun again and learn new things, like the functional paradigm. As someone who also had a big-IDE solid founding mentality, I made the jump to Python and it rocked my world (don't quote that out of context)

Besides, it has a [huge collection of libraries]("http://docs.python.org/library/index.html") included, and a pretty simplistic syntax. Everything is an object, although you're not enforced to use classes, and it also has functions as first-class citizens.

---

### Post by Axos on 2009-12-31
Please correct me if I'm wrong but I believe Sun open-sourced the Java compiler and associated tools but did **not** open-source the (massive) runtime library. So the runtime library is being reimplemented (if not in whole, at least in part). When I last tried running one of my GUI apps under the open runtime library, it looked like **crap**, and that's being very, very kind. So I use Sun's closed-source stuff instead (both the compiler and libraries). Maybe someday the open stuff will work as well as the closed stuff.

---

### Post by caelestis2 on 2010-01-01
C++ is not a step down. Java is a step down because the automated memory management isn't as great as when coded in. It's interpreted and slower as well. And don't tell me Java is faster than C++ in anything because bytecode will always have overhead compared to compiled machine code.

---

### Post by shadylookin on 2010-01-01
> **caelestis2 said:**
> C++ is not a step down. Java is a step down because the automated memory management isn't as great as when coded in. It's interpreted and slower as well. And don't tell me Java is faster than C++ in anything because bytecode will always have overhead compared to compiled machine code.

sigh. 

Automated memory management allows developers the ability to write programs faster because they don't have to deal with memory management. Java is JIT compiled. While true it is usually slower than c++ it's rarely an issue.

---

### Post by caelestis2 on 2010-01-01
Okay, you are analyzing it from an economic point of view where rapid app dev. is an issue. I am going from a performance-wise point of view in terms of which language is the step down from the other.

---

### Post by CptPicard on 2010-01-01
> **caelestis2 said:**
> Okay, you are analyzing it from an economic point of view where rapid app dev. is an issue. I am going from a performance-wise point of view in terms of which language is the step down from the other.

Since you're new here... read [this thread]("http://ubuntuforums.org/showthread.php?t=851794"), it accumulated this discussion a long time ago.

Mind you, I would not say much about Java in particular; it's just simply a straightened-out C++ which has in the past decade stagnated while C# has been taking the core idea further.

The point is... the idea that there is a up/down hierarchy of languages where in particular, for some weird reason, memory management is some sort of Magic Ingredient of Power is wrong and always gives me the impression of a "programmer in training" boasting about his pointers because he still bothers with busy-work and is impressed by "constant factors" in the runtime, preferring to write something in assembly instead of implementing a better algorithm (probably because it is doubtful that he knows one exists).

Actually, some higher-level language constructs such as closures pretty much require a memory manager as the closure environment's lifecycle management pretty much has to be transparent because of the way the closure behaves... and considering that the closure is straight from formal logic and a very important and flexible language construct, I would have trouble seeing that a language that incorporates them would simply be seen as a "step down" simply because it incorporates an algorithm that removes some of the "tedious menial labour" of program construction in exchange for a more expressive tool for the programmer...

---

### Post by Linux_Lurker on 2010-01-01
I appreciate the input.  I guess I may atleast start out in C#, I'm more interested in being a productive developer than I am in learning new skills, but possibly with the intent of learning C++.  Can anybody direct me to some good links/tutorials on the following subjects:

1.  Memory management, and those funny little C++isms in punctuation{::, *, &, ->} 
2.  Libraries, which ones are actually good, and how to use 'em in Linux.(preferably with robust code-completion).
3.  Header files, and their proper use.
4.  GUI creation in Linux, libraries, visual GUI editors, etc...

---

### Post by 10nitro on 2010-01-02
If you are ever concerned about any libraries or anything, `sudo apt-get install vrms'.  vrms is a nifty little program that will let you know about any issues rms might have with software on your system (that is installed through apt, it won't catch stuff you compile yourself).


> 1. Memory management, and those funny little C++isms in punctuation{::, *, &, ->} 
`::' is the only C++ism there, the others are memory management punctuation.

Pointers:```

//summery:
mem_location == &varname; // & gives the location in memory of the variable.
varname == *mem_location; // * gives the value stored at `mem_location'
// a variable storing a memory location is called a ``pointer''

//example 1:
int var = 1;
int *ptr = &var; // a pointer to var

//example 2:
int var = 1;
int *ptr; // a pointer
ptr = &var; // make the pointer point to var

/* I both of these examples, `*ptr' can be used interchangeably with
 * `var' in any following code, as can `ptr' and `&var'
 */

```

Structures (a class without functions/methods*):```

struct struct_name {
    int foo;
    int bar;
};

struct struct_name struct_var;
struct struct_name *struct_ptr = &struct_var; // a pointer to struct_var

struct_ptr->foo = (*struct_ptr).foo = struct_var.foo = (&struct_var)->foo

```

*Java calls funtions `methods', which makes me think C# might too; they are the same thing.  Also, C does not have classes, only structs.  In C++ they are the same thing, but one defaults to public, the other to private (don't rely on defaults anyway).  This means that structs can have functions, but programmers have a feeling in their gut that if they give it many, they should rename it a class.

Anyway, I am a C programmer, and can only teach you the C++ I've taught myself in the last week by pooring over the code the a certain app.

I would personally think that C++ would be the perfect language, IF they'd stopped at adding classes.  Instead, they had to go and change I/O streams, memory allocation, the standard library...

---

### Post by ssam on 2010-01-02
a new entry is [Vala]("http://live.gnome.org/Vala").

Aims to gave similar features to C#, but using gnomes GObject system. it is then 'compiled' into C. 

the openmoko/freesmartphone people are switching their apps from python to vala for a boost in speed.

---

### Post by Linux_Lurker on 2010-01-06
@10nitro:  I appreciate the example, it does clarify some things, I think I'm at the "well, what do I do with it?" stage now :D  I guess the next thing to do is download some random source tarballs and see how others used it.

@ssam:  Vala looks perfect, I'm still trying to get a good setup for it.  Monodevelop doesn't have Vala code-completion, and I'm having to hunt down the dependencies for Val(a)IDE.  I'm also trying to install gedit-valencia, but it's being a PITA too.  However, if I can get a working IDE, I believe Vala is the way to go.

Thanks, everybody :)

---

