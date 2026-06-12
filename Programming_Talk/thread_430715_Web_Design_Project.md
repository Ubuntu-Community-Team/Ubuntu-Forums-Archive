---
title: "Web Design Project"
date: 2007-05-02
forum: Programming Talk
---

### Post by cisforcojo on 2007-05-02
Hey guys,

I've got a fairly big web design project (for me considering the last I did any web design was... 10 years ago)

What I need is a user system with database support, email support, and a "news page" that can be automatically updated by the site. 

I really know nothing of databases in linux. I was planning on looking into MySQL and use APACHE for the server. 

I'm also planning on using Aptana for the web design. I'd like to use Flash but that seems weak at best for Ubuntu right now.

This is just a fun, personal project. Any help would be greatly appreciated!!!

---

### Post by Tomosaur on 2007-05-02
Well, Linux has the latest flash player - but as far as creating flash media goes, you may well be out of luck, as far as I'm aware there are no flash creation apps available for Linux at this time, excepting [OpenLaszlo](http://www.openlaszlo.org/), which may in fact be perfectly suited for your needs :P

---

### Post by cisforcojo on 2007-05-02
Yeah I've got the latest flash installed cuz I love that eyecandy. 

Anyway, I'm brand new to this and OpenLazlo looks really good. Basically, my HTML skills at this point are, I can make a blank HTML page with some text. Nothing. Gonna be fun to learn to get all this working together.

---

### Post by Tomosaur on 2007-05-02
> **cisforcojo said:**
> Yeah I've got the latest flash installed cuz I love that eyecandy. 

Anyway, I'm brand new to this and OpenLazlo looks really good. Basically, my HTML skills at this point are, I can make a blank HTML page with some text. Nothing. Gonna be fun to learn to get all this working together.

There are lots of WYSIWYG web design packages out there, so it's well worth 'shopping around' for one that suits you. When it comes down to it though, there's no substitute for learning how to hand-code. WYSIWYG editors are often criticised for generating 'messy' code, which ultimately means the final product may:
a) load slower
b) look different on different browsers / platforms

But yeah, OpenLaszlo is very, very interesting. I've played with it myself, although have never done anything serious with it. I'm not a big fan of 'flash only' websites - many people don't use flash, and too much of it can just look very tacky. If you can find the right balance, then you can certainly make a very interesting site. OpenLaszlo allows you to combine a lot of different aspects of web design, and it's fairly simple to get good results fast.

---

### Post by cisforcojo on 2007-05-02
Yeah I agree hard-coding is the best. Do you have any advice on where to start for building a user system for a website?  Or for generating emails?

---

### Post by Tomosaur on 2007-05-02
> **cisforcojo said:**
> Yeah I agree hard-coding is the best. Do you have any advice on where to start for building a user system for a website?  Or for generating emails?

Well as you've probably guessed, it's no easy feat to sort all of that yourself. There are probably a few open-source projects available to you, but I don't know of anything specific, sorry. I had to create a user/database combo system myself a few weeks ago, I used apache, php, and postgresql everything myself, but if you have no experience with it then it's hard to reccommend anything. There's a lot of theory involved which you'll need to understand fairly well before attempting anything serious, as you have a responsibility to protect user's data, identity, etc etc. The best solution would be to just pick and choose between already available software, but again, I don't know of anything specific to recommend, sorry.

---

### Post by AdamG on 2007-05-02
What you need is a web application framework. 

Ruby on Rails has all the buzz, but Django is solid too. I'm a Django fan myself. It has built-in users, email, and everything is dynamically generated; it runs on Apache with mod_python and the Python language itself, of course. RSS, OpenID and PDF generation is all very easy to add to your already-existing application, meaning it can "grow" with you as you build the site. 

I don't know all that much about RoR so I'll refrain from commenting on the technical aspects, but there are some pretty nifty RoR sites out there too. 

Hand-coding user authentication, email and dynamic generation support is exhilerating to do once - and exactly once. I'd look into a WAF if I were you - you should look into learning to do these things manually later on, but they can help you get started.

---

### Post by yanike on 2007-05-04
Checkout my LInux help thread

[http://www.winmatrix.com/forums/index.php?showtopic=12163](http://www.winmatrix.com/forums/index.php?showtopic=12163)



Yes! There is a flash alternative for Linux. It's called SWiSH Max which I think is better than Flash for beginners and advanced users.  I've created all my sites using it.  You need CrossOver Office Professional to run it though. Find CrossOver Pro here -> [http://www.codeweavers.com/](http://www.codeweavers.com/)

Link to my SWiSH Max thread -> [http://www.winmatrix.com/forums/index.php?showtopic=13130](http://www.winmatrix.com/forums/index.php?showtopic=13130)


I update my thread all the time.  You will find alot of great information on it :)

O. L.,
Yanike
[http://www.yanike.com](http://www.yanike.com)

---

### Post by cisforcojo on 2007-05-05
re protecting their identity, I actually DON'T have that much responsibility to do so. That kind of mentality doesn't really exist here and this site isn't commercial. Just for fun and is a learning experience for me. I appreciate everyone's help though. This definitely isn't easy, but it is definitely fun. Before this I was working on the pythonchallenge and was having a blast. If you haven't tried it, you should. It's one of the most creative sites I've ever seen.

---

### Post by wolfear on 2007-05-08
You might try a simple CMS portal written in php with mysql backend?
the one I generally recommend is here:
[http://ravenphpscripts.com]("http://ravenphpscripts.com")
I am pretty sure it has all the functions you need built in and you wont need to add a bunch of extras on your server (the new version does require php "short open tags" to be on for some odd reason).
The modular design allows you to customize just about anything with a bit of php/mysql knowledge.
Nearly all templates are mostly html so it's easy to create a custom look and flash is easy to insert (so i have heard..don't care much for flash personally, but it does add a bit of spice if used sparingly).

If you are just looking to add a bit of motion to your pages and not a full animation, you could look into animated gifs. I have no clue if there is a program in Linux to make them. Gimp might, I haven't played with that part of it yet.

If you are dead set on hand coding everything and want to use the framework idea, you could also check out Code Igniter
[http://www.codeigniter.com/]("http://www.codeigniter.com/")
It's an easy to learn php framework with quite a few nifty add ons to make life easy.

Just a few more options.

---

