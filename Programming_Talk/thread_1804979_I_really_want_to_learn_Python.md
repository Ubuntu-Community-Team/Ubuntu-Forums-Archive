---
title: "I really want to learn Python"
date: 2011-07-15
forum: Programming Talk
---

### Post by kyosa on 2011-07-15
I really want to learn Python, but I cant find out how to really learn it. I have read all the docs and done several tutorials, but still I can't figure it out.

If I try to make my own I don't know where to start and don't know what to write :)

Does any one have an idea/tip to give me. Does everyone struggle with this or is it something I have missed?

---

### Post by realzippy on 2011-07-15
Also tried [Python The Hard Way]("http://learnpythonthehardway.org/")?

---

### Post by kyosa on 2011-07-15
I will try it ;) 

I cant understand why I struggle so much wit this. I'm starting to think I'm stupid, but I hope not :=)

---

### Post by Arndt on 2011-07-15
> **kyosa said:**
> I will try it ;) 

I cant understand why I struggle so much wit this. I'm starting to think I'm stupid, but I hope not :=)

What other programming languages are you familiar with?

---

### Post by TwoEars on 2011-07-15
Well, 

1) Can you write algorithms? 
2) Do you understand the syntax?
3) Are you fine with reading the docs? 

If you can do all of these, you're on a good path. I'd be happy to provide private tutoring if needs be.

What is getting you stuck?
Deciding what problems are, or solving them?
Writing your solution in Python?
Making your scripts modular and into a project?

Python is one of the easiest languages to learn, as it is basically executable pseudocode. If you're getting stuck, it's probably because you can't work out an algorithm.

---

### Post by kyosa on 2011-07-15
> **Arndt said:**
> What other programming languages are you familiar with?
This is my first language that I try to learn, but I have worked with php, HTML,CSS and perl, but just making things to work if it had some problems, not making it my self.

Python is my first language and that I'm serious trying to learn, but I'm struggling to find out how to thing programming. I know what I want to do, but I cant figure out how to start writing code. 

Just a example:
I want to search for a string in a logfile and copy that line to a new logg and do a count how many times the string in last 7 days are in the new file. I really don't know how to start and should I have two scrip or just all in one. I'm totally lost. I have read a lot and watch movie on youtube and show me do, but still I feel that I have not learn anything.

---

### Post by kyosa on 2011-07-15
> **TwoEars said:**
> Well, 

1) Can you write algorithms? 
2) Do you understand the syntax?
3) Are you fine with reading the docs? 

If you can do all of these, you're on a good path. I'd be happy to provide private tutoring if needs be.

What is getting you stuck?
Deciding what problems are, or solving them?
Writing your solution in Python?
Making your scripts modular and into a project?

Python is one of the easiest languages to learn, as it is basically executable pseudocode. If you're getting stuck, it's probably because you can't work out an algorithm.
1) I have to say no
2) yes
3) I am

I would love to have you as a private tutoring, but I'm a fraid that you wold lose pation with me since am so blank it this. Maybe when I'm getting a bit better?

I see that all say it is easy learn and to be true that scare me, since I'm not able to mange it.

---

### Post by cgroza on 2011-07-15
> **kyosa said:**
> 
Just a example:
I want to search for a string in a logfile and copy that line to a new logg and do a count how many times the string in last 7 days are in the new file. I really don't know how to start and should I have two scrip or just all in one. I'm totally lost. I have read a lot and watch movie on youtube and show me do, but still I feel that I have not learn anything.

Well, when you start, stop thinking about the language. You must design an algorithm.
So, in your own words you must know which steps you must do.
For the above it would be:
```
Create a counter.
Read the file line by line and store the lines in a list.
While looping through the list of lines:
       check if the line matches your criteria:
                       if it matches, add 1 to the counter.
       if not, go to the next iteration.
Output the information.

```After this step in done, you must check the knowledge you need.
For this it would be:
What is a list.
How to open a file.
How to read a file.
How to parse a line of text.

After this step is done, all you have to do is express it in the language of your choice.

---

### Post by ruffEdgz on 2011-07-15
> **kyosa said:**
> I really want to learn Python, but I cant find out how to really learn it. I have read all the docs and done several tutorials, but still I can't figure it out.

If I try to make my own I don't know where to start and don't know what to write :)

Does any one have an idea/tip to give me. Does everyone struggle with this or is it something I have missed?

To answer your question at the top, I found it helpful to read up on it (which is always the first step to learning anything) but I always wanted to apply it so I found this site:

[http://codingbat.com/python](http://codingbat.com/python)

It was a nice site that allowed me to practice the parts of python I learned reading in an example from this site.

Hope this helps!

---

### Post by TwoEars on 2011-07-15
> **kyosa said:**
> 1) I have to say no
2) yes
3) I am

I would love to have you as a private tutoring, but I'm a fraid that you wold lose pation with me since am so blank it this. Maybe when I'm getting a bit better?

I see that all say it is easy learn and to be true that scare me, since I'm not able to mange it.

Well, in that case, you need to read some algorithm theory. I'm afraid I can't really suggest guides, most teach through x language.

---

### Post by JupiterV2 on 2011-07-15
I wonder what it is that you "don't get?" First off, did you take notes? Whenever I learn a new language I get a notebook and make notes. I usually use tabs to mark off sections and number them, with an index on the first page, so I can go back at any time. Sometimes, writing things in your own words helps retention. From there, start something small. I'm not talking a project. Try an reproduce something from scratch you saw in the tutorial, without using any references. Even a "hello world" program. Keep building on those blocks and eventually you'll get it. Remember, work smarter, not harder.

---

### Post by StephenF on 2011-07-15
Write small programs. Test what you have learned. More play, less reading. 

Programming is something you need to do in order to learn.

---

### Post by kyosa on 2011-07-16
Thank you so much for all your input. I will start on what you all suggest and see how things are going forward. I know that I must invest a lot of time to Python, and that is no problem at all.

**My first project will be:**
I want to build a website that list up my server and application and tell me how many times they have been restarted the last week. I want to make a script that collect information from the log files on the server and application and move into a database that will be access from a website.

But first I need to make simple tings and try to get Python, but I hope one day that I can do this project :)

---

### Post by miguel.guasch on 2011-09-09
> **kyosa said:**
> I really want to learn Python, but I cant find out how to really learn it. I have read all the docs and done several tutorials, but still I can't figure it out.

If I try to make my own I don't know where to start and don't know what to write :)

Does any one have an idea/tip to give me. Does everyone struggle with this or is it something I have missed?

Best thing I ever discovered to learn python with was [www.learnpythonthehardway.org](www.learnpythonthehardway.org)

Helped lots.

---

### Post by GenBattle on 2011-09-09
> **kyosa said:**
> Thank you so much for all your input. I will start on what you all suggest and see how things are going forward. I know that I must invest a lot of time to Python, and that is no problem at all.

**My first project will be:**
I want to build a website that list up my server and application and tell me how many times they have been restarted the last week. I want to make a script that collect information from the log files on the server and application and move into a database that will be access from a website.

But first I need to make simple tings and try to get Python, but I hope one day that I can do this project :)

Focus on keeping it simple. work on it in parts; make a script to collect the information you need from the server log files. Then once it's working nicely, extend it to store the data somewhere, then extend it further to display the data on a web page. Do everything in stages. T

hink about how you will do each task; work on breaking things down to the smallest possible parts; eventually you'll have individual lines of code that you can write out. I usually write a program in english pseudocode comments first if i'm having trouble with it, then try and code each part just after the comment.

---

