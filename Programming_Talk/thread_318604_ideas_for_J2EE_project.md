---
title: "ideas for J2EE project"
date: 2006-12-14
forum: Programming Talk
---

### Post by welshboy on 2006-12-14
Hey there folks,

Just wanted to ask a favour if that's ok?

I'm trying to learn stuff to get a job as a programmer.  I have a degree in Computer Science, but I didn't go straight into the industry after graduation.  (I won't go in to why).

And a lot of job sites I look at, want experience in J2EE.  Now I know what all the J2EE stuff is, and I'm hoping to write a system that would be considered a J2EE application.

However due to lack of experience in the last three years, I honestly don't know what kind of thing a J2EE application would be. 

I was wondering if anyone would be willing to give me some ideas for J2EE projects I could write, to try and get my experience up to do.  My hope is to do a kind of programming portfolio of the stuff that I've written, to show the folks that I can indeed write computer programs.  

Many thanks

welshboy

---

### Post by lloyd mcclendon on 2006-12-14
my first app was a patient scheduler.  no technically it wasn't j2ee since it ran in plain tomcat and used j2se, but it was a good example of enterprise development with good open source stuff & no crazy stuff from sun.  ejb3 is a totally different animal than the crap that was ejb2 so i am starting to look into using them.

someone would log in, enter some pt info, pick a doctor, and have a list of times that she was avail pop up.  they could also view a list of patients, drill down to one to edit.  also had email functionality and some other bells & whistles.

some sort of CRUD application would proably be a good start.  you will want to look into some frameworks & tools.  i can suggest some, if you're interested let me know and i'll elaborate.

---

### Post by pmasiar on 2006-12-14
If you have $100 - $150 to invest, I would recommend *hands-down the best book* with tasks to solve: [Etudes for Programmers]("http://www.amazon.com/Etudes-Programmers-Charles-Wetherell/dp/0132918072") . When I was looking for it on internet again (I was surprised: for some reason was not reprinted since late 70), I read about one 14 year old who solved all task from it and got hired in place od CS graduate.

Really very good and interesting tasks.

You may also consider learning the tools: eclipse is now almost standard IDE. Everybody talks about design patterns mumbo-jumbo.

Also, many java programmers realized that web applications can be done much easier and faster in scripting languages like python or ruby (see couple of discussions about it just within last week). So you may want to add another tool your toolset - a scripting language.

---

### Post by welshboy on 2006-12-15
Hi Folks,

Many thanks for your replies.  I don't have a clue what CRUD stands for, so if you could tell me what that means, that would be cool.

But yeah, I'll have a crack at trying to get hold of that book.  Sounds like a lot of fun.

Many thanks.

---

### Post by pmasiar on 2006-12-15
CRUD: Create Read Update Delete: basic database operation. 

IMHO very bad name (who would want to implement CRUD? not me!). I prefer BREAD: Browse Read Edit Append Delete. You implement bread, and then add butter to make your bread-and butter database app. :-)

---

### Post by welshboy on 2006-12-15
Cool, many thanks for that.

I'm currently designing a course management system for a side project, would something like that be considered J2EE??  I intend to use the JDBC to connect to a mySQL server, which will make it easier in terms of writing a login system, the program will then be able to either e-mail or print labels so that the stuff can be sent to the students, and e-mails sent to those running the course to book materials etc.  And possibly a servlet will be included to show a kind of course diary.

What do you think?

---

### Post by pmasiar on 2006-12-15
I searched sourceforge for java course, using this search string: "(+java +course) AND trove: (71 72 130 585 586)". Got 12 projects. You may want to play around with some synonyms, find more projects, join any of them, or register yet another yours.

J2EE feels so "enterprisey" - means funny :-) Free software community prefers agility and simplicity, IMHO. All cool kids do web apps in python and ruby, with AJAX. 8-) YMMV

---

