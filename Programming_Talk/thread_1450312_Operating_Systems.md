---
title: "Operating Systems"
date: 2010-04-08
forum: Programming Talk
---

### Post by JDShu on 2010-04-08
I'm trying to teach myself how operating systems work, at the level of of an undergrad level introduction to operating systems course. Currently I'm am reading and trying to absorb the notes [here]("http://pages.cs.wisc.edu/%7Esolomon/cs537-old/last/notes.html"). However while understandable its really a supplement for the students who took the course.

What would your advice be to learn operating systems, hopefully without needing to purchase anything. The local library has Tanenbaum's 2nd edition of the book, which I'm guessing teaches basic concepts but is really out of date - maybe that doesn't matter? Do you guys know any online resources, and what kind of projects should I do to best learn how operating systems work?

---

### Post by soltanis on 2010-04-09
Though a lot of components in OS's have definitely become very complex over the years, the basic ideas of it have remained largely the same. I'd hit the Tanenbaum book -- after all, the K&R book is also old as hell, but it's still the best reference for C.

---

### Post by lostinxlation on 2010-04-09
To understand how OS works, you need to know how computers work in depth. So, before going into OS, you should read the computer architecture books and have a good understanding on how the processor works at instruction level as well as other stuffs such as virtual memory, cache, trap etc...

---

### Post by Luke has no name on 2010-04-09
"Understanding the Linux Kernel 3e"

Way over my head. Heh.

---

### Post by NovaAesa on 2010-04-09
I would highly recommend "Operating Systems, Internals and Design Principals" by Stallings. It's written in a way that's very easy to read. Maybe check a few libraries to see if they have it.

---

### Post by vik_2010 on 2010-04-09
Here buddy,

I think you'll like this:

[http://webcast.berkeley.edu/course_details_new.php?seriesid=2010-B-26518&semesterid=2010-B](http://webcast.berkeley.edu/course_details_new.php?seriesid=2010-B-26518&semesterid=2010-B)

---

### Post by JDShu on 2010-04-09
> **NovaAesa said:**
> I would highly recommend "Operating Systems, Internals and Design Principals" by Stallings. It's written in a way that's very easy to read. Maybe check a few libraries to see if they have it.

> **soltanis said:**
> Though a lot of components in OS's have  definitely become very complex over the years, the basic ideas of it  have remained largely the same. I'd hit the Tanenbaum book -- after all,  the K&R book is also old as hell, but it's still the best reference  for C.

Thanks! I've reserved those two books!

> **lostinxlation said:**
> To understand how OS works, you need to  know how computers work in depth. So, before going into OS, you should  read the computer architecture books and have a good understanding on  how the processor works at instruction level as well as other stuffs  such as virtual memory, cache, trap etc...

hmm I see that makes sense. Do you have a book that you would recommend?

---

### Post by uljanow on 2010-04-09
The best way of learning how an OS works is by writing one. I'd recommend ARM (RISC) which is a clean architecture.

---

### Post by JDShu on 2010-04-09
> **uljanow said:**
> The best way of learning how an OS works is by writing one. I'd recommend ARM (RISC) which is a clean architecture.

That sounds like a massive undertaking o.O

---

### Post by NathanB on 2010-04-09
> **JDShu said:**
> That sounds like a massive undertaking o.O

It may "sound" that way, but it doesn't need to be "massive" to qualify as an Operating System.  Mind you, the CompSci graduation requirement at most Universities is that the student either construct their own compiler or their own OS.  It is the best way to demonstrate that the student learned all the skills taught by their previous course work.  This is why hobby compilers and hobby OS's are the most common type of software you'll encounter (both OSS and private) on the 'net.

The academic resources are plentiful and easily accessible:  [http://aodfaq.wikispaces.com/](http://aodfaq.wikispaces.com/)

---

### Post by Cracauer on 2010-04-10
That link to the Tannenbaumish material isn't quite to my liking. It doesn't even know about virtual memory. While you can argue that it is easier to understand this way you also learn something that is not relevant anymore.

This is what I recommend:
[http://www.amazon.com/Design-Implementation-FreeBSD-Operating-System/dp/0201702452/ref=sr_1_1?ie=UTF8&s=books&qid=1270875289&sr=8-1](http://www.amazon.com/Design-Implementation-FreeBSD-Operating-System/dp/0201702452/ref=sr_1_1?ie=UTF8&s=books&qid=1270875289&sr=8-1)

Unfortunately books about the Linux kernel are general very poor self-teaching material, the above BSD book is based on a classic book. Everything in there is relevant, it has virtual memory and modern filesystems. That doesn't mean that the FreeBSD kernel still looks like the book says but at least you got a fighting chance. This is probably the best combo of book and running(!) kernel you can get.

---

### Post by lostinxlation on 2010-04-10
> **JDShu said:**
>  
hmm I see that makes sense. Do you have a book that you would recommend?
If you don't know much about computer architecture, "Computer Organization & Design" written by John Hennessy and David Patterson is a good start. Don't be confused with another book written by the same authors, "Computer Architecture, quantitative analysis', which is a book with much advanced topic for processor performance analysis.

---

### Post by JDShu on 2010-04-12
> **lostinxlation said:**
> If you don't know much about computer architecture, "Computer Organization & Design" written by John Hennessy and David Patterson is a good start. Don't be confused with another book written by the same authors, "Computer Architecture, quantitative analysis', which is a book with much advanced topic for processor performance analysis.

I got a hold of the book and its a great read, thanks!

---

### Post by phrostbyte on 2010-04-13
Wikipedia believe it or not is a pretty decent resource for this kind of stuff, if you know where to look.

[http://en.wikipedia.org/wiki/Mutex](http://en.wikipedia.org/wiki/Mutex)
[http://en.wikipedia.org/wiki/Semaphore_%28programming%29](http://en.wikipedia.org/wiki/Semaphore_%28programming%29)
[http://en.wikipedia.org/wiki/Thread_%28computer_science%29](http://en.wikipedia.org/wiki/Thread_%28computer_science%29)
[http://en.wikipedia.org/wiki/Process_scheduling](http://en.wikipedia.org/wiki/Process_scheduling)
[http://en.wikipedia.org/wiki/Interrupts](http://en.wikipedia.org/wiki/Interrupts)
[http://en.wikipedia.org/wiki/Real-time_OS](http://en.wikipedia.org/wiki/Real-time_OS)
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

---

### Post by phrostbyte on 2010-04-13
Of course after you get a grasp of the fundamentals, it's always worth looking at a production kernel to see how it might be structured. Hey, I know of such production kernel. It's called the "Linux kernel". :P

But you can get Linus's branch quite easily, this command will spit it in the directory of your choosing (install [git-core]("apt://git-core")):

```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
```

Some interesting stuff is in the arch/x86/boot directory.

---

