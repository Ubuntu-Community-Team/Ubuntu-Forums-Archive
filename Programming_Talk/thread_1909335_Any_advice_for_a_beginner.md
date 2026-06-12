---
title: "Any advice for a beginner?"
date: 2012-01-15
forum: Programming Talk
---

### Post by rectec794613 on 2012-01-15
Hey guys. I've been thinking about learning programming for a while now, and I just started today. I checked out some helpful guides and decided to start with BASIC. I downloaded Just BASIC and spent all day learning it. So far I know variables, strings, functions, and many other codes. There is still much to learn, so I present you with the following questions:

[LIST=1]
[*]Is BASIC a good starting point?
[*]If so, how much of it should I learn before continuing?
[*]What should I do after I learn it? What language should I learn next?
[*]What language(s) should I learn if I want to program software for Linux?
[/LIST]
Thank you.

---

### Post by Bachstelze on 2012-01-15
1. No. Start with Python if you want to be able to quickly have fun doing things, or with Lisp if you want to know your stuff and don't care how long it will take to become productive.

*EDIT: BASIC has the bad sides of Lisp (not used in the real world, will not make you productive in anything) without the good ones (will not give you understanding of anything other than itself).*

4. Depends what kind of things. C++ or maybe C# for big programs, Python for small utilities, C for low-level things (device drivers, etc.).

---

### Post by rectec794613 on 2012-01-15
Hmm. I though BASIC was basically the building blocks for many other languages... Well you gotta start somewhere, right? BASIC is apparently a very easy language, according to this site: [http://gamenacho.com/top-5-easiest-programming-languages/](http://gamenacho.com/top-5-easiest-programming-languages/)
It also lists Python the 5th easiest language. As a matter of fact, I did dabble a little in Python a while back, before I was fully committed. I'll go check out Python and learn some of it tomorrow. The reason I asked for Linux languages is because I'm thinking of working on Ubuntu, specifically with Unity. Unity is written, among others, in Vala. So for now I wish to work my way up.

Is Python easy for a beginner? What exactly *would* you reccomend starting with?

---

### Post by Bachstelze on 2012-01-15
> **rectec794613 said:**
> 
Is Python easy for a beginner? What exactly *would* you reccomend starting with?

Like I said, Python or Lisp depending on your goals and timeframe. Yes, Python is very easy to pick up. Lisp will probably make you a better programmer in the long run, but the learning curve is steeper so it will take you a long while before you can really be productive. Python will get you started more quickly and will definitely not make you a bad programmer if you pay attention and have some common sense.

---

### Post by imagecko on 2012-01-15
If I was in your place, I would have started with Python or C.
You don't have so much use of BASIC.

---

### Post by stchman on 2012-01-15
I started on a Commodore 64 learning BASIC back in the 80s.

I then learned C in the late 90s.

I recommend Java, it is a great language, well documented, and runs on pretty much anything.

---

### Post by trent.josephsen on 2012-01-15
Java is nice for enterprise stuff and real life programs... sometimes.  IMNSHO it's not good for learning.  Showing Java to somebody who can't program yet is like dropping a first-time flight student into the cockpit of an F-22:  sure, it's an awesome plane, but you don't yet have the skills or experience to fully appreciate the options it gives you.

Starting with a **huge** language like Java can get overwhelming fast.  Especially when you start getting into the object oriented stuff, which has to happen pretty early with Java if the student is to make any sense of it, there's a real pitfall in that you're using advanced tools before you know what they're really good for.  [Spaghetti inheritance](http://catb.org/jargon/html/S/spaghetti-inheritance.html) is often the result of inexperienced programmers trying to work with Java.

I always recommend Python, as do most people in this forum.  You do hear a lot of people recommending C or C++; I don't, because those languages have a whole host of traps for new programmers that you likely won't know to avoid until you have some experience.

Anyone who recommends BASIC as a first programming language in this day and age is selling something.

---

### Post by rectec794613 on 2012-01-15
Yeah I do realize BASIC isn't very useful these days, I just wanted to start out small. But yeah, now that I think of it, Python is where I should be. I've noticed a lot of Linux/Ubuntu programs are written in Python. So today I'll start learning it. And hey, at least I have some previous experience, even if it was in BASIC. Java is a fairly common language, but I just don't see myself writing Java apps. Anyway, thanks, guys. :)

---

### Post by rectec794613 on 2012-01-15
That said, what should I use for developing in Python? I see IDLE has some good reviews, but I'm unsure.

---

### Post by trent.josephsen on 2012-01-15
I use vi, but there's nothing wrong with IDLE.

---

### Post by simeon87 on 2012-01-15
Just use a text editor. It'll teach you more about programming than an IDE.

If I had a dollar for every beginner who didn't know whether a problem in the program was caused by the code, the interpreter or the IDE, I'd have a nice amount of cash by now.

---

### Post by rectec794613 on 2012-01-15
Thanks. Right now I'm using the interpreter in a terminal. Off to a rocky start but I'm still determined. When I first started using Python I used gedit, but now I think it'll be easier just using the interpreter directly.

---

### Post by imagecko on 2012-01-16
To learn Python, try out Google's Python Class: [http://code.google.com/edu/languages/google-python-class/index.html](http://code.google.com/edu/languages/google-python-class/index.html)

---

### Post by nvteighen on 2012-01-16
> **rectec794613 said:**
> Thanks. Right now I'm using the interpreter in a terminal. Off to a rocky start but I'm still determined. When I first started using Python I used gedit, but now I think it'll be easier just using the interpreter directly.

That's the best way to learn Python. You'll notice though that you'll need to use a text editor rather soon, but that's part of the learning.

Also, try the ipython interpreter (it's in the repos). It's a standard Python interpreter with some interesting and helpful features to aid typing code in.

---

