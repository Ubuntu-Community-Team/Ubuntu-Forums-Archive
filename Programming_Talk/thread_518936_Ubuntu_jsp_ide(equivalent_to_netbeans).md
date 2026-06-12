---
title: "Ubuntu jsp ide(equivalent to netbeans?)"
date: 2007-08-06
forum: Programming Talk
---

### Post by Brendan Hart on 2007-08-06
hello 
Ubuntu jsp ide(equivalent to netbeans?)
is there one?

---

### Post by LaRoza on 2007-08-06
There is a linux version:

[http://www.netbeans.org/community/releases/41/install.html](http://www.netbeans.org/community/releases/41/install.html)

---

### Post by pmasiar on 2007-08-06
Java claims to be cross-platform, netbeans claims to be in java, so it would be funny if netbeans was not available on Linux, don't you think so?

Eclipse is another popular java IDE (for both Win and GNU/Linux)

---

### Post by ahvargas on 2007-08-06
You can use eclipse with the pulgin WTP.
[http://www.eclipse.org/webtools/main.php](http://www.eclipse.org/webtools/main.php)

---

### Post by ahvargas on 2007-08-06
also you can use this plugin for eclipse :[http://www.aptana.com/](http://www.aptana.com/)

---

### Post by AlexThomson_NZ on 2007-08-06
> **pmasiar said:**
> Java claims to be cross-platform, netbeans claims to be in java, so it would be funny if netbeans was not available on Linux, don't you think so?

Eclipse is another popular java IDE (for both Win and GNU/Linux)

I thought you were going to tell him to use python for a second there!

Seriously though, I think JSP editing is something that should be core functionality in apps like Netbeans and Eclipse, but I think is sorely lacking (I am not the only one [http://tersesystems.com/post/5400060.jhtml](http://tersesystems.com/post/5400060.jhtml)).  There are some good JSP plugins out there, but bugger having to pay for them!  And the ones that are free have not been too flash in my experience.

---

### Post by pmasiar on 2007-08-06
> **AlexThomson_NZ said:**
> I thought you were going to tell him to use python for a second there!


Why, Python is obviously superior, but OP is not ready to look for something better yet. Let him suffer with Java and JSP and Struts for a while, *then* OP  will be back asking for better, cleaner, more easier to maintain ways to write web apps, more compliant with [Model-View-Controller](http://en.wikipedia.org/wiki/Model_view_controller) approach instead of inevitable mess of JSP, and easier to understand than Struts. *Then* will be good time to mention Python/Django/Turbogears, but not sooner. :-)

Ooops, you made me to disclose my secret plans! But you have only yourself to blame for it! :-)

---

### Post by AlexThomson_NZ on 2007-08-06
> **pmasiar said:**
> Why, Python is obviously superior, but OP is not ready to look for something better yet. Let him suffer with Java and JSP and Struts for a while, *then* OP  will be back asking for better, cleaner, more easier to maintain ways to write web apps, more compliant with [Model-View-Controller](http://en.wikipedia.org/wiki/Model_view_controller) approach instead of inevitable mess of JSP, and easier to understand than Struts. *Then* will be good time to mention Python/Django/Turbogears, but not sooner. :-)

Ooops, you made me to disclose my secret plans! But you have only yourself to blame for it! :-)

LOL- true- we all have to pay our Java dues!  I wonder if that's why we don't see too many people moving from Java to RoR/python,etc.  "Well, after 5 years, I think I finally understand it!  No way am I moving to something else now!" :)

---

### Post by bribaetz on 2007-08-06
why java C++ or c or C# could be as good and to write java code takes twice as much time because java requires more coding

---

### Post by pmasiar on 2007-08-06
> **AlexThomson_NZ said:**
> LOL- true- we all have to pay our Java dues!  I wonder if that's why we don't see too many people moving from Java to RoR/python,etc.  "Well, after 5 years, I think I finally understand it!  No way am I moving to something else now!" :)

Exactly!

The only problem with this line of thinking is: even if most/all programming languages are equally [Turing-complete](http://en.wikipedia.org/wiki/Turing_complete) it does not mean that all of equally easy to code in. Fortunately my experience was in many other languages (most of them *much* worse than Java tho), and I learned Perl and then Python before decision was made to convert most/all internal development in our group to Java (and it was made 10 years too late if you ask me :-) ).

So I can see that if after 3 months of hard work i *still* don't get Struts, it is problem with Struts and not with me. And after looking through TurboGears.... nah, Java/Struts is now even more frustrating for me than before, because now I know *exactly* how much simpler it is in TurboGears.

But I am not surprised that many people are reluctant to switch to new languages after investing so much time to become reasonably skilled in one (ie Java). Your productivity in new language will be for some time less than in old one - and it is hard to foresee for how long it will be, where is the breaking point. 

[Bruce Eckel](http://en.wikipedia.org/wiki/Bruce_Eckel), well-know Java expert, is [typical case](http://mindview.net/WebLog/ArticleIndex): he says [I'm Over It](http://mindview.net/WebLog/log-0053) (over with static type checking) and in couple posts explains why (including implementing latent typing in Java):
[About Latent Typing](http://mindview.net/WebLog/log-0051), 
[Strong Typing vs. Strong Testing](http://mindview.net/WebLog/log-0025) 
[How to Argue about Typing](http://mindview.net/WebLog/log-0052)

and btw for all self-taught programmers around, Bruce himself admits he was self-taught: [How I got started in programming](http://mindview.net/WebLog/log-0030)

Every visit I will find copule more gems found in his posts: 
about [Incompetence](http://mindview.net/WebLog/log-0023) and research showing that "... the incompetent will tend to grossly overestimate their skills and abilities." (and the consequences for programmers).
[Productivity over Performance](http://www.artima.com/intv/prodperf.html) and how Zope, special web server in Python, can be faster than Apache, generic web server in C.

---

### Post by AlexThomson_NZ on 2007-08-06
// Getting slightly off topic here, but...

Personally, I have a love/hate relationship with Java.  While I LOVE the language syntax (coming from a C and C++ background, it just feels "right"), whenever I have to troubleshoot environmental problems (classpaths, etc.), or have to learn a new J2EE concept, all I can think about is "Goddamn, this sucks!".  But for the industry I'm in (very, very large scale, complex web applications)- there is no alternative

---

### Post by kknd on 2007-08-06
Python is good. But you will need to know other language if you need to do heavy calculations. For web it performance if OK.

I program mainly in Java, but my target aren't web.

---

### Post by pmasiar on 2007-08-06
> **AlexThomson_NZ said:**
> Personally, I have a love/hate relationship with Java. ... But for the industry I'm in (very, very large scale, complex web applications)- there is no alternative

i read some introspection that 90% of why Java is better than C++ is 1.) full implementation of standard 2.) garbage collection.

Java is only alternative for "enterprisey" complex web apps. It was not even designed for text processing.... but for GUI for set-top boxes. Big part of success is marketing, and being (10 years ago :-) ) a strong alternative to MSFT.

I understand big companies have lot of investment in old code and process, they have huge inertia and are reluctant to change (and there are decent secure jobs there).

It does not mean there is no alternative - it just means that alternatives are not obsolete enough (oops, I mean mature and stable enough :-) )  to be considered by "enterprise" IT management.

---

### Post by Note360 on 2007-08-07
I like Java, but it sucks wiht cli stuff.

---

