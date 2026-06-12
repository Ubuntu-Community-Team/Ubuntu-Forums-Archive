---
title: "Dreamweaver alternative?"
date: 2009-10-14
forum: Programming Talk
---

### Post by armageddon08 on 2009-10-14
Is there a good WYSIWYG alternative for dreamweaver alternative for linux?

---

### Post by Can+~ on 2009-10-14
I've heard good things about aptana:

[http://www.aptana.org/](http://www.aptana.org/)

---

### Post by armageddon08 on 2009-10-15
> **Can+~ said:**
> I've heard good things about aptana:

[http://www.aptana.org/](http://www.aptana.org/)

Is it a WYSIWYG editor?

---

### Post by giuspen on 2009-10-15
if you like kde gui you can try quanta (you can install also on gnome)

sudo apt-get install quanta

(for me kde is a finger in the ***)

for gnome there's kompozer

sudo apt-get install kompozer

but if you are used to dreamweaver (as am I) that's a finger in the *** too

I would like to write a gnome "dreamweaver-like" application but it requires so a lot of time :(

---

### Post by hessiess on 2009-10-15
Learn HTML, CSS and use a text editor. Visual editors output awful HTML and are incapable of doing a lot of things you cn do with raw code.

The best web pages are dynamic and adapt to the browser, the wysiwyg model is incapable of working like this.

---

### Post by howefield on 2009-10-15
> **armageddon08 said:**
> Is there a good WYSIWYG alternative for dreamweaver alternative for linux?

Dreamweaver works pretty well in wine.

---

### Post by an_teallach on 2009-10-15
Hello there - my first post!!

I've used Bluefish and NVU in the past and they're pretty good.

I know NVU has template support, however it seems slightly buggy at times and often crashes.

Does anyone know of any other editors with template support?

---

### Post by NoaHall on 2009-10-15
Geany's what I use.

---

### Post by jeneverboy on 2009-10-15
Dreamweaver in wine works perfect for me too.

---

### Post by ajy0852 on 2009-10-15
To build a web page from scratch, you're really best off knowing HTML/CSS. HTML is quite easy to learn and it's totally worth your time. Take a look at tutorials on w3schools. A knowledge of HTML and CSS will even make a WYSIWYG editor much more enjoyable and effective to use, so I'd recommend it.

As for WYSIWYG editors (I know, the actual topic of the thread), Kompozer is pretty good. If there is even still a version in the repo's, it's not going to work for you - it'll just crash constantly because it doesn't work with the current version of GTK. Instead, go to kompozer.net and download the 0.8 beta. Extract the package and double-click on "kompozer" inside the kompozer folder.

Geany and Aptana are both great code editors, same with Bluefish. Aptana includes a preview function but it's not actually WYSIWYG (Bluefish and Aptana both have toolbar buttons that can insert code snippets into your source file though). Nvu is really just an older version of Kompozer that is no longer updated, and it'll have the same problem with GTK as old versions of Kompozer. I have also used Quanta for a time. It's a great code editor with a WYSIWYG mode that I found pretty ineffective. The main problem for me is that it's a KDE 3.5 app that hasn't yet been updated for KDE 4.

---

### Post by donsy on 2010-07-17
> **hessiess said:**
> Learn HTML, CSS and use a text editor. Visual editors output awful HTML and are incapable of doing a lot of things you cn do with raw code.

The best web pages are dynamic and adapt to the browser, the wysiwyg model is incapable of working like this.
A friend asked me to build her a small-business website which will use forms, PHP, and MySQL. The PHP and MySQL are no problem, but I wonder just how far I can go with coding the raw HTML into gedit. Isn't something like Dreamweaver required to do anything other than a very simple website? I know nothing about WYSIWYG tools, and I'm wondering if I should start learning. How far can one go with just coding the raw HTML and CSS?

---

### Post by trent.josephsen on 2010-07-17
This thread is a little stale.

> **donsy said:**
> A friend asked me to build her a small-business website which will use forms, PHP, and MySQL. The PHP and MySQL are no problem, but I wonder just how far I can go with coding the raw HTML into gedit. Isn't something like Dreamweaver required to do anything other than a very simple website?
Nonsense.  With careful design it is possible to make great-looking websites with minimal HTML and CSS.  The key is "design".  You're not just throwing together a wad of HTML whenever a new page is needed; you need to design your base code to be extensible in-place and your new code to extend and reuse the old code.  This was not true in the pre-CSS days of table-based layout, when it really was necessary to use Dreamweaver or a similar tool if you wanted anything decent-looking (and Heaven help you if you tried to make a minor edit in any other tool).

> I know nothing about WYSIWYG tools, and I'm wondering if I should start learning. How far can one go with just coding the raw HTML and CSS?
What do you mean, "raw HTML"?  You're using PHP, right?  Which means (most of) your pages are going to be generated on the fly.  You don't have to write static HTML pages for everything you put out there.  Use templates to eliminate redundancy so your files don't all start with <!DOCTYPE ...><html><head>blah blah blah</head><body>, which means that if you ever change the entire site you have to change every single file.  Code with your brain, not your fingers.

---

### Post by donsy on 2010-07-17
> **trent.josephsen said:**
> 
What do you mean, "raw HTML"?  You're using PHP, right?  Which means (most of) your pages are going to be generated on the fly.  You don't have to write static HTML pages for everything you put out there. 
Well I was planning on using PHP mainly for editing and cleaning the data and generating the proper SQL to insert it into the database, not necessarily for generating HTML on the fly. For that I would prefer to have as much statically coded HTML as possible. 

> **trent.josephsen said:**
> 
Use templates to eliminate redundancy so your files don't all start with <!DOCTYPE ...><html><head>blah blah blah</head><body>, which means that if you ever change the entire site you have to change every single file.
Can you elaborate a little more on this or provide a link?

---

### Post by trent.josephsen on 2010-07-17
> **donsy said:**
> Well I was planning on using PHP mainly for editing and cleaning the data and generating the proper SQL to insert it into the database, not necessarily for generating HTML on the fly. For that I would prefer to have as much statically coded HTML as possible.
Why?  I mean, for a site with only 2-3 pages and no dynamic content, it might make sense, but static HTML becomes unmaintainable very, very quickly.

> Can you elaborate a little more on this or provide a link?
Erm, it won't work with static HTML (hence the term "static").  My experience is with Python/Django and Perl/HTML::Template; no PHP knowledge whatsoever.  You might look into SSI (Server Side Includes) if you're truly opposed to dynamically generated HTML.

---

