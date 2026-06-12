---
title: "How do I get the gambas drawingarea control"
date: 2013-11-09
forum: Programming Talk
---

### Post by Tom_Carr on 2013-11-09
I just installed gambas2 from the ubuntu software center.  I found documentation about a drawingarea control here
[http://en.wikibooks.org/wiki/Gambas/Graphics](http://en.wikibooks.org/wiki/Gambas/Graphics)
But it does not show up in my toolbox.  Do I have to add it?  If so how?

One other gambas question.  I see there is a gambas 3, but the version in the  ubuntu software center is gambas2.  Why?

---

### Post by kalaharix on 2013-11-10
The Gambas wiki refers to Gambas3. Gambas2 has not been updated for some time.

I will give you my take on why Gambas3 is not in the Ubuntu Software Centre: It will not get into The Ubuntu Software centre if it is not in parent Debians repository. Debian is a very conservative distribution. Gambas is very active and constantly updated. Many of the dependencies that Gambas3 requires are newer than those used by Debian. Attempts have been made over the years to incorporate Gambas3 in to the Debian repository (an attempt is being made at the moment) but it is apparently a lot of work.

Paradoxically, it is relatively easy to install Gambas3 on Ubuntu and derivatives by specifying a software source from within the Gambas community. There are currently two software sources for Gambas3: one for the stable release and another for the daily build. There are many instructions on the web using these sources. One set that I have written is at 

[http://kalaharix.wordpress.com/]("http://kalaharix.wordpress.com/")

I have just used these instruction s to install Gambas3 on a fresh install of Lubuntu 13.10 and know it works on Ubuntu 13.10. Somebody has commented on the blog that it works on Mint 15. Many non-Debian derived distributions already have Gambas3 in their repositories.

Gambas3 is well worth the effort and remains, to my mind, the finest application for data manipulation in Linux.

---

### Post by Tom_Carr on 2013-11-10
Thanks for the info klaaharix.  I am running ubuntu 12.04.  Do you have any idea if Gambas3 will work on ubuntu 12.04?

---

### Post by Tom_Carr on 2013-11-10
I see from your blog that you installed gambas3 on ubuntu 12.04  in April 2012.  I will remove gambas2, follow your instructions, and see what happens.   I will do that later this afternoon, so if you have any advice, I will read it here.

---

### Post by Tom_Carr on 2013-11-10
kalaharix, I used the instructions in your blog and installed gambas3.  It works much better.  Thanks.
I am going to start a new thread on general gambas questions, because I have lots of them.

---

