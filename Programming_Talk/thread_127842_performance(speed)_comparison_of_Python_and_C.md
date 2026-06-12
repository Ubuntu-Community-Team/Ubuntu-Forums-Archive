---
title: "performance(speed) comparison of Python and C"
date: 2006-02-09
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-09
My professor today told me that C is much faster than Python and that I should avoid python if I have to get the complex mathematical program working efficiently.

how true is the above statement.

Any comments please.

---

### Post by matthew on 2006-02-09
C is definitely faster. For most things it won't matter, but if you are writing something that is math intensive you will be better off using C. Python is great for quick mockups, prototyping, or writing stuff for use on the desktop (other things, too...this is a generalization) but if you need speed C is better.

Why the speed difference?

C is compiled into machine language. Python must run using an interpreter which is inherently slower as it adds an extra step to the process every time the program is run.

---

### Post by Ozitraveller on 2006-02-10
When a C program (any compilable language) is compiled, it is converted into and executable, i.e. a form that is ready to be executed. Whereas Python (and any other interpreted language) does it's conversion as every statement is executed. Generally speaking..

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=krypto_wizard]My professor today told me that C is much faster than Python and that I should avoid python if I have to get the complex mathematical program working efficiently.[/quote]It depends on the situation and what you're coding.

It very well may turn out that the differences that do exist don't matter for your code, if you design it correctly.  Correct design yields performance gains on the orders of hundreds or thousands, moving closer to the hardware only nets gains on the orders of tens or hundreds, tops, best case.

[quote=matthew] 	C is definitely faster. For most things it won't matter, but if you are writing something that is math intensive you will be better off using C.[/quote]No, you won't be.  For matrix computation, a good matrix library in python won't be much slower than C.  C++ would be a different story, as it's eaiser to leverage some nitfy tricks there for that sort of thing.

> Python must run using an interpreter which is inherently slower as it adds an extra step to the process every time the program is run.No, that has nothing to do with it in this case.

---

### Post by 3rdalbum on 2006-02-10
Real-world speed differences between Python and C is a hot topic.

I would argue that Python code is much easier to optimise than C, and that it's much easier to write it efficiently than C. Add to this the ability to call modules written in C, then add to it the ability to use special modules like Psycho to further optimise the code, and you'll find that the speed difference isn't that great.

There are tools around to actually kinda "compile" Python code to C, but I don't know how effective they are or even whether they're available for Linux. (Heck, I don't even know if Psycho is available for Linux).

---

### Post by matthew on 2006-02-10
[quote=LordHunter317]It very well may turn out that the differences that do exist don't matter for your code, if you design it correctly. Correct design yields performance gains on the orders of hundreds or thousands, moving closer to the hardware only nets gains on the orders of tens or hundreds, tops, best case.[/quote]This is a valid and excellent point.

---

### Post by krypto_wizard on 2006-02-10
I am trying to write a code which has 10,000 nodes and they mimic a Bit torrent like file sharing mechanism.

I am not using threads but just a standalone kind of program which has to deal with lot of data. I personally thought that this program won't make much of a difference in python (or C for that matter).

Any suggestions to write such kind of programs. Its kinda class project and I have been assigned to simulate a BitTorrent like file sharing mechanism where a server has a full copy and then 10000 users come in the swarm. I have to simulate such enviroment. I can assume certain data for upload and download speed for nodes. And finaly I have to present data such mean download time, share ratio of nodes etc.

All your help is greatly appreciated.

Thanks

---

### Post by Viro on 2006-02-10
[QUOTE=LordHunter317]
It very well may turn out that the differences that do exist don't matter for your code, if you design it correctly.  Correct design yields performance gains on the orders of hundreds or thousands, moving closer to the hardware only nets gains on the orders of tens or hundreds, tops, best case.
[/QUOTE]

In theory, this is true. However, if you're saying that C has gains in the order of tens or hundreds, assuming your program in C takes an hour to complete a task, your python program is going to take 10 - 100 hours. Sometimes, no amount of correct design will make up for a poorly performing runtime.

Sadly, while I love the Python language to bits, it is far too slow. Sure, you can make Python fast by delegating work to C libraries. However, if you're solving a problem that doesn't have a C library, you're stuck with either implementing the entire thing in Python, or writing most of the stuff in C and using Python as a sort of glue. Neither of these options are appealing to me, mainly because it boils down to a trade off. Write your app in an hour and see it taking a day to run, or writing your app in a day and seeing it take an hour to run. 

As things currently stand, Python is no where near the speed of C. It is good for prototyping applications, but I believe that the final code should be done in something else.

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=Viro]In theory, this is true. However, if you're saying that C has gains in the order of tens or hundreds, assuming your program in C takes an hour to complete a task, your python program is going to take 10 - 100 hours.[/QUOTE]That's best case, and for numerical crunching you could see that.  But likely, you won't, especially if you're really doing the math in a C or C++ library.  

I will agree that if you to do everything in pure python, it will be incredibly slow for these sorts of tasks.  This is due to the design of the language and some runtime braindamage.

> As things currently stand, Python is no where near the speed of C. It is good for prototyping applications, but I believe that the final code should be done in something else.If you're CPU-bound sure, which many numerical applications are.  If you're not, then it matters far, far less (which is the overwhelming majority of code out there).

---

### Post by jerome bettis on 2006-02-10
aren't most of the standard python libraries written in C?  i remember reading that somewhere, that the majority of the libs are "highly optimized C code" (i definately remember that exact quote)

i'm not sure if it's true, and to be honest i really don't care.  i've decided i'm not a fan of python.  i gave it a shot, and at first i thought i liked it, but i don't.  it promotes bad habits and it's design seems kinda ad lib instead of well thought out in advance.  it just doesn't have the tight uniformity that i think a good language should have.

teach someone python programming first and they'll have to work much harder to catch up to those who were taught a language that emphasizes good programming practice, like pascal.  python doesn't seem to care at all about that [-(

/rant

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=jerome bettis] i gave it a shot, and at first i thought i liked it, but i don't.  it promotes bad habits[/quote]Such as?

>  and it's design seems kinda ad lib instead of well thought out in advance.Examples?

>   it just doesn't have the tight uniformity that i think a good language should have.As opposed to what?  "Syntax mimics usage" C and C++?  "void pointers arent' really" Java and C#?

> teach someone python programming first and they'll have to work much harder to catch up to those who were taught a language that emphasizes good programming practice, like pascal.Language rarely matters in teaching someone good programming practice.

---

### Post by jerome bettis on 2006-02-10
hmm you can't delete your posts ...  they should add that feature

---

### Post by jerome bettis on 2006-02-10
i knew you we're gonna jump all over me.  :rolleyes:

i prefer variables that have to be actually declared and typed at the time the program is written - i want to see you argue against that one! :p 

i personally like the { } to line up blocks.  yes the whitespace thing is a novel idea and most people are ok with it, but i have an easier time reading code with the {}.   a bunch of little things like that just irk me about python.  no private methods?  ok, let's just pretend it's private  by making it look bad with __ everywhere.   and the [:-1] thing for reversing an array looks like something from C++.  i'll try to think of some more ..

everyone is different, most people like python and don't care for java, i'm the other way around.  i think java is the best language to type and produce code in right now.  

you really think teaching VB right away would not put people into bad habits?  come on, language definately matters.  someone who learns C first will almost certainly have a stronger foundation that python.

i will give python credit, it's flexible and well suited for all kinds of stuff.  the map and lamda functions are really neat, built in dictionaries etc.  it has a lot of nice things, it's just not my cup of tea at the moment.  and you'd never catch me teaching it to someone without a strong foundation and the proven ablity to think and develop solid code.

but this is way off topic, we're supposed to be talking about speed anyway.

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=jerome bettis]i prefer variables that hve to be actually declared and typed at the time the program is written - i want to see you argue against that one! :p[/quote]I won't, because as a rule I prefer static type-checking as a rule, but preferably with type inference, which precious few languages have.  At least C++ carefully written lets you do some type-inference through templates and MPL.  C# 3.0 will add much needed basic type-inferencing.

> i personally like the { } to line up blocks.  yes the whitespace thing is a novel idea and most people are ok with it, but i have an easier time reading code with the {}.This I'll agree to, and despite what python people say, is a valid complaint.

>   a bunch of little things like that just irk me about python.  no private methods?  ok, let's just pretend it's private  by making it look bad with __ everywhere.I've noted that for most things, Smalltalk OOP is a travesty.  We're in agreement here.  However, in practice, these things are small*er*.

I can think of some major reasons to hate python, most of them stemming from interpreter braindamage.

>    and the [:-1] thing for reversing an array looks like something from C++. ITYM Matlab. 

> you really think teaching VB right away would not put people into bad habits?No, I don't, as long as you clearly explain it's limitations and how to overcome them.  Programmers need to be able to think critically. 

Besides, VB.NET is just verbose C#.

>  come on, language definately matters.  someone who learns C first will almost certainly have a stronger foundation that python.No, I don't believe that all.  Most of the things one learns about C aren't convertiable to any other language.  And the things they learn that apply everywhere can be taught in any language, by definition.

>  and you'd never catch me teaching it to someone without a strong foundation and the proven ablity to think and develop solid code.I don't think I'd let you teach anyone, as you have a stunted opinion about what is important in CS and software engineering.

---

### Post by cwaldbieser on 2006-02-10
[QUOTE=LordHunter317]
I can think of some major reasons to hate python, most of them stemming from interpreter braindamage.
[/QUOTE]
I noticed you have mentioned this a few times, however I am not sure exactly what you are getting at.  "interpreter braindamage" does not succinctly convey your point to me.

Maybe you would care to elaborate for the benifit of those of us who are not familiar with your particular complaints?

---

### Post by cwaldbieser on 2006-02-10
[QUOTE=jerome bettis]
i prefer variables that have to be actually declared and typed at the time the program is written - i want to see you argue against that one! :p[/QUOTE]
I don't always care to declare variables, especially if they aren't typed.  For example, in VBScript or JavaScript, I am not all too crazy about "dim"ing a variable or declaring it with "var".  I like the syntaxes like python, awk, and bash scripts where you can just use the variable when you need it.

I do recognize the benefit of having the compiler do static type-checking.  For some projects it seems like a big benefit, for others, it doesn't seem so important.

---

### Post by LordHunter317 on 2006-02-11
> **cwaldbieser]I noticed you have mentioned this a few times, however I am not sure exactly what you are getting at.  "interpreter braindamage" does not succinctly convey your point to me.[/quote]The garbage collector won't sweep reference-cycled objects by default, on the virtue of it being reference-counted.  You can tell it to do so, but default policy can lead to leaky memory or worse: leaked unmanaged resources.

The intrepreter is not thread safe.  "Multithreaded" python applications cannot run multiple threads concurrently.  Rather, you just have cancellations at regular intervals.

The heap allocation strategy has several bugs that make it prone to heap fragmentation and lead one to situations where memory will never be returned to the heap that should be.  Memory allocated for primitive types is never released and always reused for those primitve types.  For many applications this is fine said:**
>  	I don't always care to declare variables, especially if they aren't typedThis is absolute crazy talk.  While not everyone is for static typing, arguing for variables not being predeclared is generally crazy.  Typos are a huge source of bugs and without mandatory variable declaration, the compiler and runtime cannot do that. 

You'll note every style guide for every language that doesn't require variable declaration tells you not to do it.  That's for a damn good reason.

---

### Post by cwaldbieser on 2006-02-11
[QUOTE=LordHunter317]
This is absolute crazy talk.  While not everyone is for static typing, arguing for variables not being predeclared is generally crazy.  Typos are a huge source of bugs and without mandatory variable declaration, the compiler and runtime cannot do that. 

You'll note every style guide for every language that doesn't require variable declaration tells you not to do it.  That's for a damn good reason.[/QUOTE]
Crazy or not, I have not observed the practice to cause any major problems during my daily use.  This may be related to the fact that the interpreters I am normally using don't do as good a job about catching the typos as they could.   For example:

```

Option Explicit

dim x
x = 1
if x = 2 then
    msgbox "Frotz: " & xx
else
    msgBox "Plugh: " & x
end if

```
This (contrived) example will actually run fine, even though I made a typo ("xx" instead of "x") at one point.  If I change the assignment to "x = 2", then the interpreter cries foul, but by this point, I already know something is wrong because my outputs are queer.

Also, in a good proportion of problems that I have observed that were caused by typos, the variables *were* declared-- both the correct variable and the typo variable.

I suppose that the reason that these typo problems have not seemed to serious to me is that I do not find myself often working with tools where both of the following conditions exist: 
a) you have the option not to declare variables
b) the compiler/interpreter does a good job capitalizing on the extra information you are giving it by providing the declarations.

---

### Post by LordHunter317 on 2006-02-11
[QUOTE=cwaldbieser]This (contrived) example will actually run fine, even though I made a typo ("xx" instead of "x") at one point.  If I change the assignment to "x = 2", then the interpreter cries foul, but by this point, I already know something is wrong because my outputs are queer.[/quote]Right, and with a compiler that required variable declarations, *you couldn't have even run the code.*

With an interpreter that does the same, hopefully you would have either got an exception at function call / compile time or at the actual execution.  Then you don't have to see the output as it halts code.

Both are better then forcing the programmer to detect, since he's prone to miss such things.

> Also, in a good proportion of problems that I have observed that were caused by typos, the variables *were* declared-- both the correct variable and the typo variable.Well yes, there's no way aroudn that.

---

### Post by steve.horsley on 2006-02-11
[QUOTE=LordHunter317]The garbage collector won't sweep reference-cycled objects by default, on the virtue of it being reference-counted.  You can tell it to do so, but default policy can lead to leaky memory or worse: leaked unmanaged resources.
[/QUOTE]Yikes! I thought there was a theread that periodically scanned for cyclic garbage. 

In fact this doc says it does not run periodically, but when allocations exceed deallocations by a threshold. That seems rather simplistic to me, and it does seem possible to permanently accumulate a large number of cyclic structures, but only if it reaches a steady state freeing (by dereferencing) as many objects as it is allocating before it frees the cyclic objects.

[http://docs.python.org/lib/module-gc.html](http://docs.python.org/lib/module-gc.html)

and this GC seems to be enabled by default:
> steve@StevesPC:~$ python
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gc
>>> gc.isenabled()
True
>>>

---

### Post by LordHunter317 on 2006-02-11
[QUOTE=steve.horsley]Yikes! I thought there was a theread that periodically scanned for cyclic garbage.[/quote]It does, but if you read that page carefully, it can't free them in all situations.

This is because it doesn't provide any mechanism for determining how to run finalizers.  I'm not sure how .NET and Java get around this, but they do.

---

### Post by kvorion on 2006-02-11
Since the discussion is about C, I would like to ask the people here whether it is worth the effort to learn Python if you are already good at C. I love to learn new programming languages, but I have heard people say that Python is a good "first language" to learn, because it is kind to beginners.

I am good at C/C++ and I use them for most of my assignments. I would like to know how Python would be useful to me apart from the enlightening experience that accompanies any new knowledge.

---

### Post by Van_Gogh on 2006-02-11
I don't know C well, only done some cursory reading, but I do know that most of the problems I solve with Python, I wouldn't want to do in C, because I'd have to write 10-50 times the number of lines to solve the same problem, with less flexibility. So I definitely recommend learning Python or some similar language. 

After you've learned it, you'll soon see that there are quite a few problems that are better solved in quick'n'loose languages like Python than rigid C(of course the inverse is also true).

I have a programmer friend who only knows Java and C# and basically believes that they are the be-all of programming languages. I've shown him some code I've written in Python and he always insists that "there must be something wrong somewhere", if I could do that in so few lines, so I can't impress him into trying Python. I can apparantly only impress him with Fortran(which is also a very nice language for its uses), but it's nothing near Python in pleasantness...

---

### Post by Jessehk on 2006-02-11
Whenever I program something (only programming small little apps right now) with Python I always accomplish more, but I get a sense that I am cheating.

I get a lot more satisfaction from making a template class in C++ with the STL in 50 lines then I do when I make the same thing in Python with 15.

---

### Post by krypto_wizard on 2006-02-12
Why do you think that you are cheating yourself ?

Does C/C++ gives you a felling of accomplisment ? 

Can you lighten this more.

[QUOTE=Jessehk]Whenever I program something (only programming small little apps right now) with Python I always accomplish more, but I get a sense that I am cheating.

I get a lot more satisfaction from making a template class in C++ with the STL in 50 lines then I do when I make the same thing in Python with 15.[/QUOTE]

---

### Post by Jengu on 2006-02-12
If you want to get something done, use Python. 99% of the time it will be sufficient for what you need and faster to work with.

That said C still lets you get closer to the hardware and gets compiled to machine code. So it's more appropriate for some tasks. But most desktop apps have only a few specific operations that require much computing power and you can specifically write those sections in C and leave the rest of your program in Python. For more intensive applications this isn't necessarily true (Unreal Engine 3 has a flat performance profile for instance).

But the gap between C and Python may shorten soon. The [PyPy]("http://codespeak.net/pypy/dist/pypy/doc/news.html") project is working on making Python JIT (just in time) compiled like is now done with Java, along with pulling some other sweet performance enhancing tricks. A year from now I would not be surprised if PyPy leaves the current Python interpreter (written in C) in the dust.

Shuttleworth prefers software written in Python. There's a reason.

---

### Post by Single on 2006-02-12
[QUOTE=Jengu]The [PyPy]("http://codespeak.net/pypy/dist/pypy/doc/news.html") project is working on making Python JIT (just in time) compiled like is now done with Java, along with pulling some other sweet performance enhancing tricks. A year from now I would not be surprised if PyPy leaves the current Python interpreter (written in C) in the dust.
[/QUOTE]
I think [Freeze]("http://wiki.python.org/moin/Freeze") and [py2exe]("http://www.py2exe.org/") are more interesting, since they don't even require jit or interpreter.

---

### Post by hod139 on 2006-02-12
This post seems to have gotten away from the original posters question:
[quote=krypto_wizard]
My professor today told me that C is much faster than Python and that I should avoid python if I have to get the **complex mathematical** program working **efficiently**.
[/quote] (emphasis mine)

While I have never programmed in Python, I have done plenty of complex mathematical programming in C, where for me complex mathematical programming implies CPU intensive programming. 
[quote=krypto_wizard]
how true is the above statement.
[/quote] One reason to use C for complex math instead of Python (note, this is a comparison between C and python, I'm going to ignore C++, Java (colt library) and Matlab for the rest of the post) is the large set of math and linear algebra libraries available, for example CBLAS ([http://www.intel.com/software/products/mkl/docs/mklqref/cblas.htm]("http://www.intel.com/software/products/mkl/docs/mklqref/cblas.htm")) and GSL ([http://www.gnu.org/software/gsl/)]("http://www.gnu.org/software/gsl/%29;"). Another argument for C is the good references available, for example "Numerical Recipes in C " ([http://www.library.cornell.edu/nr/bookcpdf.html)]("http://www.library.cornell.edu/nr/bookcpdf.html%29").   The BLAS library was written for Fortran and is highly tuned/optimized.  It is **the** library all other linear algebra packages (ATLAS, LAPACK, uBLAS) compare themselves again for both functionality, speed, and robustness. Matlab uses this library for most of its linear algebra computations.

As I said, I have never programmed in Python and maybe (doubtful) there are similar libraries available, but I would have a difficult time believing they are as well tested, fast, and robust as my two example libraries given. I would also be shocked to find trusworthy references for numerical programming in Python.

I'm not sure what your professor means by efficiency: time taken to write the program or efficiency of the running binary. If it is time taken to write the program, I would argue that C would be faster. For example, in vision a commonly required matrix operation is Sigular Value Decomposition. Writing this method robustly is very difficult (the version in Numerical Recipes in C for example is not robust) but the version in GSL is very good (not perfect. In fact the only robust version I know of is Matlabs). For another example, how about implementing some of the many matrix-matrix or matrix-vector operations already available in CBLAS (the C wrapper to BLAS). To say this another way, GSL has already implemented over 1,000 commonly used functions for numerical computing, and the three levels of BLAS were written to solve the most common linear algebra (Matrix-Vector and Matrix-Matrix) functions.

If efficiency is the running time of the executable, again I would argue for C instead of Python, and it has nothing to do with language features. As I said earlier, the BLAS library is highly optimized and used as a benchmark against other libraries. GSL has a long history of development and improvements behind it, which isn't the best argument for efficiency but I don't want to look up official benchmarks. In any case, GSL implementations are not slow.

I would also argue that robustness is at least as important as efficiency in numerical computing. This would be another reason for using C, since as I have said many times now, the C numerical libraries are very robust. Developing robust numerical functions is also a very time consuming process.

Sorry for the long post, it just seems that every time someone mentions efficiency it usually becomes an argument about language specifics: compiled vs interpreted, garbage collection, heap management, etc. While these types of arguments are important, you can't forget about the problem you are solving. As LordHunter317 stated, "It very well may turn out that the differences that do exist don't matter for your code, if you design it correctly". This is a much more compact way of stating my rant! There are many C libraries available for numerical computing designed correctly, whereas to my knowledge, there are not any available for Python.

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=hod139]
As I said, I have never programmed in Python and maybe (doubtful) there are similar libraries available, but I would have a difficult time believing they are as well tested, fast, and robust as my two example libraries given. I would also be shocked to find trusworthy references for numerical programming in Python.
[/QUOTE]

I think someone mentioned it in this thread before, but here is the link:
[http://numeric.scipy.org/]("http://numeric.scipy.org/")
I am not into mathematical programming, but it seems to have been received well by the python community.  I am not sure how it would compare to some of the libraries you mention, but numerical programming in python does exist.

---

### Post by hod139 on 2006-02-12
The documentation costs $40.00!!  All I wanted to do was read what it can do; at least the old documention is still free.   

cwaldbieser, thanks for the reference (I didn't see it anywhere else in this thread), this is going to make for some interesting reading. I even see a SVD function!!!

---

### Post by hod139 on 2006-02-12
Ok, after a very quick look at some of the documentation, it seems that NumPy (the numerical python package) defines some N-dim array types, and uses the LAPACK and BLAS libraries to perform most of the linear algebra.  

There is going to have to be some wrapping involved to communicate with these libraries and I can't image it is going to come cheaply, but I may be wrong.  My first question is this, does anyone know the cost associated with wrapping the Python code to talk with a C or Fortran library? 

My second question is why would you want to use Python for numerical computing if it is only accessing C libraries to begin with?  Why not use C which will be able to access these libraries natively and more efficiently?  I have a feeling answers to this question are going to be limited to personal preferences, but maybe I'll be surprised by some.

This does seem like an interesting project though, and it makes me wonder why Lawrence Livermore National Labs wants numerical computing capabilites in Python.

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=hod139]Ok, after a very quick look at some of the documentation, it seems that NumPy (the numerical python package) defines some N-dim array types, and uses the LAPACK and BLAS libraries to perform most of the linear algebra.  

There is going to have to be some wrapping involved to communicate with these libraries and I can't image it is going to come cheaply, but I may be wrong.  My first question is this, does anyone know the cost associated with wrapping the Python code to talk with a C or Fortran library? 

My second question is why would you want to use Python for numerical computing if it is only accessing C libraries to begin with?  Why not use C which will be able to access these libraries natively and more efficiently?  I have a feeling answers to this question are going to be limited to personal preferences, but maybe I'll be surprised by some.

This does seem like an interesting project though, and it makes me wonder why Lawrence Livermore National Labs wants numerical computing capabilites in Python.[/QUOTE]

I think part of the answer is that a lot of the people who use it may be more into the mathematics than the programming aspect of it.  If you don't know C and you don't know python, it can be a lot easier to get something small working quickly in python than it can be in C.

---

### Post by hod139 on 2006-02-12
[quote=cwaldbieser]I think part of the answer is that a lot of the people who use it may be more into the mathematics than the programming aspect of it. If you don't know C and you don't know python, it can be a lot easier to get something small working quickly in python than it can be in C.[/quote]

I suppose that is the obvious answer.  Similarly, if you already know Python using this package you can perform numerical computations without having to learn another language.  

As an aside, if a user is only interested in mathematical programming, I would suggest AMPL or Matlab instead of C or Python (or anything else).   Of course, this thread was about math programming in C versus Python, so I'll try not to get too off topic.

---

### Post by Van_Gogh on 2006-02-12
[QUOTE=cwaldbieser]I think part of the answer is that a lot of the people who use it may be more into the mathematics than the programming aspect of it.  If you don't know C and you don't know python, it can be a lot easier to get something small working quickly in python than it can be in C.[/QUOTE]

Hear. hear. If learning Python takes a tenth of what it takes to learn C, I think many people are willing to trade-off computational speed for programming speed, especially if you're a professionla in another field than CS. And by using libraries like numeric or sciPy the hit you take from not using C(or Fortran or whatever) may be small enough to be acceptable.

---

### Post by nszabolcs on 2006-02-12
[QUOTE=hod139]
There is going to have to be some wrapping involved to communicate with these libraries and I can't image it is going to come cheaply, but I may be wrong.  My first question is this, does anyone know the cost associated with wrapping the Python code to talk with a C or Fortran library? 
[/QUOTE]
here is an old numerical computing benchmark:
[http://old.scipy.org/documentation/weave/weaveperformance.html](http://old.scipy.org/documentation/weave/weaveperformance.html)
(the results can be found at the end of the page)

[QUOTE=hod139]
My second question is why would you want to use Python for numerical computing if it is only accessing C libraries to begin with? Why not use C which will be able to access these libraries natively and more efficiently? I have a feeling answers to this question are going to be limited to personal preferences, but maybe I'll be surprised by some.
[/QUOTE]
you can use/test the functions from an interpreter! (like in matlab)

[QUOTE=hod139]
The documentation costs $40.00!! All I wanted to do was read what it can do; at least the old documention is still free.
[/QUOTE]
new scipy is not ready yet, the documentation will be free.
if you want to know the content of a python package it's pretty easy:
```

>>> import module
>>> dir(module)

```

---

### Post by hod139 on 2006-02-12
> **nszabolcs]here is an old numerical computing benchmark:
[http://old.scipy.org/documentation/weave/weaveperformance.html]("http://old.scipy.org/documentation/weave/weaveperformance.html")
(the results can be found at the end of the page)
[/quote] Very interesting. This page confirmed that straight Python for numerical computing is extremely slow said:**
> 
you can use/test the functions from an interpreter! (like in matlab)
 I keep forgetting you can do that with Python. Sounds like it could be neat, but there are usually many steps in setting up a numerical problem, not a single line. So without ever having used Python, I don't know how useful this would be.

[quote=nszabolcs]
new scipy is not ready yet, the documentation will be free.
if you want to know the content of a python package it's pretty easy:
```

>>> import module
>>> dir(module)

```[/quote] Thanks

---

### Post by Viro on 2006-02-13
[QUOTE=hod139]Very interesting. This page confirmed that straight Python for numerical computing is extremely slow; but it also showed that the overhead in calling highly tuned C and Fortran Gausse-Seidel solvers for a simple problem can also be made much lower than I (and even the authors of the site) thought. It seems to be a contrived example though, so those numbers may not be typical, but it proves it might not be as much overhead as I originally thought.  The weave stuff seems really interesting.  Good site.
[/QUOTE]

The problem with the results presented on that site, is the fact that most of the heavy lifting is left to the underlying C/Fortran library. As you have noted, it is fine for contrived examples, but if you're solving anything that hasn't been done before or where there isn't a convenient C library to delegate processing to (i.e. *you* are the one writing most of the code) you will find that Python has IMHO very little to offer over traditional languages like C/C++/Fortran. Even the best Python result on that site (using Pyrex) is approximately 20% slower than C++ code. 

That is what most of the Python aficionados don't seem to realize. If the only way of getting Python fast is to code the libraries in C, why should I bother with Python? I'm already having to code/debug in C with all the unavoidable headaches and pitfalls, why bother writing the glue code in Python? Why not just code the whole thing in C? Sure, C may be more difficult to learn than Python, but for numerical code? The speed increase you would get from writing in straight C completely negates whatever *potential* productivity gain Python gives.

Python is a nice language, and perhaps it works for writing glue code for simple GUI apps that do not do much processor intensive tasks. But for complex mathematical code, Python is a poor choice.

---

### Post by nszabolcs on 2006-02-13
[QUOTE=Viro]If the only way of getting Python fast is to code the libraries in C, why should I bother with Python? I'm already having to code/debug in C with all the unavoidable headaches and pitfalls, why bother writing the glue code in Python? Why not just code the whole thing in C? Sure, C may be more difficult to learn than Python, but for numerical code? The speed increase you would get from writing in straight C completely negates whatever *potential* productivity gain Python gives.[/QUOTE]

There is a cool programming contest, [www.challenge24.org](www.challenge24.org) (It is held in every year and you can use anything you want. In this year the first round will be on 02.26. and you can still register). Last year in the first round i solved every problem with less than 30 lines of python code! (well each team has 3 members, so not all the problems was solved by me on the contest, but i solved them all after the contest just for fun).
Now this is what you can not do in C. There were image processing, combinatorics, graph algorithms, text processing and other kind of interesting problems. I solved the image processing problem with scipy + PIL and that was the first time i used those libraries. If i had to use C it would have been hours just to find a suitable library and read the documentation.
Probably matlab would have been a good alternative, but that one has awkward syntax and a lack of libraries when you don't want to use it for numeric computing.
I don't think C is difficult to learn. My problem with C is the lack of a powerfull standard lib (or other well designed libs with uniform interface).
eg: data structures (hash table, dynamic array), string (no buffer overflow, unicode, ...), non-blocking io and most of the hihglevel staff in python/java/c#/ruby... std libs.

---

### Post by Viro on 2006-02-13
[QUOTE=nszabolcs]Last year in the first round i solved every problem with less than 30 lines of python code! [/quote]

I have never doubted that you Python programs are much shorter in length than the equivalent C program. The problem, as is the topic of this thread, and as I and others have mentioned is Pythons poor execution speed. Assuming you take 10 minutes to code the solution in Python, how long will it take you in C? Let's assume you take 6 times longer in C and take an hour to code up the solution. Is Python better than C? The answer depends on what you're doing with Python.

In the stuff I do, numerical analysis of complex chaotic systems, problem sets take hours to days to run. From my dabbling with Python, it seems that C is anywhere from 10x - 100x faster than Python. You can see where this is going. Even if Python allows me to code a solution faster than C, this productivity gain is completely negated by its poor runtime performance. 

The OP wanted to know if C was faster than Python for complex mathematical code. The answer is most definitely no. That doesn't mean you can't use Python for anything else, I like it for prototyping algorithms and such but I always code the final solution in C.

---

### Post by krypto_wizard on 2006-02-14
I believe quantitative evaluation of both C and Python would provide us better insight into the matter. For example some complex set of programs running over a large set and then comparing times. Is it a good metric for comparison ?

---

