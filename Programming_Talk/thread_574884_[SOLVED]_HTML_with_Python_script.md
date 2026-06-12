---
title: "[SOLVED] HTML with Python script"
date: 2007-10-13
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2007-10-13
I was wondering if I can use python scripts like java scripts, in xhtml page?

---

### Post by Smygis on 2007-10-13
Nope. You cant.

---

### Post by DamjanDimitrioski on 2007-10-13
What other scripting languages for xhtml, other then php, java, asp, are there in the world?

---

### Post by DamjanDimitrioski on 2007-10-13
Also I can't understand this beans system, how it works?
Give me link

---

### Post by Smygis on 2007-10-13
> **DamjanDimitrioski said:**
> What other scripting languages for xhtml, other then php, java, asp, are there in the world?

As far as i know, Only JavaScript.

ASP, Java, PHP, Ruby (on Rails), Python, Perl and so on all work on the server side of things. ;)

---

### Post by DamjanDimitrioski on 2007-10-13
That was what I needed, thanks.

---

### Post by pmasiar on 2007-10-14
There is one neat templating system, kid, which allows you to use python (and template-side functions) in XML to generate HTML. But as previous poster said, only javascript runs in your browser.

If you do web apps, you are much better off (after trying it to do it by hand, and struggling a lot or failing) to use established web app framework. Django is "pronounced" by Guido as official, and has plenty of support and docs, but I like Turbogears more, because it is more flexible.

Why you neeed to run Python in browser? To validate input?

There is one "small" (so i mean, BIG and ugly) problem with running any javascript for validating user's input by javascript on client (browser): you cannot trust user, so you need to do exactly same validation on server again, and because you don't code server in javascript, you have to do it in different language. So if you ever seen opened can of worms, you know this is it.

There is one interesting AJAX library, ZK, which runs javascript in browser and reports all events back to the server, which can process them (in Java) by exactly came classes which will be used later to validate use's input, and passes results back to client. Very neat!

---

