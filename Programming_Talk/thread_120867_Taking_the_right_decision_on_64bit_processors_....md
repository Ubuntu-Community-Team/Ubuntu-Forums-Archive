---
title: "Taking the right decision on 64bit processors ..."
date: 2006-01-23
forum: Programming Talk
---

### Post by dimis on 2006-01-23
[I was really confused where to put this thread and I hope I took the right decision.]

This is perhaps a long story, so I 'll try to be as brief as possible. It all started when I bought a brand new 64-bit machine about 1 year ago and I wanted to know the actual performance of my brand new pc (and of course verify that AMD was right when placing that plus (+) after the declared performance frequency compared to an Intel processor). So I thought it would be nice to have a test bed and test the performance of various processors.

Anyway, at that time, I created a [thread](http://forum.msi.com.tw/index.php?topic=79970.0;topicseen) on another forum (MSI due to my mainboard) because performance seemed to be outragously low and thought my motherboard was not well configured. Partially I was right about that, partially it was my limited knowledge about 64-bit processors at that time, and most notably it turned out that it was compiler+OS matters ...

So, you can all get a brief introduction to the story right [here](http://cgi.di.uoa.gr/~stud1098/amd). Please do not spend time reading the last lines of the page (i.e. "comments" and "some first conclusions") since most of that stuff is rubbish (due to many things I didn't know at that time). The running times you view on the above page were generated with the [DJGPP](http://www.delorie.com/djgpp/) compiler for windows.

I believe that some of you already have visited the above link, downloaded sources and executed same/similar experiments on your machine. If not, I suggest you do so now! (meaning visit [this](http://cgi.di.uoa.gr/~stud1098/amd) page, download sources and execute the 4 samples I present on that page).

For reference I will place running times of competition machines and DJGPP on my pc here:
```
Competition Machine (Pentium4@3 GHz ~ gcc / WinXP):
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Test-set : **perm17.in**
Cubic    :  3,186.813 msecs
Quadratic:     54.945 msecs
Linear   :     54.945 msecs
Test-set : **perm22.in**
Cubic    :  3,901.099 msecs
Quadratic:    934.066 msecs
Linear   :     54.945 msecs
Test-set : **perm30.in**
Cubic    : 11,923.077 msecs
Quadratic:     54.945 msecs
Linear   :     54.945 msecs
Test-set : **perm33.in**
Linear   :    714.286 msecs
```
Regarding the following AMD-processor-based pc, you can find more info on the specifications [here](http://cgi.di.uoa.gr/~stud1098/amd/cpuz.htm).
```
AMD 3000+ (s754) ~ DJGPP / WinXP :
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Test-set : **perm17.in**
Cubic    :  6,318.681 msecs
Quadratic:     54.945 msecs
Linear   :      0.000 msecs
Test-set : **perm22.in**
Cubic    :  9,010.989 msecs
Quadratic:  1,428.571 msecs
Linear   :      0.000 msecs
Test-set : **perm30.in**
Cubic    : 41,923.077 msecs
Quadratic:      0.000 msecs
Linear   :      0.000 msecs
Test-set : **perm33.in**
Linear   :    659.341 msecs
```
Comparing the above data is what made me angry at that time and I started that thread on MSI Forum. However, soon afterwards I tried to run the same samples with an executable I made with Visual Studio 6.0. Here is how things go with an executable made with Visual Studio 6.0 (Release version and no additional service packs for VS added on the following configuration):

[On the following tables my configuration has changed slightly from above, in the sense that I have added 512MB of RAM on my pc.]

```
AMD 3000+ (s754) ~ VS 6.0 / WinXP:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Test-set : **perm17.in**
Cubic    :  4,484.000 msecs
Quadratic:      0.000 msecs
Linear   :     15.000 msecs
Test-set : **perm22.in**
Cubic    :  5,375.000 msecs
Quadratic:  1,109.000 msecs
Linear   :     15.000 msecs
Test-set : **perm30.in**
Cubic    : 15,109.000 msecs
Quadratic:     31.000 msecs
Linear   :     15.000 msecs
Test-set : **perm33.in**
Linear   :  1,046.000 msecs
```
Now, these running times are far better than those achieved with DJGPP under 32bit-Windows. I believe this shows that the compiler Microsoft uses for Visual Studio 6.0 does much better optimization on source code or they somehow exploit in a better way system calls (after all it's a M$ os). The above results made me calm since one has to consider the overhead which is incurred on 32bit systems when instructing a 64bit processor and hence running times were pretty ok this time.

Since then, I was looking for a good 64bit OS so that I can take full advantage of my pc. It turned out that 64bit OSs are not mature yet and as a result one is not able to manage everything quite effortlessly. This made me install 32bit Ubuntu 5.10 - recommended by a friend of mine to whom I am grateful. I was told that AMD-64bit processors behave well on Ubuntu. So let's see the running times here:
```
AMD 3000+ (s754) ~ gcc 4.0.2 / Ubuntu 32bit:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Test-set : **perm17.in**
Cubic    :  6,680.000 msecs
Quadratic:     10.000 msecs
Linear   :     20.000 msecs
Test-set : **perm22.in**
Cubic    :  8,710.000 msecs
Quadratic:    860.000 msecs
Linear   :     10.000 msecs
Test-set : **perm30.in**
Cubic    : 31,490.000 msecs
Quadratic:     10.000 msecs
Linear   :     10.000 msecs
Test-set : **perm33.in**
Linear   :    650.000 msecs
```
Obviously the above results are better than those achieved with DJGPP on WinXP. However, the performance is simply ... bad! :( (Compare with running times obtained with VS6.0 on WinXP). I did that testing yesterday and I must admit that I was disappointed. So, I run 64bit Ubuntu (Live! CD) and gave a try of the above over there. Here are the scores:
```
AMD 3000+ (s754) ~ gcc 4.0.2 / Ubuntu 64bit (Live! CD):
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Test-set : **perm17.in**
Cubic    :  2,750.000 msecs
Quadratic:      0.000 msecs
Linear   :     10.000 msecs
Test-set : **perm22.in**
Cubic    :  3,490.000 msecs
Quadratic:  1,050.000 msecs
Linear   :     10.000 msecs
Test-set : **perm30.in**
Cubic    : 11,960.000 msecs
Quadratic:     10.000 msecs
Linear   :     10.000 msecs
Test-set : **perm33.in**
Linear   :    490.000 msecs
```
Now, these are running times! :D And these results certainly justify that the processor works @3000+ compared to an Intel processor.

My conclusion:
--------------
Generally speaking, I am pleased with the response times my pc has on 32bit systems (i.e. Ubuntu-32bit 5.10). However, the above indicate that if someone has an AMD 64bit processor and installs a 32bit OS he/she is going to make serious concessions on the performance of his/her system (working about 3 times slower - unless someone knows a trick that I am not aware of); especially if he/she is a student/researcher and wants to run processor-expensive experiments on that machine.
Let's hope the next Ubuntu 64bit release solves all side-problems that exist at the moment (I 've heard that the current Ubuntu release has some problems similar to those that appear on other 64bit OSs and hence I 've not even tried to install Ubuntu64 on my machine. I am too tired to try to find out for the time-being.)!  :)

Best regards and hope the above can help some AMD (and not only) users,
Dimis

---

### Post by LordHunter317 on 2006-01-23
[QUOTE=dimis]Comparing the above data is what made me angry at that time and I started that thread on MSI Forum.[/quote]Well, you shouldn't have.  Not only is that data stastically invalid and shouldn't be used to draw inferences, it's meaningless.

> [On the following tables my configuration has changed slightly from above, in the sense that I have added 512MB of RAM on my pc.]Not that it likely matters, but it means the data is invalid.

You shouldn't draw conclusions from this data.

> Now, these running times are far better than those achieved with DJGPP under 32bit-Windows. I believe this shows that the compiler Microsoft uses for Visual Studio 6.0 does much better optimization on source code or they somehow exploit in a better way system calls (after all it's a M$ os).It's well known that GCC is a terrible optimizing compiler.  This shouldn't suprise you in the least.

>  The above results made me calm since one has to consider the overhead which is incurred on 32bit systems when instructing a 64bit processor and hence running times were pretty ok this time.There is no overhead, and I don't know what you lead you to believe there is.  Whatever misinformation you have, you need to loose.

Any overhead comes from dealing with 64-bit code, if only due to the nature it's bigger.

> Now, these are running times!No, they're not.  We have no clue why that is, but I can venture some guesses.  Needless to say, that code ends up inadvertently exploiting some features of an AMD64 processor running in long mode, namely the extra registers.

On x86_64, code that fits entirely in L1 and that has mostly streaming data will reap huge benefits from the extra registers.  This is an example of such code.

You can't conclude anything from one test.  The P4 performs better likely due to it's deeper pipeline and larger caches, both of which will improve performance on this sort of code.


> :D And these results certainly justify that the processor works @3000+ compared to an Intel processor.It hasn't been compared to that for sometime.

> However, the above indicate that if someone has an AMD 64bit processor and installs a 32bit OS he/she is going to make serious concessions on the performance of his/her system (working about 3 times slower - unless someone knows a trick that I am not aware of); especially if he/she is a student/researcher and wants to run processor-expensive experiments on that machine.It indicates nothing of the sort.  To be blunt, you need to go take a class on basic statistics before you even consider making any more conclusions of this sort.  This is one tiny data point with easy explanations as to its behavior.

---

### Post by Viro on 2006-01-24
A couple of points about your benchmark. You need to use the same compiler on all processors in order to make your data valid. An executable that is generated by different versions of GCC will perform differently. This is widely documented. Unless you standardize the compiler version across all platforms, that invalidates your result too. On windows, try using MingW or Dev-C++ instead of the archaic DJGPP. 

Next, there are some rows where the execution time is  0.000 msecs. This should immediately ring the warning bells in your head. Something is clearly wrong here. This could indicate that the compiler has done something funky with your code. Or that your dataset isn't large enough to provide any meaningful result. 

Lastly, the compiler flags used. GCC is instructed to compile at -O3, but you do not specify the processor architecture. Is this wise? Perhaps you should try specifying the kind of CPU architecture used to see if this helps GCC.

---

### Post by Viro on 2006-01-24
I've just run some of your benchmarks on my machine (P3 1GHz) and there is definitely something wrong with the configuration of your AMD system. For the datasets Perm17.in and Perm22.in, my results are 7720.000 msecs and 10690.000 msecs. Just 1 second slower than your AMD 3000+ machine, which is impossible. 

I compiled them using the standard GCC that ships with Ubuntu, and my compiler flags were "-O3 -march=pentium3 -fomit-frame-pointer -s -DNDEBUG". Try those on your AMD machine and see what results you get.

---

### Post by dimis on 2006-01-24
> **Viro]A couple of points about your benchmark. You need to use the same compiler on all processors in order to make your data valid. An executable that is generated by different versions of GCC will perform differently. This is widely documented. Unless you standardize the compiler version across all platforms, that invalidates your result too. On windows, try using MingW or Dev-C++ instead of the archaic DJGPP. [/QUOTE]
You are totally correct on the above observations and I will soon try mingw or dev-c++ and see running times on Windows with these. I will update this thread as soon as I do so. However, this thread can be used exactly towards the direction you say, meaning that executables made with different compilers behave differently. On the other hand, regarding the tests made on my Ubuntu system, I used gcc version 4.0.2 (I believe the same one as yours) which indicates that if I am not missing something basic, running times are bad if someone uses a 64bit processor on a 32bit OS. 
> Next, there are some rows where the execution time is  0.000 msecs. This should immediately ring the warning bells in your head. Something is clearly wrong here. This could indicate that the compiler has done something funky with your code. Or that your dataset isn't large enough to provide any meaningful result.
The fact that some experiments have running time 0.000msecs is easily justified. I simply didn't handle correct the output said:**
> Lastly, the compiler flags used. GCC is instructed to compile at -O3, but you do not specify the processor architecture. Is this wise? Perhaps you should try specifying the kind of CPU architecture used to see if this helps GCC.
Perhaps this is exactly what I 've been missing! Thank you for your reference on that one. I 'll go check out the documentation and try again the data-sets. However, if you know which particular directives apply to my machine or you can give me a more direct reference I will deeply appreciate it! :)

> I compiled them using the standard GCC that ships with Ubuntu, and my compiler flags were "-O3 -march=pentium3 -fomit-frame-pointer -s -DNDEBUG". Try those on your AMD machine and see what results you get.
You were correct on that one! Here are my running times using a makefile as you proposed:
perm17.in - cubic: 4,120.000 msecs
perm22.in - cubic: 5,790.000 msecs

Now I can't wait and find out which directives apply to my machine exactly! Thank you very much for your feedback. I believe that the above can help some other people as well. :)

---

### Post by dimis on 2006-01-24
[QUOTE=LordHunter317]
There is no overhead, and I don't know what you lead you to believe there is.  Whatever misinformation you have, you need to loose.
Any overhead comes from dealing with 64-bit code, if only due to the nature it's bigger.[/QUOTE]
Aren't the above controversial?

> You can't conclude anything from one test.  The P4 performs better likely due to it's deeper pipeline and larger caches, both of which will improve performance on this sort of code.
Well, I regeret to inform you, but you can conclude *something* from the above tests. Of course it is not something definite, but the above running times indicate that someone should be carefull when working on systems like the one I own.

> It indicates nothing of the sort.  To be blunt, you need to go take a class on basic statistics before you even consider making any more conclusions of this sort.  This is one tiny data point with easy explanations as to its behavior.
Will you also go and take a class on basic complexity - also known as algorithms? When you do so, come back again and tell me if I have to attend a class on basic statistics.

My piece of advice: If you are not in the mood to explain your thoughts perhaps you should not judge things so easily. Look at Viro's short posts where this man enlightened me in a very short and immediate way.

---

### Post by Viro on 2006-01-24
You could try using -march=athlon-xp since you are generating 32 bit executables, and -march=k8 only works on 64 bit executables.

---

### Post by LordHunter317 on 2006-01-24
[QUOTE=dimis]Moreover, you are correct that some data-sets are small. However, running times from cubic algorithm surely suffice to draw some conclusions regarding the performance of someone's machine.[/quote]**No, they're not.**

> Aren't the above controversial?No, they're not.  x86_64 isn't like other architectures, and some select codebases will benefit immensely from being 64-bits without a single change.  Most will not, they will be slightly slower.

> Well, I regeret to inform you, but you can conclude something from the above tests.**No, you cannot:**[list][*]They are not statistically significant.  Hell, we don't even know if they're repeatable[*]They're not fair tests.[/list]The data is invalid.  **When I said you needed to take a stats class, *I meant it.***

> Will you also go and take a class on basic complexity - also known as algorithms? When you do so, come back again and tell me if I have to attend a class on basic statistics.I understand plently about algorithms and fail to see their relevance here.


> My piece of advice: If you are not in the mood to explain your thoughts perhaps you should not judge things so easily.I uhh, shouldn't have to.  **You admitted the test weren't fair, *that should be the end of this discussion.***  You've also made it aparent you have no clue about porting considerations for AMD64, otherwise you would have been able to make potentical conclusions about this behavior.  IOW, you lack any of hte information required to make any inferences.  Any conclusion you draw with your presence knowledge is wrong.

---

### Post by LordHunter317 on 2006-01-24
[QUOTE=Viro]I've just run some of your benchmarks on my machine (P3 1GHz) and there is definitely something wrong with the configuration of your AMD system. For the datasets Perm17.in and Perm22.in, my results are 7720.000 msecs and 10690.000 msecs. Just 1 second slower than your AMD 3000+ machine, which is impossible.[/quote]No, it isn't.

---

### Post by dimis on 2006-01-25
One by one then:
> **LordHunter317]> Originally Posted by dimis
Moreover, you are correct that some data-sets are small. However, running times from cubic algorithm surely suffice to draw some conclusions regarding the performance of someone's machine.**No, they're not.**[/quote]
Your negation referring to what? Aren't some data-sets small or I may not draw conclusions from the testings?

[QUOTE=LordHunter317]No, they're not.  x86_64 isn't like other architectures, and some select codebases will benefit immensely from being 64-bits without a single change.  Most will not, they will be slightly slower.[/quote]
You have to decide. Either there is some overhead on 64bit architectures running on 32bit OSs as you say here and seem to comply with what I said right from the beginning or there isn't as you said on another post:
[QUOTE=LordHunter317]
There is no overhead, and I don't know what you lead you to believe there is.[/quote]
I hope you get it soon that both of us say the same thing here. If my english are misleading I apologize.

[QUOTE=LordHunter317]
> 
Well, I regeret to inform you, but you can conclude something from the above tests.
**No, you cannot:**[list][*]They are not statistically significant.  Hell, we don't even know if they're repeatable[*]They're not fair tests.[/list]The data is invalid.  **When I said you needed to take a stats class, *I meant it.***[/quote]
[list]
[*] All algorithms are deterministic. A simple view to the source code would have reavealed it to you that I don't make a single call to the rand() function. Hence, all tests are repeatable if you can understand what an algorithm means. But even if I did use calls on rand function one would be able to draw conclusions, since most of the times, if you write the code you know the distribution that is behind your algorithms. But I guess one can understand that if he has attended a class on statistics.
[*] Tests are fair. As you pointed out, all tests are repeatable since we deal with deterministic algorithms. Hence, same instructions will go one-by-one on your processor and with the same order you are going to make your system calls to RAM (and of course for this part, motherboard plays a role. But do you know a motherboard that supports both AMD64 and Pentium4?  said:**
> 
I hope you can see now that a class in complexity would be enlightening for you.

[QUOTE=LordHunter317]I understand plently about algorithms and fail to see their relevance here.
Read above.

[QUOTE=LordHunter317]> My piece of advice: If you are not in the mood to explain your thoughts perhaps you should not judge things so easily.
I uhh, shouldn't have to.[/quote]
Exactly, since your posts are not constructive at all.

[QUOTE=LordHunter317]**You admitted the test weren't fair, *that should be the end of this discussion.***  You've also made it aparent you have no clue about porting considerations for AMD64, otherwise you would have been able to make potentical conclusions about this behavior.  IOW, you lack any of hte information required to make any inferences.  Any conclusion you draw with your presence knowledge is wrong.[/QUOTE]
[list]
[*] I never said they are not fair. Read my posts carefully. What I said was that test sets for the linear-time algorithms are not large enough to be very accurate. But as you can understand we can talk about cubic-time algorithm where test-sets are ok since timings are ok compared to 1 / CLOCKS_PER_SEC.
[*] Yes and I should comment out myself to make it clearer to you from my opening post:
> (working about 3 times slower - unless someone knows a trick that I am not aware of)
Now that Viro made me realize my ignorance on that part, I downloaded the latest GCC documentation and have already achieved the following timings for my pc:
[list]
[*] perm17.in - Less than 4 secs.
[*] perm22.in ~ Less than 5.5 secs.
[*] perm30.in ~ Less than 25 secs.
[/list]
using the directives:
```
-O3 -mtune=athlon64 -march=athlon64 -fomit-frame-pointer -s -DNDEBUG
```
Still, these timings are not good enough! Primarily, what bothers me most is why an executable by VS 6.0 (prior .net) was so efficient when I never mentioned anything about my platform (I repeat that I have not installed a single service pack there for exactly this reason).
[/list]

---

### Post by LordHunter317 on 2006-01-25
> **dimis]Your negation referring to what?[/quote]That a single test could ever possibly be valid for drawing performance conclusions.

> You have to decide. Either there is some overhead on 64bit architectures running on 32bit OSsThere isn't.  

>  as you say here and seem to complyThat's not what I said.  Learn to read.  What I said was some codebases see a [bspecifically on x86_64.[/b]  The reason is because x86_64 adds more features to the ISA than just wider GPRs and addressing: it raises the lowest level FP compatability and adds extra registers.  x86_64 is virtually unique in this regard.  But those two changes can cause massive speedups for certain codebases, just like choosing a P4 over a P3 can.

That doesn't translate to "there's overhead running 32-bit code".  There is no penalty for running 32-bit code in either compatability or long mode beyond the fact you can't use the new features.  Well, duh.

> I hope you get it soon that both of us say the same thing here.No, I'm not.  Your inability to comprehend doesn't change the truth of what I'm saying.  Your argument would be helped if you actually took some time to read about the x86_64 ISA, as it's readily apparent you have not.

> All algorithms are deterministic.With respect to input and output, not runtime.  And you suggested I needed to take an algorithms course :rolleyes:

> Hence, all tests are repeatable if you can understand what an algorithm means.No, they're not.  **They're only repeatable if we yield the same runtimes (within margin of error).**   You haven't proven that will be the case, and your testing methodology is so flawed it's hard to believe it would.

> But even if I did use calls on rand function one would be able to draw conclusions, since most of the times, if you write the code you know the distribution that is behind your algorithms.Which has no correlation to runtime necessarily.

> [*] Tests are fair. As you pointed out, all tests are repeatable since we deal with deterministic algorithms.No, they're not fair.  You failed to hold all variables controled but one.  Also, you didn't prove repeatabilty, you only half proved it (and you didnt' really prove it, it's just assumed).

> Hence, same instructions will go one-by-one on your processor and with the same order you are going to make your system calls to RAM (and of course for this part, motherboard plays a role.It plays a very minor role.  In fact, it really plays no role at all on the AMD64 platform besides the fact it contains the physical wiring from RAM to the CPU said:**
>  *On an entirely different test*, you can measure the timing for specific commands.No, you can measure it on this one.

> But again here motherboards do play a role and of course the hardware implementation they have for multiplying.:rolleyes:  Do you even read what you write?  What piece of hardware is ever conceptually used for multiplication on the motherboard?

At this point, I think you need to stop trying to introduce hardware until you read a basic digital logic and micrprocessor architecture book.  It's painfully obvious you understand little about either.
 
> 
I hope you can see now that a class in complexity would be enlightening for you.No, it's apparent you need to take one, as well as several courses in digital hardware.

> Exactly, since your posts are not constructive at all.They're perfectly constructive.  The failings of these test are obvious, and you've admitted to them.  I don't really think I can connect the dots further, unless you want me to suggest a better testing regime.

> [*] I never said they are not fair.Yes, you did.  **You admitted to failing to hold accurate controls on all the variables, that makes the tests unfair**.  We don't know what to attribute to the differences you see. 

> Now that Viro made me realize my ignorance on that part, I downloaded the latest GCC documentation and have already achieved the following timings for my pc:Which makes the tests even less fair.  You must be using the same compiler, same optimizations, etc in order to compare to the published P4 data.  You're not.

---

### Post by dimis on 2006-01-25
[QUOTE=LordHunter317]That a single test could ever possibly be valid for drawing performance conclusions.[/quote]
A single test *can be valid* for drawing performance conclusions. If you want to hear something that might calm you down is that usually a single test can be used so as to get *some* indications.

[QUOTE=LordHunter317]There isn't. [/quote]
Read below.

[QUOTE=LordHunter317]That's not what I said.  Learn to read.[/quote]
Ok, I 'll read once more ...
[QUOTE=LordHunter317]x86_64 isn't like other architectures, and some select codebases will benefit immensely from being 64-bits without a single change. Most **will not, they will be slightly *slower*.**[/quote]

[QUOTE=LordHunter317]Your argument would be helped if you actually took some time to read about the x86_64 ISA, as it's readily apparent you have not.[/quote]
Do you have a good reference?

[QUOTE=LordHunter317]With respect to input and output, not runtime.  And you suggested I needed to take an algorithms course :rolleyes:[/quote]
Ok let's see: You run a program that takes 4 secs (let's say this is the expected value) to complete while on the same machine on a different compiler runs on 3 secs (expected value). Do you know a multitasking-multiprocessing OS that gives coupons of 1 sec (!!!) to processes running in normal mode? Search and you won't find one! That's the reason I started this thread. Because what you are trying to say is unrealistic. 

[QUOTE=LordHunter317]No, they're not.  **They're only repeatable if we yield the same runtimes (within margin of error).**   You haven't proven that will be the case, and your testing methodology is so flawed it's hard to believe it would.[/quote]
My advice: Go back and study more.

[QUOTE=LordHunter317]Which has no correlation to runtime necessarily.[/quote]
On single instances it necessarily correlates ...

[QUOTE=LordHunter317]No, they're not fair.  You failed to hold all variables controled but one.  Also, you didn't prove repeatabilty, you only half proved it (and you didnt' really prove it, it's just assumed).[/quote]
Ok then. Take it as an exercise.

[QUOTE=LordHunter317]No, you can measure it on this one.[/quote]
What you can extract from this test is a system with more unknowns than number of equations. The only thing you can find is the variable that describes the solution set (and that again with distortion since if you want more accuracy you have to repeat your experiments).

[QUOTE=LordHunter317]:rolleyes:  Do you even read what you write?  What piece of hardware is ever conceptually used for multiplication on the motherboard?[/quote]
Obviously you never heard of another method of multiplying apart from the multiplication you learnt from high-school which is not optimal?
Will you ever go and take that class in algorithms? Try to focus more on bit-complexity.

[QUOTE=LordHunter317]At this point, I think you need to stop trying to introduce hardware until you read a basic digital logic and micrprocessor architecture book.  It's painfully obvious you understand little about either.[/quote]
Ok. Probably you learnt statistics recently and you are proud of yourself. Congrats. That doesn't mean you know everything yet. As far as I am concerned, it's painful and time-consuming to explain matters to someone who doesn't know much for some other things apart from statistics, yet he's totally convinced that he is right with his limited observations. And it seems that someone should give an end to this "conversation". Is this going to be me or you?
 
[QUOTE=LordHunter317]Which makes the tests even less fair.  You must be using the same compiler, same optimizations, etc in order to compare to the published P4 data.  You're not.[/QUOTE]
Read again the title of the thread and my initial post. (Also note Viro's surprise on my running times.)

---

### Post by LordHunter317 on 2006-01-25
> **dimis]A single test *can be valid* for drawing performance conclusions.[/quote]No, it cannot.  Runtime is non-deterministic said:**
>  If you want to hear something that might calm you down is that usually a single test can be used so as to get *some* indications.No, it can't be used for crap.  Ever.  You need to run it at least once **and throw the data out** to deal with operating system caching issues alone (assuming your data is cacheable in system RAM, and it is in this case).

> Do you have a good reference?The relevant CPU articles on Ars Technica, and the offical Programmer references from AMD would be good starts.  The Wikipedia article was reviewed reasonably recently by someone I personally trust, and it covers the fundamental differences between IA-32 and x86_64 w.r.t. performance and porting considerations.

> Ok let's see: You run a program that takes 4 secs (let's say this is the expected value) to complete while on the same machine on a different compiler runs on 3 secs (expected value).Which is relevant how?  This doesn't prove determinism of runtime, which is what your argument was based on.   Runtime isn't deterministic.  You won't get the same runtime consistently for running the same program with the same inputs.  Even if you removed all the software considerations, modern superscalar processors doing branch prediction don't necessarily do it deterministically. 

> Do you know a multitasking-multiprocessing OS that gives coupons of 1 sec (!!!) to processes running in normal mode?No, but how is this relevant?

> Because what you are trying to say is unrealistic. It's hardly unrealistic.  It's trivally easy to prove.  Run  the program multiple times.  Do you get the same runtime?  No, therefore runtime is not deterministic.  QED.

> On single instances it necessarily correlates ...No, it doesn't.  There are other software and hardware factors to consider.  Just knowing the behavior of the algorithm is insuffcient.  Runtime is not a fuction of solely the algorithm you run and its inputs on a modern processor and operating system.    You can reduce the other portions to noise, but you haven't demonstrated that you have done so thus far.  

> Ok then. Take it as an exercise.No, because the onus is on you to provide proof of your claims.  You can either prove, or g oback.

> What you can extract from this test is a system with more unknowns than number of equations.**Only because *your testing methodology is flawed.*** 

> Obviously you never heard of another method of multiplying apart from the multiplication you learnt from high-school which is not optimal?Complete non-sequitur.  **What part of the motherboard does multiplication?**  Answer:  The CPU.  ***Nothing* on the motherboard is responsible for multiplication** beyond the same components the CPU always relies on.  **And if they are broken, the *whole CPU will not work.***

Your original statement made absolutely no sense.  Your response makes even less sense.  You were wrong, plain and simple, or being delibrately obtuse on purpose.

> Ok. Probably you learnt statistics recently and you are proud of yourself. Congrats. That doesn't mean you know everything yet.Wonderful, but this is a personal attack and non-sequitur.  And my last stats course was over a year ago at this point (praise God).

The point still remains: your data is invalid.

> As far as I am concerned, it's painful and time-consuming to explain matters to someone who doesn't know much for some other things apart from statistics,I've demonstrated a clear grasp of teh architectural issues and hardware design issues you clearly haven't considered as possible.  You assumed the issue was "32-bits vs. 64-bits" when the reality is that in general, 64-bit code runs slower than 32-bit code, if for the only reason that it's bigger.  Your specific code base is a special exception case on AMD64.   If you did this on say PPC32 vs PPC64, I suspect you would have gotten drastically different results, because you wouldn't be able to leverage the ISA extensions AMD64 brings.


> yet he's totally convinced that he is right with his limited observations.You're the one providing the observations, and I'm been pretting consistent in saying, "We really can't tell a thing, we don't have enough data." 

> Read again the title of the thread and my initial post. (Also note Viro's surprise on my running times.)There's no suprise there.   When you can fit it inside L2 cache, things are fast.

---

