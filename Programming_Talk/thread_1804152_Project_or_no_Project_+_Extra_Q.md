---
title: "Project or no Project? + Extra Q?"
date: 2011-07-14
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-07-14
Alright Im making this question cause im very confused.

I was seeing some tutorials, and on those tutorials people use **Projects**, but I dont like to.

- Is really needed for Programing?


Now I have another problem related to the below and is that I have seen on some tutorials that they use 2 **.cpp** files.

- How Im supposed to compile that?

- Its not the same if I use headers instead?


Thank you for your help.

---

### Post by megabytemonster on 2011-07-14
Projects are a feature of many IDE's (Integrated Development Environment, such as Eclipse or Visual Studio). They're not necessary for programming, just convenient (all your files are grouped together, and other features).

When you split up your code into multiple files, you usually have one file (containing the main function) which references the others (through include statements or whatever), so you just need to compile that one.

Header files are often used in C++/C, but they're not mandatory. You can place the same information directly into a .cpp file and then have the class definition immediately below.

---

