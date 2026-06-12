---
title: "Linux/Programming Advice"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by kam2 on 2014-04-02
Hi all,

So I have recently just downloaded Ubuntu 13.10 and am wanting to learn how to program. Unfortunately I have no programming experience so i thats why i have come here. I was wondering if Linux is the best OS for programming, and if so then is Ubuntu going to suffice for beginners programming? Also if anyone out there has any tips or any where I can go to read up and learn how to start with programming that would be awesome! (I would like to start learning C/C++ programming language)

---

### Post by Double.J on 2014-04-02
Hi there! 

Welcome to the forums!

i got started with [cprogramming]("http://www.cprogramming.com/tutorial.html") and used [cplusplus]("http://www.cplusplus.com") as a reference.

i also understand that codecademy are planning to introduce c/c++ in the future, though could be some way off.

i personally do like linux for programming as it is easy to test them from the command line. At the end of the day you should use the os, or at least have available the os that you plan to code for.

in terms of IDEs to write your code in , I like code::blocks, geany and eclipse in that order for c++. (All in the repos)  some people say just a text editor is best so you don't become dependant on grammatical assistants. I do not believe this is best for the beginner. I do advise using a full featured ide at the start as you're going to benefit from the help.

Finally do you know what you plan to code for? C++ and especially C are now seen as lower level languages, which makes things like C great for kernels, but a bit over complicated compared to say python if you were working on databases? 

Best of luck! Do not give up. It will get challenging, but will end up so rewarding!

---

### Post by kam2 on 2014-04-02
Thanks for the reply!

I will definitely be checking out those references and will be checking out those IDEs as well. I haven't really set my mind on which language i would like to start coding with, i really just said c/c++ because I'm in touch with a few people who are adequate with the language. I would LOVE to learn python but i thought i should probably start with a basic programming knowledge before i start with such an advanced language, or is it not necessary and is smarter to just jump into python? What do you think?

---

### Post by Double.J on 2014-04-02
So, what do you start with? That could literally turn this thread into war and peace - there is no correct answer.

just to help programming languages are often described as high level or low level or somewhere in between.

Here's the catch - it basically means the opposite of what you think; it doesn't actually mean that say python, which is high level is hard to learn, and c which is now considered low level is hard.

to explain, as I'm sure you are aware everything you're computer does is 1's and 0's. Your computer is also just a calculator, so every program is just a binary mathematical problem to your computer. As you can imagine, it's take a lifetime to tell your computer the whole equation, so languages do the hard work for us. The first of these were assembly and machine codes. They enabled chips to be programmed quickly, but not in a very fast or easy to read way. It was still us having to talk like a computer. These would be classified as the lowest level languages. That is because they are the least removed from what the machine is doing (not very abstract) many languages later, C came out. Now at the time it was considered high level!

This was because it was one if the furthest removed from what was happening. Instead of typing out machine code which very literally tells the chip what to do, you write in easy to read sentences that make sense to us, and then the compiler translates these commands through a dictionary to generate the code.

If you've ever used google translate to translate a french document, you'll understand that this means here may have been a more efficient way to write it if you had a french person to hand!

Fast forward 30 years and the sheer scale of software means that those early low level languages are now impractical and only used for firmware and the once high level C is now used for things like kernels because it has the right balance between ease of writing and abstraction - as of last year, the linux kernel was just shy of 17 million lines of code worked on by one and a half thousand developers; they need to be able to easily read it (just fyi it started out just shy of 175 thousand 20 years ago!)


Now something like python is high level not because they are harder to learn, but because they are easier to learn. Python has a huge library of functions so that you don't have to type it all out, it also does away with a lot of grammar and is a language closer to our own than that of the computer chips. It looks very similar to C in a lot of ways, but it is the grandchild. Same goes for ruby and java. You wouldn't write a kernel in java or python or ruby for a whole host of reasons, but the main one is that they are high level languages - they create additional abstraction between the coder and the chips. Over 17 million lines of code this will decrease performance and as a kernel is such a low level part of an os introduce errors without providing an adequate user performance boost over C. C also has a lot of those built in functions I was talking about designed specifically for this kind of use. It is complex for a reason.

Now if you were going to make an app, you'd likely use java - it's built in functions are most helpful to this. You could write it in c++ but you wouldn't really get a performance boost for all your hard work because you aren't making use of it's abilities. 

Honestly if python interests you - head on over to codecademy and take the python course! If nothing else codecademy will set the basics of programming for you - skills you can take to any language!

just to help make it clearer; here's and example of the famous 'hello world' program in C and python:


C:
```
#include <stdio.h>
main()
{
    printf("hello world");
}

```
python:
```
print "hello world"

```

see how they do the same but there's that little bit more grammar in C? It's what makes it low level and python high level.

neither is better. Just different tools. They all end up as 1's and 0's!

jj

---

### Post by Double.J on 2014-04-02
Oh also,

if you do decide to use python as stated I recommend [ninja ide]("http://ninja-ide.org/downloads/"). You have to add it's repository at the moment, but it'll be in the 14.04 repo! 

You can use the other ide's with plugins but I've grown to really like ninja and i was very pleased to see it added to the main ubuntu repo in the 14.04 alpha

---

### Post by Rob Sayer on 2014-04-02
Linux is a good environment to program in because it's open source.  There's nothing hidden from you.

I'm not convinced that C is the best language for beginners.  It's not a high level language ... more medium level, or a high level assembler.  It's ubiquitous largely because it's extremely portable.  Certain concepts that are a bit much for beginners, like pointers, are essential in C.

I think the CS department at the local university is using Python in the intro computer science programming course.  C++ is more second year.  I'd try python first if I were you.

---

