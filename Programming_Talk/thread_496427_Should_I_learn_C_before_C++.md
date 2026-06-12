---
title: "Should I learn C before C++?"
date: 2007-07-09
forum: Programming Talk
---

### Post by krugman on 2007-07-09
Hello:)

So, I have just started learning C, but I was wondering whether I should/could directly start learning C++.

Basically, I want to learn C++  because I am going to work in some finance departments (asset management and the likes...), and some notions of programming in C++ might be an asset, so to speak.
 For instance, here is the very beginning of a program that I would lke to understand (and hopefully, one day, be able to create my own!):

```

typedef double Time;
typedef double Rate;
/**********************************************************************************
General diffusion process classes
This class describes a stochastic process governed by dx(t) = mu(t, x(t))dt +
sigma(t, x(t))dz(t).
**********************************************************************************/
class DiffusionProcess
{
   public:
     DiffusionProcess(double x0) : x0_(x0) {}
     virtual -DiffusionProcess() {}
     double x0() const { return x0_; }
     // returns the drift part of the equation, i.e. mu(t, x_t)
     virtual double drift(Time t, double x) const = 0;
     // returns the diffusion part of the equation, i.e. sigma(t,x_t)
     virtual double diffusion(Time t, double x) const = 0;
     // returns the expectation of the process after a time interval
     // returns E(x_{t_0 + delta t} | x_{t_0} = x_0) since it is Markov.
     // By default, it returns the Euler approximation defined by
     // x_0 + mu(t_0, x_0) delta t.
     virtual double expectation(Time t0, double x0, Time dt) const {
       return x0 + drift(t0, x0)*dt;
     }
     // returns the variance of the process after a time interval
     // returns Var(x_{t_0 + Delta t} | x_{t_0} = x_0).
     // By default, it returns the Euler approximation defined by
     // sigma(t_0, x_0)^2 \Delta t .
     virtual double variance(Time t0, double x0, Time dt) const {
       double sigma = diffusion(t0, x0);
       return sigma*sigma*dt;
     }
   private:
     double x0_;
};

/**********************************************************************************
Black-Scholes diffusion process class

This class describes the stochastic process governed by dS = (r â&#128;&#147; 0.5{sigma^2}) dt
+ sigmadz(t).
**********************************************************************************/
class BlackScholesProcess : public DiffusionProcess
{
   public:
     BlackScholesProcess(Rate rate, double volatility, double s0 = 0.0)
       : DiffusionProcess(s0), r_(rate), sigma_(volatility) {}
     double drift(Time t, double x) const {
       return r_ - 0.5*sigma_*sigma_;
     }
     double diffusion(Time t, double x) const {
       return sigma_;
     }
   private:
     double r_, sigma_;
};


```

I have started working with Prata "C Primer plus" which seems quite good. But should I jump directly to "C++ Primer plus" for instance?

Thanks for the advice:)

---

### Post by merinda on 2007-07-09
You should at least learn C "a little" before learning C++. Find introduction tutorial for C.

---

### Post by DC@DR on 2007-07-09
Both way are ok, I think, these two languages are pretty similar in ideas, syntax, concept v.v... But if I were you, I would start with C first, then after that learning C++ is just as easy as eating candies :-)

---

### Post by runningwithscissors on 2007-07-09
Leran C. It's nice.

You needn't learn C++ at all. It's not very nice.

---

### Post by loell on 2007-07-09
> **runningwithscissors said:**
> Leran C. It's nice.

You needn't learn C++ at all. It's not very nice.
while we share the same opinion , i don't know if its a good idea  stating the above.
get ready to be burned by c++ fanatics :lolflag:

---

### Post by lisati on 2007-07-09
> **runningwithscissors said:**
> Leran C. It's nice.

You needn't learn C++ at all. It's not very nice.

I once read that C++ started as a "preprocessor" for C

---

### Post by jcookeman on 2007-07-09
The easy answer to this question is, "no." 

C and C++ are two separate languages (oh yes they are). And, while C++ originated from C and tries to maintain compatibility, there is little to gain from attempting this. Unless you really want to know C -- you are wasting your time. Truth be told, if you know C++ really well, you will know quite a bit about C, anyway.

It's obviously quite beneficial to to learn the basics of programming and imperative language characteristics first before you dive off into OOP. But, if your sole goal is know C++, just start with it.

---

### Post by Rui Pais on 2007-07-09
C and C++ has only in common some basic syntax. The purpose and the concepts of those 2 *different* languages is different too. 
You can learn any of them without knowing the other (but since they share the same basis you can "read" one if you know the other.


If you are required to work on an environment with others working with C++ (like the  example you give), you should stick to what ever your department use, or you will find your self in trouble,trying to write compatible code or don't understanding your colleges code.




Forget other peoples preferences (why people always have to give they personal preferences when they are not asked about?...)

---

### Post by krugman on 2007-07-09
Thx for the answers guys!

Well, I don't know specifically in which department I will work, but I know that some of the programs are generally made thx to C++.

So I guess I will keep learning a few basics in C, and then switch very quickly to C++ and to Prata's book since I find his C Primer plus very good.

---

### Post by Rui Pais on 2007-07-09
A good free book is 
[Thinking in C++]("http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html") (can be downloaded as html, txt and pdf.)

Chapter 3, is named "The C in C++" and gives a resume of the C one needs for C++.

---

### Post by aks44 on 2007-07-09
If you start learning C, then switch to C++ later, you are likely to be a horrible C++ programmer at least at the beginning.

C++ is way safer than C on many aspects, and doing C-like programming in C++ defeats the whole purpose of the language.

IMHO, C teaches some concepts that should be only for advanced C++ programmers (raw pointers and unchecked casts are a plea to newbies).

On the contrary, going C++ first will teach you better programming practices, which will help you writing good C code later when you decide to learn it.

Just my 2 cents.

---

### Post by samjh on 2007-07-09
I learnt C first, and then C++.

Don't make the same mistake.

If you want to learn C++, then learn C++.
If you want to learn C, then learn C.

What happens when you learn C first?  You will end up learning C++ as an extension of C, rather than a whole new language.  C++ is much more powerful than C, and needs to be learned as a language of its own, with the most simple abstractions first, and then digging into C-like details later.

I highly recommend: [Accelerated C++](http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X)
It is an excellent tutorial-style book with a handy reference for commonly-used library features.  It's the book that made me treat C++ as a language in its own right, instead of staying handicapped by thinking about it the same way as C.

---

### Post by kknd on 2007-07-09
You don't need. 

When programming in C++, C programmers can feel tempted to use C things like *char, memcpy, etc =), very evil.

---

### Post by LaRoza on 2007-07-09
I learned C++ as my first language, and am now working on C. I can tell you I am glad I studied C++ first.

They should be seen as two different languages, and because I learned C++ first, it is easy to view it that way.

If you want free resources for learning programming, including C and C++, check out my wiki. (it is in my sig).

---

### Post by harun on 2007-07-09
> **aks44 said:**
> If you start learning C, then switch to C++ later, you are likely to be a horrible C++ programmer at least at the beginning.

C++ is way safer than C on many aspects, and doing C-like programming in C++ defeats the whole purpose of the language.

IMHO, C teaches some concepts that should be only for advanced C++ programmers (raw pointers and unchecked casts are a plea to newbies).

On the contrary, going C++ first will teach you better programming practices, which will help you writing good C code later when you decide to learn it.

Just my 2 cents.

A good 2 cents indeed. I agree with this whole heartedly :).

---

### Post by the_unforgiven on 2007-07-09
> **lisati said:**
> I once read that C++ started as a "preprocessor" for C
The first implementation of C++ compiler which was written by Bjarne Stroustrup (known as Cfront) actually used to convert the C++ code to C - it was really a preprocessor for C, so to speak. ;)
Here is wikipedia entry for Cfront:
[http://en.wikipedia.org/wiki/Cfront](http://en.wikipedia.org/wiki/Cfront)

Just a trivia ;)

---

### Post by Wybiral on 2007-07-09
I learned C++ first, then C. Not saying that was the easiest way or that I condone it, but now I can program well in both C++ and C.

After learning C though, it's hard to force myself to work on C++ projects (I like C a lot more).

I also agree that C and C++ are very different... The have some basic structure in common, but the way in which you should program with each is VERY different due to their different perks and drawbacks.

---

### Post by Wybiral on 2007-07-09
> **aks44 said:**
> IMHO, C teaches some concepts that should be only for advanced C++ programmers (raw pointers and unchecked casts are a plea to newbies).

I strongly disagree with this... Any C++ program should have a very solid understanding of pointers and manual memory management. They aren't obsolete, you will still need a working knowledge of them (even if you use them less).

This is why so many C++ programmers ask things like "how do I pass an array to a function or return an array"... Because they have no idea how the memory is laid out and how dereferencing a pointer works.

My advice: it's fine to start with C++, but don't let it blind you from the workings of the language (otherwise you will hit a problem later that requires it and have no idea how to solve it or will take the long way around)

---

### Post by Note360 on 2007-07-09
I have soem sort of inbreed contempt for C++ i dont know why. I think it is because i think its object system and syntax are brutish (I prefer the ruby, python, objective c, C#, Java object systems).

Back on topic. It was said before, if you want to learn C then learn C if you want to learn C++ then learn C++. I like Objective C myself, but i cant seem to get it working under Ubuntu. C# is also nice, but do not be confused all of them are very different (C and Obj C being the most simular).

In end, for you I would either finish the C book since you have it. Then take your brain turn it into a liquid drip that liquid out of your ear then put a new brain in and learn C++ after some time you might be able to use a centrifuge to seperate the C parts from your old brain and then drip the info back in. (Note: Do not try this at home)

---

### Post by harun on 2007-07-09
> **Wybiral said:**
> I strongly disagree with this... Any C++ program should have a very solid understanding of pointers and manual memory management. They aren't obsolete, you will still need a working knowledge of them (even if you use them less).


I will assume you mean C++ programmer and not C++ program.

Any C++ programmer who has a good understanding of pointers and manual memory management knows why you don't use either until you have to.

---

### Post by Wybiral on 2007-07-09
> **harun said:**
> I will assume you mean C++ programmer and not C++ program.

Indeed, nice catch :)

> **harun said:**
> Any C++ programmer who has a good understanding of pointers and manual memory management knows why you don't use either until you have to.

Maybe true... Although I hardly see how you can avoid it for large projects. Memory management in C++ isn't really dangerous since you've got your class destructors. But pointers... How can you avoid using and having a solid understanding of pointers and actually write programs larger then a few files?

I guess it really depends on the type of program and how efficient you intend for it to run.

How would you propose to pass an array to a function without the use of pointers? (kindof a trick question since arrays are pointers themselves)

Suppose you need to implement your own ADT like a binary tree or some custom list... You're going to do it without pointers and memory allocation? What about if you need a custom string class (say you need something different then is provided by the standard string type)?

I'm just saying... You need to learn how they work and how to use them efficiently even if you don't use them often... Because you will more then likely run into a problem that would benefit from that knowledge (and save yourself the trouble of taking the long way around)

---

### Post by rekahsoft on 2007-07-09
I personally started on C++...i am happy i made the choice to learn C++ first...i was already a java programmer and knew/felt comfortable with oop and since C++ is an expantion of C you learn things about C...the transition from C++ to C was easy :P

---

### Post by hod139 on 2007-07-09
> **krugman said:**
> Hello:)

So, I have just started learning C, but I was wondering whether I should/could directly start learning C++.

This question has been asked many times and you will never get the answer you are looking for.  Some people will say C first, others C++ first.

> 
Basically, I want to learn C++  because I am going to work in some finance departments (asset management and the likes...), and some notions of programming in C++ might be an asset, so to speak.
 
If you have a specific project in mind and it is already using C++, then I would suggest you learn C++.  Learn the language you need to.  Let other people argue about whether or not the project should have been written in C or C++ or Python or Java or Fortran or ...

---

### Post by aks44 on 2007-07-09
@Wybiral :

I totally agree with you, one can't seriously use C++ without knowing how the things work under the hood (pointers is just one subject, vtables and more generally the C++ ABI are other examples).

However, a beginner should not IMHO learn these things first. And when I said "raw pointers", I really ment "raw".

As you pointed it out, RAII is there to take care of releasing resources, and freestanding pointers should be avoided at all costs.

Concerning the common "how do I pass an array to a function or return an array..." question, I'll only say : std::vector<whatever>& ;)

---

### Post by Wybiral on 2007-07-09
> **aks44 said:**
> Concerning the common "how do I pass an array to a function or return an array..." question, I'll only say : std::vector<whatever>& ;)

Well, that works... But what if it's a character array meant to be used as a string later on? A vector might not be the best way...

You're also still using a reference, which is a pointer.

But, my only point was that even in C++ you aren't excused from understanding how memory is handled and how to create your own data types.

Because strictly using the STL types isn't going to be enough, you will have to know enough about the underlying processes to create your own ADT and there's nothing evil, difficult, or wrong with using pointers or dynamically allocated memory.

---

### Post by aks44 on 2007-07-09
> **Wybiral said:**
> But, my only point was that even in C++ you aren't excused from understanding how memory is handled and how to create your own data types.

Because strictly using the STL types isn't going to be enough, you will have to know enough about the underlying processes to create your own ADT and there's nothing evil, difficult, or wrong with using pointers or dynamically allocated memory.

Looks like there's some deficiency in my english, because I am under the impression that we're saying the same thing...

My original point was only about freestanding pointers (à la C, ie. unguarded by a RAII enveloppe).

---

### Post by Wybiral on 2007-07-09
> **aks44 said:**
> Looks like there's some deficiency in my english, because I am under the impression that we're saying the same thing...

My original point was only about freestanding pointers (à la C, ie. unguarded by a RAII enveloppe).

I personally don't think C is that unsafe...

But, that's fine. My initial disagreement was that you said that only *** advanced *** C++ programmers should deal with those concepts when I believe any average C++ programmer should be well educated about them and how to use them.

I guess your use of the term "raw" pointers is a little ambiguous.

You mean pointers without destructors?

---

### Post by aks44 on 2007-07-10
> **Wybiral said:**
> I guess your use of the term "raw" pointers is a little ambiguous.
You mean pointers without destructors?
I mean pointers that are not wrapped in a class which destructor takes care of cleaning them (which is dubbed RAII, "Resource Acquisition Is Initialization").


> **Wybiral said:**
> I personally don't think C is that unsafe...

But, that's fine. My initial disagreement was that you said that only *** advanced *** C++ programmers should deal with those concepts when I believe any average C++ programmer should be well educated about them and how to use them.
I don't think either that C is unsafe. The whole point with C is that you are in full control of the execution flow, so it is not quite hard to correctly free the resources you allocated, in every single case.

But, C programming techniques in a C++ program are often disastrous IMHO. Due to C++ exceptions, you are no more in full control of the execution flow, and unguarded pointers make it very hard to guarantee that your program will not leak.

eg.
```
Foo* bar = new Foo();
fooBar(bar);
delete bar;
```
If fooBar (or whatever fooBar uses) throws, you're doomed, bar will be leaked. That's not what I would call rock-solid code...

---

### Post by Wybiral on 2007-07-10
> **aks44 said:**
> I mean pointers that are not wrapped in a class which destructor takes care of cleaning them (which is dubbed RAII, "Resource Acquisition Is Initialization").



I don't think either that C is unsafe. The whole point with C is that you are in full control of the execution flow, so it is not quite hard to correctly free the resources you allocated, in every single case.

But, C programming techniques in a C++ program are often disastrous IMHO. Due to C++ exceptions, you are no more in full control of the execution flow, and unguarded pointers make it very hard to guarantee that your program will not leak.

eg.
```
Foo* bar = new Foo();
fooBar(bar);
delete bar;
```
If fooBar (or whatever fooBar uses) throws, you're doomed, bar will be leaked. That's not what I would call rock-solid code...

I'm aware of RAII, and I'm aware that you have to be a bit more careful when using dynamically allocated memory in C++.

But, my point was that you need to be aware. Even non-advanced C++ users should be aware of how to effectively use them. It's not dangerous when you know when and why it's dangerous.

But eventually you will need to use them... Otherwise you will take a longer approach to solve a simple problem and no one wants to do that!

Anyway, that's all I was saying... You don't have to be an advanced C++ programmer, every C++ programmer should know how to use pointers and dynamic allocation because there will come a time when they will pay off.

I guess mainly I was confused by you saying "raw" pointers and I thought you meant pointers in-general... And programming in either C or C++ without pointers is hardly worth your time. (and yes, references in C++ are basically still pointers)

---

### Post by aks44 on 2007-07-10
> **Wybiral said:**
> I guess mainly I was confused by you saying "raw" pointers and I thought you meant pointers in-general... And programming in either C or C++ without pointers is hardly worth your time.

I guess we agree then ;)

---

### Post by Wybiral on 2007-07-10
> **aks44 said:**
> I guess we agree then ;)

Yeah, I think we should give this thread back to the OP, lol.

---

### Post by pmasiar on 2007-07-10
> **Wybiral said:**
> programming in either C or C++ without pointers is hardly worth your time. 

Exactly. One does C/C++ for most efficient code. If not, why bother: better code it in less effective, more forgiving language, and be done with it faster.

So I agree with both of you that (if job is worth doing, should be worth doing right) both C/C++ should be studied with eye on maximal code efficiency (including pointer magic) or not at all.

---

### Post by the_unforgiven on 2007-07-11
> **Wybiral said:**
> (and yes, references in C++ are basically still pointers)
Not quite right..
References are more like aliases - not pointers.
Pointers can have separate existence (aka free pointer), a reference cannot - it needs to be bound all the time.
Check here for more interesting discussion on C++ references (the article also shows differences with pointers):
[http://en.wikipedia.org/wiki/Reference_(C++)](http://en.wikipedia.org/wiki/Reference_(C++))

Sorry for adding fuel to the fire ;)

HTH ;)

---

### Post by Wybiral on 2007-07-11
> **the_unforgiven said:**
> Not quite right..
References are more like aliases - not pointers.
Pointers can have separate existence (aka free pointer), a reference cannot - it needs to be bound all the time.
Check here for more interesting discussion on C++ references (the article also shows differences with pointers):
[http://en.wikipedia.org/wiki/Reference_(C++)](http://en.wikipedia.org/wiki/Reference_(C++))

Sorry for adding fuel to the fire ;)

HTH ;)

IMO references are mainly used as function parameters... But, still, if you understand what a pointer is, you can see how they are basically the same thing. They are using to point to an address.

C (using pointer)
```

void a(int *b)

a(&x);

```

C++ (using reference)
```

void a(int &b)

a(x)

```

The only difference is that the C one requires you to dereference the pointer in use.

---

### Post by LaRoza on 2007-07-11
> **Wybiral said:**
> IMO references are mainly used as function parameters... But, still, if you understand what a pointer is, you can see how they are basically the same thing. They are using to point to an address.



They are not the same thing, a reference is an alias, and a pointer is variable that holds an address.

References use pointers, but that is ony important to those making compilers.

References cannot be reassigned and they cannot be null, whereas pointers can.

---

### Post by Wybiral on 2007-07-11
> **LaRoza said:**
> They are not the same thing, a reference is an alias, and a pointer is variable that holds an address.

References use pointers, but that is ony important to those making compilers.

References cannot be reassigned and they cannot be null, whereas pointers can.

Well, yeah, obviously they have technical differences or they wouldn't have two different names... But they are essentially the same thing. Anything a reference can do, a pointer can do. Their implementation is very similar (even if they have some simple differences).

As I said, references are generally only used as function parameters, where a pointer could be used. The only difference is that you don't have to dereference the address passed using a reference, and you do with the pointer. But they are used the same... To maintain the use of an address in memory.

I am aware that they are different, but as a general understanding... Passing by reference is basically passing by pointer.

---

### Post by harun on 2007-07-11
> **Wybiral said:**
> Well, yeah, obviously they have technical differences or they wouldn't have two different names... But they are essentially the same thing. Anything a reference can do, a pointer can do. Their implementation is very similar (even if they have some simple differences).

As I said, references are generally only used as function parameters, where a pointer could be used. The only difference is that you don't have to dereference the address passed using a reference, and you do with the pointer. But they are used the same... To maintain the use of an address in memory.

I am aware that they are different, but as a general understanding... Passing by reference is basically passing by pointer.

Not quite:

[http://www.parashift.com/c++-faq-lite/references.html#faq-8.5](http://www.parashift.com/c++-faq-lite/references.html#faq-8.5)

That being said, I agree in larger projects you are going to use pointers many times but in passing as arguments usually you are going to be passing by reference. At least in most of the large projects I have been involved with.

---

### Post by LaRoza on 2007-07-11
A pointer is not a reference, a variable is not a constant, and postfix is not the same as prefix. 

Although the above concepts are similar, they are distinctly differently, and the difference is important to learn, especially when first learning a language.

---

### Post by slavik on 2007-07-11
C is simpler than C++ ...

if you want to pass an array into a function, with C you just pass the pointer, with C++ (if you are actually using OO), first you have to encapsulate the array into an object, then you have to create a copy of an object and then you send it to the function.

C vs. C++ is not a very interesting arguement because C++ is pretty much 100% backwards compatible (I haven't been able to write any C code that g++ doesn't like and I mix printf() with operator<<() a lot).

On the other hand, C++ has a lot of very nice features (that Java devs decided to not put in) like operator overloading.

But don't forget that even C can be used to write object oriented code ... (look at GTK and X)

---

### Post by Wybiral on 2007-07-11
> **LaRoza said:**
> A pointer is not a reference, a variable is not a constant, and postfix is not the same as prefix. 

Although the above concepts are similar, they are distinctly differently, and the difference is important to learn, especially when first learning a language.

I know the difference :)

I actually don't recall ever saying that they were the exact same thing, I just said there were similar and used similarly.

A reference grabs an address and allows it to be used as a normal variable, while a pointer stores and address and must be dereferenced first before use.

Regardless, they "point" to an address in memory...

If you don't believe me I would be glad to dissect some C++ assembly output for you and point out why I say they are so similar.

---

### Post by LaRoza on 2007-07-11
> **Wybiral said:**
> I know the difference :)
If you don't believe me I would be glad to dissect some C++ assembly output for you and point out why I say they are so similar.
> 
References use pointers, but that is ony important to those making compilers.


Sorry if I offended you. I know they are similar, but I think you are saying that because you understand them. For someone who doesn't understand them, saying they are similar is just confusing. It is best for a person starting out to have the two distinct in there mind.

My previous post, quoted above, show I believe you.

---

### Post by slavik on 2007-07-11
If you ask a java person, references are completely different than pointers. :)

---

### Post by Wybiral on 2007-07-11
> **LaRoza said:**
> Sorry if I offended you. I know they are similar, but I think you are saying that because you understand them. For someone who doesn't understand them, saying they are similar is just confusing. It is best for a person starting out to have the two distinct in there mind.

My previous post, quoted above, show I believe you.

OK. No harm done.

But this sort-of goes back to my original point... Which is that C++ programmers need to understand the dirty C underbelly to actually understand what is going on in the higher C++ code.

Any C++ programmer who thinks that using a reference parameter is just magically linking it to the variable passed to it obviously has no clear understanding of how data is being stored.

IMO, to be a programmer in any language one should have a thorough understanding of how the elements of the language work. I don't mean that everyone should study the assembly output (although it helps... Immensely) but it's VERY important that a C++ programmer understand exactly how data is stored and accessed.

Like I mentioned in an earlier post, this is why so many C++ programmers don't know how to handle things like arrays... They think "wow, how am I supposed to pass all of these 'variables' to a function?" not realizing that the array label is just a pointer and using "x[y]" is just dereferencing that pointer with an offset (the same as "*(x+y)").

But, we seem to be on the same page, I guess the only difference is that I DO think beginners should learn these things. Otherwise they have a warped perception on how data is being stored, and managed.

As pmasiar was getting to... If you don't want to take advantage of the low-level perks of using C and C++, then why bother using them at all? Why not use python or something that would speed your development and benefit from other peoples understanding of the low-level parts?

---

### Post by LaRoza on 2007-07-11
> **Wybiral said:**
> OK. No harm done.

But this sort-of goes back to my original point... Which is that C++ programmers need to understand the dirty C underbelly to actually understand what is going on in the higher C++ code.

IMO, to be a programmer in any language one should have a thorough understanding of how the elements of the language work. I don't mean that everyone should study the assembly output (although it helps... Immensely) but it's VERY important that a C++ programmer understand exactly how data is stored and accessed.

As pmasiar was getting to... If you don't want to take advantage of the low-level perks of using C and C++, then why bother using them at all? Why not use python or something that would speed your development and benefit from other peoples understanding of the low-level parts?

I am studing assembler now, if only to learn how things work. (And because its fun, but I need a real reason to justify it).

---

### Post by pmasiar on 2007-07-11
> **Wybiral said:**
> IMO, to be a programmer in any language one should have a thorough understanding of how the elements of the language work. ... it's VERY important that a C++ programmer understand exactly how data is stored and accessed.


In dynamically typed languages like Perl/Python/Ruby, big part of this "dirty underbelly" is hidden from casual users by design. But if any speed-obsessed C++ wannabe thinks s/he can rely on "magic" without understanding it, someone is for ugly surprise.

[Bruce Eckel](http://en.wikipedia.org/wiki/Bruce_Eckel) wrote excellent books explaining design decisions in Java and C++: not only *how* language features work, but *why* they were designed that way. Extremely enlightening reading, IMHO. Available for free download legally, but if you can afford it, think about buying paper book: we need to encourage people like Bruce to keep publishing. :-)

---

### Post by slavik on 2007-07-11
like someone said (I think it was on slashdot), you need to understand the level under which you work ...

for C++, it's C, for Java, it's the jvm, for C, it's assembly, so on and so forth.

---

### Post by Yasumoto on 2007-07-12
> **slavik said:**
> like someone said (I think it was on slashdot), you need to understand the level under which you work ...

for C++, it's C, for Java, it's the jvm, for C, it's assembly, so on and so forth.

hm. That's a really good point. Now I've just got to make the time to learn everything, and then actually *apply* that knowledge.

---

### Post by Sockerdrickan on 2007-07-13
I heard C++ is better for games.

---

### Post by runningwithscissors on 2007-07-13
> **Tux0r said:**
> I heard C++ is better for games.Where from?

---

### Post by jdmrsx05 on 2007-07-13
I've taken classes in both C and C++ (as I'm sure a lot of you on this thread have) and it seems to me as though they are two different languages, no matter what language you decide to use, once you learn the syntax the logic is very much the same.  But I guess I'll find that out when I take more classes this semester.  Anybody suggest where to go from C++?

---

### Post by Wybiral on 2007-07-13
> **Tux0r said:**
> I heard C++ is better for games.

Actually, a number of the ID games (the people who made wolf3d, doom, and quake) were written in C, even though C++ was pretty big at the time. It wasn't until the most recent doom that they used C++ instead.

C++ is used a lot these days... But all of the C++ engines I've looked at recently have one thing in common... They're basically just C code, lol. I think people just use it for it's popularity and some parts of the STL. But for a program that demands efficiency such as game engines, you aren't going to see a ton of C++'s OOP features being used (simply because the dirty, low-level way is going to be faster and smaller).

Anyway, neither is "better" if you know your language. And it certainly depends on the type of game, the availability of libraries, and the desired performance.

---

### Post by pmasiar on 2007-07-13
> **Tux0r said:**
> I heard C++ is better for games.

This is exactly how rumors are spread. Someone with little clue starts repeating that, and it is spread by others with even less clue. If author cannot argue why it is so, why even repeat it?

And for what values of "better" is it true?

C++ is higher level, so it allows for more abstraction - pushing more work from programmer to compiler. It means that code is easier to write, and less effective. Same as C is "better" than assembler, and Python is "better" than C++. "Better" depends what are your goals, and where you want to make compromises. Programming is engineering, not religion or morale. :-)

---

### Post by slavik on 2007-07-13
C++ makes OO easier as comapred to C. OO is still possible with C.

---

### Post by eoshicute on 2007-07-13
hmm I think not, why? because C and C++ are same language. if you can C++, absolutely you can C :)

---

### Post by aks44 on 2007-07-13
> **slavik said:**
> C++ makes OO easier as comapred to C. OO is still possible with C.

The point (IMHO) is that OOP is harder to do in C than in C++, while "plain old C" is just as easy to do in C++ than in C.

Even though I am a strong advocate for C++ programming techniques, the language itself still allows you to do pure C (set apart a few minor syntax differences that don't really matter) without any performance loss compared to plain C.

The contrary is not true: C's "OOP" workarounds impose an awful burden on the programmer (which is a performance loss, on the developper side), and there are very strong chances that your OOP C code isn't even near the quality of C++ compiler-generated code (runtime performance loss).

C++ being a superset of C, why not using the most adequate tools to do the job? (sometimes it will be OOP, sometimes good ol' procedural programming)

---

### Post by Wybiral on 2007-07-13
> **aks44 said:**
> The contrary is not true: C's "OOP" workarounds impose an awful burden on the programmer (which is a performance loss, on the developper side), and there are very strong chances that your OOP C code isn't even near the quality of C++ compiler-generated code (runtime performance loss).

Do you have any proof that C++ compilers generate more efficient OOP code then the C "work around"? I would love to see some examples of this.

I think OOP is helpful... Sometimes... But pure OOP usually isn't a requirement. And if you want to discuss performance, well, OOP isn't the best method when you want minimal-memory-maximum-speed performance.

OOP is good for abstraction and code reuse which can result in faster development time, but when the job doesn't require abstraction and does require maximum performance (such as a game engine) then the pure OOP approach isn't going to do anything but add overhead.

I think it's wisest to pick and choose the most efficient features from OOP, not use all of it simply because you want your code to fit into that paradigm.

> **aks44 said:**
> why not using the most adequate tools to do the job? (sometimes it will be OOP, sometimes good ol' procedural programming)

That I agree with.

---

### Post by hod139 on 2007-07-13
> **pmasiar said:**
>  Programming is engineering, not religion or morale. :-)
Yeah right!  As much as I want to agree with you, even the small number of <strike>flame wars </strike> debates on these forums disproves this statement.  I've been surprised actually with how well behaved this thread has remained.  Anytime you have more than one way to solve a problem, arguments will arise over which way is better. 

These arguments don't disappear at the higher level software design questions.  For a single example, people are still arguing over the model-view-control GUI design principles.  There are pros and cons to having multiple ways to solve a problem, and one of the cons is all the bickering that will occur over which way is better.

[quote=eoshicute]
hmm I think not, why? because C and C++ are same language. if you can C++, absolutely you can C :smile:
[/quote]
This is absolutely not true!  C and C++ share some syntactic similarities, that's it!

---

### Post by Wybiral on 2007-07-13
> **hod139 said:**
> There are pros and cons to having multiple ways to solve a problem, and one of the cons is all the bickering that will occur over which way is better.

Ah, but one of the pro's is having a diverse gene pool of ideas to evolve.

---

### Post by LaRoza on 2007-07-13
> **Wybiral said:**
> Ah, but one of the pro's is having a diverse gene pool of ideas to evolve.

i agree, it is good for people to *discuss* languages and advantages and disadvantages. If noone did that we'd all be using VB.

---

### Post by aks44 on 2007-07-13
> **Wybiral said:**
> Do you have any proof that C++ compilers generate more efficient OOP code then the C "work around"? I would love to see some examples of this.

The only "example" I can give you, is that at work we had a pretty hard time handwriting asm routines that would beat a C++ optimizing compiler. And the team is far from incompetent IMHO...

> **Wybiral said:**
> OOP is good for abstraction and code reuse which can result in faster development time, but when the job doesn't require abstraction and does require maximum performance (such as a game engine) then the pure OOP approach isn't going to do anything but add overhead.

I can't disagree on this, obviously. My point being: I consider development time being part of the "performance", as much as runtime performance. IOW, get to know your tools and use them the most wisely you can ;)


> **hod139 said:**
> This is absolutely not true!  C and C++ share some syntactic similarities, that's it!

Again, C++ is (almost) a superset of C, set apart a few minor syntax differencies in some very obscure cases.

---

### Post by aks44 on 2007-07-13
> **LaRoza said:**
> i agree, it is good for people to *discuss* languages and advantages and disadvantages. If noone did that we'd all be using VB.

Naaah, we'd be all using ASM because it was what was there in first place ;)

---

### Post by hod139 on 2007-07-13
> **Wybiral said:**
> Ah, but one of the pro's is having a diverse gene pool of ideas to evolve.
This is absolutely true.  I didn't state any of the many pros of having multiple solution paths available in my previous post.  My personal preference, and maybe I should have stated it in my previous post, is to have multiple options available for solving problems.

My only intention was to point out that because of the abundance of solutions available (e.g. languages, design principles) people will always argue over which is better.  There is an "artistic" quality to programming, it is not purely engineering.

---

### Post by aks44 on 2007-07-13
> **hod139 said:**
> My only intention was to point out that because of the abundance of solutions available (e.g. languages, design principles) people will always argue over which is better.  There is an "artistic" quality to programming, it is not purely engineering.

So true :)

---

### Post by LaRoza on 2007-07-13
> **aks44 said:**
> Naaah, we'd be all using ASM because it was what was there in first place ;)

I was also referring to the growth of the community and languages like C/C++, Python, Perl and other evolving languages that are the result of people sharing ideas and not being stifled by a single entity.

---

### Post by hod139 on 2007-07-13
> **aks44 said:**
> 
Again, C++ is (almost) a superset of C, set apart a few minor syntax differencies in some very obscure cases.
Again, C++ and C are very different languages.  Can you write most C code in C++, yes.  I won't argue that.  However, C++ supports OOP (by design), generics, operator overloading, etc.  These additions radically change the way you use the language.  You would not, or rather should not, write C style procedural code in C++.

---

### Post by Wybiral on 2007-07-13
> **aks44 said:**
> The only "example" I can give you, is that at work we had a pretty hard time handwriting asm routines that would beat a C++ optimizing compiler. And the team is far from incompetent IMHO...

Seriously? What kind of code are we talking about here?

I know I can usually write better assembly then the GCC compiler.

But maybe you guys are using a good optimizing compiler?

---

### Post by aks44 on 2007-07-13
> **Wybiral said:**
> Seriously? What kind of code are we talking about here?

I know I can usually write better assembly then the GCC compiler.

But maybe you guys are using a good optimizing compiler?

Well, Microsoft's compiler is a very good one, indeed.

---

### Post by LaRoza on 2007-07-13
> **aks44 said:**
> Well, Microsoft's compiler is a very good one, indeed.

Is it free and ansii compliant?

---

### Post by Lster on 2007-07-13
Sorry to get off topic but does anyone know of a good reource that compares Visual C++ and G++ (or GCC)? I would be very interested to see how they compare performance wise...

---

### Post by aks44 on 2007-07-13
> **LaRoza said:**
> Is it free and ansii compliant?

No, and no. But it works on our customers' platform and produces quality code. Not that I agree with using it though, but this decision isn't in my hands.

---

### Post by LaRoza on 2007-07-13
> **aks44 said:**
> No, and no. But it works on our customers' platform and produces quality code. Not that I agree with using it though, but this decision isn't in my hands.

Well, I guess I won't be using that. Do you know of a Free Ansii C compiler for DOS? (off topic, but I am hoping someone knows of one)

---

### Post by Wybiral on 2007-07-13
> **aks44 said:**
> Well, Microsoft's compiler is a very good one, indeed.

But this issue really depends how good the people writing assembly code are. If they weren't assembly programmers by nature, they weren't going to be able to generate equivalent code.

---

### Post by Wybiral on 2007-07-13
> **Lster said:**
> Sorry to get off topic but does anyone know of a good reource that compares Visual C++ and G++ (or GCC)? I would be very interested to see how they compare performance wise...

I've seen conflicting benchmarks... I don't think either is officially better. Maybe better in certain areas of optimization.

---

### Post by aks44 on 2007-07-13
Not sure about the GNU vs MS thing (I'm very new to the Linux environment), all I can tell is that VC 8.0 is way better than that crappy VC 6.0, and has had many enhancements concerning standards compliance (should we thank Herb Sutter for this?).

The only part I've seen VC8 being really deficient is concerning "advanced" SFINAE templates.

Too bad it still relies on so much proprietary double underscore keywords...

---

