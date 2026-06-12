---
title: "Language transition."
date: 2007-12-23
forum: Recurring Discussions
---

### Post by slavik on 2007-12-23
Every time someone new to programming (who is interested in it) comes along and asks where to start. Of course, we start a flamewar of which language is best for beginners.

In this thread I would like to propose that we look at transitioning between two languages that are completely different in one particular feature set, memory management.

Personally, I think that C is a good starting language because it abstracts the system away a little bit but not enough where there is no machine (like Haskel, Scheme and some others do).

Those advocating that the beginner should start from a scripting programming language (Python, Perl, Ruby are the big 3 in this category). Once the beginner decides that he needs/wants to learn a language where there is no automatic memory management. How is that person supposed to learn to manage memory without getting fed up with C or C++ and just use the first language (s)he learned?

As for going from having to do memory management to it being automagic, I see this as a much simpler step as memory management becomes "one less thing to worry about."

---

### Post by CptPicard on 2007-12-23
> **slavik said:**
> Of course, we start a flamewar of which language is best for beginners.

Of course we do. That's what we're here for :-|

> 
Personally, I think that C is a good starting language because it abstracts the system away a little bit but not enough where there is no machine (like Haskel, Scheme and some others do).

Depends a bit on how you want to look at it. In Scheme you need to be machine-ishly mindful of your environments at least when you start using set!... but personally I think Scheme is a great tool at teaching computational abstraction from the starting point of the concept of computation as mathematical function evaluation. But of course I digress here...

> How is that person supposed to learn to manage memory without getting fed up with C or C++ and just use the first language (s)he learned?

By learning it. Seriously, malloc/free are just two more functions, there's nothing magical about them. Then you just need the concepts of stack and heap and there you go.

If the person is fed up enough to use the original language, good for him. He'll come back when he genuinely needs to manage his memory.

I don't code to manage memory. I code to get something done, and manage memory if I must.

>  I see this as a much simpler step as memory management becomes "one less thing to worry about."

... until the person got fed up of trying to learn to program because of memory management and segfaults before he got to that point.

I don't understand this "max immediate pain is good for you so you'll know how bad a place the world is, son... now go get the paddle" mentality.

---

### Post by ghostdog74 on 2007-12-23
why start this thread at all?

---

### Post by CptPicard on 2007-12-23
Because that's what we do, have flamewars on what sort of languages n00bs should start with. Duh. It's half the fun :)

---

### Post by LaRoza on 2007-12-23
I try to avoid flame wars, but usually recommend Python and C, in that order.

I am highly tempted to say "Start with C", but do not because of several issues. The first one is speed. Learning basic programming concepts with Python is much easier. You can use variables, conditions, loops, functions, and other universal concepts without worrying exactly what a "string" is to a processor.

One can start with Python, write trivial example programs until they understand the concepts, then they can (and should) get closer to the machine. 

C is perfect for this. It is a very useful and widely used language, and requires a bit more thought of how programs actualy work.

As for the GC of Python, that is a very good point. Learning how to manage memory is a vital part of programming, however, it is not immediately rewarding. I doubt anyone understood what good pointers were at first, and malloc is even more confusing at first.

No matter where one starts, one should strive to move on. Learning with training wheels (a GC) doesn't mean they will rely on it forever, and are incapable of learning otherwise.

C never really made sense to me, until I studied assembly. Then it made perfect sense. 

I also found studying Lisp to make me a better programmer in other languages, because of the new paradigm involved.

So for people setting out to learn, I highly recommend:

* Python, to get up to speed quickly and not be disappointed
* C, to understand what is going on, and to know what power one can have
* Lisp, to understand logic and to see imperative languages in a new light

(Note the languages are not in stone, I could have said Perl, Assembly, and Haskell, the concept is the same)

---

### Post by revanthedarth on 2007-12-23
C, then C++. I first learned actionscript and HTML. Then i learned C, and then C++. I'm head of the olimpiad team in my school, and I teach them only C (I'm thinking of teaching C++ too).

I was trying to learn Visual Basic too, but VB isn't just my type. C++ is everything for me, i can do what i think. It has all i want. Nothing less, but a bit more. Brainf#$k seems cool too, i'll try to learn it sometime, just for fun.

By the way, Assembly should be learned. I'm thinking of learning it to do some calculations faster, but it doesn't seem easy :) And it shouldn't be the first language to learn.

---

### Post by LaRoza on 2007-12-23
> **revanthedarth said:**
> 
By the way, Assembly should be learned. I'm thinking of learning it to do some calculations faster, but it doesn't seem easy :) And it shouldn't be the first language to learn.

If you don't know it, giving advice on it can be tricky.

It isn't difficult, and some think it should be the first language. I think that is only true if that person is already knowledgable about the inner workings of the hardware.

My wiki has a section on it, and a forum member here wrote a good tutorial (if incomplete) tutorial for it.

---

### Post by CptPicard on 2007-12-23
> **revanthedarth said:**
> I'm head of the olimpiad team in my school, and I teach them only C (I'm thinking of teaching C++ too).

Why?

Testing solutions to problems is so much quicker on something else. I like checking out different algorithms, and fast prototyping is so much more convenient on higher-level languages... and as algorithm choice dominates running time almost always, you even get a pretty good idea of the efficiency differentials.

If you're coaching other people for some kind of a competition, it's problem solution skills they're mostly testing, not bit-pushing skills.

> 
C++ is everything for me, i can do what i think. It has all i want. Nothing less, but a bit more.

Don't restrict your toolset like that... they're all Turing-complete, but some languages are a better choice sometimes than others.

> 
By the way, Assembly should be learned. I'm thinking of learning it to do some calculations faster, but it doesn't seem easy

Assembly is actually quite easy. It's probably worth "learning" up to the point that you know what it looks like and why it looks like the way it does, but modern compilers beat you most of the time in actually producing code, so you'd be hard pressed to come up with anything faster, unless it's some really specific trick with some particular fancy instruction.

---

### Post by revanthedarth on 2007-12-23
Well, i have to use C actually, because in Turkey, we use C/C++ in olimpiads. But first step of the olimpiads aren't about a programming language at all. I don't know pascal, but i can solve pascal problems, it's like that. It's about loops. (But the second exam is about programming, just like IOI)

And, pseudo-codes are easier to write, but if you want to make it a real code, you must be familiar with the language you use. 

Anyway, I'll try to learn Assembly, once I'm familiar with GLSL. Thanks for the support :)

And, I know C++ more than any language. That's why i love C++. I'm not saying it's the best language and nothing can be better, but it's doing the trick.

And, I'm teaching them combinations, permutations etc, all you need for the exam. But when i said "Only C", i meant no other languages.

---

### Post by ghostdog74 on 2007-12-23
@OP congrats, you started another worthless flame war.

---

### Post by samjh on 2007-12-23
My take on the whole C vs very-high-level-languages is this:

If the learner is serious about building their skills as a programmer, and is learning to program with the aim of obtaining well-rounded skills and solid grounding in computer science, then I will always recommend C.

But if the learner wants to program only as a hobby or to create application or web software only, nothing much else, then my advice will be Python/Ruby/etc.

Programming is a manual skill.  Software design is of a higher order, but the skills of a designer must be grounded on manual skills.  Developing software is like any form of engineering - from civil to environmental to materials engineering.  As someone who graduated from an engineering faculty, I don't know of ANY mechanical engineer who doesn't know how to perform basic welding, or fails in their understanding of dynamics; nor do I know of any civil engineer who cannot get their head around static structures, or mix concrete; and no materials engineer that I've come across lacks laboratory skills.  I know a lot of engineers who design and develop at higher levels of abstraction, and ALL of them know how to do the manual stuff amidst the dirt and grime.

You simply cannot become a skilled developer or designer of anything if your grounding in low-level skills are shaky or non-existent.  In my opinion, developing or designing software is the same: if you're serious about becoming skilled in creating software, you must know the low-level stuff.  (I will here pause to take exception to web pages and web applications, since they are more in the realm of multimedia production rather than software or computer systems engineering.)

Now some people will say a person can learn something like Python and obtain low-level programming skills later.  In my experience with programmers of varying backgrounds, I differ with that view.  Most programmers who cut their teeth in Assembly, Ada, C, C++, and Pascal, have no problems transitioning to higher-level languages like Java, Python, Perl, VB.NET, etc.  In fact, many gladly make the switch to fit project requirements.  However I have seen most programmers who first learnt Java, Perl, PHP, Haskell, and other higher-level languages unable to adapt to lower-level languages, or at the very least struggling to do so.  Your mileage may vary.  But in my view, it's much easier to develop the mental agility and discipline required for low-level programming by learning a low-level language first, than to develop those skills after molding their mindset by using less-strenous very high-level languages.  While very high-level languages are much more productive and easier to learn than lower-level languages, such ease has penalties for the learner: less discipline and less mental agility is required for those languages.  Relaxed coding habits, lack of discipline over data types and memory usage, poorly optimised algorithms, etc., are bad habits that I've encountered in the past from programmers with high-level-only backgrounds.

As I said, "your mileage may vary".  This is just my experience and my point of view on the matter.


PS: Some people here seem to throw the phrase "flame war" a little too much.  This thread is what we make it.  Start flaming, and this thread will become a flame war.  Let's just keep this rational and objective.

.

---

### Post by slavik on 2007-12-23
> **ghostdog74 said:**
> @OP congrats, you started another worthless flame war.
Thank you. I knew you'd appreciate it.

@LaRoza: but don't you think that going from a lower level language to a higher level language is easier than the otherway around?

@everyone else: this isn't about any particular languages, this is about going from higher level languages to lower level languages and vice versa.

---

### Post by LaRoza on 2007-12-23
> **slavik said:**
> 
@LaRoza: but don't you think that going from a lower level language to a higher level language is easier than the otherway around?


I am on the fence, so to speak. Learning C would make all other imperative languages easier to learn, however, C itself would take more time than Python (to learn basics). With Python, you can use the interactive prompt to try out a loop, or a function with no hassle, whereas in C, you often to reach a level  of a certain "critical knowledge" before actually having an idea what is going on.

---

### Post by popch on 2007-12-23
Just a few disconnected thoughts:

I rather recommend learning a higher level language first, before going on to lower level ones. But then, I also recommend learning how to design programs before learning how to code them. 

Those two questions are closely related. Program design deals with the 'structure' (the coarse layout) of the software to be built. Quite a few programming languages bring useful constructs out of the box which facilitate building software that way.

The question of the programming languages is very often given too much weight. Meaningful software development should be done within development environments which supply as much as the coding as possible. And there's much that is possible. This opinion does not apply to the development of snippets of code such as algorithms or proofs of concept, but to complete systems. It also does not apply to the process of learning a programming language.

I question the use of the singular (or of very small numbers) in this context. Most meaningful software projects need parts written to several separate environments, most likely to be done in different languages. Also, since not all languages are created equal, different projects may require different languages. I have done project work in Assembly language, Forth, Smalltalk, COBOL and Prolog, to name but a few, in most cases in combination with components in other languages. Since each of those language has (or used to have) its particular strengths, I would not dream of using every one for every job I did with those tools.

Lastly, the question of speed of execution is often (but not always) given too much weight.

The issues are most often seen as [LIST=1]
[*]compiled vs interpreted code
[*]generated vs hand coded series of instructions[/LIST]The compiled vs interpreted bit is obviously true in most cases. The influence on the perceived speed of the system is, however, very variable. Very many applications spend much time serving the GUI or reading or writing disk files. That code practically never is written in the (interpreted) language the application is written in, but it is compiled

In some instances, the programmer was able to improve the structure and algorithms because the higher level language used relieved him of other tasks. That's a trade off which not only saves on project duration but - surprisingly - on program execution time as well.

The other discussion centers on the point that a hand-coded sequence may run better than one generated by a compiler. If that has to become true, you must in most cases be either a very very good programmer or use a very poor or flawed compiler. There are, of course, exceptions, and in some cases you really can produce better code manually than by letting the compiler produce it for you.  In that case you make the best of several worlds by coding exactly those crucial 0.5% of the code manually and let the compiler of a high level language take care of the rest. Useful programming languages let you do that easily.

---

### Post by CptPicard on 2007-12-23
> **samjh said:**
> 
If the learner is serious about building their skills as a programmer, and is learning to program with the aim of obtaining well-rounded skills and solid grounding in computer science, then I will always recommend C.

I have a solid grounding in CS and I started with BASIC, Pascal, and admittedly, C. But I honestly cannot say that it was at the point when I learned about malloc/free that I would somehow have reached enlightenment about CS -- that came much later when I started seeing the interplay of various algorithmic and theory of computation concepts.

I agree with you that if you want to be serious about computers, you want to know how they work, certainly. At that point you can't avoid the stack/heap distinction and pointers. However to say that someone is claiming that you could entirely avoid the concepts is employing a straw man when we're discussing where someone should *start* with. Besides, I feel you're being overtly harsh on high-level languages -- computation is so much more than bit pushing and managing your memory.

> But if the learner wants to program only as a hobby or to create application or web software only, nothing much else, then my advice will be Python/Ruby/etc.

Oh come on. :) Someone who is creating "only" applications ... right ;) Languages that manage your memory for you are perfectly good tools, and it does not make you a more manly man to do it yourself.

> Programming is a manual skill.  Software design is of a higher order, but the skills of a designer must be grounded on manual skills.

Unless you're coding very specifically close to the iron, everything of interest is expressible in a higher-level language, and often in a much better way. And at that point, algorithm and high-level design choices become the dominant concerns almost always.

> As someone who graduated from an engineering faculty,...

I think here lies the difference in our ways of looking at the issue. For you it is a machine you put code on top of, for me code itself is an idea and machine is secondary.

Nothing wrong with the distinction, it just is...

> I don't know of ANY mechanical engineer who doesn't know how to perform basic welding, or fails in their understanding of dynamics...

Again, straw man :) I would equally much flunk a computer scientist who doesn't know how memory addressing and allocation work in an OS, but it is no reason to make a learning curve steeper than necessary or to be too macho about manual memory management.

> You simply cannot become a skilled developer or designer of anything if your grounding in low-level skills are shaky or non-existent.

I would claim you can become quite a brilliant coder "just" writing Lisp for a Lisp machine. A lot of people did.

Analogously, great things can be coded on Python, theoretically speaking without any understanding of how memory management works. CS theory does not require manual memory management for algorithms. Suppose some kid comes out of the woodwork having learned just Python and he demonstrates some brilliant new algorithm that solves a long-standing problem -- I would give him way more props than to someone who hand-crafts assembly.

> I will here pause to take exception to web pages and web applications, since they are more in the realm of multimedia production rather than software or computer systems engineering.

Well.. big enterprise information systems that you write on Enterprise Java for example can be hideously complex and have all sorts of concurrency issues etc... they can well use web apps as front ends. And there is no assembly in sight :)

> While very high-level languages are much more productive and easier to learn than lower-level languages, such ease has penalties for the learner: less discipline and less mental agility is required for those languages.

I can understand the "knowing what memory management is is a civilizing influence" argument, but this is too far... manual memory management is drudgery, not something that makes you nobler or gives you "mental agility". This is the good old argument that pain is good for you and grows character, but to me, the fact is that more expressive higher level languages give you much more freedom in exercising your mind, and doing it faster, too. Higher-level languages also have genuinely more interesting building blocks -- higher-order functions, closures and continuations come to mind.

> Relaxed coding habits, lack of discipline over data types and memory usage, poorly optimised algorithms, etc., are bad habits that I've encountered in the past from programmers with high-level-only backgrounds.

I'd rather train people in thinking instead of those issues, at least to begin with. Algorithm optimization as I understand it on the other hand is not related to higher/lower level languages really.. it's just easier to do on higher level languages, when you can more quickly switch some implementation strategy. Of course, the final squeeze-style optimizations are low-level stuff, but those are last resort anyway.

---

### Post by samjh on 2007-12-23
Looking back, yes, I think I was too harsh on high-level languages.

[quote=CptPicard]I think here lies the difference in our ways of looking at the issue. For you it is a machine you put code on top of, for me code itself is an idea and machine is secondary.[/quote]Indeed that is that way I look at it: put the code on top of the machine.

[quote=CptPicard][quote=samjh]But if the learner wants to program only as a hobby or to create application or web software only, nothing much else, then my advice will be Python/Ruby/etc.[/quote]Oh come on.  Someone who is creating "only" applications ... right Languages that manage your memory for you are perfectly good tools, and it does not make you a more manly man to do it yourself.[/quote]Sorry, I didn't mean to sound so derogatory.  Of course, they are perfectly good tools, and the job of writing applications and web apps are demanding in themselves.

Obviously for anyone who doesn't care an iota about programming close to the metal, C is probably no use.  If that is the case, by all means start with Python/Ruby/etc.  My post was written with learners who wish to incorporate low-level, close-to-the-metal programming at some point in their career.  In that case, I still think it's better to learn from bottom-up.

[quote=CptPicard]I have a solid grounding in CS and I started with BASIC, Pascal, and admittedly, C.[/quote]Interesting.  I started with BASIC and Pascal as well, except my next language was Java then C.

Which makes me wonder.  How many people with backgrounds in both low-level and high-level programming who recommends starting with Python, learned C/C++/Pascal or similar lower-level languages first?

---

### Post by CptPicard on 2007-12-23
> **samjh said:**
> My post was written with learners who wish to incorporate low-level, close-to-the-metal programming at some point in their career.

Well. If we keep considering beginners ... you just do not make that kind of decisions about your future career when you are just learning to program. This is why I would not invert the learning curve. Also, as pmasiar once pointed out, having high-level programming ability is useful for other people than software developers... scientists and engineers of other types need to be able to do number-crunching as well.

If "the point" arrives in your career, you know you need to get a handle on memory management, and you already know how the rest of the language works. And at that point you're supposed to be a near pro already, so the "oh dang I wish I had focused on C early on" argument is moot as you're supposed to know all sorts of languages anyway.

I have trouble seeing where exactly the damage occurs to the budding programmer mind... I see no reason why the ability for resource-management rigour you seem to fear gets corrupted could not be cultivated later on.

I am willing to grant though that C is such a simple language in general that you could just as well learn basic ideas of control structures and such using it. It's just that when you want to go beyond that, things get more hairy than they would on a higher level language...

> How many people with backgrounds in both low-level and high-level programming who recommends starting with Python, learned C/C++/Pascal or similar lower-level languages first?

Probably quite a lot, as those folks who started with Python or other modern high level languages are not yet old enough to be in a position to start giving out advice. :) There are people around who started with punchcards, and I bet most of them would advocate something a bit more abstract for the n00b as they themselves have hopefully also seen the light already...

Btw, I do sort of hope I had skipped the Pascal phase of my "development".. it was a waste. C is much more compact and clean.

---

### Post by LaRoza on 2007-12-23
> **samjh said:**
> 
Which makes me wonder.  How many people with backgrounds in both low-level and high-level programming who recommends starting with Python, learned C/C++/Pascal or similar lower-level languages first?

I learned C++ first. I would have rather started with Python, looking back.

---

