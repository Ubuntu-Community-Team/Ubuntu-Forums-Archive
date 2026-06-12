---
title: "Prolog - Worth the Hassle?"
date: 2010-12-03
forum: Programming Talk
---

### Post by Majorix on 2010-12-03
I am a computer science student (1st year). This semester we are having only one computer related lesson, and that's "Computer Science - An Overview".

Since I have been hacking for years now, I always used to get bored in this class. But yesterday was different.

As an introduction to declarative programming languages, they showed us an example of Prolog solving a tough logic puzzle in just a few lines. I had never seen something as stunning as this, and needless to say, I got quickly attracted to Prolog.

However from the looks of it, this language is not used that widely. Is it a dead language? Or is there a hope? Would I just be wasting my time learning a whole new way of programming -- I have only worked with functional and object-oriented languages so far. Or would it get me to a better-paid job?

If I should give it a go, is this book I have called "Prolog Programming for Artificial Intelligence" by Ivan Bratko a good book to start with?

Looking forward to input from people with experience regarding the matter. Thanks!

---

### Post by PaulM1985 on 2010-12-03
My university used prolog in one of the Comp Sci modules.  I think it is mainly for research purposes rather than for actual paid business work.  

I would say it is probably worth learning because if they are showing it to you, you are probably going to have a coursework assignment based on it at some point in the future.

I have never seen a job advertised where applicants were required to know prolog.

Paul

---

### Post by Arndt on 2010-12-03
> **PaulM1985 said:**
> My university used prolog in one of the Comp Sci modules.  I think it is mainly for research purposes rather than for actual paid business work.  

I would say it is probably worth learning because if they are showing it to you, you are probably going to have a coursework assignment based on it at some point in the future.

I have never seen a job advertised where applicants were required to know prolog.

Paul

I can say that people do write serious programs in Prolog, but sometimes it's because everyone involved already knows it and feels comfortable with it. So you may well find it used in companies where there is a critical mass of people who have taken this course or similar ones.

Knowledge of Prolog may be an added bonus when applying for a job if the people there know what it is, but I think it's unlikely to find a job ad mentioning Prolog.

---

### Post by CptPicard on 2010-12-03
> **Majorix said:**
> 
As an introduction to declarative programming languages, they showed us an example of Prolog solving a tough logic puzzle in just a few lines. I had never seen something as stunning as this, and needless to say, I got quickly attracted to Prolog.

I'm very glad to hear this. I've seen you around here for years now and I guess you're familiar with the HLL vs. LLL debates... symbolic programming can be very ... revealing. Not only about programming languages but about problem structure as well. This is what I used to rant about here.

> 
However from the looks of it, this language is not used that widely. Is it a dead language? Or is there a hope? 

It's mostly a research thing. But that's not a bad thing by any means. Knowing what Prolog can do and how to implement one can be useful for not only logic problems but all sorts of other things as well... like, the Arc Lisp actually runs on top of some kind of Prolog AFAIK.

I must admit I always sucked at Prolog although I can appreciate it. Just my weak spot of not being able to formulate things quite as declaratively as I should although I like functional programming... :)


> Would I just be wasting my time learning a whole new way of programming

No, never.

> I have only worked with functional and object-oriented languages so far. Or *would it get me to a better-paid job?*

I recently took up a job with the most interesting open-source consultancy in Helsinki... they hire for talent, not for number of abbreviations/languages/frameworks on the resume. We don't actually use anything like Lisp (or Prolog) on the job, but knowing that everyone is both a very insightful programmer in general, and is capable of picking up new stuff fast, is one of our most important resources. 

And who knows? If you think of Lisp, my own personal favourite as you may have noticed... the lowly Javascript which is getting more and more important by the day, is actually a functional programming language at its core... a lot of the patterns in functional-land are applicable, despite the language's obvious shortcomings. And don't even mention distributed computing and the cloud...

> 
If I should give it a go, is this book I have called "Prolog Programming for Artificial Intelligence" by Ivan Bratko a good book to start with?


I've got it and have been happy with it. It may be a bit difficult for a beginner, but give it a shot certainly.

---

### Post by worksofcraft on 2010-12-03
I wrote several extensive programs in Prolog that were used for a number of years in industrial applications. One involved testing an electronic product in manufacturing. Prolog turned out to be an excellent choice searching all the possible modes of failure with it's inference engine.

Another was as a front end to software version control system and again the inference engine was a great help recursively finding dependencies and getting and putting the right files and labels into the repositories. It was eventually replaced when the vendors of the version control system created something similar, but IMHO the inbuilt intelligence of my Prolog implementation still made it much easier to use.

Personally I find all the procedural C/C++ look-a-like languages getting a bit tedious. It takes a little time to get familiar with formulating your design the Prolog way, but as you mentioned, it often helps you reach remarkably simple logic.

IMO Prolog would be absolutely perfect as a scripting language for the web... if only it were available in web browsers. It also makes an excellent database query language that would be much better than SQL IMO....

However, when you DO get into industry, the choice to use Prolog will ultimately be yours to make ;)

---

### Post by unknownPoster on 2010-12-03
> **worksofcraft said:**
> 

However, when you DO get into industry, the choice to use Prolog will ultimately be yours to make ;)

Or your boss's decision. It's been my experience that whoever signs the paycheck determines what programming language(s) you are allowed to use. :P

---

### Post by worksofcraft on 2010-12-03
> **unknownPoster said:**
> Or your boss's decision. It's been my experience that whoever signs the paycheck determines what programming language(s) you are allowed to use. :P

In my experience the guy who signed the pay check didn't know the difference between Assembler or Prolog and as long as product was delivered ahead of schedule he didn't care either ;)

---

### Post by nvteighen on 2010-12-04
I guess all new knowledge is worth the hassle, even when it turns out to be completely "useless".

If you use Prolog afterwards or not is a matter of circumstance, but if you enjoy learning it and feel attracted to it, do it... I mean, why not?

---

### Post by Majorix on 2010-12-04
Thanks for the insight, people. I think that now I feel much more encouraged to start with Prolog. Even if I don't get a job just because I know Prolog, it might still be a really good free-time activity.

---

