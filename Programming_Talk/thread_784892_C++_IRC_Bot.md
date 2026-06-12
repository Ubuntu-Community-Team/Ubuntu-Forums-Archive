---
title: "C++ IRC Bot"
date: 2008-05-06
forum: Programming Talk
---

### Post by solarwind on 2008-05-06
Hey all, does anyone know of a c++ IRC bot other than bobot++ (it's horribly written)? Or a framework. I'm trying to make one and I don't want to start from scratch.

---

### Post by Kadrus on 2008-05-07
mm..I suggest creating an IRC bot using Perl...[Link]("http://wholok.com/irc/")

---

### Post by solarwind on 2008-05-07
I need to do it in C++

---

### Post by Wybiral on 2008-05-07
> **solarwind said:**
> I need to do it in C++

Why?

---

### Post by LaRoza on 2008-05-07
> **solarwind said:**
> I need to do it in C++

"need"? Homework?

---

### Post by solarwind on 2008-05-07
> **LaRoza said:**
> "need"? Homework?

That sounds like a very ignorant assumption. I do not take computer science class. I need to do it in c++ because I want to. I like it. Also because I feel that C++ has very little overhead compared to most other interpreted languages and that it's better suited for this job. Also, I like c++, did I mention that?

---

### Post by LaRoza on 2008-05-07
> **solarwind said:**
> That sounds like a very ignorant assumption. I do not take computer science class. I need to do it in c++ because I want to. I like it. Also because I feel that C++ has very little overhead compared to most other interpreted languages and that it's better suited for this job. Also, I like c++, did I mention that?

Does it sound ignorant? Or does it sound like I have seen too many homework questions on this forum?

I was asking, not accusing. If you want to accuse me of being ignorant, at least have evidence of it. 

Homework questions would have been moved if I were to believe it to be homework. 

If you want to do it in C++, you don't "need". C++ may have less overhead, but development time will be substantially increased. Whose time is more important, yours or a processors? There is nothing wrong with doing it in C++, it is your choice, however, without clarification of why you "needed" to do it in C++, I doubt anyone would answer.

Note I wasn't the first one to suspect something afoot, perhaps he is ignorant too?

---

### Post by solarwind on 2008-05-07
Perhaps.

> If you want to do it in C++, you don't "need". C++ may have less overhead, but development time will be substantially increased. Whose time is more important, yours or a processors?

Processor's.

---

### Post by LaRoza on 2008-05-07
> **solarwind said:**
> 
Processor's.
This may help: [http://www.governmentsecurity.org/archive/t10881.html](http://www.governmentsecurity.org/archive/t10881.html)

It gives advise which may help also. It seems to use C or C++.

As for the processor's time being more important, I doubt the CPU will be the bottleneck.

---

### Post by solarwind on 2008-05-07
> **LaRoza said:**
> This may help: [http://www.governmentsecurity.org/archive/t10881.html](http://www.governmentsecurity.org/archive/t10881.html)

It gives advise which may help also. It seems to use C or C++.

As for the processor's time being more important, I doubt the CPU will be the bottleneck.

Thanks. I appreciate you searching that up for me. However, prior to posting, I did a lot of research and came across many sites (including that one) which were no use to me. The best I could find was bobot++, a poorly written c++ fork of bobot. It's horribly written. I'd fix it up, but I'd much rather be writing my own custom stuff and use a framework.

I see your point about the CPU being the bottleneck. I do agree, but I'd much rather have a native application than having to fire up a vm to interpret my code. Also, this stuff will be running on BSD machines that do not have perl, python or java. Trust me, my best languages are Java and Python. For this kind of stuff, I would generally use Python and Java, but in this case, I'd much rather do it in c++ anyway.

---

### Post by LaRoza on 2008-05-07
> **solarwind said:**
> Thanks. I appreciate you searching that up for me. However, prior to posting, I did a lot of research and came across many sites (including that one) which were no use to me. The best I could find was bobot++, a poorly written c++ fork of bobot. It's horribly written. I'd fix it up, but I'd much rather be writing my own custom stuff and use a framework.

I doubt I could find anything more that would be useful.

If the existing frameworks are not usable, it would seem the best solution is to write your own. 

Using bobot and its fork as examples, perhaps you could write something even better.

I found this, in C: [http://www.dryfish.org/cbot/download.html](http://www.dryfish.org/cbot/download.html)

---

### Post by solarwind on 2008-05-07
> **LaRoza said:**
> I doubt I could find anything more that would be useful.

If the existing frameworks are not usable, it would seem the best solution is to write your own. 

Using bobot and its fork as examples, perhaps you could write something even better.

I found this, in C: [http://www.dryfish.org/cbot/download.html](http://www.dryfish.org/cbot/download.html)

Thanks. I came across that earlier as well. Thanks again!

---

### Post by Wybiral on 2008-05-07
> **solarwind said:**
> Also because I feel that C++ has very little overhead compared to most other interpreted languages and that it's better suited for this job.

Why not use C? It has even less overhead than C++. But, you do know that the bottleneck in this program will be the network, which has nothing to do with the language... Right? What makes C++ more suited for this job than, say, Python/Lisp/Ruby/Perl? C++ has terrible facilities for handling strings and built-in support for parsing data, etc... The things that would make a language "suited" for an IRC bot.

But, you'll see... Have fun! (some people live for pain)

---

### Post by solarwind on 2008-05-07
> **Wybiral said:**
> Why not use C? It has even less overhead than C++. But, you do know that the bottleneck in this program will be the network, which has nothing to do with the language... Right? What makes C++ more suited for this job than, say, Python/Lisp/Ruby/Perl? C++ has terrible facilities for handling strings and built-in support for parsing data, etc... The things that would make a language "suited" for an IRC bot.

But, you'll see... Have fun! (some people live for pain)

I'll be sure to keep your prophecy in mind when I'm writhing in pain writing C++ code, mighty Dumbledore.

---

### Post by ZylGadis on 2008-05-07
> **solarwind said:**
> That sounds like a very ignorant assumption. I do not take computer science class. I need to do it in c++ because I want to. I like it. Also because I feel that C++ has very little overhead compared to most other interpreted languages and that it's better suited for this job. Also, I like c++, did I mention that?

C++ is not an interpreted language. Besides, given your priorities, I'd use machine code (in hex, because I think binary is too low level).

---

### Post by Wybiral on 2008-05-07
> **solarwind said:**
> I'll be sure to keep your prophecy in mind when I'm writhing in pain writing C++ code, mighty Dumbledore.

Well, I'm sure it doesn't seem painful when that's all you know, just like I'm sure higher-level languages seem pointless right now. [Read]("http://www.paulgraham.com/avg.html").

---

### Post by solarwind on 2008-05-08
> **ZylGadis said:**
> C++ is not an interpreted language. Besides, given your priorities, I'd use machine code (in hex, because I think binary is too low level).

Haha! I see what you did there! Funny man!

---

### Post by solarwind on 2008-05-08
> **Wybiral said:**
> Well, I'm sure it doesn't seem painful when that's all you know, just like I'm sure higher-level languages seem pointless right now. [Read]("http://www.paulgraham.com/avg.html").

Well, I know C, C++, Java, Python, PHP, PIC micro assembler, 8086 assembler, so... I know what I'm doing...

Whatever, this thread is getting pointless. People like to argue about stupid things, even if they haven't the slightest clue on what they're talking about. I will find my way. I give thanks to all who *humbly* tried to answer, without posting wise a$$ remarks (I'm looking at you, ZylGadis, it's not cool, you phale). I'm half way done writing a bot in c++. Thanks again!

Over and out.

---

### Post by Wybiral on 2008-05-08
> **solarwind said:**
> People like to argue about stupid things, even if they haven't the slightest clue on what they're talking about.

Yes, they sure do.

(did you see what I did there?)

---

### Post by Wybiral on 2008-05-08
> **solarwind said:**
> Well, I know C, C++, Java, Python, PHP, PIC micro assembler, 8086 assembler, so... I know what I'm doing...

So, of course, you know that something as trivial as an IRC bot could be written in a few lines of Python or Lisp code? Doing it in C++ when you could do it in Python seems like a terrible waste of typing time.

---

### Post by LaRoza on 2008-05-08
> **Wybiral said:**
> So, of course, you know that something as trivial as an IRC bot could be written in a few lines of Python or Lisp code? Doing it in C++ when you could do it in Python seems like a terrible waste of typing time.

I think the earlier post of the OP stating that the machine this is going to run on explains the reason for C++ (or any compiled language I imagine).

---

### Post by slavik on 2008-05-08
> **LaRoza said:**
> Does it sound ignorant? Or does it sound like I have seen too many homework questions on this forum?

I was asking, not accusing. If you want to accuse me of being ignorant, at least have evidence of it. 

Homework questions would have been moved if I were to believe it to be homework. 

If you want to do it in C++, you don't "need". C++ may have less overhead, but development time will be substantially increased. Whose time is more important, yours or a processors? There is nothing wrong with doing it in C++, it is your choice, however, without clarification of why you "needed" to do it in C++, I doubt anyone would answer.

Note I wasn't the first one to suspect something afoot, perhaps he is ignorant too?

to extend this a bit:
1. LaRoza, you killed JFK and Lincoln!!! :P
2. Writing an IRC bot in a language that is better suited for text processing (Perl, Ruby, Python, many others) would be simpler than C++ (depending on what you need the bot to actually do).

(NOTE: PRP = "Perl, Ruby, Python")

extending #2:
connecting to a computer in PRP will take 5 lines, in C++ (like in C) 30.
if you want to do any kind of a response to a loosely worded question you will need to use a regex, meaning PRP is simpler.

There is nothing wrong with C++ and if you continue on with using C++, you will learn a lot about the system and even appreciate PRP should you move on to them.

but in one sentece, my point is "you win either way." :)

---

### Post by Wybiral on 2008-05-08
> **LaRoza said:**
> I think the earlier post of the OP stating that the machine this is going to run on explains the reason for C++ (or any compiled language I imagine).

Yeah, it was post #6 that I was responding to (where it wasn't so clear that it was for a special machine, mostly by phrases like "I like C++" that make my head explode a little).

---

### Post by slavik on 2008-05-08
> **Wybiral said:**
> Yeah, it was post #6 that I was responding to (where it wasn't so clear that it was for a special machine, mostly by phrases like "I like C++" that make my head explode a little).

NASA has had probes which ran on interpreted code (I don't remember what language this was) (it was lost because one of the variables in a comparison was misspelled).

---

### Post by Wybiral on 2008-05-08
> **slavik said:**
> NASA has had probes which ran on interpreted code (I don't remember what language this was) (it was lost because one of the variables in a comparison was misspelled).

lol, so NASA doesn't use unit tests?

---

### Post by slavik on 2008-05-08
> **Wybiral said:**
> lol, so NASA doesn't use unit tests?
this was way back in the day ... 80s or such I think.

EDIT:
I was incorrect, it was in the 60s, and they used FORTRAN, here's the wikipedia link: [http://en.wikipedia.org/wiki/Mariner_1](http://en.wikipedia.org/wiki/Mariner_1)

---

### Post by LaRoza on 2008-05-08
> **slavik said:**
> NASA has had probes which ran on interpreted code (I don't remember what language this was) (it was lost because one of the variables in a comparison was misspelled).

Ada has resulted in the destruction of very expensive hardware, and Lisp has allowed the success of a mission.

> 
An even more impressive instance of remote debugging occurred on NASA's 1998 Deep Space 1 mission. A half year after the space craft launched, a bit of Lisp code was going to control the spacecraft for two days while conducting a sequence of experiments. Unfortunately, a subtle race condition in the code had escaped detection during ground testing and was already in space. When the bug manifested in the wild--100 million miles away from Earth--the team was able to diagnose and fix the running code, allowing the experiments to complete.14 One of the programmers described it as follows:
Debugging a program running on a $100M piece of hardware that is 100 million miles away is an interesting experience. Having a read-eval-print loop running on the spacecraft proved invaluable in finding and fixing the problem.

---

### Post by WitchCraft on 2010-03-04
> **LaRoza said:**
> Ada has resulted in the destruction of very expensive hardware, and Lisp has allowed the success of a mission.

No, Ada wasn't the fault, the fault was that the ballistic data was not updated for Arianne5, it used the Arianne4 data...
Would have resulted in the same catastrophe if LISP was used, unless LISP's errors would have compensated for the garbage data.

---

### Post by WitchCraft on 2010-03-04
> **Wybiral said:**
> lol, so NASA doesn't use unit tests?

I can safely say this: NASA does. 
But the *censored* ESA management decided that they needed to safe money, since Arianne5 was too expensive.
Oh and BTW, the management wasn't the entity being fired for this...

---

### Post by cariboo on 2010-03-04
This thread is 2 years old, there is no need to reopen it. If you want to comment on the subject please start a new thread. Closed.

---

