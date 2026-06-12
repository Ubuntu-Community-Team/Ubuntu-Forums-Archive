---
title: "JSP alternatives"
date: 2008-10-26
forum: Programming Talk
---

### Post by tashe on 2008-10-26
I'm trying to learn some JSP lately, mainly because I've read in some tutorials that it goes nice with Java (the language I currently use, besides Macedonian :)). I want to learn JSP because combined with Java and a database I can create a web app for the use of the database (2-3 users). But I'm little dissapointed lately cause I find the JSP syntax confusing.
Do you think it is worth learning JSP, or is it better to try with PHP or Swing in Java?
thanks in advance

---

### Post by CptPicard on 2008-10-26
> **tashe said:**
> 
Do you think it is worth learning JSP, or is it better to try with PHP or Swing in Java?


Umm... I have no idea how you it would even be possible to use PHP with Java... and Swing is a desktop GUI toolkit, it has nothing to do with web applications.

JSP pretty much is *the* view technology in Java web apps so it's certainly worth learning... then there are alternatives such as Velocity templates. A lot of frameworks have their own view markups too.

---

### Post by tashe on 2008-10-26
But I've read that in newer editions Java will be used less and less for scripting. Isn't that a negative thing to start right form the start?

---

### Post by CptPicard on 2008-10-26
I really don't understand what you mean... JSPs compile into servlets, which are basic building blocks of Java web applications...

---

### Post by drubin on 2008-10-26
> **tashe said:**
> I'm trying to learn some JSP lately, mainly because I've read in some tutorials that it goes nice with Java (the language I currently use, besides Macedonian :)). I want to learn JSP because combined with Java and a database I can create a web app for the use of the database (2-3 users). But I'm little dissapointed lately cause I find the JSP syntax confusing.
Do you think it is worth learning JSP, or is it better to try with PHP or Swing in Java?
thanks in advance

Your needs are small and fairly light weight I would go for the php approach. You might find the syntax more to your liking.  

But as for a learning exprience defiantly try and see what you can get going.

---

### Post by CptPicard on 2008-10-26
Oops, I misread the original post... you were not trying to use "PHP with Java" :)

Then again, Swing still has nothing to do with web apps.

I really wouldn't advice PHP in any case though... if you want some lightweight web app development, check out Python and TurboGears or Django.

And, really, if you are comfortable with Java, JSP still *is* something you want to know if you ever will write Java web apps... and with something like JSTL taglibs and a proper editor such as found in Netbeans it's not all that bad.

---

### Post by drubin on 2008-10-26
> **CptPicard said:**
> I really wouldn't advice PHP in any case though... if you want some lightweight web app development, check out Python and TurboGears or Django.


I would not consider having to use those frameworks lightweight. 

But yes try to get the jsp thing working for you.

---

### Post by pmasiar on 2008-10-26
> **drubin said:**
> I would not consider having to use those frameworks lightweight.

It depends on your definition in "lightweight" - and compared with Java, it's easy to be "lightweight" 8-)

More important, both Django and Turbogears are clean systems using [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) design patters, while JSP is as messy as PHP. For small projects it makes little difference, but for real projects it does make a difference.

For beginner, I would recommend Django, which comes with automagicakky generated data admin interface, object-relation mapper, and other goodies. That's before mentioning Python, superior in these tasks to both PHP and Java. 8-)

---

### Post by CptPicard on 2008-10-26
> **pmasiar said:**
> 
 while JSP is as messy as PHP.

Strongly disagreed -- you really really are not supposed to code your app as JSPs, but to use servlets as controllers and then just pass data structures to the JSP for rendering... as you well know :)

---

### Post by pmasiar on 2008-10-26
> **CptPicard said:**
> Strongly disagreed -- you really really are not supposed to code your app as JSPs, but to use servlets as controllers and then just pass data structures to the JSP for rendering... as you well know :)

Yes, and I do it in my day job in Struts, but I would never consider such usage of JSP replaceable with PHP. If someone does, it hints me that such person lacks understanding of MVC pattern, and why it is "right" way to code.

And Java sucks in text processing anyway, big time, in no way I would consider it "scripting" language, so...

---

### Post by tashe on 2008-10-27
I'll give JSP a try. It is messy, but if it's needed when I'm going to look for a job after university, then no doubt I'll try to learn it.
My original idea with this thread was to ask if there were any alternatives to JSP. But after your answers it seems that I should be patient with it.


I'm sorry, I wrote scripting with Java cause thats the way it was called in the book, when you insert Java in JSP.

thanks for the time you spent answering my question :)

---

### Post by CptPicard on 2008-10-27
> **tashe said:**
> 
I'm sorry, I wrote scripting with Java cause thats the way it was called in the book, when you insert Java in JSP.


Which is exactly the bad habit with JSPs you should avoid. Don't use scriptlets (the <%  %> ones) unless you absolutely must. I suggest you read up in JSTL tags ASAP to get into proper design patterns...

---

### Post by tashe on 2008-10-27
Then if i dont use them, is there any other way to use java code with jsp?

---

### Post by CptPicard on 2008-10-27
Well, do you really need to use Java code *in* your JSPs?

I mean, you can if you absolutely have to, but that has been bad form since the 90s... :)

Learn about the Model-View-Controller pattern and how that applies to servlets and jsp pages... in modern JSPs you use JSP tags which extract stuff from the page context into your page markup.

---

