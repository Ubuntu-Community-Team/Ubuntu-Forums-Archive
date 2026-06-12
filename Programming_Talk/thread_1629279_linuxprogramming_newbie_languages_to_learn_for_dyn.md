---
title: "linux/programming newbie: languages to learn for dynamic website design?"
date: 2010-11-23
forum: Programming Talk
---

### Post by UbuNoob001 on 2010-11-23
So a friend and I are new-ish to linux (I am reasonably comfortable with basic /etc text editing, command admin). We are, however, *completely* new to programming and (x)html. 

We have a few (what we think are) interesting ideas for dynamic websites. 

Ideally we would like to develop our own course of study to get to the point where we have a basic understanding of programming so that our adventures in the programming of a dynamic website would be possible. 

Here is what I would like to do: 
1. learn the basics of programming with a language that would teach good code habits and fundamental understanding. 
2. become comfortable with (x)html
3. learn another language for the extension of (x)html into a dynamic data-heavy website. 

**Much of what we need learn to do is the following: use daily updated public-domain data from several other sites, manipulate that data algorithmically, which would then yield updating output on our site. **

**Question** could you please suggest a way about going about 1>2>3? 

note: Ideally the language of (1) would be something that would not be "wasted" just on web design etc. As a language, C really appeals to me. However, if learning this wouldn't lend itself to being helpful in learning another language for webdesign maybe I shouldn't use it(?).
       If (1) weren't to be C, what language would be funadmental enough to teach good coding but also be helpful in learning (3)

---

### Post by DangerOnTheRanger on 2010-11-23
If you're new at programming, and just want to make a dynamic web site, *forget *about learning anything besides (X)HTML for now.
C is no good for web programming, in my opinion, and most everyone else. It's just too hard.

You just need a Content Management System(CMS) for having a dynamic web site.

Drupal([http://drupal.org]("http://drupal.org/")) is what I use(at [http://openblox.sf.net]("http://openblox.sf.net/")), and is very popular for medium to large web sites(Canonical uses it, among others.)

Joomla!([http://joomla.org]("http://joomla.org/")) is popular for blogs, and smaller web sites. I don't know much about it, though.

Those are the big two. Others include Plone, PHP-Fusion, DotNetNuke, Django-CMS, and WordPress. See:

 [http://en.wikipedia.org/wiki/List_of_content_management_systems#Free_and_open_source_software](http://en.wikipedia.org/wiki/List_of_content_management_systems#Free_and_open_source_software)

for an *truly exhaustive *list.

---

### Post by UbuNoob001 on 2010-11-23
> **DangerOnTheRanger said:**
> If you're new at programming, and just want to make a dynamic web site, *forget *about learning anything besides (X)HTML for now.
C is no good for web programming, in my opinion, and most everyone else. It's just too hard.

You just need a Content Management System(CMS) for having a dynamic web site.

Drupal([http://drupal.org]("http://drupal.org/")) is what I use(at [http://openblox.sf.net]("http://openblox.sf.net/")), and is very popular for medium to large web sites(Canonical uses it, among others.)

Joomla!([http://joomla.org]("http://joomla.org/")) is popular for blogs, and smaller web sites. I don't know much about it, though.

Those are the big two. Others include Plone, PHP-Fusion, DotNetNuke, Django-CMS, and WordPress. See:

 [http://en.wikipedia.org/wiki/List_of_content_management_systems#Free_and_open_source_software](http://en.wikipedia.org/wiki/List_of_content_management_systems#Free_and_open_source_software)

for an *truly exhaustive *list.

Thanks for the suggestion: just as an update (which I just included in an edit), much of what we are trying to get the website to do is : use daily updated public-domain data from several other sites, manipulate that data algorithmically, which would then yield updating output on our site. 

 Thanks again for the suggestions.

---

### Post by SeijiSensei on 2010-11-23
> **UbuNoob001 said:**
> Thanks for the suggestion: just as an update (which I just included in an edit), much of what we are trying to get the website to do is : use daily updated public-domain data from several other sites, manipulate that data algorithmically, which would then yield updating output on our site. 

Thanks again for the suggestions.

I write sites in PHP and could probably write the backend for what you'd like to do in that language.  You can use functions in PHP to read a webpage or other online data source into an array, parse the text as needed to extract the data, manipulate the data with formulas, and display it as an HTML document.

You can get into enormous arguments with professional programmers about whether you will develop "good code habits" writing in PHP.  I don't really care about these religious issues; I use PHP because I know it well and can build powerful dynamic websites with it.

You might browse [these books](http://oreilly.com/php/index.html) from O'Reilly, an excellent technical publisher with a focus on open source applications.

---

### Post by DangerOnTheRanger on 2010-11-23
All that is possible with a CMS. you just write a PHP extension for that CMS that implements your intended behavior.

Plus, you get all the benefits that a CMS has over raw PHP.

---

### Post by UbuNoob001 on 2010-11-23
> **SeijiSensei said:**
> I write sites in PHP and could probably write the backend for what you'd like to do in that language.  You can use functions in PHP to read a webpage or other online data source into an array, parse the text as needed to extract the data, manipulate the data with formulas, and display it as an HTML document.

You can get into enormous arguments with professional programmers about whether you will develop "good code habits" writing in PHP.  I don't really care about these religious issues; I use PHP because I know it well and can build powerful dynamic websites with it.

You might browse [these books](http://oreilly.com/php/index.html) from O'Reilly, an excellent technical publisher with a focus on open source applications.

Great. For the sake of comparison, would there be another language which would manipulate this type of data as successfully as PHP? Is there one which would produce less of the "religious" worries regarding code-habits from developers? 

Many thanks, great suggestions ill check out O'Reilly

---

### Post by DangerOnTheRanger on 2010-11-23
Easy. Python([http://python.org]("http://python.org/")).
Available on pretty much every system, including the PlayStation, IIRC.
Also, Plone is written in Python.

---

### Post by wrtpeeps on 2010-11-23
It will be an unpopular opinion, but I really like ASP.NET MVC for websites.

I'm not sure how well supported (if even) it is by the Mono project, so it may not be suitable for you, but I thought I'd throw it out there for you just in case.

Clean code and good separation of concerns (that's where the MVC comes in).

---

### Post by worseisworser on 2010-11-24
> **UbuNoob001 said:**
> So a friend and I are new-ish to linux (I am reasonably comfortable with basic /etc text editing, command admin). We are, however, *completely* new to programming and (x)html. 

We have a few (what we think are) interesting ideas for dynamic websites. 

Ideally we would like to develop our own course of study to get to the point where we have a basic understanding of programming so that our adventures in the programming of a dynamic website would be possible. 

Here is what I would like to do: 
1. learn the basics of programming with a language that would teach good code habits and fundamental understanding. 
2. become comfortable with (x)html
3. learn another language for the extension of (x)html into a dynamic data-heavy website. 

**Much of what we need learn to do is the following: use daily updated public-domain data from several other sites, manipulate that data algorithmically, which would then yield updating output on our site. **

**Question** could you please suggest a way about going about 1>2>3? 

note: Ideally the language of (1) would be something that would not be "wasted" just on web design etc. As a language, C really appeals to me. However, if learning this wouldn't lend itself to being helpful in learning another language for webdesign maybe I shouldn't use it(?).
       If (1) weren't to be C, what language would be funadmental enough to teach good coding but also be helpful in learning (3)

C isn't suitable for this kind of work. Some suggestions are Python, Common Lisp, Ruby, PHP, Perl.

---

### Post by DanielWaterworth on 2010-11-24
People who know me would be surprised to hear that I'm not about to say something along the lines of "you should be using python and anything else is the spawn of satan".

I think it's more important to familiarise yourself with all of the components of the project than to worry about the language you'll use. Use whatever you find comfortable, there aren't many languages out there that you couldn't write a website in.

If you're new to web development, I'd recommend learning about XSS, CSRF and SQL injection before you begin.

---

### Post by GenBattle on 2010-11-24
+1 for Python.

It has just about every library you could ever need for web interaction and data processing (I built an app to query a server for a JSON stream and do a bunch of processing). It also teaches you/has facilities for good habits such as indentation, documentation, and unit testing.

It's also very easy to get started with if you just start messing around with the interactive interpreter. You can literally build and run a program one line at a time, which is great when you're experimenting and exploring.

---

### Post by directhex on 2010-11-24
> **wrtpeeps said:**
> It will be an unpopular opinion, but I really like ASP.NET MVC for websites.

I'm not sure how well supported (if even) it is by the Mono project, so it may not be suitable for you, but I thought I'd throw it out there for you just in case.

Clean code and good separation of concerns (that's where the MVC comes in).

ASP.NET MVC 1 and 2 are part of Ubuntu, and distributed with the Mono source code. Microsoft released them under a Free Software license. Package names are libmono-system-web-mvc1.0-cil and libmono-system-web-mvc2.0-cil

---

### Post by UbuNoob001 on 2010-11-24
> **GenBattle said:**
> +1 for Python.

It has just about every library you could ever need for web interaction and data processing (I built an app to query a server for a JSON stream and do a bunch of processing). It also teaches you/has facilities for good habits such as indentation, documentation, and unit testing.

It's also very easy to get started with if you just start messing around with the interactive interpreter. You can literally build and run a program one line at a time, which is great when you're experimenting and exploring.


So you would agree that while I might, down the line, have an interest in programming linux applications, since my immediate priority is to learn
1. the basics of programming (in general) and to 
2. learn a language that would be suitable for helping us manipulate constantly updating data from websites

that learning Python would satisfy both conditions? 

Again, and keep in mind I am completely new to programming, but would Python be helpful in 
1. fetch data from site X,Y,Z
2. manipulate data D(x,y,z) into A
3. send A to an updating index.(x)html ?

Or will many other languages/programs need to be used to aid in such? 

Thanks again for helping a total newbie :)

---

### Post by DangerOnTheRanger on 2010-11-24
> **DanielWaterworth said:**
> People who know me would be surprised to hear that I'm not about to say something along the lines of "you should be using python and anything else is the spawn of satan".

I think it's more important to familiarise yourself with all of the components of the project than to worry about the language you'll use. Use whatever you find comfortable, there aren't many languages out there that you couldn't write a website in.

If you're new to web development, I'd recommend learning about XSS, CSRF and SQL injection before you begin.

You don't have to worry about that(for the most part) if you use a CMS.

Also, no, no language besides Python is needed for what you want to do.
But if you want to update the content without refreshing the page, you will need to learn Javascript and its JQuery extension.

---

### Post by UbuNoob001 on 2010-11-24
> **DangerOnTheRanger said:**
> You don't have to worry about that(for the most part) if you use a CMS.

Also, no, no language besides Python is needed for what you want to do.
But if you want to update the content without refreshing the page, you will need to learn Javascript and its JQuery extension.

Great. I suspect Python is where I should start. There is so much I need to learn its rather overwhelming. 

Before I mark this thread as solved, what we are talking about (re: the functionality of Python) is not something that could be done with C correct?

edit: or say PHP/Ruby?

---

### Post by DangerOnTheRanger on 2010-11-24
If you mean Python's features, then yes.
If you mean Python is the only solution to your problem, then no.

---

### Post by UbuNoob001 on 2010-11-25
I have decided to go with Python. Thanks to everyone for their suggestions and support.

---

### Post by ZaHACKieL on 2010-11-25
I just want to add that even when I use PHP for making websites, I with Python as your choice because, depending on your line of work, it will be useful for more things besides web. Let's say, for scientific work we use Python a lot so if you learn it you may use it in other areas.

BUT I think I have to say that I've found more documentation for PHP in the web, specially when you look for things like MySQL, Apache, JQuery...

Maybe I'm wrong but at least that's my experience with it.

Good luck and come back here if you need more help

---

### Post by CptPicard on 2010-11-25
I'm generally a Python guy but due to work I've spent this autumn mostly with Ruby on Rails. It's worth looking into as well as it is probably the most popular dynamic-typed-language web framework at the moment.

My language preference is still with Python though...

---

### Post by DangerOnTheRanger on 2010-11-27
> **ZaHACKieL said:**
> I just want to add that even when I use PHP for making websites, I with Python as your choice because, depending on your line of work, it will be useful for more things besides web. Let's say, for scientific work we use Python a lot so if you learn it you may use it in other areas.

BUT I think I have to say that I've found more documentation for PHP in the web, specially when you look for things like MySQL, Apache, JQuery...

Maybe I'm wrong but at least that's my experience with it.

Good luck and come back here if you need more help

Python has a built-in SQLite binding(sqlite3), Apache supports Python with mod_python, and JQuery is just a Javascript UI library; he's(the OP) is talking about a* server-side *language...

---

### Post by DangerOnTheRanger on 2010-11-27
> **DangerOnTheRanger said:**
> You don't have to worry about that(for the most part) if you use a CMS.

Also, no, no language besides Python is needed for what you want to do.
But if you want to update the content without refreshing the page, you will need to learn Javascript and its JQuery extension.

Ach! Not JQuery, *AJAX! *Just one of those days, I guess...

---

### Post by UbuNoob001 on 2010-11-27
> **ZaHACKieL said:**
> I just want to add that even when I use PHP for making websites, I with Python as your choice because, depending on your line of work, it will be useful for more things besides web. Let's say, for scientific work we use Python a lot so if you learn it you may use it in other areas.

BUT I think I have to say that I've found more documentation for PHP in the web, specially when you look for things like MySQL, Apache, JQuery...

Maybe I'm wrong but at least that's my experience with it.

Good luck and come back here if you need more help


ZaHACKiel,
   Yeah, I think this (Python) is the best way to go for that purpose. As it is my first language, and I would like to be able apply my learning to non web-based applications as well. From what I have heard given its flexibility, power, and ease-of-learning, this is for now a good choice. 
  Thanks for the support and will check back here in the forums for additional help, im sure ill need it !  :)
    Ubu

---

