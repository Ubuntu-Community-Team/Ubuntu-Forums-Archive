---
title: "[SOLVED] Starting out with Python"
date: 2008-10-17
forum: Programming Talk
---

### Post by nixforme on 2008-10-17
I have some experience with programming, mostly visual basic (I know, yuck). I have been looking at the different languages and seeing what I should start out with. I have a list on what I want to learn and the first on on the list is Python. I have one issue though, I don't know what thought but I just cannot grasp Python at all. The syntax is killing me. Don't laugh. I don't know why I am having so many problems. I have been tiring to use the Python third edition from O'Riliey. I like ORiliey books, but like I said I can't seem to grasp it. Is there anything I can look at to help me?

Thanks

---

### Post by pmasiar on 2008-10-17
see wiki in my sig for many links to good free books - and training tasks. Good luck!

---

### Post by nvteighen on 2008-10-18
For you, "Dive into Python". It's a book that is meant for people with some programming experience and it refers to Visual Basic practices/concepts quite a lot.

You can even install it from the repos:
```

sudo apt-get install diveintopython

```

Then open your favorite web browser and type "/usr/share/doc/diveintopython/html/index.html".

If you prefer PDF docs, visit [http://diveintopython.org](http://diveintopython.org)

---

### Post by sheto on 2008-10-19
I would recommend How to think like a Computer Scientist. Check it out at [http://www.openbookproject.net/thinkcs/python/english2e/index.xhtml]("http://www.openbookproject.net/thinkcs/python/english2e/index.xhtml"). This book taught me Python. Hope this helps.

---

### Post by newbuntuxx on 2008-10-19
I recommend that you start learning C instead of python, and then move on to Python.

Unfortunately, I too started with visual basic (I was forced to in secondary school!). But then when I moved on to learn actual programming languages (C, Java...) I discovered that visual basic wasn't exactly programming language material. Yes, I admit that it was a lot of fun (drag and drop icons on a form, write two to three lines of code, and voila, you have a program with a GUI). Obviously though, real life programming is not drag and drop.

I also believe that learning Python as a first programming language will simply leave you with a lot of gaps, simply because it is too high level and it comes with batteries :). Don't get me wrong, the latter is a good thing, however, its like giving an elementary school student a calculator on a math test, instead of letting him use the pen, paper and his brain to get the answer. 

Hope this helps

---

### Post by Canis familiaris on 2008-10-19
> **newbuntuxx said:**
> I recommend that you start learning C instead of python, and then move on to Python.

Unfortunately, I too started with visual basic (I was forced to in secondary school!). But then when I moved on to learn actual programming languages (C, Java...) I discovered that visual basic wasn't exactly programming language material. Yes, I admit that it was a lot of fun (drag and drop icons on a form, write two to three lines of code, and voila, you have a program with a GUI). Obviously though, real life programming is not drag and drop.

I also believe that learning Python as a first programming language will simply leave you with a lot of gaps, simply because it is too high level and it comes with batteries :). Don't get me wrong, the latter is a good thing, however, its like giving an elementary school student a calculator on a math test, instead of letting him use the pen, paper and his brain to get the answer. 

Hope this helps

Oh no! The debate starts again...yet again... :|

---

### Post by LaRoza on 2008-10-19
> **newbuntuxx said:**
> 
I also believe that learning Python as a first programming language will simply leave you with a lot of gaps, simply because it is too high level and it comes with batteries :). Don't get me wrong, the latter is a good thing, however, its like giving an elementary school student a calculator on a math test, instead of letting him use the pen, paper and his brain to get the answer. 


Studies show that starting with Python leads to swifter proficiency in other languages. Your beliefs do not align with reality ;)

It is like giving an elementary student a pencil instead of a pen for a math test.

---

### Post by ghostdog74 on 2008-10-19
> **LaRoza said:**
> Studies show that starting with Python leads to swifter proficiency in other languages. 
hmm..do you mean the person will program faster in say, C if he had learn Python before that? what do you mean by swifter proficiency? Maybe you should show those studies to newbuntuxx and those who doesn't know.

---

### Post by pp. on 2008-10-19
> **LaRoza said:**
> Studies show that starting with Python leads to swifter proficiency in other languages. Your beliefs do not align with reality ;)

The last time I saw a reference to those studies, it was 'Java' that was supposedly learned faster after having learned Python, not generically 'other languages'. I could understand the effect of such a curriculum on learning Java, that being a very complex language. But for C?

Are there any links to those studies, say, in the stickies?

---

### Post by tibellus on 2008-10-19
Your favorite language is always the best:) I think the best thing to do on this thread would be to answer to nixforme's questions. You can find a really good book on Python over here: [http://www.swaroopch.com/notes/Python](http://www.swaroopch.com/notes/Python) It is free and from my point of view it is one of the best books for a Python beginner.

I hope it helps you out. All the best and happy coding:)

---

### Post by intel on 2008-10-19
O'reilly Learning Python 3rd Edition
Everything else is just a waste of your time

---

### Post by Nemooo on 2008-10-19
> **intel said:**
> O'reilly Learning Python 3rd Edition
Everything else is just a waste of your time

Obviously not, since that book is hard to grasp for him. People learn different, so there's no book to rule them all.

OP: Have a brief look at the different books and pick one to go from and if there's a subject you don't understand to your satisfaction  look it up in one of the other books. Some things takes more than one try to learn.

---

### Post by nvteighen on 2008-10-19
> **newbuntuxx said:**
> I recommend that you start learning C instead of python, and then move on to Python.

Unfortunately, I too started with visual basic (I was forced to in secondary school!). But then when I moved on to learn actual programming languages (C, Java...) I discovered that visual basic wasn't exactly programming language material. Yes, I admit that it was a lot of fun (drag and drop icons on a form, write two to three lines of code, and voila, you have a program with a GUI). Obviously though, real life programming is not drag and drop.

I also believe that learning Python as a first programming language will simply leave you with a lot of gaps, simply because it is too high level and it comes with batteries :). Don't get me wrong, the latter is a good thing, however, its like giving an elementary school student a calculator on a math test, instead of letting him use the pen, paper and his brain to get the answer. 

Hope this helps

What!?

Python is very powerful because it has a lot of expression power: the power of letting you to write more abstract things that are more unrelated to the computer and nearer to the knowledge you want to express and just simulate on the computer. According to your argument, Lisp (possibly the highest-level language in the market) is useless... and what you can do in Lisp or any high-level language is simply inimaginable in C.

Can you even return a function from a function in C? No. Can you use lists, no? Can you even "talk" (express knowledge) in strings? No, as there are no strings in C, just arrays of 1-byte length variables that we consider to be "strings"... but you surely know there aren't characters in C, just numbers and sometimes those are translated using ASCII in some context.

C is a great language. Yes, I love it: it's clean and elegant, but is meant for setting up the computer and for creating tools devoted to manipulate the computer, not to model some process in the real world. That's why it gives you that much efficiency power, memory control and speed... Any decent programmer should learn C, but I wouldn't recommend it to someone with no programming experience, as it can deviate the concept of programming to just computer-specific stuff, which is only one part of this art.

---

### Post by Sinkingships7 on 2008-10-19
> **nvteighen said:**
> 

C is a great language. Yes, I love it: it's clean and elegant, but is meant for setting up the computer and for creating tools devoted to manipulate the computer, not to model some process in the real world. That's why it gives you that much efficiency power, memory control and speed... Any decent programmer should learn C, but I wouldn't recommend it to someone with no programming experience, as it can deviate the concept of programming to just computer-specific stuff, which is only one part of this art.

Yup, that just about sums it up. There is no reason, in modern day programming, for anyone to start out with C. The only thing that it will give the average beginner is a headache and slow advancement towards their primary goal. You want to learn how to program, not how to fight against a language.

Common concepts, data structures, algorithms. A good understanding of those (and more) are more important than the language you implement them in. It just so happens that Python is powerful and well-rounded enough to offer the ability to learn all of these things with a clear and easy-to-read syntax, tons of built-in library functionality, and a strong, dynamic type system. Not to mention that it enforces good coding structure with mandatory whitespace delimiting and automatic memory management.

---

### Post by pmasiar on 2008-10-19
> **ghostdog74 said:**
> hmm..do you mean the person will program faster in say, C if he had learn Python before that? what do you mean by swifter proficiency? Maybe you should show those studies to newbuntuxx and those who doesn't know.

Yes. Studies (about Java) were linked in some sticky. But even plain common sense suggests that learning basic concepts of programming in Python allows to learn those, and then continue in language of your choice. It is because clean simple high-level language like Python allows learner to focus on high-level concepts, without being distracted and confused by low-level details. Like when you start learn reading, you don't start with a Shakespeare or Wiliam Faulkmer's The Sound and the Fury.

Many programmers who do not know Python are confuse by Python being both easy to learn and having quite advanced features, missing in many simpler languages like C. Of course Python does not have some facilities needed for extreme performance in code (like static typing), which  might (or might be not) important for the learner, and if important, learner need to learn (also, and after Python) another, statically typed language. But static typing is quite trivial, it is quite a lot of pain for little gain. 

Starting with C has little sense, and learning C later makes sense only if you are ready to spent huge amounts of time to  write highly efficient code. Most people value their time more than CPU's time, so are concened to create the needed program as quickly as possible. CPUs are cheap and fast, even if code will be 20% or 50% slower it's not a big deal, if you can write it 10 times faster.

---

### Post by ghostdog74 on 2008-10-19
thanks, but that's not what i am asking. I am asking for proof of "swifter proficiency" when one learns Python then switch to other language like C, as what Laroza said.  Seriously, do you believe one can have "swifter proficiency" (depending on what that means) when he switch from Python to C or some other similar?

---

### Post by pmasiar on 2008-10-19
> **ghostdog74 said:**
>  Seriously, do you believe one can have "swifter proficiency" (depending on what that means) when he switch from Python to C or some other similar?

yes. All learning is from simple to more complex, so it would be right way to learn

---

### Post by ghostdog74 on 2008-10-19
> **pmasiar said:**
> yes. All learning is from simple to more complex, so it would be right way to learn
what i am asking, for example, to someone who doesn't encounter pointers in Python, then suddenly after switching to C, he has to learn pointers. So is there any studies that provide proof learning Python beforehand can help you understand pointers better and faster? That's just an example and my understanding of Laroza's "swifter proficiency".

---

### Post by slavik on 2008-10-19
> **LaRoza said:**
> Studies show that starting with Python leads to swifter proficiency in other languages. Your beliefs do not align with reality ;)

It is like giving an elementary student a pencil instead of a pen for a math test.
You mean the ones comparing Python with Java as a first language? Come on, you know better than that.

---

### Post by newbuntuxx on 2008-10-19
My apologies to the OP, as I did not intend to spark a debate here and Hijack the thread. My previous post was purely based on my own experience. It was entirely subjective, and it was certainly not based on any studies or statistics of any sort. Thus, I may very well be wrong. 

And to the respected Python gurus and supporters I say: I was not belittling Python in any way! In fact, I believe (personal opinion) it to be much more powerful than C or Java. This is because (personal opinion again) a good programming language is a language that is very high level, efficient, and has many useful tools to prevent the coders from re-inventing the wheel, IMHO. The latter helps the developer write and debug code much faster. Thats why I like Python.

But....

For someone to **better** understand the basic inner workings of the computer , I personally **recommend** them to start with C, if they are a beginner.

This is not an insult to Python. I believe that Python was created to serve a certain purpose and that is: Rapid development, while C was created for the purpose of creating an OS. 

So, you can't really compare the two since they serve two different purposes. 

once again, that was just my two cents.

---

### Post by LaRoza on 2008-10-20
> **ghostdog74 said:**
> thanks, but that's not what i am asking. I am asking for proof of "swifter proficiency" when one learns Python then switch to other language like C, as what Laroza said.  Seriously, do you believe one can have "swifter proficiency" (depending on what that means) when he switch from Python to C or some other similar?

Look at the questions on the forum. When someone is learning C with no prior programming experience, we get a lot of questions about simple C concepts, usually based on syntax or doing things that have nothing to do with programming itself. When someone has a problem in C, it is rarely with the concept they are trying to study, but a lack of understanding of C itself. 

When someone goes from Python to C, they will have to spend time with pointers, arrays, and the simplicity of C, but they will not be doing that while learning programming. 

Python questions on this forum are usuall easily answered and understood. There is no "hidden bug" in the simple programs beginners do. Trying to explain C issues usually involves analogies (cubby holes...) and several attempts. Python (and others) usually don't.

For learning how to program, Python (sans modules) is better (IMO) than C, because of this. 

Of course, it doesn't matter to me personally what people started with. I started with C++, and have already done things the hardway (and lived to look back at shake my head at the waste of time).

---

### Post by ghostdog74 on 2008-10-20
> **LaRoza said:**
> Look at the questions on the forum. When someone is learning C with no prior programming experience, we get a lot of questions about simple C concepts, usually based on syntax or doing things that have nothing to do with programming itself. When someone has a problem in C, it is rarely with the concept they are trying to study, but a lack of understanding of C itself. 

don't you think they should go to school and learn these programming concepts first? IMO, giving example from posters in this forum having difficulties in C is not substantial evidence because some of them may never been under someone's programming supervision (like a real life teacher) before. Do you have links to those studies that you mention that proofs learning Python first and then switching to C makes them understand C and pointers(for eg) faster ?

---

### Post by pmasiar on 2008-10-20
> **ghostdog74 said:**
> what i am asking, for example, to someone who doesn't encounter pointers in Python, then suddenly after switching to C, he has to learn pointers. So is there any studies that provide proof learning Python beforehand can help you understand pointers better and faster? That's just an example and my understanding of Laroza's "swifter proficiency".

I know that you know that pointers are not the untimate secret knowledge in CompSci, so I am not sure why here. Yes, they are important to understand, and when I compare people who know only some Java, they are completely lost when learning cost of operation on different data structures (because Java hides many details).

But there is more to learn in programming beyond pointers, and it is possible to learn basics of programming without grokking pointers. But when beginner is learning pointers, after learning programming in Python, she understands basic concepts, and can focus on deeper stuff without being confused.

Yes, I would recommend learning C before learning OOP and Java/C++, because OOP adds rather complicated layer, and if beginner tries to understand 'close to metal' operation after OOP, looks like they are confused. OOP was originally just a 'design pattern' in C. For me it's hard to judge from my own experience because I learned ASM first ;-)

---

### Post by ghostdog74 on 2008-10-20
> **pmasiar said:**
> But when beginner is learning pointers, after learning programming in Python, she understands basic concepts, and can focus on deeper stuff without being confused.

this is reiterated again, but never showed proof of studies. How does learning Python before learning C's pointers enable one to understand basic concepts of pointers in C, when there isn't pointers in Python in the first place? hmm.. i hope i am clear in the way i asked the question now :)

---

### Post by slavik on 2008-10-20
learning Python does not make you understand pointers at all unless you understand how references work ... references are pointers, with some wrappers (even though x == y will compare the references, not the object values).

Python is a better first language than many others, but I would not say that it is the best. Think about competing languages as Olympic Games. There are various categories and events. Then there are decathletes that do ten different events, yet, if someone is very good at only one type of game, we call them the best athlete even though they are good at only one thing. Decathletes are good at all ten. Catch my drift?

A 70kg body builder cannot lift 210kg, even though they have all the bulging muscles. An Olympic weight lifter doesn't look like (s)he has any power in them. :)

---

### Post by Canis familiaris on 2008-10-20
> **LaRoza said:**
> . I started with C++, and have already done things the hardway (and lived to look back at shake my head at the waste of time).
I started with C++ too but have no regrets. My previous experience with C++ is helping me a LOT now as I am learning Python.

P.S.: There is no waste of time during learning programming. ;) (unless you are short on time :| )

---

### Post by pmasiar on 2008-10-20
> **ghostdog74 said:**
> this is reiterated again, but never showed proof of studies.

As you understand, this kind of studies are extremely hard to make, because anyone can learn first language only once.

> How does learning Python before learning C's pointers enable one to understand basic concepts of pointers in C, when there isn't pointers in Python in the first place? 

By separating learning basics of programming (variables, loops, functions, return values) from implementation details, like pointers. So when learner dives into pointers, all the basics are fully grokked and do not confuse her anymore.

---

### Post by LaRoza on 2008-10-20
> **ghostdog74 said:**
> don't you think they should go to school and learn these programming concepts first? IMO, giving example from posters in this forum having difficulties in C is not substantial evidence because some of them may never been under someone's programming supervision (like a real life teacher) before. Do you have links to those studies that you mention that proofs learning Python first and then switching to C makes them understand C and pointers(for eg) faster ?

No. I don't think one should have to go to school first. I don't know about everyone else, school is not something that is free and automatic for everyone. Plus, many learn programming on their own (like me).

I never had someone to teach me either, and my advice and point of view is with that background. Therefore, I give advice which makes no assumptions, only that the person is sentient, has access to a computer, the internet at least some of the time (unless specified), time to study on their own,  and no extra money.

No, I don't have any links with such proof, but give me a minute and I will make such a link.

> **slavik said:**
> learning Python does not make you understand pointers at all unless you understand how references work ... references are pointers, with some wrappers (even though x == y will compare the references, not the object values).

No, it doesn't teach the C concept of pointers, but it doesn't get put them in the way of learning, and one does learn the concept (lists, used as arrays). 

> 
A 70kg body builder cannot lift 210kg, even though they have all the bulging muscles. An Olympic weight lifter doesn't look like (s)he has any power in them. :)

Now that is inaccurate. "Bodybuilder" is too vague. You should say "the average 70kg body builder". Many weightlifters and powerlifters have gone into bodybuilding at some point.

And an Olympic weight lifter looks like they have a lot of power in them (to those who know what it looks like)

> **Anurag_panda said:**
> I started with C++ too but have no regrets. My previous experience with C++ is helping me a LOT now as I am learning Python.

It works the other way too, IMO, swifter.

> 
P.S.: There is no waste of time during learning programming. ;) (unless you are short on time :| )
By waste of time, I meant that I spent more time on things that weren't important than learning things that were useful. Sure, skateboarding up a hill will "work" and the effort won't be a "waste" because it was needed to get to the goal, but there are much earier ways.

---

### Post by nvteighen on 2008-10-20
I usually defend the idea of going from Python to C; but I'd like to know how many of us that defend that argument actually did that path... I did something *like* that (in the sense of having started from a high-level language): I started from BASIC and VB and then (after some years without programming) went on C and then Python... But IIRC you, pmasiar, started programming with Algol-60, am I right? LaRoza, C++... 

It would be nice to ask those that followed our advice of starting on Python and then learned something else to tell us how they felt...

Just for intellectual honesty.

---

### Post by Sinkingships7 on 2008-10-20
> **nvteighen said:**
> 
It would be nice to ask those that followed our advice of starting on Python and then learned something else to tell us how they felt...

Just for intellectual honesty.

Well, when I came to these forums asking for help with my first real language, C++, I was told that it would be best to move onto Python and drop C++ for the time being. I did not, however, follow that advice. I continued with C++, then studied C for awhile. With enough determination and aspirin, that path shouldn't discourage young programmers. The only wish that I HAD listened, as I now see how long it took for me to grasp such simple concepts, all because I was wrestling with the language.

I'm still learning C++... -_-

---

### Post by pmasiar on 2008-10-20
> **Sinkingships7 said:**
> WThe only wish that I HAD listened, as I now see how long it took for me to grasp such simple concepts, all because I was wrestling with the language

So this could be considered as anecdote supporting the idea that learning simpler language does help learning more tricky language? Without any doubt, there would be many who would claim double-blind study. Like for research of joint surgery, chirurgs did sham surgery (as placebo) - to have blind study. 

Maybe we need to test this idea by teaching someone Java, telling him that it is a simple language called Python ;-) for comparision

---

### Post by LaRoza on 2008-10-20
> **pmasiar said:**
> So this could be considered as anecdote supporting the idea that learning simpler language does help learning more tricky language? Without any doubt, there would be many who would claim double-blind study. Like for research of joint surgery, chirurgs did sham surgery (as placebo) - to have blind study. 

Maybe we need to test this idea by teaching someone Java, telling him that it is a simple language called Python ;-) for comparision

I started with C++, but struggled with it, and only got it after learning PHP (which is comparable to the Python/Ruby/Perl/PHP/Tcl)

---

### Post by Frijolie on 2008-10-21
Along these lines I would also like to begin to learn Python myself. However, after doing a little reading, I've learned that v 3 is coming out soon and will not be backwards compatible with other versions. With this being said, which version should I begin on (2.5 or 3)?

---

### Post by nvteighen on 2008-10-21
> **Sinkingships7 said:**
> The only wish that I HAD listened, as I now see how long it took for me to grasp such simple concepts, all because I was wrestling with the language.


> **LaRoza said:**
> I started with C++, but struggled with it, and only got it after learning PHP (which is comparable to the Python/Ruby/Perl/PHP/Tcl)

This is the kind of posts I wanted. These are of course not a scientific evidence for anything, but it shows a clear situation we people here notice from beginners' posts: that they start learning a low-level language and usually their questions are not related to programming concepts (e.g, what's a loop meant for) but either to language-specific points that are related to implementation details needed on low-level programming (e.g. pointers). That's a good evidence that people starting on those languages get easily distracted on secondary language-specific stuff instead of learning more about the general techniques they'll use in all languages (e.g. modularity, recursion, iteration, data structures, algorithms, etc.).

But where are those who learned Python and then C or C++? Are they here to tell us their experience?

> **pmasiar said:**
> So this could be considered as anecdote supporting the idea that learning simpler language does help learning more tricky language?

Yup. 8)

> Maybe we need to test this idea by teaching someone Java, telling him that it is a simple language called Python ;-) for comparision

That should be tried in a cell room with no Internet access so the "pacient" couldn't figure out what's going on. :p

---

### Post by CptPicard on 2008-10-21
We should also teach them Scheme telling them it's the all-powerful assembler that is the lowest level and thus gives you Most Control (tm)...

Then they would miss Lisp machines for the rest of their lives and be all traumatized by register machines...

---

### Post by pmasiar on 2008-10-21
> **Frijolie said:**
> Along these lines I would also like to begin to learn Python myself. However, after doing a little reading, I've learned that v 3 is coming out soon and will not be backwards compatible with other versions. With this being said, which version should I begin on (2.5 or 3)?

Learn current 2.5 or newer 2.6. You will be able to convert your code to 3.0 almost automatically, and the difference is not that big: mostly, in 2.5 print is statement but in 3.0 is a function. Also, most books are for Python 2 ;-)

---

### Post by nixforme on 2008-10-21
Wow, never thought that this would turn into such a big debate. I do thank all of you that have contributed to this. I have made my decision and I will be starting out with Python and work my way up.

Thanks again to all of you :)

---

### Post by nvteighen on 2008-10-21
> **nixforme said:**
> Wow, never thought that this would turn into such a big debate. I do thank all of you that have contributed to this. I have made my decision and I will be starting out with Python and work my way up.

Thanks again to all of you :)
Good luck!

And if you have any doubt, just ask here! :)

---

### Post by LaRoza on 2008-10-21
> **Frijolie said:**
> Along these lines I would also like to begin to learn Python myself. However, after doing a little reading, I've learned that v 3 is coming out soon and will not be backwards compatible with other versions. With this being said, which version should I begin on (2.5 or 3)?

The changes won't be that hard to deal with. Code-wise, it would be quite simple to change, and it wouldn't interfere with your learning.

---

