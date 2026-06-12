---
title: "The next step in learning to program"
date: 2007-10-13
forum: Programming Talk
---

### Post by Mishok on 2007-10-13
Hello Ubuntu community :)
I have a question for the coders/programmers/developers. I am a person who has had a bit of a programing background. Nothing too extensive, but i do know the basic programming concepts (had 2 years of java in high school). Currently I  have been reading up on C and pretty much just learning the new syntax. Eventually I would like to be able to contribute to an open source project maybe not of ubuntu's magnitude but something that people will still use. So the question is: What would you recommend as the next step for me? I already know the basics, but i feel that i am running out of ideas for the things i can do with my knowledge. Are there any small projects out there which i can look at and maybe digest their code to better my understanding of how programs are designed? Any particular forums/communities to hang around in? There is only so much you can learn from a manual. Any help or suggestions from you will be greatly appreciated.

---

### Post by Adnarim on 2007-10-13
You need several years just to become an average C coder ;) The best is to start writing you're own programs for educational purpose. So imo learning by doing is always the best way.

The best C-community: [http://cboard.cprogramming.com/](http://cboard.cprogramming.com/)

---

### Post by leg on 2007-10-13
> **Adnarim said:**
> You need several years just to become an average C coder ;) The best is to start writing you're own programs for educational purpose. So imo learning by doing is always the best way.

The best C-community: [http://cboard.cprogramming.com/](http://cboard.cprogramming.com/)Absolutely but also find a project you are interested in and offer to test for them. That would be a good start and help you learn how the projects are organised.

---

### Post by mjwood0 on 2007-10-13
The absolute best way to learn to program in any language is to constantly use it (just like learning a foreign language) and to debug your code.  Pick a project for yourself (perhaps not something even public) and challenge yourself to complete it.  Try to break it.  Learn how to use a debugger and stack trace and you'll be on your way.

Being fluent in a language doesn't make a person a good programmer.  Programming involves not only being fluent, but understanding the broader impacts of your code (architecture, memory management, etc.)

---

### Post by scruff on 2007-10-14
I learned solely from the net and am a pretty capable programmer at this point. I also feel like I am sometimes starved for ideas, but luckily I get paid now for solving problems using a variety of languages these days.

Based on that, I suggest finding something useful to yourself on sourceforge.net t ocontribute to. Something that you would definitely use on a daily basis. You could learn a lot by fixing bugs on the project or getting involved full swing as a developer. That is definitely the best way to learn - to be forced into solving problems you didn't know existed :)

---

### Post by Mishok on 2007-10-14
thanks for the replies guys. 
You pretty much confirmed what i was thinking. The best way to learn programming is by doing it. The problem with me is that i find it hard to keep coming up with projects to challenge myself, but i guess that is just something i will have to overcome.

---

### Post by NovaAesa on 2007-10-14
> **Mishok said:**
> The problem with me is that i find it hard to keep coming up with projects to challenge myself, but i guess that is just something i will have to overcome.

If you're looking for an idea for a project, here's an idea that I did a project based on about a year ago. At the time, I found it very challenging but the final program was very useful for me as well. So here's the idea: create an application where you can input an unsolved sudoku puzzle. The program then has to output the answer to the puzzle. When I did the proejct (I wrote it in Visual Basic btw, this was before I discovered linux), it only took about a month to finish. It was well worth it at the end!

Yeah, so if you're looking for an idea you're welcome to borrow mine (although I'm sure its not exactly an original idea).

---

### Post by slavik on 2007-10-14
seeing as how you are confortable with Java, when you become comfortable with C, I suggest learning a "scripting" language (Perl, Python, Ruby)

as far as an idea for a project, find an algorithm or a problem (an itch) then write code to implement it or fix it :)

---

### Post by ankursethi on 2007-10-14
I've found getting a data structures book can help a lot. I find myself skipping the entire chapter and looking at the exercises to find interesting problems. Some can even give you ideas for bigger projects.

Also try polishing your basics with programming contest problems. They are designed to be small and doable in very little time, but they can turn very complicated when you actually start coding them if you aren't completely sure of what you're doing.

For code, look at small UNIX stuff such as textutils and coreutils at the Free Software Directory ([http://directory.fsf.org](http://directory.fsf.org)).

---

### Post by gnuman on 2007-10-14
> **Mishok said:**
> thanks for the replies guys. 
You pretty much confirmed what i was thinking. The best way to learn programming is by doing it. The problem with me is that i find it hard to keep coming up with projects to challenge myself, but i guess that is just something i will have to overcome.

The [COLOR="Blue"][[COLOR="Blue"]Python Challenge[/COLOR] ]("http://www.pythonchallenge.com/")[/COLOR]should keep you busy when you run out of other tasks....  

Most of the challenges can be solved in most comp languages, not just Python.  In fact, that's part of the fun of the site is to read how the same challenge was solved in various ways in various languages.

---

### Post by j_g on 2007-10-14
Here's a suggestion that you don't hear very often.

I think that one of the best ways to gain a very good understanding of something is to study it to the point that you can write a tutorial about it. So find an existing C project that is similiar to what you'd like to work on but doesn't have a lot of documentation, study the code to learn a lot more about C coding, and then utilize that time/effort to create tutorials/documentation that others can use. One of the really big drawbacks to coding for Linux is that so much of what's out there is not documented in a form that is useful to people who don't have time to peruse all the sources to figure out how to use the code. For example, just the other day, I went to the web page for directfb, clicked on the link for programming, and discovered that the API docs consist of a list of the names of functions in the directfb library, often without any description of what the functions do. There are a couple tutorials for how to do some specific more-esoteric things, but no overview of how the API works nor how the functions relate to each other. Here's an instance of where the documentation needs to be fleshed out a great deal more. Lots of projects need better documentation, so as long as you're learning, use your time/effort to aid in documentation. If you can write a good tutorial about something, then you know that thing.

---

### Post by CptPicard on 2007-10-14
Syntax is always the easy part. 

I would recommend taking it to the next level, and actually start learning about algorithms in a more abstract sense. You will be a much more competent problem-solver when you have a toolkit inside your head you can start to apply instead of trying to solve everything from scratch -- trust me, most problems in this world are already either solved or proven to be "very hard". The typical trap is that a lot of the trivially *easy-looking* problems are actually extremely tough, and variants of them are embedded everywhere -- they're just superficially disguised as something else!

The architecture best practices you learn best by reading other people's code. Don't reinvent the wheel the hard way.

I am admittedly a very lazy coder and therefore my "practical skills" are always in need of improvement... I always lose interest in a project once I "figure it out" -- and that generally mostly happens all in the head. The rest is typing and I just never bother. :)

---

### Post by Wybiral on 2007-10-14
> **j_g said:**
> Here's a suggestion that you don't hear very often.

I think that one of the best ways to gain a very good understanding of something is to study it to the point that you can write a tutorial about it.

I actually agree with this. Writing tutorials is a great way to test yourself. It helps you find areas that you didn't even know you were unsure about. You don't have to make them public even, just writing them for yourself to test your knowledge of the subject is a great way to get all the details down.

> **j_g said:**
> One of the really big drawbacks to coding for Linux is that so much of what's out there is not documented in a form that is useful to people who don't have time to peruse all the sources to figure out how to use the code.

lol, you couldn't help could you? I like how you insinuate that other platforms don't have this problem.

---

### Post by pmasiar on 2007-10-14
Wiki in my sig has couple ideas for simple text-based games. WIki has links for ython beginners (because I believe Python is better first-time learners), but feel free to ignore it and just solve the tasks.

You need to learn data structures, and design principles. Usual approach is just to solve homework problems (I have links for that too). Excellent collection of problems to be solved is boog "Etudes for programmers", sadly not printed since 79. BTW is here someone who read it like me? Another set of problems is [http://projecteuler.net/](http://projecteuler.net/) with sets of problems to solve.

And yes, get involved in some project. Be prepared that it could take you 10 years to become really competent programmer, especially in C.

---

### Post by pmasiar on 2007-10-14
Mishok, one thing which is different in open source community is that software is created in the open, and results are somewhat different from traditional "closed source" and some forum members are known to miss this important difference and whine about it.
> **j_g said:**
> One of the really big drawbacks to coding for Linux is that so much of what's out there is not documented in a form that is useful to people who don't have time to peruse all the sources to figure out how to use the code. 

Because it is created mostly by volunteers, people do what is interesting for **them** to do in their free time. Most hackers prefer to write code and fixing bugs before improving documentation, so some docs might be "good enough" for hackers (who has the code to look if any questions) but not up to standard set by docs created by well paid technical writing professionals. Of course if you think you can improve docs, you can, and just submit improved docs to original project. Docs are open source too :-)

Don't mind j_g, he is known whiner about this issue. We had this discussion so many times it is not even funny anymore.

---

### Post by slavik on 2007-10-14
try to find a book called "etudes for programmers"

---

