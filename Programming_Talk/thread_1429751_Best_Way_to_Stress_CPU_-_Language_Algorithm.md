---
title: "Best Way to Stress CPU - Language? Algorithm?"
date: 2010-03-14
forum: Programming Talk
---

### Post by era86 on 2010-03-14
Greetings all!

I'm trying to write a small application for stressing/torturing my CPU.  I know there are already programs that do this such as Prime95, but I was wondering if there are any other algorithms out there that are used in stress tests.

Also, is there a specific language to use here?  I was going to use Python because I've worked with the thread library for it.

Any feedback would be appreciated.  Thanks in advanced!

---

### Post by LKjell on 2010-03-14
well.... you see the blue square with ATTENTION ALL USERS: Malicious Commands ? If you read about forkbomb it will stress your cpu till your system hangs.

---

### Post by Sam on 2010-03-14
```
echo "void main(int argc, char **argv) { while(1); }" > stress.c && gcc stress.c -o stress

./stress
```

Ctrl-C to exit

---

### Post by schauerlich on 2010-03-14
> **Sam said:**
> ```
echo "void main(int argc, char **argv) { while(1); }" > stress.c && gcc stress.c -o stress

./stress
```

Ctrl-C to exit

That'll only take care of one core. you could run ./stress for as many cores as you have, though.

Also, ANSI cops don't like void main :)

---

### Post by soltanis on 2010-03-14
I'm no expert here but it seems to me that floating point operations tend to be stressful (that's why GPUs tend to handle them when they're needed i.e. in graphics-intensive applications).

If you want to just torture your CPU and never get anywhere, I hear that prime factorization is one hell of a problem. Consider parallelizing it for maximum power wastage.

---

### Post by era86 on 2010-03-14
I'm currently using the following in Python:

```

import threading
import math

def primefactors(x):
    factorlist=[]
    loop=2
    while loop<=x:
        if x%loop==0:
            x/=loop
            factorlist.append(loop)
        else:
            loop+=1
    return factorlist

class MyThread ( threading.Thread ) :
    def run(self):
       for i in range(100000):
           print primefactors(i)
                
 
for i in range(4):
    MyThread().start()

```

But it doesn't stress the cores all the way.  I get maybe 70-85% load on average.  Perhaps doing this in a different language will make a difference?

---

### Post by flippo on 2010-03-14
For what purpose, or on what level do you intend on stressing your processor?

Processors are very complicated things, they do some very nasty things internally that make them fast.  If you want to write a truly gruesome micro-architectural test you have to take things into account like cacheing, out-of-order processing, load-store queue prediction, branch prediction, etc etc...

If you looking to write something truly nasty on a core, then assembly is pretty much the only way to go (one of the few things that needs that much control).  

If you just want to watch your CPU numbers go through the roof, I would recommend a compiled language, you wont have to worry about the interpreter doing strange things you don't intend.

---

### Post by Cracauer on 2010-03-14
The best stress test is mprime/prime95.

I don't think anybody knows exactly why but it heats up the CPUs most. And it has the required internal checking so that you get reports when things go wrong.

---

### Post by Bachstelze on 2010-03-15
> **LKjell said:**
> well.... you see the blue square with ATTENTION ALL USERS: Malicious Commands ? If you read about forkbomb it will stress your cpu till your system hangs.

No it won't. What it does is max out the number of available processes so no new process can be created, which is what makes the machine unusable. It doesn't use the CPU at all.

---

### Post by ssam on 2010-03-15
an empty while loop is just a jump instruction, so the more complex parts of the CPU can drop into low power modes while it runs. you need

[http://pages.sbcglobal.net/redelm/](http://pages.sbcglobal.net/redelm/)
[http://packages.ubuntu.com/karmic/cpuburn](http://packages.ubuntu.com/karmic/cpuburn)

it has "optimized assembler for maximum loading"

---

### Post by era86 on 2010-03-15
> **ssam said:**
> an empty while loop is just a jump instruction, so the more complex parts of the CPU can drop into low power modes while it runs. you need

[http://pages.sbcglobal.net/redelm/](http://pages.sbcglobal.net/redelm/)
[http://packages.ubuntu.com/karmic/cpuburn](http://packages.ubuntu.com/karmic/cpuburn)

it has "optimized assembler for maximum loading"

I looked into this a bit more.  I also found that the "pi" program being run from the command line can get one of the cores up to 100% load.

The source for Prime95 uses some assembly code that I might just use.  I was able to sift through it and take a look.  Although complicated, I'll probably just include the source files I need and make the calls.

---

### Post by slavik on 2010-03-16
Welcome to GIL. No matter how many threads you create, they will never be concurrent.

Prime95 is not really a CPU stress tool, it has an actual use (looking for large prime numbers).

---

### Post by era86 on 2010-03-16
> **slavik said:**
> Welcome to GIL. No matter how many threads you create, they will never be concurrent.

Prime95 is not really a CPU stress tool, it has an actual use (looking for large prime numbers).

I understand the Prime95 is used to factor large primes, but the algorithm itself actually does stress on the CPU, putting it at 100% load nearly the whole time.

SuperPi also does this by attempting to approximate pi to user-desired precision.  This usually stresses the cores pretty well too.

I'll read into GIL.  Sounds interesting!  From this link: [http://en.wikipedia.org/wiki/Global_Interpreter_Lock](http://en.wikipedia.org/wiki/Global_Interpreter_Lock), it seems Python has a way to achieve full concurrency using CPython.

I'm thinking of implementing one of the Pi algorithms.  Not sure yet.  This task may just be too much work than it's worth, but I guess it makes a good side project.

---

### Post by soltanis on 2010-03-16
Yeah, the global interpreter lock is pretty terrible as it prevents real concurrency. Of course you can still fork and run two separate processes, in which case the kernel can schedule them concurrently, but you'll have two separate interpreters running as the downside.

Look on the bright side -- there used to be a BKL (Big Kernel Lock) which made the Linux Kernel suck at concurrency the same way.

---

### Post by era86 on 2010-03-16
It seems since Python 2.6, there is a class <b>multiprocessing</b> that will effectively sidestep the GIL by using subprocesses rather than threads.

[http://docs.python.org/dev/library/multiprocessing.html](http://docs.python.org/dev/library/multiprocessing.html)

I'm thinking that I can spawn the pi command as a "process" rather than a thread.  I'll let you know.

---

### Post by Slim Moe on 2010-03-17
```
#include <stdio.h>

int main(int argc, char *argv[])
{
    for (;;)
    {
        char cpu[3] = "CPU";
    }
    
    return 0;
}

```

Adrenaline ..

[[IMG]http://img80.imageshack.us/img80/8555/cpustress.th.png[/IMG]](http://img80.imageshack.us/i/cpustress.png/)

---

### Post by Cracauer on 2010-03-17
There is only one way to find out how stressful a given program is:

Run it.  Measure the CPU temperature.  Whatever has the highest temperature is most stressful at least for that definition of stress.  All the non-hands-on theoretical thought given here and elsewhere goes right out the window once you actually look at what is happening.

In practice, prime95/mprime (and larger suites using prime95 such as OCCT) heat up the CPU most. This is measured, not from theory.

There are tens of thousands of sports overclockers who constantly look for harder and harder test programs. They all use prime95 variants. There is a reason for it, and they look very closely, and they have been looking very closely for many years.

In addition, it is pretty useless to just stress the CPU. Presumably you also want to know when it starts giving out nonsense. In a simple program with no checking on anything you'll never know, and you aren't likely to crash the OS right away. Prime95 has excellent internal consistency checks, and *in practice* it is the first program to report errors.

---

### Post by era86 on 2010-03-17
Well, I basically wanted to make a small program that stresses all cores of the CPU while outputting the temps.  It is very simple, nothing fancy.

I only care about how hot it can get (testing thermal paste for example).  I am under the impression that getting them to run at full load will get them the hottest.

Sorry if I'm misusing the word "stress" here.  Should probably be using the term "get hot" test. :)

I'll compare the heat of the CPU after both tests for about an hour and see if the <i>temperature</i> at all differs, since that's all I care about.  Thanks for the info!

---

### Post by Lux Perpetua on 2010-03-17
You may have misspoken here, but I must point out: > **era86 said:**
> I understand the Prime95 is used to factor large primes....Factoring primes, however large, is trivial. (Don't feel too bad; Bill Gates made the same mistake very publicly a while ago.)

---

### Post by era86 on 2010-03-18
> **Lux Perpetua said:**
> You may have misspoken here, but I must point out: Factoring primes, however large, is trivial. (Don't feel too bad; Bill Gates made the same mistake very publicly a while ago.)

Sorry, got that mixed up.  Thanks for the insight. :popcorn:

---

### Post by Cracauer on 2010-03-18
> **era86 said:**
> Well, I basically wanted to make a small program that stresses all cores of the CPU while outputting the temps.  It is very simple, nothing fancy.

I only care about how hot it can get (testing thermal paste for example).  I am under the impression that getting them to run at full load will get them the hottest.

Sorry if I'm misusing the word "stress" here.  Should probably be using the term "get hot" test. :)

I'll compare the heat of the CPU after both tests for about an hour and see if the <i>temperature</i> at all differs, since that's all I care about.  Thanks for the info!

As has been explained in this thread before:

You don't get a lot of stress from just tiny pieces of code. You only use a small part of the CPU's silicon and the other parts will remain unused and hence untested - and they do not produce heat.

The only way to figure out how much silicon you use is to run a piece of code and look at the CPU temperature.



Edited to add: you also want individual processes, not threads on the different processors. They need to be as separate as possible, any trace of synchronization will ease the load on the CPU. Doesn't matter whether it is locks that are explicit to your program, whether it is cache sychronization done by hardware or whether it is VM page tables and TLB entries maintained by the OS.

---

### Post by Reiger on 2010-03-18
There already exists an excellent &#8220;stress test&#8221; for CPU's. It's called &#8220;compile the Linux kernel&#8221;. With appropriate -M flag (number of cores + 1) it should aggressively occupy all of your cores, and due to the fact that it takes quite some time to compile the kernel allow for heat to &#8220;build up&#8221;.

It quickly gets my old Pentium dual core to 80° anyways.

---

### Post by flippo on 2010-03-18
Although kernel compilation is a decent test it doesn't hit everything (FPU for example...).  Gcc is also known for being a branch prediction killer, which will insert a great deal of noops into the OoO core allowing it to cool.  I think Intel has some benchmarks which are good stress tests.  


No one program will fully stress all parts of your core, but if your just going for heat and really serious about it, the program needs to be written very carefully and with a knowledge of the micro-architecture.

---

### Post by Cracauer on 2010-03-18
Kernel compilation isn't good at all.

First of all there is disk involved. These causes gaps in CPU load even if the block is already resident. Then there is lots of userland/kernel space switched from all the system calls, both for disk blocks but also for tons of stat(2) calls, forks, execs, waits etc. All these kernel turnaround ease off on the CPU.

Then, loading it with `make -j4` or `make -j16` on a 4-core causes substantially less than full load on all cores since there are always moments when the dependency chain isn't filled enough with runnable stuff. This improves if you run 4 independent builds in separate trees all with -j1, but even then the load is much lower than with a carefully selected thing like prime95. Apart from the factors given in the previous paragraph, having multiple trees will now cause much more memory to be used and make it much more likely you actually do his the disk.

The one thing halfway good about kernel compile as a method of CPU load testing is that it has a reasonable, not great but reasonable, amount of internal consistency checking. Flipping random bits from CPU or memory instability has a good chance of causing a build fail. But not a great one, you would never notice if you just have bad code inside your new kernel image. Again, mprime/prime95 has much more to offer.

---

### Post by era86 on 2010-03-18
Thanks Cracauer, I'll actually be using the Prime95 code since it is open source.  It is going to take some work, but who cares, I'll be the one working.  :)

---

### Post by Reiger on 2010-03-18
I thought that the intended &#8220;stress&#8221; was to see how high temperatures would go. For that you do not need something that is pegging the CPU at 100% load; you just need to be running something which keeps it sufficiently occupied for a sufficiently long duration of time that there is a buildup of excess heat. (CPU's have built-in sanity-checks that will down-clock the cores once termal load becomes too high anyway.)

Of course keeping Prime95 running just as long as it would take to compile a kernel gets you a more reliable result; but for simple machines the kernel compile thing should be sufficient load to make the fan prove it is worth its money (or not).

---

### Post by NathanB on 2010-03-19
Just do an internet search of "cpu burn in" and "cpu stress test" to discover some really interesting tools (some with source code) on this subject.

---

### Post by slavik on 2010-03-19
> **era86 said:**
> I understand the Prime95 is used to factor large primes, but the algorithm itself actually does stress on the CPU, putting it at 100% load nearly the whole time.

SuperPi also does this by attempting to approximate pi to user-desired precision.  This usually stresses the cores pretty well too.

I'll read into GIL.  Sounds interesting!  From this link: [http://en.wikipedia.org/wiki/Global_Interpreter_Lock](http://en.wikipedia.org/wiki/Global_Interpreter_Lock), it seems Python has a way to achieve full concurrency using CPython.

I'm thinking of implementing one of the Pi algorithms.  Not sure yet.  This task may just be too much work than it's worth, but I guess it makes a good side project.
Err, Python can't achieve concurrency, it's just like saying that a single CPU is running multiple programs at once (even though it doesn't).

---

### Post by era86 on 2010-03-19
> **slavik said:**
> Err, Python can't achieve concurrency, it's just like saying that a single CPU is running multiple programs at once (even though it doesn't).

What about the link in this post?

> **era86 said:**
> It seems since Python 2.6, there is a class <b>multiprocessing</b> that will effectively sidestep the GIL by using subprocesses rather than threads.

[http://docs.python.org/dev/library/multiprocessing.html](http://docs.python.org/dev/library/multiprocessing.html)

I'm thinking that I can spawn the pi command as a "process" rather than a thread.  I'll let you know.

Would I still be able to achieve multiple processes?

---

