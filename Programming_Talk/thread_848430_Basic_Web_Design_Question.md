---
title: "Basic Web Design Question"
date: 2008-07-03
forum: Programming Talk
---

### Post by TedPacyga on 2008-07-03
My question has to do with web designing, so I believe this is the right place for this, if not I am sorry.

I started learning HTML, and all that other stuff to make web pages, but was wondering what is actually necessary to learn.  Like I also started reading about CSS, but do I actually need that?  Basically what languages(these are programming languages right?) should I learn for web design?  Do people even use HTML or do they just use XHTML?  I would like to know what most people use so I can learn that, and not things I don't need to.

Thanks.

---

### Post by gnuman on 2008-07-03
I'd recommend learning XHTML and CSS first.  A good book to start with is the Head First HTML book.

[_Head First HTML link._]("http://oreilly.com/catalog/9780596101978/")

This site is also pretty helpful in sorting out all the facets of web design and programming:


[URL="http://struts.apache.org/primer.html"]
_Key Technologies Primer._[/URL]

---

### Post by Joshuwa on 2008-07-03
> **TedPacyga said:**
> My question has to do with web designing, so I believe this is the right place for this, if not I am sorry.

I started learning HTML, and all that other stuff to make web pages, but was wondering what is actually necessary to learn.  Like I also started reading about CSS, but do I actually need that?  Basically what languages(these are programming languages right?) should I learn for web design?  Do people even use HTML or do they just use XHTML?  I would like to know what most people use so I can learn that, and not things I don't need to.

Thanks.

CSS is essential to today's web design.

The idea is to separate the content from the design, so that either can be changed independently without affecting the other. For this reason, you will never use HTML to specify sizes, positions, colors, styles, etc. Let the HTML be used for the content/text of the site, and use images and CSS to do the styling of it.

As a web designer, the **design** is your main focus. Strong skills in Photoshop (or other app) to create a design, cut it up, and then use strong CSS + HTML skills to make it happen in the browser.

You need to know HTML to be able to make your CSS work, but I stress again: CSS is where the magic happens.

HTML is not a programming language, and there is a difference between a web **developer** and a web **designer**. Designers focus on looks, developers are under the hood making functions and code work, connecting databases, etc.

Design and development, like design and content, should be independent, and the designer shouldn't be developing, and the developer shouldn't be designing.

As a designer though, it is helpful to not necessarily know languages such as PHP, Python, Javascript, etc - but you should be familiar with them enough to be able to embed your design into their code.

If a developer sends you some PHP pages, you should know where and how you can edit it to put your CSS/HTML in.

---

### Post by CptPicard on 2008-07-03
> **TedPacyga said:**
> 
I started learning HTML, and all that other stuff to make web pages, but was wondering what is actually necessary to learn.  Like I also started reading about CSS, but do I actually need that?

Yes, actually CSS is the preferred way these days to attach styling to (preferably) XHTML.

>   Basically what languages(these are programming languages right?)

No, they're not programming languages. Turing-completeness is the general requirement, and neither HTML or CSS are. They are sort of document description languages, not programming languages. :)

You might also want to learn JavaScript if you want to add client-side functionality to your pages... that *is* a proper programming language.

> Do people even use HTML or do they just use XHTML?

You should be aiming at using XHTML, yes, to future-proof what you're doing.

---

### Post by pmasiar on 2008-07-03
If you want to be web designer, there is no way around CSS. XHTML is just properly (XML) formatted HTML, but CSS lets you to separate content from style (so you do not format every element).

You may want to consider moving farther. AJAX makes more fun and dynamic webpages on client, and consider server side programming too. Many HTML designers like you jump for  PHP, because it allows them to add simple things with little effort, and only later realize how hard is to implement big systems (dozens or hundreds of pages) in PHP in a flexible and reliable way. Other way is to use Python or Ruby and web framework like Django or Rails.

Programming with Javascript, Python or Ruby is completely different and harder: HTML/CSS shows result immediately and visually, program will generate response and you have to understand it, so you may consider staying on the graphics designer side of it.

Summary: there is no silver bullet, there are many technologies you will have to learn, and many more will appear later in your career. If you are afraid of learning new tools and approaches, computers and web may be not good career choice for you. Yes, it is like drinking from the firehose - that is part of the fun! (and part of why salaries are good: because it is not simple or dumb).

---

### Post by TedPacyga on 2008-07-03
First of all, thank you all for the quick and informative responses.  Right now I am just studying all I can about computers in general.  I want to learn as much as I can about the programming and structure of computers and the internet.  So not only will I be learning about web designing, but also I want to learn computer programming in general, and for that I picked up learning Python a few days ago.  I want to understand how all of this works, and that is why I want to study as much as I can, about as many topics about computers I can.  Also in the future,  I will be able to choose exactly what interests me the most, since right now basically everything and anything that deals with computer is exciting for me.

---

### Post by LaRoza on 2008-07-03
> **TedPacyga said:**
> Also in the future,  I will be able to choose exactly what interests me the most, since right now basically everything and anything that deals with computer is exciting for me.

Good idea, there is a lot to study and getting a diverse taste will be very helpful.

My wiki might help you; it has a section of web design.

---

### Post by stevescripts on 2008-07-03
Just in case you haven't found it by now - W3Schools is a good place to start:

[http://www.w3schools.com/default.asp]("http://www.w3schools.com/default.asp")

---

### Post by era86 on 2008-07-03
> **stevescripts said:**
> Just in case you haven't found it by now - W3Schools is a good place to start:

[http://www.w3schools.com/default.asp]("http://www.w3schools.com/default.asp")

+1

I learned CSS from this site back in 2004.  This is a great site to use as a learning tool as well as a quick reference.  Bookmark it!

---

### Post by TedPacyga on 2008-07-03
> Just in case you haven't found it by now - W3Schools is a good place to start:

[http://www.w3schools.com/default.asp](http://www.w3schools.com/default.asp)

Yeah I have been there before, but thanks.  It's good stuff.

> My wiki might help you; it has a section of web design. 	

Thanks, I will take a look at that.

---

### Post by LaRoza on 2008-07-03
> **TedPacyga said:**
> Thanks, I will take a look at that.

It really doesn't have much more than what is already here, but there is more for more advanced things (ECMAScript and server side programming)

---

