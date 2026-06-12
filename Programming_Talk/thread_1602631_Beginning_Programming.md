---
title: "Beginning Programming"
date: 2010-10-21
forum: Programming Talk
---

### Post by SOG420 on 2010-10-21
I  have been using Linux ( specifically Ubuntu) for about 4 years now and I have decided that its time to delve into programming. I wanted to get some opinions on where to start. I have a few books on Perl, PHP, Python, C, and C++. I just wanted to opinions on this.

---

### Post by GregBrannon on 2010-10-21
I recommend that this thread move to the Programming Talk sub-forum.

SOG420, I recommend that you review the stickies and the threads in the Programming Talk sub-forum.

This question has been asked many times - asking again is fine - and the overriding opinion of the wisdom assembled here has been to start with Python.  Maybe you'll get a different answer this time or find a convincing minority argument for starting with another language.

Good luck!

---

### Post by SOG420 on 2010-10-21
I hate it when people post in the wrong place. My apologies and thanks for the response. For the mod: feel free to delete post I just needed to read stickies.

---

### Post by SevenMachines on 2010-10-22
Theres never a bad place to post a question, Its just that the programming forum is a better place for this one, theres quite a few threads in there worth looking at, but yes, python :*) Still on my 'todo' list but is well designed and will allow you to do everything from beginner to coding guru

---

### Post by Joeb454 on 2010-10-22
Thread moved to Programming Talk :)

---

### Post by dv3500ea on 2010-10-22
Some of these links may help you:
[LIST]
[*][How to start programming - guides and links for many languages]("http://ubuntuforums.org/showthread.php?t=333867")
[*][Quickly]("https://wiki.ubuntu.com/Quickly")
[*][Ubuntu Developer Videos]("http://ubuntu.mirocommunity.org/")
[*][Ruby in 20 minutes]("http://www.ruby-lang.org/en/documentation/quickstart/")
[*][Non Programmer's Tutorial for Python]("http://en.wikibooks.org/wiki/Non-Programmer's_Tutorial_for_Python_2.6_")
[/LIST]

You will need to learn a programming language and there is lots of choice available. I suggest [Ruby]("http://www.ruby-lang.org/") because it is easy to learn but once you have learnt the basics there is always more to learn. It is also very fun, especially if you play around with [Shoes]("http://shoesrb.com/"), a program which enables you to create fun little graphical apps (using the ruby language) easily.

---

### Post by Miyavix3 on 2010-10-22
Personal opinion: Python

Just because it enforces 'good programming' by implementing force indentations.

I learned python first, and for any other language I felt the need to indent properly as I did in python.

Also, ruby is nice but can be confusing because it hangs out with perl. He's a bad influece. :tongue:

---

### Post by juancarlospaco on 2010-10-22
Python

---

### Post by spurs21 on 2010-10-22
My best recommendation would be to follow MIT OpenCourseWare class 6.00. It has an amazing video lecture + homework series for Programming (using Python), designed for those who have never programmed before. It's a very interesting class that will get you up and writing cool stuff as opposed to spending weeks of writing cute examples of for loops in C or C++.

[http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/lecture-videos/](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/lecture-videos/)

Structure and Interpretation of Computer Programs is a pretty amazing book that's worth looking into after completing that Python course, and it's free.

[http://mitpress.mit.edu/sicp/](http://mitpress.mit.edu/sicp/)

Also, there's two great courses with videos available that are based on SICP:
Berkeley's CS61A
[http://webcast.berkeley.edu/course_details_new.php?seriesid=2010-D-26275&semesterid=2010-D](http://webcast.berkeley.edu/course_details_new.php?seriesid=2010-D-26275&semesterid=2010-D)

A class given to people at HP (I believe) by the authors of the book back in the mid 80s. They're both outstanding writers and teachers. Hal Abelson is particularly amazing to listen to.
[http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/video-lectures/](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/video-lectures/)

Once you understand just a bit about recursion, you can probably jump to SICP.

---

### Post by linux-hack on 2010-10-22
> **juancarlospaco said:**
> Python

+1 :popcorn:

---

### Post by Eragon0605 on 2010-10-22
Yes, I would encourage you to start with python as well. Once you have the basics of python and computer programming in general down, I would ***highly*** recommend looking at several other languages such as C++. Python is a great language for beginners, but it isn't for everyone. I personally can't do much of anything with python, I just don't work well with it. I find I personally can work much, much better with C++. Basically what I'm trying to get at here is: don't limit yourself to one language. There are many, many different languages out there and each one is meant for different people and different tasks.

---

### Post by ibuclaw on 2010-10-22
A recommended read before you start your programming endeavour.
[http://writing.bryanwoods4e.com/1-poor-poor-child](http://writing.bryanwoods4e.com/1-poor-poor-child)

---

### Post by spurs21 on 2010-10-22
> **ibuclaw said:**
> A recommended read before you start your programming endeavour.
[http://writing.bryanwoods4e.com/1-poor-poor-child](http://writing.bryanwoods4e.com/1-poor-poor-child)

I disagree with a couple of things in the link above:

> 
As a linguistics major, you're no stranger to the idea that a person is  only capable of having thoughts and ideas that can be expressed in their  language, and there is no reason to expect programming languages to  differ from spoken languages in this area.
This is the Sapir-Whorf hypothesis, which has been widely discredited in modern linguistics with the theory of the universal grammar. It's roots come from extremely sloppy word for word translations of Native American languages by a guy who never even met a Native American. The idea that one needs to frame his thought in a spoken language to think is ridiculous to me, as how does one learn his first spoken language if that's the case? I do think it's somewhat applicable in the context of programming, as there's no programming language sophisticated enough to match the expressiveness and instinctual understanding a spoken language provides someone.

I also disagree on it being ok to suck at math. You gotta really know mathematical induction if you want to be able to know a complicated algorithm works and terminates in a finite time. If you can't make an inductive argument, you're stuck with just putting a lot of input in and seeing if it checks out ok, and then fiddling with the algorithm when it inevitably doesn't work the first time (and you're almost never going to get it right the first time unless you've proved it correct beforehand). It's so easy to get off-by-one errors if your integer math isn't strong. Code with off-by-one errors always seems to look right.

I remember my 2nd quarter programming class used Sedgewick's Algorithms book, and I was completely lost because his arguments were of the hand-waving type and his code might as well have been in Chinese since it didn't teach you how to rigorously understand things. I didn't start getting the class until I bought the Cormen book which showed you how to prove an algorithm worked and how to analyse its performance rigorously without the hand-waving. If you don't know probability, then you've just closed the book on randomized algorithms. If you ever have to do low-level stuff in C or assembly dealing with memory, it's tough if you're not good with binary or hex representations and how p-adic arithmetic (specifically for p=2 and p=16) works. Finally, job interview questions are often going to be about algorithms, and without a strong mathematical background, it's going to be tough to be creative when it comes to procedures you can't find in a textbook or library.

---

### Post by dv3500ea on 2010-10-23
> **Eragon0605 said:**
> Basically what I'm trying to get at here is: don't limit yourself to one language. There are many, many different languages out there and each one is meant for different people and different tasks.

+1

Learning several languages will make you a better programmer.

---

### Post by ibuclaw on 2010-10-23
> **spurs21 said:**
> I also disagree on it being ok to suck at math. You gotta really know mathematical induction if you want to be able to know a complicated algorithm works and terminates in a finite time. If you can't make an inductive argument, you're stuck with just putting a lot of input in and seeing if it checks out ok, and then fiddling with the algorithm when it inevitably doesn't work the first time (and you're almost never going to get it right the first time unless you've proved it correct beforehand). It's so easy to get off-by-one errors if your integer math isn't strong. Code with off-by-one errors always seems to look right.

I suck at Math. =)

OK, that is a half lie. I used to not suck, though years of no formal practice takes its toll very quickly.

To me, being from a C-style background. Understanding process of execution; being able to deduce in my head just exactly what X does kinda comes along with that procedural/imperative thinking, and in a way is much more important.

---

### Post by StephenF on 2010-10-23
Before formulating a programming style maybe consider what type of person you are?

[http://www.myersbriggs.org/my-mbti-personality-type/mbti-basics/sensing-or-intuition.asp](http://www.myersbriggs.org/my-mbti-personality-type/mbti-basics/sensing-or-intuition.asp)

A personality preference for intuition would probably make of you a great top-down software architect while a sensing preference would suggest you would be better at creating device drivers or writing strict standards compliant modules.

If the advice in this thread seems to pull in two opposite directions it's because the answers given are right for the people making the posts and need to be taken as subjective.

---

### Post by CptPicard on 2010-10-23
> **spurs21 said:**
> The idea that one needs to frame his thought in a spoken language to think is ridiculous to me, as how does one learn his first spoken language if that's the case? I do think it's somewhat applicable in the context of programming, as there's no programming language sophisticated enough to match the expressiveness and instinctual understanding a spoken language provides someone.

We've talked about this a lot here before in, for example, the high-level vs. low-level [megathread]("http://ubuntuforums.org/showthread.php?t=851794"). There are people (like me) who pretty strongly feel that the concepts higher-level languages introduce are valuable in themselves as they increase the mental "vocabulary" of the programmer and introduce new approaches in terms of programming style for some given problem... the vocabulary of lower-level languages is more machine-specific, so in that sense you're writing things about the computer, not about your problem.

Most of the math in programming really is about logic and reasoning, arithmetic and discrete sets... but those really are basic tools in any formal, rigorous field. The more complex mathematics is related to the application domain at hand.

> Finally, job interview questions are often going to be about algorithms, and without a strong mathematical background, it's going to be tough to be creative when it comes to procedures you can't find in a textbook or library.

In most everyday programming, the problems really are not something you'll find in a textbook. It's important to understand algorithmics because it gives you a toolkit to recognize problems that are solved already and apply that knowledge to spinning variants of those solutions (I personally have a pencil-and-paper style algorithmics academic background), but when you're designing a programmatic solution to some "real-world" problem that may even be ill-specified, it is surprising how much a programming language can affect the thinking process going on in how to formulate that solution...

---

### Post by steevk on 2010-10-23
> **dv3500ea said:**
> especially if you play around with [Shoes]("http://shoes.heroku.com/"), a program which enables you to create fun little graphical apps (using the ruby language) easily.

Hey, thanks for mentioning Shoes. I also agree it's a great way to get started, but I'm a little biased...

Just so you know, the official url is [http://shoesrb.com/](http://shoesrb.com/) now.

---

### Post by SOG420 on 2010-10-23
Holy Crap Guys! I expected this thread to be dead. I just came back out of curiosity  and found 20 something replies. Thanks for all the links and opinions.

---

### Post by spurs21 on 2010-10-23
> **CptPicard said:**
> We've talked about this a lot here before in, for example, the high-level vs. low-level [megathread]("http://ubuntuforums.org/showthread.php?t=851794"). There are people (like me) who pretty strongly feel that the concepts higher-level languages introduce are valuable in themselves as they increase the mental "vocabulary" of the programmer and introduce new approaches in terms of programming style for some given problem... the vocabulary of lower-level languages is more machine-specific, so in that sense you're writing things about the computer, not about your problem.


I was mainly just taking issue with Sapir-Whorf in relation to spoken language. Natural language doesn't have the same problems expressing complex topics as say Java does expressing lambda or C supporting OOP. Plus, natural languages don't censor thought, the way say, Java does by getting rid of C++ staples like pass by reference and multiple (non-interface) inheritance.

> 
Most of the math in programming really is about logic and reasoning, arithmetic and discrete sets... but those really are basic tools in any formal, rigorous field. The more complex mathematics is related to the application domain at hand.
I agree; calc, ODE, PDE, analysis, algebra, topology, number theory, and the like from an undergrad math degree aren't too important unless you're writing something simulating a physical system, generating graphics, or perhaps something involving crypotgraphy. Still, logic, reasoning, and mathematical induction are about the most important things there are to not sucking at math, and they're at the very core of reasoning about process. I think **ibuclaw** was selling himself way short when he said he sucked at math. Maybe a better way to put things would be that one has to have strong mathematical skills, but not necessarily a broad basis of knowledge in the subject.

---

### Post by wkhasintha on 2010-10-23
Go with Python

---

### Post by CptPicard on 2010-10-24
> **spurs21 said:**
> I was mainly just taking issue with Sapir-Whorf in relation to spoken language.

Yes, we're in agreement I think. I have personally found it intriguing that I seem to be supportive of the hypothesis when it comes to programming languages, although they are theoretically proven to be equally "powerful" although they are not expressive in the same way -- and the "expressiveness" of a programming language seems hard to pin down in a rigorous way. 

On the other hand, I do not believe it to be true of natural language; it would open the door to all kinds of strange theories about users of a certain natural language being less competent in thinking about things than users of some other language... there is however some proof of some Amazonian tribes lacking exact numeric concepts, but I suspect this is just a cultural matter: they have not had the need for something like "exactly three" so they have not named it.

> Plus, natural languages don't censor thought, the way say, Java does by getting rid of C++ staples like pass by reference and multiple (non-interface) inheritance.

Well, that seems to contain the idea that the way C++ does it is somehow deeper, more insightful or "correct". Java is just defined in a different way, because things like pass by reference as they stand in C++ are perhaps not quite as relevant in a language where every object variable is of a reference type.

> I think **ibuclaw** was selling himself way short when he said he sucked at math.

Sucking at math is always relative -- most people on the planet suck at math relative to some other people, and the more they actually know math, the more aware they are of this fact. It's a very depressing subject in this regard ;) I am very aware that I suck at math compared to my CS PhD friend for example...

> 
 Maybe a better way to put things would be that one has to have strong mathematical skills, but not necessarily a broad basis of knowledge in the subject.

I'd say that primarily one needs capacity for rigorous formal reasoning about abstract things and systems. Mathematical ability tends to correlate very strongly with this, of course.

---

### Post by ibuclaw on 2010-10-24
> **spurs21 said:**
> I think **ibuclaw** was selling himself way short when he said he sucked at math.

Well that's my life story right there... :)

> **CptPicard said:**
> Sucking at math is always relative -- most people on the planet suck at math relative to some other people, and the more they actually know math, the more aware they are of this fact. It's a very depressing subject in this regard ;) I am very aware that I suck at math compared to my CS PhD friend for example...


I believe it's called the Dunning&#8211;Kruger effect

---

