---
title: "Idea for A Program"
date: 2013-04-07
forum: Programming Talk
---

### Post by Bresser on 2013-04-07
Okay, 
So here is my idea: I want to make a program that will watch a Powerpoint, write down the text inside that Powerpoint and use it to input the answers to questions. So... :
[LIST=1]
[*]Is it even possible?
[*]What language(s) would need to be used?
[/LIST]

---

### Post by hayden92 on 2013-04-07
Hi Bresser,

It is definitely possible but getting the program to be reliable and to gather the correct data might be a little tricky.
I had a quick go at pulling the text from powerpoints, and it's easiest if the powerpoint is converted to something easier to read (e.g. HTML).

If I were to do it, the program would convert the powerpoint into html, read the html and look for tags such as <h1> to gather text data. 
Store this information into a plain text file and then read off of that. It's possible in most languages (I would use c++) but you will need some system calls (to convert the files to different formats) that are specific to the program you use to convert the powerpoints.

---

### Post by schragge on 2013-04-08
Or you may use some ready-made converters from Ubuntu repositories like [ppthtml](http://manpages.ubuntu.com/manpages/precise/en/man1/ppthtml.1.html) or [catppt](http://manpages.ubuntu.com/manpages/precise/en/man1/catppt.1.html). The last tool outputs the contents of a PowerPoint presentation as plain text.

---

### Post by ofnuts on 2013-04-08
> **Bresser said:**
> Okay, 
So here is my idea: I want to make a program that will watch a Powerpoint, write down the text inside that Powerpoint and use it to input the answers to questions. So... :
[LIST=1]
[*]Is it even possible? 
[*]What language(s) would need to be used? 
[/LIST]


The cynic in me says he has never seen any answers in a Powerpoint presentation :)

The pragmatic and ex-colleague of people working in that field says the text in a Powerpoint is much too short and telegraphic to extract any meaningful content. 

At best you can make a program that extracts "sentences", and tries to guess the important words in questions (ie, remove articles/prepositions...) and output sentences that contain {all|one of} the remaining words. Going further than this requires a thesaurus (so that if you are asked about vehicles, you can find sentences about cars), language models ("Poor Rich!"), and bit more programming expertise. 

Start with Python.

---

