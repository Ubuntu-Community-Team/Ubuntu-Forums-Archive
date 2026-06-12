---
title: "Open source transition"
date: 2012-03-04
forum: Programming Talk
---

### Post by HeroOfCanton on 2012-03-04
I'm trying to slowly convert as much as I can to OSS. For personal use it was an easy switch and I haven't booted my laptop to Windows in months. :)

A much bigger issue, however, is my work. I own a web development company and have been a Coldfusion specialist for many years. The costs of running a CF server that serves thousands of users has become a bit absurd, so I'm looking into transitioning the business to CentOS/Apache and PHP as an alternative. (Not to mention the cost of Adobe software suites every few years)

Couple of quick questions that would help me with this transition.

1) What editor is best for web development in linux? I love Eclipse for Java and android development, but for web programming I've heard it's a bit lacking. Any suggestions for someone coming from Dreamweaver?

2) What are some good open source projects to learn coding from? A CMS or forum would be nice, as I'll need these eventually anyways, but my main concern is well documented, well formatted, code regardless of what it does. Prefer something that uses MySQL for data storage. Also would like to see some OOP being used with best practices. Javadoc commenting would be awesome, but not a must if everything is well commented in another style.

I've been programming for about 20 years so the depth and size of a project is not a concern, just need to be sure it's well commented so I know what the heck is going on without extensive GIS needed. More for learning than actual use at this stage. Once I get the hang of it I'll find some OSS to build on for my specific needs.

Thanks in advance!

---

### Post by MG&amp;TL on 2012-03-05
1) I use bluefish, on the rare occasions I do web code.

2) [https://launchpad.net/](https://launchpad.net/) Go and get lost, in lots of code. There must be at least one project on there using Java OOP.

---

### Post by juancarlospaco on 2012-03-05
I use Vim when im on CLI, i use Ninja IDE when im on GUI.

Django or Plone.

Try Ngix instead of Apaches.

---

### Post by 1clue on 2012-03-05
If you're thinking about a web framework and you are coming from a Java background, maybe you should look into groovy/grails.  [http://www.grails.org](http://www.grails.org)

It runs on the Java Virtual Machine.  Groovy is a much more compact language, has loose typing and compiles into Java byte code.  Much of the boilerplate is gone, leaving mostly just the interesting stuff.  Grails is a web application framework for groovy, using convention before configuration.  You CAN override normal behavior very easily, but if you don't want to then you spend a lot less time wiring things together because it all happens by name.

My code editors are STS ([http://www.springsource.com](http://www.springsource.com)) and Vim.  I haven't noticed any huge flaws in HTML but for me it's mostly just HTML, CSS, Javascript and JQuery.

*PS:*

I would recommend not converting things just for the sake of converting things.  If your commercial licensing is driving you under then that's fine, but switching out every piece of software you have just to be thorough is a bit extreme.

---

### Post by HeroOfCanton on 2012-03-07
Thanks for the replies. I'll look into those editors, frameworks, and alt server software. I'm in no rush to make a conversion so I'll give each of those a nice evaluation period. Keep 'em coming if anyone has more suggestions!

For the web programming I was leaning towards PHP (to start) just because of the widespread use and support. I'll check these others out too though. I'm not so much from a Java background, as a "general" programmer. Started in BASIC (late 80's), then C, then C++, then HTML, etc, etc. Just like to tinker and the number of programming languages out there serve my ADD well. :) At this point all I know is it's time to move on from Coldfusion for web projects. Never know what may catch my interest...

> I would recommend not converting things just for the sake of converting  things.  If your commercial licensing is driving you under then that's  fine, but switching out every piece of software you have just to be  thorough is a bit extreme.     In addition to the licensing costs, which are absurd, I'm finding Coldfusion to be too tough on my hardware too. Coded in it for things as "high traffic" as a national ISP with little issue in the past. Silly as it sounds, my personal hobby website somehow sees heavier traffic and is requiring more and more hardware to keep it running up to speed. Now topping $6,000 per year for my cloud server! A linux box with the same hardware could save me hundreds every month (CF Server is ***expensive***). Bonus is I could probably downgrade the hardware in the process.

Besides, isn't doing things just for the sake of doing them what separates us geeks from the rest? :D

---

### Post by AlexDudko on 2012-03-07
1. Bluefish, Kompozer for markup. NetBeans for php, JavaScript.
2. [http://www.w3schools.com/default.asp]("http://www.w3schools.com/default.asp") Very simple but sufficient in most cases.

---

### Post by Some Penguin on 2012-03-07
> **HeroOfCanton said:**
> 
2) What are some good open source projects to learn coding from? A CMS or forum would be nice, as I'll need these eventually anyways, but my main concern is well documented, well formatted, code regardless of what it does. Prefer something that uses MySQL for data storage. Also would like to see some OOP being used with best practices. Javadoc commenting would be awesome, but not a must if everything is well commented in another style.



[http://code.google.com/p/guava-libraries/]("http://code.google.com/p/guava-libraries/") is pretty decent in terms of coding quality. 

Personally, I'd favor PostgreSQL over MySQL for reliability, and if required to use the latter would run like hell from MyISAM (favoring InnoDB for the simple non-clustered case).

---

### Post by bizz101 on 2012-03-07
> **HeroOfCanton said:**
> 

1) What editor is best for web development in linux? I love Eclipse for Java and android development, but for web programming I've heard it's a bit lacking. Any suggestions for someone coming from Dreamweaver?


Try Aptana Studio 3. It's based on Eclipse and more focused on web dev. I use it for PHP and it's great.
[URL="http://aptana.com/"]
http://aptana.com/[/URL]

---

### Post by 1clue on 2012-03-07
> **HeroOfCanton said:**
> Besides, isn't doing things just for the sake of doing them what separates us geeks from the rest? :D

Yes, if it's a low-risk situation.  If you own a bank though, and you decide that Friday night you're going to switch everything over to the nearest Open Source alternative and wire it all together by Monday...

Just saying take it slow and do one thing at a time.

Good luck and have fun.

---

### Post by HeroOfCanton on 2012-03-14
I've settled on Bluefish for the editor. Seems to do most of what I need. I do like the Ninja IDE style, but the PHP support seems a bit lacking.

Also found PHP to be pretty darn easy to learn, so the code really isn't that important anymore. Marking as solved. Thanks again.

And no worries 1clue. Certainly don't own any banks. I'll be sure to keep my clients happy though. If all goes well they won't have a clue that anything other than the file extensions have changed. :)

---

