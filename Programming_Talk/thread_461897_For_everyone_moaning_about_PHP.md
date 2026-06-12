---
title: "For everyone moaning about PHP"
date: 2007-06-02
forum: Programming Talk
---

### Post by hagen00 on 2007-06-02
[qcodo.com]("http://www.qcodo.com")

Yes, this is the answer...

---

### Post by Mirrorball on 2007-06-02
There are several answers actually:
[http://framework.zend.com/](http://framework.zend.com/)
[http://codeigniter.com/](http://codeigniter.com/)
[http://www.cakephp.com.br/](http://www.cakephp.com.br/)
[http://www.symfony-project.com/](http://www.symfony-project.com/)
[http://www.pradosoft.com/](http://www.pradosoft.com/)

---

### Post by durus on 2007-06-02
What do you think about Zend framework ? I want to start use a framework but can't chose witch to use, do you think that Zend framework will be like a standard framework for php as it is Zend that holds that project?

---

### Post by Mirrorball on 2007-06-02
Zend Framework is very good, but slow. I only wish it were faster.

---

### Post by hagen00 on 2007-06-03
The other frameworks are all blown out of the water by Qcodo in my opinion. CodeIgniter is quite nice and clean, but you still have to do all the work yourself. Cake is bloated and like many of the other frameworks, it does all its stuff at runtime (sorry for the poor technical language, but this is how I understand it). Qcodo does code generation, meaning that there are no performance issues, because run time stuff is minimzed. 

Qcodo's code generation is amazing - so much of what you need is auto generated for you based on your data model in a very clean way. 

I've looked at a lot of frameworks (not in too much detail) but the one that blew me away was Qcodo.

---

### Post by hagen00 on 2007-06-03
[http://www.qcodo.com/documentation/article.php/6]("http://www.qcodo.com/documentation/article.php/6")

This explains it...

---

### Post by barmazal on 2007-06-03
everyone moaning PHP is not MVC language when language cannot be MVC so you should speak about frameworks and not PHP itself since all of these languages are C libraries.

anyway, after taking a brief look on all these frameworks i would go for Zend since big company+PHP inventors behind the product. Prado was existing since it looks exactly as .NET.


my bet would be modX, it's half framework half CMS ... makes job easy for designers and webmasters while gives certain freedom for developers

---

### Post by mech7 on 2007-06-03
> **hagen00 said:**
> The other frameworks are all blown out of the water by Qcodo in my opinion. CodeIgniter is quite nice and clean, but you still have to do all the work yourself. Cake is bloated and like many of the other frameworks, it does all its stuff at runtime (sorry for the poor technical language, but this is how I understand it). Qcodo does code generation, meaning that there are no performance issues, because run time stuff is minimzed. 

Qcodo's code generation is amazing - so much of what you need is auto generated for you based on your data model in a very clean way. 

I've looked at a lot of frameworks (not in too much detail) but the one that blew me away was Qcodo.

I am not sure what you mean by code generation but if it is the same as scaffolding then cake-php can do this too.. You can bake the scaffolding code to get a starting point :) I am trying out Zend Framework now but so far i like Cake better.

---

### Post by pmasiar on 2007-06-03
> **barmazal said:**
> everyone moaning PHP is not MVC language when language cannot be MVC so you should speak about frameworks and not PHP itself since all of these languages are C libraries.

Of course no language is MVC by itself. But it makes difference *how* are those libraries glued together, how readable is the resulting code. Even if two languages are Turing-complete, it does not mean usability of the code is the same - far from that.

PHP was good option for beginners couple years ago before Rails and Django and TurboGears. Especially Python is more "universal" language than PHP, once learned it can be used way beyond web applications.

Obviously PHP is still hugely popular, and will remain so for some time, no doubts. But if newbie can with the little bit more intellectual efforts (for creating web pages) learn Python instead of PHP, I would suggest to give preference to Python based on wider usability of the language. Unless, of course, said beginner wants to participate in a web project which is written in PHP - then the choice is obvious.

If, on the other side, beginner wants to participate in OLPC or Ubuntu, Python is obviously better choice, right?

Each language is best tool in some niche. Some niches expand, others shrink - that's life, and we need to be prepared for change. :-)

---

### Post by barmazal on 2007-06-04
you said Python and Ruby are dynamic MVC languages! 

PHP was good for beginners? PHP will remain web standard for a while with all due respect to ROR, Turbo Gears and Django propaganda there are no real time proof to their superiority, no large amount of huge sites powered by those, not sure what Google and NASA do using Python but it's written on Python's website.

Just to compare Joomla is one of PHP CMSes while it has same amount of users as Python website. I won't got to php.net coz it's not fair.

all these cross platform stuff doesn't work on me, since 98% of world still using Windows PC and very small amount of MACS. The only importance Linux currently has it hosting Apache+PHP+mySQL websites when again PHP is server side language.

Without PHP 50% of Linux users will turn to Windows, since MAIN LINUX CUSTOMERS ARE HOSTING COMPANIES. Can you say the same about Python? I would assure you that much more would prefer LAMP with PHP over Python preinstalled on any Linux.

If you ask me Python users are just those who never achieved noting in PHP or ASP or Java and got frustrated and turned to yet another language. coz again THERE ARE PHP FRAMEWORKS WITH MVC MODEL and even some of these not require a line of php code just using it's API.

good luck promoting Python, hopefully you will find not guy like me who uses .NET but real PHP user who can smash Python once for all.

---

### Post by hagen00 on 2007-06-04
> **mech7 said:**
> I am not sure what you mean by code generation but if it is the same as scaffolding then cake-php can do this too.. You can bake the scaffolding code to get a starting point :) I am trying out Zend Framework now but so far i like Cake better.

Take a look at the link i posted before. Code generation means that hard code - classes, functions views - all of it. Because it is hard code, it's quicker and easier to extend (just extend a generated class). Simple as that I think - take a look at the link i posted. Mike Ho explains it much better than i can.

---

### Post by Znupi on 2007-06-04
> **hagen00 said:**
> [qcodo.com]("http://www.qcodo.com")

Yes, this is the answer...
So, what? This is like a wysiwyg editor for PHP? Geez, people, these things are evil, it's a thousand times better if you learn to code yourself!

---

### Post by hagen00 on 2007-06-04
WYSYWIG editor for PHP???? You're joking right?

---

### Post by Znupi on 2007-06-04
I don't know, I just read the title: "Code Generator". A.k.a. it generates code, so you don't have to write it yourself. Correct me if I'm wrong.

---

### Post by hagen00 on 2007-06-04
Ok, i'll try and explain a little. 

1. You create you DB - and you are forced to do it in the best possible way. Set up foreign keys, set up many to many tables properly, manage inheritance properly. 

2. You run the code generator. It then creates classes, functions (an amazing amount of functions - more than just create, read, update, delete). All there for you. No need to hand code the classes. 

3. It creates form drafts. I.e. views that you can implement e.g. data grids with pagination, filtering, ajax enabled

4. You then extend the classes to put in your specific business logic. However thank goodness, you don't have to do any mundane create, edit, delete or read functions. They are all there.

More than that, Qcodo uses a beatiful MVC implementation that lets you write really clean and easily maitainable code that seperates logic and presentation as much as possible. 

We've written some large systems using our own approach (using classes, but not a MVC approach). It's really messy. After writing Qcodo applications, I've seen the light. Just so much cleaner. Obviously you can have your own methodology for writing PHP apps, but Mike Ho knows much more than I do about code, so why re invent the wheel?

---

### Post by Znupi on 2007-06-04
So basically, it creates a site engine for you? I have my own, thank you.

[SIZE=1]Sorry if I'm being stubborn, it's just that I'm really against anything that 'generates code', so you don't have to. I'm a DIY believer.[/SIZE]

---

### Post by hagen00 on 2007-06-04
If that's what a site engine is? Ok, never heard of that. 

i just thought, no point in re creating the wheel, if someone else can do it so much better than I will ever be able to. But obviously, if your method works for you, then great. 

The post was meant for people who moan about the Spaghetti code that PHP coders usually churn out. 

I'm also against somethign that generates code in principle (but my mates tell me to get over it). The point is that Qcodo generates beautiful code - that I can live with!

---

### Post by LaRoza on 2007-06-04
> I would assure you that much more would prefer LAMP with PHP over Python preinstalled on any Linux.

Many Linux apps are written in Python, including the Ubuntu installer, I believe.

---

### Post by pmasiar on 2007-06-04
> **barmazal said:**
> you said Python and Ruby are dynamic MVC languages! 

Can you quote me saying that?
As both you and I know, Python and Ruby are dynamically typed OOP languages, using MVC framework for Web apps. Especially Python is more widely used beyond web apps (in areas where MVC is not needed). This usage might be below your radar of course, but it exists and is strong.

>Turbo Gears and Django propaganda there are no real time proof to their superiority, no large amount of huge sites powered by those

See ie. [http://www.djangoproject.com/](http://www.djangoproject.com/), "Sites that use Django". Is Washington Post big enough?

Of course PHP was in web apps first and is strong and will be for some time as I said couple times so what exactly are we arguing about?

>not sure what Google and NASA do using Python but it's written on Python's website.

NASA usage is probably classified :-) 
Google uses Python to manage deployment of servers and it's file system, and internal productivity apps. Stuff like installing new search app to 1000 servers to try it. [PyCon 2005 presentation](http://www.sauria.com/~twl/conferences/pycon2005/20050325/Python%20at%20Google.html) by [Greg Stein](http://en.wikipedia.org/wiki/Greg_Stein) 

rest is just opinion blabber without any links or facts -- better to be ignored that worked up to flamewar in a teapot.

---

### Post by hagen00 on 2007-06-04
pmasiar - this thread was precisely meant for you. Python and ROR users tend to be very strong evangelists...and often they have a good reason for being so. However, I believe with Qcodo, there is a framework that very strongly competes with Django, Turbogears and the rest. This thread was also meant for those who are disillusioned with PHP - before moving over to an entirely different coding paradigm like python, try Qcodo first. 

Funny how everyone is throwing NASA around as a case study - There's also a NASA Qcodo implementation...

---

### Post by pmasiar on 2007-06-04
> **hagen00 said:**
> pmasiar - this thread was precisely meant for you. 

Thought so :-) OK let's discuss our positions based on facts, without flamewars.

> Python and ROR users tend to be very strong evangelists...and often they have a good reason for being so.

Absolutely. But some quotes of PHP proponents like barmazal are also far from cold facts - are they just trolls to start flamewars? I always feel urge to response (with facts I hope) when someone mentions "Python hype" or "propaganda". Especially as we found out that Python is *older* than PHP - it is just latecomer to web apps niche.

> **barmazal said:**
> If you ask me Python users are just those who never achieved noting in PHP or ASP or Java... 
hopefully you will find not guy like me who uses .NET but real PHP user who can smash Python once for all.

"never achieved noting" ... "smash Python once for all". Very ballanced comment based on rock-solid facts :-)

I agree I never achieved anything in PHP or ASP, and let me tell you why. I hate having code mixed with HTML, even as I love freedom given by dynamic typing, so I looked at PHP and run away screaming :-) I have experience maintaining big codebase - result of couple years of development. Biggest codebase was 40MB (about 1M LOC) in PROGRESS 4GL, and it was painfull. So I developed deep appreciation for clean maintainable code, which might be not first priority of many beginners - it is acquired taste I admit :-)

As I checked [PHP](http://en.wikipedia.org/wiki/Php#Criticism) *still* lacks namespaces (5,312 functions in the global namespace seems quite a lot), but OOP was added in 2004, which is good. So there is *is* some progress in PHP, but too late for me.

> However, I believe with Qcodo, there is a framework that very strongly competes with Django, Turbogears and the rest. This thread was also meant for those who are disillusioned with PHP - before moving over to an entirely different coding paradigm like python, try Qcodo first.

I agree that for experienced PHP hacker it might make sense. But IMHO for a beginner, simple Python with templating (or even embedded string interpolation) is much simpler and cleaner starting point. PHP is too much Perl-like to my taste.

I understand that Python and PHP are competitors in web app niche, and rate of conversion of beginners is important to maintain the momentum of either language. I see PHP going strong for couple (many) years, but 15-20 years from now we need cleaner languages so more people can if not write code, at least be able to read it and comment on it. And this is IMHO strongest argument for Python -- or whatever "clean and readable" language will replace it 15-20 years from now, still in timeframe of career of most of this discussion participants.

There is a reason why Python (and not ie PHP) was selected as main development language for OLPC. Think about millions of Python users, and thousands of Python hackers coming from that, 5-10 years from now.

Till then, PHP is decent language with strong current web app presence. Without doubt, new features will be added and new initiatives started for it, and will continue to have it's appeal for experienced PHP hacker for years to come.

Just *IMHO* PHP is not the best choice for a total beginner, and it's niche will be shrinking in the timeframe of 15-20 years.

---

