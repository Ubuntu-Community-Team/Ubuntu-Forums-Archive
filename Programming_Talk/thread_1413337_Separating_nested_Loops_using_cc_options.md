---
title: "Separating nested Loops using cc options"
date: 2010-02-22
forum: Programming Talk
---

### Post by newport_j on 2010-02-22
I believe that compiling gcc with the O3 option will separate nested loops that can be separated. I also know that using a program option will also show one the code now that the nested loops are separated. 

I am interested in exactly what that option is. 
Any help appreciated.

Newport_j

---

### Post by Bachstelze on 2010-02-22
> **newport_j said:**
> I also know that using a program option will also show one the code now that the nested loops are separated.

Sure about that? The [font=monospace]-S[/font] flag will make gcc output optimized assembly code, but I don't know any that will output optimized C code (does that even make sense?).

---

### Post by newport_j on 2010-02-22
I believe that my statement was misunderstood. Using the O3 option will unravel nested loops. I heard it can be done using f77 -O3, so I assume it can be done using gcc -O3. This is simply unraveling nested loops that can be unraveled. 

Since it can unravel loops, again i am referring to f77 here, it can show the new source code with these loops unraveled. That is all I want to see. I am struggling to separate some nested loops and looking for a shortcut. 

I know that compilers can do this and they can - I think - show the resulting code. I just want to know the commands to do it. That is all I am looking for.

Newport_j

---

### Post by unknownPoster on 2010-02-22
[http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/Optimize-Options.html#Optimize-Options](http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/Optimize-Options.html#Optimize-Options)

Perhaps you are looking for -funroll-loops
> 
Unroll loops whose number of iterations can be determined at compile time or upon entry to the loop. -funroll-loops implies -frerun-cse-after-loop. This option makes code larger, and may or may not make it run faster. 


---

### Post by avidday on 2010-02-22
> **newport_j said:**
> 
Since it can unravel loops, again i am referring to f77 here, it can show the new source code with these loops unraveled. That is all I want to see. I am struggling to separate some nested loops and looking for a shortcut. 

I know that compilers can do this and they can - I think - show the resulting code. I just want to know the commands to do it. That is all I am looking for.j

No compiler I have ever heard of can do what you are asking. There are optimizations to unroll loops in the assembler output from a compiler, by using inline code expansion. As someone else noted, the -funroll-loops will turn on a code optimization which attempts to inline loop code when the code analyzer can resolve them. There is also the -ftree-vectorize optimization, which will attempt to vectorize loops and issue SSE/SSE2 instructions for CPU targets which support them when loops have no dependencies and can be unrolled and arithmetic operations vectorized into 16 byte tuples.

---

### Post by MadCow108 on 2010-02-22
I guess your meaning some of the loop transformations added in the graphite branch of gcc
[http://gcc.gnu.org/gcc-4.4/changes.html](http://gcc.gnu.org/gcc-4.4/changes.html) (search for graphite)
or maybe some of the new code to auto-vectorize nested loops
[http://gcc.gnu.org/projects/tree-ssa/vectorization.html](http://gcc.gnu.org/projects/tree-ssa/vectorization.html)

But I'm not aware of an option to show the transformed code, even when it would probably be in the internal representation which will probably be hard to read.
Maybe you find something here:
[http://gcc.gnu.org/onlinedocs/gcc/Debugging-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Debugging-Options.html)
e.g:
> 
-fdump-tree-switch-options
`gimple'
Dump each function before and after the gimplification pass to a file. The file name is made by appending .gimple to the source file name.


---

### Post by lisati on 2010-02-22
I'm not sure I follow what's being asked here. Are we talking about doing some kind of tinkering on the loops so that they can be multi-threeaded?

---

### Post by ssam on 2010-02-22
there is the gcc graphite project [http://gcc.gnu.org/wiki/Graphite](http://gcc.gnu.org/wiki/Graphite) which allows the compiler to do various loop transformations and optimisations.

there is initial graphite support in GCC 4.4, but lots more in 4.5 (not yet released).

you could try some of these
```
-O3 -floop-parallelize-all -ftree-parallelize-loops=4
-O3 -march=native -floop-parallelize-all -ftree-parallelize-loops=4
-O3 -march=native -floop-parallelize-all -ftree-loop-linear -floop-interchange -floop-strip-mine  -floop-block -ftree-loop-distribution -ftree-parallelize-loops=4
```

i recently tried compiling the code i use with several different GCC versions and options. i did not see any benefit from graphite, but thats possible because the code is old fashioned fortran. i put my results online: [http://www.hep.man.ac.uk/u/sam/zgoubi-optimise/](http://www.hep.man.ac.uk/u/sam/zgoubi-optimise/)

---

### Post by newport_j on 2010-02-22
What is the LNO option/term mean?
 
 
Newport_j

---

### Post by ssam on 2010-02-23
i guess loop nest optimising
[http://en.wikipedia.org/wiki/Loop_nest_optimization](http://en.wikipedia.org/wiki/Loop_nest_optimization)

---

### Post by dwhitney67 on 2010-02-23
> **newport_j said:**
> I am struggling to separate some nested loops and looking for a shortcut. 


Can you please provide an example of these nested loops that are plaguing your application.

The most basic type of nested loop would look something like:
```

for (int i = 0; i < Ni; ++i)
{
   for (int j = 0; j < Nj; ++j)
   {
      // do something special here
   }

   // and possibly something special here
}

```

---

