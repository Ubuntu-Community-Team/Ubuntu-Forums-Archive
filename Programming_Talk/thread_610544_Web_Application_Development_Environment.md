---
title: "Web Application Development Environment"
date: 2007-11-12
forum: Programming Talk
---

### Post by tjpren on 2007-11-12
Hi guys,

Having been using Ubuntu for a month or so, I'm wanting to look at a programming environment.  Coming from a windows environment, I am familiar with VB and the Visual Studio environment.

I'm wanting to develop **web apps, that link to databases**.

I like the graphical design environment of MS, and so have started looking at Gambas.  Looks good, but doesn't seem to have any web app support.

I've looked at Python, but found myself floundering using IDLE.  from what I can see, Python is more like scripting language ?

As I understand it, Linux, Apache and PHP go together but what is a good programming app to develop web apps (preferably with a good graphical environment).

---

### Post by Compyx on 2007-11-12
For building dynamic websites, I personally prefer a good text-editor over GUI's and IDE's. Handcoding everything gives you a lot more control over the entire process and will greatly help in keeping things simple and making sure your code validates. It also helps in getting a good understanding how for example PHP interacts with MySQL, how to manage sessions and how to prevent SQL-injection and cross-site scripting attacks.

Of course, there are complete frameworks for build webapps such as Ruby on Rails, Zope, etc. I am not familiar with these tools, I just use VIM with the Gimp and Inkscape for graphics.

---

### Post by zero-9376 on 2007-11-12
i did a VERY simple web app as part of my thesis using TurboGears [http://www.turbogears.com/](http://www.turbogears.com/)
They have a video on the site showing the construction of a basic wiki in 20 minutes. They use python which I personally found very easy to pick up just by reading the basics and using the documentation i was able to write the 3 CLI applications and the web interface in 2 weeks

---

### Post by pmasiar on 2007-11-12
We had discussions about "lack of MS-like IDEs" for Linux many times, so if you want to discuss that, finding older threads and linking them would save us all plenty of time. 

In summary:
1) many people do not care about integrated IDEs, because they learned universal editor, VIM or EMACS, and use it for everything (and it works for new languages, and you can transfer all customizations). Many other ppl use simpler to learn and use editors, like Scite (my favorite) or dozen others, for editing **everything**.

2) Most people don't see point using crufty and obsolete language like BASIC, if you can have much improved modern language like Python or Ruby (or even Perl or PHP). BASIC was not intended to be used for text parsing, it is simplified fortran for number-crunching, and most people gladly abandons it for better languages.

3) Designing decent IDE is lot of work, big part of it is rather boring, and free software works differently from proprietary closed source: Developers will add code to "scratch own itch" and stop when it is "good enough" and move to more interesting projects. Because most skilled developers don't care about IDEs as I said before (use VIM or EMACS for X years), so finishing touches on potential IDE's in free software is left to less skilled depelopers (who are by definition not qualified to do it), or to commercial IDE developers.

4) So yes, there are IDEs for widely used Linux languages, but they are mostly not for free (often having free teaser version). But again, this makes sense to do for widely used popular languages, like Python, Perl, PHP (Komodo and others), not for obscure and obsolete language like BASIC. Yet another way is language-specific plugins to almost-universal IDE like Eclipse. Maybe you have luck with BASIC plugin, but frankly, just switch to decent modern language and be done with it.

Curiously, what in your POV distinguishes BASIC from as you call them "scripting" languages? You may want to learn about Blub Paradox in languages before answering: [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

Edit: Some (not many: it is basically one poster, but I was warned i would be banned if I mention his name, so i will not :-) ) disagree with points above, but I don't care defend my positions from any attacks by above mentioned individual. Either someone else will, or not - and ultimately it is up to you to make your own mind, what is best solution for your circumstances.

---

### Post by tjpren on 2007-12-27
Hi,
Thanks for the reply.

I suppose where I am coming from is what I am familiar with - Windows and VB.  Its basically all I have known, however, I'm wanting to broaden my horizons - hence my foray to Linux.  I've got to stress, I'm hardly a programmer - I can write some code, and can marvel at exponents to whom it appears as an easy task.

I've now got Apache loaded and running (XAMPP), and have settled on PHP as my "new" language.  I'm trying to get PHPEclipse to work at the present, although its proving difficult, to be my IDE.  I think I will struggle in writing code in a text editor environment - I need syntax checking and a reference library at least.

My programming is specifically focussed toward web development, mainly as a work suppliment (looking at alternatives to the Windows/VB thing as I metioned above).

Anyway, thats my rambling

Regards.:)

---

### Post by ghostdog74 on 2007-12-27
> **tjpren said:**
> Hi guys,

Having been using Ubuntu for a month or so, I'm wanting to look at a programming environment.  Coming from a windows environment, I am familiar with VB and the Visual Studio environment.

I assume you are already familiar with VB studio and Visual studio web developer and you have been doing ASP since day one?
You can use VB to connect to database as well, you know?

---

### Post by Zerocool10482 on 2007-12-27
I'm not a web developer but I've heard about this.

[http://www.aptana.com/](http://www.aptana.com/)

If doesn't work then use something from Gnomefiles.org

---

