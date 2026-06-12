---
title: "[SOLVED] Bash or Python?"
date: 2008-04-16
forum: Programming Talk
---

### Post by Sinyster69 on 2008-04-16
:)Hello everyone 

Before I start I did do my reseach and yes i am a complete noob to Programing, I have used Ubuntu for the past 4 months now and i decide to buy a laptop with ubuntu 7.10 on it. 

I know what languages i am going to learn(Python, Bash, Ruby, C and C++).

But for my first language i am stuck between Python and Bash.. 
Some of my friends tell me to learn Bash first, so i can understand linux better, then move on to programing in other languages and others say its not that important to learn bash first.

In your guys opinion what should i do?

---

### Post by Xavieran on 2008-04-16
I would learn Python...it is a lot more object oriented than BASH and can be used to the same effect...

I personally find that a combination of BASH and python (os.system("command")) is very useful...
:)

---

### Post by slavik on 2008-04-16
> **Xavieran said:**
> I would learn Python...it is a lot more object oriented than BASH and can be used to the same effect...

I personally find that a combination of BASH and python (os.system("command")) is very useful...
:)
start explaining what OO is, don't forget exceptions while you're at it.

to the OP: I agree with your friends. pick up some BASH and then move on to something bigger.

Warning: I am a C/Perl proponent.

---

### Post by ghostdog74 on 2008-04-16
you have 5 choices only. just pick one and start. Don't waste time waiting here for an answer because there will be no perfect answer.

---

### Post by LaRoza on 2008-04-16
Bash is good to know (ghostdog74 drives this point home), however, I think it isn't the best language to start with unless you need it.

Python (as it is in the title) is a better place to start with programming.

EDIT: I had written this before ghostdog74 actually posted...

---

### Post by pmasiar on 2008-04-16
Bash is good to know but not good to start. When you know Python, you can safely ignore 60% of bash with no bad consequences.

Ruby is very like Python, so no much gain learning it. But C is good to know.

Consider more "different" languages, like lisp, SQL, prolog - and Javascript with HTML/CSS is also extremely useful to know.

---

### Post by arist0tle on 2008-04-16
Python..... you'll pull your hair out with bash

---

### Post by ghostdog74 on 2008-04-16
> **arist0tle said:**
> Python..... you'll pull your hair out with bash
how does bash make you pull your hair out?

---

### Post by ghostdog74 on 2008-04-16
> **pmasiar said:**
> Bash is good to know but not good to start. When you know Python, you can safely ignore 60% of bash with no bad consequences.

when you know bash/shell, you still can work in *nix without Python. Except complicated requirements, for basic programming, Bash is as good as Python for starting out.

---

### Post by mssever on 2008-04-16
Bash is good to know just for normal every day CLI work, if nothing else. It's also installed on virtually every UNIX-like system out there. But its poor error handling can be annoying, as is the difficulty of doing many common tasks (that's why awk/sed were invented, which were replaced by Perl and later by Python and Ruby). Better learn Bash first, because once you learn Ruby or Python, you won't want to suffer the pain of learning Bash later. :)

---

### Post by Wybiral on 2008-04-16
> **ghostdog74 said:**
> how does bash make you pull your hair out?

BASH isn't meant for programming, it's meant for gluing other applications together with *limited* support for programming constructs and data structures. And since there's no reason to say it's easier than Python, while there are obvious reasons to say it's more limited than Python, I would say to just skip it and learn Python.

---

### Post by pmasiar on 2008-04-16
> **mssever said:**
> Better learn Bash first, because once you learn Ruby or Python, you won't want to suffer the pain of learning Bash later. :)

Maybe this could be a reason why to **avoid** bash as much as possible?

---

### Post by LaRoza on 2008-04-16
@OP See what you started? You should have looked at a tutorial for Bash and Python and decided from there....

---

### Post by ghostdog74 on 2008-04-16
> **Wybiral said:**
> BASH isn't meant for programming, it's meant for gluing other applications together with *limited* support for programming constructs and data structures. 
So in Python for example, say when you import a module, aren't you "glueing" together something to work with something else?

---

### Post by Wybiral on 2008-04-16
> **pmasiar said:**
> Maybe this could be a reason why to **avoid** bash as much as possible?

Exactly. The only reason I would ever see a point in learning BASH is if you're in a situation where it's the only language you can use. So far, I've never been in that situation (every Linux machine I've ever been on has had Python or Ruby installed).

---

### Post by Wybiral on 2008-04-16
> **ghostdog74 said:**
> So in Python for example, say when you import a module, aren't you "glueing" together something to work with something else?

If you want to look at it that way, but objects in Python can communicate with more than just pipes and command line arguments. Try to write an OpenGL application or something in BASH. It doesn't work because executing programs doesn't allow you to easily maintain state or anything like you can in a _real programming language_. BASH is designed to be glue between applications, not to design new applications.

---

### Post by ghostdog74 on 2008-04-16
> **Wybiral said:**
> If you want to look at it that way, but objects in Python can communicate with more than just pipes and command line arguments. Try to write an OpenGL application or something in BASH. It doesn't work because executing programs doesn't allow you to easily maintain state or anything like you can in a _real programming language_. BASH is designed to be glue between applications, not to design new applications.
I do agree with you, Bash is not for design and building applications from scratch(its doable), however let's come back to OP. For starting to learn programming, both bash/python (since OP has chosen these 2, although i had said to OP just pick one out of the 5) can be used. Both languages have common programming constructs like loops, if/else controls, arrays, variables etc so i don't really see why one has to be better than the other ( for starting out ). You can already guess what will be my suggestion to OP in the end. Learn both.

---

### Post by nanotube on 2008-04-16
i think it's important to learn at least the basics of bash so as to become familiar with the "unix way". at the very least getting comfortable with pipes, redirects, command substitution, (and to a lesser extent, loops and conditionals) is highly recommended. shell can be quirky and arcane, but it enables you to do some things /extremely/ easily, so it's good to know what it's about.

python is very nice, and an excellent first language to learn (i'm a fan of it myself), but bashing bash (hah!) is not necessary to make that point. :)

as to which one to start with... i'd lean toward getting familiar with the basics of bash first, since it can be done fairly quickly, over the course of a few days to a week, by reading through the [bash scripting guide]("http://tldp.org/LDP/abs/html/") and playing around. then you can move on and take a longer time getting more thoroughly familiar with python. that'd be my personal opinion.

---

### Post by Wybiral on 2008-04-16
I see what you're saying. My opinion is just that since Python will allow you to actually expand your programming beyond simple command-line task automation, it makes more sense for a programmer to start with Python. If automating command-line tasks is all you want to do... Maybe bash is right for you.

---

### Post by Sinyster69 on 2008-04-17
From reading and reseaching, I have decided i will go with Python first and later on Bash..

Thank you everybody on your opinion and help.. I am happy I joined this forum and I am  looking towards learning more from you guys :-D

---

### Post by mssever on 2008-04-17
> **pmasiar said:**
> Maybe this could be a reason why to **avoid** bash as much as possible?

Perhaps. But it is true that Bash (sometimes in its sh incarnation) is still widely used as glue. Many OS-type applications make considerable use of bash scripts (init scripts, anyone?). The .deb packaging format specifies bash for certain parts of the packaging. Plus, working with bash will teach you about the various tools available. That can be handy if you're programming in language X and you don't have a library for some particular task handy. Just call the same command that you'd call from bash (assuming that cross-platform compatibility isn't an issue).  Of course, the value of bash depends on the type of programming you do.

Please don't construe this as bash advocacy. It's not. Before I learned Ruby, I did a lot of Bash programming. Now, I rarely write in bash, because Ruby and Python are both so much easier to deal with. But I still use knowledge I gained from writing bash scripts. All in all, I think there's a lot more value in knowing Python or Ruby than in Bash.

---

### Post by ruy_lopez on 2008-04-17
> **LaRoza said:**
> @OP See what you started? You should have looked at a tutorial for Bash and Python and decided from there....

That's right. Blame the OP.

OP: There are plenty of "experts" in here who will help you choose a language. If only there was an expert who could tell you which of them knows what they are talking about.

---

### Post by WW on 2008-04-17
*BASH* as a *recommended* first programming language?  I don't think so. The syntax of if-then conditionals alone  is too much ugliness to inflict on any aspiring beginner.

---

### Post by slavik on 2008-04-17
> **WW said:**
> *BASH* as a *recommended* first programming language?  I don't think so. The syntax of if-then conditionals alone  is too much ugliness to inflict on any aspiring beginner.
did you just claim syntax as a negative point?

---

### Post by WW on 2008-04-17
Darn it.  It's late, and weakened by tiredness :shock:,  I forgot that I avoid threads that go where this one has gone #-o .  So, nevermind, it's all been said (and I agree with all of it :) ).

Sinyster69: good choice, have fun with Python.

---

### Post by Wybiral on 2008-04-17
> **ruy_lopez said:**
> OP: There are plenty of "experts" in here who will help you choose a language. If only there was an expert who could tell you which of them knows what they are talking about.

Who made you the expert on questioning other people's expertise? :p

---

### Post by ruy_lopez on 2008-04-17
> **Wybiral said:**
> Who made you the expert on questioning other people's expertise? :p

It's a privilege I elected for myself. As did you when you questioned my questioning of other people's expertise. (insert fish face)

I certainly wasn't questioning *your* infallible expertise. Personally, I don't know enough about every language to give beginners a lecture on which one to choose. In that sense, you could say I'm an expert on my own lack of expertise.

---

### Post by Wybiral on 2008-04-17
> **ruy_lopez said:**
> It's a privilege I elected for myself. As did you when you questioned my questioning of other people's expertise. (insert fish face)

I certainly wasn't questioning *your* infallible expertise. Personally, I don't know enough about every language to give beginners a lecture on which one to choose. In that sense, you could say I'm an expert on my own lack of expertise.

:) (I was just joking around btw, light-hearted fun)

---

### Post by ruy_lopez on 2008-04-17
> **Wybiral said:**
> :) (I was just joking around btw, light-hearted fun)

I always wondered about the true meaning of those smiling faces. Thanks for clarifying.

---

### Post by LaRoza on 2008-04-17
> **ruy_lopez said:**
> That's right. Blame the OP.

OP: There are plenty of "experts" in here who will help you choose a language. If only there was an expert who could tell you which of them knows what they are talking about.
It was a joke...

If anyone wants a real expert opinion on the matter, see my homepage. There is a very smart and impartial language quiz that tells you what you need to learn.

[http://laroza.freehostia.com/home/apps/programming/index.php](http://laroza.freehostia.com/home/apps/programming/index.php)

---

### Post by ruy_lopez on 2008-04-17
> **LaRoza said:**
> It was a joke...

And it's certainly got a lot funnier since you explained the humour. What is this? Explain-your-jokes-day or something?

ruy_lopez is spanish for "please explain everything to me". That's a joke, an inverse joke, commonly known as "irony". I'm sure you will laugh your head off when you reach the explanation.

I was serious about the "experts" part, but it wasn't an insult meant towards anyone in particular. I just figured the OP might benefit from thinking for him/herself. I didn't want to say "think for youself" because that's hypocritical "advice".

---

### Post by Wybiral on 2008-04-17
lol

I've learned to be careful around here. Sometimes people have a tendency of taking things too seriously (that was not a joke ... but _that_ was)

---

