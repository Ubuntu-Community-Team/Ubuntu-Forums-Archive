---
title: "Programming"
date: 2007-06-20
forum: Programming Talk
---

### Post by limby on 2007-06-20
Hi im a hobbyist programmer mainly using delphi though i want to move on to c++/c# 
I live in the UK

I want to take this seriously, So im thinking of taking a computeach or similar course in C++
Will this get me a job when i pass.. 

I Would be greatful for any support on this subject many thanks..Limby

---

### Post by Modred on 2007-06-20
I personally like Deitel's *How to Program: C++* for an introductory text and reference for C++.  I got a third edition off of eBay for $5.  Current edition is 5th, last I checked, but you could probably do fine with 3rd or later.

As for getting a job after you finish a class or something similar, I really can't say.  If you've done some programming before, you might be a quick study to the new language, but that doesn't guarantee anything.

---

### Post by Golyadkin on 2007-06-20
Deitels books are great yeah, I can vouch for those. 

However, just knowing how to program won't really get you a job. Developing software is more than programming, you also have to learn about design and user interface design and such.My experience is that what companies want is mainly a degree in computer science, and experience on projects. It would be great if you could learn programming by helping out with open source projects. That way, you also gain experience which you can use as a portfolio when you apply for a job, and at the same time help the open source community.

---

### Post by pmasiar on 2007-06-20
It is hard to tell which language to learn - learn the one used by company you want to work for :-)

Seriously, think about companies in area where you want to work, check what they use - check job boards to "feel the market". Think about summer internship in such a company - if you like it there and they like you, it will be easier to overcome your lack of experience.

Because yes, most companies are looking for 1-3 years of experience in a given language at minimum. It takes months to learn libraries, and become comfortable with workarounds around language weaknesses.

If you dare, special advice: get position in IT-recruiting company as recruiter - just for couple months. You will see how IT jobs are filled up, what smart people do to get job, and how recruiters spot red flags. You will have insider view on job hunting for rest of your life. I know, I was lucky to do it myself.

Your programming homeworks have little relevance to real programming challenges you will face on the job.  You will learn *syntax* but it is long way to know how to solve real problems. How to talk to customers to gather requirements, to see difference between what they want and what they need, and how to get there within timeframe and budget.

Helping open-source project is *very* good idea, especially if it is a project which your employer uses. There are even open source accounting and ERP if you are so inclined.

For some reason you excluded java, web app languages like Python and Ruby, and AJAX. Java is old, but rapid web app development is new, and not many people have the skills yet, so it might be easier to get started. There aren't many people with 5 years of experience in Ruby on Rails :-)

---

### Post by ScottLij on 2007-06-20
How would a novice/intermediate programmer get involved in helping out an open source development project?

---

### Post by pmasiar on 2007-06-21
*When the Student is Ready the Teacher will Appear*

If you are willing to work hard to understand a project (so: you are deeply interested in that project, you want to add something *you* will use), developers will be open to help you to learn it. Many projects set aside simple bugs for new developers to "learn the ropes". Just ask. But be prepared to spend substantial time on self-learning: if helping you will take too much time, it is not worth to experts.

So: start with finding a project you care so much that you are willing to spend hours (weeks) to learn in and out. But be prepared - it will take weeks of hard work to advance a level. 

If you are not ready for that, start with programming some game using pygame - you learn how to handle non-trivial projects.

---

### Post by limby on 2007-06-21
Hi, Many thanks to all who have answered my post. There is a lot of useful stuff here to get me going. 
other languages, i know are a must. I was looking into c++/c# because thats where the
jobs seem to be.  Maybe im not looking.. i have some good grounding in problem solving so 
im going to see about the open source projects for now and move from there, 
Many thanks all. 

Just one question - Why is there so many different languages that pretty much do the same thing.
                                I mean, wouldnt it be easyier if just one language was the mainstream,
                                and adapted with the times. 
                               

Limby

---

### Post by Golyadkin on 2007-06-21
Well, for the same reason there are more than one religion, more than one operating system, more than one cellphone operator and more than one political party instead of a communist dictatorship: people want to have  a choice. Some programming languages serve different purposes. There are programming languages for desktop applications, programming languages for web applications, and so on. Also, programming languages evolve with software development practises, like the object oriented paradigm. There are whole generations of programming languages, like currently the 4GL languages.

---

### Post by incubus on 2007-06-21
> **limby said:**
> 
Just one question - Why is there so many different languages that pretty much do the same thing.
                                I mean, wouldnt it be easyier if just one language was the mainstream,
                                and adapted with the times. 
                               

Limby

Limby, very good question.  If you think of programming as solving problems, you'll soon realize that there are many ways of accomplishing the same goals or approximating results.  In other words, different people will come up with different solutions.  And having many languages is, in my opinion, largely a consequence of that.  Sometimes it's so much like that that it becomes almost like a religion.  And the "holy wars" between languages come naturally, of course.

I do believe it's good to get exposed to more than one perspective, but for starting I would pick one and try to learn it very well.  While you do that, I recommend you to read a little bit about the different paradigms and their histories.  Wikipedia has good sections on those topics.

Good luck on your project.

incubus

---

### Post by Golyadkin on 2007-06-21
I agree with incubus (good band btw) in that it is good to learn one language very very well, and then most others will be simple to pick up. For instance, if you know C++, you can pick up Java without too much trouble (just learn the new syntax) and then you can hop over to C# and then Mono and ... and .... :D

---

### Post by pmasiar on 2007-06-21
> **limby said:**
> Why is there so many different languages that pretty much do the same thing.
I mean, wouldnt it be easyier if just one language was the mainstream,and adapted with the times. 

Big part of differences is deliberate incompatibility created by competing companies.

Java was created incompatible with C++ libraries to create a standard "protected" from MSFT influence, independent of windowd API - this (and lavish marketing spending) is part of the success. Then, MSFT created .NET and C# as incompatible (and slightly improved - they hired the C++ guy) java. With API different from both Windows and java of course. :-)

And free software creates it's own world, independent from (and incompatible with) either Java or C# (continuing old POSIX standard). So **real question is not "which language" but "which platform"** - as I said there are 3 major platforms, and its hard to be expert in all.

Many languages were born as product of vision of single extremely smart hacker as solution for what he needed at the time - and grew from there. These are ie Perl, Ruby, Python, PHP, Forth: all originally created by 1 person to solve specific problem. Read history of these languages in wikipedia and you will realize that each of them was the best solution for the particular problem at the time.

If language is good, it will shift from it's niche to neighboring niches and grow, borrowing (stealing) ideas from languages successfull in these other niches. So Python is slowly taking over big part of what Perl was used for (system administration scripts), PHP (web applications) and stealing Ruby's crown jewel - RAD web framework (Ruby on Rails): Python has TurboGears and Django instead.

Long term free platform will win, but for next 10-20-30 years it might be profitable to work on other platforms too. Profitable, but less fun :-)

---

### Post by limby on 2007-06-21
psamiar thanks. Now i see it from that prospective things make more sense. 
like pro-tools on the mac. and sonar on windows pc. 
But these do pretty much the same thing.


Ive heard of most of the other languages but i chose pascal to get me started.

I thought if i had pascal/delphi and java knowledge and then gain my main qualification in
C++/ or C#. or computer science?

 Does anyone know of a simple open source project to break me in gently?
 Is open university any good for computer science?
 Has anyone taken this route and do i need any pre qualifications.

Many thanks Limby..

---

### Post by LaRoza on 2007-06-21
[http://sourceforge.net/index.php](http://sourceforge.net/index.php) has a lot of projects you might want to join.

---

### Post by pmasiar on 2007-06-21
> **limby said:**
>  Does anyone know of a simple open source project to break me in gently?.

If you don't have own ideas to solve, start with simple programming tasks from wiki in my sig - you can solve them in any language. You can ask for help here or in extremely friendly python-mentor mailing list (if you go with Python).

You can build portfolio of solutions, and self-confidence. :-)

---

