---
title: "What is mkvinfo's output format?"
date: 2010-05-31
forum: Programming Talk
---

### Post by Jerrac on 2010-05-31
I'm playing with writing a python script to convert mkv files to some other format. One task I need to do is read the output from mkvinfo and find out what track is what. 

So, is the output from mkvinfo is a specific format that python has a function it can use to parse it?

fyi, I am new to python. This is halfway meant to teach me more about programming in python.

If there isn't a parsing function, I'll just use regular expressions, or something.

Attached is some example output from mkvinfo.

---

### Post by Redache on 2010-05-31
From what I can tell that file is just a plain text file with mkvinfo's own data structure.

You would have to write your own parser to traverse that file. I'd start with learning how to replace the "+" in the file whilst it's being fed into Python. 

I recommend you target the parts of the file that you actually need then write a parser that pulls the relevant information out of the file and stores it.

---

### Post by Jerrac on 2010-05-31
Hmm... Ok, I thought it might be that.

Thanks for the response.

---

