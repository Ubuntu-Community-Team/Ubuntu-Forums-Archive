---
title: "No speedup from -march=core2?"
date: 2009-08-08
forum: Programming Talk
---

### Post by stair314 on 2009-08-08
I just upgraded to g++ 4.3 and was excited to try out the -march=core2 optimization. Unfortunately it has had no effect on the runtime of my program. I was already using -O3. Is there something else I should do to get the benefit of the optimization?
My code is essentially all math: matrix-matrix or matrix-vector multiplication using Eigen 2.0.4, and lots of evaluating tanh in a tight for loop. I don't see any speedup for small problem sizes or large ones.

---

### Post by tgalati4 on 2009-08-09
There are a few things you can do.  They require some work.

Try profiling your code.  You will have to search for the appropriate tools, but look to see where your cpu cycles are being used.  Use the 80/20 rule--80% of your cpu cycles are consume in 20% of the code.  Post a section of that code on the forums.  There are a few smart people who can offer suggestions.

-O2 and -O3 optimizations work better when you structure your number crunching in such a way that the optimization routines can easily recast them to more efficient code.

Multiprocessor subspace crunching can sometimes speed up numerical solutions.  Unrolling loops, changing order of math operations, etc.

Are you running 64-bit?  If so, then single precision math should give the same numerical precision as double precision in 32-bit mode.  That saves you a clock cycle for each add and multiply operation.  This requires you to rewrite your code to single precision and compile for 64-bit.

man time

for some basic profiling.

As far as Core2, I'm sure Intel has white papers extolling the virtues of their new processor.  You will have to do some research to determine what exactly the core2 optimization is doing.  2-way associative cache, shared cache, and of course multi-processing all need to be considered when writing your code for a specific architecture.

If your code is writing out temporary results to a file, consider running your code in a ramdisk to reduce the I/O wait.

---

### Post by stroyan on 2009-08-09
If your program spends a lot of time in tanh from libm.so.6 then compiling your program with -march=core2 may not be nearly as important as compiling libm.so with -march=core2.
You could get the source for libc6-dev and rebuild /usr/lib/libm.a.
Or you could use an optimized library like the Intel Math Kernel Library.
[http://software.intel.com/en-us/intel-mkl/](http://software.intel.com/en-us/intel-mkl/)

Another approach is to use the multiple cores.
Adding a few pragmas and options could take advantage of the OpenMP feature of gcc to use multiple threads.
Have a look at [http://en.wikipedia.org/wiki/OpenMP](http://en.wikipedia.org/wiki/OpenMP) or google for tutorials.

---

### Post by stroyan on 2009-08-09
> **tgalati4 said:**
> 
Are you running 64-bit?  If so, then single precision math should give the same numerical precision as double precision in 32-bit mode.  That saves you a clock cycle for each add and multiply operation.  This requires you to rewrite your code to single precision and compile for 64-bit.

You are mistaken.
32-bit vs 64-bit pointers has no effect on the precision of floating point math.
A float is still a 32-bit representation.

Compiling as 64-bit does make more floating point registers available.
That can help to improve the performance of loops operating on many values.

---

### Post by stair314 on 2009-08-09
Essentially all of my time is spent in Eigen:

> 
Each sample counts as 0.01 seconds.
  %   cumulative   self              self     total           
 time   seconds   seconds    calls   s/call   s/call  name    
 37.90      0.47     0.47      400     0.00     0.00  void Eigen::ei_cache_friendly_product<float>(
int, int, int, bool, float const*, int, bool, float const*, int, bool, float*, int)
 18.55      0.70     0.23      200     0.00     0.00  sdn::SingleLayerNetwork::backProp()
 17.74      0.92     0.22      200     0.00     0.00  Eigen::Matrix<float, 10000, 10000, 2, 10000, 
10000>& Eigen::MatrixBase<Eigen::Matrix<float, 10000, 10000, 2, 10000, 10000> >::lazyAssign<Eigen::
Product<Eigen::Matrix<float, 10000, 10000, 2, 10000, 10000> const&, Eigen::Transpose<Eigen::Matrix<
float, 10000, 10000, 2, 10000, 10000> > const&, 1> >(Eigen::MatrixBase<Eigen::Product<Eigen::Matrix
<float, 10000, 10000, 2, 10000, 10000> const&, Eigen::Transpose<Eigen::Matrix<float, 10000, 10000, 
2, 10000, 10000> > const&, 1> > const&)
 16.94      1.13     0.21      500     0.00     0.00  Eigen::Matrix<float, 10000, 10000, 2, 10000, 
10000>& Eigen::MatrixBase<Eigen::Matrix<float, 10000, 10000, 2, 10000, 10000> >::lazyAssign<Eigen::
CwiseBinaryOp<Eigen::ei_scalar_difference_op<float>, Eigen::Matrix<float, 10000, 10000, 2, 10000, 1
0000>, Eigen::CwiseUnaryOp<Eigen::ei_scalar_multiple_op<float>, Eigen::Matrix<float, 10000, 10000, 
2, 10000, 10000> > > >(Eigen::MatrixBase<Eigen::CwiseBinaryOp<Eigen::ei_scalar_difference_op<float>
, Eigen::Matrix<float, 10000, 10000, 2, 10000, 10000>, Eigen::CwiseUnaryOp<Eigen::ei_scalar_multipl
e_op<float>, Eigen::Matrix<float, 10000, 10000, 2, 10000, 10000> > > > const&)


Thanks for all the suggestions for how to optimize the code. I've spent a lot of time optimizing it already though, so I was mainly curious if anyone knew much about the effect of the -march=core2 flag. Thanks!

---

### Post by Habbit on 2009-08-09
> **stair314 said:**
> I was mainly curious if anyone knew much about the effect of the -march=core2 flag. Thanks!

From [the GCC 4.3.4 manual]("http://gcc.gnu.org/onlinedocs/gcc-4.3.4/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options"), -march=core2 should enable all of mmx, sse, sse2, sse3 and ssse3. If you were using -march=nocona before, as most people were doing, there are no additional instruction sets, and most changes might be in the instruction scheduling, etc. Thus, YMMV.

---

### Post by ibuclaw on 2009-08-09
> **stair314 said:**
> Essentially all of my time is spent in Eigen:



Thanks for all the suggestions for how to optimize the code. I've spent a lot of time optimizing it already though, so I was mainly curious if anyone knew much about the effect of the -march=core2 flag. Thanks!

All what -march does is enable instruction subsets supported by the given local machine. -march=core2 just sets 64-bit extensions, MMX, SSE, SSE2, SSE3 and SSSE3 instructions in the code.

You may want to try **-march=native** instead, as that should choose the best option for your CPU type. But considering the speed of hardware, you probably won't notice much of a difference.


Now, trying a different compiler may produce different results ... someone earlier suggested the Intel Maths Library. I can vouch that the Intel C Compiler is excellent for programs you want to run more optimised on Intel CPUs.

You can get the Application Developer License version here: [http://www.intel.com/cd/software/products/asmo-na/eng/compilers/clin/219856.htm](http://www.intel.com/cd/software/products/asmo-na/eng/compilers/clin/219856.htm)

Regards
Iain

---

### Post by fr4nko on 2009-08-09
> **stroyan said:**
> 
Another approach is to use the multiple cores.
Adding a few pragmas and options could take advantage of the OpenMP feature of gcc to use multiple threads.
Have a look at [http://en.wikipedia.org/wiki/OpenMP](http://en.wikipedia.org/wiki/OpenMP) or google for tutorials.
Good suggestion, openmp can be an excellent way to effectively use multicore CPU. As far as I now today there is no compiler that can automatically optimize your code to effectively use multiple cores, you have to try to make you code parallel by yourself and openmp can be easy to use.

I've written a C program for the [shootout language benchmark]("http://shootout.alioth.debian.org/u32q/benchmark.php?test=binarytrees&lang=all") for the binary-tree by using the openmp library and it is the fastest implementation till now :-({|=

Francesco

---

### Post by tgalati4 on 2009-08-09
You are correct.  I was thinking FORTRAN with double vs single precision.  On an old Octane (MIPS 64-bit processor) double precision was actually quad precision.  This was neat (about 28 digits of precision) but overkill for most problems.  So, that required rewriting your code for single precision, which resulted in a nice speed increase.

---

