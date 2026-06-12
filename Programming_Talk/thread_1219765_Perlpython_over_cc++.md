---
title: "Perl/python over c/c++"
date: 2009-07-22
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-22
could someone please explain when perl and python should be used and when c and c++ should be?

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> could someone please explain when perl and python should be used and when c and c++ should be?
C and C++ should be used when you write software that is low-level and/or might be stressed for a longer time.

---

### Post by apoth on 2009-07-22
Use python the rest of the time. Perl's reserved for sadomasochists. ;)

---

### Post by Dullstar on 2009-07-22
I recommend Python, if only because it's the only programming language I could figure out at all.  I wrote a whole calculator with that, with C/C++ I can't even get past Hello World!

---

### Post by Sockerdrickan on 2009-07-22
> **Dullstar said:**
> I recommend Python, if only because it's the only programming language I could figure out at all.  I wrote a whole calculator with that, with C/C++ I can't even get past Hello World!
OP asked when which tool should be used, not which is better generally.

---

### Post by nrs on 2009-07-22
C when performance is supremely critical, C++ when performance is critical and you don't want to be a complete ascetic. I use Python for pretty much everything else.

---

### Post by TheStatsMan on 2009-07-22
As a rule of thumb, I guess if the higher level language can be used to answer the problem adequately well (eg find a solution within the necessary or desired timeframe) then the higher level language should be used as in general the solution will be achieved in less time.

As a statistician: I would generally look at programs in this order:
1. has the program already been done in R (choose R)
2. Is this something that I can solve with Octave (or others, not R though as I don't like the language, all the rest are pretty much the same); choose octave; 
3. Would I rather do it in python or is it going to be used by others at work use python
4. Can most of the code be done in python and turbocharged using C/C++ 
5. Use C++ (generally large scale programming with new algorithms not suited to higher level languages)

Basically the list for me goes from highest R to lowest C++. This is not a strict list, as I have a lot of C++ code if I can often produce an answer in the same time (or at least near enough, sometimes possibly less) as the high level language then I would favour c++. Sometimes I may be in a mood to code in a certain language so that can also effect my decision. The more re-usable the code is the less preference I would give to the programs at the top of the list.

---

### Post by nipunreddevil on 2009-07-22
What shall be the benefits be for learning python/perl over strengrhening c/c++ in the same time.
I also intend to use GTK+.

---

### Post by TheStatsMan on 2009-07-22
The benefit is obvious. You can learn python (I haven't used perl so I can't comment on it) in a very short amount of time. Your aim should be to maximize the speed of development and in general higher level language will shorten development time. The answer is going to vary a lot the depending on the problem.

---

### Post by nipunreddevil on 2009-07-22
How easy is it for a person who knows c/c++/java to learn python.
what role does it play in shell scripting?

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> How easy is it for a person who knows c/c++/java to learn python.
Very easy I would say from personal experience. :D

---

### Post by nipunreddevil on 2009-07-22
How easy is PYTHON for designing of interfaces and for serial port access as compared to c/c++/Java

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> How easy is PYTHON for designing of interfaces and for serial port access as compared to c/c++/Java
That sounds more like a task for C or C++ absolutely. :)

---

### Post by nipunreddevil on 2009-07-22
ok.
how much of a speed difference will exist between c and PYTHON for doing the same tasks.
Which is easier for QT and GTK+,C or PYTHON?

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> how much of a speed difference will exist between c and PYTHON for doing the same tasks.
That depends on the task, do however note that most intensive standard functions in Python are implemented in C. :D

---

### Post by nipunreddevil on 2009-07-22
Ok thanks,
So what would you recommend for design of a Ground control station of a uav requiring serial port interfacing,displaying movable maps like google maps ,display virtual cockpit like flight simulators,A GUI window with all these. 
factors:
Real time?
Ease in design?
Support and help available?
Time reqd?

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> Ok thanks,
So what would you recommend for design of a Ground control station of a uav requiring serial port interfacing,displaying movable maps like google maps ,display virtual cockpit like flight simulators,A GUI window with all these. 
factors:
Real time?
Ease in design?
Support and help available?
Time reqd?
I don't know what that actually is in detail but my instinct tells me that you should use C or C++ for this task.

---

### Post by apoth on 2009-07-22
> **nipunreddevil said:**
> So what would you recommend for design of a Ground control station of a uav requiring serial port interfacing,displaying movable maps like google maps ,display virtual cockpit like flight simulators,A GUI window

It depends, but I'd probably split it up, deal with the serial port interfacing in C/C++, the maps, display and GUI probably something else, maybe Python, Java or Javascript, or a mix again.

---

### Post by nipunreddevil on 2009-07-22
Ok thanks
Where shall i get started from?

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> Ok thanks
Where shall i get started from?
[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)
and
[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

If you are referring to programming by itself.

---

### Post by nipunreddevil on 2009-07-22
Thanks for the links,but sir i am referring to my appliction.
have good knowledge of c/cpp.Decent one of JAVA.started with gtk couple of days back.Saw Python tutorial and find it easy and interesting.So help regarding approach towards application .

---

### Post by Sockerdrickan on 2009-07-22
Ok then you might want to look for similar projects and read as much as you can about them, then starting to plan your implementation with some abstract drawings for example...

---

### Post by nipunreddevil on 2009-07-22
> **apoth said:**
> It depends, but I'd probably split it up, deal with the serial port interfacing in C/C++, the maps, display and GUI probably something else, maybe Python, Java or Javascript, or a mix again.

Thats a very interesting approach.
Is this approach followed in commercial software.
Could you provide some examples of how to go about it.

---

### Post by nipunreddevil on 2009-07-22
> **Tux0r said:**
> Ok then you might want to look for similar projects and read as much as you can about them, then starting to plan your implementation with some abstract drawings for example...

Sir the basic  problem is that these softwares are available commercially for a lot of money.
plus i have read people who have developed their own software used Labview which i will not use simply for the cost

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> Sir the basic  problem is that these softwares are available commercially for a lot of money.
plus i have read people who have developed their own software used Labview which i will not use simply for the cost
Ok then you are going to have to do this from the ground up. One way is to write headers with class declarations, before implementing them. Another is to draw inheritance schemes. Do what suites you best and try to keep it as abstract as possible from the start.

---

### Post by nipunreddevil on 2009-07-22
> **Tux0r said:**
> Ok then you are going to have to do this from the ground up. One way is to write headers with class declarations, before implementing them. Another is to draw inheritance schemes. Do what suites you best and try to keep it as abstract as possible from the start.
Thanks for the reply sir.
Could you explain i easier words,seems too heavy to digest what you just said.

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> Thanks for the reply sir.
Could you explain i easier words,seems too heavy to digest what you just said.
Ok. Just like this, try to visualize your software:

[IMG]http://www.vtk.org/doc/nightly/html/classvtkQtChartView__inherit__graph.png[/IMG]

Then start writing on the classes you feel are the most basic parts of the program.

---

### Post by nipunreddevil on 2009-07-22
Thanks a lot.
This sure helps.
will get back if i face more problems along the road less traveled

---

### Post by Sockerdrickan on 2009-07-22
> **nipunreddevil said:**
> Thanks a lot.
This sure helps.
will get back if i face more problems along the road less traveled
Ok then! :D

Good luck and don't start writing implementation parts until you get an idea of how your program will be structured, that's the most crucial part of larger projects.

---

### Post by jpkotta on 2009-07-24
Serial ports are very easy in Python.  It's in the python-serial package.

```

import serial
ser = serial.Serial()
ser.port = "/dev/ttyS0" # or "COM1" in Windows
ser.baudrate = 115200
ser.open()
ser.write("string to send")
print ser.read(ser.inWaiting())
ser.close()
```

Also, have a look at wxPython for GUI stuff.  My guess is that the serial port is going to be slower than the Python code, so any speed advantage that C/C++ have is lost.  You should still do a rough estimate on how fast your code needs to run, and benchmark a Python mockup.

---

### Post by CptPicard on 2009-07-24
No offense, but I am getting the distinct feeling that nipunreddevil should preferably spend more time learning about programming in general before tackling the writing of an UAV ground control station... ;)

---

### Post by nipunreddevil on 2009-07-25
> **CptPicard said:**
> No offense, but I am getting the distinct feeling that nipunreddevil should preferably spend more time learning about programming in general before tackling the writing of an UAV ground control station... ;)
Ok,
I agree with you partially.Let me tell you that i am presently in second year of my undergraduate course in Computer Engineering.
The syllabus has been not updated for past thirty odd years,and the only language been taught is c.The only relevant course so far has been Data Structures,where the faculty was incompetent when it came to new stuff like trees.
So,all that i have learnt is through internet and forums.
I may not have god enough programming skills and knowledge but i still try my level best.
I made this UAV ground station in JAVA last year.will upload its link soon.
Wanted to make it an open source project this time.
I am trying my level best and have been asking for help.
Hope you all forgive me for my stupid questions and doubts if i disturb you.
Sorry again

---

### Post by CptPicard on 2009-07-25
Nah, don't take it like that. I just want to make sure you are at least somewhat on the right page for what you are trying to accomplish... those kinds of potential mismatches are hard to just "help" with, you know.

---

### Post by nipunreddevil on 2009-07-25
> **CptPicard said:**
> Nah, don't take it like that. I just want to make sure you are at least somewhat on the right page for what you are trying to accomplish... those kinds of potential mismatches are hard to just "help" with, you know.

Seriously sir,
I am humble enough to admit i am no geek
and i need help from experts like you to reach to a higher level

---

### Post by slavik on 2009-07-25
> **nipunreddevil said:**
> Ok,
I agree with you partially.Let me tell you that i am presently in second year of my undergraduate course in Computer Engineering.
The syllabus has been not updated for past thirty odd years,and the only language been taught is c.The only relevant course so far has been Data Structures,where the faculty was incompetent when it came to new stuff like trees.
So,all that i have learnt is through internet and forums.
I may not have god enough programming skills and knowledge but i still try my level best.
I made this UAV ground station in JAVA last year.will upload its link soon.
Wanted to make it an open source project this time.
I am trying my level best and have been asking for help.
Hope you all forgive me for my stupid questions and doubts if i disturb you.
Sorry again
"trees" are not new ... if anything, the latest introduction of trees was with the Unix filesystem which was early 70s. I am sure tree existed as a data tructure well before that.

---

### Post by nipunreddevil on 2009-07-25
> **slavik said:**
> "trees" are not new ... if anything, the latest introduction of trees was with the Unix filesystem which was early 70s. I am sure tree existed as a data tructure well before that.

What i meant was stuff which we had not studied in school,new for us
WE knew arrays and lists in school
and didnt learn much beyond that in college

---

### Post by slavik on 2009-07-25
do you know the difference between a "list" and some features it might have?

lists can be "doubly linked" or "circular" or even "sorted" ... if you answer no to all these questions, question the dept. head.

---

### Post by nipunreddevil on 2009-07-25
> **slavik said:**
> do you know the difference between a "list" and some features it might have?

lists can be "doubly linked" or "circular" or even "sorted" ... if you answer no to all these questions, question the dept. head.

Yes know all this stuff
Had learnt it in school itself
Its the trees and the dictionaries and stuff which our faculty could not teach/didnt knw themselves
So i have started with MIT OCW on ALGOS

---

### Post by CptPicard on 2009-07-25
Oh man... how much would I make if I came teach over there?? Would I get a fancy title? :D

---

