---
title: "Programming for Ubuntu"
date: 2007-03-31
forum: Programming Talk
---

### Post by Majorix on 2007-03-31
I am a young (20 year old) freelancer developer. I will start Computer Programming in university next year.

Anyways, I always liked contributing. As such, since the time I started using Ubuntu I thought about joining the development team.

But the thing is that I don't know what programming languages are used in the development of Ubuntu and if my level of knowledge in these languages is enough to be able to really contribute.

Now, I would be glad if someone responsive for these things could tell me what languages are used, what level of knowledge in them is expected and where I can study these languages further to get better in developing for Ubuntu.

Thanks a lot.

---

### Post by moephan on 2007-03-31
If you go to the [ubuntu job site]("http://www.ubuntu.com/employment") you can get a general idea. Python is the language used for application development, and c/c++ seem to be used for system development. Also, check out the [developer zone]("http://www.ubuntu.com/community/participate/developerzone") where you can get a sense for the tools needed for high level participation, as well as the kinds of projects that the community is working on right now.

If you want to get started today, just pick an app to write, and start writing it in Python. That experience will teach you a lot about your question.

Cheers, Rick

---

### Post by Majorix on 2007-03-31
Oh yes, the Developers Zone was what I was looking for. Thanks Rick. I had changed the homepage of Firefox which originally lead me to that Developers Zone but since the time I changed I was looking for it.

I think the job option is not good for me yet. Since I can't travel internationally because of studies and since I don't have a degree level of education yet (it was in the reqs list in the job option that I was interested in).

So I guess I will just go hunt for some bounties for now :)

Thanks for caring.

---

### Post by pmasiar on 2007-03-31
to start with Python: [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart)

Wiki has also links to language tutorials, data structures courses and tasks to train on: more complicated than simple examples, but simple enough for a beginner.

---

### Post by Wybiral on 2007-03-31
C is a good language, especially if you want to help by adding driver support for unsupported hardware. But it certainly isn't limited to that (graphics, games, and GUI's are all pretty easy in C). C is very useful, fast, and simple.

But if you plan to do any kernel programming or low level stuff for hardware... C is your language, hands down. A basic knowledge of assembly wouldn't hurt too.

---

### Post by Majorix on 2007-03-31
Thanks a lot for the suggestions guys. Though I think I forgot to tell that I am quite ok with C and its children/grandchildren (C++ and C#) and have a basic knowledge of Python (I guess enough to understand a code I see written). I will view some code samples so that I can also write stuff myself. Any links to such sites with samples you know?

I will have to agree with you on that Wybiral, C is the language to go with when you want to code stuff for the kernel or want to develop a game. Even Unix itself is written in C, because it is fast. Thing is, you can do everything Python does with C too, but you can't do everything C does with Python. I can't imagine a 3D advanced game written in Python. That would require one hell of a computer to run fast.

---

### Post by Wybiral on 2007-03-31
> **Majorix said:**
> ... Thing is, you can do everything Python does with C too, but you can't do everything C does with Python. I can't imagine a 3D advanced game written in Python. That would require one hell of a computer to run fast.

I agree. Not that python is bad or anything, but the statement of one-way power was correct. In fact, most python modules were written in C (in fact, python was written in C). But thats enough about that (otherwise this thread will explode into flames)

What kind of source code are you looking for? What kind of software do you want to develop for Linux?

---

### Post by Majorix on 2007-03-31
> What kind of source code are you looking for?

Just any kind. It shouldn't be too hard though, I am just a beginner in Python :) I want to get used to the structure and the libraries.

> What kind of software do you want to develop for Linux?

I guess I will usually just go hunting for bounties. Whichever bounty rewards more, I will try that. So I have no real answer for your question.

---

### Post by pmasiar on 2007-03-31
> **Majorix said:**
> Thing is, you can do everything Python does with C too, but you can't do everything C does with Python. I can't imagine a 3D advanced game written in Python. That would require one hell of a computer to run fast.

I remember when exactly those argument were used to express opinion that Assembler will never be replaced by C. :-)

It is arguable that programming tasks you mentioned above is mostly putting together library calls. Python has [SciPy](http://en.wikipedia.org/wiki/Scipy) and [NumPy](http://en.wikipedia.org/wiki/NumPy) modules to handle complex calculations, fast. Python code is compiled, and C++ code needs "interpret" proper object methods at runtime. Sure there is some performance penalty, but: **don't guess where bottleneck is - measure**. So don't be superstitious about raw speed. Program needs be fast enough, but not faster :-)

Next challenge (next 10-20 years) will be parallel and multiprocess systems. It remains to be seen if high-level language like Python (and coming Py 3.0) will scale better than C in those situations, or if other languages will take hold. Ie. if high-level library calls will scale (with 20% loss compared with C) over 16 CPUs of future chips, the fact that Python is 50% slower than C might be irrelevant and more important would be that it will take care of paralellisation of the processes.

I agree that C is important and faster now than Python. I claim that most important speed in programming is "speed to market" :-)

---

### Post by Wybiral on 2007-03-31
But by the time you're done programming the project... Having to do tests to find bottlenecks... Then reimplementing those parts in C... Couldn't you have just written it in C and had the same "speed to market"?

I don't think C development is that slow... I can develop stuff in it pretty quickly and I'm a slow typer!

It's not premature optimization if you just write in C. It's really not that hard of a language.

And no, for 3d graphics and games, you cannot rely entirely on external library calls, and even if you could... The function call overhead would eventually begin to eat you alive.

C never replaced assembly... Assembly was absorbed by C. People still use assembly to write those C compilers, and in-fact, I use assembly myself almost everyday. But I guess the biggest difference is that C is closer to the speed of assembly then python is close to the speed of C.

Only time will tell with more complicated paralellisation... But even if HLL like python took place... Who would be porting python to work properly? C programmers... Which means there has to be C solutions in the first place.

---

### Post by lnostdal on 2007-03-31
Hm, I think you'll find that quite a lot of stuff is way slower to code using C than a HLL like Python if you actually tried this.

For instance, I'm doing web scraping using a HLL for a client right now. Doing that kind of stuff in C would be quite boring, time-consuming and unsuitable.

edit:
..figuring out where bottlenecks are is easy and fun to do using a profiler: [http://ubuntuforums.org/showpost.php?p=2360427&postcount=2](http://ubuntuforums.org/showpost.php?p=2360427&postcount=2)

---

### Post by Wybiral on 2007-03-31
Well, yeah, C and assembly are terrible for web development. But for most applications I don't think it's THAT big of a speed difference (development speed). C and assembly have libraries too! Thats really the main thing that makes python development so fast, all those modules at your disposal. But once you get locked into a solid collection of your own libraries and ones that you're used to in C or assembly, you can develop pretty quickly.

edit:

lnostdal: writing programs that are already fast is easy and fun using C and assembly!

---

### Post by jvc26 on 2007-03-31
Good tutorial type things that I found useful were:
[http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)
and also I got hold of Beginning Python:Novice to Professional which I found really helpful - and something I still go back to every now and again to refresh my mind on things I've forgotten
Il

---

### Post by lnostdal on 2007-03-31
No, the extra language and environment features (not libraries) in Python(#1) alone will give a significant gain in programmer performance.


#1: well, i must admit i have more knowledge with common lisp .. but say any HLL in general

---

### Post by Wybiral on 2007-03-31
> **lnostdal said:**
> No, the extra language and environment features (not libraries) in Python(#1) alone will give a significant gain in programmer performance.


#1: well, i must admit i have more knowledge with common lisp .. but say any HLL in general

OK, I worded that wrong... Python is like a low level language (like C) but with a bunch of libraries tacked on.

List's could easily be implemented as a library in C (they are all the time)

String operations can easily be implemented in C (yes, even multiplication like python has)

Iterators... RE parsers... Even simple dynamic types... Can all be implemented in C, and there are libraries available for most of them.

So I don't think the difference in development time is all that different if you're comfortable with C and you have access to some good libraries.

But I don't think python is useless... It's a preference issue. But to simply say that python is easier or will always be faster to develop in, that's just not always true.

---

### Post by lnostdal on 2007-03-31
No, Python is not like a low level language with added libraries. C and Python are different languages; also disregarding the libraries.

There is a line or border between "language" and "library". Python-the-language has features that are impossible to do in C-the-language without implementing Python in C. ("greenspunning" if you will)

You are totally missing out if you do not understand high-level language features. They will save time in a big way.

---

### Post by Wybiral on 2007-03-31
I know the difference... But you can easily accomplish the same thing in another language if you have a good enough library.

---

### Post by lnostdal on 2007-03-31
No. A library will not add language features. (edit: in C at least)

---

### Post by pmasiar on 2007-03-31
> **Wybiral said:**
> Python is like a low level language (like C) but with a bunch of libraries tacked on.

Not so. Syntactic sugar around call lowers mental complexity and increases productivity. [Research shows](http://nothing.tmtm.com/archives/494)  higher language with less lines and less language constructs allows to be more productive, plain and simple. Maybe you, Wybiral, is the rare superprogrammer, one out of the of the thousand whose productivity is 100 times average coder, but odds are you are not :-)

IMHO you should read "Mythical man-month" (hint: it is the only book which is as relevant today as it was when written 25 years ago) and Dijkstra's works, like Humble Programmer, to understand software complexity better.

---

### Post by Wybiral on 2007-04-01
lol. Maybe I am...

Or maybe I just know more about C and assembly then most HLL programmers are willing to investigate.

Once you start your own library of code to go back on when need-be, writing in C or even assembly is super-easy and isn't much slower then other languages.

---

### Post by lnostdal on 2007-04-01
You're making a big mistake believing this.

Try doing some of this with libraries in C (and while writing C when using that library):

* lambda / anonymous functions.

* A version of `if' that returns the value (any type) of its then- or else-part:

```

(+ 10 (if t    ;; t means `true'.
          2    ;; The then-part of the if; 2 is returned.
          3))  ;; The else-part of the if; 3 is returned.
=> 12


(+ 10 (if nil  ;; nil means `false'.
          2    ;; The then-part of the if; 2 is returned.
          3))  ;; The else-part of the if; 3 is returned.
=> 13

```

Conditionals that return values like that has saved me a _lot_ of typing. These are very simplified examples, but `if' is used thousands of times in a program and can be used to represent "bigger things" (more complexity/nesting etc.). Actually; almost everything returns a value. For instance `defclass' returns a class _object_ that you can pass around and store in an array etc.. You can create (construct) instances via this class object later on. C cannot refer to a struct; only an instance of a struct.

* In general be able to handle values of any type efficiently. Or being able to write without type declarations first, then add them later when needed.

* Closures. You can essentially take some runtime state (code (ie; not a function pointer) and data), save it in a variable then pass it around and invoke it later .. this stuff is very handy.

* Try doing code-is-data & data-is-code in C. This gives _amazing_ features with regards to meta-programming and macros. This is impossible to do in C. Don't like doing prefix math in Lisp? You can change it to infix if you want.

* Try writing C code like this: [http://nostdal.org/~lars/programming/lisp/aromyxo/concurrency/tests/map-reduce-thing.lisp](http://nostdal.org/~lars/programming/lisp/aromyxo/concurrency/tests/map-reduce-thing.lisp) .. (output from running it is at the bottom). Do you see how the code for new threads (the stuff enclosed in `withThread') are inlined with the rest of the code? Lambdas or anonymous functions are used to achieve this. Google uses something similar, well based on map and reduce btw. [http://labs.google.com/papers/mapreduce.html](http://labs.google.com/papers/mapreduce.html).

* Also take a look at Prolog and Erlang.

* Try adding _compile time_ support for OOP (inheritance, polymorphic methods, multimethods; throw in entire CLOS and the whole MOP while you're at it). Lisp did not always have language-support for OOP but it was added as a library (yes, a library that added compile-time or language support for OOP) .. doing the same in C is impossible.

* Try to add support for reflection and introspection of C structs and other things. "What fields/members does this struct contain?". Then later manipulating an instance of that struct based on the information retrieved from that introspection/reflection. Remember; it should be added as a library and you should write C code at all times. If Lisp did not have support for introspection of classes or structures (and most other things) already it could have easily been added, and it would still all be Lisp code. This would not be the case considering C.

* Implement the point above with both compile- and run-time support.

* Try to add support for runtime (re)compilation of functions/code. Yes, you can change or "create new" code at runtime, and it is compiled to native optimized machine code at all times.

* Try creating something similar to the condition system in Lisp using C. ( [http://www.gigamonkeys.com/book/beyond-exception-handling-conditions-and-restarts.html](http://www.gigamonkeys.com/book/beyond-exception-handling-conditions-and-restarts.html) ). I think it would either be very hard or impossible.

* Implement a compiler for a custom language ([DSL]("http://en.wikipedia.org/wiki/Domain-specific_programming_language")) that compiles it to native machine code at _compile-time_ of its host language. This is not possible in C. 

* etc. .. there are thousands of examples


If you do not understand the "point of" these high-level features then you do not understand them deeply, and you cannot judge whether they would improve ones productivity (they will when working with high-level, complex, or abstract tasks and things).

---

### Post by Wybiral on 2007-04-01
Yeah, but that is almost 100% for lisp... And I never said anything about C being capable of lisp functionality. I said python.

You don't NEED lambdas. I'm certain there are equally as efficient ways without them.

> 
(+ 10 (if t    ;; t means `true'.
          2    ;; The then-part of the if; 2 is returned.
          3))  ;; The else-part of the if; 3 is returned.
=> 12


(+ 10 (if nil  ;; nil means `false'.
          2    ;; The then-part of the if; 2 is returned.
          3))  ;; The else-part of the if; 3 is returned.
=> 13

Not possible in C?
```

int main()
{
   long x;
   long t = 10;

   x = 10 + (t?2:3);
   printf("%i\n", x);

   x = 10 + (0?2:3);
   printf("%i\n", x);

}

```

Dynamic typing... You CAN live without this. Static typing also makes for more documented code.

Closures... Function pointers (cast them to void* if you have to)

Code-is-data... CODE IS DATA. Learn some assembly if you disagree. Yes, I can use data as code.

I can alter my runtime code if need be... Once again... Code IS data, even in C.

But, like I said... Those statements were about *python*. Not lisp... Try doing half of those lispy things in python.

EDIT:

It was dumb to even make that statement (didn't I say it would explode into flames?)
So, lets leave this be and leave it clean for the people who actually want to post relative posts?

---

### Post by lnostdal on 2007-04-01
ternary-if: ah, forgot about that .. so stuff this will work:

```

#include <stdio.h>

int result = 0;

void someSideEffect()
{
  result = 1234;
}

int getResult()
{
  return result;
}


int main()
{
  int x = (1 ? someSideEffect(),getResult() : 3);
  printf("%d\n", x);
  return 0;
}

```
==> 1234

etc.  well, try doing it with `do', `while' and `switch' ..etc. .. or try adding a new conditional construct entirely -- like for instance a `dotimes'.

typing: we're not talking about what we can live without, but what is more productive .. this _is_ more productive when working with non-trivial stuff that requires explorative programming ...static typing just gets in the way here

closures: ..are not function pointers .. not even close. :)

code-is-data: that is not what i'm talking about .. not at all

alter runtime: just plain no - this is not wait i'm talking about

python has a lot of these things too .. HLLs in general .. i only use lisp as an example

---

### Post by pmasiar on 2007-04-01
> **Wybiral said:**
> And I never said anything about C being capable of lisp functionality. I said python.

Syntax is deceiving. Python is closer to Lisp than C, if you want that functionality. That's the whole beauty of Python: you can learn basic programming like C (only simpler syntax) and when are you ready, you can go on whole new level of programming using dynamic Lisp tricks.  Python has map, lambda, and [closure](http://www-128.ibm.com/developerworks/library/l-prog2.html). BTW closure is much more than function pointer: it "closes over" current values of an outside variable. Pythonic way is to set it as optional parameter with default value. Google will find you plenty of examples.

> You don't NEED lambdas. I'm certain there are equally as efficient ways without them....Dynamic typing... You CAN live without this.

You are funny. You are like deaf man who learned to read lips and explains that you don't need be able to listen - you CAN go around without.

Your thinking is in terms of assembler and C. Obviously you do not need any higher functions and do not see how you can use them. As they say, real programmer can program fortran code in any language. :-)

> Yes, I can use data as code....

Like in Lisp, also in Python I can put together a string and execute it. Doing this is *much* harder in C. 

> Those statements were about *python*. Not lisp... Try doing half of those lispy things in python.

Most of Lisp tricks have obvious Python equivalent - only thing you cannot do is complicated anonymous functions. Python's lambda is simpler than Lisp's - can have only simple expressions.

---

### Post by pmasiar on 2007-04-01
I almost forgot about this one: Wybiral asked very good question:
> **Wybiral said:**
> But by the time you're done programming the project... Having to do tests to find bottlenecks... Then reimplementing those parts in C... Couldn't you have just written it in C and had the same "speed to market"?

Don't guess: measure.

HLL gives you possibility to try couple different ways implementing solution, test which one is quicker. 

With C, you still need to write tests and make sure you are not doing something stupid. You just have to write all this (including tests) in lower-level language. Without testing and measuring, you just *hope* your C implementation is efficient.

That said, OP expressed preference for C and all this discussion is just  for amusement and maybe education of a random passer-by.... :-(

---

### Post by Wybiral on 2007-04-01
> **pmasiar said:**
> I almost forgot about this one: Wybiral asked very good question:


Don't guess: measure.

HLL gives you possibility to try couple different ways implementing solution, test which one is quicker. 

With C, you still need to write tests and make sure you are not doing something stupid. You just have to write all this (including tests) in lower-level language. Without testing and measuring, you just *hope* your C implementation is efficient.

That said, OP expressed preference for C and all this discussion is just  for amusement and maybe education of a random passer-by.... :-(

That was part of my original point really... People who stay in HLL and don't know anything about the low level they are built upon have no idea how to write efficient code. The ONLY way you can learn this is to learn about the low level parts.

If you have a good enough understanding of assembly and how your C compiler works... You shouldn't have to guess, you already know when something isn't going to compile efficiently.

I realize that HLL are useful and that yes... In a number of cases they will increase your productivity since they have so much built in functionality. But they are not the cure-all for productivity. Anyone with enough comfort and knowledge of the language they use is capable of being productive, especially after you begin to build collections of code that can be reused and libraries that you can just link to whenever you need a certain functionality.

Off the bat... Python is a more productive language. But once you've because comfortable with your native language, you become much more efficient. There comes a point when I would say that a C programmer is as efficient as a python programmer after they find their niche.

EDIT:

You guys are bringing up points in the fashion of "yeah, but can the oil painter create a rotating 3d model???"

No... He cannot. He is a painter and has other ways of creating art. His goal is not to create a 3d model, so he does not paint pictures which require them.

Your "can C do this and this" is silly, because they are different languages. C doesn't have HLL features, and doesn't need them. C programmers just don't write software where they NEED a HLL feature. It's that simple.

---

