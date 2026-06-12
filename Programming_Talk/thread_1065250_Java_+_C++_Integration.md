---
title: "Java + C++ Integration"
date: 2009-02-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-02-09
About a week ago I started a Java vs. C++ thread.  Since then, I have coded up two simple test and indeed, found the Java code to run significantly faster than C++.  Most of the execution was spent in library calls so I cannot claim that C++ is more efficient...just more efficient in this case.  In any case, how hard would it be to integrate the C++ library via a C++ interface and have the rest of the project coded in Java?  This would allow me to use my preferred Eclipse IDE and still have speed where it matters.  I googled and found references to JNI, but everything on C++ and Java integration that I found was dated before 1999.  Can this no longer be done or is it no longer done for performance reasons -- the interface being so slow that all performance gains obtained from C++ are lost in the interface translation / loading?

---

### Post by eye208 on 2009-02-09
> **SNYP40A1 said:**
> Since then, I have coded up two simple test and indeed, found the Java code to run significantly faster than C++.
I find that hard to believe. Will you show us the test programs?

---

### Post by kavon89 on 2009-02-09
> **SNYP40A1 said:**
> found the Java code to run significantly faster than C++.

Indeed, like the guy above me... show us the code. Significantly faster than C++ sounds like a problem with your code. I can see Java consistently edging out C++ in certain situations, but not with a very wide margin.

---

### Post by SNYP40A1 on 2009-02-09
> **kavon89 said:**
> Indeed, like the guy above me... show us the code. Significantly faster than C++ sounds like a problem with your code. I can see Java consistently edging out C++ in certain situations, but not with a very wide margin.

I am using the open-source technical analysis library and I developed code in Java and C++ which makes library calls in a loop in order to simulate a genetic algorithm.  However, the order of library function calls and parameters are exactly the same (although the interface between C++ and Java is a little different).  Here's my original post:

<<<<<<<<<<<<<<<

I went ahead and made a 2 simple identical programs in C++ and Java consisting of about 35-40 indicators found in talib.  I used the SVN checkout taken today for the Java code (Java code base 0.4 has bugs), but I substituted in the ta_lib header and library (.dll, multithreaded, no debug -- cdr environment) found in the base 0.4.0 build because I assumed it was built with the Intel Compiler and I can't install the Intel Compiler since I am using Visual Studio Express 2008.  I was using the Java Environment SE 6.0, all ta-lib Java sources compiled through Eclipse 3.4. 

System is Core2Duo E6700 w/ 1 GB ram, Win XP Pro, Virus Scanner disabled, no other programs other than system processes running in background.

Source code is attached for both C++ and Java.  Functions called and parameters are identical.  I used the abstract library following the CoreMetaTest examples.  Java code looks long and ugly, but it's really just copy / paste about 40 times.   It's a bit sloppy, but I think efficient, correct me if I am wrong, I want this to be a fair comparison.  Before running in loop, I printed the first 100 samples of each output to a text file and compared the output which matched.  You can verify this yourself by enabling the print option and setting the loop count to 1.  Both programs use the attached data.csv file.  I only start the clock after the data file is scanned into memory.  Here are the runtimes that I found:

C++:

25844 ms
25812 ms
25859 ms
25875 ms

Java:

40485 ms
40469 ms
40437 ms
40453 ms
40438 ms

On the last run, I ran with Windows clock open to make sure the test time was reported accurately to ~ nearest 2 seconds.

So this confirms what I expected, C++ appears to be significantly faster than Java.  Too bad, I prefer developing in Java, but I might need speed later if I start experimenting with genetic algorithms.  Although the abstract interface really does make things easier.  Nice work!

Again, if anyone is interested in this, please review my Java source code posted and let me know if I am doing anything too horribly inefficient.  As I said, I want this to be a fair test.
<<<<<<<<<<<<<

I originally posted here:

[http://www.tadoc.org/forum/index.php?topic=812.0](http://www.tadoc.org/forum/index.php?topic=812.0)

Library - Project: TA Lib, came from source forge SVN:

[http://sourceforge.net/svn/?group_id=8903](http://sourceforge.net/svn/?group_id=8903)

#include "stdafx.h" in my CPP file is a Visual Studio 2008 header, you can delete it.

The code that I attached should not be taking much time to execute, most of the time will be taken by the library calls.  All source is included in the link above.  To refer to the original thread, go here (you will need to register):

[http://www.tadoc.org/forum/index.php?topic=812.0](http://www.tadoc.org/forum/index.php?topic=812.0)

You might not consider less than a 2x difference to be "significant", but in a genetic algorithm application, it probably matters.  Since GAs are easy to parallize, the ease of development in Java vs. C++ might justify the efficiency cost, but a better compromise would be to leave the library in C++ and have the rest of my code in Java.

---

### Post by michael_1234 on 2009-02-09
> So this confirms what I expected, C++ appears to be significantly faster than Java.

ooohhh.... I'm not sure where to start....  Perhaps I'll start with the fact that I've seen this type of reasoning (from former students, in newsgroups, in cubicles, in the subway...) way, way too many times since I started using -- then teaching -- Java, after already having used/taught C++, way back 10+ years ago (...I was in the corporate setting, where "adult" learners are very, very suspicious of anything new & different).

I really don't mean to sound harsh, so I'll temper my criticisms with kindness.  What you have is a "microbenchmark", which (here comes the harsh part) is pretty much useless, and reveals only that you don't know terribly much about how the JVM works.  (Sorry... please take these criticisms as constructive).  

But ... (here's the "kind" part), no worries, mate: you're in really good company. Practically no one knows how the JVM "works".   

Here's the bad news: language comparisions are a mine field.  By the time I finish writing this, there'll probably be a zillion posts. (Well, this isn't usenet, so I might be ok.)

Ok:  So, if nothing else, please just take this little nugget of information & mull it over: A Java application is compiled into "bytecode", which, depending on how often the same code is executed (at runtime), will be compiled into native code.  That is, the compiled Java bytecode will -- under the right circumstances -- be compiled into native binary code, just like your C++ program.  In this respect, after running long enough, could you not imagine that you would have both programs performing approximately equally?  

That's very much a lay interpretation of the situation that I used to use to allay the FUD that "java is slow, just code it in C/C++ to begin with".  For the real scoop, look into this for more info (quite interesting... with a lot of (liquid) Java at hand): [http://wikis.sun.com/display/HotSpotInternals/MicroBenchmarks](http://wikis.sun.com/display/HotSpotInternals/MicroBenchmarks)

On a closing note: I would recommend implementing the whole thing in Java, taking advantage of the wealth of API's with pre-existing near-optimimal implementations.  Then, only after profiling (quite easy to do in pure Java -- see the Netbeans profiler), look to optimize the pure-Java code; if there's a particular method that can't be tuned in pure Java, then implement that method in C++ via JNI.  Allow the interface between C++/Java to be clean to allow the Java implementation to be used if there is no native implementation available (eg, strategy design pattern).  Also, I've seen drastically different performance on different OS's and hardware (Sun vs. Windows vs. Linux...), both for C and Java, so you'll want to profile on your desired target platform(s).

Good luck & best wishes,
-m

---

### Post by SNYP40A1 on 2009-02-09
Michael,
I do know a little about the JVM which is why I started at 100 cycles.  Yes, the gap between java and C++ was larger at 100 cycles and the gap closed (talking about percentage - the ratio of runtimes, not actual difference in runtimes) a bit by 1000 cycles.  However, the proportion in runtime stopped there.  There was no difference in the ratio of runtimes (Java runtime / C++ runtime) between 1000 cycles and 10000 cycles.  At that point, the JVM did all it could as far as optimizations are concerned, but it was not enough.  And since the exact same function calls and parameters are executed on every iteration of the loop, I think this benchmark represents the best case aside from re-writing the ta lib library which is something I don't want to do at this point if I can avoid it.  I know that Java is compiled into bytecode and that the virtual machine can perform optimizations during runtime that a compile-time language like C++ cannot.  However, I think my test does serve to illustrate that the benefits of this are not enough in this particular context.  This might be a micro benchmark, but for my application, on this particular project, it's the only benchmark that matters.  I mentioned that I created the Java vs. C++ thread about a week ago.  My bias is towards Java and particularly the Eclipse Platform.  I would much rather just do the entire project in Java.  But at this point, my best bet might be to use the JNI interface and leave the more computationally heavy part in C++, if that's possible.  Note though that the project was started in C++ and the Java code was at least partially auto-generated.  Obviously, the author has more of an interest in optimizing the C++ code than the Java code.

Again, I don't care about Java vs. C++ in the general case.  If you do care, go back to the more general thread that I started least week and post there.  Thanks for your input, I'll look into JNI.

---

### Post by michael_1234 on 2009-02-10
*> I do know a little about the JVM which is why I started at 100 cycles.*

Ok, thanks for being patient with me.  Didn't mean to come off so strong.  ...I didn't see the other thread, so I'll post one last follow-up here.  (Then, I've got to get back to work.  This is my once-a-week diversion.)

As far as JNI is concerned, you're right, there are no real current references, but people still do it (I do it in my job currently... quite a bit). The 1999 Sun JNI spec is still really just as valid today as it was then ( [http://java.sun.com/docs/books/jni/](http://java.sun.com/docs/books/jni/) ).  The only real changes came with Java NIO at Java 1.4, for which there are very few references wrt JNI (in a nutshell: it introduced allocation of memory via direct byte buffers, into which java could directly write, for passing data between C and Java).  ...And these won't necessarily give you better performance (results tend to vary). The tricky part is actually using/understanding NIO, should you choose to use it (it's totally optional). See also:
 [http://java.sun.com/j2se/1.5.0/docs/guide/jni/spec/jniTOC.html](http://java.sun.com/j2se/1.5.0/docs/guide/jni/spec/jniTOC.html) 
[http://java.sun.com/j2se/1.4.2/docs/guide/jni/index.html](http://java.sun.com/j2se/1.4.2/docs/guide/jni/index.html)

As mentioned, I do a fair amount of JNI coding, and a LOT of profiling on my pure-Java code (in my day-job, I'm doing high-performance messaging & data transformation, where faster == better).... you do discover quite a bit when profiling (but you know this).  In the case of Java, little things like putting a variable outside (yes, outside) of a "for.." loop will prevent the JVM from doing smart optimizations for your temp variables. The real killer in your sample Java program (and as I have found in mine) have always been string formatting & I/O, though. Get rid of any number to string conversions (and vice-versa) and get rid of System.out.println inside your timed test.  The "C" program may also be reporting at the same intervals to stdout, but that in itself may be just plain slower in Java (and is not what the "real" program is doing -- eg., testing the wrong thing).  Use System.nanoTime for calculating time deltas.  

*> if you do care, go back to the more general thread that I started least week and post there.*

Sorry for not seeing that thread.  That's ok, I'm just burning a few cycles end-of-day for a little change of pace before another run of coding.  Time to get back to it......

Again, my apologies for not looking more deeply into the code; I did try to compile it (even checked-out the code for missing dependencies), so I don't mean to seem like I'm trolling (though... it's kind of what I'm doing...)

Best of luck,
-m

---

### Post by SNYP40A1 on 2009-02-10
> **michael_1234 said:**
> *> I do know a little about the JVM which is why I started at 100 cycles.*

Ok, thanks for being patient with me.  Didn't mean to come off so strong.  ...I didn't see the other thread, so I'll post one last follow-up here.  (Then, I've got to get back to work.  This is my once-a-week diversion.)

As far as JNI is concerned, you're right, there are no real current references, but people still do it (I do it in my job currently... quite a bit). The 1999 Sun JNI spec is still really just as valid today as it was then ( [http://java.sun.com/docs/books/jni/](http://java.sun.com/docs/books/jni/) ).  The only real changes came with Java NIO at Java 1.4, for which there are very few references wrt JNI (in a nutshell: it introduced allocation of memory via direct byte buffers, into which java could directly write, for passing data between C and Java).  ...And these won't necessarily give you better performance (results tend to vary). The tricky part is actually using/understanding NIO, should you choose to use it (it's totally optional). See also:
 [http://java.sun.com/j2se/1.5.0/docs/guide/jni/spec/jniTOC.html](http://java.sun.com/j2se/1.5.0/docs/guide/jni/spec/jniTOC.html) 
[http://java.sun.com/j2se/1.4.2/docs/guide/jni/index.html](http://java.sun.com/j2se/1.4.2/docs/guide/jni/index.html)

As mentioned, I do a fair amount of JNI coding, and a LOT of profiling on my pure-Java code (in my day-job, I'm doing high-performance messaging & data transformation, where faster == better).... you do discover quite a bit when profiling (but you know this).  In the case of Java, little things like putting a variable outside (yes, outside) of a "for.." loop will prevent the JVM from doing smart optimizations for your temp variables. The real killer in your sample Java program (and as I have found in mine) have always been string formatting & I/O, though. Get rid of any number to string conversions (and vice-versa) and get rid of System.out.println inside your timed test.  The "C" program may also be reporting at the same intervals to stdout, but that in itself may be just plain slower in Java (and is not what the "real" program is doing -- eg., testing the wrong thing).  Use System.nanoTime for calculating time deltas.  

*> if you do care, go back to the more general thread that I started least week and post there.*

Sorry for not seeing that thread.  That's ok, I'm just burning a few cycles end-of-day for a little change of pace before another run of coding.  Time to get back to it......

Again, my apologies for not looking more deeply into the code; I did try to compile it (even checked-out the code for missing dependencies), so I don't mean to seem like I'm trolling (though... it's kind of what I'm doing...)

Best of luck,
-m

No problem, I appreciate all the advice I can get.  There's a variable in both the C++ and Java code called PRINT or something like that.  It's #define in C++ and a boolean in Java.  When running for timing, I set print to false so that the only thing that gets printed is the time at the end.  

Interesting note about about the variables in for loops.  It makes sense that these are areas for optimization.  

So if I were to take the attached C++ file and modify it slightly to become an object to be used through JNI, could I expect the overall performance of the Java program which would then just be a wrapper around the C++ library to be about as fast as if I were just running the C++ program directly?  In clearer words, is there much of a performance penalty for using JNI?  I assume JNI basically just builds a sandbox around the c code.

---

### Post by SNYP40A1 on 2009-02-10
I installed an execution time profiler for Eclipse and ran it on the Java program.  Without going into too much detail, it appears that too much time is spent on executing methods in the abstract layer (which retrieve information for each function).  In reality, this would only need to be done once per function, not on every loop.  In fact, only about 25% of the program execution time is spent calculating the important result.  However, the same case applies for the C++ program, but the abstract layer is different and likely more efficient for the C++ case.  The abstract or meta layer was not really optimized, nor should it be, it's not needed to be called as often as I used it.  I will consider calling the functions directly in order to see how much time is saved.  I wish I had an execution profiler for C++.

---

### Post by eye208 on 2009-02-10
> **michael_1234 said:**
> Ok:  So, if nothing else, please just take this little nugget of information & mull it over: A Java application is compiled into "bytecode", which, depending on how often the same code is executed (at runtime), will be compiled into native code.  That is, the compiled Java bytecode will -- under the right circumstances -- be compiled into native binary code, just like your C++ program.  In this respect, after running long enough, could you not imagine that you would have both programs performing approximately equally?
No.

The JIT compiler is pretty good, but it doesn't turn Java into C++. You still have a garbage collector running in the background. To get an idea of its impact on performance, consider the following test program:
```
final class Node {
        private Node next = null;
        public void append(Node node) {
                if (next == null)
                        next = node;
                else
                        next.append(node);
        }
        public static void main(String args[]) {
                for (int n = 0; n < 10000; n++) {
                        Node node = new Node();
                        for (int i = 0; i < 1000; i++)
                                node.append(new Node());
                }
                System.out.println("Done.");
        }
}
```
Note that the class is declared final to maximize the effects of JIT compilation. There are no library calls except for the final message to stdout. The program just allocates a linked list of 1000 nodes, then discards it. This is repeated 10000 times.

Here is the same program in C++:
```
#include <iostream>

using namespace std;

class Node {
private:
        Node *next;
public:
        Node() {
                next = NULL;
        }
        ~Node() {
                if (next != NULL)
                        delete next;
        }
        void append(Node *node) {
                if (next == NULL)
                        next = node;
                else
                        next->append(node);
        }
};

int main() {
        for (int n = 0; n < 10000; n++) {
                Node *node = new Node;
                for (int i = 0; i < 1000; i++)
                        node->append(new Node);
                delete node;
        }
        cout << "Done." << endl;
        return 0;
}
```
Compile and run the programs like this:
```
javac Node.java
g++ -o node -s -O3 node.cc

time java Node
time ./node
```

---

### Post by CptPicard on 2009-02-10
There was a thread a while back where we tested Java vs. C++ with a an example pulled from my real-life code (look it up on my profile in my "threads started by...) if you're interested. In that thread, Cracauer finally pulled quite an impressive C++ implementation, although his hashing scheme can be further implemented in Java (and in some earlier version of my tools, has been...)

That sort of relatively small constant factor difference is what I usually see in Java vs. C++ in general, and I consider it acceptable most of the time... algorithmic improvements first, local optimizations second, switching languages last. Especially in data analysis such as using TA with genetic algorithms against data series (which I have been doing as well btw), you do want the flexibility you get by having your algorithms run somewhat slower or so. Besides, it's much easier to use multiple cores from Java, and this linear improvement trounces your constant loss...

And that latter kind of garbage-collector-abuse is exactly the sort of pathological Java any half-competent Java coder knows to avoid. In any decent Java code GC overhead tends to be negligible -- in general the significant Java vs. C++ speed difference does not come from garbage collector.

---

### Post by eye208 on 2009-02-10
OK, the obligatory CptPicard post.

Don't get me wrong, I like Java, but this ...
> **CptPicard said:**
> Besides, it's much easier to use multiple cores from Java, and this linear improvement trounces your constant loss...
... is nonsense.

> And that latter kind of garbage-collector-abuse is exactly the sort of pathological Java any half-competent Java coder knows to avoid.
OK, here's an exercise for you: Read some XML or HTML document into memory. What do you get? Yup, an object tree. It doesn't matter if you use the library functions or homegrown ones. But hey, no one does this kind of stuff, right? Office documents in ODF or OOXML format? SVG drawings? 3D meshes in Collada format? NPCs in a game? No sir, we don't do these "pathological" things. Our memory management method sucks, so we just avoid managing our memory.

I have no idea why I even reply to your posts. It's a waste of time.

---

### Post by CptPicard on 2009-02-10
> **eye208 said:**
> 
Don't get me wrong, I like Java, but this ...

Actually, this does not have much to do with particularly "liking" Java, although it is a convenient middle of the road tool for a lot of things.

> 
... is nonsense.

Why?

I find Java's handling of threading quite convenient (in particular the way it fits in with the rest of the language), and the new concurrency package is making it better, although there are some design issues in the API I would have liked to have been handled differently -- I find myself having to hack around them more often than I would like.

Java's object monitor system was, back in the day, a big step forward -- and debugging multithreading issues in Java has always been, if not pleasant, but quite doable.

It really is remarkable how you are capable of trolling me into actually responding at length by just producing content-free denounciations. You're skilled, I give you that.

> No sir, we don't do these "pathological" things.

Avoiding unnecessary cycles of allocation/deallocation is a good strategy anywhere -- even in non-GC languages where you don't need to separately recognize first the parts of your heap that you can deallocate.

I don't know how you do things in your company -- perhaps you indeed do go out of your way to spam garbage objects around -- but my Java specifically seeks to avoid that. And the garbage that ends up being produced, is usually quite neatly handled by the GC. Especially in benchmarks where computation is a substantial part of runtime, like in most of the stuff I do, GC runtimes really are not the big issue *unless* there is something there like what you did in the example -- newing garbage in tight loop. And that can and should usually be designed away.

> 
 Our memory management method sucks, so we just avoid managing our memory.

Which is in a lot of architectures a good solution. A GC (and automatic resource management schemes in particular) are a method that works nicely together with smalltalk-like OOP languages where objects are hopefully rather independent and shouldn't care all that much about each others' lifecycle (esp. not have to track it), and just send messages to each other... consider even asynchronous messaging schemes.

A GC is a tool, to be used with understanding. For example I have run multithreaded graph algorithms on a multi-gigabyte graph (clique discovery, local alternations to the graph's structure, path discovery...)... tracking the nodes so that there are no leaks over the algorithms' runtime (hours) without GC would have complicated the whole thing a lot. With smart management of allocated objects, percentage of time spent in GC was not an issue.

> I have no idea why I even reply to your posts. It's a waste of time.

By all means, don't -- there is always the ignore button. I mostly stopped reading yours a while ago, although this was specifically technical, so I did.

Anyway, I'm putting you on my ignore as I do not feel like I am gaining anything from our communications. Have a Nice Life :)

---

### Post by ajackson on 2009-02-10
> **eye208 said:**
> OK, the obligatory CptPicard post.
As opposed to the mandatory "I know every" post by eye208.

> I have no idea why I even reply to your posts. It's a waste of time.
Because you are a troll and you can't help showing your "superior" knowledge to the rest of us?

Back on topic.

Garbage collection doesn't necessarily mean that you shouldn't do some tidying of your own, even if that "some" is forcing the GC to run at a particular time. Java programs are a bit of a memory hog but the programmer can help reduce the amount of memory used and the speed at which it is released.

You can write programs in all languages that just gobble memory, GC just helps combat some of the wastage but isn't a fix all for efficient memory management.

---

### Post by eye208 on 2009-02-10
Ah, now the spokesperson is taking over.

Look, my benchmark was supposed to show why Java programs *doing the same things as C++ programs* usually end up slightly slower. I am not bashing Java at all. I am just dismissing some myths. If a C++ program actually ends up slower than a Java program, it's because the C++ programmer didn't know his stuff. Whatever optimization you apply to the Java code can be applied to the C++ code as well. Whatever you do, the speed difference will not go away. This is the price to be paid for automatic memory management, array bounds checking etc. You can't defeat the laws of physics.

---

### Post by ajackson on 2009-02-10
> **eye208 said:**
> Ah, now the spokesperson is taking over.
I keep forgetting to ask, what type of bridge do you live under?

> Look, my benchmark was supposed to show why Java programs *doing the same things as C++ programs* usually end up slightly slower.
I'm sure I once posted about speed being a relative thing, you seem fixated on running speed and running speed alone.

> I am just dismissing some myths.
Funny I thought you were giving your opinion, the same as other posters have done, I've not seen any myths debunked.

> If a C++ program actually ends up slower than a Java program, it's because the C++ programmer didn't know his stuff.
Very simplistic way of looking at it, if one program is slower than the other blame the programmer. If everything was based purely on running speed why would anyone use a slower language? Oh that's right running speed **isn't** the only contributing factor in finding a suitable tool for the job.

> This is the price to be paid for automatic memory management, array bounds checking etc.
There are quite a lot of situations where that extra level of processing is useful. Just as there are situations where that extra processing is not needed, it's all about choosing the right tool for the right job but then, what was it, oh yes "market research have shown that a certain language is the best choice for most projects", yet your employer doesn't seem to share that view if I remember right.

Final OT note: Pure running speed is often not the best measure of an applications quality, certainly where GUIs are involved as the human on the other side of the screen tends to slow things down and probably wouldn't notce an extra second here or there but they would notice their PC grinding to a halt because a badly coded app has eaten all it's memory.

---

### Post by michael_1234 on 2009-02-10
I feel somewhat to blame for starting this (or at least fueling it). I threw out an overly simplistic analogy about JIT and all heck broke loose.  I'll take the blame for that.  You'll have to trust me that I knew it was oversimplified.  It (performance & software development in general) is a technically complex topic that can't be addressed with generalities.

I think everyone can agree that these types of threads are not uncommon, and often only minimally instructive for the original poster (that's not to say they aren't entertaining for some of those involved).

And, I think that given an actual project, all parties involved could implement multiple solutions (in C, C++ and Java & various combinations thereof), some with good performance, some with poor.  Regardless, we'd all profile the application and improve where necessary.  Hopefully we designed to allow pluggable implementations in the key areas of interest.  Implementation XYZ would be initially fastest, and maybe it would be simple to maintain & enhance, maybe not. Often the slower, cleaner implementation (read: OO) is easer to optimize without obfuscating the original design.

Regardless, the only conclusion I really can come to is this:   I really shouldn't be posting here while at work. :-)

Peace,
-m

---

### Post by SNYP40A1 on 2009-02-11
I went back and replaced all the indirect calls in my Java program with direct calls, but that only saved about 1.2 seconds (out of 40) of time.  I misinterpreted the execution timing.  I am still going to stick with Java for now as I really do prefer the Java + Eclipse development environment and easier threading.  If I need speed I will look into JNI later.

---

### Post by Kilon on 2009-02-11
> **SNYP40A1 said:**
> I went back and replaced all the indirect calls in my Java program with direct calls, but that only saved about 1.2 seconds (out of 40) of time.  I misinterpreted the execution timing.  I am still going to stick with Java for now as I really do prefer the Java + Eclipse development environment and easier threading.  If I need speed I will look into JNI later.


Bottom line is that benchmarks have limited usage. They can only show you how the language performs under specific situations. Also what I do not like about benchmarks is that they assume that 

1) you are an excellent programmer, pretty unrealistic

2) you have time to test and try optimisations, pretty unrealistic again 

3) that you will be willing to optimise your code but make it look ugly and difficult for other people to understand just to make it abit faster, pretty unrealistic yet again. 

I have read benchmarks for example that showing Jython 300X times slower than java. I did a simple test with calling java functions from jython (pretty much what the average jython programmer would do most of the time) and found out that it was actually 3x time slower. Later I found out that the test did require that the whole code implement only jython code with no java calls, a pretty unrealistic scenario. 

I think the best answer you can find is to actually use the programming langauge and see how it goes. Speed like any other problems can be solved in several ways and it should NOT be a deciding factor for choosing a language. In the end , speed will be the least of your problems. ;)

---

### Post by eye208 on 2009-02-11
> **CptPicard said:**
> it's much easier to use multiple cores from Java

> **SNYP40A1 said:**
> easier threading
Let's bust another myth, shall we?

Threading in Java:
```
class Demo extends Thread {
	public void run() {
		try {
			while (!isInterrupted()) {
				System.out.println("Hello World!");
				sleep(1000);
			}
		} catch (Exception ex) {}
	}
	public static void main(String args[]) {
		try {
			Thread t = new Demo();
			t.start();
			System.in.read();
			t.interrupt();
		} catch (Exception ex) {}
	}
}
```

The same thing in C++:
```
#include <iostream>
#include <boost/thread.hpp>
using namespace std;
using namespace boost;

class Demo {
public:
	void operator()() {
		while (true) {
			cout << "Hello World!" << endl;
			this_thread::sleep(posix_time::milliseconds(1000));
		}
	}
};

int main() {
	Demo d;
	thread t(d);
	cin.get();
	t.interrupt();
	return 0;
}
```

Thread synchronization in Java:
```
class Demo2 {
	public synchronized void doSomeStuff() {
		//
		// do some stuff
		//
	}
	public synchronized void doOtherStuff() {
		//
		// do other stuff
		//
	}
}
```

The same thing in C++:
```
#include <boost/thread.hpp>
using namespace boost;

class Demo2 {
	mutex m;
public:
	void doSomeStuff() {
		lock_guard<mutex> l(m);
		//
		// do some stuff
		//
	}
	void doOtherStuff() {
		lock_guard<mutex> l(m);
		//
		// do other stuff
		//
	}
};
```

---

### Post by ajackson on 2009-02-12
> **eye208 said:**
> Let's bust another myth, shall we?
Unfortunately you have just proven that threading is easier in Java as the threading classes are part of the standard java set up. Your C++ example used a third-party library which takes extra effort (not much I agree) to fetch and install. If threading using just the standard libraries was as easy in C++ as it is in Java you wouldn't need someone else to implement it for you.

I also remember you saying that using third-party libraries was dumbing down, show us how to do it using just the standard libraries after all to compare claims like this there has to be a level playing field.

---

### Post by eye208 on 2009-02-12
What makes the Java thread API more "standard" than the C++ thread API? Java and its libraries have never been standardized in any way.

---

### Post by ajackson on 2009-02-12
> **eye208 said:**
> What makes the Java thread API more "standard" than the C++ thread API?
Because the Java thread class is part of the core fundamental libraries included with Java. Your code was using a third-party library to do the same thing, which is as far from standard as you can get.

> Java and its libraries have never been standardized in any way.
Oh dear. Just because Java doesn't have an ANSI, ECMA or ISO issued standard doesn't mean that Java isn't standardised. Sun dictates what the Java standards are.

---

### Post by eye208 on 2009-02-12
> **ajackson said:**
> Sun dictates what the Java standards are.
The whole point of a standard is to prevent such a situation.

---

### Post by japju on 2009-02-12
> **eye208 said:**
> 

The JIT compiler is pretty good, but it doesn't turn Java into C++. You still have a garbage collector running in the background.

...

Note that the class is declared final to maximize the effects of JIT compilation.

1) I'm afraid that that is another pointless micro-benchmark that would not reflect the behaviour of actual programs. The effect of GC is very difficult to predict, and whether it speeds up or slows down Java program compared to the similar C++ program depends on the size and lifespan mix of your objects. Note that in Java you know that after

```

SomeObject object = new SomeObject();

```

object will be non-null. GC hugely simplifies allocation and deallocation of objects and allows elimination C++ code that is necessary of you care about the correctness of your program. (Of course, you can skip the tests and just pray.... But that is bad style.)

2) As far as HotSpot JVM is concerned, using final will not change the behaviour of the JIT:

[http://java.sun.com/developer/technicalArticles/Networking/HotSpot/inlining.html](http://java.sun.com/developer/technicalArticles/Networking/HotSpot/inlining.html)

On non-HotSpot JVMs, it might or might not..... Note that the Java to byte code compiler can never eliminate methods, even final ones, as the class actually loaded at run time might not be the one that was seen during the compilation!

---

### Post by howlingmadhowie on 2009-02-12
> **eye208 said:**
> The whole point of a standard is to prevent such a situation.

actually if i'm being very picky, the gp isn't quite correct. the java language specification is regulated by the java community process. here's a list of the people on the committee: [clickity]("http://www.jcp.org/en/participation/committee").

i cannot say how much influence sun has on the process, but i imagine it's quite large.

---

### Post by japju on 2009-02-12
> **eye208 said:**
> I am just dismissing some myths. If a C++ program actually ends up slower than a Java program, it's because the C++ programmer didn't know his stuff. Whatever optimization you apply to the Java code can be applied to the C++ code as well. 
Actually, you are quite mistaken:

1) You are actually perpetuating the myths, not addressing myths. It is a myth than given any two programming languages A and B, one is always faster/better than the other.

2) It most definitely is not possible to apply the same optimisations to C++ program than Java. The semantics differences e.g. multiple inheritance guarantees that.

Bad/unsuitable algorithm is just that no matter what the implementation language is.

---

### Post by ajackson on 2009-02-12
> **eye208 said:**
> The whole point of a standard is to prevent such a situation.
Oh dear is that a straw man argument I spy? There are many standards which are de facto standards (like the Java one more or less is), that doesn't stop them being standards or do you still have betamax videos?

Accept that the Java thread class is part of the **core** Java language and the library you used to prove that threading in C++ is as easy as in Java is a third party (thus non-standard) library. I agree when using that library threading is as simple in C++ as in Java but it requires extra effort to find and install the third party library therefore threading is easier in Java than C++.

I know you won't agree, mainly because it is me posting this.

---

### Post by ajackson on 2009-02-12
> **howlingmadhowie said:**
> actually if i'm being very picky, the gp isn't quite correct. the java language specification is regulated by the java community process. here's a list of the people on the committee: [clickity]("http://www.jcp.org/en/participation/committee").

i cannot say how much influence sun has on the process, but i imagine it's quite large.
Thanks for that information (I do miss the thanks button), makes the Java standard slightly more than a de facto standard but still a standard.

---

### Post by eye208 on 2009-02-12
> **japju said:**
> I'm afraid that that is another pointless micro-benchmark that would not reflect the behaviour of actual programs. The effect of GC is very difficult to predict, and whether it speeds up or slows down Java program compared to the similar C++ program depends on the size and lifespan mix of your objects.
If it's true that there are cases in which the GC's effect is to speed up instead of slow down, there must be at least one micro-benchmark to prove it. Show me the code.

> GC hugely simplifies allocation and deallocation of objects and allows elimination C++ code that is necessary of you care about the correctness of your program. (Of course, you can skip the tests and just pray.... But that is bad style.)
Contrary to popular belief, Java can leak memory and resources too. See this article for more detail:

[http://java.sun.com/developer/technicalArticles/javase/finalization/](http://java.sun.com/developer/technicalArticles/javase/finalization/)

The problem is that[list][*]most Java programmers are not aware of this, and[*]there is no workaround because [RAII](http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization) doesn't work in Java.[/list]

---

### Post by CptPicard on 2009-02-12
*Sigh*... so I see eye bit with the "but C++ has the boost thread library!" counterargument I was expecting. Maybe I should start cautiously qualifying everything I say in anticipation of all the ankle-biting.

Interestingly, this *is* a case where "just writing libraries" is doable (as a counter-example, you couldn't get proper higher-order functions and/or lambdas by just writing libraries -- no wonder they are a core concept in programming language theory) -- but fact remains that Java has had threads well-integrated for ages, and there is *nothing* "nonsensical" about stating that threading in Java is rather convenient (esp. when OP is already doing Java, and will benefit from parallelization just as much as my own code does -- turns out we do similar things), regardless of whether C++ guys have managed to follow up with a library later on.

Just stating the remark about C++ threading libraries would have been a much better approach than suggesting that Java's threading "doesn't exist" because of it, and therefore, I'm wrong.

EDIT: Really, read the context. The OP is thinking about Java and C++ and is thinking of doing some sort of weird interfacing (probably bad idea). He will benefit from parallelizing what he's doing. I note that parallelism in Java is easy to do anyway so he needs to consider if language migration is worth it if he can just multithread, which is, uh, easy.

So in barges eye208 and claims that the statement about threading in Java is nonsense... :p 

ajackson, I value your input, but he just wants to disagree as matter of principle and rile you up. I think you're wasting your time.

---

### Post by eye208 on 2009-02-12
> **ajackson said:**
> I know you won't agree, mainly because it is me posting this.
I disagree because you are wrong. C++ is standardized at least to some extent, but Java isn't standardized at all. In fact this was one of the major selling points of Microsoft .NET as a Java competitor. The .NET engine and C# are ECMA/ISO standards. In the Java Community Process, Sun has always had the final word.

By the way, the Boost thread API will be part of the upcoming C++0x standard.

---

### Post by ajackson on 2009-02-12
> **eye208 said:**
> I disagree because you are wrong.
Oh really, how come? Java is standardised, lack of an official stamp from a third party doesn't change that fact.

Taken from the JCP FAQ [http://www.jcp.org/en/introduction/faq](http://www.jcp.org/en/introduction/faq)

[quote=JCP FAQ]Q: What prevents Sun from controlling or dominating the groups that develop and maintain Java specifications?
A: Sun, and the other Executive Committee (EC) members, serve as technology oversight groups for the work of the Expert Groups. The ECs do not micro-manage the day-to-day workings of Expert Groups. Rather, the ECs have the opportunity to review the work of each Expert Group at well-defined points as their specifications proceed through the JCP. The primary function of the ECs is to ensure that specifications do not overlap or conflict with one another and that the specifications meet the needs of the industry segment for which they are being written.[/quote]

Sun work with and as part of JCP to progress Java.

> By the way, the Boost thread API will be part of the upcoming C++0x standard.
**will be part** does not make it standard yet.

---

### Post by eye208 on 2009-02-12
> **CptPicard said:**
> but fact remains that Java has had threads well-integrated for ages, and there is *nothing* "nonsensical" about stating that threading in Java is rather convenient (esp. when OP is already doing Java, and will benefit from parallelization just as much as my own code does -- turns out we do similar things), regardless of whether C++ guys have managed to follow up with a library later on.
Java's threading model, especially its thread synchronization model, is only a subset of what threading is all about. Boost's approach is much more complete. And Java isn't the first to offer a thread class either. However, new is that some Java programmers apparently consider their soviet-style walled ecosystem a benefit rather than a constraint.

---

### Post by ajackson on 2009-02-12
> **eye208 said:**
> And Java isn't the first to offer a thread class either.
Who claimed it was?

> However, new is that some Java programmers apparently consider their soviet-style walled ecosystem a benefit rather than a constraint.
[adopt David Attenborough voice]
and here we see the poor creature, unable to reason correctly but valiantly attempting not to invoke Godwin's law, stumbling and floundering wildly hoping for salvation but knowing that the sun is coming out and he is a long way from his bridge
[/adopt David Attenborough voice]

Nice to see the fall back to the "everyone who disagrees is a fan boy" argument.

---

### Post by nvteighen on 2009-02-12
> **eye208 said:**
> What makes the Java thread API more "standard" than the C++ thread API? Java and its libraries have never been standardized in any way.

Great.

Very simple: do the following experiment. Write a C++ program using Boost and try to compile it without linking to Boost :). It's not part of the language, no matter how common it is. No, printf() in C is not part of the language (oh right, the Std. Lib. is linked automatically)...

So, what's part of a programming language? Yeah, iostream and stdio.h are really so much used that knowing C++ or C, respectively, means to know those I/O routines... and also the Std. Library. But then we're mistaking what a programming language is about: rather than a semantical system, it's a framework to create a semantical system (which is the program)... So, even if a certain routine is really common and "standard", if it's not part of the "framework", but of the results the framework can create. :)

Well, that "framework" can be really more than a framework, and include stuff that actually should be a result not a built-in feature. You may believe Java should not include the threads as part of the language... ok, but you don't design Java :) But the fact is that the threads are there, in the semantic-producing part and not in the semantic-product side.

There's no Java standard... ok, there's no Open Standard, you mean. There is a "de facto" standard that is enforced by Sun's power in the market. If Sun makes a change to Java, everybody will have to adapt his code ;) The same happens with Python and Perl... But, if in some case, the monopolic authority of Van Rossum (Python) or L. Wall (Perl) is challenged by a new implementation, then you can get to the horrible situation Scheme is at: a standard nobody follows (R5RS... now R6RS) and lots of implementations all incompatible (to the point PLT Scheme != MIT/GNU Scheme != MIT Scheme48 != ...). That is an anarchic situation, not Java's (Sun controls both decent implementations: SunJDK and OpenJDK... GNU Java/Classpath doesn't count).

So, there are two "standard" situations: the monopolic "de facto" one and the "de jure" ISO/ANSI standards...

---

### Post by eye208 on 2009-02-13
> **nvteighen said:**
> Write a C++ program using Boost and try to compile it without linking to Boost :). It's not part of the language, no matter how common it is.
Write a Java program and try to run it without a JRE. The JRE is not part of the system, and it's not common at all. If you think installing Boost on the developer's machine is troublesome, installing a JRE must be the mother of all troubles since it is mandatory for both the developer and the user.

> You may believe Java should not include the threads as part of the language... ok, but you don't design Java :) But the fact is that the threads are there, in the semantic-producing part and not in the semantic-product side.
Nonsense. The Java thread and concurrency classes are wrappers around operating system APIs. On Linux, the Java VM links to the POSIX thread library. Which, of course, is not written in Java at all. Using a thread class in Java is no different from using a thread class in C++. The concurrency packages were not even part of Java until version 6. They were added because the built-in thread semantics of Java were not up to snuff. Now Java programmers are dealing with mutex objects and locks just like C++ programmers do. It's not easier at all.

---

### Post by nvteighen on 2009-02-13
> **eye208 said:**
> Write a Java program and try to run it without a JRE. The JRE is not part of the system, and it's not common at all. If you think installing Boost on the developer's machine is troublesome, installing a JRE must be the mother of all troubles since it is mandatory for both the developer and the user.

We're talking about the languages and not about how the languages are interpreted on top of the computer. The fact is that you can't consider Boost being part of C++, while the Java threads are.

> 
Nonsense. The Java thread and concurrency classes are wrappers around operating system APIs. On Linux, the Java VM links to the POSIX thread library. Which, of course, is not written in Java at all. Using a thread class in Java is no different from using a thread class in C++. The concurrency packages were not even part of Java until version 6. They were added because the built-in thread semantics of Java were not up to snuff. Now Java programmers are dealing with mutex objects and locks just like C++ programmers do. It's not easier at all.

Yes, and the conclusion is? Again, nobody should care (except the Java developers, of course) about what Java threads really are. You have to forget everything that lies below the language, so what matters to me is the theorical aspect of what is to be considered "part of" a language and what not. Maybe I'm on the wrong discussion?

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> Write a Java program and try to run it without a JRE. The JRE is not part of the system, and it's not common at all. If you think installing Boost on the developer's machine is troublesome, installing a JRE must be the mother of all troubles since it is mandatory for both the developer and the user.
Write a C++ program that needs a third-party .so and try to run it on a system without that .so, that .so needs to be on both the developers and users machine.

>  On Linux, the Java VM links to the POSIX thread library. Which, of course, is not written in Java at all.
So Java threads have to be discounted because the underlying system library they use wasn't written in Java? OK lets say a C++ library makes use of a function written in C or assembler, does that invalidate it as a library?

> Using a thread class in Java is no different from using a thread class in C++.
You are correct but in Java the thread class is included as part of the core libraries supplied with the JVM, in C++ it is not. That is the difference.

>  The concurrency packages were not even part of Java until version 6. They were added because the built-in thread semantics of Java were not up to snuff.
At least you now agree they are included by default, a poor built-in implementation is still better than no built-in implementation because it is still easier **from a base install** (i.e. no additional library installations) to write a Java threaded program than a C++ threaded program.

> Now Java programmers are dealing with mutex objects and locks just like C++ programmers do. It's not easier at all.
So Java, like most languages, has evolved but the C++ programmer still needs to install a third party library (and get it, and/or the underlying .so it relies on, onto the end-users system).

You said yourself in C++0x threading will be included as part of the core but you also imply concurrency in Java can't be counted because it was added in version 6, can you not see the hypocrisy in those statements?

---

### Post by eye208 on 2009-02-13
> **nvteighen said:**
> The fact is that you can't consider Boost being part of C++
Why not? It has been subject to pretty much the same "community process" as the Java libraries.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> You said yourself in C++0x threading will be included as part of the core but you also imply concurrency in Java can't be counted because it was added in version 6, can you not see the hypocrisy in those statements?
The hypocrisy is on your part. You want the lately added Java libs to be counted, but not the Boost libs.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> The hypocrisy is on your part. You want the lately added Java libs to be counted, but not the Boost libs.
You mean the Java libs that are part of the current Java core? If you install Java or allow Java to update itself you will find that those libs are there. If you install C++ the Boost libs are not. Leave that poor straw man alone.

Java 6 came out 11th December 2006, I wouldn't call that "lately added", those libraries have been in place for over two years, in programming terms two years is a fairly long time period.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> Why not? It has been subject to pretty much the same "community process" as the Java libraries.
It is not part of the **core** C++ system, it is a third party library.

---

### Post by Kilon on 2009-02-13
> **ajackson said:**
> It is not part of the **core** C++ system, it is a third party library.

However someone could build a C++ distribution with the libraries included and ready to be used.

---

### Post by tneva82 on 2009-02-13
> **eye208 said:**
> The hypocrisy is on your part. You want the lately added Java libs to be counted, but not the Boost libs.

Boost hasn't been added to C++ yet however. Java libs have been. That's the difference. When Boost HAS been added then it's different but at the moment it's not part of c++. At the moment it's just 3rd party library.

---

### Post by ajackson on 2009-02-13
> **Kilon said:**
> However someone could build a C++ distribution with the libraries included and ready to be used.
That is true, but it is then still a third party library and you would have to seek out that particular bundle because you couldn't expect your application to compile/work against a bundle that just includes the current standard/core of C++. With Java as long as the current version of the JVM is installed the threading will work.

Edit: For example a membership system I have written uses a SQLite database, so I have had to use a suitable JDBC driver for SQLite. When I want to copy my compiled jar file to the end user I have to make sure that the jar file containing that driver is also copied. If the driver was part of the base JVM set up I would only have to copy my jar file.

---

### Post by Kilon on 2009-02-13
> **ajackson said:**
> That is true, but it is then still a third party library and you would have to seek out that particular bundle because you couldn't expect your application to compile/work against a bundle that just includes the current standard/core of C++. With Java as long as the current version of the JVM is installed the threading will work.

You could pack the app with the libs and thus make it more self efficient than JAVA. 

In Java if the right libs are not include ( or you have a old JRE) then the whole JRE must be installed which a waste of download and time.  

Unless the lib is distributed separately from the JRE.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> It is not part of the **core** C++ system, it is a third party library.
There are only two alternatives:

Java is not a standard because it is controlled by Sun.
-> Java is a third party component.

Java is a standard because it is controlled by a community.
-> Boost is a standard too.

No matter which option you choose, you can't justify treating Java and Boost in different ways.

---

### Post by ajackson on 2009-02-13
> **Kilon said:**
> You could pack the app with the libs and thus make it more self efficient than JAVA.
Again true but also again the third party library needs installing, you just do the additional step in your installer to save the end user having to.

> In Java if the right libs are not include ( or you have a old JRE) then the whole JRE must be installed which a waste of download and time.
Unfortunately that is a problem when libraries and languages evolve, it isn't unique to Java so if you used a newer version of a C++ library *Bob* (yeah I'm awful at coming up with sensible library names) that has a function that is not in the prvious version of that library you would need to update that library.

> Unless the lib is distributed separately from the JRE.
As I said in my edit (which I think you didn't see before your reply), this is a way around the problem but it is still an extra step you have to take, a trivial one but still an extra step.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> There are only two alternatives:

Java is not a standard because it is controlled by Sun.
-> Java is a third party component.

Java is a standard because it is controlled by a community.
-> Boost is a standard too.

No matter which option you choose, you can't justify treating Java and Boost in different ways.
Like I said before leave that poor straw man alone.

Sun does develop Java and is the only developer who does, the Java standard is controlled by a community of which Sun is part of. The libraries for threading are part of the core Java system, thus they are standard.

C++ standard is looked after by ISO, Boost is not in the current version of that ISO standard for C++ but is a widely used third party library which is community driven work.

The current Java standard (version 6) contains thread classes, the current C++ standard does not.

---

### Post by Kilon on 2009-02-13
> **ajackson said:**
> 

Unfortunately that is a problem when libraries and languages evolve, it isn't unique to Java so if you used a newer version of a C++ library *Bob* (yeah I'm awful at coming up with sensible library names) that has a function that is not in the prvious version of that library you would need to update that library.



Would not be cool , if the java could talk to the app and ask it what libs it required and then connect to the internet and download the libs automatically ?

I recently read an article that said that this can be achieved with the JAVA WEB START which is part of JRE, but I do not think the process is automatic . But I might be wrong here.

---

### Post by ajackson on 2009-02-13
> **Kilon said:**
> Would not be cool , if the java could talk to the app and ask it what libs it required and then connect to the internet and download the libs automatically ?

I recently read an article that said that this can be achieved with the JAVA WEB START which is part of JRE, but I do not think the process is automatic . But I might be wrong here.
I know under windows systems (which I have to maintain apps on) Java checks periodically for updates to the JVM, under Ubuntu (not sure about other distros) the end user is reliant on a new version being added to the repository for an auto-update to happen.

But again the same can be said about other languages so it is not unique to Java.

I guess the applications installer (and update facility) would have to do the donkey work of ensuring the correct libs are in place. Makes on-line apps more attractive because all the libs would live on the server so only one place needs maintaining.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> The current Java standard (version 6) contains thread classes, the current C++ standard does not.
The current C++ standard is ISO/IEC 14882:2003.
The current C standard is ISO/IEC 9899:1999.
The current C# standard is ISO/IEC 23270.
The current Pascal standard is ISO/IEC 10206.
The current POSIX standard is ISO/IEC 9945.

The current Java standard is none.

Please stop talking about "Java standards". It makes you look clueless.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> The current Java standard is none.
Nope the current standard is version 6.

> Please stop talking about "Java standards". It makes you look clueless.
As I've said before just because something doesn't have an ISO issues standard does not mean it is not a standard. A lot of things don't have an ISO standard but are still classed as standards so if anyone is looking clueless, it ain't me.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> As I've said before just because something doesn't have an ISO issues standard does not mean it is not a standard.
OK, then Boost is a standard. Thank you for pointing this out.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> OK, then Boost is a standard. Thank you for pointing this out.
Sigh, your argument (which I see you are trying to shift again) was that threading is as easy in C++ as in Java. Boost is not part of standard C++, yet Java's thread class is part of standard Java. Once you install Boost it is as simple **but** you have to install two things rather than one, downloading and installing two things is harder than downloading and installing one.

When C++0x becomes standard if someone said threading is easier in Java than C++ I would tell them that it isn't because it is part of the core system. Your obsession with "what is standard" is quite disconcerting and seems to be just purely a diversionary tactic to avoid admitting that in Java threading is included by default (I won't use the term standard since that would fuel your illogical arguments) but by default in C++ it isn't as it relies on a third party library.

---

### Post by tneva82 on 2009-02-13
> **eye208 said:**
> OK, then Boost is a standard. Thank you for pointing this out.

Is boost installed AUTOMATICLY when you download C++ compiler? If I download your basic run of the mill C++ compiler set can I compile programs which use boost just like that?

If not and I have to download it separatly it's not standard.

Edit: Nope. Can't compile. Whole bunch of errors comes with your example code. And since I didn't install some custom-made c++ compiler package you can rule that out. If it would be standard it would be installed.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> Sigh, your argument (which I see you are trying to shift again) was that threading is as easy in C++ as in Java. Boost is not part of standard C++, yet Java's thread class is part of standard Java. Once you install Boost it is as simple **but** you have to install two things rather than one, downloading and installing two things is harder than downloading and installing one.
I see. Boost is "not easy" because it's a separate download. You have to install "two things rather than one".

Let's look at the downloads for Java 6:

java-common
sun-java6-bin
sun-java6-fonts
sun-java6-plugin
sun-java6-jre
sun-java6-jdk
sun-java6-demo
sun-java6-source
sun-java6-doc
sun-java6-javadb

Wow! Looks like Java is the most "difficult" SDK ever! ;)

What about OpenJDK?

openjdk-6-dbg
openjdk-6-demo
openjdk-6-doc
openjdk-6-jdk
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-lib
openjdk-6-source
openjdk-6-source-files
icedtea6-plugin

Damn! So many downloads. And that's just Java standard 6! Imagine you have to install Java standards 5, 6 and 7 side by side! ;)

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> I see. Boost is "not easy" because it's a separate download. You have to install "two things rather than one".
How did I know you would jump on that.

> Let's look at the downloads for Java 6:

java-common
sun-java6-bin
sun-java6-fonts
sun-java6-plugin
sun-java6-jre
sun-java6-jdk
sun-java6-demo
sun-java6-source
sun-java6-doc
sun-java6-javadb
And how many of those are needed to compile and run your example code? I have java-common, sun-jav6-bin, sun-java6-jdk and sun-java6-jre installed and can run the code.

Of course those packages are how Ubuntu choose to bundle Sun Java version 6, via the Sun Java website you can download just one package (sadly no deb version but this isn't a discussion about how a particular distro packages java).

Have you done a listing to see how many boost packages there are, now I know that you don't need to install them all to compile and run your example code but since you seem to be stating that all those sun-java6 packages need installing I can ask for a level playing field and insist on the same (I make it 27 packages, if you include all the -devs as well and that is without installing C++).

> What about OpenJDK?
What about OpenJDK? That's like saying what about installing Microsofts C++ or Company *X*'s C++ as well as G++.

> Java standard 6!
Which according to you doesn't exist.

> Imagine you have to install Java standards 5, 6 and 7 side by side! ;)
Imagine you have to install the last 3 versions of G++ side by side, you argument is... I don't know what your argument is.

OK we are not talking about how a particular distro packages Java, we are talking about the fact that to compile the two examples of threading code you supplied you need to install just the core of Java but the core and Boost for the C++ code.

Stop trying to divert the discussion or change what we are talking about. Do you agree that to compile your C++ code you would need to install Boost on top of a C++ installation but for the Java code you only need the core Java installation?

No doubt you don't and will come up with some more smoke and mirrors about how with the Java version you need to eat a cucumber covered in peanut butter or some other such nonsense but the fact remains the C++ example needs a third party library to work, the Java example just uses the core libraries.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> How did I know you would jump on that.
Well, I refuted every other argument of yours, so the packaging was the only one left.

Also note that we have only looked at the developer's side so far. To run my Boost-powered threading demo, the user has to install exactly nothing. To run the Java-powered threading demo, the user has to download and install the whole JRE.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> Well, I refuted every other argument of yours, so the packaging was the only one left.
How about the one that this discussion is **actually** about? Implementing a threaded application is easier in Java than C++, remember that one?*****

> Also note that we have only looked at the developer's side so far. To run my Boost-powered threading demo, the user has to install exactly nothing. To run the Java-powered threading demo, the user has to download and install the whole JRE.
What part of implementing is so hard to understand?

***** Disclaimer, this discussion is not about:
- What is a standard
- How distribution *X* bundles its packages
- Boost is part of C++0x
- Java is a third party component
- The price of potatoes in Tesco
- The shipping forecast
- The atomic number of plutonium
- What the latest films on at the cinema are like
- The average rainfall in Rome

---

### Post by nvteighen on 2009-02-13
> **eye208 said:**
> There are only two alternatives:

Java is not a standard because it is controlled by Sun.
-> Java is a third party component.

Java is a standard because it is controlled by a community.
-> Boost is a standard too.

No matter which option you choose, you can't justify treating Java and Boost in different ways.

Great... Windows is not a standard because it is controlled by Microsoft and it's not controlled by a community... it rather controls the community and everyone, no matter what he does, either imitates or deliberatedly avoids what Windows does... Isn't that a standard? Yes, "de facto", but with enough power to drive more than 80% of the market.

> **eye208 said:**
> The current C++ standard is ISO/IEC 14882:2003.
The current C standard is ISO/IEC 9899:1999.
The current C# standard is ISO/IEC 23270.
The current Pascal standard is ISO/IEC 10206.
The current POSIX standard is ISO/IEC 9945.

The current Java standard is none.

Please stop talking about "Java standards". It makes you look clueless.

What part of **"de facto"** standard you don't understand? It's clear: Java is not a **"de jure"** standard like the ones you quote. But Sun has the power to enforce its criteria on the market.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> How about the one that this discussion is **actually** about? Implementing a threaded application is easier in Java than C++, remember that one?
I have already proved that it's just as easy in C++ as it is in Java. I have also demonstrated that C++ is faster than Java. And I provided material to show that garbage collection is no reliable protection against memory and resource leakage. I consider RAII a very elegant way to handle resource (de)allocation, but that's just my opinion.

The only good thing about Java is that it pays my bills. Otherwise I wouldn't touch it with a ten-foot pole.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> I have already proved that it's just as easy in C++ as it is in Java.
By using a third party library. In Java it is part of the core installation.

So can we get back to implementing a threaded application is easier in Java than C++?*****

***** Disclaimer, this discussion is not about:
- Implementing the solution using non-core libraries
- Disliking a particular language
- Disliking a particula forum member
- Using non core libraries and pretending that they are part of the core system
- Memory management
- Memory leakage
- Processing speed
- What is a standard
- How distribution X bundles its packages
- Boost is part of C++0x
- Java is a third party component
- The price of potatoes in Tesco
- The shipping forecast
- The atomic number of plutonium
- What the latest films on at the cinema are like
- The average rainfall in Rome

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> By using a third party library. In Java it is part of the core installation.
OK, let's do it without Boost.
```
#include <iostream>
#include <cc++/thread.h>
using namespace std;
using namespace ost;

class Demo : public Thread {
	void run() {
		while (true) {
			cout << "Hello World!" << endl;
			Thread::sleep(1000);
		}
	}
};

int main() {
	Demo d;
	d.start();
	cin.get();
	return 0;
}
```
This example uses the GNU Common C++ library, a core component of GNU C++.

Checkmate.

---

### Post by ajackson on 2009-02-13
> **eye208 said:**
> This example uses the GNU Common C++ library, a core component of GNU C++.

Very nice, so if I took that code to a compiler other than GNU C++ it would still compile would it?

Since C++ has an ISO standard you can prove to me that this is in fact part of that standard (if it is why are they adding it in C++0x?). The Java thread class is part of the current Java standards.

So can we get back to implementing a threaded application is easier in Java than C++?*****

***** Disclaimer, this discussion is not about:
- Implementing the solution using non-core libraries
- Disliking a particular language
- Disliking a particula forum member
**- Using non core libraries and pretending that they are part of the core system**
- Memory management
- Memory leakage
- Processing speed
- What is a standard
- How distribution X bundles its packages
- Boost is part of C++0x
- Java is a third party component
- The price of potatoes in Tesco
- The shipping forecast
- The atomic number of plutonium
- What the latest films on at the cinema are like
- The average rainfall in Rome

---

### Post by tneva82 on 2009-02-13
> **eye208 said:**
> I have already proved that it's just as easy in C++ as it is in Java. I have also demonstrated that C++ is faster than Java. 

Yes with non-standard libraries. With standard libraries Java beats C++ hands down.

---

### Post by eye208 on 2009-02-13
> **ajackson said:**
> Very nice, so if I took that code to a compiler other than GNU C++ it would still compile would it?

Since C++ has an ISO standard you can prove to me that this is in fact part of that standard (if it is why are they adding it in C++0x?). The Java thread class is part of the current Java standards.
:lolflag:

This discussion reminds me of the Black Knight vs. King Arthur scene in "Monty Python and the Holy Grail". No matter how many arms and legs I cut off, you keep coming back for more. ;)

When I talked about ISO standards, you guys told me that de facto standards matter more than de jure standards. So there, GNU C++ is a de facto standard. Now you are referring to ISO again. Sorry, but your last leg has just been cut off. Implementing a threaded app is easier in C++. Game over! :P

---

### Post by eye208 on 2009-02-13
> **tneva82 said:**
> Yes with non-standard libraries. With standard libraries Java beats C++ hands down.
:lolflag:

This is hilarious...

Keep 'em coming! :popcorn:

---

### Post by scourge on 2009-02-13
> **ajackson said:**
> By using a third party library. In Java it is part of the core installation.

So can we get back to implementing a threaded application is easier in Java than C++?*****

So you want to compare threading in Java to threading in C++, but 3rd party libraries like Boost and POSIX are banned? When the rules of the competition are defined like this, Java wins hands down, since pure ISO C++ doesn't have threads. But what use is this kind of a comparison? Why would anyone care, considering how easy it is to install, link to, and use the Boost libs?

If we go down this road, why not compare the difficulty of writing a GUI application: wow, Java beats just about every programming language ever invented, because it's one of the few that comes with its own GUI package, and the others need 3rd party libs.

---

### Post by nvteighen on 2009-02-13
> **eye208 said:**
> 
When I talked about ISO standards, you guys told me that de facto standards matter more than de jure standards. So there, GNU C++ is a de facto standard. Now you are referring to ISO again. Sorry, but your last leg has just been cut off. Implementing a threaded app is easier in C++. Game over! :P

What? When did someone said that "de facto" standards matter more than "de jure"? No, at least what I said (because I brought up the distinction) was that you can't say Java is not a standard because there is a "de facto" enforcement Sun does over what Java is and what not.

GNU C++ is not a standard. Neither is MS VisualC++. Those are implementations of a certain standard... none of both has control over. And even that, I still argue that that stuff is, standard or not, not the C++ language itself... Where the Java threads, as long as I'm informed, is part of the language (if I'm misinformed and it happens to be a library in Java too... even a standard one, then, I retract myself and the thread class is not part of Java).

---

### Post by CptPicard on 2009-02-13
The fundamental Java threading integration is an integral language issue -- Thread is very much a foundational Java class, and the associated monitor etc abstractions have been been core Java language abstractions for a long time. The Java Concurrency API is a latter, more elaborate library that is part of the standard library, and makes strong use of the former.

Nevertheless, it still is a nonsense point to debate, although the idea that threading in particular is amenable to library implementantions is valid. The OP should, and as per PMs with me, already has, looked at making use of Java's threading for his GAs to increase efficiency instead of changing languages.

---

### Post by eye208 on 2009-02-13
> **CptPicard said:**
> Nevertheless, it still is a nonsense point to debate
I told you so in post #12.

---

### Post by tneva82 on 2009-02-14
> **eye208 said:**
>  Implementing a threaded app is easier in C++. Game over! :P

Only if you are willing to use non-standard libraries. In Java it's easier to use threaded app's with standard librariers.

Haven't EVER seen more blindsided fellow than you.

---

### Post by ajackson on 2009-02-14
> **eye208 said:**
> When I talked about ISO standards, you guys told me that de facto standards matter more than de jure standards. So there, GNU C++ is a de facto standard. Now you are referring to ISO again. Sorry, but your last leg has just been cut off. Implementing a threaded app is easier in C++. Game over! :P
I had to divert you away from the term standard because you couldn't grasp what that concept meant.

The Java code can be compiled on **any** Java compiler that implements the current (version 6) Java standard, your latest C++ code can be compiled only on GNU C++ not **any** C++ compiler that implements the current C++ standard.

*snip*
I think the conclusions have been drawn, no need to keep riding the roundabout

---

### Post by ajackson on 2009-02-14
> **scourge said:**
> So you want to compare threading in Java to threading in C++, but 3rd party libraries like Boost and POSIX are banned? When the rules of the competition are defined like this, Java wins hands down, since pure ISO C++ doesn't have threads. But what use is this kind of a comparison?
The playing field is level, a core implementation of the latest Java and C++ standards. Of course implementing a threaded application is as easy in both if you allow third party libraries that is one of the ideas of third party libraries to fill the gaps that the standards miss.

The discussion was about the core implementation being easier in one language than the other, eye208 has tried various smoke and mirror distraction techniques because he refuses to see what you have stated clearly.

> **scourge said:**
> pure ISO C++ doesn't have threads

I will state again when you use third party libraries it is just as easy to implement a threaded application in C++ as is Java, when you don't (the subject of this discussion) it is not.

Sadly ey208 is a troll which is a pity because he seems to know how to code.

---

### Post by yse on 2009-02-14
> **SNYP40A1 said:**
> About a week ago I started a Java vs. C++ thread.  Since then, I have coded up two simple test and indeed, found the Java code to run significantly faster than C++.  Most of the execution was spent in library calls so I cannot claim that C++ is more efficient...just more efficient in this case.  In any case, how hard would it be to integrate the C++ library via a C++ interface and have the rest of the project coded in Java?  This would allow me to use my preferred Eclipse IDE and still have speed where it matters.  I googled and found references to JNI, but everything on C++ and Java integration that I found was dated before 1999.  Can this no longer be done or is it no longer done for performance reasons -- the interface being so slow that all performance gains obtained from C++ are lost in the interface translation / loading?

C++ is faster that Java in all cases.

You do something wrong IMHO.

---

### Post by scourge on 2009-02-14
> **ajackson said:**
> I will state again when you use third party libraries it is just as easy to implement a threaded application in C++ as is Java, when you don't (the subject of this discussion) it is not.

With this I agree, and it should be the end of the discussion, because there's nowhere we can go from here. However, I think it would be interesting to compare Boost or Qt threads to Java threads in another discussion.

> Sadly ey208 is a troll which is a pity because he seems to know how to code.

I wouldn't be so quick to call other posters trolls, even if they argue provocatively. In fact, I don't even see the point in trying to evaluate their character. That's not what this forum is about.

---

### Post by ajackson on 2009-02-14
> **scourge said:**
> With this I agree, and it should be the end of the discussion, because there's nowhere we can go from here. 
I agree, for me I think the discussion is over. If others want to continue it by all means do so, just remember **what** the discussion is about.

---

### Post by eye208 on 2009-02-14
> **tneva82 said:**
> Only if you are willing to use non-standard libraries. In Java it's easier to use threaded app's with standard librariers.

Haven't EVER seen more blindsided fellow than you.
The flaw in your and ajackson's logic is that you keep switching between two different definitions of the term "standard".

**If "standard" means "ISO/IEC standard"**, then the entire Java ecosystem is non-standard. There is neither an ISO Java standard nor an ISO Java standard library.

**If "standard" means "de facto standard"**, then GNU Common C++ is a standard library. The GNU Compiler Collection is a de facto standard that exists on multiple platforms. GCC is the default compiler on Linux, BSD and Mac OS. It supports more target platforms than any other compiler, including Java.

No matter which definition of "standard" you stick to, the result is in C++'s favor. You have seen the examples. Multithreading in C++ involves fewer lines of code. It's easier.

---

### Post by ajackson on 2009-02-14
> **eye208 said:**
> The flaw in your and ajackson's logic is that you keep switching between two different definitions of the term "standard".
No just the one but you have to understand order of precedence. The only person who keeps trying to move the goal posts is you. This is why I stopped using the term standard as you have no idea what it means.

If a language has a de jure standard, that is it's standard. If a languages doesn't have a de jure standard then the de facto standard is it's standard.

C++ has a de jure standard, it does have de facto standards but they are largely platform specific (i.e. GNU on Linux). C++'s standard is the de jure standard.

Java has no de jure standard, it does have a de facto standard that is platform independent. Java's standard is the de facto standard.

I'll let you have the final word <snip>

---

### Post by eye208 on 2009-02-14
> **ajackson said:**
> If a language has a de jure standard, that is it's standard. If a languages doesn't have a de jure standard then the de facto standard is it's standard.
A language can have both a de jure standard and a de facto standard as long as the latter does not violate the former. In the case of GNU C++, the ISO standard is a subset of the de facto standard. There is no conflict at all.

In the case of Java, there is no de jure standard, and the de facto standard keeps changing with every release. Ask any full-time Java developer if he/she thinks that Java is a standardized language. You will hear a [resounding No!](http://forums.sun.com/thread.jspa?threadID=5365088&tstart=0)

There have been both binary and source code incompatibilities in every Java release. If you don't believe me, take a look at these documents issued by Sun:

[http://java.sun.com/javase/6/webnotes/compatibility.html](http://java.sun.com/javase/6/webnotes/compatibility.html)
[http://java.sun.com/j2se/1.5.0/compatibility.html](http://java.sun.com/j2se/1.5.0/compatibility.html)
[http://java.sun.com/j2se/1.4.2/compatibility.html](http://java.sun.com/j2se/1.4.2/compatibility.html)
[http://java.sun.com/j2se/1.4.1/compatibility.html](http://java.sun.com/j2se/1.4.1/compatibility.html)
[http://java.sun.com/j2se/1.4/compatibility.html](http://java.sun.com/j2se/1.4/compatibility.html)
[http://java.sun.com/j2se/1.3/compatibility.html](http://java.sun.com/j2se/1.3/compatibility.html)
[http://java.sun.com/products/jdk/1.2/compatibility.html](http://java.sun.com/products/jdk/1.2/compatibility.html)
[http://java.sun.com/products/jdk/1.1/compatibility.html](http://java.sun.com/products/jdk/1.1/compatibility.html)

Java is not a standard by any stretch of the imagination. If you require full compatibility with all existing Java applications, you have to install no less than **seven** JREs side by side!

<snip>

---

### Post by ajackson on 2009-02-14
> **eye208 said:**
> A language can have both a de jure standard and a de facto standard as long as the latter does not violate the former. In the case of GNU C++, the ISO standard is a subset of the de facto standard. There is no conflict at all.
You are right it can have both **but** the de jure is always the standard when the de jure exists.

> the de facto standard keeps changing with every release.
So the C++ standard doesn't change with each new version of the standard? Remarkable.

> Ask any full-time Java developer if he/she thinks that Java is a standardized language. You will hear a [resounding No!](http://forums.sun.com/thread.jspa?threadID=5365088&tstart=0)
I see one solitary post (not yours was it).

> There have been both binary and source code incompatibilities in every Java release.
Who every said that backwards compatibility was a requirement of a standard change?

> Java is not a standard by any stretch of the imagination.
Excuse me while I snigger.

>  If you require full compatibility with all existing Java applications, you have to install no less than **seven** JREs side by side!
Excuse the parrot, ho every said that backwards compatibility was a requirement of a standard change?

> <snip>
For those that missed the snip it read
> Sorry, but you guys really have no clue. And frankly, I don't believe that anyone of you has ever written a non-trivial application in Java. The level of stupidity you are displaying here is truly breathtaking.
So what does writing or not writing non-trivial applications in a particular have to do with understanding what a standard is?

Not being able to understand general concepts (standards aren't purely for programming languages you know) is more scary IMHO.

Oh I was right my cat does discuss things in a more sensible way.

---

### Post by bapoumba on 2009-02-14
Getting heated here, closing for now.

Edit: the thread will remain closed.

---

