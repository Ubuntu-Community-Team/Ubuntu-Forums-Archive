---
title: "python Interview Questions"
date: 2007-10-30
forum: Programming Talk
---

### Post by krypto_wizard on 2007-10-30
Hi,

I have used Python for a couple of projects last year and I found it extremely useful. I could write two middle size projects in 2-3 months (part time). Right now I am a bit rusty and trying to catch up again with Python.

I am now appearing for Job Interviews these days and I am wondering if anybody of you appeared for a Python Interview. Can you please share the questions you were asked. That will be great help to me.

Thanks,

---

### Post by dataw0lf on 2007-10-30
> **krypto_wizard said:**
> Hi,
I am now appearing for Job Interviews these days and I am wondering if anybody of you appeared for a Python Interview. Can you please share the questions you were asked. That will be great help to me.

Thanks,

I interview potential Python programmers every couple months ( I manage 3 teams).  Generally, I try to stay away from language semantics and focus on general programming techniques (which, when it comes to Python, is tit for tat).  What type of position are you applying  for, and what's the focus in?  This usually matters more to an interviewer than the language used itself.

---

### Post by pmasiar on 2007-10-30
In library they should have books about what to expect on interview, how to behave, what to ask, what to answer. Non-technical questions are more important - technology anyone can learn, given time. Attitude is harder to change.

---

### Post by hecato on 2007-10-30
mmmm, haha, I have been in interview, specifically trying to find one where I can use/apply python.
In fact here where I live there are 3 or 4 places where you can search for job, I have search for python and only found like 3, 2 of them mainly "oh, is good if you know: C, C++, java, bash, python, perl,...", I have been in an interview in a place that deploy for mobile apps, they have sayed tht they use python with django for do portals (dont know if for mobile), but so far so good, is the only interview where they actually say me that they use python for some. The majority of works are for java, C#, and less C/++ and others.

By the way, they haven't asked me nothing about python, only say me that they have a page right now, and that perhaps I can enter to "investigation" that is more like "you will resolve any in any language that is present, including python, java, C++ (BREW), and things like that".

---

### Post by krypto_wizard on 2007-10-30
> **dataw0lf said:**
> I interview potential Python programmers every couple months ( I manage 3 teams).  Generally, I try to stay away from language semantics and focus on general programming techniques (which, when it comes to Python, is tit for tat).  What type of position are you applying  for, and what's the focus in?  This usually matters more to an interviewer than the language used itself.

I am applying to a start up that builds new generation networking solutions using optical networks. They do lot of coding in Python along with C and C++. The company liked my background in network but want me to undergo a Python interview test as that is what I will code in. I am catching up again with Python.

My motive here was to get a good glimpse of good interview questions for Python. For example if you search for C Programming Interview questions,  then there is a set of say 100-200 questions which are asked more often than other parts. So I was trying to see if any body here had any interview experience in Python.

All your responses are greatly appreciated.

Thanks.

---

### Post by krypto_wizard on 2007-10-30
> **dataw0lf said:**
>   Generally, I try to stay away from language semantics and focus on general programming techniques (which, when it comes to Python, is tit for tat). 

What are some of the most common and basic questions would you ask someone to test if that candidate has basic knowledge of Python ? I appreciate your response.

---

### Post by dataw0lf on 2007-10-30
Ah, that makes more sense.  Well, look over the socket module, and familiarize yourself with general socket programming.  When I test specifically on Python knowledge, here are the general modules that I cover (along with general Python semantics - duck typing, list comprehensions, immutable versus mutable, etc):
 sys, os, time, re, string, random, threading, socket, os.path, and types.  These are, in descending order, the most commonly occuring modules in the Python package.

Overviewing [http://www.diveintopython.org/](http://www.diveintopython.org/) may be a good idea too;  it tends to focus on Python specific idioms, which will most likely be the focus of the test.

I'd also ask if they do any sort of unit testing, and which module they use if they do, and familiarize yourself with it.

---

### Post by krypto_wizard on 2007-10-30
> **dataw0lf said:**
> Ah, that makes more sense.  Well, look over the socket module, and familiarize yourself with general socket programming.  When I test specifically on Python knowledge, here are the general modules that I cover (along with general Python semantics - duck typing, list comprehensions, immutable versus mutable, etc):
 sys, os, time, re, string, random, threading, socket, os.path, and types.  These are, in descending order, the most commonly occuring modules in the Python package.

Overviewing [http://www.diveintopython.org/](http://www.diveintopython.org/) may be a good idea too;  it tends to focus on Python specific idioms, which will most likely be the focus of the test.

I'd also ask if they do any sort of unit testing, and which module they use if they do, and familiarize yourself with it.

Thanks for your help. I think they use twisted network library in their work a lot. May be I should glance through it before the interview.

---

### Post by dataw0lf on 2007-10-30
> **krypto_wizard said:**
> Thanks for your help. I think they use twisted network library in their work a lot. May be I should glance through it before the interview.

That's probably a good idea, but if you're iffy on general Python, I'd focus on that much more.  They'll be willing to guide you through the Twisted libraries if you prove you have a good grasp of the general Python language.

---

