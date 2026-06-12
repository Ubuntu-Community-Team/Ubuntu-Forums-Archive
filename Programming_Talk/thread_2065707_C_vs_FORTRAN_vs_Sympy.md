---
title: "C vs FORTRAN vs Sympy"
date: 2012-10-02
forum: Programming Talk
---

### Post by Holotype on 2012-10-02
I hear a lot of theoretical physicists use python (sympy) for complex calculations instead of mathematica. Also, a lot of codes are written in Fortran. My question is this: Can I do symbolic and numerical calculations in C at as high of a level as Sympy? Or, is it at a higher level (which I'm guessing is correct)?

I have time to learn. I understand C is much faster and more fundamental, so I would prefer to learn C (especially since I already know some of it). I don't know any Python.

---

### Post by rai4shu2 on 2012-10-02
C is actually quite a bit slower if you don't know what you're doing. It can go a lot faster, but that's if you understand how to design your code properly for speed. If all you want is to solve some equations, then I strongly suggest you stick with Fortran or Python.

---

### Post by MadCow108 on 2012-10-02
sympy and C/Fortran are worlds apart
you can't really do interactive symbolic calculations with C/Fortran, and if you could it would be a huge pita.

but its very useful to learn both, low level and high level
especially as a physicist.
You might also want to look in to the root software developed by CERN, very commonly used by experimental physicists. It offers some kind of interactivity to C/C++.

For sympy I recommend looking into the ipython notebook or sage.
It makes it feel very much like Mathematica.

performance wise simple fortran tends to be a little faster due to the compiler being able to do more work.
But its not that significant.
Only learn it if you need it for some legacy applications.

---

### Post by TheStatsMan on 2012-10-04
> **MadCow108 said:**
> 
For sympy I recommend looking into the ipython notebook or sage.
It makes it feel very much like Mathematica.


There is an interactive wrapper with sympy called isympy, which is just ipython combined with sympy.

> 
performance wise simple fortran tends to be a little faster due to the compiler being able to do more work.
But its not that significant.
Only learn it if you need it for some legacy applications.

I was agreeing with everything that Madcow said up until this point.  I have found Fortran+Python to be a marriage made in Heaven for  scientfic applications. It has replaced C++ for me.  I write my code in  Python and write the bits that need speed in Fortran (I only sometimes  write extensions in C for fun). Whilst Fortran on its own is terrible,  as it is simply not as good for generic coding as C or C++, Python is  very good for writing generic code, but not so good for implemeting  recursive algorithms that we often want implement in scientific  applications. Fortran on the other hand is excellent for implementing  such algorithms on arrays in particular and has significant advantages  over both C and C++ (IMO) for this kind of operation.  The biggest for  me is possibly the ease of debugging code. Fortran is so well defined  (which has the other side effect of a possible speed advantage) that the  compiler can give far more precise information at compile time to where  any bugs are in the code. This sounds like something simple, but in  practice I think this makes a big difference in my experience.  I mean  the compiler can tell you exactly where mistakes are where in C the  equivalent mistake could be a run time error. Another big advantage of  Fortran is array slicing is built into the language. It may seem trivial  to get around when implementing algorithms on arrays and we can use  elegant Matrix classes in C++ to help in some cases, but I don't think  you can beat Fortran in this area when it comes to the speed of  implementation of the kind of algorithms we use in scientific  programming. Even if it just comes back to the speed of debugging. The  complexity of the classes required in C++ to produce elegant solutions  really does slow you down when debugging code. I don't think anyone that  has heavily used templates can argue with this point. This is even more  true once you start getting into expression templates and static  polymorphism.

There is another reason to learn Fortran (for  scientific programmers, i,e, guys doing a lot of algorithms on arrays).  That is there is no real cost to it. The language is so simple you can  learn it in an afternoon. You can't learn C in an afternoon. The  language may be simple in a language structure sense (well it is simple  when you get it) but it is no way near as simple as Fortran, and  the  incredible flexibility of C comes at a cost and learning to produce good  C code really takes some time (for most this may be years rather than  in the Fortran case days, or if you already know how to code perhaps  hours).  It is also easy to call Fortran from C or C++ (nearly as easy  as it is to call from Python) and there is so much Legacy code out there  it is really something you should learn even if you are primarily  developing your scientific programs in C or C++.

I think in  general for scientific programming, I think learn Python (obviously  including numpy, scipy , etc, learn how to speed up your algorithms with  Fortran and then perhaps learn C after that to round things out.  Actually, I think learning C at some stage could be invaluable, it even  if it is to simply help you understand what is going on to produce  better Python code. Possibly C++ even more so (if you have enough time).  If you work on really big data you really need to understand memory  mangement, even if you are writing the main part of your code in a  language that handles the garbage collection, understanding when memory  is being allocated and destroyed is important. Understanding things like  operator overloading both the old fashion way and with expression  templates also is pretty invaluable if you really want to understand  how  libraries like numpy are working (and languages like MATLAB as  well), which can really help you write efficient code.

---

### Post by Holotype on 2012-10-05
Thanks for all of the replies. I think I will keep learning C, but I'm going to take Python a lot more seriously. I hear it is pretty easy to learn, so I'll pick up a book or three on Python. Also, I know a little FORTRAN already, so I can pick up the rest as I go. I use gdb, so I'm getting a good feel for memory usage.

---

### Post by ssam on 2012-10-09
I have used python, C and FORTRAN for scientific computing.

Python is in general not fast, but often fast enough for certain things. If you can use numpy, and scipy instead of writing your own loops you will get a huge speed up. if you can use numexpr that will help even more. if you find yourself needing the write a loop that runs over an array it could be very slow. at this point i move to a C function, that you pass your array to, and it passes back a modified array, or an answer. i use F2PY to wrap this so it looks like a python function.

I would recommend using C over FORTRAN. it is more modern. it encourages more structured programs. the compiler can catch far more errors (in fortran if you missspell a variable name you get a new uninitialised variable). you can write more dynamic code.

suppose i want to do
```

double xs[] = {2.1, 3.4, 5.6};
for(int i=0; i<(sizeof(x)/sizeof(x[0])); i++)
{
    //do something with xs[i]
}

```
sometimes i need to adjust xs, so i just change the values between the curly braces.
now actually i needed this code in fortran.
```

PARAMETER (NXS = 3)
DOUBLE PRECISION XS(NXS)
DATA XS /2.1, 3.4, 5.6/
DO I = 1, NXS
    do something with XS(I)
ENDDO

```
now that may not look all that much worse, but notice that i have to change NXS by hand, if i add or remove things from XS. also the top 3 lines can't be put next to the loop, they have to be put at the top of the program/subroutine. they also can't be put next to each other, because all the variable declarations must be before all of the DATA declarations. and one more thing that i never solved was, in C, if i change the list to {}, then compiler just optimises out the for loop. in fortran i get an error. so i have to comment out the for loop.

so to make a simple change in a fortran program i have to change 3 things in 3 different places. if i miss one i get a crash, or silent data corruption, or a compile error. 

one possible advantage of fortran, is that it is a bit simpler of the compiler. in C the compile often can't tell if 2 arrays overlap or not, so can't enable some optimisation. you have to use the restrict keyword to promise that your array does not overlap any other.

---

### Post by TheStatsMan on 2012-10-09
> **ssam said:**
> I have used python, C and FORTRAN for scientific computing.

Python is in general not fast, but often fast enough for certain things. If you can use numpy, and scipy instead of writing your own loops you will get a huge speed up. if you can use numexpr that will help even more. if you find yourself needing the write a loop that runs over an array it could be very slow. at this point i move to a C function, that you pass your array to, and it passes back a modified array, or an answer. i use F2PY to wrap this so it looks like a python function.

I would recommend using C over FORTRAN. it is more modern. it encourages more structured programs. the compiler can catch far more errors (in fortran if you missspell a variable name you get a new uninitialised variable). you can write more dynamic code.

You won't if you use implicit none. The compiler will catch more errors in Fortran because it is more well defined, but that is only assuming you are writing decent code, and if you were it would instantly catch the mistake you mentioned. 

> 
suppose i want to do
```

double xs[] = {2.1, 3.4, 5.6};
for(int i=0; i<(sizeof(x)/sizeof(x[0])); i++)
{
    //do something with xs[i]
}

```sometimes i need to adjust xs, so i just change the values between the curly braces.
When using C or Fortran to speed up Python you really should be declaring memory in Python, most of the time and passing it to the compiled language.  How often is it going to beneficial to declare a specific array on the stack like this. If you are doing things like this often you are doing something wrong.

> 
now actually i needed this code in fortran.
```

PARAMETER (NXS = 3)
DOUBLE PRECISION XS(NXS)
DATA XS /2.1, 3.4, 5.6/
DO I = 1, NXS
    do something with XS(I)
ENDDO

```As above, you really shouldn't be doing this kind of thing a lot (at all) in scientific coding.  Generally very large arrays are declared on the heap, using Python and passed to C or Fortran, where lots of operations are done on them. Things like array slicing on multidimensional arrays are so much easier in Fortran and are less error prone than doing an equivalent thing in C.  Not to mention all the built in operations on arrays
 I mean if A and B are arrays you can do things like

```

A(3:6, :, t) = B(1:4, :) + C

```assuming conformable dimensions, and t is an integer. Write the equivalent in C and tell me that it is easier and less error prone.

Anyway C is more flexible, but you get a lot of flexibility from Python and you can then use Fortran for what it is good at, which is doing operations on arrays, which is a lot of what you are doing in scientific programming. That said some extensions are still better with C, but most of the time I find Fortran is the better tool for the job.  Obviously, if you are writing an extention on a GPU, you are going to have to use a variant of C and for more complex data structures C is better suited, but for working on arrays Fortran is very nice. It is also slightly easier to call BLAS and Lapack from Fortran, which is a big plus and a bigger plus is you can actually pass slices of the arrays directly to this routines. I think this is very important a lot of the time in scientific computing.

---

### Post by ssam on 2012-10-09
I think a lot of this comes down to personal preference. 

> **TheStatsMan said:**
> You won't if you use implicit none. The compiler will catch more errors in Fortran because it is more well defined, but that is only assuming you are writing decent code, and if you were it would instantly catch the mistake you mentioned. 

implicit none was not an option in the fortran code i have worked with, as there would be to much existing stuff to fix. i am sure it is possible to write nice fortran, but like readable perl, and safe php, its not something you often see in practice.

> **TheStatsMan said:**
> 
When using C or Fortran to speed up Python you really should be declaring memory in Python, most of the time and passing it to the compiled language.  How often is it going to beneficial to declare a specific array on the stack like this. If you are doing things like this often you are doing something wrong.

As above, you really shouldn't be doing this kind of thing a lot (at all) in scientific coding.

I guess i could have explained my above code better. XS was holding points of interest (which would change between runs of the code). For each point of interest i needed to look though some other data and see if it was near that point. I dont see how that could be expressed in array notation.

> **TheStatsMan said:**
> 
Generally very large arrays are declared on the heap, using Python and passed to C or Fortran, where lots of operations are done on them. Things like array slicing on multidimensional arrays are so much easier in Fortran and are less error prone than doing an equivalent thing in C.  Not to mention all the built in operations on arrays
 I mean if A and B are arrays you can do things like

```

A(3:6, :, t) = B(1:4, :) + C

```assuming conformable dimensions, and t is an integer. Write the equivalent in C and tell me that it is easier and less error prone.


if what you are doing is that simple you can do it straight in numpy. or use numexpr to multithread it. i would only jump out of python if it was impossible to express what i needed without a loop.

> **TheStatsMan said:**
> 
Anyway C is more flexible, but you get a lot of flexibility from Python and you can then use Fortran for what it is good at, which is doing operations on arrays, which is a lot of what you are doing in scientific programming. That said some extensions are still better with C, but most of the time I find Fortran is the better tool for the job.  Obviously, if you are writing an extention on a GPU, you are going to have to use a variant of C and for more complex data structures C is better suited, but for working on arrays Fortran is very nice. It is also slightly easier to call BLAS and Lapack from Fortran, which is a big plus and a bigger plus is you can actually pass slices of the arrays directly to this routines. I think this is very important a lot of the time in scientific computing.

---

### Post by TheStatsMan on 2012-10-10
> **ssam said:**
> 
implicit none was not an option in the fortran code i have worked with

But it is an option now, we are talking about what the OP should look at now, not decades ago.

> 
, as there would be to much existing stuff to fix. i am sure it is possible to write nice fortran, but like readable perl, and safe php, its not something you often see in practice.
The fortran libraries that are good, such as LAPACK and BLAS are probably some of the most tested code on the planet. The APIs are pretty ugly at first but they make sense  after using them for a while and snippets actually make them easy to use. They are the basis of so much of what we do in scientific programming. They are used heavily from people using C, C++, Fortran, etc. In fact many of the legacy libraries are fantastic. It isn't like it is all broken out there. 

There is just as much horrid C (well probably a lot more, a lot more people use it) out there as there is Fortran.  If the language writes the constructs to write decent code that is all we can ask. That said I wouldn't use Fortran on its own, I use it with Python, it gets around the short comings of the language (for my use case). If I could I use one language I would use C++, I mean Fortran is a terrible general purpose language and Python is too slow on its own for most of what I do. Since I am not bound by such restrictions, I use Python and Fortran together, which I think is a far superior solution for most of what I do. On there own they are both inadequate for my needs but jointly I think they work well together (once  again for the scientific uses). I use C as well in extensions, I just use Fortran a hell of a lot more. I use C when using C libraries like METIS,  or if it is equally as easy as Fortran sometimes, not usually I use C to mix things up a little.  

> 
I guess i could have explained my above code better. XS was holding points of interest (which would change between runs of the code). For each point of interest i needed to look though some other data and see if it was near that point. I dont see how that could be expressed in array notation.
In a more realistic setting (by that I mean something you regularly do) you are more likely declaring the array on the heap (using Python) and passing to a function, in that case there is little difference between the either Fortran of C for simple operations like you described.

> 
if what you are doing is that simple you can do it straight in numpy. or use numexpr to multithread it. i would only jump out of python if it was impossible to express what i needed without a loop.There are a couple of points here, the first one of which is important. One, the operation I expressed is obviously only going to be written in a compiled language if it is a part of a large loop. You may have many such operations in such a loop. So using numpy or numexpr is to slow. In this case that part of the operation (something that is similar to what we very commonly do as scientific programmers) is far easier and safer to do in Fortran than C.  

Second point (a very minor one and arguably practically unimportant in most cases) if you are really after optimal performance on a complex operation you won't get that from numexpr either. To understand this you need to understand expression templates. I used to use these regularly back in my C++ days and they still are not optimal in performance. One while they solve the problem of temporary array allocation of "old fashioned" operating overloading for some operations they do not do them for them all.  For example matrix multiplication (in general) still needs the creation of a temporary.  So depending on the exact bottleneck in the code numpexpr may still be far from optimal. Admittedly this is a minor issue as it is uncommon (although it does happen) in practice. My first point is very relevant however.

One other point that should be highlighted, you note you could just as easily do that with operation with numpy. The reverse way to look at it is, it is nearly as easy to use Fortran as numpy (this certainly could not be said about C), but you will get the speed of a compiled language. For writing scientific extensions, where you want to do large amounts of these kinds of operations inside loops, this is invaluable.

---

