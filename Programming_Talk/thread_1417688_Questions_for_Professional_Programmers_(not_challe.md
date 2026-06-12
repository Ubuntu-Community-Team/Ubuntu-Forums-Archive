---
title: "Questions for Professional Programmers (not challenges)"
date: 2010-02-27
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-02-27
Well I have a few questions that deal with profession of computer programming.

[WARNING::: Potentially bad grammer below!! // too tired to prroof read]
 
 
[U][B]1) How important is *understanding* linear algebra to programming.
[/B][/U]                                   --> I am assuming that linear algebra is very important to programming, but I am wondering how important acctually understanding it is.
                                               --> I can hold down a [80-85]% average in the class, but with the exception of basic matrixrow operations I don't understand why I am doing anything I do (BAD linear teacher=] -- only explains what to do not why.) (And I'm wondering if I should go and start reading up on it so I can understand it better.)

_**2) How much learning are you expected to do after getting a degree? (Software Engineering Degree.)**_
[U][B]
3) What programming language is typically used in a professional setting?
[/B][/U]                                   --> How hard is it to switch from one language to another?
                                   --> Do you need to learn multiple languages depending on the job? (( Assuming this one's answer is yes. ))



Not trying to decide on whether or not to stick with it, I've already made up my mind, *I'm just curious.*

---

### Post by CptPicard on 2010-02-27
> **YourMomsASmurph said:**
> --> I am assuming that linear algebra is very important to programming, but I am wondering how important acctually understanding it is.

I guess I could easily say that strictly speaking *for programming*, it is not important... but in applications domains where it is important, it is (think 3D graphics). Also, vector/matrix maths pop up as formulations in a lot of directions in algorithmics.

But considering that programming is about solving problems, if one takes this kind of an attitude, one can be dismissive of everything and end up in a situation where one can't really understand the problem domains one is supposed to be programming in. Typing up the code according to some language rules is just a fairly trivial part of the task.

By the way, linear algebra is often one of the first math classes in university simply because it's a good introduction to higher mathematics and the way things are abstracted there. It's to build a certain mindset... for the time being it is probably smart to just learn the axioms and how to play with them; enlightenment about, say, matrices as linear transformations come in due time.

> How much learning are you expected to do after getting a degree? (Software Engineering Degree.)

Rest of your life. Esp. in programming it has to be something you're willing to tinker with and think about on your own, you can't be "taught" it.

> 
3) What programming language is typically used in a professional setting?

Any that accomplishes the task. Again, a somewhat wrong kind of question... real worthy professionals don't try to limit themselves to something so they don't have to wander out of the comfort zone.

> --> How hard is it to switch from one language to another?

After maybe a dozen languages that are sufficiently different, trivial. Most Java/C++-style languages work very similarly, the more different ones (Prolog, Lisp, Haskell...) require genuine readjustment in thinking... but eventually you have recognized all the main pieces that go in one form or another into any given programming language, so after that, switching back and forth is not hard.

> 
                                   --> Do you need to learn multiple languages depending on the job? (( Assuming this one's answer is yes. ))


Yes.

---

### Post by Reiger on 2010-02-27
Having to learn multiple languages: yes. In fact, as I understand it CS courses consider learning languages a by product -- a triviality you pick up along the way.

There will be, say, 3 explicit courses that teach some aspect of programming/problem solving along the lines of introduction to a certain language. For instance Object Oriented Programming/Imperative programming is tackled with a Java course; Function Programming is tackled with Haskell or similar; and Declarative programming with SQL/Prolog. But you might get an introduction to systems and networking which assumes you know C. Or a side assignment which demands you write something in assembler for a fictitious CPU arch.

And likewise you might get an introduction to the wonderful world of web programing which assumes you learn everything you need by yourself while the course itself is focusing on the high level concepts of Sessions, Restful APIs and/or XSS attacks.

---

### Post by dwhitney67 on 2010-02-27
> **CptPicard said:**
> 
Rest of your life.

And that's the truth.  By now, the OP is probably eye-balling the Business School's curriculum and/or thinking of becoming a truck driver.  Let's not scare him away.  :-)

---

### Post by lisati on 2010-02-27
It has been a while since I worked as a programmer; here goes with my $0.02:

1. It's probably not liner algebra as such that will be helpful, but the ability to solve problems - +1 to Capt. Picard's comments. Linear algebra *can* be of help in learning how to solve *some* problems. Although there is a superficial resemblance between some aspects of algebra and some programming languages, there will be times when the symbolism in one area won't sit comfortably with the symbolism used in the other. (Example: "a=a+1" is valid in some programming languages, but means something different to what you might expect in algebra.)

2. Having a formal education can be a good thing. Having said that, I've found that the learning process continues long after your formal education has finished. If all I had to work with was that I managed to retain of my formal education, I'd be stuck, and probably wouldn't be using Ubuntu, let alone having my own web page and email server hosted on one of my machines. I'd be surprised to hear of a business that used punched cards these days.

---

### Post by YourMomsASmurph on 2010-02-27
> **dwhitney67 said:**
> And that's the truth.  By now, the OP is probably eye-balling the Business School's curriculum and/or thinking of becoming a truck driver.  Let's not scare him away.  :-)

lol. Not at all, I'm happy to keep learning, (or self learnning, what ever the case may be) after getting a degree. I find programming extremely... Fun? Satisfying?... Don't know what word to use, but either way being a programmer would be a job I would enjoy. Just wanted to know a little more about the profession. 


I appreciate all the responses, they were quite helpful but basically what I expected to hear.


{{{
[Rather than making a new thread (will tomorrow if I get no response) I'd like to ask a Q about c++ and switching between data types]

Is it possible to switch a string "45" into an int 45? -- > I know it is possible in some languages (python at least) So, im assuming there is probably a way to do it in c++.

Only thing I can think of so far is to make it a char (instead of string), get the int value for the char, then subtract some kind of constant to get an integer value of the number. ((NO idea if this would work.))  
}}}

---

### Post by bukwirm on 2010-02-27
Look up the atoi or strtol functions.

---

### Post by dwhitney67 on 2010-02-27
```

std::string       fortyfive("45");
std::stringstream iss(fortyfive);
int               num;
iss >> num;

```
It's less "sexy" than using the C library's atoi() function, but it's C++.

But here's something that can't be done as easily in C:
```

std::string       numbers("45 54");
std::stringstream iss(numbers);
int               num1, num2;
iss >> num1 >> num2;

```

---

### Post by gordintoronto on 2010-02-28
Linear Algebra?  Totally irrelevant. Then again, I was doing business applications.

I took ONE really useful course in university.  It was offered by the Philsophy department: logic.  One term studied three words: and, or and not.  You might have trouble believing it, but some people got 60% (or less) on the exam.  Three words.

My degree qualified me to begin learning.

I have also used at least a dozen languages.  One of them was the assembler language for the 6502 chip (Apple II), which I learned by the light of a campfire, with no computer anywhere near.  Got home and tried lots of stuff, and it all worked.

A good programmer can truly grok 400 lines of code.  A great programmer can truly grok 4,000 lines of code.

---

### Post by matthew.ball on 2010-02-28
You never came across implication in logic?

---

### Post by Reiger on 2010-02-28
Probably, but implication only gets interesting when you throw in not and or. ;)

---

### Post by grayrainbow on 2010-02-28
Well, first and for most, as everything in programming...it depends.

But going one by one:

1) I know a lot of programmers who don't have big clue of anything in math(except +, * and a like), so in general you could be programmer without a lot of math. But I also know(and currently work) with people for who math is kinda second natural language. In general in some places linear algebra is not required, but more math always lead to more possibilities and bigger opportunity for interesting job. NOTE: to implement some already solve problem, one does not need to KNOWS the math, just if one KNOWS the math eventual debugging could be extremely more easy.

2) Hmm, depends what one thinks for learning. There are, and there always will be new APIs which one has to learn in some degree. I also think that there always will be new techniques that one has to master. Hell, even the desktop user interface change in time and people comfortable with PCs in past was force to learn in order to use todays machines. So in general +1 for whole life.

3) For different purposes people use different languages. And since programming nowadays is mainly collective effort, one of the reasons for choice is what language members of the team are comfortable with.
About the switch...well it kinda depends. Basicly most of the programming languages consist of exactly the same things - control flow statements, and once you learn that one does not need to learn it again couse its kinda same in every language. Of course there are some big differences in languages, which make transitions from one language to another harder or not. For example pointers a quite hard concept for many people, the freedom of expression in C/C++ is also extremely hard for lots of people, functional programming approach is also...un&#1072;cceptble for most of programmers in the world, object oriented programming is found kinda hard for some people, logic programming is...well lots of people don't find it programming at all. I believe you get the idea.
Multiple languages? Well, my personal opinion is that if one does not have a desire to learn at least few programming languages, one has not the right to call him/herself programmer. Probably the only thing in common in different areas of programming is not to get answer of questions like "what is 1+1?", but more - expression of ones vision. It's pretty much like literature, one has to be good to express with some language some solution/problem, and/or one has to be very good in translations from one language to another, and for that learning, but REALLY LEARN, few languages always helps, just one has to be careful couse learning to much languages is usually waste of time for production environment.

P.S. Btw, good look to everybody decides to go in the magic of programming. Have fun :)

---

### Post by CptPicard on 2010-02-28
> **matthew.ball said:**
> You never came across implication in logic?

Well, it's got a truth table definition so I guess one could assume that they did also study what follows of those three operators ;) But I would assume that a logic class at least looks at "natural reasoning" (not sure what it's called in English) and quantified logical sentences...

But yes... logic and with some discrete math thrown in is essentially "basis of formalized thought" so it's very valuable. When one wishes to specialize on computable functions, things like Lisp follow very naturally from math... (after all, it used to be a notation for programs meant for academic publications -- machine code listings or vaguer descriptions are not anywhere near as illustrative)

---

