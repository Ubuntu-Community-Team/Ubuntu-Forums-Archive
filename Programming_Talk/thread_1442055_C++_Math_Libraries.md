---
title: "C++ Math Libraries"
date: 2010-03-29
forum: Programming Talk
---

### Post by PaulM1985 on 2010-03-29
Hi

I was wondering if anyone could recommend some c/c++ maths libraries.  The main functions I would require are matrix multiplication/inverse, line intersections, nearest point between two or more lines, various other algebra with vectors, data fitting.

I found codecogs but it seems like I would have to pay for it.  I could work at writing something like this myself but I assumed that there would already be something like this available that would probably be more efficient than anything I would create myself.

I was planning on using this with OpenCV.

Any suggestions?

Paul

---

### Post by TheBuzzSaw on 2010-03-29
How performance-sensitive does it need to be? Writing your own Matrix object should not be too difficult. The other stuff doesn't sound too hard either.

---

### Post by PaulM1985 on 2010-03-29
It would need to be pretty quick.  I probably will do it myself, just assumed that there would be something already available.  Seems like there might not be.  I have noticed that OpenCV does have quite a bit of the things I want already in it.

Any suggestions still would be appreciated.

Paul

---

### Post by MadCow108 on 2010-03-29
if performance is critical, don't do it yourself unless you have a lot of time and experience.

three libraries I've heard of:
[http://www.gnu.org/software/gsl/](http://www.gnu.org/software/gsl/)
[http://directory.fsf.org/project/atlas/](http://directory.fsf.org/project/atlas/)
[http://www.oonumerics.org/blitz/](http://www.oonumerics.org/blitz/)

---

### Post by PaulM1985 on 2010-03-29
The idea that I am looking at is hopefully creating something like Project Natal that Xbox are doing where games are played by people's movements.

I'm not kidding myself into thinking that I can "out-do" Microsoft since it is only me working on this for general interest and entertainment.   I thought I would mess around with a few webcams and see what results I can get.  Wearing a yellow rubber glove (something really distinct that would stand out on an image), seeing if I can track its movement in 3-d and returning coordinates before considering integrating it into some useful application.

Since there is going to be alot of matrix multiplication and projection calculations, I thought using something that has already been created is likely to be quicker and take me less time to get some sort of output.  

Thanks for the links.

Paul

---

### Post by abraxas334 on 2010-03-30
First thing I was taught, don't write your own linear algebra code ever! Even if you just have 4x4 martices. intel and other processor manufracturers use exisitng libraries to benchmark their processing power. So they are highly optimised fortran routines with c/c++ wrappers!
If you develop using ubuntu you can install most of the stuff using synaptic. The blas library is the mother of pretty much all linear algebra libraries! Only problem I find is that documentation is only understandable to people who wrote it, and you really need to know your problem well in order to pick the right routine!
[http://www.netlib.org/lapack/]("http://www.netlib.org/lapack/")
There are implementation for C++ making use of templates too! I am trying to tackle arpack++ at the moment. Its no fun, but hopefully it will be faster when I run it so I can forget about the painful development time!

---

### Post by TheStatsMan on 2010-03-30
For linear algebra have a look at eigen2. It is very impressive. Admittedly, I don't use it because we have MKL, which we use on the supercomputer one of my workplaces and I simply use ATLAS when I am not there. MKL is very fast and a lot of it is parallelized, whereas Eigen2 is not.    It is just a matter of linking to the different libraries.  If you go the BLAS, Lapack path the one thing that is worth writing yourself is a nice C++ matrix class to wrap the BLAS and Lapack subroutines that you wish to use. That way you can use the wrapped functions in performance critical sections and use overloaded operators in non-performance critical sections. In my opinion it is worth putting the effort in to overload the operators using expression templates where possible. 

 Both Atlas and MKL contain optimised versions of BLAS. ATLAS is opensource. Don't use an unoptimised version of BLAS it is real slow.

It isn't hard to match these libraries for 4x4 matrices, by the way. It is for large matrix*matrix multiplications that is what they do a really good job at.

---

