---
title: "Some tips for a college programmer?"
date: 2006-11-04
forum: Programming Talk
---

### Post by neobonzi on 2006-11-04
Hey there everyone!

I'm a long time computer lover and short time linux user currently enrolled as a Computer Science major at California Polytechnic State University (CalPoly).

  My school starts off by teaching CPE101 - 103 in C and I really wanted to do all my programming on linux. I was wondering what a good interface might be to work on projects?

  For example, on windows they direct us to use a program called JGrasp and now that im on linux i was wondering what you all use? Thanks for the help!

---

### Post by Joe_CoT on 2006-11-04
Strange, I generally use gcc and gedit :D

To be honest, gedit is actually really, really good -- it does syntax highlighting for C/C++, java, html, php, etc.

If you're looking for an IDE to work with, a lot of people use Eclipse or Ajunta I believe. Basically, just go to the programming section in Add/Remove programs and try IDEs until you find one you like.

---

### Post by bettlebrox on 2006-11-04
U won't be stuck for choice! 

Emacs
vi
Gedit
Eclipse
Kdevelop
and more!

IDE's can isolate you a bit from what's is going on. I think it's a good idea to start w/ either Emacs or Vi and compile stuff your self (or learn make). As you become better at it, then try an IDE as you'll then have a better grasp of the whole process and then be better prepared at debugging.

Have a look at "[The Art of Unix Programming]("http://catb.org/esr/writings/taoup/html/")" by ESR.

Luck

---

### Post by hod139 on 2006-11-04
> **neobonzi said:**
> 
  For example, on windows they direct us to use a program called JGrasp and now that im on linux i was wondering what you all use? Thanks for the help!

If your school wants you to use jGRASP, why not use jGRASP?  While I personnally don't like schools that lock students into a specific tool, many of the exercises and projects your professor has may require, or be much more simplified, using jGRASP.

Since jGRASP is written in java it should work fine in Linux.

---

### Post by rplantz on 2006-11-04
> **hod139 said:**
> If your school wants you to use jGRASP, why not use jGRASP?  While I personnally don't like schools that lock students into a specific tool, many of the exercises and projects your professor has may require, or be much more simplified, using jGRASP.

Since jGRASP is written in java it should work fine in Linux.

I was a CS Professor at Sonoma State (also part of the CSU system) for 21 years. One of the problems with grading programs is that each programming environment has its own idiosyncrasies. If I allowed students to use whatever they wanted, grading was a nightmare. For example, not all C compilers follow the standards precisely. So a student could make what was technically a mistake, the program would run on his or her machine, but it would not run on mine.

After a few years of this, I finally specified that the program had to compile and run correctly in the environment supplied in our labs. This allowed students to do most of their development at home, but they needed to do the final tweaking in one of our labs.

In return, I took the time to read each program and comment on the student's style, etc. That is, I did a conscientious job of grading programs.

My advice is to talk with your instructor(s) about what they expect from you. If they are good teachers (some professors are not very good teachers), they will discuss this with you, and you can both learn in the process.

Yes, I learned a LOT from my students. I almost always had at least one student who was a Linux geek, and they taught me a lot. I encouraged them to correct me, even in front of the rest of the class.

---

### Post by junglepeanut on 2006-11-04
I agree with many other posters, find an IDE you like, then plan some time to double check it works with JGrasp. I did basically the same thing for one of the professors in my Introduction to C++ courses (I am a Physics Major) awhile back at CalPoly as well. My brother (ECE major) used the same IDE recommended a few years later. Both of us found are own ways and were happy. If I recall correctly the courses in the 100 level are lecture/lab for programming and you have lecture one day a week then you have to go to the lab the next day. I found that I could get by with trying new things out while I was in the lab. Then go home work on the code where I was most comfortable. Then since the labs are open all the time, I would just test it out before it was due under his compiler.

That being said I have been a way from the campus for a while so I forget everyones names, but most of the professors were decent teachers but brilliant in their areas. So I actually learned just by doing what they asked. (This meant I did not do well on portions of the test were I was asked to define an array, but when we had to write code or debug code for a test I did well.)

---

### Post by neobonzi on 2006-11-05
Hey all! thanks for the great replies - 

  I tried installing Jgrasp on linux but im such a total newbie that I had trouble getting it to work correctly. I installed ajunta and it's a pretty cool program but im going to keep looking around for more.

  Its cool to see a professor who taught at sanoma and a calpoly alumni here! My professor, Zoe Wood, requires all output to be identical to a sample. They run a comparison on their unix systems and take points off for every discrepancy. The coding is completely up to us and the only important thing is style (indentation, commenting, cleanliness) so I'm fairly free to explore different avenues as far as programming environments.

---

### Post by theorem_hunter on 2006-11-05
well your very luck you have that freedom. at my uni im forced to use m$ visual studio 2005.

my lectures tell me to stop wasting time with Linux & that there is not money in it, getting a job wise. 

im told that Microsoft pays them to encourage m$ products & a m$ way of life. :(

---

### Post by rplantz on 2006-11-05
> **neobonzi said:**
> The coding is completely up to us and the only important thing is style (indentation, commenting, cleanliness) so I'm fairly free to explore different avenues as far as programming environments.

To maximize your learning, I recommend that you discuss the various avenues with your professor. We don't go into teaching for the money. Most of us do it because we like learning and teaching. The fact that you have asked these questions here suggest that you really want to learn the stuff. Most professors like students who want to learn. This is especially true at the CSU campuses. (The UC system emphasizes research, and many professors there see undergraduate teaching as taking time away from their research. I'm not blaming them because they are under lots of pressure to bring in grant money.)

So, tackle your programming assignments early. Read the book several times. (Yes, several times; it's not a novel.) Then, if you come up with more than one way to approach the problem, go ask your professor about the pros and cons of each approach. I'm reasonably sure that she will be very willing to discuss your ideas with you. I suspect that she will enjoy finding a student who wants to learn the material and that you will learn more.

---

### Post by yolloms on 2006-11-07
kate along with gcc from the terminal.

kate does syntax highlighting and indexing.

---

### Post by Choad on 2006-11-07
> **theorem_hunter said:**
> well your very luck you have that freedom. at my uni im forced to use m$ visual studio 2005.

my lectures tell me to stop wasting time with Linux & that there is not money in it, getting a job wise. 

im told that Microsoft pays them to encourage m$ products & a m$ way of life. :(
so *that* is why microsoft is is cozying up with novell!?

lol i get tired of being better informed than most of my teachers. the guy who actually teaches programming in the lab is a good guy, knows alot and is fun, but some of my other lecturers... 

for the most part, a nice text editor + gcc in a terminal is what you want. the only special features it should offer are syntax highlighting and simple auto-indent (ie you dont have to tab 3 times at the beggining of each new line on the 3rd teir)

</my 2 cents>

---

### Post by bettlebrox on 2006-11-07
I agree with Choad.

---

### Post by Bakerconspiracy on 2007-07-11
> **theorem_hunter said:**
> well your very luck you have that freedom. at my uni im forced to use m$ visual studio 2005.

my lectures tell me to stop wasting time with Linux & that there is not money in it, getting a job wise. 

im told that Microsoft pays them to encourage m$ products & a m$ way of life. :(

It is very disheartening to hear this.... What school do you go to?

---

### Post by xtacocorex on 2007-07-11
Are you seriously expecting a response from a long dead thread?

---

### Post by kknd on 2007-07-11
Vim + gcc are your friends =).

If you do not like Vim, try gedit.

---

### Post by Note360 on 2007-07-11
try Vim (gvim), Emacs, Scribes, Gedit and Kate and find the one you like (plus gcc for compilation). If you want you can try an IDE but I found I never liked IDEs.

IF you try vim and Emacs give them the proper time (atleast a week) and configure them to your liking. Both are extremely flexible.

---

