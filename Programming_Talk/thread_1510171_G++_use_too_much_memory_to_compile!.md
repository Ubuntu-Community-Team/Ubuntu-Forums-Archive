---
title: "G++ use too much memory to compile!"
date: 2010-06-15
forum: Programming Talk
---

### Post by margemoosh on 2010-06-15
i have a file written with c++ when i use visual studio in windows it compiles it in 3 seconds and don't use too much memory for that but when i want to compile it in ubuntu with g++ it takes about 1 minutes and use all memory i have(2GB) and compile it without ant error or warning.
i want to know why g++ use that much memory and takes too much time to compile.
my c++ program will declare a lot of variables about 10 martix each 3000x3000 and double type!
but visual studio compile it so fast.what's wrong with g++?
is there any better(faster) compiler than g++?

---

### Post by nvteighen on 2010-06-15
> **margemoosh said:**
> i have a file written with c++ when i use visual studio in windows it compiles it in 3 seconds and don't use too much memory for that but when i want to compile it in ubuntu with g++ it takes about 1 minutes and use all memory i have(2GB) and compile it without ant error or warning.
i want to know why g++ use that much memory and takes too much time to compile.
my c++ program will declare a lot of variables about 10 martix each 3000x3000 and double type!
but visual studio compile it so fast.what's wrong with g++?
is there any better(faster) compiler than g++?

Show the code. Chances are you're using some non-standard Microsoft extension. Anyway, the correct thing to do would be using STL containers, not double[][]...

---

### Post by SledgeHammer_999 on 2010-06-15
A really recent release(a few months) of gcc had something about using a different technique on compiling code that uses a lot less memory when compiling. Unfortunately my memory hasn't kept the details. I know that these changes are targeted for gcc 4.5 and that lucid has the "old" 4.4 release. Maybe this has something to do with it.

---

### Post by beren.olvar on 2010-06-15
could you check the visual studio's compile options versus the ones you are using with g++?

Also, you should check the runtime performance of your compiled code. There are some optimizations meant for better runtime at the expense of compile time.

---

### Post by SledgeHammer_999 on 2010-06-15
I think I found the change I was talking about. As it seems it isn't relevant to you.

> Compilation time for code that uses templates should now scale linearly with the number of instantiations rather than quadratically, as template instantiations are now looked up using hash tables.

link-->[http://gcc.gnu.org/gcc-4.5/changes.html](http://gcc.gnu.org/gcc-4.5/changes.html)

---

### Post by MadCow108 on 2010-06-15
maybe it is the linking and not compiling which needs the time and memory?
in that case it may be beneficial to use the rather new gold linker instead of ld (assuming you want elf format).
gold is considerably faster and less memory consuming.

But I would really be interested to see the code which requires only 1 minute to build but needs 2 gb of memory.
Code which eats up my memory while linking tend to be huge C++ projects like LLVM, but that also takes around 3 hours to build...
Maybe you stumbled over a compiler bug?

---

### Post by uOpt on 2010-06-15
How do you know it's using too much memory?

Please post the transcript of the session.

And how much paging space do you have?

---

### Post by Zugzwang on 2010-06-15
Hmmm, probably it has something to do with incremental linking and precompiled headers, in which Visual C++ and Borland C++ are quite strong and which g++/ld usually do not use? If you have plenty of C++ source files which include dozens of standard include files, which are precompiled by VC++ but not by Gnu C++, this would explain the time difference.

---

### Post by margemoosh on 2010-06-15
i attached source code.
system monitor shows i'm using 300mb memory and after i start to compile it reached 1.8gb and when compile ends it return too 300mb.
i know my program needs so much memory to run but i can't understand why compiler needs that much ram and time when visual studio compile it in a few seconds.
running performance in both compilers are the same i guess.(time complexy is O(n^3):mad:)
is there any option in g++ that i'm not using?i just use -Wall to see warnings.

---

### Post by MadCow108 on 2010-06-15
weird, it compiles on my moderate pc (gcc 4.1.2 and 3.4.6) in ~0.3 second with no noticeable memory use.

Which version of gcc are you using?
Are you using profile guided compilation?

btw. that must be the worst piece of code I ever saw o_O
perfect example for write only code.
you should really get rid of all these repetitions and magic numbers.
loop unrolling is better left to the compiler or handled over template-metaprogramming.

---

### Post by Zugzwang on 2010-06-15
I can confirm the slowness here. But it's the linking part and not the compiling part which is so slow:

```

me@my-computer:/tmp$ time g++ 03.24.cpp

real    0m11.337s
user    0m10.300s
sys     0m1.020s
me@my-computer:/tmp$ time g++ -c 03.24.cpp

real    0m0.547s
user    0m0.490s
sys     0m0.050s
me@my-computer:/tmp$ gcc --version
gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

Also, if that code is not automatically generated, it is, as already said, a nice example for badly organized code.

---

### Post by MadCow108 on 2010-06-15
interesting.
this must be a regression in speed:

> 
gcc 4.1.2 and 3.4.6
model name      : AMD Phenom(tm) II X2 550 Processor
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB

time g++ 03.24.cpp

real    0m0.490s
user    0m0.328s
sys     0m0.032s


> 
gcc 4.4.3
//note the far superior machine to above
model name      : Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 3072 KB

time g++ 03.24.cpp

real    0m8.805s
user    0m7.970s
sys     0m0.810s


one should check the release notes

---

### Post by margemoosh on 2010-06-15
> **MadCow108 said:**
> weird, it compiles on my moderate pc (gcc 4.1.2 and 3.4.6) in ~0.3 second with no noticeable memory use.

Which version of gcc are you using?
Are you using profile guided compilation?

btw. that must be the worst piece of code I ever saw o_O
perfect example for write only code.
you should really get rid of all these repetitions and magic numbers.
loop unrolling is better left to the compiler or handled over template-metaprogramming.


I'm using g++.
gcc cant compile my code and gave me a lot of errors.
this code is not mine:)
it's for my cousin he's civil eng. and he wrote that code and i should make this code running for him(i agree with worst piece of code:p )

---

### Post by MadCow108 on 2010-06-15
g++ is part of gcc.
I could also confirm the high memory usage on 4.4.3

it may be related to this regression:
[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=12245](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=12245)
try initializing your huge arrays

---

### Post by margemoosh on 2010-06-15
> **MadCow108 said:**
> g++ is part of gcc.
I could also confirm the high memory usage on 4.4.3

it may be related to this regression:
[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=12245](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=12245)
try initializing your huge arrays

yes i think that's my problem.
i think i should use new for creating arrays in run time not in compile time.
extra work for me:(

---

### Post by MadCow108 on 2010-06-15
the gold linker also handles this ok.
Not as fast as 4.1.2 but acceptable and no memory explosion.
#warning changes /use/bin/ld symlink to gold:
sudo apt-get install binutils-gold

g++ file.cpp -fuse-ld=gold

but I think its still beta, so use with care

---

### Post by margemoosh on 2010-06-15
> **MadCow108 said:**
> the gold linker also handles this ok.
Not as fast as 4.1.2 but acceptable and no memory explosion.
#warning changes /use/bin/ld symlink to gold:
sudo apt-get install binutils-gold

g++ file.cpp -fuse-ld=gold

but I think its still beta, so use with care

thanks gold linker works fine.

---

### Post by MadCow108 on 2010-06-15
It really seems to be related to the global arrays:
this reproduces the problem.
fast in <=4.1.2, slow and memory consuming while linking in 4.4:
```

#define N 8000
double a1[N][N];
double a2[N][N];
double a3[N][N];


int main()
{
  return 0;
}

```
So using dynamic allocation should fix the problem

---

### Post by margemoosh on 2010-06-15
> **MadCow108 said:**
> Would you mind if I check the reason for this and maybe file a bug report including the code?

no problem.
i'll be happy if this code helps.

---

### Post by nvteighen on 2010-06-15
Very slow here too:
```

ugi@UGI:~/Desktop$ g++ --version
g++ (Debian 4.4.4-1) 4.4.4
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

ugi@UGI:~/Desktop$ time g++ -o 03.24 03.24.cpp -Wall -Wextra -pedantic

[snip ...]

real	0m16.543s
user	0m15.105s
sys	0m1.396s
ugi@UGI:~/Desktop$ 

```

---

### Post by MadCow108 on 2010-06-15
it is also present in gcc 4.5 + ld 2.20.51

---

### Post by splicerr on 2010-06-15
No slowness nor 'memory explosion' here...

```

$ time g++ 03.24.cpp

real    0m0.788s
user    0m0.696s
sys    0m0.076s

$ gcc --version
gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3

```

---

### Post by SledgeHammer_999 on 2010-06-15
I don't see a slowness either:

```

$time g++ 03.24.cpp

real	0m1.202s
user	0m0.740s
sys	0m0.090s

$g++ --version
g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3

$uname -a
Linux hammered-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

---

### Post by uOpt on 2010-06-15
> **margemoosh said:**
> I'm using g++.
gcc cant compile my code and gave me a lot of errors.
this code is not mine:)
it's for my cousin he's civil eng. and he wrote that code and i should make this code running for him(i agree with worst piece of code:p )

Please p.m. me a list of buildings and bridges he's involved in.

---

