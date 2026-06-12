---
title: "Which language to learn?"
date: 2008-05-15
forum: Recurring Discussions
---

### Post by prowi on 2008-05-15
I'm not new to Ubuntu as a desktop environment but I am relatively new to Linux development programming.  My programming experience/knowledge is limited to maths/stats languages (R, MATLAB, Numpy) but I would like to extend it to languages suitable for supporting Linux and general open source development community.  
I essentially want to know what development language you would recommend a newbie learn and why. (assume that the newbie will only tamper with real problems once these languages are fully mastered)

Specifically:
(1) What do you think are the overall most commonly used development languages?  
(2) Programmers with which language skills are most lacking in the development community?

---

### Post by LaRoza on 2008-05-15
> **prowi said:**
> I'm not new to Ubuntu as a desktop environment but I am relatively new to Linux development programming.  My programming experience/knowledge is limited to maths/stats languages (R, MATLAB, Numpy) but I would like to extend it to languages suitable for supporting Linux and general open source development community.  
I essentially want to know what development language you would recommend a newbie learn and why. (assume that the newbie will only tamper with real problems once these languages are fully mastered)

Specifically:
(1) What do you think are the overall most commonly used development languages?  
(2) Programmers with which language skills are most lacking in the development community?

The sticky should help answer this.

---

### Post by slavik on 2008-05-16
> **prowi said:**
> I'm not new to Ubuntu as a desktop environment but I am relatively new to Linux development programming.  My programming experience/knowledge is limited to maths/stats languages (R, MATLAB, Numpy) but I would like to extend it to languages suitable for supporting Linux and general open source development community.  
I essentially want to know what development language you would recommend a newbie learn and why. (assume that the newbie will only tamper with real problems once these languages are fully mastered)

Specifically:
(1) What do you think are the overall most commonly used development languages?  
(2) Programmers with which language skills are most lacking in the development community?

1. C++, Java, C#.
2. Which development community exactly are you referring to?

Ss for the answer to the first paragraph, I would have to say C. As a language, it is very small yet will allow you to do some neat things. Then you can move on to a sledgehammer called Perl.

---

### Post by Verminox on 2008-05-16
The general open source development community also includes web development. So if you fancy web development over console/desktop applications, start with learning XHTML/CSS and then try PHP/Javascript. It's *relatively* easier to make user interfaces on web pages using HTML because it would take a longer time for a beginner to transition from the terminal to the desktop.

That being said, the [FAQ]("http://ubuntuforums.org/showthread.php?t=606009") sticky would be a great place to get an overview of everything.

---

### Post by anxfisa on 2008-05-16
I have no background but am picking up Ruby and loving it. It is the most poetic. It dances on "rails" like a pro. I know it is not very efficient ram and space cost wise, but we are entering an era where that may soon become a non issue.  

I am excited by this thread as i am wondering the same and hope others can guide us logically better than my aesthetic rant. 

Thank you for asking this. YOU :guitar: RAWK!

---

### Post by anxfisa on 2008-05-16
> **Verminox said:**
> The general open source development community also includes web development. So if you fancy web development over console/desktop applications, start with learning XHTML/CSS and then try PHP/Javascript. It's *relatively* easier to make user interfaces on web pages using HTML because it would take a longer time for a beginner to transition from the terminal to the desktop.

That being said, the [FAQ]("http://ubuntuforums.org/showthread.php?t=606009") sticky would be a great place to get an overview of everything.

Thank you so much, that approach seems way easier than diving into Ruby. Should I say "Bahut Dhanyavad?" or "Shukran?" Amongst the languages I love to learn are world languages. I can speak spanish and Japanese with some fluency other than English. Others are literary only for me for lack of practice.

---

### Post by Verminox on 2008-05-16
> **anxfisa said:**
> Thank you so much, that approach seems way easier than diving into Ruby. Should I say "Bahut Dhanyavad?" or "Shukran?" Amongst the languages I love to learn are world languages. I can speak spanish and Japanese with some fluency other than English. Others are literary only for me for lack of practice.

Hey, that's pretty good Hindi! And you're welcome :)

---

### Post by pmasiar on 2008-05-16
> **prowi said:**
> (0) what development language you would recommend a newbie learn and why?

Specifically:
(1) What do you think are the overall most commonly used development languages?  
(2) Programmers with which language skills are most lacking in the development community?

(1) That depends on the project. Projects are most often in C, C++, Java, Perl, Python, C# (not in frequency order). Most internal development for ubuntu is in Python, C is probably the most popular, but not as productive for coder as Python. 

(0) Every competent programmer should know multiple languages and use the one most fit for the task at hand. It means to know Python for 90% tasks which are not time critical, C for time critical, and couple more as used in projects related to interests or job.

Perl was popular for quick throwaway code (run once and forget it) 5 years ago, but Python is replacing it. In web app development, PHP and Ruby are popular, Python is catching up.

(2) It depends how you define "community". Around here, way too many "developers" are obsessed by "raw speed" while ignoring the most important speed: speed of development, and arguing all the time for C++, C# or Java, or even for C. Real developers, working on the projects, do not waste time here, but solve problems, fix bugs, in whatever language their project was started. You cannot expect correct answer from this forum - vast majority of participants are not part of any project, they are just wannabes, preparing to dive. After they dive in, they realize how misguided their bias was, but it is in the future :-)

So the skill is lacking most here is the competency :-) There are many competent programmers but they are minority, and not even the loud minority. Development community itself (whatever you mean by that) does not lack skills - it is meritocracy, you need to have skills to get projects with any usable code and following. Skill added most recently is focus to user-friendlines, which was not a goal 5-10 years ago.

---

### Post by prowi on 2008-05-18
Thanks for the responses.  
By 'development', I mean if I wanted to investigate how, say, nautilus/grep/chmod was working which language would I use?  ie offline, basic, Ubuntu stuff.  

From the responses so far it seems C or Python would be the way to go.  

# On a tangent, the point about human languages makes me wonder if the logical structure of your mother tongue predisposes you to learn any computer language more quickly.  Hmmmm...

---

### Post by supirman on 2008-05-18
> **pmasiar said:**
> 
(0) ...know multiple languages and use the one most fit for the task at hand. It means to know Python for 90% tasks which are not time critical, C for time critical, ...

What if **all** tasks are time critical?  :evil: :) In my world (embedded systems), we don't usually have the hardware resources available for python.  I have used python in a few of our larger embedded systems though - very useful for scripting.  We also use it for scripts related to our build process.


However, I concur that most people on forums (these, and others) that dish out advice most readily are often entirely unqualified to do so.  It often seems the case that those with the strongest views and loudest voices know the least.  


To any newbie, learn any language you wish - learning languages is easy.  The most important part is to learn the basics and the thought process.  The language you use isn't important.

---

### Post by pmasiar on 2008-05-18
> **supirman said:**
> What if **all** tasks are time critical?  :evil: :) In my world (embedded systems), we don't usually have the hardware resources available for python.

Never is it so that all the tasks are equally important. 80/20 rule applies: 80% of the time is spent in 20% of the code. But you need to **measure** where it is, not to guess.

Take a look at Forth, it was designed to work in such constraints. Often, you can generate code more compact than handcoded ASM, and more flexible.

---

### Post by dempl_dempl on 2008-05-18
> **pmasiar said:**
> Never is it so that all the tasks are equally important. 80/20 rule applies: 80% of the time is spent in 20% of the code. But you need to **measure** where it is, not to guess.

Take a look at Forth, it was designed to work in such constraints. Often, you can generate code more compact than handcoded ASM, and more flexible.

I disagree , the rule 90/10 aplies :P

---

### Post by dempl_dempl on 2008-05-18
[ My bad.. browser duped the post ...  ]

---

### Post by supirman on 2008-05-18
> **pmasiar said:**
> Never is it so that all the tasks are equally important. 80/20 rule applies: 80% of the time is spent in 20% of the code. But you need to **measure** where it is, not to guess.

Take a look at Forth, it was designed to work in such constraints. Often, you can generate code more compact than handcoded ASM, and more flexible.

Try interfacing keyboard, mouse, touchscreen, usb peripherals, handling A to D conversion, front-panel button scanning/debouncing/etc and performing remote communications with 5ms response windows via RS485 - all on an 8051.  Oh yea, and all peripherals are bit-banged (the damn hardware guys would rather save $1.00 per microcontroller than give me integrated i2c/usb controllers, etc).  

All of these may not be exactly equally important, they all have strict time constraints which need met within a few milliseconds.
Irrespective of speed, you still won't be putting any python on most of the systems we use (16MHz processor, 64k RAM, 64k code space).  

Anyhow, I liked python the little bit that I did with it - it just doesn't apply in the embedded space in which I work.

---

### Post by pmasiar on 2008-05-18
> **supirman said:**
> Try interfacing keyboard, mouse, ...

As I said, those 20% you can do in C, and links easily with Python. Or do all in Forth, I've seen P-machine and Pascal compiler on top of Forth, running in 64K :-)

---

### Post by slavik on 2008-05-18
> **pmasiar said:**
> As I said, those 20% you can do in C, and links easily with Python. Or do all in Forth, I've seen P-machine and Pascal compiler on top of Forth, running in 64K :-)
and how will he get the Python interpreter to run in 64k of memory?

In an embedded system like supirman mentioned, Python brings nothing to the table.

```

slavik@slavik-desktop:~$ ls -lh /usr/bin/python2.5
-rwxr-xr-x 1 root root 1.4M 2008-05-07 12:51 /usr/bin/python2.5

```

note that the Python 2.5 interpreter takes up 1.4MB of space.

---

### Post by LaRoza on 2008-05-18
> **slavik said:**
> and how will he get the Python interpreter to run in 64k of memory?

In an embedded system like supirman mentioned, Python brings nothing to the table.

```

slavik@slavik-desktop:~$ ls -lh /usr/bin/python2.5
-rwxr-xr-x 1 root root 1.4M 2008-05-07 12:51 /usr/bin/python2.5

```

note that the Python 2.5 interpreter takes up 1.4MB of space.

64k: [http://www.tinypy.org/](http://www.tinypy.org/)

---

### Post by slavik on 2008-05-18
and the space for actual python code?

---

### Post by LaRoza on 2008-05-18
> **slavik said:**
> and the space for actual python code?

I wasn't joining in on this argument, just pointing out the project. 

No one here thinks Python is the solution to everything.

---

### Post by supirman on 2008-05-18
> **pmasiar said:**
> As I said, those 20% you can do in C, and links easily with Python. Or do all in Forth, I've seen P-machine and Pascal compiler on top of Forth, running in 64K :-)

Eh, we make KVM switches and extenders, so those are much closer to 100% of the code in our systems, not 20% :)


On a different note - I've never looked at forth, I'll have to see if it will work with our flavor of 8051.  I work for a small company and they're quite set in their ways, but if there were ways to be more efficient, the owner would encourage it.

---

### Post by Wybiral on 2008-05-18
> **LaRoza said:**
> 64k: [http://www.tinypy.org/](http://www.tinypy.org/)

Actually, tinypy is a bit deceiving... It's 64k of SOURCE CODE (yeah, it doesn't make sense to me either, I liked it better when I thought it was a 64k interpreter).

---

### Post by pmasiar on 2008-05-18
> **slavik said:**
> and how will he get the Python interpreter to run in 64k of memory?


I am not sure what is it with you guys, try to read more carefully :-) I never said Python will run in 64K. It was never designed to run in such constraints.

I said that I've seen Forth compiler, with P-code machine and **Pascal** compiler (all implemented in Forth) run in 64K box (with i8080 CPU). It was Forth, not Python. Is it clear now? IIRC it was not full Pascal (not all libraries), just what was needed for basic learning of programming in Pascal, but it included visual debugger/execution tracer. I don't follow Forth for more than 20 years now, so I have no idea where Forth stands now - only that it is still used in embedded systems :-)

---

### Post by slavik on 2008-05-18
> **pmasiar said:**
> I am not sure what is it with you guys, try to read more carefully :-) I never said Python will run in 64K. It was never designed to run in such constraints.

I said that I've seen Forth compiler, with P-code machine and **Pascal** compiler (all implemented in Forth) run in 64K box (with i8080 CPU). It was Forth, not Python. Is it clear now? IIRC it was not full Pascal (not all libraries), just what was needed for basic learning of programming in Pascal, but it included visual debugger/execution tracer. I don't follow Forth for more than 20 years now, so I have no idea where Forth stands now - only that it is still used in embedded systems :-)
you started your argument about being able to do "20% of those in C", then said that Python could do the rest and then switched to something completely different for the 64k memory point.

---

### Post by pmasiar on 2008-05-18
> **slavik said:**
> you started your argument about being able to do "20% of those in C", then said that Python could do the rest and then switched to something completely different for the 64k memory point.

... so instead of trying what I actually said, and spending some effort to understand, you just assumed I said "do all in Python", and argued with that, even if it was **not** what I said? Is the Python the only language I am allowed to like, and all others are forbidden to me, forever? What if I become interested in Erlang, should I register different nick? :-)

---

### Post by pmasiar on 2008-05-18
> **supirman said:**
> On a different note - I've never looked at forth, I'll have to see if it will work with our flavor of 8051.  I work for a small company and they're quite set in their ways, but if there were ways to be more efficient, the owner would encourage it.

Forth is extremely easy to implement (80% is written in Forth), and is implemented for many many CPUs.

Google suggests [http://www.camelforth.com/page.php?4](http://www.camelforth.com/page.php?4)

"CamelForth/8051 requires an 8051 family microprocessor with a serial port and at least 8K of PROM and 1K of RAM."

Warning: Forth is extremely powerful and has absolutely no protection against programmer's errors. For 10% people who can handle it, is very productive. For the rest, is unusable. :-)

---

### Post by slavik on 2008-05-19
> **pmasiar said:**
> As I said, those 20% you can do in C, and links easily with Python. Or do all in Forth, I've seen P-machine and Pascal compiler on top of Forth, running in 64K :-)

re-read that argument, does it make sense to you?

supirman's argument is that something like Python is not usable on an embedded system and goes on to argue that some advanced functionality (is this something to control a very large machine?) is not doable in Python. Your response is that the low level stuff (the 20% of the code) can be coded in C and rest in Python (have you actually written your own C routines that are called from Python?). Then you seem to completely ignore the constricted space and move on to something else.

On a side note, P-System (hence the term 'p-code' and the original idea for a virtual machine) was created when home computers had 64K of memory. (IOW: I am not surprised!)

---

### Post by anxfisa on 2008-05-19
Wow! I have a long way to go. Thank you all for good insight. I am brushing up xhtml thanks to Verminox wonderful advice. And am still trying to go through Ruby, which i love. Thank the gods i am familiar with html somewhat. 

I am thinking programming is the one place where you start at the top (mark-up languages) and work your way down (to binary.) :D

---

### Post by slavik on 2008-05-19
> **anxfisa said:**
> Wow! I have a long way to go. Thank you all for good insight. I am brushing up xhtml thanks to Verminox wonderful advice. And am still trying to go through Ruby, which i love. Thank the gods i am familiar with html somewhat. 

I am thinking programming is the one place where you start at the top (mark-up languages) and work your way down (to binary.) :D
Or you start at binary and go up (this is my view) (although mark up languages are mark up, not programming, IMO).

---

### Post by pjkoczan on 2008-05-19
> **anxfisa said:**
> I am thinking programming is the one place where you start at the top (mark-up languages) and work your way down (to binary.) :D

The way I learned to program was to start at the top level (Basic, Pascal, and C++), and once I became proficient in that, delve deeply to the bottom level (binary and assembly), and use the knowledge I gained to increase my overall understanding.

Granted, I don't think anything beyond university courses, compiler development, and maybe embedded systems would force you to learn and write assembly, but it helps a lot to understand what's going on at the very low level, especially when you get into more complicated programs and memory management in C.

---

### Post by cardinals_fan on 2008-05-19
> **anxfisa said:**
> I have no background but am picking up Ruby and loving it. It is the most poetic. It dances on "rails" like a pro. I know it is not very efficient ram and space cost wise, but we are entering an era where that may soon become a non issue.  

I am excited by this thread as i am wondering the same and hope others can guide us logically better than my aesthetic rant. 

Thank you for asking this. YOU :guitar: RAWK!
My thoughts exactly.  I started what should become a new tradition last summer: write a script a day (increasing in complexity) over the summer in a chosen language.  Last summer I did Perl, but this year I'm trying Ruby.

In a few pre-summer tests, Ruby has blown me away.  It actually makes sense, unlike many languages.  The whole thing feels very logical for scripting.

---

### Post by anxfisa on 2008-05-26
Currently I am going back and forth between brushing up XHTML and learning Ruby. I have gotten stuck a few times but i enjoy the challenge of figuring things out. Soon I will be able to participate in intelligent conversation. It is incredible to learn programming languages, after awhile they sort of start to teach themselves. 

It is very exciting to me. :cool:

---

