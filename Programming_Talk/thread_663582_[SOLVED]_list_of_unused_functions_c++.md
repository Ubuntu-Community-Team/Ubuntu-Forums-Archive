---
title: "[SOLVED] list of unused functions c++"
date: 2008-01-10
forum: Programming Talk
---

### Post by monkeyking on 2008-01-10
Hey,
i'm doing a c/c++ program,
that has evolved quite a lot.

Is there any smart programs/scripts.
That can tjeck if any functions are unused.

thanks in advance.

---

### Post by LaRoza on 2008-01-10
Not that I know of. But any function defined, but not called will not affect the size or speed of the program.

---

### Post by uljanow on 2008-01-10
> **monkeyking said:**
> Is there any smart programs/scripts.
That can tjeck if any functions are unused. gcc, with warnings enabled.

---

### Post by monkeyking on 2008-01-10
> **uljanow said:**
> gcc, with warnings enabled.

As far as I can tell it only list unused variabels.
I know it won't change the speed,
It's only for making the source nicer.

```

#include <stdio.h>
  int plus(x,y){
  return (x+y);
}
int main (void){
  int a=2;
  int b=3;
  printf("test\n");
  return 0;
}

```

```

gcc tmp.c -Wall
tmp.c: In function &#8216;main&#8217;:
tmp.c:9: warning: unused variable &#8216;b&#8217;
tmp.c:8: warning: unused variable &#8216;a&#8217;

```

---

### Post by Zugzwang on 2008-01-10
According to [http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html]("http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html"), enabling warnings only detects certain unused certain static functions.

In fact this would be a task of the linker or an external analysis program.

---

### Post by LaRoza on 2008-01-10
Is this program one big file? If so, you should change that.

---

### Post by Zugzwang on 2008-01-10
It's a pity that the GNU linker is somewhat limited in functions. I'm pretty sure that for example the Borland linker (for Windows) automatically removes unused functions from the executable. In such a case, you wouldn't have to care about unused functions (unless it's really your goal to clean up your source code and not the executable.

I'd suggest using tools made for other purposes for your task. For example, when you generate documentation of your program/library using Doxygen, you can [set CALLER_GRAPH]("http://www.stack.nl/~dimitri/doxygen/diagrams.html") to generate a caller graph for every function. Then you would have to manually look through the documentation for each function.

Google also reveals the link to another tool you might want to look at: [http://sourcenav.sourceforge.net/]("http://sourcenav.sourceforge.net/")

---

### Post by monkeyking on 2009-01-02
After one year, while I was trying to solve another problem,
I actually found what seems like a solution.

this is a copy paste from man gprof for anyone that cares.


[PHP] "-z"
       "--display-unused-functions"
           If you give the -z option, "gprof" will mention  all  functions  in
           the  flat  profile, even those that were never called, and that had
           no time spent in them.  This is useful in conjunction with  the  -c
           option for discovering which routines were never called.
[/PHP]

---

### Post by kcode on 2009-01-03
> **LaRoza said:**
> Not that I know of. But any function defined, but not called will not affect the size or speed of the program.

But why shouldn't it increase the size?

---

### Post by slavik on 2009-01-03
> **kcode said:**
> But why shouldn't it increase the size?
if the compiler optimizes the code enough, it might be able to optimize the function away, but I don't know if compilers are that smart (or if they are told to do it).

for example:
if (0==1) { printf("hello\n"); }

will never be compiled in.

---

### Post by dribeas on 2009-01-03
Profiler information will tell you only what functions were not called in the profiled execution. If you have some rarely used function (recovery from some error, signal trap) that gets used seldomly it will be marked as never used, while in fact is is needed.

The compiler can help optimizing size up to some extent. If you have functions implemented in a shared library, the linker (at the time the library is created) will not know what functions will be called in executables, and cannot eliminate it. 

If you link statically, the linker would have a change at eliminating not referenced functions, but I don't know whether it does in fact remove it from the binary.

---

### Post by slavik on 2009-01-03
But then, much like a valgrind memcheck, you could just run through the binary and see what functions are unreachable.

---

### Post by monkeyking on 2009-12-28
> **slavik said:**
> But then, much like a valgrind memcheck, you could just run through the binary and see what functions are unreachable.

Sorry for reviving this thread yet again.
How would you check which functions are unreachable in the binary?

---

### Post by phorgan1 on 2010-04-22
> **monkeyking said:**
> After one year, while I was trying to solve another problem,
I actually found what seems like a solution.

this is a copy paste from man gprof for anyone that cares.


[PHP] "-z"
       "--display-unused-functions"
           If you give the -z option, "gprof" will mention  all  functions  in
           the  flat  profile, even those that were never called, and that had
           no time spent in them.  This is useful in conjunction with  the  -c
           option for discovering which routines were never called.
[/PHP]

The problem with this, is that you only find out that the code didn't go through a path that called the method or function.  The method or function could be called by some part of your code that just didn't get exercised in the profiling run.  Just because it's rare or hard to get to doesn't mean that it's unimportant, or never used.

---

### Post by MadCow108 on 2010-04-23
that is not really a problem because if you remove a function which is indeed used in some unlikely path the compiler/linker will complain that its missing.
The compiler checks all paths it determines possible no matter how unlikely.

@ monkeyking (if he ever looks in here again ^^)
you can do that with:
-Wunreachable-code
but it will not necessarily detect all cases because the information the compiler has is limited.
It may also have false positives, so be careful

to add something new to this old thread:
the new gcc 4.5 can optimize non-static unused functions away thanks to the new link time optimizer.
pass the -flto -fwhole-program flags to the compile and link stage
This will then remove all symbols which are never referenced (in addition to more aggressive interprocedual optimizations like inlining across translation units)

---

### Post by monkeyking on 2010-05-05
> **MadCow108 said:**
> that is not really a problem because if you remove a function which is indeed used in some unlikely path the compiler/linker will complain that its missing.
The compiler checks all paths it determines possible no matter how unlikely.

@ monkeyking (if he ever looks in here again ^^)
you can do that with:
-Wunreachable-code
but it will not necessarily detect all cases because the information the compiler has is limited.
It may also have false positives, so be careful

to add something new to this old thread:
the new gcc 4.5 can optimize non-static unused functions away thanks to the new link time optimizer.
pass the -flto -fwhole-program flags to the compile and link stage
This will then remove all symbols which are never referenced (in addition to more aggressive interprocedual optimizations like inlining across translation units)

Well I'm indeed looking here from time to time, but I'm mostly using stackoverflow these days.
Thanks for the -Wunreachable compile argument.

---

