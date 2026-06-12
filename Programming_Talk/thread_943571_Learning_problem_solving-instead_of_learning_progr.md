---
title: "Learning problem solving-instead of learning progrmming :)"
date: 2008-10-10
forum: Programming Talk
---

### Post by hoboy on 2008-10-10
Hello I have really benefit from this forum, as a NewB in the world of programming I have asked many questions about learning programming, it is obvious that people learn differently, I begin to understand that in order to be a good programmer one has to be a good problem solver, a good problem decompositioner.
Why programming books are not about this, but more about the language syntax learning ?.
Ok forgive me if I am wrong I am only a 16 year who think that hi begin to understand the topic :)
I am right ?
tks

---

### Post by Npl on 2008-10-10
actually you need to know computers, programming and problem solving. Those three are somewhat connected.
problem solving depends on the programming-language, you solve and break apart problems differently in different languages (C vs LISP for example). You might also pick the correct language for the problem at hand.
also, your code ultimately runs on the computer so you need to learn what goes well and what doesnt. Looking at the assembly produced from compilers can help alot to get a deeper understanding.

If you are just starting out however, you shouldnt aim at "getting good", but to be able to get something done first. Find something you want to program and do it, and most beginner-books focus at the task at hand for that reason.

There are books which focus on efficient algorithms, like those from Robert Sedgewick

---

### Post by hoboy on 2008-10-10
> **Npl said:**
> actually you need to know computers, programming and problem solving. Those three are somewhat connected.
problem solving depends on the programming-language, you solve and break apart problems differently in different languages (C vs LISP for example). You might also pick the correct language for the problem at hand.
also, your code ultimately runs on the computer so you need to learn what goes well and what doesnt. Looking at the assembly produced from compilers can help alot to get a deeper understanding.

If you are just starting out however, you shouldnt aim at "getting good", but to be able to get something done first. Find something you want to program and do it, and most beginner-books focus at the task at hand for that reason.

There are books which focus on efficient algorithms, like those from Robert Sedgewick
Thanks i have discover that I had a problem because i have learn the java syntax, but still I could really program, then I realized that I was missing something.
thanks for your advices.

---

### Post by issih on 2008-10-10
To be honest, the ability to think, to solve problems and to be able to consider a situation and work out a good solution is what education is meant to be for.

Universities are meant to turn out people capable of independent work, who can research a subject, grasp the concepts and formulate an efficient solution. In reality I'm not sure that ever really happened and even less sure it happens now, but nonetheless it is what you are really being taught by being in education. In theory you are learning how to be useful.

There is obviously a large element of natural aptitude in terms of being able to break a process down into subroutines, and being able to fit things together to achieve your aim, but how much is natural and how much can be learned is an impossible debate.

Either way, I wouldn't worry about not being too sure at your age, you have a lot of learning still to do, but then we all do, always :)

Other than that I agree with what was said above, its a combination of everything, language structure , design analysis and programme architecture. Sadly theres never one simple answer huh

---

### Post by LaRoza on 2008-10-10
> **hoboy said:**
> Hello I have really benefit from this forum, as a NewB in the world of programming I have asked many questions about learning programming, it is obvious that people learn differently, I begin to understand that in order to be a good programmer one has to be a good problem solver, a good problem decompositioner.
Why programming books are not about this, but more about the language syntax learning ?.
Ok forgive me if I am wrong I am only a 16 year who think that hi begin to understand the topic :)
I am right ?
tks

Problem solving is what the human brain is good at. Programming is a tool to solve problems. So, they go hand in hand. If you have the knowledge of building, but lack the ability to use the tools, you are held back. If you can use the tools, but can't design anything, you are equally held back.

Programming can be used in any field so the knowledge you need depends on the goal. If you want to do low level things, you need knowledge of computer hardware. If you wish to solve math problems or do calculations, you need to understand the math.

So, I suggest you reinforce your knowledge of math and computers and whatever interests you.

---

### Post by sillyxone on 2008-10-10
Short answer: books alone cannot make up a 4-year degree. They aim at people who is taking/has taken the courses.


Long answer: If you know why Universities teach Scheme/Lisp in the very first Computer Science class, then you can pretty much answer your question.

The purpose of a computer science program is to teach you how to learn and how to think (in computer field). After graduating, you're supposed to know how to learn on your own effectively.

Jobs require X years of experiences, but you cannot have the experience until you have a job. Similarly, they want to teach you how to think, how to divide and conquer problems, to understand how computers work, but you can only learn if you can experiment and interact with the computer. Thus, Scheme or Python is chosen because it's simple to learn, you don't have to deal much with complicated syntax and structure, and can focus on thinking and solving problems (especially important for grasping hard-to-digest concepts like scope and lambda function). Later on when you're pretty good with programming then they move on to more complicated languages.

Also, you need to be able to solve problems in different ways with different programming paradigms, thus, learning just one language is not enough.

Most Computer Science programs follow the basic pattern:
- structure of computer programming 1 (Scheme, Python or other easy to learn)
- structure of computer programming 2 (Java or C++)
- machine architecture (C)
- program design and development, or software engineering 1 (C++, Java)
- algorithm and data structure (usually C/C++ or Java)
- programming languages (various, including Prolog) 
- ... at this point, you should be able to learn almost any language that you like on your own (Delphi, PHP, Ruby, Javascript, ...)


Thus, a language usually doesn't have its own course, but is used and taught in a course as a tool for learning the course main contents. You will have to master the languages on your own. Perhaps you're supposed to use those books after taking the courses instead of before?

---

### Post by pmasiar on 2008-10-10
This is chicken-and-egg problem: you need to have experience in problem solving to understand books what write about the problem solving methods ;-)

Start with learning a language, preferably language what is readable (like Python), so you can read code of other people. Start solving problems (my wiki has links to many training tasks - will take you a year or more to solve them all). Read about how other people solved same problems. Learn data structures. After a year, you will have basic grasp, and after you re-read same books, you will be surprised how much you missed as first reading.

---

### Post by dribeas on 2008-10-10
I kind of disagree with many of the posts. To me the most important part is problem solving and then the language (as it has been already mention it provides the tool set). On the other hand, I cannot agree that computer science degrees are the only way. Where I work, the two best programmers (I am using programmer as a general term for the whole software engineering process: analysis, design...) are a graduate in physics and an engineer in a non-computer field.

You can learn a lot out of books, go to your nearest bookstore/library and grab a copy of Cormen's 'Introduction to algorithms', or GoF's 'Design patterns' get to read good books in your language of choice and as many articles as you come across. To me a good book on a language is not a book that explains the syntax, but one that explains designs and the implications your choices. 

Some books are able to change your thinking patterns. To me chapter 7 of Alexandrescu's 'Modern C++ Design' (available online) was mind-widening. The whole chapter focuses on design of a small facility: a smart pointer. At each step the author works on a new functionality that you might want to include, providing different solutions and working out the strengths and weaknesses of them, compromising on lesser functionalities when the implications are worse than the added value.

By the way, I am an engineer and not a computer science graduate but most of my friends hold computer science degrees. Having gone through the same education there are huge differences in their programming skills, and as I pointed before, I know really good programmers that are not cs either.

EDIT: Oh, I forgot to mention that this is why I do agree with @pmasiar that python is a good start language as the tool set is wide and you can focus on problem solving.

---

### Post by Rich78 on 2008-10-10
From my own experience, the best way to truly learn is on the job.  However to get the job you have to get the break you need from the employer and be willing and keen to learn.

Put the time in and you'll reap the benefits.  There are no short cuts and only if you really want to learn, then you will progress.

I've seen many people come and go with passing interest in the subject, you provide all the tools and the books and in the end they loose interest.

I also don't agree that a degree is the only way to succeed as there is an element of not being exposed to real world business problems.  

That said there's a lot of good to going through the uni system and a degree "can" open doors, but not guaranteed. 

The quickest way to learning a language is to be set a project by an outside party and just get stuck in, use the books as reference and eventually things will start to click. 

 Setting yourself little projects can be hard going but being driven by someone else will help motivate you.

---

### Post by era86 on 2008-10-10
> **dribeas said:**
> I kind of disagree with many of the posts. To me the most important part is problem solving and then the language (as it has been already mention it provides the tool set).

Problems = Languages, right?  In computer science, I believe that is how they are defined.  So, what is the argument here?:)

I agree with the above post.  Must know how to solve problems before learning any language.  Anyone can write a simple addition() function using the language, but what if you don't know how addition works?  How can you implement it using the language?

---

### Post by issih on 2008-10-11
Never said do computer science...I'm a physicist, well sort of. Education is meant to teach you how to think, regardless of subject. In theory anyway, in reality everyone has aptitude in different areas and everyone learns task specific skills either through coursework or job related activites. My main point was that its to early to be expecting to grasp everything, and the best people at everything in life are those that admit they don't nkow everything...beware the expert, he's probably an idiot in a suit :)

---

### Post by Shin_Gouki2501 on 2008-10-11
Certainly a interesting question. One general problem of prograsmming langues is that you STILL have to focus more on the "HOW" and not on the "WHAT".

quite nicely explained here:
[http://blog.jaoo.dk/2008/10/07/the-future-of-programming-languages/](http://blog.jaoo.dk/2008/10/07/the-future-of-programming-languages/)

and that quy actually does know a thing or two about programming/languages.

I hope the original poster will take a lookt at it IMO its quite usefull concerning his topic!

---

### Post by lisati on 2008-10-11
> **Shin_Gouki2501 said:**
> Certainly a interesting question. One general problem of prograsmming langues is that you STILL have to focus more on the "HOW" and not on the "WHAT".

quite nicely explained here:
[http://blog.jaoo.dk/2008/10/07/the-future-of-programming-languages/](http://blog.jaoo.dk/2008/10/07/the-future-of-programming-languages/)

and that quy actually does know a thing or two about programming/languages.

I hope the original poster will take a lookt at it IMO its quite usefull concerning his topic!
Interesting video. Just a thought: somewhere the "what" has to be translated into "how".

---

