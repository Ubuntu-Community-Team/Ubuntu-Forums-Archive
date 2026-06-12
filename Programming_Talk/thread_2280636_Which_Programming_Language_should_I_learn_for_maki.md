---
title: "Which Programming Language should I learn for making softwares for LINUX?"
date: 2015-06-01
forum: Programming Talk
---

### Post by sarang3 on 2015-06-01
Hi,
I have been learning SHELL SCRIPTING since 3 months, and I will soon learn the advanced shell scripting. 
I also have the knowledge of Java Core.
But I wanted to know, which programming language should I learn which will help me to write Programs after I get job in any company. I read in few threads that C++ and Python are good.
My queries are:
1) Which programming language should I go for first, C++ OR Python OR something you experts may suggest?
2) I wish to make GUI apps (front and backend BOTH), the same what is ASP.NET in Windows, so which books should I refer (the issue is that it should be available in India too) :p
3) Are there "playlists" available for the course I want to learn? (If yes, please give me the link)

I hope I was clear with my ques, please give me a detailed answer, in not very technical terms, since I am just a student who wants to learn. ):P

---

### Post by Lars Noodén on 2015-06-01
> **sarang3 said:**
> 2) I wish to make GUI apps

Qt will make that a lot easier.  It is cross-platform and used by many major applications.  It is in the repository and it uses C++ but there are bindings for Python as well as a few other languages.

---

### Post by sarang3 on 2015-06-01
Sir, Last question,
Is there any difference between QT C++ programming for WINDOWS AND LINUX?
Like, for Linux the structure of the program or writing style of the program will change, in comparison to Windows?
I have got a playlist in youtube. The guy performed the programming in Windows.
Will it be same for Linux?

---

### Post by ofnuts on 2015-06-01
> **sarang3 said:**
> Sir, Last question,
Is there any difference between QT C++ programming for WINDOWS AND LINUX?
Like, for Linux the structure of the program or writing style of the program will change, in comparison to Windows?
I have got a playlist in youtube. The guy performed the programming in Windows.
Will it be same for Linux?

It depends on what GUI framework is used. Some frameworks such as Qt or GTK have Linux and Windows versions, others are Windows-only.

Otherwise the fundamentals of GUI programming are the same everywhere (event loop, event handling, threading), even if some languages and/or frameworks can make things easier, so what you learn with a given language+framework can be re-used with another language-framework pair.

---

### Post by dwhitney67 on 2015-06-04
In a typical day at work, I have to program in C++, Java and Bash.

On rare occasions, I have to develop/maintain Windows command-script.  On other occasions, develop in Python and JavaScript.  On rarer occasions, I have to deal with Perl.

---

### Post by cyberslayer on 2015-06-05
> **sarang3 said:**
> Hi,
I have been learning SHELL SCRIPTING since 3 months, and I will soon learn the advanced shell scripting. 
I also have the knowledge of Java Core.
But I wanted to know, which programming language should I learn which will help me to write Programs after I get job in any company. I read in few threads that C++ and Python are good.
My queries are:
1) Which programming language should I go for first, C++ OR Python OR something you experts may suggest?
2) I wish to make GUI apps (front and backend BOTH), the same what is ASP.NET in Windows, so which books should I refer (the issue is that it should be available in India too) :p
3) Are there "playlists" available for the course I want to learn? (If yes, please give me the link)

I hope I was clear with my ques, please give me a detailed answer, in not very technical terms, since I am just a student who wants to learn. ):P

This question has been asked many times before in many places online.  What it boils down to is that there are many reasonable programming languages, and all of them have slightly different purposes.  You'll need to learn more than one (or even more than a few) if you want to become a serious programmer.  Which one you start with isn't particularly important IMO.  Just pick whatever interests you the most.

---

### Post by dwhitney67 on 2015-06-05
> **cyberslayer said:**
> This question has been asked many times before in many places online.  What it boils down to is that there are many reasonable programming languages, and all of them have slightly different purposes.  You'll need to learn more than one (or even more than a few) if you want to become a serious programmer.  Which one you start with isn't particularly important IMO.  Just pick whatever interests you the most.

Your answer sums up everything quite well.  If I can add one more thing, the OP should focus on becoming an expert (or learn for the first time) the programming language that his/her respective employer is expecting them to know, and for which they are **paying **him/her to know.

---

### Post by CptPicard on 2015-06-06
Native GUIs are overrated. Qt/GTK and C/C++ is a fair answer for that particular question if he really means that he wants to build native Linux GUI apps. An easier route is of course Python and its bindings to the windowing toolkits.

However, a lot of stuff happens on servers these days and if he wants to both use Linux and have a marketable skill, Java is not a bad answer at all, plus Javascript for the front-end development. The JVM is a very solid runtime that runs even other languages; I have been messing around with Clojure.

---

