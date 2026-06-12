---
title: "Object Oriented Programming Resources"
date: 2018-07-09
forum: Programming Talk
---

### Post by jason.jackal on 2018-07-09
Folks,
I have been programming in Python, BASH and some TCL for a while now; however, I want to get some skills and resources in Object Oriented Programming (OOP), yet I am struggling with OOP concepts. What are some good/great OOP books or resources that will start at zero(0) and teach OOP concepts from a beginner who knows nothing of OOP design and programming concepts?

Thank you
JJ

---

### Post by TheFu on 2018-07-09
> **jason.jackal said:**
> Folks,
I have been programming in Python, BASH and some TCL for a while now; however, I want to get some skills and resources in Object Oriented Programming (OOP), yet I am struggling with OOP concepts. What are some good/great OOP books or resources that will start at zero(0) and teach OOP concepts from a beginner who knows nothing of OOP design and programming concepts?

Out of those, only Python supports OOP.  

I remember when I was in your position a few decades ago. For me, I wasn't able to "click" with the ideas until I attended a physical class with an instructor. Books and articles didn't help. Then it all became clear, the big ideas, not the specific implementations. Implementation details take more time and I made lots of mistakes.  You are probably smarter than I am. Back then, we didn't have any video on computers, so no youtube existed. 

I know that MIT has a python-based course that introduces some OOP/OOD concepts.  It is a mix of video, reading, and assignments.   All online, free. [https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/video-lectures/](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/video-lectures/) .  Edx probably has some free training too. [https://www.edx.org/course/software-construction-object-oriented-ubcx-softconst2x](https://www.edx.org/course/software-construction-object-oriented-ubcx-softconst2x)

Some knowledge needs formal introductions.

---

### Post by jason.jackal on 2018-07-10
> **TheFu said:**
> Out of those, only Python supports OOP.  

I remember when I was in your position a few decades ago. For me, I wasn't able to "click" with the ideas until I attended a physical class with an instructor. Books and articles didn't help. Then it all became clear, the big ideas, not the specific implementations. Implementation details take more time and I made lots of mistakes.  You are probably smarter than I am. Back then, we didn't have any video on computers, so no youtube existed. 

I know that MIT has a python-based course that introduces some OOP/OOD concepts.  It is a mix of video, reading, and assignments.   All online, free. [https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/video-lectures/](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/video-lectures/) .  Edx probably has some free training too. [https://www.edx.org/course/software-construction-object-oriented-ubcx-softconst2x](https://www.edx.org/course/software-construction-object-oriented-ubcx-softconst2x)

Some knowledge needs formal introductions.
HI TheFu,
Yeah for some reason I just cannot grasp OOP/OOD. I have had only two formal programming classes in my life, (Way back time machine) C and Visual Basic, +cough++ ++cough++ that must have been sometime in the early to mid 90s, since Java was not out yet.

My main goal is to learn Java, which I have the Head First Java book; however, I seem to be missing something since I am not getting the OOP design. Granted I have only started and on chapter 2, yet I feel like I do not have the beginning pieces.

Thank you

---

### Post by Rocket2DMn on 2018-07-10
I learned OOP in college, but it wasn't until I used it for probably over a year in industry before it really clicked.  I think the toy problems you see in textbooks and assignments aren't sufficient because they are designed specifically to try and describe and demonstrate OOP (I know, sounds counter-intuitive).  I needed to see it in real software, interacting with real data and external resources (e.g., with databases, web services, application servers, service buses, other software including legacy components), and maybe even see the same problem implemented 1) without OOP practices, 2) poorly as OO, and 3) well as OO.  This basically comes down to "learn by example" where the examples are real, not made up.

---

### Post by TheFu on 2018-07-10
If you learn X/Windows programming in C, you'll see that they used "structs" as a way to keep data for a specific "object" together.  The specific type for the struct was dependent on the X-widget (button, label, menu, portal, menuitem, etc) that is to be modified or used.  The core idea is that the data and the functions which act on that data are grouped (encapsulated) together.  This prevents all sorts of common programming errors with mismatched types that are extremely common in untyped languages.

OOP without OOD is useless.  Start with baby-OOD first. You don't need to be an expert, but understanding simple UML diagrams is very helpful when discussing OOD/OOP.

Don't get too sidetracked by polymorphism or inheritance. In 20+ yrs, I've found those to be mostly tricks, not really necessary. About 10% of the time, those tools are very helpful, but not usually.  

Opinions follow. BTW, we are about the same age.

Java?   Ewwww.  I met with some of the Sun designers in the early 1990s while working in a govt lab. We were writing cross-platform C++ code (over 12 different platforms) for our GUI application.  Java promised the world and the things these designers said would take a few years to correct have never been corrected in ... 25 yrs.  Java is still slow. It still sucks RAM.  And it still has memory management and security issues.  It solves 1 problem - compile once, but introduces 50 others, IMHO.   But if you want a corporate programming job, then Java is still the language for a few more years until Oracle screws it up more.  Devs are running away from the Oracle Java stuff hoping to avoid their licensing.  The big guys will probably still be sued by Oracle, even if they do convert to F/LOSS alternatives.  Non-enterprise software development has left java already.  Java is "legacy" now, just like C. OTOH, if you have a specific job that you want and it requires Java, then that is what you should learn.  I did Java for android about a year and would rather go to the dentist every day than do that again.  Only played with Java on other OSes. 

I think Google is moving away from Java for their portable devices, choosing a different language to get away from Oracle's grips. It has been reported they are dropping "Android" to make a clear non-Java OS.  I found a few articles about it on reputable computing websites.

IMHO.

---

### Post by jason.jackal on 2018-07-10
> **Rocket2DMn said:**
> I learned OOP in college, but it wasn't until I used it for probably over a year in industry before it really clicked.  I think the toy problems you see in textbooks and assignments aren't sufficient because they are designed specifically to try and describe and demonstrate OOP (I know, sounds counter-intuitive).  I needed to see it in real software, interacting with real data and external resources (e.g., with databases, web services, application servers, service buses, other software including legacy components), and maybe even see the same problem implemented 1) without OOP practices, 2) poorly as OO, and 3) well as OO.  This basically comes down to "learn by example" where the examples are real, not made up.

That is how I learned Perl by doing real world items; however, these days I do not do much in Perl. To be honest, I mainly still use TCL due to Cisco devices and my Python is not that strong yet.

---

### Post by jason.jackal on 2018-07-10
> **TheFu said:**
> If you learn X/Windows programming in C, you'll see that they used "structs" as a way to keep data for a specific "object" together.  The specific type for the struct was dependent on the X-widget (button, label, menu, portal, menuitem, etc) that is to be modified or used.  The core idea is that the data and the functions which act on that data are grouped (encapsulated) together.  This prevents all sorts of common programming errors with mismatched types that are extremely common in untyped languages.

OOP without OOD is useless.  Start with baby-OOD first. You don't need to be an expert, but understanding simple UML diagrams is very helpful when discussing OOD/OOP.

Don't get too sidetracked by polymorphism or inheritance. In 20+ yrs, I've found those to be mostly tricks, not really necessary. About 10% of the time, those tools are very helpful, but not usually.  

Opinions follow. BTW, we are about the same age.

Java?   Ewwww.  I met with some of the Sun designers in the early 1990s while working in a govt lab. We were writing cross-platform C++ code (over 12 different platforms) for our GUI application.  Java promised the world and the things these designers said would take a few years to correct have never been corrected in ... 25 yrs.  Java is still slow. It still sucks RAM.  And it still has memory management and security issues.  It solves 1 problem - compile once, but introduces 50 others, IMHO.   But if you want a corporate programming job, then Java is still the language for a few more years until Oracle screws it up more.  Devs are running away from the Oracle Java stuff hoping to avoid their licensing.  The big guys will probably still be sued by Oracle, even if they do convert to F/LOSS alternatives.  Non-enterprise software development has left java already.  Java is "legacy" now, just like C. OTOH, if you have a specific job that you want and it requires Java, then that is what you should learn.  I did Java for android about a year and would rather go to the dentist every day than do that again.  Only played with Java on other OSes. 

I think Google is moving away from Java for their portable devices, choosing a different language to get away from Oracle's grips. It has been reported they are dropping "Android" to make a clear non-Java OS.  I found a few articles about it on reputable computing websites.

IMHO.
I am not a big fan of Java as well; however, I have an interest in Android programming. Would you recommend C++ for OOP/OOD to learn? From what I have read Python does OOP/OOD; however, I am not sure if that is the best place to start for OOP/OOD. I use Python now, but that is more of a scripting language, which could technically be done with BASH/AWK and/or Perl. To be honest - I have found GO, and really sort left Python for some of my scripts and for what I have been doing BASH has been serving me better.

---

