---
title: "things you like/love about a language"
date: 2007-09-04
forum: Programming Talk
---

### Post by slavik on 2007-09-04
I hope this is "deep enough"

post something that you hate/love about a language. It has to be something specific.

---

### Post by LaRoza on 2007-09-04
> **slavik said:**
> I hope this is "deep enough"

post something that you hate/love about a language. It has to be something specific.

Subject: PHP

I like this language more than most for daily use. I like its similarity to C, with its dynamic typing, easy to understand variable names, $varname, and its OO (in PHP5).

I realize that other languages fit this describtion, and have advantages over it, but PHP is something I "love", if one could be said to "love" a language. 

Other languages I like (so others don't think I use one language and think it is the "best"):
* Python
* C
* C++
* ECMAScript
* Fortran
* (working on) Java, Assembly, Perl and other languages I come across.

---

### Post by pmasiar on 2007-09-04
> **slavik said:**
> I hope this is "deep enough"

post something that you hate/love about a language. 

I think [this my post](http://ubuntuforums.org/showpost.php?p=3307798&postcount=26) explains the "deep enough" part of OP. :-) Yes, this is deep question, and my post explains what I like on languages.

We will see which thread has bigger staying power, if this one can be kept clean, might get stickied...

Right now I am not sure where to continue discussion:  here, or where it started. We shall see (and clean the mess later).

So here is copy/paste:

I like if language has small number of basic concepts which work good with each other. Like in Python, you can use for loop to iterate through a list, array, string, tuple, dictionary, or iterator expression. All of these are **very** different by themselves, but it makes sense to look at every item in them one by one, and **exactly same syntax** allows me to do that.

I like language which allows me to pass parameters in a flexible way, and make changes later, and still have it reasonably easy. What if I need to pass function as a parameter? What if I need to return more than simple scalar value from a function? What If this scalar returned here needs to become array? How many headstands and push ups I need to do to make compiler happy?

I like language which lets me to use facilities accessible to it. If "they" can do it, I want be able to do it, when I need it. I remember PROGRESS database was able to make some operations on system data types which were not possible on my variables of same type. I forgot the details now, but I remembered how I was annoyed: they just decided that I am just a farmer in dirty boots and not smart enough to handle it, so I am not allowed to handle it. Yes, I like language to tread me as responsible smart adult, not as dumb relative who needs to be protected for his own good. Like operator overloading in java: they can do it for strings, but I cannot. Come on! If it is useful to you, it could be useful to me to!

I like language "to make simple things easy, and hard things possible". My first language with this approach was Perl, and I **loved** it. Duck-typing is so great, I could not believed how you can write code without fighting with compiler, and if you passed object done properly, it just works. So compiler might be your friend, not gestapo interrogator! What a concept!

Also, simple things should **look** easy. Like ZIP compression: if something is used often, add some syntax sugar so it **looks** easy. If something is dangerous, add some syntax vinegar to it so it looks scary. As I read some architect talking about "design patterns" and how to judge them: design pattern is good, if people use it right way intuitively, without thinking. Like push and pull doors: It is hard to pull on push side, and pull side just invites you to pull (and not push). I am not sure how doors are done in other (non-USA) countries tho

Edit: BTW I did not answered same day as posted, I thought about it, and slept over it, and thought again, and **then** I wrote my answer :-) You may want to try it too it works :-)

---

### Post by Carl Hamlin on 2007-09-04
I'm a concrete thinker. Logical abstraction of real functionality makes me feel like I'm at an uncomfortable remove. I don't like it.

That's why I code in ASM. At any point in the execution process, I can envision the exact opcode that's executing. If the necessity arises, I can patch the binary.

If my code creates a segmentation fault, the overwhelming likelihood is that I know why before I even go back to the code, and halfway suspected that I was going to have to deal with it.

Data corrupting itself in memory?

Oop. Looks like I wasn't as careful as I should have been shunting off a child process.

Plus, my code runs *lightning* fast.

High level languages offer me none of this. They make me uncomfortable. I don't like them.

With ASM, I know *exactly* where I stand.

------

ASM is the first programming language I ever learned. I'm reliably informed that were that not the case, I might think better of high-level programming.

Maybe.

I just hate having to blow away all the smoke and mirrors just to get to the root of the problem.

---

### Post by AntiRush on 2007-09-04
> **Carl Hamlin said:**
> I'm a concrete thinker. Logical abstraction of real functionality makes me feel like I'm at an uncomfortable remove. I don't like it.

That's why I code in ASM. At any point in the execution process, I can envision the exact opcode that's executing. If the necessity arises, I can patch the binary.

If my code creates a segmentation fault, the overwhelming likelihood is that I know why before I even go back to the code, and halfway suspected that I was going to have to deal with it.

Data corrupting itself in memory?

Oop. Looks like I wasn't as careful as I should have been shunting off a child process.

Plus, my code runs *lightning* fast.

High level languages offer me none of this. They make me uncomfortable. I don't like them.

With ASM, I know *exactly* where I stand.

------

ASM is the first programming language I ever learned. I'm reliably informed that were that not the case, I might think better of high-level programming.

Maybe.

I just hate having to blow away all the smoke and mirrors just to get to the root of the problem.

I, too, am an ASM afficionado.  Writing something in assembly is generally much more satisfying to me than in a higher level language.  You feel like you've accomplished more.  

It is interesting to note though, that most modern compilers will produce more efficient assembly than a human coder - at least in some cases.  They are very good at unrolling loops, substituting pre-incrementing for post-incrementing, and efficiently eliminating unneeded recursion.  

Python gets my vote for a higher level language.  I love it's rich built in library which makes quick projects where it is more important to be fast than quick much faster to code.

---

### Post by slavik on 2007-09-04
but what specific feature of php do you like/love? anythign you hate about any language? (this is supposed to be more about who did what right and who did what wrong in your eyes).

---

### Post by Wybiral on 2007-09-04
> **Carl Hamlin said:**
>  ... 

I too used to be a huge assembly fan. I still code in it as a hobby (because admittedly, it's fun).

But... Assembly comes with three downsides... Lack of portability, difficulty managing large projects, and increased development time.

After I got used to C, then C++, now I'm getting into Python... I still go back to assembly every now and then for the challenge, but I can whip out applications in C++ and Python in a couple of days that would take me months to develop in assembly. And I know that they will be portable.

Sure, there are times when assembly is perfect, like when you need to brute force something or use direct hardware communication. But since I rarely find myself needing either of those; C, C++, and Python seem to suite my needs very well.

As far as speed goes... Believe it or not, assembly isn't always faster. Before you gasp and claim the absurdity in that statement, consider the fact that the most impactive optimizations are not the smaller operations themselves, but rather are the larger algorithmic implementations. A good example I can give is a 3d terrain engine I was working on recently...

There was no physical way I could optimize it any further using low-level optimization. I had shaved off all the operations I could and it still was not fast enough. Then I took the abstract route and explored various high-level optimization techniques (most of which would have taken months to code in assembly, but were implemented in C++ within a number of days)... The results were outstanding, it finally began to run at a usable speed. This is why high-level abstraction pays off most of the time...

Looking at the problem from a far allows you to shave off huge amounts of low-level operations because it makes it easier to algorithmically optimize. Looking at the problem under a microscope allows you to shave off a few isolated operations, but it just isn't as big of an impact as optimizing the entire algorithm itself.

In short... I enjoy the fun of coding in assembly, but hate the lack of portability and increased dev-time... And I enjoy the abstraction of C++ and Python because I can look at the problem in a more human way, thus making it easier to algorithmically optimize.

---

### Post by LaRoza on 2007-09-04
Ah, I didn't realize this thread was an extension of another.

I like PHP usability and flexibility. It has the features of C, Java, and Python that I like:

* C style
* Opjects like Java
* Python's dynamic typing

PHP has the ability to pass by reference, and value.

One thing I strongly dislike about PHP is the global namespace has thousands of functions, :(

Now for Hate: I can't say I hate a language or feature unless I were informed about it, but PHP's cluttered global namespace is possible the worst thing I have every seen in any language. Why should I have to rely on the syntax highlighting of my editor to find if a function is already defined?

---

### Post by slavik on 2007-09-04
peoples ... this isn't a discussion about languages. :) This is more of "LanguageX does Z and I really hate it" or "LanguageY does W and I love it"

---

### Post by kknd on 2007-09-04
I like languages with a good organization, portability, and speed.

---

