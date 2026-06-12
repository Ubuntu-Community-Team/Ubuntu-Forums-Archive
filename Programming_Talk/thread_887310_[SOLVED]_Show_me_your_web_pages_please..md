---
title: "[SOLVED] Show me your web pages please."
date: 2008-08-12
forum: Programming Talk
---

### Post by ddixonr on 2008-08-12
Hey fellow web developers. I just started putting a website together. I bought an html quick guide from the local electronics store and got to work. I am hosting it on my ubuntu hardy desktop, which of course is always on. I installed Apache, followed a tutorial to get that going, and then started taking examples from my html guide to begin making pages. 

I would like to learn new things without learning the whole of php, python, css, etc. Would anyone like to share with me the files/code it takes to create forms users can send to me, visitor registrations/logins, polls, comment sections, and other visitor involved items?

To be clear, I have no real programming experience. Thanks for any help provided.

---

### Post by LaRoza on 2008-08-12
> **ddixonr said:**
> Hey fellow web developers. I just started putting a website together. I bought an html quick guide from the local electronics store and got to work. I am hosting it on my ubuntu hardy desktop, which of course is always on. I installed Apache, followed a tutorial to get that going, and then started taking examples from my html guide to begin making pages. 

I would like to learn new things without learning the whole of php, python, css, etc. Would anyone like to share with me the files/code it takes to create forms users can send to me, visitor registrations/logins, polls, comment sections, and other visitor involved items?

To be clear, I have no real programming experience. Thanks for any help provided.
My web page is the "Learn to Program" link in my sig. It was written totally by me and is all valid code. (I wrote the PHP, CSS, ECMAScript and XHTML)

For now, learn how to write valid and logical XHTML. Then learn CSS and then get into scripting.

If you use pre-made solutions too early, you're pages will end up sloppy and poorly designed.

After learning web design, you can check out the various frameworks.

Oh, you don't need a server for plain XHTML files, you can just open them in a browser.

Also check out [www.useit.com](www.useit.com) for the most important part of web design.

---

### Post by namegame on 2008-08-12
Forms usually require some sort of language behind them, usually PHP.

Your best bet would be a WYSIWYG (what you see is what you get) editor for HTML/PHP/CSS, if you need a website in the immediate future.

I've used Bluefish in the past, and it works quite well.
[http://bluefish.openoffice.nl/](http://bluefish.openoffice.nl/)

It's never a bad idea to learn the fundamentals of the languages you are using.

---

### Post by lisati on 2008-08-12
Open Office Writer can save documents in HTML formatm which can then be transferred to your server.

Most of the web pages I've thrown together (and some of them look just like they have been) have been created with Yahoo's "PageBuilder". Sadly, the last time I went to use it, it didn't work too well with Linux (Ubuntu)

---

### Post by perlluver on 2008-08-12
Here is my website, written by hand in CSS, and HTML.  [http://www.freewebs.com/perlluver](http://www.freewebs.com/perlluver).

---

### Post by skeeterbug on 2008-08-12
Personal project of mine: [http://www.guildreport.com/](http://www.guildreport.com/)

Site I did for my employer: [http://www.mission3.com/](http://www.mission3.com/)

guildreport.com is done using Python, mission3.com is Ruby. I use Aptana with the ruby on rails (previously RadRails) for RoR, and the PyDev plugin for Python. It has a great html/css editor, ftp, svn support, etc. 

If you want to add polls, registration, and login functionality to your site you are going to have to learn a server side programming language. I started out in high school doing asp/php.

---

### Post by tinny on 2008-08-12
Static HTML pages will only take you so far. To provide the type of functionality that forums, wiki's etc do you need to look at server side coding (like stated previously).

Heres one of the web sites ive worked on.
[https://www.1place.co.nz/](https://www.1place.co.nz/)

Technologies:

XHTML
Java Applets
JBoss Seam
EJB3
Hibernate

But sounds to me like you dont want to be a "Software Developer" (and fair enough :) ). Maybe something like [Adobe Flex]("http://en.wikipedia.org/wiki/Adobe_Flex") / [Flash]("http://en.wikipedia.org/wiki/Adobe_Flash") is what you should look at. I believe that Flex / Flash are technologies that enable much greater creativity than boring high level programming languages. Good web developers should be creative and not technical.

---

### Post by hessiess on 2008-08-12
[www.hessiess.com](www.hessiess.com)
not terably complicated, but its still 100% standerds complient XHTML, 100% table free and was created using nothing more than a text editor. Dont use WYSIWYG editors, thay output horrably messy, table ridden code, which 99.9% of the time will have major display errors in one or more web browsers.

---

### Post by rabatitat on 2008-08-12
> **ddixonr said:**
> Hey fellow web developers. I just started putting a website together. I bought an html quick guide from the local electronics store and got to work. I am hosting it on my ubuntu hardy desktop, which of course is always on. I installed Apache, followed a tutorial to get that going, and then started taking examples from my html guide to begin making pages. 

I would like to learn new things without learning the whole of php, python, css, etc. Would anyone like to share with me the files/code it takes to create forms users can send to me, visitor registrations/logins, polls, comment sections, and other visitor involved items?

To be clear, I have no real programming experience. Thanks for any help provided.

Wow, don't expect to get those things going on your server right away...

There's a lot more involved to making those kinds of pages than just copying and pasting other people's scripts/code (even if they let you)...

If you've already got your LAMP stack ready, then by all means learn in that order... Linux commands/tools... Apache (HTML/HTTP)... MySQL(easy way to handle data) PHP... easy way to run scripts...

You will have to learn a little programming to get it done.

---

### Post by Tomosaur on 2008-08-12
It might be worth your while looking at a CMS like Joomla or Drupal. I prefer Joomla, but both are great at what they do. The beauty of it is that you can check out all of the source code and see what's going on. Many of the modules available are open-source too so you can find say, a login system that you like and take a peak behind the scenes to see what's going on.

The downside of Joomla is that most of the templates from the 1.0 version are riddled with tables, and although many of the new, 1.5 version templates have a bigger drive to be table-less, the chances are that, unless you build your own template from scratch, you will still end up with a lot of tables. Whether this is a big problem for you or not, I don't know. I'm not particularly bothered by it, although I am building a website for a bar and am using a custom-modification of the default rhuk_milkyway template. The final design is not 100% there yet, but the overall look-and-feel is remaining as it is now. The problem is that the template still uses a lot of tables, so I may spend a while converting it to a table-less template to make sure a future maintainer doesn't have to deal with them.

---

### Post by Reiger on 2008-08-12
@OP you may have heard a lot of "but it uses a lot of tables", "tables are evil", "don't use tables" etc. etc. Question is: why?

Answer to the question:

A) Practical reasons;
[list="1"]
[*] There exist quite a few cross-browser inconsistencies with tables; especially when you start throwing CSS in or start doing other stuff which is intended to make the table lay-out your entire page.
[*] It comes at the expense of readability. Only editors & browsers which don't get fed up with 50 'essentially redundant pieces of code' in a row would be capable to 'understand' what the heck table-ridden code actually does. Start identing properly, and you may even risk breaking it; for all it's 'robust' features tables are actually pretty fragile.
[/list]
B) Principles.
[list="1"]
[*] By 'common' convention you should separate layout from content as much as possible; and you should *always* separate content from colours and the like. Tables tend to disrupt this good practice. (You can infer the reasons why by looking at the practical reasons...)
[*] You should try to use the logical tools for the job. You should use a list (ul or ol; with li elements) and not a row of text lines + br elements to render a list. You should use a p element for a paragraph instead; a h1 element for a header (and not for ordinary text)... Likewise you should use a table to render well... a table!
[/list]

EDIT: And please stay away from the awful practice of "Using Flash to solve everything!", i.e. pages which contain of a HTML 'wrapper' around what is essentially just a flash object... If only because those pages tend to have a horrible performance (loading times etc. etc.) and a disastrous effect on browser stability.

---

### Post by ddixonr on 2008-08-12
Thanks for all the great replies. It seems learning programming is inevitable, but I will look at the tools/templates some of you listed.

---

### Post by TreeFinger on 2008-08-12
[http://www.personal.psu.edu/sjc5002/](http://www.personal.psu.edu/sjc5002/)

I use tables on my page for my projects :(

Was going to update it to get rid of tables but haven't gotten around to it.

XHTML/CSS

---

### Post by rabatitat on 2008-08-18
Well the main issue IME with frames, tables, AND CSS would be their ever-changing implementations across browsers...

The layouts change (sometimes drastically) across browsers.

The one thing I've learned is not to FORCE the browser. By this I mean forcing it to use anything specific i.e. fonts.

My HTML designs are minimalist and my code is "generic" just so I can avoid these complications.

Oh and as for Flash and other non-standard plug-ins, I wouldn't recommend using them unless absolutely necessary. Although they do tend to be a workaround for prettifying your pages...

I can't wait for SVG to be a full W3C specification...

Edit: As for learing, start with the manuals then the online HOWTOs. Whatever they teach you in school is at best 25% of you'll need in real life.

---

