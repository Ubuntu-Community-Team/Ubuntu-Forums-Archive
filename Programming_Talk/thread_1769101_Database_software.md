---
title: "Database software"
date: 2011-05-27
forum: Programming Talk
---

### Post by IAsolutions on 2011-05-27
I'm working in a personal project and I'm a begginer. I need some ideas for a software that I can use to develope a very simple database.

I have basic knowledge in html, c/c++

if there is something graphic would be great.

I'm working with ubuntu 11.04 and have access to a pc (just in case)

thanks for your help.

---

### Post by r-senior on 2011-05-27
Would MySQL be too big for your project? 

Has GUI administrator and query tools. Also runs on Windows and databases can easily be exported/imported between the two.

---

### Post by JupiterV2 on 2011-05-27
Just to be clear...are you designing a database, or you need to utilize one?

If you need to utilize one, SQLite is fantastic. Light and simple to use. If you want a client/server interface, then PostgreSQL or MySQL might be what you want.

If you are trying to design one, that gets more complicated. Are you just wanting to know what IDE, editor or compiler to use?

---

### Post by MBybee on 2011-05-27
> **JupiterV2 said:**
> Just to be clear...are you designing a database, or you need to utilize one?

If you need to utilize one, SQLite is fantastic. Light and simple to use. If you want a client/server interface, then PostgreSQL or MySQL might be what you want.

If you are trying to design one, that gets more complicated. Are you just wanting to know what IDE, editor or compiler to use?

Extra votes for SQLite. This is my go-to DB for little stuff. It's only real issue is concurrency. It has none :)

Firefox has a nice plugin to get a GUI for SQLite, btw.

---

### Post by juancarlospaco on 2011-05-27
SQLite

---

### Post by IAsolutions on 2011-05-27
SQLite sounds like is the option for now but basically I was looking for what editor/ compiler to use.

---

### Post by unknownPoster on 2011-05-28
> **IAsolutions said:**
> SQLite sounds like is the option for now but basically I was looking for what editor/ compiler to use.

If you have to ask that question, you may not be ready to develop applications that need database functionality.

The "standard" compiler for Linux is gcc (Gnu Compiler Collection) and code can be written in any text editor or ide of your choice.

---

### Post by IAsolutions on 2011-05-30
thanks everone your answers has been very helpful.

I wonder, according to unknownPoster, when I'll be ready to develop applications?? any ideas, any more useful comment?

---

### Post by unknownPoster on 2011-05-30
> **IAsolutions said:**
> thanks everone your answers has been very helpful.

I wonder, according to unknownPoster, when I'll be ready to develop applications?? any ideas, any more useful comment?

Well my comment was useful.

First, IDE is irrelevant as that's personal preference.

If you haven't chosen a "compiler" then you haven't chosen a language. 

You seem to have a lot of decisions to make before worrying about which database to use.

---

### Post by JupiterV2 on 2011-05-30
> **IAsolutions said:**
> thanks everone your answers has been very helpful.

I wonder, according to unknownPoster, when I'll be ready to develop applications?? any ideas, any more useful comment?

Well, that all depends on what you mean by "applications." Strictly speaking, the classic "Hello World" program is a simple application. If you define an application as having a GUI, database back-end and an embedded scripting language, then you have a ways to go.

The end result is:

1. You don't need an IDE. They're just a collection of tools which assist in the development process. You can write most, if not all, programs in a text editor. That said, they can be a very useful tool and can help speed up development.

2. You need a compiler if you're going to write a program/application in a compiled language. Tcl, Perl, Shell, Python, etc. can all be run from within a shell/interpreter.

I personally believe that if you choose to learn a compiled language like C, that you should write your first programs in a text editor and compile them by hand from a CLI. Then, once you understand the basics, you can move on to an IDE if you feel the need.

This is my personal opinion of course.

---

