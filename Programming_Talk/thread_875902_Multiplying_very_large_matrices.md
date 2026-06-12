---
title: "Multiplying very large matrices"
date: 2008-07-31
forum: Programming Talk
---

### Post by PaulM1985 on 2008-07-31
Hi

I have been trying to complete a project which involves multiplying two very large matrices together.  (3000x5000)

Since I am not able to store two matrices of that size and a third of 3000x3000 in my RAM memory, I have created csv files for each matrix.

I have created functions to return a row vector of floats from the first matrix and a column vector from the second to be multiplied together and create a value for the third (solution) matrix. 

I admit that this will take along time to do (as there are going to be 5000 multiplications per value), but I seem to be only completing one value a second.  Does anybody know of any quicker ways to multiply two matrices?

Paul

---

### Post by nvteighen on 2008-07-31
> **PaulM1985 said:**
> Hi

I have been trying to complete a project which involves multiplying two very large matrices together.  (3000x5000)

Since I am not able to store two matrices of that size and a third of 3000x3000 in my RAM memory, I have created csv files for each matrix.

A question: is this just a part of the project or the project itself? If it's just part, consider seriously to use a library that does this for you... otherwise, you'll be losing efforts in the wrong place...

But anyway, why should a 3000x5000 matrix not fit in your RAM? Unless you're storing it in the stack, which is limited, you could use dynamic memory...

What language are you using for this?

---

### Post by Npl on 2008-07-31
> **PaulM1985 said:**
> Hi

I have been trying to complete a project which involves multiplying two very large matrices together.  (3000x5000)

Since I am not able to store two matrices of that size and a third of 3000x3000 in my RAM memory, I have created csv files for each matrix.

I have created functions to return a row vector of floats from the first matrix and a column vector from the second to be multiplied together and create a value for the third (solution) matrix. 

I admit that this will take along time to do (as there are going to be 5000 multiplications per value), but I seem to be only completing one value a second.  Does anybody know of any quicker ways to multiply two matrices?

PaulI`d guess that the File-IO slows everything down. I dont know the csv-Format, but can you read whole rows/columns in chunks, or do you need alot of small reads?

Also, if you have enough memory, then keep the source Matrizes in RAM and write out the result-Matrix.

---

### Post by PaulM1985 on 2008-07-31
Hi  

I am using Java.  Matrix multiplication is just one part of it.  I have written functions for matrix transpose, singular value decomposition and pseudo inverse.  My project is for mathematical modeling.  I have tried storing the info in RAM before and I have had errors in Java saying that there was not enough memory.  

I originally carried this out on a smaller scale in Matlab, since functions like pinv were built in.  When I tried running the larger matrices through Matlab, I encountered memory errors and that is when I moved to Java.

Once I get the matrix multiplication sorted, I should save a lot of time as this function is heavily used.

I agree that opening and reading the files is probably the cause of the problem.  I am currently storing the matrix files on a USB memory stick and running the program on there so that my hard disk doesnt have to do the creating/deleting of large files.  Is there a way that I could use the USB stick as additional RAM memory? 

Paul

---

### Post by WW on 2008-07-31
Are your matrices dense or sparse (i.e. roughly what percentage of the entries are nonzero)?  If only a small percentage are nonzero, you can use some form of sparse matrix representation to save memory.

I don't use Java, so I don't know much about the available libraries, but surely linear algebra libraries already exist that can do this. Can you use any of the software listed at [Java Numerics](http://math.nist.gov/javanumerics/)? (Scroll down to the Libraries section.)

---

### Post by Zugzwang on 2008-07-31
Do you know that in the default setting, Java uses only 32MB of ram or so? You can increase the amount by adding "-Xmx512m" (for example: 512MB) to the Java invocation command on the terminal.

---

### Post by mike_g on 2008-07-31
Assuming that you are using 32bit datatype, then you would only require around 120MB of ram for you two matrices plus perhaps another 60 for the output. Like NPL said, file IO is almost definitely your bottlneck. So yeah, try increasing the RAM; that should sort it out.

If theres still issues with speed, one option would be to write a DLL in C, just to handle the calculations. GPUs are also very good at dealing with this kind of stuff, if you can program for them.

---

### Post by PaulM1985 on 2008-07-31
> **Zugzwang said:**
> Do you know that in the default setting, Java uses only 32MB of ram or so? You can increase the amount by adding "-Xmx512m" (for example: 512MB) to the Java invocation command on the terminal.

Hi Zugzwang,

So, to do this, do I type that in for compiling or running, so is it:

>javac -Xmx512m myfile.java

or 

>java -Xmx512m myfile

Paul

---

### Post by dribeas on 2008-07-31
>java -Xmx512m myfile

---

### Post by Reiger on 2008-07-31
But if this is 'the project'; then you're using the wrong tool for the job. You'd be better off using a functional language for this task; because some of those compiles do a pretty good job at optimizing code; not to mention that the languages themselves are geared towards these kinds of problems...

---

### Post by hod139 on 2008-07-31
I second WW's advice.  I have personally used the Colt ([http://acs.lbl.gov/~hoschek/colt/](http://acs.lbl.gov/~hoschek/colt/)) and it is very good.  You will hear a lot of people complain about the slower performance of java, but the Colt group has managed to write a BLAS implementation that is 90% as fast as FORTRAN.

---

### Post by marzshadow on 2008-08-02
> **PaulM1985 said:**
> Hi  


I agree that opening and reading the files is probably the cause of the problem.  I am currently storing the matrix files on a USB memory stick and running the program on there so that my hard disk doesnt have to do the creating/deleting of large files.  Is there a way that I could use the USB stick as additional RAM memory? 

Paul

Paul, USB sick memory is very slow.  Slower than disk.  And it has a limited number of writes (it's flash).  If you have to use files, use disk files.

--Mark

---

### Post by CptPicard on 2008-08-02
Also, you should not be using the naive method, there are better ones... 

[http://en.wikipedia.org/wiki/Matrix_multiplication#Algorithms](http://en.wikipedia.org/wiki/Matrix_multiplication#Algorithms)

(But I second the advice of using  something from a library...)

---

### Post by Erdaron on 2008-08-02
If you can use Python, then try NumPy, which is made specifically for dealing with matrices and arrays in an efficient manner. I haven't dealt with sets quite as huge as yours, but I've processed data sets with about 200,000 lines and eight columns of data, and while it wasn't super-fast, it certainly faithfully crunched through it without errors. NumPy is also in the Ubuntu repos.

A library is likely to be implementing one of those algorithms for improved efficiency.

---

### Post by pmasiar on 2008-08-02
> **Erdaron said:**
> If you can use Python, then try NumPy, ...A library is likely to be implementing one of those algorithms for improved efficiency.

NumPy is python binding for C libraries, used in scientific calculations. Speed would unlikely be issue there.

---

### Post by slavik on 2008-08-02
haskell can do matrix multiplication faster than C ...

what I would recommend is converting the second matrix so that rows are vertical and columns are horizontal, then you can read the rows you want using readline, multiply them and write them out to a file.

---

### Post by PaulM1985 on 2008-08-02
Hi 

Thanks with the advice using the -Xmx512m, but unfortunately I ran out of memory again, because I have to have a couple of other large matrices in memory for singular value decomposition.

I am using the USB stick because I didn't want to have any damage to my hard disk because of large scale writing and deleting.

I don't know Python, but know a bit of C.  Would you recommend using C instead of Java.  Would I be able to read and write to files as I am already doing?  

Any other general advice?

Thanks 

Paul

---

### Post by PaulM1985 on 2008-08-02
> **slavik said:**
> haskell can do matrix multiplication faster than C ...

what I would recommend is converting the second matrix so that rows are vertical and columns are horizontal, then you can read the rows you want using readline, multiply them and write them out to a file.


Hi Slavik

Thanks for the idea but that was something I had thought of and tried originally.  Unfortunately, it was still taking a very long time to compute.

Paul

---

### Post by CptPicard on 2008-08-02
> **PaulM1985 said:**
> 
I am using the USB stick because I didn't want to have any damage to my hard disk because of large scale writing and deleting.


Seriously now... this is the least of your concerns. Reading and writing are what hard drives are built to do, and throughout their lifetime, your matrix ops are a drop in the ocean...

---

### Post by PaulM1985 on 2008-08-02
The only reason I am concerned is that I have had to replace 2 hard disks on my laptop in the past and so I don't really want to have to get a 3rd.

---

### Post by CptPicard on 2008-08-02
In particular cheap laptop 2.5" drives do have quality issues. You also need to ask yourself whether you have enough RAM on your machine, if the laptop swaps constantly that really does kill the drive faster than it should die "of natural causes".

---

### Post by PaulM1985 on 2008-08-02
I know do need more RAM in both my computers, and really would like to replace them both, but Im a bit skint at the moment.

Im not sure how to do this, or if it is really a doable/practical solution, but would I be able to link my laptop and desktop computers together so that I would be able to use the RAM and processors on both?

Paul

---

### Post by CptPicard on 2008-08-02
That would require using very special libraries and coding against them... plus network latency would kill your multiplication performance.

---

### Post by pmasiar on 2008-08-02
> **slavik said:**
> haskell can do matrix multiplication faster than C ...

That's quite strong claim. Do you have any links to support it, or you will just fall back on your infallibility? :-)

---

### Post by slavik on 2008-08-02
can't find the link atm, but since haskel is a lazy evaluation language it doesn't evaluate the results of a function right away. this becomes useful when you might end up having 2 inputs that are the same (like in matrix multiplication, or taylor series or other mathematical functions). then you evaluate a function once for all the times it occurs.

that, and I'm infallible, you should know that by now. :)

---

### Post by CptPicard on 2008-08-02
> **slavik said:**
> becomes useful when you might end up having 2 inputs that are the same (like in matrix multiplication, or taylor series or other mathematical functions). then you evaluate a function once for all the times it occurs.

Hmm... I am not absolutely sure if pure-functional substitutability extends quite that far, that is, all the way to runtime? You would have to do a lot of caching at runtime which would probably kill performance in the general case. Of course in contexts where you can guarantee that x is some given value, you can compile different invocations of f(x) into the same one, but ... like the way you suggest, I am not sure :)

(I may be wrong here though, I am not infallible although I may often seem like I am...)

---

### Post by slavik on 2008-08-02
it has to do with the language being lazy. haskell has no problems passing partially evaluated functions. it's the only language to do this afaik.

---

### Post by pmasiar on 2008-08-02
> **slavik said:**
> it has to do with the language being lazy. haskell has no problems passing partially evaluated functions. 

... but will be lazy evaluation (with all the overhead of passing partially evaluated functions) more effective than just doing it as fast as we can, as C does? If yes, in which real-life scenarios/benchmarks? 

Seem that you do not have any hard data to support your claim, beyond of course your avatar's infallibilty - but that not good enough for me :-)

---

### Post by hod139 on 2008-08-03
> **PaulM1985 said:**
> The only reason I am concerned is that I have had to replace 2 hard disks on my laptop in the past and so I don't really want to have to get a 3rd.
You might be affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

Here is the forum's thread: [http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

---

### Post by Wybiral on 2008-08-04
> **slavik said:**
> it has to do with the language being lazy. haskell has no problems passing partially evaluated functions. **it's the only language to do this afaik**.

Since lisps code is a data structure, it can easily be held onto and evaluated later, it just doesn't do it implicitly.

```
([color=#008000]**let **[/color][[color=#19177C]value[/color] ([color=#0000FF]delay[/color] ([color=#008000]+ [/color][color=#19177C]x[/color] [color=#666666]2[/color]))]
  [color=#408080]*; (+ x 2) isn't evaluated yet*[/color]
  ([color=#008000]print [/color]([color=#0000FF]value[/color]))
  [color=#408080]*; Now it is*[/color]
  )
```

It's how lisp usually creates streams, via some kind of lazy cons.

In fact, you can do the same thing in any language that supports lambdas, for instance:
```
[color=#008000]**def**[/color] [color=#0000FF]take[/color](n, itr):
    [color=#008000]**for**[/color] i [color=#AA22FF]**in**[/color] [color=#008000]xrange[/color](n):
        [color=#008000]**yield**[/color] itr[[color=#666666]0[/color]]
        itr [color=#666666]=[/color] [color=#008000]apply[/color](itr[[color=#666666]1[/color]])

[color=#008000]**def**[/color] [color=#0000FF]fibs[/color](a[color=#666666]=[/color][color=#666666]0[/color], b[color=#666666]=[/color][color=#666666]1[/color]):
    [color=#008000]**return**[/color] (a, ([color=#008000]**lambda**[/color]: fibs(b, a [color=#666666]+[/color] b)))

[color=#008000]**for**[/color] i [color=#AA22FF]**in**[/color] take([color=#666666]10[/color], fibs()):
    [color=#008000]**print**[/color] i
```
Without that lambda, fibs would recurse forever. Instead the values are lazily evaluated as they're being pulled.

---

### Post by PaulM1985 on 2008-08-05
Hiya

I thought I would let you know my "solution" to continue with my project.  I don't think there are many options other than get more RAM. I have spoken to my work and they have let me run it on their server over the weekend.  Not a proper solution I know but that is how I am going to continue with it, if anyone was interested.

Paul

---

### Post by slavik on 2008-08-05
> **pmasiar said:**
> ... but will be lazy evaluation (with all the overhead of passing partially evaluated functions) more effective than just doing it as fast as we can, as C does? If yes, in which real-life scenarios/benchmarks? 

Seem that you do not have any hard data to support your claim, beyond of course your avatar's infallibilty - but that not good enough for me :-)
sometimes you might not have all the data to finish calculating a function, you might need to calculate a variable that is being computed somewhere else on the network, doesn't stop you from precalculating everything you can before more data comes.

---

### Post by matrixmatrixmatrix on 2008-10-03
i have a question,

i have to find some smart representation of large matrices in secondary memory. this representation have to be smart because then i have to use it to do matrix operation like multypling matrices, adding matrices and other operations...

i have to minimize the lseek of operating system....

somebody can help me?

---

