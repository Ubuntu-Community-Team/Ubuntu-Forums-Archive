---
title: "PHP Code to C++"
date: 2008-08-06
forum: Programming Talk
---

### Post by Neon612 on 2008-08-06
I've got a few files linked together in PHP that output an xml file of what mp3 files are in the selected folder. I'd like to either convert these files to c++ code or find something that does the same thing.

---

### Post by LaRoza on 2008-08-06
> **Neon612 said:**
> I've got a few files linked together in PHP that output an xml file of what mp3 files are in the selected folder. I'd like to either convert these files to c++ code or find something that does the same thing.

Then rewrite it in C++...

There isn't an automated way to do this.

---

### Post by Neon612 on 2008-08-06
I know I need to rewrite it. I heven't done any PHP coding and my C++ is limited. (I've only be working on and off with it for the past month.)

---

### Post by LaRoza on 2008-08-06
> **Neon612 said:**
> I know I need to rewrite it. I heven't done any PHP coding and my C++ is limited. (I've only be working on and off with it for the past month.)

So this is just an annoucement? What is the question?

If you need tutorials, check out my wiki.

---

### Post by dwhitney67 on 2008-08-06
> **Neon612 said:**
> I've got a few **files** linked together in PHP that output an xml **file** of what mp3 **files** are in the selected folder. I'd like to either convert these **files** to c++ code or find something that does the same thing.
I am confused at to what you mean by "files".

What is it that you want?  Have you tried solving the problem on your own?  If you have an initial thought on how to solve the "problem", please let us know.  Otherwise, be terse, and simply spell out the requirements of your task.

Thank you.

---

### Post by Neon612 on 2008-08-06
> **Neon612 said:**
> I've got a few **php code** files linked together in PHP that output an **xml file** of what **mp3 files** are in the selected folder. I'd like to either convert these **php** files to c++ code or find something that does the same thing.

I've fixed my previous post a bit. for those of you who want more specific information.

---

### Post by LaRoza on 2008-08-06
> **Neon612 said:**
> I've fixed my previous post a bit. for those of you who want more specific information.

That would be everyone ;)

That sounds trivial to do. What is the dtd/schema of the XML.

Why does it have to be in C++?

---

### Post by escapee on 2008-08-06
Ya...no offense but it's still not helping.  What is your question?

---

### Post by Neon612 on 2008-08-06
My purpose is to convert three php files (xxx.php) to their equivilent c++ (xxx.cpp) codings.

The XML file is supposed to look through a directory, find any MP3 files in it and add them to the XML file. Which will then be read by an online flash music player.

---

### Post by dwhitney67 on 2008-08-06
I hate to tell you this, but XML is merely a format that is used to encapsulate ASCII data sent between two systems/processes.

An XML file in itself cannot "do" anything.

Thus, from what I understand, you want an application (preferably in C++??) to read the contents of a directory (perhaps recursively delving into sub-directories??) to populate an XML file with filenames that have the .mp3 extension.

Is this correct?

---

### Post by Neon612 on 2008-08-06
Close. It will get the file names as well as their ID3 data. (title,album, genre...)

---

### Post by pmasiar on 2008-08-07
Looks like XML is some kind of description of the files? XML is data markup format, not a programming language.

IMNSHO you will be much better off (and done faster) doing it in Python. ElementTree is excellent XML parser. And there is no automatic way to convert PHP to C++, as you know by now -- and why C++? Is it some kind of voodoo to you? Python is closer to PHP than C++ is.

---

### Post by LaRoza on 2008-08-07
I suggest you (OP) read the "How to ask questions" link in pmasiars sig ;)

Answer these questions:

[list]
[*] What do you want of the forum members? (Do you want help learning, suggestions for tools, etc)
[*] What do you want to do and **why**?
[*] Exactly what does the php do, where does it do it (server?), and what is done with the output?
[*] What is the DTD or schema of the XML?
[/list]

---

