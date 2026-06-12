---
title: "How can I, as a PHP programmer, benefit from XML?"
date: 2006-07-18
forum: Programming Talk
---

### Post by Isoss on 2006-07-18
Hi!
I've always heard and read so much about xml. I even got some tutorials and tried to know what exactly can this markup langauge do! I know it's for organizing data! But dunno how I can, as a php programmer, benefit from it!

I see a lotta sites using XML as in [http://www.goodphptutorials.com/](http://www.goodphptutorials.com/) ... I can see there is a relationship between XML and RSS. for if I point the cursor to the XML icon in the mentioned website it shows the alt value as : "Get the latest tutorials using the magic of RSS". I can see RSS is about bookmarking news or something (correct me if I'm wrong) So I hope someone would explain what XML can do exactly and what RSS really is?

Thanks

---

### Post by LordHunter317 on 2006-07-18
XML lets you organize data.  That's it. People may try to make it more than that, but that's it.  It's just a file format.  It's nothing more magical than that.  Anyone who tells you otherwise either has some drugs you should ask him for (they're really good) or is selling you something (but probably not drugs). 

It's only real advantage to any other format is it has tons of parsers in every language for you, and that it is extensible (though the useful of this is rather limited in most cases).  It's also naturally hiearchial, which is good for hiearchial things, like configuration files frequently are.

RSS stands for 'Really Simple Syndication' and it's a XML format designed for giving update summaries when sites change.  A blog would have an RSS File that gets a new entry added when a new post is added.

This forum uses RSS to let you know when a new thread is added  to a forum.

---

### Post by Isoss on 2006-07-19
Ok ... Thanks so much! but, forgive my ignorance ... I read that a thousand time. But still dunno how can I apply xml. I have a christian website and it's written with PHP and all data are mysqldb based. I have a db for the arabic bible, news, ads, sermons, hymns and a lotta info about churches and stuff. How can I apply xml in a useful way? I am not of that kind that preferes getting to know new stuff in an abstract way of learning .. I always would apply in a practical way so I can comprehend and understand. actually that's how I understood how PHP and some other programming languages work! applying the vague scripts and then get to understand it's machanism.

I don't even know how to use RSS, I.E can't find or figure how to get the RSS which this forum uses and how to use it!

Can you or anyone please help me making these more practical in my mind?

Thanks for your time.

---

### Post by slider on 2006-07-19
> **Isoss said:**
> Can you or anyone please help me making these more practical in my mind?

I am just starting the process of reworking a site to use the new XML Dom in php5. I look at XML this way, it helps to enforce separation between logic and display and gives you access to some tools to support more output formats.  

Here's a usage case that may help clarify. Right now, you are probably taking data out of your db and writing xhtml directly for your website. Lets say you have a need/desire to produce HDML to serve your site to hand held devices. If your site is well designed with display separate from logic, you could just write a new display interface to create the HDML. If you have display wrapped up with logic and/or database access, you have a harder task. Plus, who knows down the line how many display/output markup languages you are going to want to support.

If you write your database access code to create XML and then use XSL to transform that into XHTML and HDML then, when you need to write out FooML down the line, all you have to do is write a new translation  to create the new output format.

---

### Post by bieber on 2006-07-19
XML isn't a file format in and of itself, it's sort of a set of guidelines to create your own file format.  And that's where it becomes useful.  You can just sit down and create a markup language for an application you're writing, and then use any XML parsing library to read it.  Plus it's useful if you need to try and read a file in a text editor created by a program.  Of course, you get that with plain text config files as well...

---

### Post by mostwanted on 2006-07-19
I recently updated my RSS file to RSS 2.0.

Then used this new feed in conjunction with [talkr.com]("http://talkr.com").

Now I've added links to the audio clips from talkr.com below each new blog post.

That's one way to benefit from it.

---

### Post by slaging on 2006-07-19
Great examples & tutorials at [http://www.w3schools.com/default.asp]("http://www.w3schools.com/default.asp")
 I've always used XML for Data Islands ( [http://www.w3schools.com/xml/xml_data_island.asp]("http://www.w3schools.com/xml/xml_data_island.asp") )
Hope the links help.

---

### Post by Oler1s on 2006-07-19
Just to emphasize. XML is a tool. If you don't need it, you don't use it. Sort of like a carpenter trying to hammer nails in and wants to figure out how to fit in a power saw.

Do you need an automatically updating list? Do you need to transfer data from one format to another (not a database though)? XML is a useful intermediate tool. When you actually need XML, it's usefulness becomes apparent.

---

### Post by bieber on 2006-07-19
Slaging, that whole Data Islands thing looks really nifty.  Does it work in IE, though?

---

### Post by Oler1s on 2006-07-19
> **bieber said:**
> Data Islands thing looks really nifty.  Does it work in IE, though?

I think it only works in IE. Have seen ideas about using Javascript for Mozilla support though.

---

### Post by tekrei on 2006-07-20
You can learn AJAX web development : [http://developer.mozilla.org/en/docs/AJAX:Getting_Started](http://developer.mozilla.org/en/docs/AJAX:Getting_Started)
Use PHP as server side scripting,Javascript as client side and XML for data transfer.

"AJAX (Asynchronous JavaScript and XML) is a newly coined term for two powerful browser features that have been around for years, but were overlooked by many web developers until recently when applications such as Gmail, Google Suggest, and Google Maps hit the streets.

The two features in question are that you can:

    * Make requests to the server without reloading the page
    * Parse and work with XML documents "

---

