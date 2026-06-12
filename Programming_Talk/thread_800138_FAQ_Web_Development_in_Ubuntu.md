---
title: "FAQ: Web Development in Ubuntu"
date: 2008-05-19
forum: Programming Talk
---

### Post by Verminox on 2008-05-19
[size=6]How do I create Web Pages?[/size]

[size=5]XHTML[/size]

Although the internet can be used to transfer virtually any type of file, most websites that you come across are actually a collection of **(X)HTML** documents. The **(eXtensible) HyperText Markup Language**, as the name suggests, is a language that is used to describe the *structure* of text-based information in a document &#8212; by denoting certain text as links, headings, paragraphs, lists, and so on &#8212; and to supplement that text with interactive forms, embedded images, and other objects.

The main difference HTML and XHTML is that XHTML conforms to XML syntax. This means that XHTML code is stricter and cleaner. It is much easier to learn because there are strict rules to follow and lesser ambiguity. Also, it concentrates on the semantics of the document so you can cleanly separate the *content* of the document from its *presentation*, which makes creating and maintaining the code much simpler. As XHTML is XML, it can also be easily parsed by standard XML parsers which is really useful when your web page is used by other applications, search engines, etc. As such, if you are new to web design, start learning XHTML and forget the old HTML even existed. (Note: The remainder of this article will only refer to XHTML)

You do not need to install anything to create or view XHTML files. You simply create a file with the markup and save it with a .html extension, and open it in a web browser like Firefox or Konqueror to view it.

[size=4]Resources[/size]
[W3Schools]("http://www.w3schools.com/xhtml/") - Although it is a good tutorial, it requires you to first read the HTML tutorial, and then understand the transition of HTML to XHTML.
[TopXML]("http://www.topxml.com/xhtml/") - Good site. It has a nice reference section so you can keep coming back to it to lookup something you might have forgotten while creating web pages in the future.
[XHTML Validator]("http://validator.w3.org/")

[size=5]CSS[/size]

**Cascading Style Sheets** is a language that is used to describe the *presentation* of web documents. It is most used with XHTML documents to tell the web browser how to render elements of the document (such as the font, colors, layout, etc). CSS can also describe the presentation of the document on different devices such as the screen, a projector, the printer, a speech device or a Braille-based device. It is used to separate *presentation* from the *structure* of a document.

CSS, like XHTML, is directly supported by web browsers. CSS files have a .css extension.

[size=4]Resources[/size]
[W3Schools]("http://www.w3schools.com/Css/default.asp") - The only good one I could find.
[CSS Validator]("http://jigsaw.w3.org/css-validator/")

If you want to create static web documents only, then XHTML + CSS is ideal and it is all that is required. All further languages described here are used to either enhance user experience or to dynamically generate XHTML/CSS on a web server.

[size=5]JavaScript[/size]

**JavaScript** is the most common implementation of the ECMAScript standard for client-side scripting of web pages (The other popular implementation is **JScript**, although most of the API is the same). JavaScript affects the *behaviour* of the web document once it is loaded. For example, handling events and responding to them such as popping up an alert box if you click a link, or hiding an element on pushing a button. In short, it is a scripting language with a C-style syntax that gives you access to the Document Object Model (DOM), and lets you make changes to it on-the-fly, in response to events. Scripting can make web pages interactive and lively, and more responsive to the user's actions.

As with XHTML and CSS, you don't need to install anything to be able to use client side scripting. Either embed the script in your XHTML page or save it as a .js file and let your XHTML link to it. The end-user will need a browser that supports scripting though. Although most modern browsers have script support, some devices such as handhelds may not. Further, a user can easily disable scripting in the browser or edit the script itself. Therefore, don't count on it to do responsible tasks. Use it only as an optional experience-enhancing feature that your web pages can very well do without.

[size=4]Resources[/size]

[W3Schools]("http://www.w3schools.com/JS/default.asp") Again
[JavaScriptKit]("http://www.javascriptkit.com/")

[size=4]ECMAScript? JavaScript? JScript? I'm Confused[/size]

Techincally speaking, the language specification is called **ECMAScript**, which standardizes the language. This scripting language can be used for any purpose, however it is more popular for use on web pages. The most common dialect of ECMAScript is **JavaScript**. This implementation is used by the Firefox (and other Mozilla products), Opera, Konqueror, Safari, etc. Microsoft's Internet Explorer and the .NET framework use the **JScript** dialect. In web browsers, these implementations come with the Document Object Model (DOM) which is an API to access and modify elements in the web page. Generally, all Javascript code *should* work with IE's JScript implementation (with minor exceptions).

[size=6]What are cookies?[/size]

HTTP Cookies are pieces of information that web sites can store on the user's web browser. Sites use these cookies to remember things about the user from the last time(s) he/she visited the site. Cookies can help in tracking information about a user, or letting the server know of some persistent information about the user or the session over multiple page requests.

Cookies can be created on-the-fly by scripting languages such as ECMAScript, or they can be sent in the HTTP Headers by a web server. However, browsers are implemented in such a way that pages or servers can only read the cookie that has been created in the same domain, to avoid security risks. However, security issues relating to cookies are still prominent (see section of security below).

[size=6]What is a web server?[/size]

When you etner a URL in your browser, the browser sends an HTTP request to a remote machine (your ISP contacts a DNS to resolve the domain name into an IP address which locates the machine). If the machine has a web server (a kind of computer program) installed on it that listens for requests, then the server will process that request and send the response, which is a bunch of HTTP Headers (meta-information about the file) and the file itself (such as an XHTML page), which is what you see in your browser. The most common web servers are Apache and Microsoft Internet Information Services.

[How Web Servers Work]("http://www.howstuffworks.com/web-server.htm")


[size=6]How do I install Apache on Ubuntu?[/size]

You can install Apache the standard way and configure it yourself, and install PHP, MySQL, mod_perl, mod_python, etc. manually: [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") - Ubuntu Community Documentation

Alternatively, you can [Install XAMPP]("http://ubuntuforums.org/showthread.php?t=223410"), which gives you Apache, MySQL, PHP and Perl all in one neat package. This is a very easy to install package for new users, but it should be used as a development environment only and should not be used as a public webserver.

[size=6]What is Server Side Scripting?[/size]

As described above, web servers accept requests for pages and send responses with the data. Server Side Scripting is a technology by which web servers use other programs such as a PHP interpreter or a Python interpreter to evaluate PHP or Python code and send the output as the response. If the PHP/Python code is made in such a way that it generates XHTML documents as the output, then it is possible to create dynamic XHTML pages. Server Side Scripts can also generate other dynamic data not limited to XHTML/CSS.

[size=5]PHP[/size]

PHP is a programming language that uses somewhat a C style syntax which is used for server side scripting. It is one of the most popular server side languages out there. The massive library of functions that comes with PHP gives it it's main feature.

[size=4]Installing PHP locally[/size]

PHP as a server side language is popularly used alongside the Apache Web Server.

Manually: [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") - Ubuntu Community Documentation
or [Install XAMPP]("http://ubuntuforums.org/showthread.php?t=223410") (Development only)

[size=4]Resources[/size]
[Practical PHP Programming]("http://hudzilla.org/phpwiki/") - PHP Tutorial (Personal Favourite)
[PHP on W3Schools]("http://www.w3schools.com/php/default.asp")
[PHP.net]("http://www.php.net") - Best reference to lookup predefined functions and modules

[size=5]Python[/size]

The Python interpreter is installed on Ubuntu by default. However, in order for it to be used as a server side language, you need a web server.

For Apache: You need mod_python. Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=91101") has some answers for you. However, if you don't want all the hassle of configuring Apache, and you only need a web server for local development rather than production, then there are easier alternatives:

You can [set up very simple web server]("http://learnpython.pbwiki.com/WebApplication"), and write simple web applications in plain CGI without mod_python. Also, there are two excellent web app frameworks for Python, [Django]("http://www.djangoproject.com/") and [Turbogears]("http://turbogears.org/"). Both come with a simple web development server.

[size=6]Databases[/size]

Once you start to use server side scripting for dynamic page generation you will soon find the need to store data on the server for later use. For example information about a user account, user generated posts/comments, etc. have to be stored somewhere. 

[size=5]SQL[/size]

**Structured Query Language** is a database language used to store data in tables of information and retrieve it. There are many implementations of SQL (such as MySQL or SQLLite). All of these implementations support  Scripting languages may provide an inbuilt interface to communicate with certain types of databases or there may be additional modules that may do so. For example, PHP provides predefined functions to access MySQL databases wheras Python comes with a module for SQLite. 

[size=4]Resources[/size]
[SQL on W3Schools]("http://www.w3schools.com/sql/default.asp") - Straightforward Tutorial to SQL in general

[size=5]MySQL[/size]
MySQL is a multithreaded, multi-user SQL database management system (DBMS) which has more than 11 million installations. The program runs as a server providing multi-user access to a number of databases.

It is a popular choice for PHP users, and it is a rather powerful choice for production, but the advanced features and multi-user environment can get overwhelming for new users.

[size=4]Resources[/size]
Manual Install: [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") - Ubuntu Community Documentation
or [Install XAMPP]("http://ubuntuforums.org/showthread.php?t=223410") (Development only). An advantage here is that it comes with phpMyAdmin, a simple graphical administration tool, which often suffices for new users.
[Databases in PHP]("http://hudzilla.org/phpwiki/index.php?title=Databases") (Includes a basic MySQL Tutorial within the topics)

[size=5]SQLite[/size]
SQLite is a software library that implements a self-contained, serverless, zero-configuration, transactional SQL database engine. It is actually a small C library that is internally linked within programs that use it, but it uses the SQL API to give it the feel of a full fledged SQL server. It is widely used in desktop applications (such as Firefox 3) and for simple web development.

SQLite has bindings for a large number of programming languages, including BASIC, C, C++, Common Lisp, Java, Delphi, Lua, Tcl, R, PHP, Perl, Ruby, Python, newLisp and Smalltalk. 

Python 2.5 comes with the SQLite preloaded. For PHP, in order to have the SQLite functions available, you must compile PHP with SQLite support, or load the SQLite extension dynamically from your php.ini. 

[size=4]Resources[/size]
[PHP with SQLite]("http://www.litewebsite.com/?c=49")
[Python with SQLite]("http://docs.python.org/lib/module-sqlite3.html")

[size=5]PostgreSQL[/size]

PostgreSQL is a powerful object-relational database management system, provided under a flexible BSD-style license. PostgreSQL contains many advanced features, is very fast and standards compliant.

PostgreSQL has bindings for many programming languages such as C, C++, Python, Java, PHP, Ruby... It can be used to power anything from simple web applications to massive databases with millions of records. 

[size=4]Resources[/size]
[Ubuntu Community Documentation]("https://help.ubuntu.com/community/PostgreSQL")
[PostgreSQL Wiki]("http://wiki.postgresql.org/wiki/Main_Page")

[size=6]What are the security risks involved when deploying web pages?[/size]

Security vulnerabilities in web applications generally occurs as a form of a code injection, that is, when a malicious user is able to exploit the application such that his harmful piece of code is executed to generate destructive results.

[size=5]Cross Site Scripting[/size]

Cross-site scripting (XSS) is a type of computer security vulnerability typically found in web applications which allow code injection by malicious web users into the web pages viewed by other users. Examples of such code include XHTML code and client-side scripts. 

For example, if a forum user posts a XHTML message with an embedded script that reads cookies stored in the browser and emails the data to him, then every user who reads this post has his/her cookies (which may contain information such as session IDs or passwords) sent to the attacker who can then use it to login under the victim's account. This is why sites like forums and wikis don't generally allow XHTML to be posted. XSS attacks are even possible via injecting CSS.

[XSS on Wikipedia]("http://en.wikipedia.org/wiki/Cross-site_scripting")

[size=5]Server Side Code Injection[/size]

Be **very careful** when using your server side code to perform actions based on user input. **Never** use functions such as PHP's eval(), which executes a string as PHP code on any variable string, especially one that is user-generated. Evaluating untrusted code can result in your entire system being compromised, everything from exposing stored passwords to deleting important data to tricking your system into logging in as a different user (this is very hard to detect). 

Also, **never** load other files to be executed (such as includes) with a variable filename, if the variable contains user supplied data. A malicious user may supply wrong data that allows sensitive files to get included (such as those that have your password stored in them). You may think you have validated your code, but attackers can find ways through many layers to get their harmful code into your innocent variable. 

As a rule of thumb, the only things you should do with variable data that comes from the user is either match it with expected values and perform your own static operations, use it in a mathematical context, or echo it back to the user. You might store this data in a database for further use, but when you retrieve this data later, make sure to follow the same rules again, or else you are vulnerable to second order attacks. 

[size=5]SQL Injection[/size]

Exploting usage of unescaped strings in a SQL query is one of the most common ways of exploiting a web application and it is something that most beginner applications  are vulnerable to.

[SQL Injection on Wikipedia]("http://en.wikipedia.org/wiki/SQL_Injection")

[size=6]Other Stuff[/size]

This is a list of links to stuff that is not described in this article. If anybody is willing to contribute some introductory writeup for these then please edit this post (or ask a moderator to do so)

[Ruby]("http://en.wikipedia.org/wiki/Ruby_programming_language")
[Beginner's Guide to CGI Scripting with Perl]("http://www.lies.com/begperl/")
[Perl CGI Programming FAQ]("http://www.perl.com/doc/FAQs/cgi/perl-cgi-faq.html")
[Java Applets]("http://en.wikipedia.org/wiki/Java_Applet")
[Java Servlets]("http://en.wikipedia.org/wiki/Java_Servlet")
[JavaServer Pages (JSP)]("http://en.wikipedia.org/wiki/JavaServer_Pages")

---

### Post by pmasiar on 2008-05-19
Good post, but you have too much bias towards PHP. PHP is popular, but it does not mean PHP is preferred way to build web apps.

**Server Side Scripting - there is a simpler way**

It is not only possible without mod_python, and without apache: it is also easier.

[http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) shows how to set up very simple web server (much simpler than apache), and write simple web app in plain CGI without mod_python.

There are two excellent web app frameworks for Python, Django and Turbogears. Both come with simple web development server, which reloads after changes (unlike Apache). Apache is excellent (and much more efficient) for production, but not for development.

Also, MySQL is way too complicated for beginner. Better way is to use SQLite DB library (not server, no administering) and object-relational mapper (ORM) which hides differences, so later you can use same code with real database, either MySQL or Postgress.

With plain PHP, it is extremely easy to create messy web app which are hard to modify and maintain. Using web app framework with superior language guides beginner without pain to superior results. Also, [Google App Engine](http://ubuntuforums.org/showthread.php?t=749285) provides free web hosting for Python apps.

Suggestions: instead of adding fluff with 'what a great post', just thank OP. Don't worry, this will be linked from FAQs.

---

### Post by drubin on 2008-05-19
Nice one. 

Should be made into a sticky.

---

### Post by tzulberti on 2008-05-20
Great guide

---

### Post by Verminox on 2008-05-20
> **pmasiar said:**
> Good post, but you have too much bias towards PHP. PHP is popular, but it does not mean PHP is preferred way to build web apps.

Well, to be honest, it is only because PHP is the only server side language I've worked with. Although I know about other options, I don't have the experience to write about it or provide useful resources without being terribly wrong.

It would be great if the community can contribute to stuff that I have missed out. Sadly this isn't a wiki, so you can either PM me or a moderator who can edit the post.

Edits: Changed JavaScript to ECMAScript as per LaRoza's suggestion. Technical error here. Also, I added some stuff from pmasiar's post, but I don't have any idea about SQLLite.... Links anybody?

---

### Post by dsiembab on 2008-05-20
What about PERL

---

### Post by Can+~ on 2008-05-20
> **Verminox said:**
> but I don't have any idea about SQLLite.... Links anybody?

Sqlite documentation:
[http://www.sqlite.org/docs.html](http://www.sqlite.org/docs.html)

Sqlite with Python (comes preloaded, module sqlite3)
[http://docs.python.org/lib/module-sqlite3.html](http://docs.python.org/lib/module-sqlite3.html)

sqlite just works with single files (or memory), and access it as if it were a full database. Works for web development, and specially good for client applications development (Firefox 3 uses sqlite3 for example)

---

### Post by Verminox on 2008-05-20
> **Can+~ said:**
> Sqlite documentation:
[http://www.sqlite.org/docs.html](http://www.sqlite.org/docs.html)

Sqlite with Python (comes preloaded, module sqlite3)
[http://docs.python.org/lib/module-sqlite3.html](http://docs.python.org/lib/module-sqlite3.html)

sqlite just works with single files (or memory), and access it as if it were a full database. Works for web development, and specially good for client applications development (Firefox 3 uses sqlite3 for example)

Thanks. I added SQLite and PostgreSQL to the list. However, I am confused by your use of the phrase *comes preloaded*. Does it mean that SQLite is installed on Ubuntu by default or just that Python comes with the module to interact with SQLite? I assumed it is the latter (as I found a few threads on the forums about 'installing' SQLite from the repos)... and in this case I couldn't find any page that would easily guide new users into installing SQLite on ubuntu.

---

### Post by LaRoza on 2008-05-20
> **dsiembab said:**
> What about PERL

tsk, tsk.

---

### Post by Verminox on 2008-05-20
> **dsiembab said:**
> What about PERL
I put two links to CGI/Perl in the last section (Other stuff). Most Perl related resources I found date back to mid-90s or even earlier and I could find no Ubuntu-Perl-CGI-HowTo. Also, the only thing I know about using Perl as a Server Side Language is mod_perl in Apache. Any other ideas?

PS: Since I am new to Perl, Ruby, etc. I can see how finding these resources as a novice Ubuntu user can be frustrating. Hopefully this thread should ease it out a bit.

---

### Post by stevescripts on 2008-05-20
Verminox - thanks, this is nicely done.

One more, re other ideas - folks are probably not aware of the tclhttpd -
[http://www.tcl.tk/software/tclhttpd/]("http://www.tcl.tk/software/tclhttpd/")

extremely easy to use webserver ...

Tcl, along with Python, Ruby, Perl, etc ... can be quite useful for web programming.

Steve

---

### Post by pmasiar on 2008-05-20
> **Verminox said:**
> *comes preloaded*. Does it mean that SQLite is installed on Ubuntu by default or just that Python comes with the module to interact with SQLite? 

SQLite is just a (C) library which reads/writes file in internal format, and has SQL API. It is not a server, no administration needed. Python bindings were available for a while (so it's stable now), and Py2.5 includes it by default.

Nice trick is, that many ORMs support it (because "from outside" it looks like SQL database (with single user and no password) so it is much easier to develop web-based DB app against SQLite than against "real" multiuser database, like MySQL. "Real" databases are set to manage multiple users, but web app has often  just single user - apache CGI script. You can create something in SQLite, copy whole database, run test, discard it and use copy to restore - it SQLite DB is just a file.

---

### Post by Verminox on 2008-05-21
pmasiar: Thanks, added the clarification in the OP.

stevescripts: I'll look into Tcl.

---

### Post by Darkade on 2008-07-29
Great Howto :D
Just one doubt, does anyone know about a good howto use xml and php. I've trying to setup a RSS feed for my site (you can go clicking in my signature in the 'mr wizard...') but I don't want to write an entry every time I post.  And I know there is a way to do it with PHP (SEE [http://www.phdcomics.com/gradfeed.php](http://www.phdcomics.com/gradfeed.php) !!) but I just can't find a HowTo I can learn. I think is with XML parsing or something like that but the how to in PHP.net is way too confusing.
So can anyone point me in the right direction please? :D thanks

By the way [my site]("http://arcadelair.homelinux.net") is built almost completely  from scratch all by my self :D:D (except for the experimental forums that's all phpbb LOL and and some CSS, still learning) Using PHP, Apache and some MySQL. :D:D Sorry I just had to say it :lolflag:

---

### Post by Reiger on 2008-07-29
> **Verminox said:**
> Generally, all Javascript code *should* work with IE's JScript implementation (with minor exceptions).

I suppose it depends on your definition of "generally", but you may want to note that specifically event handlers, and DOM modifications (especially those inside the 'style tree') are anything but portable.

For instance, if you want to look up properties about an event e; Spidermonkey (the JavaScript engine used by Firefox) will generally provide you with a different interface from that of the engine in MSIE. This starts at the very bottom level of *where* to fetch/point to your copy of the event from:
```

function simpleExample(e) {
e = e /* other browsers simply dispatch an event */ || window.event; /* MS IE does it different ... <_< */
return e;
}

```

Such a function is required with DHTML when you want to process events such as "onclick" or "onmouseup", at least if you want to keep your code portable. But this function clearly demonstrates (one of the many, but this one is probably the prime example of what any aspiring web developer will 'really feel' first).

Also: did you link to the Mozilla guides regarding their JavaScript engine? Those are absolute lifesavers!

[http://developer.mozilla.org/en/docs/SpiderMonkey](http://developer.mozilla.org/en/docs/SpiderMonkey)

---

### Post by Reiger on 2008-07-29
> **Darkade said:**
> Great Howto :D
Just one doubt, does anyone know about a good howto use xml and php. I've trying to setup a RSS feed for my site (you can go clicking in my signature in the 'mr wizard...') but I don't want to write an entry every time I post.  And I know there is a way to do it with PHP (SEE [http://www.phdcomics.com/gradfeed.php](http://www.phdcomics.com/gradfeed.php) !!) but I just can't find a HowTo I can learn. I think is with XML parsing or something like that but the how to in PHP.net is way too confusing.
So can anyone point me in the right direction please? :D thanks


PHP has an excellent DOMDocument API capable of processing HTML, and various flavours of XML. Including validating it against a DTD, Schema or RelaxNG Schema. Also it nicely fits in with the PHP XSL extension which exposes the XSLTProcessor class. Now that's a nifty tool, because it allows you to do XSLT Processing on the server side, which has the benefit of "only one implementation to worry about" (ever noticed how MSIE does 'it' different from Opera which does it different from Firefox?).

So what you can do is the following: have a piece of XML be translated at runtime into corresponding XHTML using an XSLT stylesheet...

For references see the PHP manuals (I use PHP 5.x myself) and W3C schools (again) for the XSLT. A simple Google search "PHP 5 DOMDocument" & "XSLT W3C Schools" should suffice for getting what you need. IIRC the W3C schools come out on top upon the simple Google query "XSLT" also, but don't quote me on that...

> 
By the way [my site]("http://arcadelair.homelinux.net") is built almost completely  from scratch all by my self :D:D (except for the experimental forums that's all phpbb LOL and and some CSS, still learning) Using PHP, Apache and some MySQL. :D:D Sorry I just had to say it :lolflag:

I briefly looked at your site; and as my standard action is... "upload it to the W3C validator" (heh, I'm using Opera; it's only a right & left click away ;-)) What can I say? You should really see the report. <_<

---

### Post by Darkade on 2008-07-29
> **Reiger said:**
> I briefly looked at your site; and as my standard action is... "upload it to the W3C validator" (heh, I'm using Opera; it's only a right & left click away ;-)) What can I say? You should really see the report. <_<
yes I know :( but much of that CSS ain't mine, as I said, but I don't know how to correct it, again as I said I'm Still learning CSS LOL

And thanks I will look at your references as soon as I get home :D

---

### Post by LaRoza on 2008-07-29
> **Darkade said:**
> yes I know :( but much of that CSS ain't mine, as I said, but I don't know how to correct it, again as I said I'm Still learning CSS LOL

And thanks I will look at your references as soon as I get home :D

You shouldn't use what you don't understand. Take my site for example ([http://laroza.freehostia.com](http://laroza.freehostia.com)). It isn't flashy, and many people think it is too plain. However, it is 100% valid code and more usable than most sites.

Do not overstep. Use what you know.

---

### Post by Darkade on 2008-07-29
Thank you both LaRoza and Reiger, in fact I'm now going into debuging my site :D.
Maybe I'll drop my CSS two colums and come up with one my self :D
Later this week I'll see that RSS feed thing :D

**EDIT:** Hey! I finished! :D:D now I have no URI problems, except for the ones from embeding the Youtube videos... which I'm now looking how to solve; and the damn CSS, I'll probably come up with my own css columns, the advantage of my site is that everything is in modules :P
But for every other thing
> This Page Is Valid HTML 4.01 Transitional!
:lolflag:

---

### Post by dsiembab on 2008-07-30
a good way for debugging is to download the web developer add-on to firefox. You can check local pages ( pages that are just on your computer ) for xhtml compliance and css compliance with the tools button you can even edit the css and html live with the toolbar. The way I started learning css and xml was at w3schools.com they have excellent tutorials and also tizag.com they also have good tutorials. For css I recommend buying O'Reilly's Cascading Style Sheets a definitive guide, I found my copy used for about 12 dollars worth every penny. If yo are haveing URI problems try using full paths on your webserver
i.e. /var/html/www/the page you use for dynamic stuff. There are good mysql php classes out there and page template php classes too. You can check them out at php classes.com and also remember google is your friend. Devnet.com is also a good site.

---

### Post by days_of_ruin on 2008-07-30
> **dsiembab said:**
> What about PERL























no.

---

### Post by Ademan on 2008-07-30
> **days_of_ruin said:**
> no.

:lolflag:

Anywho, mod_python is considered bad juju by alot of people.

> 
At #python.web we warn against using mod_python. Here's a handful of the reasons:

   1. It complicates your upgrade process, as versions of Python, Apache, and mod_python must be coordinated. The appropriate versions are not always available for some combinations.
   2. It makes user separation or chrooting of webapps impossible.
   3.

      If you're using PHP and mod_python, and you're using MySQL in both languages, you generally must coordinate versions of MySQL as well, or suffer lots of configuration headaches. The same applies for many other popular C libraries.
   4. Apache's processes will be heavier because you're embedding a python interpreter in it.
   5. Debugging a wsgi app is a lot easier.
   6. mod_python is a module for Apache, which is tested less than other well known Apache modules such as mod_proxy. Because of this reason the server administrator (which might not be you) might not want to install this module for security reasons.
   7. You wont find a lot of hosting companies offering mod_python, which makes wsgi applications (which can be deployed through several ways) very flexible in your quest for a hosting company.
   8. Using nginx as a front-end is usually a more speedy and flexible solution. 


From [mod_python entry in python wiki]("http://wiki.python.org/moin/PoundPythonWeb/mod_python")

Anywho, WSGI is considered the way to go these days for python based web development.  Most frameworks support wsgi.

---

### Post by Mickeysofine1972 on 2008-07-30
Ok here is what I use at work, (I develop for the web btw)


[LIST]
[*]Editor: gPHPEdit (in the ubuntu repos)
[*]Web framework: code igniter (its PHP and is supper for making quick efficient and secure websites)
[*]Apache2 server with PHP5 and MySql 5 running.
[/LIST]

I also edit my virtual hosts to point to my home 'Public' folder where I can edit my php / ECMAScript without worrying about permissions problems. I also edit my ECMAScript with gPHPEdit with the C/C++ code hignlighting on, (ECMAScript is part of the C family of languages to it looks fine).

I also make my login account part of the www-data group and set the web folders to 774 permissions.

If your concerned about w3c then install the web developer plugin for Firefox, it has a tools menu that will even validate offline pages and css. Also, if your gonna do any AJAX the firebug plugin makes this real easy as well as making CSS layout easy to experiment with.

As well as this I have a main ubuntu box running apache2 with the subversion module running a http SVN repo so I can keep running revisions of the sites/software I build. As I work along with another developer we can easily work on the same project and share changes easily.

For your page designs I recommend Inkscape as I have had comments from the designers in the agency I work for who have seen me using it and they say they thing its as good as Adobe Illustrator which is popular for advertising designers in the UK. And also it goes without saying that in the right hands The GIMP totally rocks.

Also, as far as I have seen, in the UK there isn't a great outcry for Python based websites and if your going to develop I would recommend PHP purely because your more likely to get work with it, bearing in mind that there millions of websites running PHP applications.

Well thats works for me, take a look at my website([http://www.mikehibbert.me.uk](http://www.mikehibbert.me.uk)) which is made using all the tools I have metioned.

Mike

---

### Post by tatewaki on 2008-10-25
I'm missing any information on java and .NET with also could be used to make server side web pages.

---

### Post by drubin on 2008-10-25
> **Verminox said:**
> 
[Java Applets]("http://en.wikipedia.org/wiki/Java_Applet")
[Java Servlets]("http://en.wikipedia.org/wiki/Java_Servlet")
[JavaServer Pages (JSP)]("http://en.wikipedia.org/wiki/JavaServer_Pages")

> **tatewaki said:**
> I'm missing any information on java and .NET with also could be used to make server side web pages.

It is there just very basic. Maybe Vermminox is not a java developer... 

Also I don't see .net having a place on Linux web servers... :(

---

### Post by LaRoza on 2008-10-25
> **drubin said:**
> 
Also I don't see .net having a place on Linux web servers... :(

Mono [http://www.codeproject.com/KB/cross-platform/introtomono2.aspx](http://www.codeproject.com/KB/cross-platform/introtomono2.aspx)

---

### Post by drubin on 2008-10-25
> **LaRoza said:**
> Mono [http://www.codeproject.com/KB/cross-platform/introtomono2.aspx](http://www.codeproject.com/KB/cross-platform/introtomono2.aspx)

I know about mono...

But to me this would be like installing wine so that you could run notepad/sol.exe

---

### Post by LaRoza on 2008-10-25
> **drubin said:**
> I know about mono...

But to me this would be like installing wine so that you could run notepad/sol.exe

Not really. .net and mono are pretty much the same concept. You need .net or you need mono to use the same code (plus the server). Wine would be adding another layer.

---

### Post by drubin on 2008-10-25
> **LaRoza said:**
> Not really. .net and mono are pretty much the same concept. You need .net or you need mono to use the same code (plus the server). Wine would be adding another layer.
You want to run MS apps/code use MS(Windows) servers. I just felt it was not needed to have a fully functional tutorial to using  .net (asp) code on a Linux forum. 

This was my personal point if others feel I am wrong and we should support it then go ahead and write the tutorial and add it to the sticky.

---

### Post by LaRoza on 2008-10-25
> **drubin said:**
> You want to run MS apps/code use MS(Windows) servers. I just felt it was not needed to have a fully functional tutorial to using  .net (asp) code on a Linux forum. 

This was my personal point if others feel I am wrong and we should support it then go ahead and write the tutorial and add it to the sticky.

.NET or ASP? Make up your mind ;)

ASP is Windows only as far as I know.

.NET and mono are implemtations of the same standard, and one can use several languages on them.

---

### Post by drubin on 2008-10-25
> **LaRoza said:**
> .NET or ASP? Make up your mind ;)

ASP is Windows only as far as I know.

.NET and mono are implemtations of the same standard, and one can use several languages on them.

In my mind when it comes to using .NET I just assume people are talking about ASAP.NET (some sort of horrible VB.NET implementation).

mono is not an implementation so much as and interpreter/compiler for .NET on linux but it is still a MS language and a horrible one at that. 

Also this would be the first time I have hard of Microsoft(the .NET part) and "standard" being used in the same sentence.:lolflag:

---

