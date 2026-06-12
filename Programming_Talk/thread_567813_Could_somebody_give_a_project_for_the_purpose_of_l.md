---
title: "Could somebody give a project for the purpose of learning!"
date: 2007-10-05
forum: Programming Talk
---

### Post by Squish on 2007-10-05
Hi, this is really a simple request.

I have decided to take on programming, and I definitely have a heart and passion for it, especially solving bugs and such. So I am taking online tutorials to learn this, but its sometimes pretty brutal just reading and reading and reading....

Anyways, I am trying to learn python right now, but its hard not having a goal. So I  am asking for someone to give me a realistic goal for me to strive for.
Like, Program a calculator in python or something like that.
Perhaps make a program that counts how many times I type the A button on the keyboard.

I dunno if any of those goals are realistic, which is why I come to the community. Anyone got a suggestion?

Thanks all, it is my hope that one day I can contribute to the opensource community.

---

### Post by smartbei on 2007-10-05
How about this:
Program a calculator that takes as input a string from the user and prints out the correct answer. It should support the following operands:
[LIST=1]
[*] ( and )
[*] - (negative)
[*]! (factorial)
[*]& (minimum of two numbers)
[*]@ (maximum of two numbers)
[*]^
[*]*
[*]/
[*]+
[*]-
[/LIST]

Those are in order of priority.

Also check out projecteuler.net for simple challenges and as you progress, some not-so-simple ones. Have fun!

---

### Post by tehkain on 2007-10-05
Also what I did years ago for my first programing project was a address book. I needed it to work over ssh so it was commandline only.

Hint:
raw_inputs
dictionary inside a dictionary.
{ 'John':{'name':'John','number':233-2334}, another dict....}

Save it using one of the many modules(cPickle, and the database dict one)

---

### Post by dwhitney67 on 2007-10-05
Try this on for size:  [CLFS]("http://www.linuxfromscratch.org/clfs/view/1.0.0/x86/index.html").  No, it isn't programming, but it will surely teach you about how a Linux OS is created.

Perhaps you can write a shell script to automate the process.

---

### Post by Squish on 2007-10-05
Aye thanks, I shall get started on these tomorrow

And then, I am going to save christmas!

---

### Post by ryno519 on 2007-10-05
> **dwhitney67 said:**
> Try this on for size:  [CLFS]("http://www.linuxfromscratch.org/clfs/view/1.0.0/x86/index.html").  No, it isn't programming, but it will surely teach you about how a Linux OS is created.

Perhaps you can write a shell script to automate the process.

I think he wanted to learn how to program, not automate the process of cross compiling an entire GNU/Linux system.


To answer the question. High schools and universities hold programming competitions every so often which is basically a challenge to see who can solve a certain coding problem the fastest. Typically you get 2 hours to code around 4 or 5 of these questions.

These questions, while typically geared towards more experienced programmers (who could finish them in a few minutes) could provide you with a few interesting challenges that you might be able to finish in a couple hours a piece. After a competition is finished they post the questions and test data online for anybody interested to answer. You can go to one of these sites, download a question sheet and the test data and have at the questions. Here's a link.

[http://cemc.uwaterloo.ca/ccc/past/previous_contests.shtml](http://cemc.uwaterloo.ca/ccc/past/previous_contests.shtml)

---

### Post by pmasiar on 2007-10-05
Wiki in my sig has some training tasks, and links. Check also pythonchallenge.

Python interactive shell IS calculator. To program calc, just read a string, and evaluate it.

---

### Post by rplantz on 2007-10-05
> **Squish said:**
> Hi, this is really a simple request.
I have decided to take on programming, and I definitely have a heart and passion for it, especially solving bugs and such. So I am taking online tutorials to learn this, but its sometimes pretty brutal just reading and reading and reading....


People who learn on their own typically write pretty awful code. I say this from the experience of starting programming in the early 1960s with very little formal training in it. It took many years of having others critique my code and having to read the code that others wrote before I got any good at writing it.

I started teaching programming in 1980 and learned a LOT more about it over the next 24 years. Students, especially beginners, ask very embarrassing questions; I had to do a lot of studying and thinking. If you really want to learn something, try explaining it to somebody else. Then you will discover where your knowledge gaps are. :)

If you don't have anybody to work with, I suggest getting some books with lots of examples. Start by copying the examples. Make small changes in them and see what happens.

There are two important things to know about programming:

(1) The main reason to do it in software is so it can be easily changed. Otherwise, it would be done in hardware. So try to write your code in such a way that somebody else can easily change it.

(2) Write your code such that others can easily understand WHY you have written it that way. Even if you are the only one who ever looks at it, you will have forgotten your train of thought the next time you look at your own code.

---

### Post by Squish on 2007-10-07
This is all very fantastic advice. I'll try making those good habits.

Unfortunately, I have no partners in crime, but I do have an extrodinary amount of free time.

Lets get too it!

---

### Post by samjh on 2007-10-07
Some of my first projects were small (around 10 to 20 hours) but useful:
[list][*]File compressor (similar to zip and unzip).[*]File comparison utility (similar to grep).[*]SI/Imperial unit converter.[*]Audio recorder and playback utility.[/list]

Have a go! :)

---

### Post by aks44 on 2007-10-07
> **samjh said:**
> File compressor (similar to zip and unzip).

This is indeed the very first (complete) program I ever wrote. Huffman tables are something very easy to begin with.

---

