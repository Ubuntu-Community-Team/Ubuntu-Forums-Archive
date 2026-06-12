---
title: "how do I practice programming logic for a beginner?"
date: 2013-06-25
forum: Programming Talk
---

### Post by pavelexpertov on 2013-06-25
Hi, I started doing java programming 6 months ago, but I managed to learn more basics for the last two months dur to huge interest in coding. Also I started reading info on oracle's tutorials and I managed to complete exercises provided by the website.... but I was put off slightly when I tried to make a class whose instances represented a deck of cards. When I couldn't manage,  I looked at correct answers. I was a bit horrified with sophisticated, but even simple coding from the answer and I felt so stupid because of that. I did have a look for ways to improve, but they were a bit over the top for me, coz it involved learning anpther language or improving code than logic. So I was wondering how you guys manage to build your logic for programming? Thank u for taking to read my post!

---

### Post by Vaphell on 2013-06-25
practice makes the master
in the beginning the brain gets overloaded and overwhelmed easily and there is no way around that. Just step back a bit in complexity, write few more programs to get more confident and try that deck of cards again. Even if you still won't write it on your own, it's very possible that someone else's code will be undestandable enough to be enlightening and open a new path in your thinking.
When you think about your program try to break it to manageable blocks and tackle them one at a time.

---

### Post by TheFu on 2013-06-25
The best way to learn is to follow others and emulate them. Follow can happen in many different ways:
* schooling/classes
* reviewing other peoples' code
* reading books from the "experts"
* reading magazines specific to your area of coding and/or langauge
* joining local groups of like-minded people and having frank discussions
* working in the field - i.e. practice.

The more you learn, the more you will appreciate that some people are coding-poets.
There is nothing like practice to make you better at anything.  Back when I was coding A LOT, anything that I'd written 2 months ago was crap, I knew it, but if you looked at the stuff I'd done today - it was beautiful, elegant, efficient, easy to understand even by the most dullard person.  Of course, in 2 months it would seem like crap to me ... 

Anyway, don't be afraid to post your crap code and get feedback.  I was lucky.  At my first professional job, we were required to have formal design, code and test reviews with 3 other peers. These included written issues submitted before the meeting with a signature from each reviewer to ensure they did actually review it and were confident they didn't miss anything.  This is strange for most environments - where the only review is "does it work" and does QA see anything wrong.  Team programming was supposed to make code better, and I suppose it does.

Also, review coding standards documents for each language. Inside those you will find smart ways to make your code defensive and fail as close to where the issue is as possible, instead of letting the code continue, for hours- days - months before that error is experienced.

Didn't reread this post - hope it makes sense.  Practice. Practice. Practice.  Just like musicians.

---

### Post by pavelexpertov on 2013-06-25
Thanx guys, just a minute ago I stepped back just to think over what I am doing with the task of creating a deck of cards. I think I am getting a bit of it done, but I think it's not gonna work due to the goal of the task :/

---

### Post by TheFu on 2013-06-25
> **pavelexpertov said:**
> Thanx guys, just a minute ago I stepped back just to think over what I am doing with the task of creating a deck of cards. I think I am getting a bit of it done, but I think it's not gonna work due to the goal of the task :/

That is a common thing.  You are learning 2 things right?  Programming and OOD?  I was lucky - back when I was learning, very few people had even heard of OOD at all, so everyone used function and structures to code.  I'd programmed 8+ yrs before touching anything OOD.  When OOD came along, there were lots of classes that were not language specific .... I don’t think I could have learned that on my own from books. The concept was too foreign to me.  Any class can teach it - doesn't need to be a name-brand college class - took mine at a local community college.  Since then, I like to say, if you want to become a priest, you need to go to a monastery.  I think the same applies to learning OOD - BTW, that is Object Oriented Design.  I still have the OOD Booch book here and refer to the diagrams for UML on the inside font and back covers.

I'd also say that I've never, ever, attempted to make a class hierarchy for a deck of cards. My 1st questions would be 
* is a single card the base-class or is the deck a base-class?
If I were trying to do this, I'd look online for other class diagrams to see a few different options and look for wholes in each design.

My OOD classes were taught near a NASA flight center, so our beginning design and programming exercises where about satellites and space ships moving around a planet that needed to be "captured."  Teach to your audience, right?

---

### Post by Vaphell on 2013-06-25
yes, java is indeed rather rigid because it forces you to do everything with objects. Maybe you could try let's say python which is not as rigid, doesn't require as much boilerplate code and has tons of nifty syntactic shortcuts.

---

### Post by pavelexpertov on 2013-06-25
> **TheFu said:**
> That is a common thing.  You are learning 2 things right?  Programming and OOD?  I was lucky - back when I was learning, very few people had even heard of OOD at all, so everyone used function and structures to code.  I'd programmed 8+ yrs before touching anything OOD.  When OOD came along, there were lots of classes that were not language specific .... I don’t think I could have learned that on my own from books. The concept was too foreign to me.  Any class can teach it - doesn't need to be a name-brand college class - took mine at a local community college.  Since then, I like to say, if you want to become a priest, you need to go to a monastery.  I think the same applies to learning OOD - BTW, that is Object Oriented Design.  I still have the OOD Booch book here and refer to the diagrams for UML on the inside font and back covers.

I'd also say that I've never, ever, attempted to make a class hierarchy for a deck of cards. My 1st questions would be 
* is a single card the base-class or is the deck a base-class?
If I were trying to do this, I'd look online for other class diagrams to see a few different options and look for wholes in each design.

My OOD classes were taught near a NASA flight center, so our beginning design and programming exercises where about satellites and space ships moving around a planet that needed to be "captured."  Teach to your audience, right?

when you do OOD, do you make a first plan by making flow charts and then writing draft classes to see if they follow planned functions?

---

### Post by pavelexpertov on 2013-06-25
> **Vaphell said:**
> yes, java is indeed rather rigid because it forces you to do everything with objects. Maybe you could try let's say python which is not as rigid, doesn't require as much boilerplate code and has tons of nifty syntactic shortcuts.

I honestly wish I could have started with python, but I want to learn java so I can learn programming in android. This is because I feel I want to become mobile independent app developer and I have lots of free time due to my age and few responsibilities. Furthermore, I am getting UDOO, so I might get a chance to play with python or C++ :D.

---

### Post by TheFu on 2013-06-25
> **pavelexpertov said:**
> when you do OOD, do you make a first plan by making flow charts and then writing draft classes to see if they follow planned functions?

Flow charting is not for OOD, it is for procedural programming. When just starting out, that isn't often clear.

Not flow charts, but class diagrams and scenarios/use cases.  Flowcharts come much later - actually, I usually just use code comments to cover the major parts of any method/function.  That doesn't always work out, since big ideas usually take more code than a method or function can hold, so I have to add a few helper_methods inside the class.

When I actually write class methods, I force them to be 20 lines or less - small, easily testable, and easily understood. If a method/function doesn't fit onto a single screen, it is too long.  This, more than any other tip, has made me a better programmer.  Also, method naming is an art form.  I try to always name the method such that the returned data answers a question.  IsFaceCard() would be an example.

---

### Post by TheFu on 2013-06-25
> **pavelexpertov said:**
> I honestly wish I could have started with python, but I want to learn java so I can learn programming in android. This is because I feel I want to become mobile independent app developer and I have lots of free time due to my age and few responsibilities. Furthermore, I am getting UDOO, so I might get a chance to play with python or C++ :D.

Programming based on your "itch" is a great idea. I wish you luck for starting with Java and Android. It is a fairly advanced topic. Android programming is unlike any other coding that I've done, with all sorts of odd ways (non-standard for any of the other 15 platforms I've coded on) the environment forces things to be handled.  I can't imagine trying to learn to program in Java AND Android at the same time.

When asked "how to learn to code" the last 2 yrs, I tell people to start with Python - though I don't know that language.  I'm from a different generation.  Python forces good coding style and has everything that a new programmer needs to learn ... except the compiling aspects of non-scripted languages.  [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program) explains and a few highly experienced Java programmers left their comments.

OTOH, Java has been taught in schools for 10 yrs as the beginning programming language. I'm from a pre-Java time - before the language existed.

---

### Post by Vaphell on 2013-06-25
play with python if only for few days and see if it influences your java negatively.
It has much higher fun/grind ratio so if you need fun to keep you going, python might be better to get you through the initial stages of the road to programming mastery. And it's not like it would be a total waste of time (even if it's not really your thing) because it's perfect for whipping up smallish programs to automate some everyday tasks, not unlike shell scripts. If you need results quick, there's your tool.

---

### Post by King Dude on 2013-06-27
Well, what a lot of people overlook is the connection between mathematics and programming. If you would like to improve programming logic, try improving your mathematics skills (specifically Algebraic equations with variables, and If-Then statements. Perhaps Geometry, Trigonometry, and Calculus if you're programming animated figures and simulated physics) before you begin tweaking your language specific code.

You may also consider using Python. I know you'd probably prefer C++ or Java, but the reason I suggest Python is because it's simpler and can later be used alongside C++ and Java as an extension. 
Here's two links to this website called Khan Academy. It helps with Mathematics, and teaches some Python in the Computer Science section.
[https://www.khanacademy.org/library#computer-science](https://www.khanacademy.org/library#computer-science)
[https://www.khanacademy.org/library#math](https://www.khanacademy.org/library#math)

And truth be told, sometimes the best way to learn is to get your hands on some source code and begin to experiment by cutting and replacing sections of the code to see what happens.

---

### Post by pavelexpertov on 2013-06-28
> **TheFu said:**
> Programming based on your "itch" is a great idea. I wish you luck for starting with Java and Android. It is a fairly advanced topic. Android programming is unlike any other coding that I've done, with all sorts of odd ways (non-standard for any of the other 15 platforms I've coded on) the environment forces things to be handled.  I can't imagine trying to learn to program in Java AND Android at the same time.

When asked "how to learn to code" the last 2 yrs, I tell people to start with Python - though I don't know that language.  I'm from a different generation.  Python forces good coding style and has everything that a new programmer needs to learn ... except the compiling aspects of non-scripted languages.  [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program) explains and a few highly experienced Java programmers left their comments.

OTOH, Java has been taught in schools for 10 yrs as the beginning programming language. I'm from a pre-Java time - before the language existed.

Thanx for your input, but also I wanted try to code apple apps as well when I get good experience and knowledge for android. I think its not too hard to learn another language when you know the basics of oop, despite syntax is well different :/.

---

### Post by r-senior on 2013-06-28
> **pavelexpertov said:**
> ... I wanted try to code apple apps as well when I get good experience and knowledge for android. I think its not too hard to learn another language when you know the basics of oop, despite syntax is well different :/.
If you start working on Apple devices, you'll find that Objective-C syntax is well well different. ;)

Fun though, and Xcode is a great IDE.

---

### Post by flowers92 on 2013-06-30
Agreed i feel like if you can java you can do anything, but learning python first or at the same time even would negatively influence your java. The world would be a much better place if everything was simple as python though. 

You can always take it slow and steady and go to school for it by spending a year's salary lol ill help you a little [http://training.linuxfoundation.org/free-linux-training/linux-training-scholarship-program](http://training.linuxfoundation.org/free-linux-training/linux-training-scholarship-program) [http://www.collegespirit.me/scholarships/](http://www.collegespirit.me/scholarships/)

---

### Post by trent.josephsen on 2013-06-30
> **flowers92 said:**
> Agreed i feel like if you can java you can do anything, but learning python first or at the same time even would negatively influence your java.

Not at all. The problem with Java is not its complexity or that people don't understand it; the problem with Java is that when coders don't know how to *solve problems*, it leads them into creating ever more deeply nested class hierarchies and IteratorStateAbstractFactoryBuilders rather than reconsider the original approach. Python encourages one to think about problems simply, which is exactly the antidote to the Java mindset. Unless you're thinking of syntactic differences like self/this or semicolons, the only reason learning Python would harm your ability to write Java is because you'll spend so much time wishing you could use Python instead. (Aside: since stuff like Jython exists, this is not always impossible.)

I also don't know what "if you can java you can do anything" is supposed to mean, or how Java is different from C, Perl, Python or C# in this regard. I can certainly think of plenty of projects for which I would not use Java nor hire a Java programmer, even a particularly skilled one. If you just mean that Java is a solid foundation for learning other languages, I'll concede the point, but I certainly don't think it's better at that than most other languages.

---

### Post by TheFu on 2013-06-30
Languages are not good or bad, but specific implementations of each language definitely are.

<rant>

IMHO, finding a "good implementation" of Java is nearly impossible. All of them that I know are slow and abuse RAM, which is exactly the opposite of what a good implementation does.  Ruby has that issue too, but is getting better about it.  C is a wonderful language with many fantastic implementations.  I understand that C# is great too, but I am not a fan of "managed code."

There are only a few places where I would seek the use Java.
* Enterprise applications that must run on 5+ different platforms.
* Android - there isn't really any choice.

Besides those specific needs, I'd use the fastest language to code with. today, python might be that language.

For many years, Java was used as THE teaching language, which seems to have produces a bunch of mediocre programmers.  Pascal was THE teaching language before that and FORTRAN was before that. Each sucked in a special way.  Today, Python is not just the language used to teach programming, but it is a beloved language by many and hated by very few.  Heck, the things that I hate about Python is the mandated use of indentation. Seems dumb to me, when a {} pair easily groups things. I'll get over it.

Java looks very much like my loved C++, so it isn't the look of the language that bothers me. It really is just the terrible implementations that suck CPU and RAM.

I've worked in large enterprises where Java was the preferred language on over 200 different projects.  I've met many mediocre Java programmers.  Honestly, everyone starts out as a terrible programmer.  A very few become "artists", but the majority get only to "competent" level after 5-10 yrs.  Learning to code is 20% of being a good programmer, maybe less.

If you search github or sourceforge, you'll find many projects that are java which shouldn&#8217;t be.  Why?  Hammer/nail.
</rant>

I'll try to find **my happy place** now. It will be ok. Promise.

---

