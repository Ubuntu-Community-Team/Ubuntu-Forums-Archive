---
title: "What is it that makes a language good?"
date: 2011-03-12
forum: Programming Talk
---

### Post by Gerontion on 2011-03-12
Not as in 'What's a good language to learn?' but simply, what is it about a programming language which makes you think it's good? By way of background, I'm very new to programming and have been learning through ActionScript 3 (mainly because, as someone who can turn a computer on without breaking it, I've been deemed 'good at computers' and have thus been asked to write some elearning software) so I've got no axe to grind...but at the same time, although I'm rather taken by programming, I've got but no real basis for understanding what it is that gets everyone excited about, for example, Python (or C++ or whatever it is) as opposed to any other language.

---

### Post by slooksterpsv on 2011-03-12
Something that is readable without having to make it readable. Something that is powerful, but simple. Something that has automatic memory management so if you "forget" you don't get leaks. Being able to use descriptive variables and functions.

E.g.

```

...
def permutation(n):
 if n <= 1:
  return 1
 else:
  return n * permutation(n-1)
...

```

And not:
```

...
int p(int n)
{
 if(n <= 1)
  return 1;
 else
  return n * p(n-1);
}
...

```

Tech. two different languages, but look how confusing that can be - what is p? What does p do? And you gotta read through it to figure it out.

Designer friendly I think is a good one, not just GUI, but how you implement it. It should be cross-platform, able to integrate well.

I dunno what else I can say, but those are my thoughts.

---

### Post by NovaAesa on 2011-03-12
> **slooksterpsv said:**
> what is p? What does p do? And you gotta read through it to figure it out.

That's hardly fair, a true comparison would have both procedures named p or both procedures named "permutation", or better yet "factorial".

IMO, a good language is one that has the correct abstraction level for the job you are planning to use it for. Aside from that,  orthogonality, simplicity, good data structures and data types, abstraction support, and expressivity are the big ones for me.

---

### Post by CptPicard on 2011-03-12
This is a question that seems to divide people into camps; but for me it is a combination of 

[LIST]
[*] Simplicity: having a small number of basic elements or concepts in the language,
[*] Genericity: The concepts are generic in the sense they cover as much ground as they can within their own scope when combined with the other things in the language
[*] Consistency: Things work logically in their various combinations, not having lots of "gotchas" you just have to know.
[*] Orthogonality: The concepts in the language do their own thing and are not confuddled with the responsibilities of other concepts; together with genericity this allows for putting them cleanly together into new concepts.
[/LIST]


The result of the above tends to be general *expressiveness*, meaning the language is amenable to defining your own abstract, high-level things that, hopefully, again demonstrate the qualities of genericity, orthogonality and  consistency.

IMO, there really is no beating Lisp in this... it's incredibly simple, as well.

---

### Post by shawnhcorey on 2011-03-12
What makes a language good is one that is written to deal with your problem domain.

What is a good language for a newbie to learn programming?  One of the scripting languages:  Perl, Python, Ruby, or PHP.

---

### Post by cgroza on 2011-03-12
> **slooksterpsv said:**
> 
E.g.
```

...
def permutation(n):
 if n <= 1:
  return 1
 else:
  return n * permutation(n-1)
...

```And not:
```

...
int p(int n)
{
 if(n <= 1)
  return 1;
 else
  return n * p(n-1);
}
...

```

Ohh, you mean python, but C++ is a good language too.
But that depends on the task you need to achieve.

---

### Post by nvteighen on 2011-03-12
Good in what sense?

I guess it's about what makes a programming language a well-designed one, I think CptPicard summarized it very well. Languages are symbolic systems of expression.

So, IMO, a good programming language has to allow its users to express what they want in simple ways that add the less amount of redundant elements in the semantics... and it makes the syntax reflect that fact.

That summarizes quite well my dislike for C++. Redundant semantics and convoluted syntax... :P

Now more seriously: it's the KISS "principle". Programming and formal thinking is hard enough, so a well-designed programming language should try not to be an additional obstacle by adding irrelevant features/requirements that don't add anything substantial to achieve the expression of the programmer's thoughts. Also, the more features you add, the more likely that your language becomes an incoherent mess.

---

### Post by CptPicard on 2011-03-12
> **shawnhcorey said:**
> What makes a language good is one that is written to deal with your problem domain.

You know, if we go down the path that the best language is the most domain-specific one, IMO the whole discussion loses its relevance. We might have a language that is so specific that it establishes the requirements of some very restricted domain by calling a single function, but that would no longer be a general-purpose (read: Turing complete) programming language that could be used for other tasks, too.


> **nvteighen said:**
> 
I guess it's about what makes a programming language a well-designed one, I think CptPicard summarized it very well. Languages are symbolic systems of expression.

It's taken like five years and and countless posts to establish my "theory of good programming language", and there it is ;)

> 
Now more seriously: it's the KISS "principle". Programming and formal thinking is hard enough, so a well-designed programming language should try not to be an additional obstacle by adding irrelevant features/requirements

Yeah, just simply adding "features" threatens all the properties I listed above. A good language should have all it needs, and nothing more.

---

### Post by laceration on 2011-03-12
I agree that C is not "good" for the reasons stated, but if you want to get into the guts of Linux or most other major programs you've got to know it.  If you just want to be a web programmer it's not necc.

---

### Post by shawnhcorey on 2011-03-12
> **CptPicard said:**
> You know, if we go down the path that the best language is the most domain-specific one, IMO the whole discussion loses its relevance. We might have a language that is so specific that it establishes the requirements of some very restricted domain by calling a single function, but that would no longer be a general-purpose (read: Turing complete) programming language that could be used for other tasks, too.

I think you worry too much.  I have yet to see a language that's useful and isn't Turning complete.  What I meant was a language that has features designed to deal with the problem domain.  It is very useful if you can express a complex data structure in one line of code.

However, I also said that these languages are not for learning how to programming simply because they have many extras features beyond being Turing complete.  A general-purpose language that you can use to do useful things in a few lines is best for learning to program.

---

### Post by wmcbrine on 2011-03-12
Python is good because it doesn't waste my time. Thought -> code.

C is good because it's tight and clean.

C++ and Java are good because... well, I'm sure I could come up with a reason eventually.

laceration: I guess you were "agreeing" with nvteighen (?), but he said "C++", not "C". Huge difference.

---

### Post by CptPicard on 2011-03-12
> **shawnhcorey said:**
> I think you worry too much.  I have yet to see a language that's useful and isn't Turning complete.

Well, HTML is handy for specifying web pages and it's not a programming language... but really, I was just trying to make a general point regarding problem domain specific features. The argument can be taken to an extreme that demonstrates the problem with the thinking. 

> 
  What I meant was a language that has features designed to deal with the problem domain.  It is very useful if you can express a complex data structure in one line of code.

The interesting and IMO justifiable features in a programming language are not domain specific, but general-purpose programming abstractions that apply everywhere. Even data structure implementations become easier to handle with these kinds of languages even though you might not have some library containing them outright (you can always write one for any Turing-complete language).

> 
However, I also said that these languages are not for learning how to programming simply because they have many extras features beyond being Turing complete.

Well, a machine language that contains simply a "compare and jump" instruction is Turing complete, is very lacking in features, and would be awful for learning to program. Also, a language that contains loads of features that do not really advance general-purpose programming by their very existence, is also awful to learn to program in, because you have to learn stuff that isn't relevant to all of your programming tasks.

> A general-purpose language that you can use to do useful things in a few lines is best for learning to program.

Yes, if it's not merely a matter of making use of a vast standard library. There are general programming conceptuals and patterns that are good to have in a good learning language (mind you, those are good languages, period), and the rest, especially the domain-specific stuff, doesn't matter, in particularly for the learner.

---

### Post by 23Andrew on 2011-03-12
I like Python because it's easy, and efficient, for small calculations or cleanup jobs around the computer.

I like C++ because it is powerful, and similar in syntax to many 
other languages, making it a good place to start.

And I like PHP, simply because of what it's used for, server side processing. It does the job well, and it feels nice to type, except starting all of the variable names with a '$' sign (as in perl).

Those are my three favourite languages. They are all really popular so it's easy to find support for them.

Hope that helps.

---

### Post by nmaster on 2011-03-12
> **slooksterpsv said:**
> Something that is readable without having to make it readable. Something that is powerful, but simple. Something that has automatic memory management so if you "forget" you don't get leaks. Being able to use descriptive variables and functions.

E.g.

```

...
def permutation(n):
 if n <= 1:
  return 1
 else:
  return n * permutation(n-1)
...

```

And not:
```

...
int p(int n)
{
 if(n <= 1)
  return 1;
 else
  return n * p(n-1);
}
...

```

Tech. two different languages, but look how confusing that can be - what is p? What does p do? And you gotta read through it to figure it out.

I agree that programming in C can be difficult sometimes, but this example does not really explain why.  You showed two functions that do the same thing, and are written in almost *exactly* the same way.  You just changed the name in the C program to make it look cryptic. As a result, the example is neither fair nor illustrative.

---

### Post by Gerontion on 2011-03-12
Hmm. Thanks for your answers. I feel somewhat more enlightened but I guess it's a bit like being presented with a glass of wine for the first time in your life and expecting to detect the cheek and impudence of a Chardonnay skipping over notes of buttery vanilla - or whatever rubbish it is that wine reviewers come out with. I imagine a lot of this comes down to the craft-like expertise you get from being an expert (which is clearly what most of you are), rather than some easily formulated set of propositions which, without the expertise, are largely meaningless (which is sadly the position I'm in!)

---

### Post by CptPicard on 2011-03-12
> **Gerontion said:**
> rather than some easily formulated set of propositions which, without the expertise, are largely meaningless (which is sadly the position I'm in!)

I formulated an exact set of propositions for your consideration. Which of them do you feel like you disagree with?

---

### Post by YesWeCan on 2011-03-12
A different angle...

A good programming language makes it as hard as possible for you to make mistakes, either syntatic or structural.

A good programming language is (other) human readable and reviewable, with all that may imply.

Another way of saying this is that a good language should frustrate the hell out of hackers. C is a hackers language.

---

### Post by shawnhcorey on 2011-03-12
> **CptPicard said:**
> Well, HTML is handy for specifying web pages and it's not a programming language... but really, I was just trying to make a general point regarding problem domain specific features. The argument can be taken to an extreme that demonstrates the problem with the thinking. 


Yes, it can be taken to extremes.  But studies have shown that a programmer creates the same number of lines of well-written, almost-bug-free code per year regardless of the language.  So a programmer using one that allows him to express solutions with only a few statements, will be more productive than a general-purpose language.

Now you can say that the programmer can use a library, but most of the ones I've seen are so badly documented that it is often faster for the programmer to create his own.  It's only when the library becomes so popular that everyone knows it, does it get good documentation.  Which is so of redundant since everyone knows it.  :)

---

### Post by CptPicard on 2011-03-13
> **numinous said:**
> 
Those dizzying tons of parenthesis just make one wonder why Lisp ended up like that.

You should indeed reflect on that if you do not understand why they're there. There's a [deep reason]("http://en.wikipedia.org/wiki/Homoiconicity") for them, and the parenthesis do not in the end matter. They actually kind of visually disappear when you get used to them :)

> **shawnhcorey said:**
> But studies have shown that a programmer creates the same number of lines of well-written, almost-bug-free code per year regardless of the language. So a programmer using one that allows him to express solutions with only a few statements, will be more productive than a general-purpose language.

I very much agree with the first part, but not the latter. As far as this discussion goes, I'm not really even interested in non-general-purpose languages; what we're talking about really is relevant only in the context of general-purpose languages -- special-purpose languages will always be tailored to their niche, but the specialization becomes a hindrance in writing other kinds of code.

> 
Now you can say that the programmer can use a library, but most of the ones I've seen are so badly documented that it is often faster for the programmer to create his own.

I'm not sure I understand how this is relevant to the point I'm trying to make...

---

### Post by Gerontion on 2011-03-13
> **CptPicard said:**
> I formulated an exact set of propositions for your consideration. Which of them do you feel like you disagree with?

I neither agree nor disagree with any of them. As I said, I just don't have the expertise to make an intelligent judgement about this so your post is - for me - largely meaningless. I made an analogy with wine tasting earlier and I think it probably holds sufficiently well - you could be given a perfectly comprehensible (and comprehensive) set of criteria for judging wines but if you just lack any real experience with wine, those criteria aren't going to get you very far and I'm in almost exactly the same position with programming languages. On reflection, it was rather a stupid thread for me to start, as I'm almost completely unqualified to appreciate any of the answers.

---

### Post by CptPicard on 2011-03-13
> **Gerontion said:**
> As I said, I just don't have the expertise to make an intelligent judgement about this

Yes, I see.

As I see them, the criteria I provided are pretty commonsense in the way that one should be able to evaluate them without deep domain knowledge. I'll be happy to elaborate if you have questions :)

---

### Post by Gerontion on 2011-03-13
Your first post certainly does make sense - once I discovered what orthogonal meant in this context - and it was, in fact, the concision and precision of your post which made me realise that my lack of knowledge/experience onto which I could map your four criteria rendered my initial question pointless. To run my analogy completely into the ground, clearly what I need to do is to drink more wine.

---

### Post by ve4cib on 2011-03-13
In my view the ultimate test of whether or not a language is good is if the answer to the question "Does it do what I need it to do?" is yes.

If whatever language you happen to choose to use does what you need it to do, and you can write the program you need without too much hassle then it's a good language for your purposes.


A good secondary consideration is how easy it is for other people to read and understand (and maintain/debug) your code.  This is a much more grey area, since a good programmer can make Perl, Lisp, or Prolog look clear, and a bad programmer can make Python an obfuscated mess.

Certain languages are much easier to keep clean and tidy than others.  Python, with its enforced indentation, is generally one of the better ones.  Javascript on the other hand is probably the single worst language I've ever encountered from this perpective.  Nobody seems to write good Javascript.


Just to chime in on the "Lisp syntax is ugly" thing...

I'd argue that Lisp's syntax is the simplest, clearest, and easiest to understand of virtually any language.  You have lists.  They're evaluated recusively, with the function name in the first position, and the parameters following.  The entire list is contained in parentheses.  That's it.  It's so simple and straight-forward.

Granted, it looks a little intimidating when it's written badly.  This is where good indentation and parenthesis alignment is essential.  Simple Lisp code can be completely illegible if it's not formatted well.  But complex Lisp code can be pretty simple if the person writing it actually hit the enter and tab keys once in a while.

---

### Post by cgroza on 2011-03-13
> **wmcbrine said:**
> 

C++ and Java are good because... well, I'm sure I could come up with a reason eventually.

laceration: I guess you were "agreeing" with nvteighen (?), but he said "C++", not "C". Huge difference.
Because C++ brings OOP to C. And Java is good because I feel cool when I write it.

---

### Post by alegomaster on 2011-03-13
A good language should have some(if not all) of these traits:

Fast speed/Quick execution

Easy Syntax

Good libraries built in

Good portability 



There are other ones but these are some of the key traits.

---

### Post by rnerwein on 2011-03-14
> **Gerontion said:**
> Not as in 'What's a good language to learn?' but simply, what is it about a programming language which makes you think it's good? By way of background, I'm very new to programming and have been learning through ActionScript 3 (mainly because, as someone who can turn a computer on without breaking it, I've been deemed 'good at computers' and have thus been asked to write some elearning software) so I've got no axe to grind...but at the same time, although I'm rather taken by programming, I've got but no real basis for understanding what it is that gets everyone excited about, for example, Python (or C++ or whatever it is) as opposed to any other language.
hello
you ask "what's a good language to learn". my opinion is: ( oh i don't want to be  your teacher ) first you have to
really learn how a computer works - what i mean is: it's only the syntax of different programming languages.
but it's always the same -> there is only "0 and 1" nothing else.
i always told my students ( 30 years ago ) the computer is i high speed idiot. 
learn the basics - assembly, c and understand what's going on in your box the rest are penatus ( if the OP system is ok).
ciao

---

### Post by andrew1992 on 2011-03-14
> **rnerwein said:**
> hello
you ask "what's a good language to learn". my opinion is: ( oh i don't want to be  your teacher ) first you have to
really learn how a computer works - what i mean is: it's only the syntax of different programming languages.
but it's always the same -> there is only "0 and 1" nothing else.
i always told my students ( 30 years ago ) the computer is i high speed idiot. 
learn the basics - assembly, c and understand what's going on in your box the rest are penatus ( if the OP system is ok).
ciao

I have to disagree with this. Sure, assembly and C are widely used in industry and teach some of the lower level programming concepts, but it is by no means a good place to start; these can be learned later on. For learning, what's wrong with Python's

```
print "Hello, world!"
```

It sure beats the C++ version:

```

#include <iostream>

int main()
{
    std::cout << "Hello, world!" << std::endl;
    return 0;
}

```

To offer my humble opinion, worrying about ugly syntax and memory management, aside from having to "re-invent the wheel", is useful for programmers who have knowledge of the basic concepts to hone their skills. Until then, leave that stuff alone and focus on data structures, logic and control flow. For these elementary concepts, not having to worry about all that other junk makes it a whole lot easier, and makes programming in general a whole lot more appealing. I suggest you start with learning Python or Ruby, because I highly doubt your task will require the speed of C or assembly. Just have fun, and learn the basics first!

---

### Post by robots.jpg on 2011-03-14
For me, readability comes first.  If I look at a code snippet, a  library, or even a module I wrote years ago, how much effort does it  take to understand what's going on?  If I'm reading code with a bunch of  mistakes written by someone with terrible style, can I still tell what  the person was *trying* to do?  

Flexibility is also nice, but only to the point that it doesn't  undermine the readability too much.  It's nice to have the option to  reduce a small block of code into a single line, but I always find it  discouraging when the most efficient way of solving a problem in a  particular language ends up being the most difficult to decipher.  Ideally, you should be able to look at the code and say, "Dang, why didn't I think of that?"


Of course you'll find it easier to read any language the longer you work with it, but it really accelerates the learning process when you can look at some source and understand it without already being at the level where you could have written it yourself.

---

### Post by shawnhcorey on 2011-03-14
> **robots.jpg said:**
> Of course you'll find it easier to read any language the longer you work with it, but it really accelerates the learning process when you can look at some source and understand it without already being at the level where you could have written it yourself.

If you want to learn to read badly written code, subscribe to a beginners' list.  You find mistakes you could never have thought of.  :)

---

### Post by forrestcupp on 2011-03-14
The answer is simple.

The thing that makes a language good is if it's the best language to get a specific job done. Each language has strengths and weaknesses, and there is no one language that is perfect for every problem that needs to be solved. I might use C++ with Ogre3D and other libraries to create a 3D game or some app that requires speed, while using C# to quickly create a decent GUI app for Windows. If I'm working in Linux, it might be better for me to create that same GUI app using Python and PyGTK. At the same time, I might need to throw together a personalized app for my Android, in which case, I'd have to use Java with the Android SDK.

I always scoffed at Visual Basic. Then recently, I realized that Visual Basic was the perfect tool to throw together a quick app to help my mother-in-law out on her old Windows Mobile phone. I could have wasted my time working it all out in C++, but why waste my time?

A good language is whatever is the best tool for the job at hand.

---

### Post by schauerlich on 2011-03-14
> **forrestcupp said:**
> I always scoffed at Visual Basic. Then recently, I realized that Visual Basic was the perfect tool to throw together a quick app to help my mother-in-law out on her old Windows Mobile phone.

Did she need to [track down the killer's IP address](http://www.youtube.com/watch?v=hkDD03yeLnU)? I hear VB is good for that.

---

### Post by andrew1992 on 2011-03-14
> **forrestcupp said:**
> The answer is simple.

The thing that makes a language good is if it's the best language to get a specific job done. Each language has strengths and weaknesses, and there is no one language that is perfect for every problem that needs to be solved. I might use C++ with Ogre3D and other libraries to create a 3D game or some app that requires speed, while using C# to quickly create a decent GUI app for Windows. If I'm working in Linux, it might be better for me to create that same GUI app using Python and PyGTK. At the same time, I might need to throw together a personalized app for my Android, in which case, I'd have to use Java with the Android SDK.

I always scoffed at Visual Basic. Then recently, I realized that Visual Basic was the perfect tool to throw together a quick app to help my mother-in-law out on her old Windows Mobile phone. I could have wasted my time working it all out in C++, but why waste my time?

A good language is whatever is the best tool for the job at hand.

I couldn't agree more, I just focused my answer upon what the original poster's task seemed to require.

---

### Post by forrestcupp on 2011-03-14
> **schauerlich said:**
> Did she need to [track down the killer's IP address](http://www.youtube.com/watch?v=hkDD03yeLnU)? I hear VB is good for that.

Lol. That's a classic.

---

### Post by jon zendatta on 2011-03-15
> **CptPicard said:**
> This is a question that seems to divide people into camps; but for me it is a combination of 

[LIST]
[*] Simplicity: having a small number of basic elements or concepts in the language,
[*] Genericity: The concepts are generic in the sense they cover as much ground as they can within their own scope when combined with the other things in the language
[*] Consistency: Things work logically in their various combinations, not having lots of "gotchas" you just have to know.
[*] Orthogonality: The concepts in the language do their own thing and are not confuddled with the responsibilities of other concepts; together with genericity this allows for putting them cleanly together into new concepts.
[/LIST]
IMO, there really is no beating Lisp in this... it's incredibly simple, as well.
Yeah, it does what you require!:KS

---

### Post by The Titan on 2011-03-15
> **forrestcupp said:**
> The answer is simple.

The thing that makes a language good is if it's the best language to get a specific job done. Each language has strengths and weaknesses, and there is no one language that is perfect for every problem that needs to be solved. I might use C++ with Ogre3D and other libraries to create a 3D...

I too could not agree more. As a web programmer I have a hard time with languages like C and C++(mainly C++) just because of the way my mind works.  Does it make it a bad programming language? Absolutely not, I love my video games that are mostly written in C++.

But at any rate, A good programming language is one that fits the task, nothing more nothing less.

---

### Post by Simian Man on 2011-03-15
> **shawnhcorey said:**
> I think you worry too much.  I have yet to see a language that's useful and isn't Turning complete.  What I meant was a language that has features designed to deal with the problem domain.

I guess all those people working with SQL are wasting their time on a useless language then huh?

---

### Post by shawnhcorey on 2011-03-15
> **Simian Man said:**
> I guess all those people working with SQL are wasting their time on a useless language then huh?

Yup.  SQL is about the ugliest excuse for a language that I have ever seen.  Rather than having an API, every database must have a parser and every application that uses it, a code generator.  Not only does this slows things down, it leaves you open to code injection.  SQL as an API is just a bad idea.

---

### Post by pbpersson on 2011-03-15
If you want to create desktop applications that can run anywhere without any further work I would recommend Java.  "Write once, run everywhere" is what they say.

You can also write applications for Android phones  :D

In theory if you write applications in C#.NET (which looks very much like Java) you can run them on Windows and also (maybe) get them to compile in Mono so you can run them in Linux.

I like portability.....why limit yourself to one platform?

However, if you are writing for the web that opens a whole new world of possibilities since the code is running on the web server under Apache or IIS or on the client machine in the browser - then you are talking ASP.NET, PHP, Javascript, etc.

---

### Post by forrestcupp on 2011-03-15
> **shawnhcorey said:**
> Yup.  SQL is about the ugliest excuse for a language that I have ever seen.  Rather than having an API, every database must have a parser and every application that uses it, a code generator.  Not only does this slows things down, it leaves you open to code injection.  SQL as an API is just a bad idea.

Tell that to my wife. The majority of her job involves SQL. There are ways to prevent code injection.

---

### Post by shawnhcorey on 2011-03-15
> **forrestcupp said:**
> There are ways to prevent code injection.

That's not the point; the point is if it had a proper API, code injection would be impossible.

I don't like languages that make more work for me.

---

### Post by Reiger on 2011-03-15
SQL is to the database what POSIX sh is to a Unix server. It is meant to be handled with care, and it is the tool designed for admins -- not applications. 

Applications can use the database API, which is typically written in C. It so happens that most databases expose the “console” as it were so applications can use a driver library to inject and evaluate SQL instead of dealing with the proper API themselves. But this is a shortcut, and this is much like SSH'ing into a database. The server trusts you have received and understood the lecture from the admins and you are sure of what code you run.

---

### Post by forrestcupp on 2011-03-15
> **shawnhcorey said:**
> That's not the point; the point is if it had a proper API, code injection would be impossible.

I don't like languages that make more work for me.

Every language makes more work for you if you do it right. Any program that requires any input from a user can be screwed up. Having to take the time to put catches and exceptions in another language is no different than taking the time to protect yourself in SQL.

In my wife's work's system, they automatically fetch the user name from the computer accessing the database, so they are protected by the system wide security, which is not weak. It doesn't have to be hard.

---

### Post by Dragonbite on 2011-03-15
> **pbpersson said:**
> In theory if you write applications in C#.NET (which looks very much like Java) you can run them on Windows and also (maybe) get them to compile in Mono so you can run them in Linux.

Plus Mono will run on iOS, Android, Linux, Solaris, OS X, Windows and I think Windows 7 Phone so it is a handy (almost) "run anywhere" language.

Good languages for me are the ones I know, or have the opportunity to learn as a process for a project.

Oh, and the one that makes me money is always a plus! :D

---

### Post by shawnhcorey on 2011-03-15
> **forrestcupp said:**
> Every language makes more work for you if you do it right. Any program that requires any input from a user can be screwed up. Having to take the time to put catches and exceptions in another language is no different than taking the time to protect yourself in SQL.

Yes, there is a difference; if SQL had a proper API, you would have to guard against code injection.  That doesn't mean you don't have to validate the data.  What it means is that you have to do extra work because of a design flaw that could have been easily avoided.

---

### Post by forrestcupp on 2011-03-15
> **Dragonbite said:**
> Plus Mono will run on iOS, Android, Linux, Solaris, OS X, Windows and I think Windows 7 Phone so it is a handy (almost) "run anywhere" language.How good of an option is Mono for Android? I'm not arguing, I really want to know. I doubt if you could put Mono based apps on the Android market, could you?

> **shawnhcorey said:**
> Yes, there is a difference; if SQL had a proper API, you would have to guard against code injection.  That doesn't mean you don't have to validate the data.  What it means is that you have to do extra work because of a design flaw that could have been easily avoided.
I agree that it shouldn't be possible to inject code into SQL. It's kind of crazy. But a lot of people use it, and I doubt if that's going to change.

---

### Post by Some Penguin on 2011-03-16
> **forrestcupp said:**
> 
I agree that it shouldn't be possible to inject code into SQL. It's kind of crazy. But a lot of people use it, and I doubt if that's going to change.

I disagree.  Runtime generation of schemas and functions can be quite useful for facilitating parallelism without using the combination of very long transactions and temporary tables, and you don't have to be remotely clued to use such things as prepared statements and placeholders in order to be quite safe.  One can readily write safe wrappers for the various clauses and string 'em together if there's a need to fully support generic queries.

Safe-escape methods are there in practically every implementation.  The clueless and careless will still shoot themselves in the foot, but they'll do that in any language that's capable of doing anything interesting at all.

On the other hand, safety is incredibly hard with any language that gives direct write access to memory, like C and close derivatives (since anybody who wrote any function you call, directly or indirectly, could write to any unprotected page mapped to your process's address space) meaning that you're at the mercy of the *most badly or maliciously written* code you're using.  If your system ends up involving a few million lines of code from you and others, the odds that it's all amazingly good are *not* amazingly good.

Interpreted languages are both generally safer in this respect and also much easier to debug, since VMs and interpreters often have very good facilities for introspection and tend to be resistant to corruption from bad or malicious code so things like stack traces are more likely to be usable.   The more forced abstraction and isolation (such as forcing people to use specific methods to alter data instead of providing ubiquitous direct access; and limiting the use of techniques which break the usual barriers, such as binding to native code), the easier it is to isolate, diagnose and fix or work around problems.

This is especially true for functional programming, since lack of side effects makes it much harder to be unpleasantly surprised.  This should not be underestimated, considering that it may well make sense to optimize for overall engineering man-hours (i.e. not just design and development, but maintenance -- the probability of code 'just working' the first time /and/ for easy implementation of the next round of enhancements is not terribly high if it's a complex project).  Good engineers can be expensive, and they're much more temperamental regarding wasting their time than machines are.

---

### Post by Pithikos on 2011-03-16
A language that is easy to read(or gives you the ability to make it readable), simple, fast enough and OPEN.

---

### Post by Dragonbite on 2011-03-16
> **forrestcupp said:**
> How good of an option is Mono for Android? I'm not arguing, I really want to know. I doubt if you could put Mono based apps on the Android market, could you?

I really don't know much about the Mobile versions of Mono because they are pay-for plugins to Monodevelop.

I think the thinking behind it is you write, at least the back-end portion, once and only need to maybe modify the front-end for the device cutting your work in half.

I don't see why you can't put them in the marketplace, though I have no idea what the regulations are for any of them.  I believe there are Mono apps in the iOS App Stores.

---

### Post by might and power on 2011-03-17
1) the quality of the API's that come with it.

2) good support for object orientation is pretty important in this day and age too. and by "good" I mean ruby, c#, java, eifel. *not* c++. 

3) documentation.

naturally it depends on the problem domain though. c++ can be the perfect choice for some problems.

---

### Post by cgroza on 2011-03-17
> **might and power said:**
> 1) the quality of the API's that come with it.

2) good support for object orientation is pretty important in this day and age too. and by "good" I mean ruby, c#, java, eifel. *not* c++. 

3) documentation.

naturally it depends on the problem domain though. c++ can be the perfect choice for some problems.

By good I mean C++, I am simply in love of that language!

---

### Post by might and power on 2011-03-18
> **cgroza said:**
> By good I mean C++, I am simply in love of that language!


haha. congratulations my friend. another good point also: a programmers preferences are subjective. what programmer x enjoys programmer y will not :D

---

### Post by nvteighen on 2011-03-18
> **cgroza said:**
> By good I mean C++, I am simply in love of that language!

Being in love is synonymous to irrationality, which is kinda a good thing for romantic relationships, but really bad in a technical matter like programming...

---

### Post by Simian Man on 2011-03-18
> **shawnhcorey said:**
> Yup.  SQL is about the ugliest excuse for a language that I have ever seen.  Rather than having an API, every database must have a parser and every application that uses it, a code generator.  Not only does this slows things down, it leaves you open to code injection.  SQL as an API is just a bad idea.

OK, you have a good point, but that was missing the point which is that a language doesn't have to be a good general purpose language - or even Turing complete - to be useful for some tasks.  Undoubtedly SQL is useful, though it is, as you say, abused.  There are other examples I could have used such as some shader languages or yacc.

Overall I think CptPicard hit the nail on the head in terms of what a language should be theoretically.

The rest of what you guys are discussing: references, APIs, implementations and other practical concerns are not nearly so interesting.

Unfortunately these two considerations are often at odds.  For example, C++ does very well in the second category, but fails utterly when considering the language on its intrinsic merits.

---

### Post by shawnhcorey on 2011-03-18
> **Simian Man said:**
> Overall I think CptPicard hit the nail on the head in terms of what a language should be theoretically.

The rest of what you guys are discussing: references, APIs, implementations and other practical concerns are not nearly so interesting.

Unfortunately these two considerations are often at odds.  For example, C++ does very well in the second category, but fails utterly when considering the language on its intrinsic merits.

Computer languages are tools.  They have no intrinsic value.  I've seen too many languages that are "the right way to do it" but any practical program is full of kludges and go-arounds simply because the designer thought actually using the language was, at best, a second place feature.  I will take practicality over aesthetics any day.

---

### Post by might and power on 2011-03-18
> **Simian Man said:**
> OK, you have a good point, but that was missing the point which is that a language doesn't have to be a good general purpose language - or even Turing complete - to be useful for some tasks.  Undoubtedly SQL is useful, though it is, as you say, abused.  There are other examples I could have used such as some shader languages or yacc.

Overall I think CptPicard hit the nail on the head in terms of what a language should be theoretically.

The rest of what you guys are discussing: references, APIs, implementations and other practical concerns are not nearly so interesting.

Unfortunately these two considerations are often at odds.  For example, C++ does very well in the second category, but fails utterly when considering the language on its intrinsic merits.

For me (unfortunately) the actual syntax of a language makes up about 30% of its "worth". Maybe even less. All the boring stuff weighs most on choice. A good example of this is php vs ruby: compared to ruby php is a disgusting horror show. But at this point i still chose it because of better support, better libraries, waaaayyyy better documentation, more free source code etc etc (this might have changed though in the year or so since I used ruby for web development).

---

### Post by CptPicard on 2011-03-18
> **might and power said:**
> For me (unfortunately) the actual syntax of a language makes up about 30% of its "worth". Maybe even less. All the boring stuff weighs most on choice.

Unfortunately, "syntax" is just a fairly superficial part of what we're talking about here. It's of course the form of the actual literal symbolic representation, but there's so much more to it... syntax serves a purpose of illustration, but the meaning is much deeper. I get these kinds of comments usually from people who just see the syntactic differences, not the semantic ones -- that is, how does the language actually *behave*, and what do its components mean?

What do you mean by "boring stuff" here, by the way, and what is the choice you have if there is less of this boring stuff?

> **shawnhcorey said:**
> Computer languages are tools.  They have no intrinsic value.

Oh, do try Lisp... ;) There is lots of intrinsic value in being perhaps the plainest, yet most expressive formalism of computable functions. Programming languages are tools of thought; you practically shape an idea through saying things in them.

> 
  I've seen too many languages that are "the right way to do it" but any practical program is full of kludges and go-arounds simply because the designer thought actually using the language was, at best, a second place feature.

Yes, for example Haskell does seem to force monads on you way too much in practical programs and so on. But, that is again a failure of the language's general-purposiveness.

> 
  I will take practicality over aesthetics any day.

I'd have to take the completely opposite point of view then. If something is not aesthetically pleasant in code, it's probably wrong or ill-thought.

---

### Post by shawnhcorey on 2011-03-18
> **CptPicard said:**
> Oh, do try Lisp... ;) There is lots of intrinsic value in being perhaps the plainest, yet most expressive formalism of computable functions. Programming languages are tools of thought; you practically shape an idea through saying things in them.

No, thanks.  Lisp is a language where you write functions to write another function that does the work.  Who was that said:

> "Show me your code and conceal your data structures, and I shall continue to be mystified. Show me your data structures, and I won't usually need your code; it'll be obvious."

The farther you get from your data, the more mistakes you'll make.

> **CptPicard said:**
> I'd have to take the completely opposite point of view then. If something is not aesthetically pleasant in code, it's probably wrong or ill-thought.

Hardly.  Things are only ill-thought when the programmer does not have a good understanding of the data.  What the code looks like is irrelevant.

PS: It was Fred Brooks, author of *The Mythical Man-Month*.

---

### Post by CptPicard on 2011-03-18
Interesting challenge.

> **shawnhcorey said:**
> No, thanks.  Lisp is a language where you write functions to write another function that does the work.

And what is the problem with that? I hope you do understand the background behind functional programming?

Programming is the act of expressing a certain subset of mathematical functions. These functions transform values to other values. This is remarkably powerful conceptually once understood.

> 
The farther you get from your data, the more mistakes you'll make.

You are not far from your data when you put data into a function and get data back. And that can be immutable data, as well, as in pure-functional programming. What is, is. It does not change over time.

In Lisp we can also take the approach of considering the code-data duality of that particular language. There, you really are close to both your code and data; they are interchangeable. Lisp lists express data that can be evaluated as functions. It is a much more high-level representation of the idea that there are bits in a computer and those can be interpreted as a program.

Also, sort-of understanding the basic gist of your argument, the converse is true. The more low-level you are in the bits sense, the more likely you are to make mistakes -- and those are stupid, pointless mistakes. They are totally meaningless with regards to anything you're actually trying to solve.


> Hardly.  Things are only ill-thought when the programmer does not have a good understanding of the data.

Please explain. What data?

It is understanding of what it actually is that the program is solving that produces good code. Having a good language helps in expressing that.

> What the code looks like is irrelevant.

I can produce you a binary dump of an executable. Is this irrelevant if you need to find a bug?

Funny that you'd have this in your signature:

> Programming is as much about organization and communication as it is about coding.

Good code communicates... if what it looks like is irrelevant, it does not communicate.

---

### Post by shawnhcorey on 2011-03-18
> **CptPicard said:**
> Please explain. What data?

All of it.  All programming is converting data in one format into another.

And where did this bit thing come from; I never mentioned it.  And besides, a bit is the same thing as a symbol; both can be as abstract or as real as you want them to be.

When I program a computer, I don't use symbols.  I construct a 2+D graph for all the input formats and all the output ones.  Then I go through it, creating the steps that will convert one to the other.  No symbols, just a bunch of lines and boxes.

If I talk about the data being code, people just get confused.  The only practical application it has is when you're writing a compiler or interrupter.  Otherwise, don't mention it.

---

### Post by CptPicard on 2011-03-18
> **shawnhcorey said:**
> All of it.  All programming is converting data in one format into another.

Agreed in the sense that it's about functional transformations.

> 
And where did this bit thing come from; I never mentioned it.  And besides, a bit is the same thing as a symbol; both can be as abstract or as real as you want them to be.

It's remarkable that I actually agree with you here. Of course in the information-theoretical sense the representations are equivalent. But for the human being the symbol is more informative than the bit. Nvteighen may be able to enlighten us more regarding the informative context of the symbol.

> 
When I program a computer, I don't use symbols.

I certainly do. I always do. Symbols with semantics are crucial.

> 
  I construct a 2+D graph for all the input formats and all the output ones.  Then I go through it, creating the steps that will convert one to the other.  No symbols, just a bunch of lines and boxes.

Intriguing. I'd be interested in hearing more about this 2+D graph of the input formats. There is a vaguely compiler-ish feel to it. Please enlighten.

> 
If I talk about the data being code, people just get confused.  The only practical application it has is when you're writing a compiler or interrupter.  Otherwise, don't mention it.

But writing a compiler/interpreter is *the* application that actually means anything, ever! It really is the part where you fully understand what is going on...

---

### Post by shawnhcorey on 2011-03-18
The 2+D means two and a little bit more dimensions.  The nodes of the graph are in two dimensions but the lines connecting them can cross each other, so they needed an infinitely small bit of another dimension.  Hence 2+D.  Or if you prefer:  (2+)D

Languages are 1+D.  Their symbols occupy the nodes but their lines need a little bit of another dimension to cross each other.

---

### Post by CptPicard on 2011-03-18
Sounds like ********, to be honest.

---

### Post by might and power on 2011-03-18
> **CptPicard said:**
> Unfortunately, "syntax" is just a fairly superficial part of what we're talking about here. It's of course the form of the actual literal symbolic representation, but there's so much more to it... syntax serves a purpose of illustration, but the meaning is much deeper. I get these kinds of comments usually from people who just see the syntactic differences, not the semantic ones -- that is, how does the language actually *behave*, and what do its components mean?

What do you mean by "boring stuff" here, by the way, and what is the choice you have if there is less of this boring stuff?



Oh, do try Lisp... ;) There is lots of intrinsic value in being perhaps the plainest, yet most expressive formalism of computable functions. Programming languages are tools of thought; you practically shape an idea through saying things in them.



Yes, for example Haskell does seem to force monads on you way too much in practical programs and so on. But, that is again a failure of the language's general-purposiveness.



I'd have to take the completely opposite point of view then. If something is not aesthetically pleasant in code, it's probably wrong or ill-thought.

Programming languages are all Turing-complete, aren't they? So the languages all "behave" the same way. For me at least, programming is the same solutions over and over - variables, methods, loops, iterators, containers yata yata. It's trivial what language you implement in. You can "program" in pseudo code and implement in the language of your choice.

---

### Post by shawnhcorey on 2011-03-18
> **might and power said:**
> Programming languages are all Turing-complete, aren't they? So the languages all "behave" the same way. For me at least, programming is the same solutions over and over - variables, methods, loops, iterators, containers yata yata. It's trivial what language you implement in. You can "program" in pseudo code and implement in the language of your choice.

True.  The difference in languages make different types of programs easier to write.  If you want a language that is hard to write and hard to understand, try [Ook!]("http://www.esolangs.org/wiki/Ook")

---

### Post by CptPicard on 2011-03-18
> **might and power said:**
> Programming languages are all Turing-complete, aren't they?

Yes, they all solve the same set of problems, theoretically speaking, as long as they are Turing-complete.

> 
 So the languages all "behave" the same way.

No, they do not. The very reason why we have different kinds of programming languges is that as human beings, our minds fit certain kinds of formalisms better.

> 
 For me at least, programming is the same solutions over and over - variables, methods, loops, iterators, containers yata yata. It's trivial what language you implement in. You can "program" in pseudo code and implement in the language of your choice.

Which just for me means that you lack the insight. You have not yet reached the point where you can make the distinction :)

---

### Post by nvteighen on 2011-03-19
> **shawnhcorey said:**
> 
When I program a computer, I don't use symbols.  I construct a 2+D graph for all the input formats and all the output ones.  Then I go through it, creating the steps that will convert one to the other.  No symbols, just a bunch of lines and boxes.


You use symbols. A graph is also a symbolic representation of what you want to do.

Let's say you want to program a search engine. Ok, what's the search engine but just an abstract behaivor? If someone tells me that he wrote a search engine, I'd expect that thing to give me some filter data in a database according to some keywords and, sometimes, search criteria.

Now, you go and write a search engine. Did you write the search engine? Yes. But is the code the search engine itself? No, it isn't. It's a text that describes and specifies the search engine. That text has to be interpreted: either by a human that reads the code and understands what you wrote or by a computer that reads the code and reflects in some way the behaivor you've described. 

But then, there's a gap between the code you wrote and the actual behaivor that code describes; that gap is filled by interpretation. And interpretation means there are symbols: you have some object A that is given some interpretation B, which is another object... but A isn't B, it refers to B.

Programming is done using artificial formal written languages because languages are symbolic devices. It's a practical matter: in order to refer to some reality that you can't refer to by physical means (pointing, holding, etc.), you have to end up designing some sort of symbolic system to do it. Formal languages are there for abstract realities and for good. How would you describe a search engine just using physical means??

> **shawnhcorey said:**
> 
Languages are 1+D.  Their symbols occupy the nodes but their lines need a little bit of another dimension to cross each other.

What?

---

### Post by shawnhcorey on 2011-03-19
Languages have 1 dimension since all the statements are in a line.  The statements are the nodes to the graph.  But just having straight sequences will not do much that is useful.  The jumps are represented by the lines and need a little more dimensionality to go around the nodes rather than through them.  Hence 1+D.

---

### Post by forrestcupp on 2011-03-19
> **CptPicard said:**
> 
Which just for me means that you lack the insight. You have not yet reached the point where you can make the distinction :)
What?? Is it lack of insight or is it versatility? A good programmer *should* be able to write pseudocode then implement it in several languages.

---

### Post by schauerlich on 2011-03-19
> **forrestcupp said:**
> What?? Is it lack of insight or is it versatility? A good programmer *should* be able to write pseudocode then implement it in several languages.

Right; but you'll notice that writing the same algorithm in C, Python and PHP is much different from writing the same algorithm in assembly, Haskell and J. The language you use DOES matter, because every language has a different set of core abstractions available to the programmer in order to assemble the same "thought," i.e. the algorithm. It's just that most of the popular languages use a pretty similar set of abstractions, and you can't appreciate the diversity of computer languages until you've had a chance to use them. It's not a statement of "you're too stupid to get it," just "you haven't gotten a good look at the problem space yet."

---

### Post by schauerlich on 2011-03-19
> **shawnhcorey said:**
> Languages have 1 dimension since all the statements are in a line.  The statements are the nodes to the graph.  But just having straight sequences will not do much that is useful.  The jumps are represented by the lines and need a little more dimensionality to go around the nodes rather than through them.  Hence 1+D.

Sounds like you don't have much experience with non-procedural languages. Not everything is sequentially executed, with the occasional jump. Just look at any non-strict language, or any concurrent language.

---

### Post by slavik on 2011-03-19
if there was a programming language that was best for everything and was best at everything, we'd have only 1 programming language. programming languages is not a solved problem.

programming languages allow us to represent "what we want done", some languages represent those wants better for some people (depending on their previous training/knowledge or what we use it for) than others.

there are also languages that are used more to represent knowledge which are very maluable in that respect (LISP, prolog).

if you're throwing around a phrase/thought similar to 'languages are turing complete, so who cares?' then you miss the whole point what what turing complete is. turing complete talks about computability, not complexity. you could write a rule/logic engine in assembly, but why bother when prolog is around and learning how to do it in prolog is quicker than doing it in assembly?

with that said, this thread is more useless than a dirty sock. if you want a real conversation, consider dropping all your language bias whatsoever, then decide what a good language should be, then see what fits best. i doubt you will be able to come up with features that do not clash.

---

### Post by shawnhcorey on 2011-03-19
> **schauerlich said:**
> Sounds like you don't have much experience with non-procedural languages. Not everything is sequentially executed, with the occasional jump. Just look at any non-strict language, or any concurrent language.

I have looked at them.  They all have short segments that are procedural and a mechanism to synchronize them.  You're just black-boxing them and claiming there is no procedural element.

---

### Post by nvteighen on 2011-03-19
> **shawnhcorey said:**
> Languages have 1 dimension since all the statements are in a line.  The statements are the nodes to the graph.  But just having straight sequences will not do much that is useful.  The jumps are represented by the lines and need a little more dimensionality to go around the nodes rather than through them.  Hence 1+D.

Ok, I get it. In Linguistics we have a technical term for that: linearity.

Some people love to talk about linearity, but IMO, it's a waste of time: it's just a descriptive concept, which is true, but irrelevant for explaining phenomena.

So yes, I can't but agree with you, but I don't get how stating that languages are one dimensional has anything to do with interpretation and representation in programming languages.

---

### Post by shawnhcorey on 2011-03-19
But I didn't say they had one dimension, I said they have 1+ dimensions.

Here's and example from Python:
[IMG]http://media.texample.net/tikz/examples/PNG/python-if-then-else-syntax-diagram.png[/IMG]
*Courtesy of [TeXample.net]("http://www.texample.net/tikz/examples/python-if-then-else-syntax-diagram/").*

The nodes are in a line but there are lines that bypass them.  To do so requires more than one dimension but can be done is less than 2.  They require 1+D.

And if the lines should ever cross, you have a goto.  :)

---

### Post by lisati on 2011-03-19
> **shawnhcorey said:**
> But I didn't say they had one dimension, I said they have 1+ dimensions.

Here's and example from Python:
<snip>
To me that looks like a form of flowchart, sitting somewhere in between the flowcharts I was taught 30+ years ago, and a formal description of an element of a language. And the use/abuse of "goto" is another potential can of worms...... :D

---

### Post by shawnhcorey on 2011-03-19
> **lisati said:**
> To me that looks like a form of flowchart, sitting somewhere in between the flowcharts I was taught 30+ years ago, and a formal description of an element of a language. And the use/abuse of "goto" is another potential can of worms...... :D

It's formal name is a syntax diagram.  [Here are a bunch more]("https://secure.wikimedia.org/wikipedia/en/wiki/Syntax_diagram").  Notice how the author carefully avoided crossing the lines?

---

### Post by lisati on 2011-03-19
> **shawnhcorey said:**
> It's formal name is a syntax diagram.
I should have known that! D'oh! It must be time for a fix of caffeine and/or nicotine...... :D

---

### Post by might and power on 2011-03-19
Really, I think the difference between imperative languages and functional languages is profound and I think probably too profound for this topic. It seems like some of you wanting to answer the question "what makes a language good" with "a language that is functional". :lolflag:

---

### Post by slavik on 2011-03-19
you mean this: [http://en.wikipedia.org/wiki/Flowchart](http://en.wikipedia.org/wiki/Flowchart)

---

### Post by Dragonbite on 2011-03-19
I'm starting to feel good not having to know all of this stuff to just code what I have to code in whatever language they throw at me.

If I had to know all of this stuff, I'd have to find another career!

---

### Post by shawnhcorey on 2011-03-19
> **Dragonbite said:**
> I'm starting to feel good not having to know all of this stuff to just code what I have to code in whatever language they throw at me.

If I had to know all of this stuff, I'd have to find another career!

If you know how to code, you probably already know this stuff; most of it is just common sense.  You just don't know the formal theory.  You don't know what you don't know you know.  :)

---

### Post by might and power on 2011-03-19
90 % of what you need to know about programming is in this book:
[http://en.wikipedia.org/wiki/Algorithms_%2B_Data_Structures_%3D_Programs](http://en.wikipedia.org/wiki/Algorithms_%2B_Data_Structures_%3D_Programs)

---

### Post by kurum! on 2011-03-19
you guys can talk, discuss and argue till the cows come home, in the end, its all about what problem needs to be solved and what tools are most appropriate for the situation and how one "feels". Ever wondered why each of us are born different?  Some may say Lisp is simple, some may find it ugly. Some may find Python's syntax simple and easy to read, some may find its whitespace feature a nuisance....enough said.

---

### Post by nvteighen on 2011-03-20
> **shawnhcorey said:**
> But I didn't say they had one dimension, I said they have 1+ dimensions.

Here's and example from Python:
[IMG]http://media.texample.net/tikz/examples/PNG/python-if-then-else-syntax-diagram.png[/IMG]
*Courtesy of [TeXample.net]("http://www.texample.net/tikz/examples/python-if-then-else-syntax-diagram/").*

The nodes are in a line but there are lines that bypass them.  To do so requires more than one dimension but can be done is less than 2.  They require 1+D.

And if the lines should ever cross, you have a goto.  :)

Do you realize that those are properties of your representation but not of the language? If I chose a 2D graph (the usual flowcharts in UML...), it'd be illegitimate to say that languages are 2D.

---

### Post by shawnhcorey on 2011-03-20
> **nvteighen said:**
> Do you realize that those are properties of your representation but not of the language? If I chose a 2D graph (the usual flowcharts in UML...), it'd be illegitimate to say that languages are 2D.

No, languages are linear.  They are time based, one symbol after another.  When you speak, you don't say all the words at once; you say them one after another.

The image is a syntax diagram, a special case of a [directed graph]("https://secure.wikimedia.org/wikipedia/en/wiki/Directed_graph").  Directed graph are often used in computer science since it has been shown that a directed graph can represent a [finite-state machine]("https://secure.wikimedia.org/wikipedia/en/wiki/Finite-state_machine") and since a [Turing machine]("https://secure.wikimedia.org/wikipedia/en/wiki/Turing_machine") is a finite-state machine, it can represent everything that's computable.

---

### Post by slavik on 2011-03-21
so far, there is no discussion on what makes a language "good," I offer the following points:

1. duck typing (convert numeric types to strings based on context among other things)
2. make assumptions, but allow explicit declaration (for when an assumption doesn't fit)
3. ability to write code in multiple paradigms (functional, OO, etc.)

knowing how to write code in any language without any theretical knowledge is a union job. many people who read/post on this forum would fit that category.

shawnhcorey: not all languages are 'linear' (serial is the term used in physics). when you have 1 unit that is interpreting instructions, the execution appears to be serial. once you have a second unit, then you can start doing some items in parallel. one theory AMD had (AI oriented) is, when you have an if statement with two possible outcomes, start calculating both of them and when you get to the actual if() statement, evaluate it and throw out the branch that is false. this was an idea they had to present a dual core cpu as a single core cpu, which is an interesting concept, but we do not usually need this in a home/server type environment. this would be more useful in some kind of an AI decision tree though that is very broad and if your system has lots of cpus (so that you precalculate the lower trees before knowing which you need to follow).

one of the arguments that are made is that Alan Turing could've done much more if he had not been exposed to John von Neuman's idea of programs being 'one isntruction after the other' which I see you (shawnhcorey) following. if this was the case, then why do we have systems with multiple processors? one of the things that are being worked on for languages like Haskel is taking statements, decomposing them and using different processors at the same time to calculate them (f(a) + f(b), where f(a) is calculated on processor1 and f(b) is calculated on processor2 and then the result is calculated on processor3 which is simply waiting for the two values).

---

### Post by shawnhcorey on 2011-03-21
All languages are linear.  When you write parallel algorithms, do you write them all at once?  No, you write them one after another in a linear fashion.

You think that because a language can represent parallel processes, it must not be linear.  Do not confuse the representation of the algorithms with their execution.

---

### Post by nvteighen on 2011-03-21
> **shawnhcorey said:**
> All languages are linear.  When you write parallel algorithms, do you write them all at once?  No, you write them one after another in a linear fashion.

You think that because a language can represent parallel processes, it must not be linear.  Do not confuse the representation of the algorithms with their execution.

You're confusing me.

First, you state that languages are 1+D (which I assume it can't be "linear", because it isn't 1D) and you show us a diagram that in your opinion reflects that. Then, you say languages are linear because one says one word after the other.

But again, it's a matter of representation: the classic example against linearity being a fundamental language property is phonetics. Phonemes are sets of features, such that you have /d/, which is [[+stop] [+voiced] [+dental] [+alveolar]], all at the same time; change [+voiced] by [-voiced] and you get /t/. The perceived linearity derives from your own decision of using words as the level from where you build up your observations.

And the same goes for syntax, although in a more abstract way. Chomskyan linguistics are very well-known by using tree-representations of syntactic structures: those are 2D. Take this example:

```

# Using a Pre-Minimalist approach

                   DP
                  /  \
                 /    \
               his     D'
                      / \
                     D  NP
                         |                    
                        cat

[*DP* his [*D'* D [*NP* cat]]] = "his cat"

```

So, ok, we could say "his cat" is 1D if you look at it as a succession of two words (his + cat). But take the bracketed version: is it linear or is it a flattened version of a 2D tree? IMO, you could both say that the Spec-DP (his) is higher than the NP completement of the functional D head (cat), but also that it's before it... higher and before? higher or before? Which is it?

But the tree is unambiguously 2D. There, the possessive is clearly higher and before the rest of the syntactic structure (in other words, it "c-commands" D' and everything D' dominates).

Be aware that Lisp works exactly this way: it's an explicit linear representation of a syntax tree (like the bracketed Chomskyan notation).

So, it's about representations. Not that a 1+D representation wouldn't be useful, but don't confuse the representation's properties with the your object's.

---

### Post by CptPicard on 2011-03-21
> **slavik said:**
> 
1. duck typing (convert numeric types to strings based on context among other things)

Sounds a bit like loose typing to me; as in Javascript. Which is a bad thing :)

Anyway, shawncorey's ideas sound much like those "I think in terms of assembly instructions and it makes me see things" claims one often hears from particularly low-level language proponents... of course, in reality, I suspect they never actually do that.

"Instructions after one another that change state" is, after all, the imperative mindset that you certainly can get from imperative languages, so I'm not surprised. A certain sequential thinking is perhaps *one* of the things that one needs to train when learning to program, but to get past syntactic "linearity" (symbols after another) one has to start understanding the higher-order concepts that are in play and being expressed. Those concepts on the other hand IMO would be pretty impossible to deduce from a sequence of instructions.

---

### Post by andrew1992 on 2011-03-21
I think I'd have to agree here.  While execution is 1-D, that's a different ball game.  

I wonder how overwhelmed the OP has become...

---

### Post by llanitedave on 2011-03-22
> **nvteighen said:**
> You're confusing me.

First, you state that languages are 1+D (which I assume it can't be "linear", because it isn't 1D) and you show us a diagram that in your opinion reflects that. Then, you say languages are linear because one says one word after the other.

But again, it's a matter of representation: the classic example against linearity being a fundamental language property is phonetics. Phonemes are sets of features, such that you have /d/, which is [[+stop] [+voiced] [+dental] [+alveolar]], all at the same time; change [+voiced] by [-voiced] and you get /t/. The perceived linearity derives from your own decision of using words as the level from where you build up your observations.

And the same goes for syntax, although in a more abstract way. Chomskyan linguistics are very well-known by using tree-representations of syntactic structures: those are 2D. Take this example:

```

# Using a Pre-Minimalist approach

                   DP
                  /  \
                 /    \
               his     D'
                      / \
                     D  NP
                         |                    
                        cat

[*DP* his [*D'* D [*NP* cat]]] = "his cat"

```

So, ok, we could say "his cat" is 1D if you look at it as a succession of two words (his + cat). But take the bracketed version: is it linear or is it a flattened version of a 2D tree? IMO, you could both say that the Spec-DP (his) is higher than the NP completement of the functional D head (cat), but also that it's before it... higher and before? higher or before? Which is it?

But the tree is unambiguously 2D. There, the possessive is clearly higher and before the rest of the syntactic structure (in other words, it "c-commands" D' and everything D' dominates).

Be aware that Lisp works exactly this way: it's an explicit linear representation of a syntax tree (like the bracketed Chomskyan notation).

So, it's about representations. Not that a 1+D representation wouldn't be useful, but don't confuse the representation's properties with the your object's.

Heh.  I'm in the middle of reading Steven Pinker's "The Language Instinct", and it's covering that exact same ground.  Our interpretation of language is linear, although our production and pre-conscious analysis of it is massively parallel.

Not sure how this ties into what makes a computer language "good" or not, though.  If it's human readable, it's going to have to be linear in its presentation, no matter how much parallel potential it may have in the hardware.  I don't think we can parse or do logic in more than one dimension -- at least most mere mortals can't.

---

### Post by slavik on 2011-03-22
> **CptPicard said:**
> Sounds a bit like loose typing to me; as in Javascript. Which is a bad thing :)

Anyway, shawncorey's ideas sound much like those "I think in terms of assembly instructions and it makes me see things" claims one often hears from particularly low-level language proponents... of course, in reality, I suspect they never actually do that.

"Instructions after one another that change state" is, after all, the imperative mindset that you certainly can get from imperative languages, so I'm not surprised. A certain sequential thinking is perhaps *one* of the things that one needs to train when learning to program, but to get past syntactic "linearity" (symbols after another) one has to start understanding the higher-order concepts that are in play and being expressed. Those concepts on the other hand IMO would be pretty impossible to deduce from a sequence of instructions.
except I don't have to worry about the type of $a when I do:
```

my int $a = 5;
say $a ~ " apples";

```

---

### Post by slooksterpsv on 2011-03-24
Ahh.. I gotta say my initial reply on this was biased, yeah I used python to show one thing and C++ to show another. Technically I should have done it both in python or both in C++ or shown both for both.

Yeah, C++ is powerful, but I find some program I make I forget what they do cause I don't describe the functions, I do like func_a blah blah blah and forget how I use it in respect to the other functions.

Anyways that's my flaw in the initial reply. Other than that, I still agree with my statements about descriptive and what not.

---

### Post by slavik on 2011-03-24
> **slooksterpsv said:**
> Ahh.. I gotta say my initial reply on this was biased, yeah I used python to show one thing and C++ to show another. Technically I should have done it both in python or both in C++ or shown both for both.

Yeah, C++ is powerful, but I find some program I make I forget what they do cause I don't describe the functions, I do like func_a blah blah blah and forget how I use it in respect to the other functions.

Anyways that's my flaw in the initial reply. Other than that, I still agree with my statements about descriptive and what not.
so your issue with C++ is that you do not use descriptive names for your functions? I do not see how this makes sense ...

---

### Post by might and power on 2011-03-25
> **andrew1992 said:**
> I think I'd have to agree here.  While execution is 1-D, that's a different ball game.  

I wonder how overwhelmed the OP has become...

Often happens ... someone asks an innocent question and the answers end up being more about the intellectual vanity of programmers than the curious persons question ...

---

