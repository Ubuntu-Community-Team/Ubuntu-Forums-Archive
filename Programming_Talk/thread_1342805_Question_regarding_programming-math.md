---
title: "Question regarding programming-math"
date: 2009-12-01
forum: Programming Talk
---

### Post by azmozizz on 2009-12-01
Hey guys, I registered here because I saw the section about programming talk. I've read all the sticky posts, thank you very much for those links. I just started learning php, and other web technologies and after I'm pretty decent at writing in those I want to go for C/C++/JAVA. My question is, do I need math to code well in those languages? I saw on other forums that you need algorithmical thinking or something like that. I don't have just the basics of math. :( So I'm a bit scared. I hope I didn't upset no one with my topic but I didn't found something on the forum that could answer my question.

---

### Post by 0cton on 2009-12-01
not necessarily, depends on what you want to program.
with todays most high languages, for most of the stuff you can think of you won't have to worry about math at all, but knowing fundamental math can help in cases.
Let me put it this way, the lower(To the architecture) you go, the more math stuff you must know usually , but even if you won't use math in your programs , basic math will help understanding some programming stuff better (such as recursive function)
But generally speaking you don't need math to code in most languages.but math may help you in becoming a better coder, and if you want a programming career you may be required to know math as well depending on the job, it's not a black or white answer but I'd go with a no, but I'll still recommend you to get better at math :)

---

### Post by dwhitney67 on 2009-12-01
I work as a software engineer, and the math I utilize is quite basic:  Addition (when I get a pay check) and Subtraction (when I pay bills).  :D

The only time I had to use an algorithm to produce a mathematical result was many years ago and I needed to compute the ambient light level (in Foot-Lambert) that was detected by a sensor mounted to a camera.  The sensor reported a digital (discrete) value that needed to be converted to floating point.

---

### Post by grayrainbow on 2009-12-01
Well, can you do physic without math? General answer - no. Same and with programming. But...you could be an engineer without heavy use of math, that include all kind of engineering.
One need math in order to understand basics of what will be used(like data structures), and most of math(high level abstract math) used in programming happen by intuition. That sad, what need heavy math is creation of new technologies, but here again one golden rule holds - simpler mean better, which for more computer scientist basicly go like - left math to mathematitions and computer implementation to programmers.

---

### Post by squarepegg on 2009-12-01
Hi Azmozizz.  

You don't need to have a lot of experience with *computations*, but being able to think *mathematically* is helpful.  (Calculations, from additions and subtraction to derivatives and integrals, are just the *outcome* of math.  They aren't math.)  

So, two things:  
> It is true that many algorithms are based on math, but not necessarily the kind that uses numbers!  Most of algorithms are based on group theory, graph theory, and the like.
> You don't need to be an algorist to program.  Sometimes the algorithm is worked out for you, and you need only figure out how to code it.  And, in any case, a lot of algorithm design is recognizing when a problem can be solved with something you've seen before.  

I suggest Skiena's *Algorithm Design Manual* for algorithms.  Wikipedia gives a pretty good overview of graph theory at [http://en.wikipedia.org/wiki/Graph_theory](http://en.wikipedia.org/wiki/Graph_theory).

Happy coding!

---

### Post by wmcbrine on 2009-12-01
OK, I'll be the downer here.

You won't necessarily use much math in programming. But if you don't *like* math -- if you find it difficult -- then you may not have the kind of mind you need to be a good programmer.

---

### Post by goshock on 2009-12-01
In my experience, logic is more important than the math portion of it.  Of course it depends on what you are going to be programming, but a good handle on logic will take you far.

---

### Post by lisati on 2009-12-01
My $0.02: Basic arithmetic (addition, subtraction, multiplication, division), together with basic logic and organizational skills, is probably more than enough for most programming tasks.

---

### Post by DougB1958 on 2009-12-01
A couple of other posters have already touched on this idea, but here's my version of it: I find that the kind of thinking that it takes to program well is very much the same kind of thinking that it takes to do math well (where "do math" doesn't mean things like arithmetic or remembering formulas as much as it means things like devising proofs or deriving equations). So you can do fine at programming without explicitly doing much math in any form (as long as you're willing to let someone else invent algorithms for you), but if you really don't have a mind for math, you probably don't have a mind for programming either. On the flip side, if you enjoy and do well at programming you could probably turn those same skills to enjoying and doing well at math.

---

### Post by shadylookin on 2009-12-01
You have to be able to do basic algebra. Other than that it depends on the specific problem you're trying to solve.

---

### Post by jpkotta on 2009-12-02
[QUOTE=Lynn A. Steen]Mathematics is the science of patterns. The mathematician seeks patterns in number, in space, in science, in computers, and in imagination. Mathematical theories explain the relation among patterns; functions and maps, operators and morphisms bind one type of pattern to another to yield lasting mathematical structures. Applications of mathematics use these patterns to explain and predict, often yielding patterns of patterns. In this way mathematics follows its own logic, beginning with patterns from science and completing the portrait by adding all patterns the derive from initial ones.[/QUOTE]

Mathematics is studying patterns.  If you want to write programs that solve tough problems (tough is relative, but the easier a problem is, the less need there is for a program to solve it), you need to find the patterns underlying the problem you want to solve, and write the code to "mirror" those patterns.

Also, mathematicians love to abstract things.  They take a pattern and see it in several different contexts.  Then they start studying that pattern independently of any context -- they abstract it out.  Likewise, programmers should be able to see different pieces of code that do essentially the same thing, and figure out how to write it such that the common elements are all in a single piece of code.  E.g. you wouldn't rewrite a sort algorithm every time you needed one, you'd write it once and only write a compare function every time you needed it in a new context.

These are two extremely useful (probably essential) skills for any decent programmer.  Knowing how to evaluate an integral or find the roots of a polynomial, probably not so much.

---

### Post by CptPicard on 2009-12-02
It works the other way too, fortunately -- programming is an excellent teacher and motivator of math-like thinking, and to get started, you don't need that much of it.

Most of the actual mathematics of programming is in the problem itself that you're solving, and then there is the possible mathematics of the analysis of the solution.

Programming itself is an interesting intersection of abstract mathematical-like structure and *linguistics*, actually... this is why higher-level languages are interesting because of the way they map the language structure to the problem structure via higher-order abstraction. One can for example look at the differences between Haskell and Lisp -- Haskell goes for a rather math-like abstraction; Lisp is a flexible, malleable generic language that seeks to allow for the specification of domain-specific languages to fit a task.

---

### Post by MindSz on 2009-12-02
What's really helped me program is to be able to think logically more than knowing actual math. After all, the computer does most of the math for you, bout you need to tell it which operations you want it to perform.

That being said, knowing how to go from decimal to binary or hex (and the other way around) and perform basic arithmetic operations on those numbers has been a real help to me.

---

### Post by azmozizz on 2009-12-02
Thank you very much from the bottom of my hearth.  This topic and your suggestions help me and also motivate me.  I love math, just that I took a brake, a long one, like 2 years. In high school we didn't do math because we were on the humanist side, not the real side were you would have math, physics, chemistry, etc. So, I don't know math very well, but I will try now to not give up and learn. I wish I could have done a rollback and see life like I see it now...I had many math teachers back in school/and high school. They used to hate me and I used to hate them back then, but in the last 2 years of high school everything changed. A new teacher came and I don't know, changed my all perception about math and life. I started not being that ignorant person I was before and funny, I started loving math. Thank you so much, I apreciate it! I never had the chance to go to a real profile in high school. And didn't got the chance to do what I wanted back then..but now I'm starting at my own to fulfill my dream of becoming a programmer. I'm a bit scared to not fail doing this. If you can give me other advices at what should I concentrate, or I don't know advices that I may use, please don't hesitate. And sorry if this will be offtopic, since I've asked only about math.

Again, guys, I want to thank you very much. :popcorn:

---

### Post by CptPicard on 2009-12-02
It's never too late, I don't tend to believe that people are to be slotted into just doing one kind of thing. A smart person will be capable in anything he puts his mind to, and math is a great framework to understand all kinds of phenomena within.

I wrote this once in a similar thread...

[http://ubuntuforums.org/showpost.php?p=4007387&postcount=10](http://ubuntuforums.org/showpost.php?p=4007387&postcount=10)

---

### Post by azmozizz on 2009-12-02
Thank you, I will have a look on that. :)

---

