---
title: "Infrastructure migration suggestions"
date: 2017-03-23
forum: Programming Talk
---

### Post by craige2 on 2017-03-23
Hello,

I made a web application for my last year project. When I started the course, years back, I thought Java was only a type of coffee. I have an engineering background :p  Through the years I've been taught Java (up to java swing), and a little bit of html, php, css, javascript.

Earlier this year I thought I have one last opportunity to try something different while I am still under the wings of university, just for the experience, I like to try new things. So for my project, I picked  a subject and a technology that was never taught during my academia experience. So I did not choose html, PHP or JEE technologies. (I think you know where it goes.... give me a second chance please!).

I started to work on it at the beginning of the year. I made a quickly research and as an inexperienced user my research was poor. I got the most results to be either Java technologies or Microsoft technologies (I am not implying that these are poor technologies). Keep in mind that I am still nowhere close to be assumed as a beginner programmer. So my research was poor. If someone is experienced in a subject, can research it better, so my research was crap :p

As I wanted to try something new I thought to give a try with Microsoft technologies. 

Now that I am done with my project, I thought to give another try researching about it and see what alternatives exists. So I found other than MS and JEE, there is also Electron, CoffeeScript, Backbone, Ruby etc. So many options about every aspect of web application... so hard to pick a combination if you do not have the experience, knowledge...


So my question is simple.


**You have a web application that:**
- Creates questionnaires and polls
- Has a chat service (signalR)
- Sends results via email
- Includes articles that are updated through cms.


**Its current infrastructure is:**
- Content Management System: Umbraco (only business logic implementation, front end through Visual Studio, update content-> articles, register users to questionnaires and polls)
- Framework: APS.NET C#
- Razor
- MSSQL Express 
- IDE Visual Studio
- Windows server 12R2
- IIS


**The question is:**
- Migrate the infrastructure but provide a complete solution with technologies that you might think would be an ideal combination. Do not consider programming experience or skill requirement. Include a complete infrastructure considering compatibility, database, IDE, framework. I would love to hear the reason behind your opinion. Please do not mix paid with free suggestions, I would love to hear a complete solution in either one.


You do not need to have a working experience on the subject, your suggestion is valuable as much. I am just curious about your opinion.

Apologies for the long post. I hope I didn't waste your time.

Thank you,
craige2

---

### Post by TheFu on 2017-03-24
Linux (the OS) is an IDE. You don't need some bloated program called an IDE. I find IDEs restrictive.  Google "linux as ide" for more details.

Nobody deploys using the tools that you've used for that last project. Sounds pretty trivial. As for different languages there are thousands: [http://rosettacode.org/](http://rosettacode.org/) - it will blow your mind.

Popular choices are:
* php / mariadb / Linux
* perl / postgres / Linux
* Python / mariadb / Linux
* Ruby / postgres / Linux

There are lots of web-app frameworks.  Rails for Ruby, Dancer or Mojolicious or Catalysat for Perl. Python has a few too.  I don't touch php.

The back end DB can usually be swapped out easily thanks to ORM - object relational models.  All the modern languages have these. Each is at a different level of maturity and performance.  In Perl, DBIx is the method and it has all sorts of protections that the other languages do not while still being extremely fast and flexible. No need to learn SQL.

The issue with using any of these tools or languages is that noobs seldom handle the security aspects much, if at all.  Review the **OWASP top 10** for each language and follow their guidelines to avoid stupid security mistakes.

And don't forget that Linux is the IDE.

BTW, I was trained as an engineer too, but switched to sw development almost 30 yrs ago.  If I were starting out today, I'd learn Python for the first 6 months, then switch to Ruby and Rails and Postgres - knowing what I know today.  Ruby doesn't scale beyond 20K concurrent users, but for internal corporate applications, that usually isn't an issue.

I do know a few corporate java developers who love their jobs.
I know many Ruby developers who love their jobs.
I did C/C++, then perl then ruby, after doing a bunch of embedded programming (about 30 different languages) for 5 yrs.  Ruby makes me happy.  Perl lets me get stuff done that is fast and efficient.

Also, don't get stuck using just SQL DBs. There are lots of other types of data bases which are sometimes better solutions.  Sometimes text-based DBs are best.  People will try to convince you that "NoSQL" is something new. It isn't.  We had/have tools from 20-30 yrs ago that did the same things. The only difference is that today networks are more stable and faster, which chances how a solution gets built and how it scales.  Usually people don't learn how to scale an application until it is much too late. Often, a re-write is needed - which isn't a bad thing.

In the Linux world, paying for tools/solutions really isn't done most of the time. The only people who do that are corporations who pay PEOPLE do solve their issue or from people that came from the microsoft world and expect to pay.  I see this all the time with video transcoders online.  All of them are rip-offs of ffmpeg, but don't do anything more.  People must be sending them money, since there are thousands of "transcoder" websites when ffmpeg and/or handbrake are available to handle pretty much anything better than those paid tools.

---

