---
title: "New to programming and I am looking for a starting point"
date: 2014-10-28
forum: Programming Talk
---

### Post by bryan.sailer on 2014-10-28
I have been given a list of requirements for an attendance application and I am stuck with where to start. The requirements are that the program must have access to a database, be able to generate reports, have the ability to incorporate a touch screen so that parents can check their children in and out with code while at the same time still utilize a bar code reader that is currently being used. Can some one please provide me with a starting point and a direction. This is my first program I will have built for actual use. I have only programmed small lines of code to make objects appear on a screen and small lines of code like that. 

experience beginner
Linux user since 2009

---

### Post by flaymond on 2014-10-28
I prefer you to use Java as your first platform or...for more powerful and much more fill your requirements..try C++ as your platform to build such programmes....and make sure you got Eclipse for better IDE (get Java JDK and SDK because eclipse need to run with those)

---

### Post by bryan.sailer on 2014-10-28
Thank you, I will start there and see what I can put together.

---

### Post by ofnuts on 2014-10-28
> **bryan.sailer said:**
> I have been given a list of requirements for an attendance application and I am stuck with where to start. The requirements are that the program must have access to a database, be able to generate reports, have the ability to incorporate a touch screen so that parents can check their children in and out with code while at the same time still utilize a bar code reader that is currently being used. Can some one please provide me with a starting point and a direction. This is my first program I will have built for actual use. I have only programmed small lines of code to make objects appear on a screen and small lines of code like that. 

experience beginner
Linux user since 2009

Use of a touch screen should be transparent to you, since for most purposes and with the proper drivers, the touchscreen will behave like a mouse and you will get mouse clicks in your application.

First thing to do, before writing code, is to think about a "data model", ie, how you are going to relate parents, children and whatever they are suppose to attend to, and what the corresponding database structures are going to be. You should also wonder about why/how/by whom this data can be changed (so called "use cases"). Very often, a "use case" ends up being a dialog,  a sequence of dialogs (aka "wizard"), or a button on a dialog (data common to several use cases)). Data model and use cases are two sides of the same thing, so in the beginning, changing one often leads to change in the second (which is why you shouldn't invest too early in the code otherwise you are going to throw away a lot of it).

---

### Post by bryan.sailer on 2014-10-28
ofnuts,
Thank you for the advice because I sure would have just jumped right into the process. I am unfamiliar with C++, do you have a reference that I can use to help me get started. I have the ideas in my head of what I want it to look like and how I would like it to function. I am planning on utilizing a SQL database. Also, a good practice for putting together a data model.

---

### Post by flaymond on 2014-10-31
You need to get C++ 'special IDE' to make your programming easier. Try codeblock from the ubuntu software center....C++ is amazing programming language especially in 'deep computer' and amazingly good to know about memories and codeblocks. Also, you need some basics about Bash Scriptings (Unix shell) to manage your files and programmes through the terminal with ease. Fortunately, you can find tutorial about Bash and C++ on Internet. I hope that help! and if you want graphic designing (3D) try download Blender. Its a good freeware.

---

### Post by SagaciousKJB on 2014-10-31
Interesting thread.  Does Java really have the hardware interface support to make use of touch screens and figner print readers though?  I figured that would require something lower level like C/C++

Most languages have pretty good support for database interface.  PHP is probably one of the more well-documented types with the most resources available for studying it and getting started with it.  But I don't really have a lot of software engineering experience, I just TRY to code in C sometimes lol

---

### Post by ofnuts on 2014-10-31
> **SagaciousKJB said:**
> Interesting thread.  Does Java really have the hardware interface support to make use of touch screens and figner print readers though?  I figured that would require something lower level like C/C++

Most languages have pretty good support for database interface.  PHP is probably one of the more well-documented types with the most resources available for studying it and getting started with it.  But I don't really have a lot of software engineering experience, I just TRY to code in C sometimes lol

C/C++ don't talk to the hardware either... and in most cases when there is a touchscreen the driver just creates the standard mouse events that Java will handle completely transparently.

---

### Post by coldraven on 2014-10-31
In the UK you would probably have to comply with the Data Protection Act which would mean that the database is encrypted. Especially if children's identities are involved. Big penalties are incurred if their names and address' are leaked out.
Maybe someone can give you pointers to implement that sort of encryption and who is allowed to access the data.

---

