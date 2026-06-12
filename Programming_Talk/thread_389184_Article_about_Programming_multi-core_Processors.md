---
title: "Article about Programming multi-core Processors"
date: 2007-03-20
forum: Programming Talk
---

### Post by pmasiar on 2007-03-20
DDJ article [Programming the Cell Processor](http://www.ddj.com/dept/64bit/197801624)  for people interested in down-and-dirty performance optimization: new challenges  when using new multicore processors, like Cell in PlayStation 3.

Cell has 1 main 64-bit processor with a PowerPC instruction set, and 8 SIMD processor with no cache (so you need load/unload local memory in 256K "pages"). IIUC it runs Fedora.

Coding gives you lots of power: 1 CEll CPU performs comparable to a 256-processor BlueGene/L supercomputer, but lots of hard work too: 60 lines algorithm was "paralelized" into 1200 lines of optimized code.

Just to give you taste of coming challenges - in case you guys thought all important problems are solved :-)

---

### Post by rplantz on 2007-03-20
Thank you for the citation.

A couple of years ago I translated a Fourier transform algorithm in C to use the altivec array processor on the PowerPC chip. It grew from a few lines to several pages, and it ran four times as fast.

During the past decade or so, there has been a trend in CS education to reduce emphasis on processor architecture. The general feeling is that high-level languages are so powerful, and processors so fast, we don't need to think about the hardware anymore.

This article supports my claim that there will always be new hardware that is not yet supported completely by compilers. I claim that good programmers need to know how the hardware works. (I also claim that good drivers need to know how cars work. :))

---

### Post by Wybiral on 2007-03-20
> **rplantz said:**
> I claim that good programmers need to know how the hardware works.

I absolutely agree, how are you supposed to write efficient programs if you don't understand at least the basics of what is going on when your program is executed?

I think too many people hide behind high level languages, and then they are stuck at the level of efficiency that the language is at and it's too complex of an abstraction layer for most people to understand enough to write efficiently.

I'm a pretty firm believer that you have to understand the machine as well as the processes that go on between your source code and the machine before you can really write efficient software.

Modern compilers and interpreters are only capable of so much, the rest is all up to you.

---

### Post by Mr. C. on 2007-03-20
Writing code to deal with parallelism is very difficult, and in fact while hardware has made leaps and bounds, developing parallel programs in computer science has hardly advanced in 30 years.

Here's a good article.

[http://www.eetimes.com/news/latest/showArticle.jhtml?articleID=197801653](http://www.eetimes.com/news/latest/showArticle.jhtml?articleID=197801653)

MrC

---

### Post by hod139 on 2007-03-20
> **Mr. C. said:**
> Writing code to deal with parallelism is very difficult, and in fact while hardware has made leaps and bounds, developing parallel programs in computer science has hardly advanced in 30 years.

Took the words right out of my mouth.  Here is an article about an interesting attempt by Valve to write a complier to automagically take advantage of multiple cores now available on most modern PCs: [http://arstechnica.com/articles/paedia/cpu/valve-multicore.ars](http://arstechnica.com/articles/paedia/cpu/valve-multicore.ars)

---

### Post by ib84 on 2007-03-22
hello,

Before reading this thread, i considered buying a PS3, to do CPU-intensive videotranscoding (1080i H.264 HighProfile, PAFF-interlaced). but you stated, it takes tricky modifying of the source code, which is beyond my possiblities.

Last question before giving up the PS3 as cheap highperformance CPU:
if a given Opensource programm is already adapted to multithreading (as i think ffmpeg is), would it still take difficult code optimizations to run ffmpeg at the real speed of the cell-processor?

thanks for a short&simple answer

regards

---

### Post by Mr. C. on 2007-03-22
> **ib84 said:**
> ... would it still take difficult code optimizations...

I find these yes/no questions a bit like a friend asking me if its cold outside, and should she wear a jacket.

Difficult for *who*: you, or someone who has written code for parallel systems, understand semaphores and monitors, threads synchronization, deadlocks, etc.

Only you can answer such a question for yourself.

MrC

---

### Post by pmasiar on 2007-03-26
Couple more related links: 

CPU speed increase is basically over at 3MHz, to gain app speed from newest CPU we need to use concurrency [The Free Lunch Is Over: A Fundamental Turn Toward Concurrency in Software](http://www.gotw.ca/publications/concurrency-ddj.htm)

Erlang, language designed for concurrency and reliability. 1.7 mil LOC in telephone switch, not available for 30ms per year! web server, able to handle 80k connections! And how java/C# compares with Erlang when handling concurrency. [Concurrency Oriented Programming in Erlang](http://ll2.ai.mit.edu/talks/armstrong.pdf) 

Enjoy!

---

