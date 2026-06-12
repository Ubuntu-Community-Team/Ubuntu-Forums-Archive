---
title: "advise on web development in c++"
date: 2016-11-06
forum: Programming Talk
---

### Post by chuchi on 2016-11-06
Hi everyone!

I am sorry if this was post before.

I am planning to develop a website in C++ and I would like to know your opinion about that.

In the past I did PHP web development. But, in my opinion, PHP and other interpreted languages are error-prone because of undefined and uninitialized variables and such things, and I feel more comfortable in C++.

Would it be a crazy idea to develop a website using C++?

Thanks a lot!

---

### Post by T.J. on 2016-11-06
> I am planning to develop a website in C++ and I would like to know your opinion about that.

You can use whatever suits you best.  The actual language chosen is *almost *irrelevant.   The real questions are how much work do you want to do (reinvention),  does the compiler produce optimal results, and do you require thread-safety while programming?


> In the past I did PHP web development. But, in my opinion, PHP and other interpreted languages are error-prone because of undefined and uninitialized variables and such things, and I feel more comfortable in C++.

In my opinion, PHP is over-hyped junk.  It is neither thread-safe nor consistent when used with most libraries. It cannot be used with Apache's intended threading model in most cases, and serves primarily as a vehicle for promoting buy-in products offered by Zend.  That said, I do not consider C++ to be a good choice either.  C++ does not initialize by default, so it is not better than PHP in that regard. 

 OOP in general is a bad model for development, IMO. Of its supposed benefits,  inheritance is seldom used, and actively discouraged - especially in C++ and Java. Exceptions are questionable and produce stack calls where you can lose debugging data. Polymorphism can be achieved in better ways with generics if it is really needed.While you can disable exceptions in some cases, the language  violates the principle of "pay for what you use."   The entire OOP model leads to designs that are over-designed and wasteful of resources - again in my opinion. I realize that there are going to be those who will descend on that evaluation shouting heresy, and to them I'd answer that I'd stack C code against their C++ any day; and see who performs better.

Even OOP advocates are dropping or disabling OOP features as programmers evaluate their usefulness.  Google coding guidelines do not permit the use of exceptions, and their language: Go does not have them at all. The Clang project coding guidelines ban exceptions and RTTI.  Game and embedded programmers already prefer not to use OOP in many cases. Naturally, you should defer to your own judgement - but I think most developers do not consider the costs of OOP as opposed to not using it.

> Would it be a crazy idea to develop a website using C++?

No, I don't think so. It's no crazier than anything else that has already been done.  If you want to do it, go for it!  Webpages are nothing more than text output with links to scripts, pictures or other resources, after all.  I'll even offer to look at the code if you want.  Before making a decision though, I'd look to see what libraries you can find to ease development.

---

### Post by chuchi on 2016-11-09
Hi T.J.!
 

 I can't believe this! Because I am also a C fan, and prefer it over C++! But most of my mates argue that C++ and OOP is better, saying things like code reuse is easier. In the end they convinced me to use C++.
 

 But now I realized I disagree with them. You can also achieve code reuse with C and good module development, and avoid complicated OOP overhead.
 

 I like C and will use it, definitely!
 

 The web application I am thinking about is not only to serve web pages, but also as a web services application, because an android application will consume those web services.
 

 Thank you very much for your advice!
 

 All the best

---

### Post by T.J. on 2016-11-09
> I can't believe this! 

Believe it my friend.   We aren't the only ones.  We are in good company, such as Edsger W. Dijkstra, Alan Kay, Paul Graham, and even Linus Torvalds. 

OOP has been tremendously over-sold.  In the 20+ years I have been a programmer, I've never seen OOP save the day in a way that functional programming could not - not once.  It works sure, but it just as easily makes things far more complex than they need to be.  The ultimate example that an OOP language is not necessary?  The Linux kernel.  It is a huge project with millions of lines, and hundreds or thousands of programmers.  It's written in C.  It is well maintained - far better than many C++ projects.  All that it takes is discipline and clear design.



> 
Because I am also a C fan, and prefer it over C++! But most of my mates argue that C++ and OOP is better, saying things like code reuse is easier. In the end they convinced me to use C++.

The greatest arguments for OOP are code reduction and reusability. Well, my response is "Create libraries." You can dismiss close to 80% of the justification for OOP features that way, IMO.
> 

 But now I realized I disagree with them. You can also achieve code reuse with C and good module development, and avoid complicated OOP overhead.

More pity for them. If you would like, we can discuss this at length. Believe it or not, OOP is so entrenched in the industry that very few people are even willing to discuss the facts, so meeting you is a treat.


 > Thank you very much for your advice!
 You're very welcome, but in all it is just advice and you must decide if it is valid.

---

### Post by QIII on 2016-11-09
What I find interesting about topics like this is the idea that it is a choice of one or the other.

Which is better?  The $64,000 question is:  "For what?"

In my line of work (granted, it's pretty specialized) the best approach is a mix of FP and OOP for different aspects of a multitude of processes.

In dogma we sometimes find selective memory that helps us forget the times that strict adherence to our pet has caused a lot of extra effort and complexity.

As with all things: use the best tool for the job at hand.  Better to have a box full of different tools than a box with a single tool which you diligently use for every purpose.

If I want a dovetail joint with variable pins and tails, I'll use a saw and chisels.  If I am interested in a strong joint without design flair, I'll use a jig and a router.  In either case, I want a perfect, tight joint.

But I'm pragmatic, not dogmatic.

---

### Post by T.J. on 2016-11-09
That is not really the discussion, at least as I try to frame it.  For me, it is a cost/benefit with the question on &#8220;Does OOP deliver what it promises over functional programming?&#8221;  

The answer for me at least, is increasingly: &#8220;No.&#8221;

The pillars of OOP are usually stated as:

**1. Polymorphism.**

Well, polymorphism is not exclusive to OOP, and never was.

Common OOP structures such as object variables or vars are really no different than C void.  In fact, in order to use object variables or vars in languages like C#, you have to cast them, just as you would a void.  It strikes me as pointless hyperbole.

C14 has enhanced function generics as well, so much of the function name argument is moot.

**2. Inheritance**

Inheritance is a dead-duck feature IMO.  C++ actively discourages its use for fear of the &#8220;diamond problem&#8221;.    Java cripples it so you can&#8217;t inherit more than once.

Furthermore, what is the actual difference between:  

```
class class1: public class 2 {}


or 


class class1 
{
  public:
    class2 my_instance;
}
```

Not very much...and you are avoiding potential multiple inheritance issues.  It&#8217;s a useless feature, especially when you consider that most RL problems do not break down into objects anyway, but steps.  My question is what good is it, really?


**3.Encapsulation**

Encapsulation is often touted as a benefit,but structs and function parameters perform this very well.  The only justification for C++ style encapsulation is to create spaghetti code, using class defined variables as scoped globals within the class to avoid function parameters.

In my experience, hiding data in classes actually makes writing reusable code harder.  Let me know if you want an example, I&#8217;d think it would be obvious though.  


**4.Abstraction**

Abstraction is basically a way of crafting an API. I&#8217;ve never met a piece of code that once designed clearly,needed a special language feature to keep it that way.



That said, OOP introduces some annoyances with linking and complexity of the compiler as well.  OOP programs tend to result in larger binaries and consume more resources.  They also tend to be slower - both of which waste precious battery life.  OOP has some interesting ideas to be sure, but I believe they are overstated.  All in all, compared to functional programming, the OOP paradigm spends an inordinate amount of time trying to find ways to avoid problems inherent in its use. C++14 has blossomed into a mismatched cesspool of so many ways to compensate for flaws or or shortcut using clean code that few people if any have ever actually mastered the language.  It's a pink camel with 6  different sized humps decided on by committee after a drunken binge, IMO.

---

### Post by chuchi on 2016-11-11
Hi T.J,
 

 I agree with everything you said. I have never seen any advantage of OOP over functional programming.
 

 Hope you do not mind if I ask you a question.
 

 As I would love to improve my C skills, I would like to get involved in any free C project.
 

 Do you have any free project I could help? Or do you know where I could go to find some free projects I could contribute?
 

 Thanks a lot!

---

### Post by spjackson on 2016-11-11
Do any of you have examples of functional programming in C that you can either post or point me at? I imagine it would be quite hard to do for anything beyond the trivial and I'd be interested to see it in action. Thanks.

---

### Post by T.J. on 2016-11-11
> Do any of you have examples of functional programming in C that you can either post or point me at? I imagine it would be quite hard to do for anything beyond the trivial and I'd be interested to see it in action. Thanks.[COLOR=#000000]


[/COLOR]I tend to muddle the terms some days, and for that I apologize.   I spend more time actually writing day-to-day boring code than applying the niceties of CompSCI theory.  Where I said "functional", I should have used "imperative" or "procedural" as in speaking of every-day C.  It has been many years since the classroom.  In the future, I will attempt to be more discriminating when speaking aloud.

That said, you can find some examples of actual functional programming in C: [https://lucabolognese.wordpress.com/2013/01/04/functional-programming-in-c/#discriminated-unions-in-c](https://lucabolognese.wordpress.com/2013/01/04/functional-programming-in-c/#discriminated-unions-in-c) 

C and C++ are extremely general purpose languages, so when it boils down to it, you can use virtually any paradigm in either language.  My dislike of C++ revolves around that fact that an OOP designed language forces you into a particular mindset when accepted programming model is not always the best way, e.g. the inheritance problem.  Even when you resort to using C++ in a procedural manner, you still have to pay for unused overhead in the compiler.

---

### Post by T.J. on 2016-11-11
> **chuchi said:**
> Hi T.J,
 

 I agree with everything you said. I have never seen any advantage of OOP over functional programming.
 

 Hope you do not mind if I ask you a question.
 

 As I would love to improve my C skills, I would like to get involved in any free C project.
 

 Do you have any free project I could help? Or do you know where I could go to find some free projects I could contribute?
 

 Thanks a lot!

I don't have any presently to offer you, Chuchi.  All of my current work is in the private sector and under a non-disclosure, i.e. Microsoft based crapware.  If you find one that you like, I will comment, and perhaps occasionally assist with the code.  You can contact me via personal message for that, as it is not a forum help request.

---

### Post by spjackson on 2016-11-11
> **T.J. said:**
> 
That said, you can find some examples of actual functional programming in C: [https://lucabolognese.wordpress.com/2013/01/04/functional-programming-in-c/#discriminated-unions-in-c](https://lucabolognese.wordpress.com/2013/01/04/functional-programming-in-c/#discriminated-unions-in-c) 

Thanks for trying, although I don't find that very persuasive. Sure, you can write functional programs in C with a little help from [Greenspun's tenth rule]("https://en.wikipedia.org/wiki/Greenspun's_tenth_rule"). Anyway, thanks for clarifying what you meant.

---

### Post by T.J. on 2016-11-11
OT:

> **spjackson said:**
> Thanks for trying, although I don't find that very persuasive. Sure, you can write functional programs in C with a little help from [Greenspun's tenth rule]("https://en.wikipedia.org/wiki/Greenspun's_tenth_rule"). Anyway, thanks for clarifying what you meant.

You're welcome.  I'm sorry the sample falls short for you.  

I consider Greenspun&#8217;s rule to be satirical, and never to be taken as completely serious.

All programs are ultimately using assembly code, because that is all your processor is capable of executing.  Given the fact that C is as close to assembly as you can get without actually using assembly, every argument against the use of the language is actually just good argument for a better library. Until processor design fundamentally changes. most language features beyond the minimum are often just syntactic candy.   It is also true that most of those language's compilers -  are written in part or entirely in C.  Even Greenspun's LISP usually  have their first implementations or bootstrappers built in C, and then built using LISP later.

The whole argument for different languages for different tasks revolves around writing robust software in the shortest span, but that can be accomplished with libraries as much as built in language features, IMO.  Ultimately, there is almost nothing that C can't do that the processor can; and where it falls short - most allow for embedded assembly.

Naturally, that could be said for a number of mid-to low level languages. C just holds the distinction of being the most historically efficient.

---

### Post by dwhitney67 on 2016-11-13
> **T.J. said:**
> 
...

**2. Inheritance**

Inheritance is a dead-duck feature IMO.  C++ actively discourages its use for fear of the &#8220;diamond problem&#8221;.    Java cripples it so you can&#8217;t inherit more than once.

Furthermore, what is the actual difference between:  

```
class class1: public class 2 {}


or 


class class1 
{
  public:
    class2 my_instance;
}
```

Not very much...and you are avoiding potential multiple inheritance issues.  It&#8217;s a useless feature, especially when you consider that most RL problems do not break down into objects anyway, but steps.  My question is what good is it, really?

...



You lost me on your argument above.  How can you say that both examples shown above are "equivalent"?  Either you erred in your statement, or you haven't a clue what you are arguing about.

What relevant experience do you have with C++?  What relevant experience do you have with C?

---

### Post by T.J. on 2016-11-13
> **dwhitney67 said:**
> You lost me on your argument above.  How can you say that both examples shown above are "equivalent"?  Either you erred in your statement, or you haven't a clue what you are arguing about.  

The examples are functionally equivalent in that whether you inherit the second class or create an instance as a variable, you have access to both the data and functions that it provides. The inheritance mechanism is a two-edged sword; and in many newer languages such as Java (only single inheritance is allowed) or C# (single inheritance and classes can be sealed), it has been deliberately limited in order to avoid issues such as multiple inheritance of the same class. By instancing a class as a variable in C++ rather than inheriting it, you lower the risks significantly - IMO. Writing code is as much an art as science, and everyone has an opinion as to the quality of code.

The fact remains that inheritance is - generally speaking - entirely unnecessary and laced with problems. You are welcome to disagree as you see fit. With respect, I believe OOP is fundamentally flawed, especially with the inheritance mechanism. I say so now in the hopes that if we discuss in the future - and I hope we do - that you understand where I am on the issue.

You are certainly welcome to your opinion of whatever I say, and will form your own judgments in any case.  That's fine. I have little time for hyperbole, and arguments of code correctness when a language provides more than one method of the same thing, unless you can demonstrate why. I thought I had. As to that success, you can only decide for yourself.


> 
What relevant experience do you have with C++?  What relevant experience do you have with C?

I've written in-house software that you have never heard of for ISPs and businesses over the last 20+ years in both languages, although certainly not full-time.  Whether you consider that suitable experience, I leave to your judgment. You would not be able to verify it in any case. If you believe the example was insufficient, please be clear and I will attempt to do better next time.

---

### Post by wildmanne39 on 2016-11-13
Please stay on topic and keep your replies polite.

---

### Post by T.J. on 2016-11-13
> **Wild Man said:**
> Please stay on topic and keep your replies polite.

I accept that as a deserved warning. I shall withdraw at once, and be more mindful in the future. I bid you "Good day." If interested parties wish to speak further on this - please message me instead - as it is a contentious issue.

---

### Post by chuchi on 2016-11-15
Hi!
 

 Definitely I will use C.  
 

 I have been looking for C libraries/frameworks for web developments and only found KORE.io.
 

 It seems OK for me, but do you know/recommend other C frameworks for web development?  
 

 Thanks a lot!

---

