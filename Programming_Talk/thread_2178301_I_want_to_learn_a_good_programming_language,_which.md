---
title: "I want to learn a good programming language, which?"
date: 2013-10-02
forum: Programming Talk
---

### Post by Cyb3 on 2013-10-02
I want to begin programming and i want to start programming on operating systems (linux), backend and interact with the hardware. Which is the "best" choice? Linux was programmed in C, please correct me if i'm wrong? Should i learn that or is C++ a better solution? I have heard of these languages:

Python
Ruby
Ruby on Rails
Java
C
C++

I'm feeling confused of which i can begin with. What is sought after in the labor market? Should i ignore what the labor market are after?

I'm having very many questions and i feel lost in the whole djungle of programming languages. What should i learn and why?

---

### Post by trent.josephsen on 2013-10-02
Did you see the [Programming Guides and Basics - Read Me First](http://ubuntuforums.org/showthread.php?t=1766253) sticky? Lots of good links there.

Unfortunately, there are no hard answers or rules of thumb. All of the languages you mention, plus dozens more, are highly sought after in one place or another, and in many cases the choice of a language comes down to no more than "Steve knows C, so we used that" or "This program started out when our CIO was on a Python kick". Which specific languages are desirable for a particular application varies from company to company, industry to industry, country to country and in the U.S., coast to coast. In my sector, Tcl and MATLAB are good examples of programming languages that are used for scripting tasks that would be subsumed by Perl, Python, Scheme, Java, bash or what-have-you in other environments. So to a certain degree, they're all interchangeable.

Now for a little more tailored advice... you say you're interested in OS development and hardware. It's good that you have an idea what you want to do. But when you're starting, you will be pretty preoccupied with things like loops and if-statements without even thinking about hardware; this stage will last for a while, and I think it's advisable to figure out that stuff in a higher-level language. This is a very contentious point and I have no intention of engaging in *that* debate again, so let's just say that there are people who disagree with me and if you search the forums or Google for "high-level vs low-level programming language" you will find a number of eloquently stated positions on both sides; pick the direction that seems best to you. I and many others on this forum usually suggest Python to beginners because it is easy to get started with and can be a real heavy-duty tool when you need it.

When you're comfortable with Python (or if, contrary to my advice, you decide to start on a lower level), may I recommend getting an Arduino? You'll need to understand hardware pretty well before you have the skill to hack on Linux, and Arduinos use some flavor of almost-but-not-quite-C that may help you transition into the realm of software that does what I call "real stuff". Some basic knowledge of electronics also recommended.

---

### Post by Cyb3 on 2013-10-03
> **trent.josephsen said:**
> Did you see the [Programming Guides and Basics - Read Me First]("http://ubuntuforums.org/showthread.php?t=1766253") sticky? Lots of good links there.

Unfortunately, there are no hard answers or rules of thumb. All of the languages you mention, plus dozens more, are highly sought after in one place or another, and in many cases the choice of a language comes down to no more than "Steve knows C, so we used that" or "This program started out when our CIO was on a Python kick". Which specific languages are desirable for a particular application varies from company to company, industry to industry, country to country and in the U.S., coast to coast. In my sector, Tcl and MATLAB are good examples of programming languages that are used for scripting tasks that would be subsumed by Perl, Python, Scheme, Java, bash or what-have-you in other environments. So to a certain degree, they're all interchangeable.

Now for a little more tailored advice... you say you're interested in OS development and hardware. It's good that you have an idea what you want to do. But when you're starting, you will be pretty preoccupied with things like loops and if-statements without even thinking about hardware; this stage will last for a while, and I think it's advisable to figure out that stuff in a higher-level language. This is a very contentious point and I have no intention of engaging in *that* debate again, so let's just say that there are people who disagree with me and if you search the forums or Google for "high-level vs low-level programming language" you will find a number of eloquently stated positions on both sides; pick the direction that seems best to you. I and many others on this forum usually suggest Python to beginners because it is easy to get started with and can be a real heavy-duty tool when you need it.

When you're comfortable with Python (or if, contrary to my advice, you decide to start on a lower level), may I recommend getting an Arduino? You'll need to understand hardware pretty well before you have the skill to hack on Linux, and Arduinos use some flavor of almost-but-not-quite-C that may help you transition into the realm of software that does what I call "real stuff". Some basic knowledge of electronics also recommended.

Thank you for a very well written answer. I've checked the links in that post a little, but some threads were more than 5 years old and i thought it might be good to ask you guys again to get an "update". So just to make things clear for me, Python is a "high-level" language? Is it easy to go from Python to C++ or C if i had to? What companies are using Python out there that are well known? Is it growing? Is this a comparison to Ruby? A lot of questions again... But i just might be starting with Python then if you guys think it's the best programming language to begin with.

---

### Post by ofnuts on 2013-10-03
I agree with TJ... Use Python to learn the basics or programming (which is mostly about acquiring a mindset...). When you are comfortable with Python, start looking at C, and exercise your hardware interfacing skills with an Arduino.

---

### Post by Vaphell on 2013-10-03
> **Cyb3 said:**
> Thank you for a very well written answer. I've checked the links in that post a little, but some threads were more than 5 years old and i thought it might be good to ask you guys again to get an "update". So just to make things clear for me, Python is a "high-level" language? Is it easy to go from Python to C++ or C if i had to? What companies are using Python out there that are well known? Is it growing? Is this a comparison to Ruby? A lot of questions again... But i just might be starting with Python then if you guys think it's the best programming language to begin with.

High level languages deal with 'what' but hide 'how' to a large degree, while low level ones expose the inner workings and expect programmer to write a lot of 'how' too. Difference between 'sort this set in ascending order' and 'from this set take elem 1 and compare it to elem 2, if e1>e2 switch places, wash rinse repeat' is obvious, the former is more abstract, high level.

It's not that easy to switch from python to c/c++ because losing all that convenience (nice syntactic sugar, automagical memory management, etc) it offers is quite painful, but once you know basic concepts of programming it's much easier to tackle the gritty details of lower level programming. Python is suggested because it's unlikely to overwhelm a novice with serious amounts of frustrating caveats that make or break his program.

Don't obsess over picking the right language, industry changes all the time and most programmers worth their salt are competent in a number of languages which lend themselves to different things. The more languages you know, the easier it is to learn another one. That being said, you can't go wrong with python, as even in the worst case scenario where you don't deal with it professionally, it's still a very nice language to whip up quick and dirty programs to automate some mundane crap - you don't write these in C.

[http://en.wikipedia.org/wiki/Python_%28programming_language%29#Use](http://en.wikipedia.org/wiki/Python_%28programming_language%29#Use)
also MIT uses Python in the intro programming classes

---

### Post by Cyb3 on 2013-10-03
> **Vaphell said:**
> High level languages deal with 'what' but hide 'how' to a large degree, while low level ones expose the inner workings and expect programmer to write a lot of 'how' too. Difference between 'sort this set in ascending order' and 'from this set take elem 1 and compare it to elem 2, if e1>e2 switch places, wash rinse repeat' is obvious, the former is more abstract, high level.

It's not that easy to switch from python to c/c++ because losing all that convenience (nice syntactic sugar, automagical memory management, etc) it offers is quite painful, but once you know basic concepts of programming it's much easier to tackle the gritty details of lower level programming. Python is suggested because it's unlikely to overwhelm a novice with serious amounts of frustrating caveats that make or break his program.

Don't obsess over picking the right language, industry changes all the time and most programmers worth their salt are competent in a number of languages which lend themselves to different things. The more languages you know, the easier it is to learn another one. That being said, you can't go wrong with python, as even in the worst case scenario where you don't deal with it professionally, it's still a very nice language to whip up quick and dirty programs to automate some mundane crap - you don't write these in C.

I think you covered everything that i was questioning here. Thank you for your answer on this. I will begin with Python. I will mark this thread as solve now but if anyone else has any opinions regarding this, please share it here :)

---

