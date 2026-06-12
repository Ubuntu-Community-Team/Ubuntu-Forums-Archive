---
title: "[SOLVED] Python - simplest way to generate XML?"
date: 2008-02-18
forum: Programming Talk
---

### Post by scruff on 2008-02-18
I'm looking for the simplest method of generating XML through Python for a music library mgmt application I am working on. I am thinking of minidom because of its small footprint but I haven't found any simple examples to generate the actual XML. Much of what I have found is geared toward parsing or manipulation of existing XML. I am used to XML::Simple in Perl...

This should be extremely easy. Here is the XML structure:

[php]
<?xml version="1.0"?>
<library>
    <track>
        <file name="foo" path="/path/to/file" lastmod="timestamp"/>
        <md title="title"/>
        <md artist="artist"/>
        <md album="album"/>
        <md genre="genre"/>
        <md etc="[more metadata]"/>
    </track>
     <track>
            ...
    </track>
</library>
[/php]

I gather this data through a variety of modules that pull the metadata directly from the music library and this is how I would like to spit out the XML. Can someone point me in the right direction?

---

### Post by pmasiar on 2008-02-18
[http://www.kid-templating.org/](http://www.kid-templating.org/) is my favorite templating system. [here is why](http://turbogears.org/about/kid.html). Genshi is Kid v 2.0 with name easier to find via Google :-)

BTW why you need XML for data storage?

---

### Post by scruff on 2008-02-18
> **pmasiar said:**
> [http://www.kid-templating.org/](http://www.kid-templating.org/) is my favorite templating system. [here is why](http://turbogears.org/about/kid.html). Genshi is Kid v 2.0 with name easier to find via Google :-)

BTW why you need XML for data storage?

That looks interesting. It seems more geared toward generating web content than plain 'ol xml though.

This is mainly an educational excercise and a cure for boredom. 

I chose XML as a means of maintaining a persistent snapshot of everything in my library. I figure if I want to use the data in ways I have not yet thought of, XML would be the way to go. I also considered a database and may even do some perf testing of both storage methods to see if the performance gains are enough to go that way. In the end though, if I release this to the public I would like as few external deps as possible by sticking to libs included in the Python dist if I can.

---

### Post by Wybiral on 2008-02-18
ElementTree works great for generating XML if templating isn't what you're looking for.

---

### Post by scruff on 2008-02-18
ElementTree looks nice and fast. I'm toying with it right now :)

---

### Post by pmasiar on 2008-02-18
> **scruff said:**
> That looks interesting. It seems more geared toward generating web content than plain 'ol xml though.

Kid (and Genshi) generate valid XML. They are used and loved for web apps development, but not limited to it.

> I chose XML as a means of maintaining a persistent snapshot of everything in my library. I figure if I want to use the data in ways I have not yet thought of, XML would be the way to go. I also considered a database and may even do some perf testing of both storage methods to see if the performance gains are enough to go that way. In the end though, if I release this to the public I would like as few external deps as possible by sticking to libs included in the Python dist if I can.

If so, SQLite will be perfect IMHO. It is included in core Python since 2.5, is a C library (no server is running), and you have full power of SQL on your fingertips. It is much more flexible than XML, which basically hardcodes one of possible hierarchical structures - and you need to maintain internal consistency by hand. And SQL-based storege scales up: you can replace DB engine to more powerful MySQL when you need the power.

SQL might be harder to learn at start (exactly because XML has hardcoded structure, while SQL is much more flexible) but with SQL different view is simple - with XML, you need to painfully transform your data.

Also, you may want to look at object-relational mappers which will hide all SQL. SQLObject and SQLAlchemy are both part of TurboGears stack (so you will have only one dependency). But for simple SQL you don't need it.

Re performance:

I am quite sure that SQLite, which is C library accessing binary data format, will be faster than any XML parser.

---

### Post by Wybiral on 2008-02-18
> **scruff said:**
> ElementTree looks nice and fast. I'm toying with it right now :)

There's also cElementTree (which is the same API, just implemented in C and very fast). And a couple other implementations of the same API (like the lxml one, which has a few extensions).

---

### Post by scruff on 2008-02-18
> **pmasiar said:**
> 
If so, SQLite will be perfect IMHO. It is included in core Python since 2.5, is a C library (no server is running), and you have full power of SQL on your fingertips. <SNIP>

I am quite sure that SQLite, which is C library accessing binary data format, will be faster than any XML parser.

That is awesome! The ability to use without setting up and configuring a MySQL server has me sold I think.

Thanks guys!

---

### Post by scruff on 2008-02-18
Also, after spending a frustrating day running through sparse documentation (and I am no stranger to such) it is very nice to see the SQLObject docs contain plenty of info and useful examples!

---

### Post by pmasiar on 2008-02-18
Yup, yet another win by challenging poster assumptions instead of answering question directly. :-)

Simplest way to generate/parse XML seems to be SQLite with SQLObject :-) because OP wanted just to store data in a flexible way. :-)

---

### Post by scruff on 2008-02-18
> **pmasiar said:**
> Yup, yet another win by challenging poster assumptions instead of answering question directly. :-)

Simplest way to generate/parse XML seems to be SQLite with SQLObject :-) because OP wanted just to store data in a flexible way. :-)

I don't know what else to say but point taken :)

---

