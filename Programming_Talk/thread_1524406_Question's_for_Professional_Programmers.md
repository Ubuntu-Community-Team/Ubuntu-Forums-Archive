---
title: "Question's for Professional Programmers"
date: 2010-07-05
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-07-05
I have just finished the first year of my engineering degree and am moving on to Software Engineering in September. I have really only taken an introductory course to programming and as such my knowledge is relativly limited.

When I graduate in four years I'm hoping that I can get a job basically anywhere I apply... (Not hoping for too much eh.. :P) --> Specifically there is the oppourtunity of working for bioware if I stay in my home city, and I hope to eventually work there. (Gaming company)

Now here comes the questions.

_**What should I start doing now to make my dreams a possibility?**_
I already attempt to write programs in my free time, but the fact is that they are kind of basic and really lackluster. The types of things that any begininer programmer or coder could do. 

So are there any books I could start reading this summer that will give me an edge and help me further my learning (List as many as possible // instructional books would be best) 

_**What courses should I pay specific attention to?**_
This is a question specifically  for people who went through the software engineering program. As of right now I am assuming that Linear Algebra will be of importance, and calculus slightly less. And are there any courses that you would recomend that I take outside of the regular cirriculum? 

_**Should I be aiming for a 4.0?**_
I mean it makes sense to aim as high as possible if I want a job, but what im asking is how much emphasis do employers give to a GPA when they are looking at hireing a new programmer?

_**Is there any advice you could give me that I haven't asked for?**_

Its like 4:30 am and I'm kinda tired so the 30 or so questions I was thinking of asking have seemed to slip my mind. Thats probably also why when I look at this tomorrow I'm gonna see about 5-10 sentances that make exactly 0 sense and will have to edit this post. But until then I was hoping that you could give me any advice that you would have liked to have gotten when you decided to pick a career in software engineering.

--------------------------
Pretty sure this is probably in the wrong section so If an admin could move it that would be great :P and sorry for posting here.

Heh come to think of is this is probablly the wrong forum, but its the only one I have in my bookmarks so you get first crack at these questions :P

---

### Post by ja660k on 2010-07-05
I'm not a professional, but im kind of in the same situation...
but im doing computer science, and im almost finished.

HD's are awesome. sure, aim for that 4.0
in the later semesters, maybe your 3rd or 4th year. study part time... and apply to tutor 1 & 2 year subjects... it looks great on your resume, and not to mention the money is really good (at my institution $100p/h for a tutorial, $33 for a lab session)

the thing i love about linux is open source. Work on open source projects.
because university assignments, no matter how big, don't really count as experience. (unless they are for an actual client)

then your potential employer:
see your degree, GPA
see your past employment
see some projects you have worked on.

and your all smiles and he is overwhelmed by your awesome.
compared to the guy who worked at the supermarket and has his degree.

thats if you want a job job after you graduate.
I would love to stay at university and do research and be employed by the university to teach students  :)

but thats just me.


and, the courses... really depend on what **you want** to do after you graduate
a sound understanding of searching and sorting algorithms was drilled into me for 3 semesters
plus knowledge in Java and C, other languages were there but were not core subjects. 

and as for books/tutorials...
[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)
is a sweet list for alot of languages :)

---

### Post by Some Penguin on 2010-07-05
> **YourMomsASmurph said:**
> 
Now here comes the questions.

_**What should I start doing now to make my dreams a possibility?**_
I already attempt to write programs in my free time, but the fact is that they are kind of basic and really lackluster. The types of things that any begininer programmer or coder could do.

So are there any books I could start reading this summer that will give me an edge and help me further my learning (List as many as possible // instructional books would be best) 

Read up on symbolic logic and recreational mathematics, such as those by Martin Gardner.  

I'm not joking.  Awareness of mere syntax is all well and good, but is not very interesting if you can't solve problems because you haven't developed good reasoning and analytical skills.

> 
_**What courses should I pay specific attention to?**_
This is a question specifically  for people who went through the software engineering program. As of right now I am assuming that Linear Algebra will be of importance, and calculus slightly less. And are there any courses that you would recomend that I take outside of the regular cirriculum? 

Logic.  Graph theory.  Data structures.  Algorithms.  Computer architecture.


> 
_**Should I be aiming for a 4.0?**_
I mean it makes sense to aim as high as possible if I want a job, but what im asking is how much emphasis do employers give to a GPA when they are looking at hireing a new programmer?

I don't really care that much about a candidate's GPA.  I do care whether or not they combine motivation, initiative, technical skills, and analytical and design skills.

I don't care whether somebody has memorized how long a Sun JVM will preserve an object that is only weakly referenced before garbage collecting it... but it IS useful to have a person who upon finding out that a system is complaining about memory use can examine a heap dump, notice that there are a lot of only weakly referenced objects running around, and realize that tuning the garbage collector is suddenly interesting (not necessarily for that person, since there may be a person who's much more familiar with how to do so, but an issue that should be raised an addressed by somebody).

I don't care about whether somebody's memorized the implementation details of splay trees; it's more interesting to know about the existence and reasonable use cases for balanced binary trees, because in practical terms, these are wheels which don't need frequent reinvention.  However, it's a problem if somebody doesn't have the skills to be able to search and understand literature, or if he's stumped by reasonably simple problems like "given a list of 1,999,999,999 distinct integers in [1, 2B], identify the missing integer from that range", because much interesting work involves solving problems, not just taking solutions that somebody else wrote and turning them into code.

And ideally, a candidate engineer would have some common sense about what to do when encountering a possible issue .  For instance, if it's a possibly major design issue in a highly intricate system that somebody else developed, filing a bug report with that person may be optimal; but if it's a minor, localized issue that is blocking the candidate from working on his own systems, simply fixing it immediately (with a relevant commit message explaining why, of course) can easily make more sense.

As for what else to do, internships and anything else that gets you experience in a team environment w/ non-toy systems is a good idea, particularly in a market where you're competing with numerous others who already have substantial experience.

---

### Post by MattThLinuxNewb on 2010-07-06
Once you've got the hang of an OOP language, some essential books:
Design Patterns by GoF
Effective C++ by Scott Meyer
Refactoring by Martin Fowler and Kent Beck
Code Complete is apparently another good one, I haven't read it yet so I can't comment.
They say that every software engineer should read The Mythical Man-Month, though personally I found a lot of it outdated and not relevant. The key message could probably be summed up as "communication in software projects doesn't scale well".
The Art of Computer Programming by Donald Knuth if you're brave.

If you've only worked with statically typed languages like C and Java, learn a dynamically typed language like Python - you're in for a pleasant surprise. [Dive Into Python](http://diveintopython.org/toc/index.html) is great if you're already comfortable with another language.

Master one or more version control systems e.g. svn, bzr. You will definitely be using them in the job so it's best to learn now and it will look good on your C.V. A good way to get practice is to contribute to an open source project you like the look of, like ja660k said. Or start a project of your own on sourceforge, etc.

Get some experience working on a project in a team before you graduate. Make a note of things you learn, communication challenges, etc, that you can talk about in your job interview when they ask you about it.

Work on some projects of your own to showcase your skills. Employers will want to see your source code. A small working game would be ideal if you can finish it as it can demonstrate your skills in a lot of areas, e.g. GUI and network programming.

That's all I can think of for now, good luck.

---

### Post by KdotJ on 2010-07-06
I too feel in a similar situation, and as for projects in my free time, I have difficulty thinking up project ideas. Especially ones where I can implements and practise everything I have learnt so far

---

### Post by descendency on 2010-07-06
Just a piece of advise for you when you apply for a job. Know the company you are applying. If you are applying to a company like Microsoft, they are not going to care much about your experience working on Open Source Projects as they do not (typically) contribute to OSS development. Similarly, don't go to Red-Hat and trash Linux based operating systems. 

This might sound stupid, but it does help to know something about what the company does and doesn't do. For example, as I experienced last spring, you don't work on a health care application without knowing quite a bit of the legal aspect of health care software requirements. It will help if you come in with some knowledge of the company (they usually have bullet points on their website) and can talk to how you can progress their company's goals.

So, if you are looking for a job in a specific game design company, you should dig around their corporate website and look for key terms you recognize that you can incorporate into your vocabulary so that they know you are a good fit for them and so you know that they are a good fit for you. 

If you don't like working in Open Source, it will be a very negative experience working for a company who's primary work is done in Open Source. 

If they have literature online - including videos like(tech demos for game engines) - then you could peruse it for ideas. 

I wish I could be more helpful, but I'm a software engineering student in my final year (In the US).

---

### Post by Some Penguin on 2010-07-06
> **KdotJ said:**
> I too feel in a similar situation, and as for projects in my free time, I have difficulty thinking up project ideas. Especially ones where I can implements and practise everything I have learnt so far

Consider browsing [http://sourceforge.net]("http://sourceforge.net/") as there are quite a few projects available.  This might also give you practice assessing what projects seem reasonable -- an important skill for a job candidate is to have some basis for deciding whether a potential employer is right for him, and this includes having some idea about whether or not e.g. the intended projects will actually work and how well they're run.  Interviewing is not a one-way street, and a lot of startups in particular simply aren't going to make it...

[http://codeforamerica.org/](http://codeforamerica.org/)  might be of interest to the civic-minded.

Maybe you'll find something hosted by [https://launchpad.net/](https://launchpad.net/) more interesting.

---

### Post by mmix on 2010-07-06
IANAPP, anyways.

[http://www.topcoder.com/](http://www.topcoder.com/)

[http://www.koders.com/](http://www.koders.com/)

[http://www.acm.org/](http://www.acm.org/)

[http://www.ieee.org/](http://www.ieee.org/)

---

### Post by phrostbyte on 2010-07-06
Well it depends on what you want to do. If it is computer graphics, computer vision, or machine learning... Linear Algebra is HUGE HUGE HUGE. Calculus is huge too, it's the basis for Fourier analysis. :) Expect to have a better grasp of mathematics then most people who major in math if you want to get far in this field. Other then game developers (which is both difficult and low paying), most people in this sector of the CS world make very huge salaries and having a Ph.D. is almost a requirement.

On the opposite spectrum, enterprise/LoB/CRUD development requires very little math. Often you will find people without college degrees or sometimes without high school degrees doing this kind of programming. Very API heavy stuff. You can make alright money doing this kind of work, but it can be boring. It is also quite prone to in-sourcing and outsourcing.

The most difficult IMO is to get a job writing open source. These kinds of jobs tend to be extremely competitive and you have to be really good. There is not many of them.

Writing some open source is helpful too, in my experience. Saying you have code in the mainline Linux kernel is a big deal. Even if you end up getting a job writing closed source.

---

### Post by phrostbyte on 2010-07-06
Oh and high GPA never hurts. But getting a 4.0 in Computer Science would look suspicious to me. :P CS is not exactly known for producing a lot of Magna Cum Laudes.

---

### Post by YourMomsASmurph on 2010-07-06
Thanks for all the advice guys I really appreciate it. 
As for working on open source projects goes; I was curious about whether or not I would actually have the skills required to do anything of value in these projects. As of now I only have a first year knowledge of programming so it is extremely limited.
My best guess is that I should start by reading the books suggested by MattThLinuxNewb.
And studying symbolic logic as suggested by some penguin.

I will look at the open source projects available but at this moment I doubt that I could really make any real contribution to any of them.\

Thx again.

---

### Post by phrostbyte on 2010-07-06
> **YourMomsASmurph said:**
> Thanks for all the advice guys I really appreciate it. 
As for working on open source projects goes; I was curious about whether or not I would actually have the skills required to do anything of value in these projects. As of now I only have a first year knowledge of programming so it is extremely limited.
My best guess is that I should start by reading the books suggested by MattThLinuxNewb.
And studying symbolic logic as suggested by some penguin.

I will look at the open source projects available but at this moment I doubt that I could really make any real contribution to any of them.\

Thx again.

I recommend having a ~/code folder where you might just svn/git/etc. pull source code from popular projects, and just spend 15-30 minutes a day just looking on how it is structured, the source tree. This is helpful. 

Don't think of it in terms of making useful contributions. You don't have to make any real contribution to them. Just play with the code, break it, and then try to fix it. Maybe you'll do something useful, who knows. :)

Or if you prefer just think of something you'd like to make and just try to make it. Don't go overboard though, no MMORPGs or anything like that. If you are into gaming, try to make a text based game. I've done this before when I was very young. It is quite entertaining. I've had more fun writing that stupid text based game then I ever had playing anyone else's game. Go to the next step and try to add multiplayer support and you have a MUD, the precursor to MMOs. :)

But I have to warn you, software devel takes a lot of time and practice. It's so easy to get started, anyone with a $300 netbook can code. No barrier of entry like many other fields. But to be good at it, it is difficult. Everyone is still learning. My employeers regularly send devs to training and conferences, at great monetary cost, even if someone have been doing what they do for 20+ years. There is ALWAYS something new to learn. :o

---

