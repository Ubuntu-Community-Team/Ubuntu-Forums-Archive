---
title: "GCC Auto Casting?"
date: 2010-04-18
forum: Programming Talk
---

### Post by Pergi on 2010-04-18
Hello Ubuntuers! I have started learning C Programming Language and i have a question regarding the GNU C Compiler included in GCC.

I have the following code:

```
int x;
float y = 6.4;	
x = y;
printf("x = %d\n", x);
```

The result is **x = 6**

Why the compiler doesn't give an error about the casting? I thought that the correct code is:

```
int x;
float y = 6.4;	
x = (int) y; // casting
printf("x = %d\n", x);
```

GCC is doing auto casting or what? On the book that i read it mentions that:
*"This type of “reverse promotion” can result in a loss of data so it requires more intervention (i.e., the compiler does not perform demotion). We need to tell the compiler our intention to demote a float to an int using an operator known as a cast."*

I searched the web before posting the thread, but i didn't find something accurate.

Thanks in advance,
Pergi

---

### Post by falconindy on 2010-04-18
It doesn't give an error, but compiled with -Wall, you would see a warning about what you're trying to do with printf. The token '%d' expects an int. If you need decimal precision in your output, use '%f' instead.

---

### Post by Simon17 on 2010-04-18
Just because the standard defines a behavior does not mean that any compiler has to implement it, although the newer versions of GCC have been getting better at enforcing these types of things.
Every compiler is different and none of them follow every letter of the standard. It's just one of the things you have to live with.

---

### Post by Pergi on 2010-04-18
Compiled with the switch -Wall at gcc, i get only the warning:
```
warning: return type of &#8216;main&#8217; is not &#8216;int&#8217;
```
I think it is not related with the casting.

The thing that i can't understand is why it doesn't give me an error at the casting, at this line, **x = y;**

For example, in Java, you are not allowed to perform the above action, because you are doing demotion. So, you need to write **x = (int) y;**

Also, the same rule exists at C according to my book. So why GCC bypass the rule and it is not giving an error, or at least a warning? :P

Thanks for the answer :)

=== Edit ===

Simon17, I just read you answer. This is the only explanation that i am thinking too. If someone knows something more, post a reply :)

---

### Post by MadCow108 on 2010-04-18
C/C++ have many implicit conversions defined in its standard.
e.g. double to float, unsigned to signed and also float to int
Its something you have to life with.

printf is a variadic function meaning it takes arbitrary amounts of arguments. This was once implemented in form of macros.
e.g. printf("%d", arg); would expand to this:
printf(const char*, int);

in this case a call with a float gets implicitly converted to an integer.
This was fully conforming to the standard at that time and the macro solution had no mean of determining the types of the arguments.

But it is obvious this is not optimal behavior, so most compilers implemented printf not with macros but with compiler builtins which can determine the type of the format flag and its arguments.

But this is not standardized pre C99 and so not enabled by default (gcc compiles c89 by default).
With gcc you enable it with the -Wformat flag which is included in -Wall

In your specific example not even the compiler builtins are going to help, as you have the implicit (perfectly legal by standard) conversion in the x= y line
To warn in that case you need the -Wconversion flag
But in my experience this flags has other issues which make it unpractical (its far to strict when dealing with function prototypes)

---

### Post by Pergi on 2010-04-18
Aha i think that i got it.

So from the above, i understand that the book that i am using is a bit outdated because it says the following:

[I]"The resulting expression is of double type, but we are trying to store this into an integer! This type of &#8220;reverse promotion&#8221; (demotion?) can result in a loss of data (how do we represent 3.5 as an integer?) so it requires more intervention (i.e., the compiler does not perform demotion).
We need to tell the compiler our intention to demote a double to an int using an operator known as a cast."[/I]

Outdated book, right?

=== Edit ===

Used -Wconversion switch and i get the warnings that i wanted to see :P
By the way, with -Wall, i don't get the same warnings. It seems like -Wall doesn't contain -Wconvertion.

---

### Post by Compyx on 2010-04-18
> **MadCow108 said:**
> gcc compiles c89 by default

No, GCC uses GNU89 by default, from the man page:
```

       -std=
           Determine the language standard.   This option is currently only
           supported when compiling C or C++.

       ...

           gnu89
               GNU dialect of ISO C90 (including some C99 features). This is
               the default for C code.

```

---

### Post by MadCow108 on 2010-04-18
sorry my mistake
but gnu89 is still mostly c89 and not the same as c99 (or even gnu99)
but this should also be irrelevant in the printf case. gcc uses the builtin method in any standard as the old varargs header has been removed quite a while ago

---

### Post by Compyx on 2010-04-18
True, gnu89 is C89 with GNU extensions, of which some are incompatible with C99. I believe that gnu89's variable length arrays don't conform to the C99 definition of variable length arrays, for example.

Personally I don't use any GNU extensions, I still compile with -std=c89. I also feel it is rather unfortunate that GCC defaults to GNU89, rather than C89. People just starting out with C will learn the GNU dialect and assume it's standard C what they're using. Then when they try to compile their 'standard' code with a different compiler, it mysteriously won't compile. 

Just think of all those victims of Turbo C, expecting their code with #include <conio.h> to compile on Linux. ;) (Search these forums for 'conio.h' and you know what I mean)

---

