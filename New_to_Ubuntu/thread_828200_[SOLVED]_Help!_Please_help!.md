---
title: "[SOLVED] Help! Please help!"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by neurostu on 2008-06-13
I was messing around with the tracker-applet, and I clicked an option that says "Hide applet/icon when indexing". I clicked ok and now the applet is gone. I can't figure out how to get it back. I'd like to continue to mess with the settings but I can't figure out how to get it to show up again...

I've tried running:
```

tracker-applet

```
in the terminal but it doesn't work...


please help!

---

### Post by gr4nf on 2008-06-13
where was it? wherever it was, use the command:
```

ls -a

```
on the directory, and you should be able to find it.

---

### Post by KingTermite on 2008-06-13
For the love of God...please stop using titles like "help, please help". It conveys NOTHING about the problem.

---

### Post by neurostu on 2008-06-13
> **KingTermite said:**
> For the love of God...please stop using titles like "help, please help". It conveys NOTHING about the problem.

Your exactly right... but my last 5 threads have had no responses, or reads (I Presume b/c people were scared by the title?).  I've decided that the more I act like a noob the more likely someone who knows the answer will read and post a response.

---

### Post by neurostu on 2008-06-13
> **gr4nf said:**
> where was it? wherever it was, use the command:
```

ls -a

```
on the directory, and you should be able to find it.
Its an applet that is visible when tracker is indexing....  the applet is running but it isn't visible. Even when I run the applet from the terminal it doesn't show up.

---

### Post by phr0ze on 2008-06-13
> **neurostu said:**
> Your exactly right... but my last 5 threads have had no responses, or reads (I Presume b/c people were scared by the title?).  I've decided that the more I act like a noob the more likely someone who knows the answer will read and post a response.

That's just rude. 'I don't get what I want so I'm going to act like a baby.'

I wish I had an answer for your tracker problem. I do like to help. But someone who's been on the boards for a while shouldn't do this on purpose.

---

### Post by ktechman on 2008-06-13
Have you tried to restart X?

---

### Post by neurostu on 2008-06-13
> **phr0ze said:**
> That's just rude. 'I don't get what I want so I'm going to act like a baby.'


I guess you're right... 

I find that these boards really cater towards getting people going with ubuntu, which can be frustrating as I'm past that point and I find I put in more then I get out, I guess its time to move to another forum...

---

### Post by neurostu on 2008-06-13
So luckily an error message just popped up on tracker-applet so I could change the pref..

No I'll cower in shame at the mistake I made.... (referencing the title of this thread)

---

### Post by KingTermite on 2008-06-13
> **neurostu said:**
> Your exactly right... but my last 5 threads have had no responses, or reads (I Presume b/c people were scared by the title?).  I've decided that the more I act like a noob the more likely someone who knows the answer will read and post a response.

I see your point...but a more detailed titled will get the attention of those whose expertise are in that area.

---

### Post by wootah on 2008-06-13
> **neurostu said:**
> I guess you're right... 

I find that these boards really cater towards getting people going with ubuntu, which can be frustrating as I'm past that point and I find I put in more then I get out, I guess its time to move to another forum...

Alright, none of that now :)

It looks like you are looking for **tracker-search-tool**.

from apt-cache:
> 
Description: metadata database, indexer and search tool - GNOME frontend
 This package provides a graphical Tracker search tool for GNOME.
 .
 Tracker is an advanced framework for first class objects with associated
 metadata and tags. It provides a one stop solution for all metadata, tags,
 shared object databases, search tools and indexing.
 .


Try running that perhaps ?

You can also **tracker-preferences** and maybe you can make it not hide itself :)

---

### Post by phr0ze on 2008-06-13
Hey, I've found exactly the same problem with these boards, once you move past the 'X wont start', 'can't play flash', 'is ubuntu better than windows' types of questions, there is nothing left but to just answer those same questions for the next guy. I've asked several intermediate questions and I got no response either. I find in some cases it's better to try launch pad or google.

I went back and looked at some of your earlier unanswered posts. I think if you posted 'Help Me' on those titles you still would not get an answer, but you would take time from people who could be answering something else. 

The boards here are real friendly but they seem to lack a level of expertise. In fact, I've talked with a couple of ubuntu developers and 'managers' and they all told me they never get on the forums. 

I've been meaning to bring up the issue somehow so this might just be it. I'm sure now that I've said this we'll get a lot of experts to suddenly appear to comment.

---

### Post by wootah on 2008-06-13
> **phr0ze said:**
> Hey, I've found exactly the same problem with these boards, once you move past the 'X wont start', 'can't play flash', 'is ubuntu better than windows' types of questions, there is nothing left but to just answer those same questions for the next guy. I've asked several intermediate questions and I got no response either. I find in some cases it's better to try launch pad or google.

I went back and looked at some of your earlier unanswered posts. I think if you posted 'Help Me' on those titles you still would not get an answer, but you would take time from people who could be answering something else. 

The boards here are real friendly but they seem to lack a level of expertise. In fact, I've talked with a couple of ubuntu developers and 'managers' and they all told me they never get on the forums. 

I've been meaning to bring up the issue somehow so this might just be it. I'm sure now that I've said this we'll get a lot of experts to suddenly appear to comment.

I think it's more important to teach users the tools to figure out their problems. Granted, with advanced stuff, the experts are more likely to not be on the forums as they are probably off hacking a project and whatnot :(

---

### Post by neurostu on 2008-06-13
> **phr0ze said:**
> Hey, I've found exactly the same problem with these boards, once you move past the 'X wont start', 'can't play flash', 'is ubuntu better than windows' types of questions, there is nothing left but to just answer those same questions for the next guy. I've asked several intermediate questions and I got no response either. I find in some cases it's better to try launch pad or google.

I went back and looked at some of your earlier unanswered posts. I think if you posted 'Help Me' on those titles you still would not get an answer, but you would take time from people who could be answering something else. 

The boards here are real friendly but they seem to lack a level of expertise. In fact, I've talked with a couple of ubuntu developers and 'managers' and they all told me they never get on the forums. 

I've been meaning to bring up the issue somehow so this might just be it. I'm sure now that I've said this we'll get a lot of experts to suddenly appear to comment.

I love these forums, they have been great. I never would have been able to learn what I did without them... but i guess its time to move on...

---

