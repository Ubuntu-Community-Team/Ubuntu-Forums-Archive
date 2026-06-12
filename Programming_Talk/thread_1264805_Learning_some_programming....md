---
title: "Learning some programming..."
date: 2009-09-12
forum: Programming Talk
---

### Post by cocheese on 2009-09-12
Im starting to learn some programming and i've decided to have a goal in that i want a program to automatically organise my music into files by artist and album.
Ive dabbled in programming before with actionscript and c++ but ive forgotten most of it.
Which language should i be looking at using to make this program?
ive started reading some guide on python and that seems to be okay but its early days and i want to make sure i wont waste my time :)

---

### Post by JordyD on 2009-09-12
You can do this with any programming language that has a library for looking at ID3 tags (assuming your collection is MP3s, I'm not really sure what others use).

[Search results for "id3 tag library"]("http://www.google.com/#hl=en&source=hp&q=id3+tag+library&aq=0&aqi=g3&oq=id3+tag+lib&fp=6d02e072335ea48a")

---

### Post by phrostbyte on 2009-09-12
First you got to define the libraries (collection of routines) you will need:

Like JordyD said, you need to pull out the tag information from the MP3 file. This can be done using an ID3 library.

You also need the ability to manipulate files, this is probably part of almost every language standard library (the library that a language comes with).

So basically your code will look something like this

[LIST=1]
[*]Recursively access every MP3 file in a directory
[*]Pull ID3 tag information (artist, author)
[*]Rename file based on ID3 tag information
[/LIST]

This probably can be done in like 20 lines of Python. Good luck. :)

---

### Post by cocheese on 2009-09-12
sounds like fun. need to figure out all the details and whatnot but thanks. will get started

---

### Post by c0mput3r_n3rD on 2009-09-12
ProgramExtraction and Report Language (perl)l would accomplish this task nicely.

---

### Post by cocheese on 2009-09-13
okay well the question in that case is which is easiest to learn?

---

### Post by nvteighen on 2009-09-13
> **cocheese said:**
> okay well the question in that case is which is easiest to learn?
A hard question to answer... Though, IMO, Perl should be easier...

What I don't know is whether this project is something you can do to start programming... Ok, it's important to have a goal, but if you don't know anything, you'll be easily frustrated and you better start learning the basics of general programming. And for that, the best seems to be Python.

---

### Post by Copernicus1234 on 2009-09-13
Perl has a very awkward syntax so I would recommend Python. Ive never touched Perl because there is no reason when Python exists.

---

### Post by jacksaff on 2009-09-13
[http://www.gigamonkeys.com/book/practical-an-id3-parser.html]("http://www.gigamonkeys.com/book/practical-an-id3-parser.html")

Is a chapter from a very good book on lisp that walks you through pretty much exactly what you want. Not the quickest way to get started (much easier to use a ready-made lib) but it's well worth a read even if you have no interest in either writing the id3 parser or in learning lisp.

---

