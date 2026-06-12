---
title: "How to use gcc option -fwhole-program"
date: 2013-03-28
forum: Programming Talk
---

### Post by DaviesX on 2013-03-28
Hi, I have some questions on using gcc's compiler options: 

(1) "[COLOR=#000000][FONT=Times New Roman]Assume that the current compilation unit represents the whole program being compiled. All public functions and variables with the exception of [/FONT][/COLOR]main[COLOR=#000000][FONT=Times New Roman] and those merged by attribute [/FONT][/COLOR]externally_visible [COLOR=#000000][FONT=Times New Roman]become static functions and in effect are optimized more aggressively by interprocedural optimizers."
according to the gcc wiki, should I specify it to gcc or ld, or both ?

(2) Do I have to specify those -Ox options to the linker, too ?

(3) In comparison to -fwhole-program and -flto (If both can be used), by using which one can produce, with respect to performance, better binary code ?

Thanks :)[/FONT][/COLOR]

---

### Post by dwhitney67 on 2013-03-28
> **DaviesX said:**
> Hi, I have some questions on using gcc's compiler options: 

(1) "[COLOR=#000000][FONT=Times New Roman]Assume that the current compilation unit represents the whole program being compiled. All public functions and variables with the exception of [/FONT][/COLOR]main[COLOR=#000000][FONT=Times New Roman] and those merged by attribute [/FONT][/COLOR]externally_visible [COLOR=#000000][FONT=Times New Roman]become static functions and in effect are optimized more aggressively by interprocedural optimizers."
according to the gcc wiki, should I specify it to gcc or ld, or both ?

Typically using 'gcc' alone should be enough.  For large projects, object files are created (using -c option) for each source file.  Then all are linked together to either form a library (shared-object and/or static) or an application.

> **DaviesX said:**
> 
(2) Do I have to specify those -Ox options to the linker, too ?

No, this is optional.  The -Ox options are meant to be used to optimize one's final code, not meant as a means to make poorly developed code run faster/better.

> **DaviesX said:**
> 
(3) In comparison to -fwhole-program and -flto (If both can be used), by using which one can produce, with respect to performance, better binary code ?

Thanks :)[/FONT][/COLOR]
I've never had a use for these options, much less know what they're used for.  I would suggest writing efficient code before attempting to lay that burden on the compiler.

---

### Post by DaviesX on 2013-03-28
Thank you very much. 
I need to use these options because, unfortunately, I've been written bad code already :(  I put all the functions into .cpp files regardless they are short enough to inline or not. Some of those short functions are to be called in some inner loops. It sucks the performance a lot (one has been making the loop 100% faster when I put it into a #define as marco-functions) 
So I hope link-time optimization can give the inliner an opportunity to inline those short functions. But when I use -Ofast -flto -fwhole-program as compiler option and -flto as linker option, it got even slower. And then, when I specify -fwhole-program to the linker also, it doesn''t generate correct code at all. If I don't use -fwhole-program on neither compiler or linker, it's still slower. But when I put -Ofast -flto on both compiler and linker, the code boost more than twice as fast just like using marco-function.
I am so confused that I don't exactly know where and how do I need to put those options =,=

---

### Post by ssam on 2013-03-28
> No, this is optional. The -Ox options are meant to be used to optimize one's final code, not meant as a means to make poorly developed code run faster/better.
I disagree. the optimiser lets you write neater more understandable code, and let the compile worry about the nitty gritty of whether 'pow(x,4)' will execute faster than 'x*x*x*x'. also if you have any code with undefined behaviour, it may well behave differently at different optimisation levels. if you do all you development with -O0, and then release it with -O2, then you (or your users) might discover a bunch of bugs you did not know you had. (pro-tip, test you code with valgrind)

LTO defers the optimisation until link time. this means it can do better Interprocedural optimization ( [https://en.wikipedia.org/wiki/Interprocedural_optimization](https://en.wikipedia.org/wiki/Interprocedural_optimization) ). for example without LTO it would be impossible to inline a function from one cpp file to a call in another cpp file. You need to pass the optimisation level at each stages of of the build, so you have '-O2 -lto' in your CFLAGS CXXFLAGS and LDFLAGS ( [http://lists.debian.org/debian-devel/2011/06/msg00149.html](http://lists.debian.org/debian-devel/2011/06/msg00149.html) ). also note that gcc decides by itself whether to inline a function, and ignores the 'inline' keyword.

have a look at the optimiser improvements section in [http://gcc.gnu.org/gcc-4.7/changes.html](http://gcc.gnu.org/gcc-4.7/changes.html) for some examples. also see [http://gcc.gnu.org/wiki/LinkTimeOptimization](http://gcc.gnu.org/wiki/LinkTimeOptimization)

LTO has been in GGC a couple of years, but it could be a bit problematic before 4.7, and has received improvements in 4.8. 

I guess with the -fwhole-program gcc can notice things like 'you only ever call this function with 6 or 13 as the argument, so i can optimise it just for those cases', otherwise it would have to worry that you may link in other code that might call the function differently.

---

### Post by DaviesX on 2013-03-28
Thanks for your reply. So do I have to put -fwhole-program for the linker ?

---

### Post by dwhitney67 on 2013-03-29
> **DaviesX said:**
> Thank you very much. 
... I've been written bad code already :( ...

Fix this problem first, then worry about optimization later.

---

### Post by dwhitney67 on 2013-03-29
> **ssam said:**
> I disagree. the optimiser lets you write neater more understandable code, ...

Baloney.

The optimizer (err, compiler) will not pretty up any code to make it more understandable.  It does help optimize generated object/executable code, but it will not affect the source code itself... which is what people will read when maintaining the code.

Also, for future reference...

op·tion·al
[op-shuh-nl]
adjective
1.
left to one's choice; not required or mandatory: Formal dress is optional.
2.
leaving something to choice.

---

### Post by MadCow108 on 2013-03-29
are you using the gold linker?
adding fwhole-program is not necessary with that linker and its also discouraged to do so.
newer documentation has the section removed from the manual (with bad grammar ;) )

[QUOTE=http://gcc.gnu.org/onlinedocs//gcc/Optimize-Options.html#Optimize-Options]
-fwhole-program
...
In combination with -flto using this option should not be used. Instead relying on a linker plugin should provide safer and more precise information.[/QUOTE]

fwhole-program was basically the workaround for when gcc did not have lto. Then you usually concatenated all your files and used whole-program to archive the same effect.
It is now unfortunately mixed up tightly with early lto documentation everywhere.

---

### Post by ssam on 2013-03-29
> **dwhitney67 said:**
> Baloney.
The optimizer (err, compiler) will not pretty up any code to make it more understandable.  It does help optimize generated object/executable code, but it will not affect the source code itself... which is what people will read when maintaining the code.


Sorry if i was not clear. i was not trying to say that the optimiser makes you code pretty. I mean often when programming there is a choice between various ways of writing an expression. Some people put lots of effort into writing code that runs faster, but is very hard to read. you end up seeing stuff like:
```

for (dd=d[k=0]; k<16; dd=d[++k]) {
    satd += (dd < 0 ? -dd : dd);
  }

```
i would say its much better to write
```

for (int i=0; i<16; i++){
   if (d[i] <0) satd += d[i];
   else satd -= d[i];
}

```
if you compile with no optimisation the first will probably run faster, and some people would be proud of that. if you compile with -O2 you will probably get identical assembly. given that in real life you spend as much time debugging code as writing code, i'd say the second is better.

or how about
```

x = y * M_PI / 2;

```
vs
```

x = y * 1.5707963467949;

```
a good optimiser will transform those into the same code. without an optimiser, you would have to use the second one in order to save a time consuming divide. and in the second one nobody will spot the subtle bug.


This is why I say that the optimiser allows you to write cleaner, more readable code.

---

### Post by DaviesX on 2013-03-29
> **MadCow108 said:**
> are you using the gold linker?
adding fwhole-program is not necessary with that linker and its also discouraged to do so.
newer documentation has the section removed from the manual (with bad grammar ;) )



fwhole-program was basically the workaround for when gcc did not have lto. Then you usually concatenated all your files and used whole-program to archive the same effect.
It is now unfortunately mixed up tightly with early lto documentation everywhere.

Ok, so I don't ever need -fwhole-program if the sources can be compiled with -flto

I don't want to fix the code because it would require me to put a lot of short function to the header and state "inline", which will make the compile time way longer :( I'd hope it spends more time on release mode and much shorter time on debug mode (just to make sure anything doesn't fail the lto optimizer).

Anyway, thanks for you guys' replies :)

---

### Post by ofnuts on 2013-03-29
> **ssam said:**
> Sorry if i was not clear. i was not trying to say that the optimiser makes you code pretty. I mean often when programming there is a choice between various ways of writing an expression. Some people put lots of effort into writing code that runs faster, but is very hard to read. you end up seeing stuff like:
```

for (dd=d[k=0]; k<16; dd=d[++k]) {
    satd += (dd < 0 ? -dd : dd);
  }

```
i would say its much better to write
```

for (int i=0; i<16; i++){
   if (d[i] <0) satd += d[i];
   else satd -= d[i];
}

```
if you compile with no optimisation the first will probably run faster, and some people would be proud of that. if you compile with -O2 you will probably get identical assembly. given that in real life you spend as much time debugging code as writing code, i'd say the second is better.

The two versions of the code aren't equivalent... the first one adds the absolute value while the second one subtracts it (I'm not too convinced either that ++k is equivalent to i++ here but I'm not going to spend time on such code :)) . And speaking of readability: 
```

for (int i=0; i<16; i++){
   satd += abs(d[i]);
}

```
> **ssam said:**
> or how about
```

x = y * M_PI / 2;

```
vs
```

x = y * 1.5707963467949;

```
a good optimiser will transform those into the same code. without an optimiser, you would have to use the second one in order to save a time consuming divide. and in the second one nobody will spot the subtle bug.


This is why I say that the optimiser allows you to write cleaner, more readable code.
Your example is not valid because you are relying on the availability of M_PI. If you were to use "3.14159265359/2" you would be exposed to typos as well. 

I however agree with the idea that a good optimizer allows you to write more readable code. But in any application there is very little code where performance is more important than readability anyway, and one can even think that readable code, which comes from a clear mind, will usually perform better.

---

