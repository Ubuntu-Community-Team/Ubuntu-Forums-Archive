---
title: "Android - Develop UI programmatically or with XML"
date: 2011-12-28
forum: Programming Talk
---

### Post by PaulM1985 on 2011-12-28
Hi

I am having my first dabble with Android development and I am looking to port across a desktop app I made in Java.  

I have found that UI development in Android is very different and I wondered what people thought.  There are loads of tutorials for creating UIs with XML, but since it is so different compared to what I am used to, I am wondering what exactly is the advantage of it.  Alot of the tutorials seem to point to programmatic interfaces being "to hard to maintain", but can't this equally apply to XML?

Paul

---

### Post by ofnuts on 2011-12-29
> **PaulM1985 said:**
> Hi

I am having my first dabble with Android development and I am looking to port across a desktop app I made in Java.  

I have found that UI development in Android is very different and I wondered what people thought.  There are loads of tutorials for creating UIs with XML, but since it is so different compared to what I am used to, I am wondering what exactly is the advantage of it.  Alot of the tutorials seem to point to programmatic interfaces being "to hard to maintain", but can't this equally apply to XML?

PaulOne advantage of XML is that it is a lot easier to have several versions of your interface as resource files and to pick the best one at run time.

---

### Post by KdotJ on 2011-12-30
XML, all the way, 100%

There are many advantages, one of the biggest is that as stated you can have multiple layouts. For example, a layout for a medium size screen, a tablet screen, different layouts for portrait and landscape.. Your app will pick the right one to use. You can add new one as needed and edit the layouts without going back to change your code.. which is always painful.

---

### Post by a9bejo on 2011-12-30
Hi, welcome to Android development. 

I strongly recommend you study the source code for a simple but well designed project first. This is by far the fastest way to learn how to best structure your code and how to solve common problems.

Here is an app from a google engineer that was made for exactly this purpose:

[http://code.google.com/p/iosched/](http://code.google.com/p/iosched/)

Study the tutorials and do your own project and all that. But also keep the source code close by at all times.

---

