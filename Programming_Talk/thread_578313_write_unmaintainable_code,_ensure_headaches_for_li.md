---
title: "write unmaintainable code, ensure headaches for life"
date: 2007-10-17
forum: Programming Talk
---

### Post by sapo on 2007-10-17
I just posted something on my blog, that I think it's interesting for programmers, I will paste it here so you don't have to visit my blog to read it, but if you want my blog is: [http://yacoding.blogspot.com](http://yacoding.blogspot.com)


Please, if you have the time to read it, please comment :)


This post is inspired by How To Write Unmaintainable Code Ensure a job for life ;-) by Roedy Green.

But rater I'd call it: How To Write Unmaintainable Code ensure headaches for life.

Well, I started programming when I was 15 years old, and since then I've learned a lot, and almost all I learned since then (except the very basics, which I learned at school) I learned by myself, I read a lot and I really enjoy programming, which helps, because as I code for fun I learn and have fun at same time.

And I lost almost all of my oldest codes. I wrote I game like space invaders using clipper once, and for what I can remember it's the code I regret most to have lost.

But these kind of code you write for fun, you don't have to maintain, even if it is a piece of ****, who cares? it's just dead code.

But the real problem starts when other people starting using your code, because you can't just trash it, and that's a big problem.

And 4 or 5 years ago, I dropped clipper and start with php, even php being a modern language it still have many problems, and one of these problems is that it is easy too learn, and it attracts a lot of newbies, like me, who you should have guessed got attracted by it's simplicity (please forgive me for using this word to describe php) and easy learning.

And what happens when a newbie join forces with other newbies to learn a language? Nothing good, I'm sure.

As clipper was a procedural language and I didn't have a clue what OOP was at that time, I started writing spaghetti code at speed of light, and that was not a good idea.

1 or 2 years after that I found myself a full time job as a php developer, or maybe you should call it, php code typer.

And man, I'm ******* proud of it, because even with spaghetti code I was able to write a web based software by myself which works flawlesslly and also was a passport to my new job.

But when you write unmaintainable code, you can be sure that it will be back to hunt you, and it started hunting me as soon as I quit that job, and till now (8 months later) I am the only one maintaining it, not that it is impossible to maintain, but it is so freaking complex, that every new php programmer (aka newbie) that looks at it says, holy ****!

Why do I think this code is unmaintainable? Well, I spent more that one hour reading my own code trying to understand what that **** some piece of code did, and after understanding it I asked myself, why the **** I wrote that?

And as the spaghetti code quantity grows, it becomes I snow ball, if you try to refactor it, you will spend a lot of time with the risk of breaking what is working, if you just keeps writing code crazily you will end up in a dead end some day, and if you try to write the new code in a better way, well it will help a little, but your software will be like when you make a collage with letters cut off from a newspaper, b-e-a-u-t-i-f-u-l.

Anyway, don't blame for skipping the topic, this is a blog damnit! So I got carried away. Sorry :)

The purpose of this post was to give a simple advice, before writing code, please take your time, hold your breath, and read something about coding quality, design patterns, or general programming books, and be sure to at least read the Pragmatic Programmer.

I'm sure it will open your eyes and make you write better code, because I knew (and Know) a lot of potencial programmers that get stuck in a company which doesn't care about code quality, and thinks that code quantity is equals code quality, and it's a shame that these companies sometimes make these good programmers rot into oblivion.

I left my last company and moved to another one, starting with a lower salary, the new company is in another city so I had to move and I spend money with rent and households stuff, but man, it was the best thing I did. I've learned a lot in this past 8 months, I can use my full potential here to learn new stuff and write better software, I don't have to be stuck 8 hours a day writing spaghetti code, because I can spend half hour researching and write a 10 line code in some minutes that will do the same work, and better.

If advice was good, we would sell it, not give, but here is a little piece of advice.

If you spend more than some minutes to understand some code (specially if it's your code), it's got to have something wrong, so think carefully about it, can it be better? Will you understand it if you read it again after 2 months? Can you really copy and paste code without any punishment? Will you be able to reuse the code?

Well, if you ask this kind of questions to yourself, I can asure you that you will not regret it in the future, I wonder what my code would be like if I had asked these questions to my self in the first place... I'm sure that I wouldn't spend 1 hour to understand it and also I wouldn't be here writing this stupid post.

Anyway, if you read everything till here, thank you, but if you just read this last line, go to hell, because this is the first sin of "spaghetti code writers", they don't like reading.

---

### Post by j_g on 2007-10-17
The secret to being able to return to code you wrote a long time ago, and pick it up easily is...

comments.

Lots and lots of comments. Each function should have a comment header that details what the function does, what are the arguments it is passed, and what it returns. Any other effects of the functions (such as updating global variables, etc) should be documented in the header.

I'm an extremely profuse commenter. I actually comment every single line of code I write. Before I write the line, I write the comment. Because of this, I've never had a situation where I've gone back to old code I wrote and said "What is this doing, and why did I do it this way?".

---

### Post by sapo on 2007-10-17
I don't agree, actually we don't comment anything at all in my current work and everyone understands.

The secret is to write good and readable code, the point is, you spend more time reading code than writing code period.

So it's better to name your methods: DoCalculationOfTimeSpentReadingCode then just calc (ok, thats a stupid example), but if you read the pragmatic programmer or any other book in this topic you will see that good code doesn't requires comments at all, because good code is self explaining.

---

### Post by mjwood0 on 2007-10-17
I think one thing that's often overlooked, especially for a language like C is the use of style and standards.  For example, I do the following:

```

/* Constants are uppercase */
#define ARRAY_SIZE 10u

/* Types end in _TYPE and enumerated values end in _E */
typedef BOOLEAN_T
{
  FALSE_E       = 0u,
  TRUE_E        = 1u
} BOOLEAN_TYPE

/* Pointers begin with p */
unsigned int pInteger;

```

I'm constantly confused by types that have no mention that they are a type or pointers that aren't clearly pointers.  

Perhaps I'm simple minded, but it does make things much more maintainable.

---

### Post by sapo on 2007-10-17
That's the idea, it doesn't matter what standards you use, the sole fact that you do have a standard it's enough.

Imagine if you have a team of 5 developers who have they own standard, when you get their code, you will most likelly spend a lot of time figuring out what everything means, but if you all use the same standard, it is easier to read each others code.

---

### Post by Wybiral on 2007-10-17
> **j_g said:**
> ... I actually comment every single line of code I write. Before I write the line, I write the comment. ...

Wow, that's hardcore. Every line? That sounds like a bit too much for me, but...

> **sapo said:**
> I don't agree, actually we don't comment anything at all in my current work and everyone understands. ...

That doesn't sound like enough (or good practice at all).

I comment when the code isn't obvious. If it isn't a common algorithm or I had to implement some "hacky" workaround for some reason. I also usually comment to say "Hey, this could be better" just to let the future me/others know that the implementation isn't meant to be final and that it should be improved whenever someone has the time.

---

### Post by sapo on 2007-10-17
Ok, anything was exagerated, but we have some comment's like:

//Hacked to solve bug XYZ

Other day I read the following code:

Try
....
...
..
Except
...

And I said, wtf, catching ALL the exceptions is so wrong, and I just removed that code, the next day the code's author came to my desk and explained the problem, it was a hack because the piece of code inside the Try group sometimes raised a generic exception but it had to be catched anyway... so I said him to comment that and put that it was necessary, otherwise we would remove it again.

:)

But usually commenting what code does means bad code.

---

### Post by Tomosaur on 2007-10-17
I agree with j_g in a way - I can't count the number of times I've looked at someone elses code and drawn a blank - especially when people try to be clever and show off (to who, exactly?). Comedy variable names, non-descriptive method / class names, manipulating returned values for every time the proc / function is called. It just annoys me and slows the whole thing down. There's nothing worse than working on a project and everyone having their own different style (or, as is often the case, no style at all). It's not rare for me to find code experiments commented out, but left in the current trunk. If you don't know how to do something, you shouldn't be working on it. Find something you know how to do and do that.

I had to do a group university project last year - it was a database backend which mobile phones could connect to via WAP and manipulate (so it involved a lot of PHP and WML). The first 2 weeks or so of implementation, people would send their code to me, and the whole thing would just fall apart - it was impossible to stitch the different bits together. In the end I just had to tell the rest of the group not to do any more coding, since it was obvious I was the only one who knew a) what we needed to do, and b) how to do it. Thankfully they just got on with documentation and such - I had all of the code done within a week, no fiddly bits left dangling around, all nicely commented etc, and we passed with 100%. If people working on a project can't code in a uniform way - documenting what they do properly, then the project will just be a mess. Comments are absolutely important - sometimes you might need to make a horrible little hack - but if that hack is obscure and abstract, then nobody will know what it is unless you comment it. Keep everything in context, keep it tidy and of a uniform style, and just get on with it.

---

### Post by sapo on 2007-10-17
And talking about this php project I've done, I have a lot of comments, but they are like this:

i++; // increments i

I laugh my *** off each time I read the comments that I added to the code :D

---

### Post by samjh on 2007-10-17
General rule of thumb for me is:

1. Brief description at the beginning of each source file.
```
/* Source file for audio capture engine. */
```

2. Brief description at the beginning of each class, function, and procedure.
```
/* init_usb_emu initialises data needed for USB port emulation driver.  Tested for versions up to 1.2 only. */
```

3. Brief description at the beginning of each large code block (roughly more than 20 lines).
```
/* Infinite loop, polls input signal from PIN03 at 0x04B, process it and pass to PIN09 at 0x128 until interrupt occurs in INTR. */
```

4. Brief description at the beginning or to the side of any code that is beyond the complexity of an introductory textbook example for the programming language.
```
// ADC resolution only 8 bit, but reader requires 32 bit resolution.
// Buffer four inputs into b_inbuff[], and interpolate averages.
// Fill b_outbuff[] with interpolated values before flushing.
```

5. Brief description for any hacks or otherwise unorthodox code.
```
// Hack!  Needs DUP_FLAG set to false, or transmit doesn't work.  Official documentation is wrong.
```

---

### Post by pmasiar on 2007-10-17
... and brief description if some other approach was tried and did not worked (and was deleted), so next guy will not try to "optimize" it.

see also [Abject-Oriented Programming](http://typicalprogrammer.com/programming/abject-oriented/)

Commenting every line is kinda excessive for me (at least in Python): I better spent time thinking about better (more descriptive, but not to long) variable and function names.

---

