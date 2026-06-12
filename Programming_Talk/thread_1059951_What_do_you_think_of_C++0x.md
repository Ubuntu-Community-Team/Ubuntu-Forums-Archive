---
title: "What do you think of C++0x?"
date: 2009-02-04
forum: Programming Talk
---

### Post by MadMan2k on 2009-02-04
I used to think of C++ as a really messy language, and recently I had to write a small project in C++ which I did cursing - but then I discovered the C++0x support in GCC and suddenly C++ became a usable language for me, because of:

* proper array data type, that knows its size
* initialisation of build-in collector types
* type inference, which saves a lot of typing sometimes
* proper smartpointers which, relieve me of manual memory management
* heavily *boosted* STL, which is even useful now

when the foreach loop support arrives, only the header files will be left for me to bitch about...

---

### Post by CptPicard on 2009-02-04
I hear it's got closures, so that is a positive. Otherwise for what I've seen is worth and what I've heard from other sources, it's "more of the same"... just more detail to worry about, not less. My eyes are on complete rewrites such as D...

---

### Post by howlingmadhowie on 2009-02-04
interesting link in your sig, CptPicard---the first i've heard of this.

about C++, people tell me it gets nasty when you get into details. linus torvalds has neither a high opinion of the language nor of the people who use it ([linky]("http://article.gmane.org/gmane.comp.version-control.git/57918")). personally i like C, but i must admit that a few things tend to confuse (such as the rather strange usage of the word static to mean two different things and '*' being used to declare a pointer and also dereference it). i find that D looks interesting, as does objective-C.

as it is, i'm going through a phase of preferring dynamically typed languages. static typing is basically a way of commenting your code for you and the compiler. it also tends to result in redundancy, including such horrors as the following:

```

ArrayIndexOutOfBoundsException myArrayIndexOutOfBoundsException = new ArrayIndexOutOfBoundsException(); /* I hope you're reading this on a wide screen */

```

---

### Post by MadMan2k on 2009-02-04
> **CptPicard said:**
> I hear it's got closures, so that is a positive. Otherwise for what I've seen is worth and what I've heard from other sources, it's "more of the same"... just more detail to worry about, not less. My eyes are on complete rewrites such as D...
actually with C++0x one will get Reference Counted Garbage Collection in the STL, so this alone is much less work when used properly.
Then there will be better integration of collection types and type inference in the language, which raises the abstraction level even more.

So in my opinion C++ is doing the right things here...

As of D; I was also excited about it in the first place, but practically it is obsolete.
There is already C/C++ for the target area of D, and they are not going to go away anytime soon. Then D lately lost momentum - the GCC frontend is outdated and there are no big players using D.
On the other hand you have the matured C++ stack; highly optimized compilers and many third-party libraries...

---

### Post by CptPicard on 2009-02-04
> **howlingmadhowie said:**
> linus torvalds has neither a high opinion of the language nor of the people who use it

The problem with Torvalds is that I get the impression he doesn't quite understand higher-level languages in general, being a kernel hacker...

> personally i like C, but i must admit that a few things tend to confuse (such as the rather strange usage of the word static to mean two different things and '*' being used to declare a pointer and also dereference it).

I also tend to be of the opinion that some lightweight virtual-function stuff on top of structs would be quite sufficient for C as far as OOP goes.

The pointer-declaration and dereferencing thing makes perfect sense once you see it this way: when you have "int *p", you need to read it as "the dereferenced p is an int". So it's "int (*p)", and it declares the pointed-to type. It is not "(int*) p"... IMO trying to see a "pointer type" there is much less fruitful.

---

### Post by eye208 on 2009-02-04
> **CptPicard said:**
> The problem with Torvalds is that I get the impression he doesn't quite understand higher-level languages in general, being a kernel hacker...
[http://yosefk.com/c++fqa/defective.html](http://yosefk.com/c++fqa/defective.html)

---

### Post by CptPicard on 2009-02-04
> **eye208 said:**
> [http://yosefk.com/c++fqa/defective.html](http://yosefk.com/c++fqa/defective.html)

Yes yes... I know it and pretty much agree with it.

---

### Post by MadMan2k on 2009-02-04
> **eye208 said:**
> [http://yosefk.com/c++fqa/defective.html](http://yosefk.com/c++fqa/defective.html)
well this is (itentionally) a exaggregation for c++ haters. Actually one can write pretty clean C++ code when using only c++ constructs.

Sure the language itself is not clean and there is much duplication, simply because of the fact that C++ emerged out of C and therefore there are C and C++ constructs available.

I have written a small article, where I show some areas where C++0x is an improvement: [http://www.rojtberg.net/199/c-becoming-usable/](http://www.rojtberg.net/199/c-becoming-usable/)

---

### Post by Simian Man on 2009-02-04
People say that C++ is an octopus created by nailing extra legs onto a dog.  I think this can be extended that C++0x is a centipede created by nailing even more legs onto said octopus.

The amount of details and complexity of the language is just too much to fit in my mind comfortably at once.  Most C++ programmers either focus on the low-level stuff (C with classes) or the high-level stuff (boost users).  However do matter how much you try to stick with a subset of the language, I have found that some other part will eventually bite you in the ***.

And I have used C++ for ~6 years and taught it at the university level (not that that says much based on some professors I have had).

For my part I will stick with the elegance of C when I want to think at a low level and a language like Python or Ocaml when I don't.

---

### Post by eye208 on 2009-02-05
> **MadMan2k said:**
> well this is (itentionally) a exaggregation for c++ haters. Actually one can write pretty clean C++ code when using only c++ constructs.
I agree.

I only pasted that URL to point out that Torvalds' aversion against C++ is not without reason. However, the assumption that he doesn't like or understand high-level languages is nonsense. In fact he is well known for being a fan of Microsoft Visual Basic.

By the way, his comment about C++ was not related to kernel hacking but to Git, his source code versioning system. He wrote most of it in plain C, and he did so in an amazingly short period of time. Those who question his skills or his ability to understand abstract concepts should at least try to prove that his language choice was wrong. I judge programmers by their achievements, and no one can dispute that Torvalds has achieved a lot. On the other hand, I don't know who CptPicard is and what he has achieved. All I can see here is talk, and talk is cheap.

---

### Post by ajackson on 2009-02-05
> **eye208 said:**
> I judge programmers by their achievements, and no one can dispute that Torvalds has achieved a lot.
There is no disputing that Linus has achieved a lot, doesn't necessarily make him a nice person (I'm not saying he isn't as I don't personally know him). He seems a man of strong opinion but a bit short in the tact department at times.

> On the other hand, I don't know who CptPicard is and what he has achieved. All I can see here is talk, and talk is cheap.
Pot, Kettle, Kettle, Pot.

C++ is a strange language, it tried and partially succeeded in making C more OO but in doing so it seemed to become a bit of a half and half entity, not quite getting it right. C++0x is more or less C++ with a bit of spit and polish. The fact that Java and C# are stealing the OO thunder from C++, in my opinion, means that C++ is in decline. Sure there are still a lot of applications written in it so it will live on but I think it's dropping down the pecking order in terms of language choice for new stuff (assuming the developers in question know various languages, if C++ is all you know then you would choose that).

---

### Post by CptPicard on 2009-02-05
> **eye208 said:**
> However, the assumption that he doesn't like or understand high-level languages is nonsense. In fact he is well known for being a fan of Microsoft Visual Basic.

Which is proof positive he does not quite understand high-level languages... or that alternatively he makes statements like that tongue in cheek. 

> He wrote most of it in plain C, and he did so in an amazingly short period of time.

So? Knowing C is not such an achievement to begin with, and we can deduce from this that he likes busy-work...

> Those who question his skills or his ability to understand abstract concepts should at least try to prove that his language choice was wrong.

He could have written git at least "more easily" in some other language. From my own perspective, *I* am perfectly capable of writing anything I want to write in C as well (as are most other competent people), but as I am capable of choosing, the choice ends up being not C most of the time. It's not C that is blessing anything there in the git case, it's just the fact that there is a competent guy in general who *can* use C as a choice...

> 
 I judge programmers by their achievements, and no one can dispute that Torvalds has achieved a lot. On the other hand, I don't know who CptPicard is and what he has achieved. All I can see here is talk, and talk is cheap.

Torvalds has written a kernel. A lot of other people have written kernels. Even more people have written a lot of really interesting stuff that are not kernels. Kernels are not special in that regard. As far as programming competence goes, we should look at RMS for an interesting point of comparison -- Emacs is essentially a Lisp machine after all...

I judge programming languages as programming languages. But as they are human tools it is also interesting to see why some things have been brought into different programming languages (for example, the lambda expression is theoretically *the* fundamental construct), and it is equally interesting to read what insightful, smart people have to say about those reasons.

It should be noted that very few "authorities" take your position of apparently complete denial of anything worthwhile outside C. To claim something like that seems totally unintellectual, and me for one would have quit programming as "too dull" a decade ago if this were the case.

It is not as if I personally were some sort of authority on the matter, of course -- I can just point out that C is essentially a subset of a lot of stuff, and to argue that it is not seems nonsense from the outset, regardless of anything else -- anybody's relative merits and all that including.

Personally, I could not be a one man company if I didn't have HLLs in my toolkit, and a lot of my lower-level coding is very much informed by approaches learned in HLLs even though the abstractions may not be available (too bad you can't really "write a library" for proper higher-order and anonymous functions). And yeah, if this ever becomes a two-man company, I can promise you that your attitude to things would drop you off the candidate list in no time, regardless of your C skills. :)

---

### Post by scourge on 2009-02-05
> **eye208 said:**
> In fact he is well known for being a fan of Microsoft Visual Basic.

This is what he said:
[QUOTE=Linus]I personally believe that Visual Basic did more for programming than Object-Oriented Languages did. Yet people laugh at VB and say it’s a bad language, and they’ve been talking about OO languages for decades. And no, Visual Basic wasn’t a great language, but I think the easy database interfaces in VB were fundamentally more important.[/QUOTE]

I think it's a bit of a stretch to say that Linus is a fan of VB (the language). He just liked the database bindings and the easy-to-use graphical form editor. And he really seems to dislike OOP.

He also said:
[QUOTE=Linus]Thus, starting with Linux 3.0 (to be released hopefully by next summer), the kernel will be completely rewritten in the easy-to-use Visual Basic language. This will eliminate all issues involving buffer overruns, as well as streamlining porting of Windows programs to Linux, since Microsoft (who will now assume ownership of Linux) assure me that Windows is written entirely in VB as well.[/QUOTE]

This was an April Fools joke, obviously.

---

### Post by eye208 on 2009-02-05
> **scourge said:**
> I think it's a bit of a stretch to say that Linus is a fan of VB (the language).
It's perfectly possible to be a fan of a language without actually using the language. LISP fans are a prime example.

---

### Post by ajackson on 2009-02-05
It's perfectly possible to dislike a language but recognise it's good bits.

---

### Post by eye208 on 2009-02-05
> **CptPicard said:**
> Knowing C is not such an achievement to begin with
But writing Git in C certainly is. After all...

> He could have written git at least "more easily" in some other language.
Actually he couldn't, because he's a kernel hacker and doesn't understand higher-level languages.

You can see there's a contradiction here. You are switching back and forth between two positions: C is too simple, C is too difficult. It seems you can't make up your mind on this.

Fact is, he wrote Git, and the "competent hackers" aka Lispers did not. This is the difference between theory and reality: The HLL fans keep marveling about the superiority of high-level languages and how these are much more intellectually challenging, but they rarely produce tangible results. It's a bit like Linux vs. The Hurd.

---

### Post by Gordon Bennett on 2009-02-05
> **eye208 said:**
> But writing Git in C certainly is. After all...


Actually he couldn't, because he's a kernel hacker and doesn't understand higher-level languages.

You can see there's a contradiction here. You are switching back and forth between two positions: C is too simple, C is too difficult. It seems you can't make up your mind on this.

Fact is, he wrote Git, and the "competent hackers" aka Lispers did not. This is the difference between theory and reality: The HLL fans keep marveling about the superiority of high-level languages and how these are much more intellectually challenging, but they rarely produce tangible results. It's a bit like Linux vs. The Hurd.


Indeed - one thing most people miss is that you don't need an 'OO' language to write to OO concepts.  After all, everything gets compiled down to raw CPU instructions/assembler, which aren't considered 'OO' in any form.

Some time ago, I worked at a company designing kernels, cpu's and all that balls-out-in-the-air type of thing - where it was well known that I intensely disliked C++ and all its acolytes.
Then a programmer I hardly knew approached me one day and said "look, I heard what your opinion is of C++.  I want to say why I chose it - I studied biology and I chose C++ because (analogy) I can conceptually work on the bacteria cells in the petri dish moving about, without having to spend most of my time building those cells or having to understand why they work."
From that point on, I understood where he and similar people were coming from, and that's cool.  Pre-heated, pre-rolled OO removes having to think about certain things and lets people get on with getting that paycheck.

And that thinking extends to other things.  When I first met a friend (who's on the BSD kernel team) he was very surprised to see me actively avoid commandline development; he had the impression that because I was designing logic-gates, assembler code and what-have-you at the time, that I'd be knee-deep in custom-made scripts etc.  "No way!"  I told him, "Why spend 10 hours on that when I can do it in 10 minutes using a GUI?"  He understood :)  Same thing, different flavour.

At the end of the day, you pick what suits you and those around you best.

For me, because of my background, C++ and its myriad revisions is fundamentally flawed in concept and execution *for the things I do* - that and the sinking feeling that if it were called E++ it wouldn't have survived 5 minutes after release ;)

But that is due to my own way of thinking how a program is written - Linus' outburst r.e. Git, was IMHO justified; it was quite apparent the dude suggesting the C++ conversion had no concept of the whole design.  It's like an evangelist telling you that their religion is better, without first asking you what yours is about.

If C++0x works for you - great; if you find yourself wanting, or if the language just doesn't float your boat, switch!  Just don't do it because they tell you it's the best thing - that path is full of compromise.

---

### Post by Simian Man on 2009-02-05
> **CptPicard said:**
> Which is proof positive he does not quite understand high-level languages... or that alternatively he makes statements like that tongue in cheek.

I am certain that he understands high-level languages because the design of Git itself is very high-level.  In fact I would argue that C programmers often end up understanding high level design better than most since they have to implement the abstractions themselves.  For example I gained more insight into object-oriented programming working with C and GTK than I did in Java.

> **CptPicard said:**
> 
He could have written git at least "more easily" in some other language. From my own perspective, *I* am perfectly capable of writing anything I want to write in C as well (as are most other competent people), but as I am capable of choosing, the choice ends up being not C most of the time. It's not C that is blessing anything there in the git case, it's just the fact that there is a competent guy in general who *can* use C as a choice...

Git is designed to be as efficient and streamlined as possible.  Linus obviously is very good at optimizing C code so it is the only logical choice for him.  I can almost guarantee you that if you were to rewrite Git in common lisp it would fail in terms of speed.


> **CptPicard said:**
> 
Torvalds has written a kernel. A lot of other people have written kernels. Even more people have written a lot of really interesting stuff that are not kernels. Kernels are not special in that regard. As far as programming competence goes, we should look at RMS for an interesting point of comparison -- Emacs is essentially a Lisp machine after all...

Ah...no.  RMS did a lot for free software, and the GNU toolchain is easily one of the most important pieces of software we have, but he is not a great programmer.  Emacs was originally started by James Gosling.  And if a kernel is so pedestrian, why has RMS's Hurd been such an epic failure :).

> **CptPicard said:**
> 
I judge programming languages as programming languages. But as they are human tools it is also interesting to see why some things have been brought into different programming languages (for example, the lambda expression is theoretically *the* fundamental construct), and it is equally interesting to read what insightful, smart people have to say about those reasons.

No the lambda expression is ***a*** fundamental construct.  It is the underpinnings of functional languages like Haskell and, to a lesser extent, Lisp.  The Turing machine is an equivalent construct that provides the theory behind languages like C.  If you don't like that that's fine, but don't get elitist.

In my experience, language theorists tend not to get a whole lot done.  Just look at the body of work that is done in plain, practical languages like C.  Then compare that to the body of work done in Lisp.  Even most Lisp evangelists readily admit they never use it.  Why is that?  If it is so great, why is it rarely used for real projects?

I will finish by promoting my favorite language, Ocaml.  It has most of the functional aspects of Lisp (and then some), along with practical procedural and object-oriented support.  It also, unlike Lisp, has a very stable, efficient implementation that makes it good for actual work.  It also has a simple FFI to C, my *other* favorite language.

---

### Post by dribeas on 2009-02-05
> **MadMan2k said:**
> 
when the foreach loop support arrives, only the header files will be left for me to bitch about...

On the features you will still miss:

There is a BOOST_FOREACH in boost libraries that behaves as you probably expect:

```
std::vector<std::string> v; // fill in
BOOST_FOREACH( std::string & s, v )
{
   std::cout << s << std::endl;
}
```

You don't want to read the code generated by the macro... :)

Modules are due in TR1 probably in about three years. That will remove the dependency on header files, but as agreement did not seem to be possible for C++0x they postponed it for a later time.

On the features you praise:

std::vector has been around for a rather long time and it has any and all features you would want from an array, including ::size().

The smart pointers have been around (at least most of them) for a long time already in boost libraries, which, not being part of the standard are a source of new standard features.

Garbage collection is a feature you comment on a later post... well, I don't quite see it as an advantage. Smart pointers are a better and more complete solution. They not only take care of memory, but also other resources through RAII, which no GC language that I know have. Ever wondered why C++ try blocks do not have a finally clause? Ever wondered why Java/C# need it?

On the C++ FQA:

Really, I started reading it. I could start commenting on the horrors it describes but I lack the energy. I do have some experience in C++ and reading what the FQA explains just proves the lack of knowledge of the reader. Of course, I do agree that C++ is not a simple or easy language, but I would relate the writer with the set of people that consider languages as pure syntax, and try to fit their experience with one language with the syntax and compilers of another.

---

### Post by Gordon Bennett on 2009-02-05
> **dribeas said:**
> I do agree that C++ is not a simple or easy language, but I would relate the writer with the set of people that consider languages as pure syntax, and try to fit their experience with one language with the syntax and compilers of another.

That's partly because C++ has the letter 'C' in it.

---

### Post by Wybiral on 2009-02-05
> **eye208 said:**
> It's perfectly possible to be a fan of a language without actually using the language. LISP fans are a prime example.

What does that mean? I use lisp, pretty frequently too (not as often as Python, but still pretty often). Sure, lisp is a great syntax to explore theory in, but there are also practical implementations of it (such as clojure).

I suggest you go read some of Paul Graham's essays or something and get back to us. While you're out, you might as well pick up some Abelson and Sussman (it seems like you would really benefit from this one).

---

### Post by Wybiral on 2009-02-05
> **eye208 said:**
> You can see there's a contradiction here. You are switching back and forth between two positions: C is too simple, C is too difficult. It seems you can't make up your mind on this.

C is a simple language, in the same sense that brainfuck and assembly are simple (typically having very few native constructs, and the ones they have are too simple to easily combine into higher-level constructs).

So while they may be simple to learn the basics of, actually writing large applications in them tends to be very difficult to manage and requires much more work because you have to personally code the constructs that should be native to the language.

---

### Post by CptPicard on 2009-02-05
> **Wybiral said:**
> 
I suggest you go read some of Paul Graham's essays or something and get back to us. While you're out, you might as well pick up some Abelson and Sussman (it seems like you would really benefit from this one).

What, you're actually suggesting that he try read and understand something of the motivations and ideas behind languages like Lisp? But but... that could mean that he couldn't just slap us as stupid fanboys anymore! :o

I am afraid these "pro-ignorance argument" guys (Lster, Shining Arcanine, billijoe... now eye208) can't and don't want to be made actually understand the point, and being dragged along arguing them can be a fool's errand (it's actually a trolling/obstruction tactic): They can demand endless amounts of "proof" from you, while not having any kind of requirements to demonstrate understanding of what is being discussed. Instead, they can just summarily ignore everything and pull you along and laugh at the keyboard at your efforts while eating popcorn :popcorn:

The argument is so totally *weird* the mind boggles. Here we have programmer A who knows language X. Then there is programmer B who knows languages X, Y and Z, which, let's say, are substantially different in paradigms (think imperative, functional, logic programming, say). 

Ok. So here comes programmer B, saying "hey, there is genuinely cool stuff that you can do in Y and Z you can't do in X (without writing an interpreter for Y and Z), and it has shaped a lot of stuff in my thinking! Check that stuff out!"

So what does A do? Well, he claims that *because he knows X*, B is wrong, unless he is able to "prove" things A is unwilling to consider to begin with. And even then, he is probably still wrong and seeing things. :p

Now, for example, it would be interesting to hear the views of a well-versed Lisper who actually feels the language has no merit, but I have not yet met anyone like that. I do hear views like that from people who just see "lots of weird parenthesis", but frankly, their views do not count, as it is not an informed opinion. The blub paradox really does exist :)

But anyway, short of getting lobotomized, it's pretty hard to "unlearn" the things I've picked up from all of the languages I've hacked in (the functional ones in particular), and it is really hard to see myself "evolving" as a programmer back in the "restricted to C" direction. It's pretty obvious in which direction the arrow of increasing knowledge is pointing in my life and career... :)

---

### Post by PythonPower on 2009-02-05
I am Lster. And, contrary to my previous opinion, I do like functional programming a lot.

In the last few months I've really got to like the way things can be defined. I'm not purist in the sense that I only use strictly functional programming but all the same I accept I judged functional programming prematurely. It fits, like I believe you once said, very nicely with mathematics.

It's funny to see people still talking about me. I'm hoping we can get on better this time round. I assure there are no hard feelings especially now I understand your opinions better. :)

---

### Post by CptPicard on 2009-02-05
Man, now THAT is an improvement from the time you wanted me banned.. something good obviously does sometimes come from this thankless job of enlightening the masses ;)

Well ok... sure, peace. No hard feelings here, either -- I actually suspected that being the smart guy you are, you would eventually get it.

(Your "what is a closure" is a bit of a classic around here you know.. ;) )

---

### Post by PythonPower on 2009-02-05
Believe it or not, I did actually know what a closure was at that time... I just didn't know it was called a closure.

A lot has changed - many people have left it seems. Are the ol' programming challenges still going strong? :p

---

### Post by CptPicard on 2009-02-05
Actually I am really glad to have you back, made my day... :)


> **PythonPower said:**
> 
A lot has changed - many people have left it seems. Are the ol' programming challenges still going strong? :p

IMO the quality of the place has been tanking ... the challenges are dead, LaRoza is banned(!), pmasiar is banned (but not permanently, but he is busy)... wybiral is busy.. I am busy...

---

### Post by PythonPower on 2009-02-05
Ah... And such is life.

I'm pretty busy with things generally, although it's downhill for the rest of my A-levels. But it's nice to say 'hi' again.

---

### Post by dribeas on 2009-02-05
> **Gordon Bennett said:**
> That's partly because C++ has the letter 'C' in it.

So does C#. Now, pun intended, so does Cobol, or sCheme :P

---

### Post by eye208 on 2009-02-06
> **CptPicard said:**
> The argument is so totally *weird* the mind boggles. Here we have programmer A who knows language X. Then there is programmer B who knows languages X, Y and Z, which, let's say, are substantially different in paradigms (think imperative, functional, logic programming, say). 

Ok. So here comes programmer B, saying "hey, there is genuinely cool stuff that you can do in Y and Z you can't do in X (without writing an interpreter for Y and Z), and it has shaped a lot of stuff in my thinking! Check that stuff out!"
This is the story from my point of view:

Programmer A has been programming computers since 1987. For 12 years he has been working full time as a software developer for a company with ~600 employees. He has been working on applications used by ~11000 clients, developed by a team of 20+ people. He has been using quite a few languages but came to the conclusion that language X works best for most projects. Market surveys show that most people in the business agree with him.

Programmer B is a CS student who considers himself smarter than Linus Torvalds, yet has achieved nothing so far. B thinks he can teach A. He thinks that smart people always prefer languages Y and Z by default. Therefore, people who prefer X cannot be smart. B gets engaged in elitist talk, yet fails to prove his point. In fact he gets offended by A asking him to prove his expertise. Why would smart people have to prove anything?

A recognizes the pattern. He knows that people like B are the reason why job interviews exist. ;)

---

### Post by ajackson on 2009-02-06
> **eye208 said:**
> Programmer A has been programming computers since 1987. For 12 years he has been working full time as a software developer for a company with ~600 employees. He has been working on applications used by ~11000 clients, developed by a team of 20+ people. He has been using quite a few languages but came to the conclusion that language X works best for most projects. Market surveys show that most people in the business agree with him.

Programmer B is a CS student who considers himself smarter than Linus Torvalds, yet has achieved nothing so far. B thinks he can teach A. He thinks that smart people always prefer languages Y and Z by default. Therefore, people who prefer X cannot be smart. B gets engaged in elitist talk, yet fails to prove his point. In fact he gets offended by A asking him to prove his expertise. Why would smart people have to prove anything?
Except you, sorry I mean *A*, is being the most elitist. I know it is just you trolling (again) but any proof to back up the "market surveys" proving that C, sorry *X*, works best for most projects?

Coming to the conclusion that people who disagree with you, sorry *A* must stop doing that, are just CS students shows how elitist you, damn sorry *A*, is. But then us mere mortals have to take your, sorry *A*'s, words that he knows everything and thus doesn't have to prove his expertise.

All I can say is 12 years doesn't make you, sorry *A*, the most experienced developer in the world, for all we know the other 19 developers could be carrying you, damn sorry *A*. Size of IT department and number of end users doesn't mean that the developers are wonderful or the app is the best in the world, take Windows ME for example.

> A recognizes the pattern. He knows that people like B are the reason why job interviews exist. ;)
While the rest of the world knows that *A* has delusions of grandeur.

---

### Post by eye208 on 2009-02-06
> **ajackson said:**
> All I can say is 12 years doesn't make you, sorry *A*, the most experienced developer in the world
A never claimed to be smarter than Linus. But B did. Now A wants to see some of the spectacular results that B achieved. It's about credibility. Maybe you should look up the definition of "troll". B matches it quite nicely. ;)

---

### Post by ajackson on 2009-02-06
> **eye208 said:**
> It's about credibility.
Of which you have none.

> Maybe you should look up the definition of "troll".
I did it said see eye208.

---

### Post by CptPicard on 2009-02-06
To cut this crap short where discussion is directed more at person than at issues, actually, this B here has been programming computers since 1986, has an algorithmics-heavy CS Master's (from same university as Linus), has been a full-time geek for the past decade both in academics and development sense, and probably most importantly during past few years of consulting work developed both the math and the computationally intensive tools for running the numbers for a couple of interesting betting markets (the less intellectually interesting half is the database/website/back-office side of the business). The profits pay the bills for quite a number of people.

The next step is to investigate implementing the algorithms in Haskell, and possible other strategies to perhaps make use of a cluster in case we're expanding to a game where the solution-space is some 10 times larger.

So, why, yeah, I do consider myself pretty credible, while there is of course nothing to establish anything here where most everyone is just a random guy on the internet.

But, I am not really interested in comparing sizes in this discussion, as I believe getting personal is not interesting. The language-matters are not developer-specific, but it is interesting how apparently working in industry does make one get rather rigidly stuck in one's ways... 

And of course the entire counter-argument that argues that these points in "languages other than C do not exist", argued from a position of ignorance usually, is completely untenable. If you're not familiar with Y and Z, you can not meaningfully say anything about their additional benefits with regards to X. In particular, a CS undergrad with functional-programming exposure is going to have a far more valid view of FP than someone with 30 years of industry experience in (only) C.

And by the way, my first job-interview question will be to please explain the concept of the lambda expression, mention a couple of languages that make use of it, and give an example of some problem where you have made use of one. Should drop 90% of undesirables.

---

### Post by techmarks on 2009-02-06
.

---

### Post by CptPicard on 2009-02-06
.

---

### Post by techmarks on 2009-02-06
Sorry Picard...I came across so judgemental and harsh.  I don't like to be that way.

I hope I wasn't offensive.

I just say as long as people are using the best tool for their particular project that is what matters.

---

### Post by eye208 on 2009-02-06
> **CptPicard said:**
> The language-matters are not developer-specific, but it is interesting how apparently working in industry does make one get rather rigidly stuck in one's ways...
It happens automatically when you work in a large team. A prerequisite of successful teamwork is to split responsibilities among the members of the team. This is where OOP and static typing come in. As soon as a project grows beyond a particular size, there is no single person in the team who knows all the code. Static interfaces help the team members to work independently and without reading each other's code. And if something goes wrong, you can tell who is responsible.

Actually we are not a pure C shop. We use Java, C#, C/C++, Perl, PHP, and even COBOL.

However, this thread was about C++, and I don't think that Linus' aversion against C++ is due to a lack of understanding on his part. He does have some valid points, and he talked about them numerous times.

---

### Post by nvteighen on 2009-02-06
> **PythonPower said:**
> I am Lster. And, contrary to my previous opinion, I do like functional programming a lot.

In the last few months I've really got to like the way things can be defined. I'm not purist in the sense that I only use strictly functional programming but all the same I accept I judged functional programming prematurely. It fits, like I believe you once said, very nicely with mathematics.

It's funny to see people still talking about me. I'm hoping we can get on better this time round. I assure there are no hard feelings especially now I understand your opinions better. :)

Hey! Welcome back. :)

---

### Post by nvteighen on 2009-02-06
> **CptPicard said:**
> 
And by the way, my first job-interview question will be to please explain the concept of the lambda expression, mention a couple of languages that make use of it, and give an example of some problem where you have made use of one. Should drop 90% of undesirables.

1) It's a function-creating expression that creates new lexical bindings and capturing the free bindings used in the creation environment.

2) Common Lisp, Scheme, Clojure and all Lisp dialects. Haskell, Python, Perl, Javascript.

3) Look at FreeTruco to see the implementation of a pure-functional dealing system.

Ok, where's my job? :D

> **eye208 said:**
> This is where OOP and static typing come in. As soon as a project grows beyond a particular size, there is no single person in the team who knows all the code. Static interfaces help the team members to work independently and without reading each other's code. And if something goes wrong, you can tell who is responsible.

Oh no, not again... Please! The examples ajackson and I gave to you in the last thread were pretty clear why you're wrong. Static typing doesn't guarrantee anything and it's not critical to good teamwork.

If you can tell me the perfect usage of this interface, I'll surrender:
```

#ifndef GRAPH_H
#define GRAPH_H

#include <stdio.h>

typedef struct GRAPH_T graph_t;
typedef struct LIST_T list_t;

list_t *list_new(void);
void list_free(list_t *);
char list_set(list_t *, size_t, int *);
size_t list_get_size(list_t *);
int list_get_elem(list_t *, size_t);
size_t list_search(list_t *, int);

graph_t *graph_new(FILE *, list_t *);
void graph_free(graph_t *);

size_t graph_get_size(graph_t *);
char graph_get_queue(graph_t *, size_t);
void graph_set_queue(graph_t *, size_t, char);

char graph_is_edge(graph_t *, size_t, size_t);

#endif

```

The interface is real from some code of mine. You don't even know what is this supposed to do.

---

### Post by CptPicard on 2009-02-06
> **techmarks said:**
> Sorry Picard...I came across so judgemental and harsh.  I don't like to be that way.

Accepted. :)

> 
I just say as long as people are using the best tool for their particular project that is what matters.

Well, even if we chose that kind of completely subjective path, they still need to know to begin with what is the best possible tool, and if they don't know the difference, they can't judge that.

---

### Post by eye208 on 2009-02-06
> **nvteighen said:**
> Oh no, not again... Please! The examples ajackson and I gave to you in the last thread were pretty clear why you're wrong.
I don't think so. The last statement I made in the other thread is still valid: If your class implements a public interface, everyone will be able to use it without ever looking at your code or your documentation.

> Static typing doesn't guarrantee anything and it's not critical to good teamwork.
It's not critical, but it saves time. And in case of failure I could tell who messed up, because the interface works like a contract.

> If you can tell me the perfect usage of this interface, I'll surrender
Thanks to static typing I can tell that these are actually two classes, list and graph. But they don't implement any public interface I'm familiar with.

---

### Post by Sockerdrickan on 2009-02-06
I think it's an improvement but on the other hand, ++language_size

---

### Post by ajackson on 2009-02-06
> **eye208 said:**
> Thanks to static typing I can tell that these are actually two classes, list and graph. But they don't implement any public interface I'm familiar with.
Which proves nvteighen (and myself) right, thanks for doing that.

Care to explain

[QUOTE=eye208]Actually we are not a pure C shop. We use Java, C#, C/C++, Perl, PHP, and even COBOL.[/quote]

You work for morons since

[QUOTE=eye208]He has been using quite a few languages but came to the conclusion that language X works best for most projects. Market surveys show that most people in the business agree with him.[/quote]

Programmer *A* was you and language *X* is C, your own employer doesn't see it as the answer to everything.

Th-th-th-th-that's all folks.

---

### Post by nvteighen on 2009-02-06
> **eye208 said:**
> 
Thanks to static typing I can tell that these are actually two classes, list and graph. But they don't implement any public interface I'm familiar with.

Great... you know that just looking at the typedefs and the constructor-like names of *_new() and *_free().

But you don't know how to use it... you don't what the (int *) argument is supposed to be in list_set() and why I insist in returning (char) or (size_t). There static typing doesn't help you at all... and the difference with dynamic typing is zero.

---

### Post by eye208 on 2009-02-06
This is like pulling teeth...

> **ajackson said:**
> Which proves nvteighen (and myself) right, thanks for doing that.
No, it doesn't. You deliberately misrepresent my statement. This is what people call a straw man argument.

> Programmer *A* was you and language *X* is C, your own employer doesn't see it as the answer to everything.
I don't see it as an answer to everything either. But my employer sees LISP as an answer to nothing. And I fully agree. No contradiction here.

---

### Post by eye208 on 2009-02-06
> **nvteighen said:**
> Great... you know that just looking at the typedefs and the constructor-like names of *_new() and *_free().

But you don't know how to use it... you don't what the (int *) argument is supposed to be in list_set() and why I insist in returning (char) or (size_t). There static typing doesn't help you at all... and the difference with dynamic typing is zero.
I wonder why it's so hard for you to understand that simple statement:

If your class implements a public interface, everyone will be able to use it without ever looking at your code or your documentation.

Am I right or am I wrong? I think the answer is obvious.

Keep in mind we are talking about OOP here. The key is to make the implementation independent from the interface. For example, in OO design, you line out the object interfaces first, then you implement the server and client. The developer of the client never needs to look at the code of the guy who implements the server. And if new implementations/subclasses are added to the class tree later, they need not be documented because they implement an interface which is already known. The client doesn't even need to know that these subclasses exist.

The more accurately the interfaces are designed, the easier it will be to add extensions to the application. If you look around, you see lots of applications working like this. The plugin interface of your browser is a nice example. The Flash plugin simply implements the interface. Do the browser developers need documentation about the Flash plugin and its exported methods? No, they don't.

---

### Post by Wybiral on 2009-02-06
> **eye208 said:**
> But my employer sees LISP as an answer to nothing. And I fully agree. No contradiction here.

Yes, I'm sure that's how Paul Graham saw it when he sold Viaweb to yahoo for $45 million. But I'm sure your employer is smarter than that silly old Graham guy anyway.

And I'm sure those guys at Reddit would have got their site up in no time had they just been smart enough to use C instead of Common-Lisp.

Imagine the disappointment when the developers of [Jak and Daxter]("http://www.franz.com/success/customer_apps/animation_graphics/naughtydog.lhtml") found out they'd be stuck coding in Lisp!

I also heard Abelson and Sussman threw a dart at a list of languages to decide what to use when writing SICP (I mean, they're all Turing complete, it's not like it matters)

After all, Lisp is one of those languages that people like, but never actually use... Right?

---

### Post by ajackson on 2009-02-06
> **eye208 said:**
> This is like pulling teeth...
I hope you are better at dentistry than, well anything you've shown us so far :)

> You deliberately misrepresent my statement.
You mean the statement you made about being able to tell what a function did just by looking at it's definition? If so how have I misrepresented that based on the fact you didn't have a clue what the purpose of nvteighen's functions were?

> But my employer sees LISP as an answer to nothing.
When did I **ever** make a comment about LISP? I've never used it so I don't know what it is capable off, therefore I have no real opinion on it. Nice to see the confirmation that you are *A* and C is *X*.

---

### Post by PythonPower on 2009-02-06
[QUOTE=ajackson]I hope you are better at dentistry than, well anything you've shown us so far :)[/QUOTE]

Comments like that don't help.

---

### Post by CptPicard on 2009-02-06
> **PythonPower said:**
> Comments like that don't help.

It's like pulling teeth for him because his basic argument is just simply false ("C covers everything and rest is crutches and sugar") and he is simply unable to see it, as anything else outside of his scope is just simply beyond his experience. Pointing it out is just honesty.

Of course I admit that the benefit of having the discussion in the first place is thus questionable, but I've known some guys to actually eventually take the hint, so it's sometimes worth it. :)

---

### Post by PythonPower on 2009-02-06
I have no criticism of the argument, just the comment seems unnecessary. In general I don't feel there is much reception to others' arguments.

---

### Post by CptPicard on 2009-02-06
> **PythonPower said:**
> In general I don't feel there is much reception to others' arguments.

I am *very* receptive to interesting, new, constructive arguments and ideas. Aggressively restrictive arguments that essentially argue that those "others' arguments" do not exist beyond some X are what I consider to be complete nonsense from the outset. At least, they are very hard to prove.

Really -- arguing that the difference between "concepts in C" and "concepts in all programming languages taken together" is the empty set is a remarkably ambitious claim... and one that I am less and less inclined wasting my time on, except just saying it's simply wrong.

---

### Post by nvteighen on 2009-02-06
> **eye208 said:**
> 
If your class implements a public interface, everyone will be able to use it without ever looking at your code or your documentation.

If my class implemts a public interface, everyone will be able to use it without ever looking at my code. But the documentation is needed: if you have a header like my list_set(), what do you know about the (int *) argument apart from its type? Nothing... You don't know what it means, so you may just know by chance that you need a pointer-to-int, but not if its dereferenced value can be zero... or whether it behaives differently depending on sign.

Such things are outside the scope of current programming languages.

> 
Keep in mind we are talking about OOP here. The key is to make the implementation independent from the interface. For example, in OO design, you line out the object interfaces first, then you implement the server and client. The developer of the client never needs to look at the code of the guy who implements the server. And if new implementations/subclasses are added to the class tree later, they need not be documented because they implement an interface which is already known. The client doesn't even need to know that these subclasses exist.

The more accurately the interfaces are designed, the easier it will be to add extensions to the application. If you look around, you see lots of applications working like this. The plugin interface of your browser is a nice example. The Flash plugin simply implements the interface. Do the browser developers need documentation about the Flash plugin and its exported methods? No, they don't.

Ok, I agree: a good interface means you don't need to know what the implementation is. Look at PycTacToe at my sig and you'll see that I know how to do that. But you also will see I don't need any static typing for it and that the docstrings (of course, manually updated... as header files also are) are all I need to make people aware of how to use stuff... and you know that docstrings can be read using the doc() function, not reading the source code; if I just redistributed the Python byte-code (.pyc), they'd be able to use doc().

But what I discuss is that static typing is the only way to have sane OOP in teamwork or that static typing gives you the whole documentation about a certain function... That's absurd because static typing is just a type-checking not a meaning-checking technique: nothing prevents you to pass a wrong argument of the right type.

So, I attach you my graph library as a shared library. You already have the header, but it's impossible to use it without an API doc.

You're focused in making your point, but you're not following what I say.

---

### Post by eye208 on 2009-02-06
> **CptPicard said:**
> "C covers everything and rest is crutches and sugar"
I never said that. It's another straw man.

---

### Post by PythonPower on 2009-02-06
[quote=CptPicard]I am very receptive to interesting, new, constructive arguments and ideas. Aggressively restrictive arguments that essentially argue that those "others' arguments" do not exist beyond some X are what I consider to be complete nonsense from the outset. At least, they are very hard to prove.
[/quote]

I just mean: this topic isn't going anywhere. I won't be taking part since I don't see anyone gaining from anything.

---

### Post by CptPicard on 2009-02-06
> **eye208 said:**
> I never said that. It's another straw man.

Would be interested in seeing what exactly it is that you are claiming then. :)

> **PythonPower said:**
> I just mean: this topic isn't going anywhere. I won't be taking part since I don't see anyone gaining from anything.

It's good fun though :)

---

### Post by nvteighen on 2009-02-06
> **PythonPower said:**
> I just mean: this topic isn't going anywhere. I won't be taking part since I don't see anyone gaining from anything.
+1

Er... some mod action? Maybe this could be merged into the "Grand Discussion of Programming Thoughts" thread?

---

### Post by 123Mike on 2009-02-06
Or just go Java. Is faster than C++ in some cases.

---

### Post by MadMan2k on 2009-02-06
> **dribeas said:**
> 
You don't want to read the code generated by the macro... :)
yeah, thats why I would like until it is available at the right level in the stack, ie in the parser of g++.

> **dribeas said:**
> 
Modules are due in TR1 probably in about three years. That will remove the dependency on header files, but as agreement did not seem to be possible for C++0x they postponed it for a later time.
that sounds promising - do you have more informations on that?

> **dribeas said:**
> 
std::vector has been around for a rather long time and it has any and all features you would want from an array, including ::size().
except that it is not array, but an arraylist with some overhead. I dont know if this overhead is considerable at all, but having a "proper" array type, just seems better.

> **dribeas said:**
> 
The smart pointers have been around (at least most of them) for a long time already in boost libraries, which, not being part of the standard are a source of new standard features.
yeah, I know that almost all of the new c++0x features were already available through boost, but since boost is not API stable, they were not widely used. That was at least the reason the gtkmm people gave for not using it.

> **dribeas said:**
> 
Garbage collection is a feature you comment on a later post... well, I don't quite see it as an advantage. Smart pointers are a better and more complete solution. They not only take care of memory, but also other resources through RAII, which no GC language that I know have. Ever wondered why C++ try blocks do not have a finally clause? Ever wondered why Java/C# need it?
well I must admit that I am not a fan of RAII coming from python. But looking solely on the GC aspct, a speparate GC process has its advantage:
imagine you are doing a computation intensive loop with "new"ing local variables.
In a reference counted scenarion the memory will get released immediately at the end of the loop, slowing down the computation, while a real GC can postpone the freeing until the computation is done and then also defragment the memory, while it is at it.


@static vs. dynamic typing:
probably this discussion could be split out in a separate thread, but I doubt it will end there. Probably because it does not matter after all and is only a matter of taste ;)

---

