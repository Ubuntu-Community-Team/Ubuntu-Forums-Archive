---
title: "Web Development: Messaging on a website"
date: 2008-06-19
forum: Programming Talk
---

### Post by TorchlightJay on 2008-06-19
Hello,
   I want to build a kind of social site where people log in and can send personal messages to other users. It is a very very basic type of messaging. How would i accomplish this? Again, all I want is for users to be able to send messages (almost like an email) to other members. Let me know what you think.

---

### Post by pmasiar on 2008-06-20
what are your current web design and programming skills? HTML, CSS, LAMP? Python/Perl/PHP/Ruby?

---

### Post by -grubby on 2008-06-20
First off, you'll definately need supple knowledge of HTML, CSS, and PHP. Mysql could and most likely *will* be involved

---

### Post by evymetal on 2008-06-20
> **nathangrubb said:**
> First off, you'll definately need supple knowledge of HTML, CSS, and PHP. Mysql could and most likely *will* be involved

Just to be pedantic, I don't "know" PHP (the most I've ever done is customising the wordpress engine for a project), but I've done this kind of thing hundreds of times ... You'll need to know some kind of server side scripting though (PHP / Python / Perl / ASP /mono etc.) I'd use MySql as I have an abnormal love of writing SQL, but you could use a berkley style db if you don't expect that many users (i.e. total messages is going to remain under 10,000) - there  are really simple to use libraries for Python and Perl that makes the database act like a list (don't know the others).


Basic Idea is :

 * sender creates a message in the browser that gets sent to a server side script that creates a "record" (/"row" depending on what you call them) that represents the message)

 * when a user logs in the server side script searches the database for messages to that user, and displays the message.


You may also be able to find an open source project that may have this, but it's the kind of thing that most programmers would hack together themselves IMO.

---

### Post by TorchlightJay on 2008-06-21
I have a working knowledge of HTML and CSS. I do mainly LAMP(PHP) programming. I know a little javascript & DHTML but I can always learn more if needed.

---

### Post by BloGTK on 2008-06-22
> **TorchlightJay said:**
> I have a working knowledge of HTML and CSS. I do mainly LAMP(PHP) programming. I know a little javascript & DHTML but I can always learn more if needed.

This might be a good use for Ruby on Rails. There's a bit of a learning curve in learning the Rails way of doing things, but once you've done a test app or two it's very easy to start coding.

There are plenty of web app stacks out there that take some of the annoying aspects of working with a database. Django for Python, Cake for PHP, etc. All of them have their own way of building an app, but they're usually easy to work with.

---

### Post by descendency on 2008-06-22
You can achieve this with some basic php/mysql coding. Where you will end up having a lot of "fun" (where most of the headache is involved) will be securing the data.

My first question would be do you have a template for the site or do you have any experience making login systems?

That might be your first area to research. (HTML/PHP for creating a basic look for the site and PHP/MySQL for the login stuff)

---

### Post by Wybiral on 2008-06-22
> **nathangrubb said:**
> First off, you'll definately need supple knowledge of HTML, CSS, and PHP. Mysql could and most likely *will* be involved

You don't _need_ PHP at all. In fact, I would advocate AGAINST that. There are dozens of options (many better than PHP) for the server code (Ruby, Perl, Java, I personally use [Python]("http://www.python.org")), as with databases, almost definitely SQL, but not necessarily MySQL (lots people use PostgreSQL, for instance, I'm using GQL at the moment).

Don't box yourself into that PHP/MySQL box, there are tons of great options. I would start with a framework also before starting your site from scratch (you'll waste far less time).

---

### Post by TorchlightJay on 2008-06-23
Hello,
  So many options. I am willing to do it but I am on a time crunch so learning too many new things may slow me down. Anyone know of a good and thorough crash course of Ruby on Rails? 

I do not know how to make login systems but I can learn very quickly. Any ideas or sample scripts. Currently we already have a site (it needs a little tweaking but the HTML and CSS is already there). We just need to integrate some kind of server side scripting to enable messaging. 

This is what we want in a nutshell:

1) People whom want to join our site fill in a sign up sheet and pay their dues (via PayPal or Google Checkout unless you know of something better). 
2) Once that is done two things happen. You get an email welcoming you to our site and we populate your data onto a portion of the site.  (this site is going to be mainly for businesses to network with each other). 
3) Once you are a member, you have the ability to message other members as a way to mingle on the digital realm. 

That's all we have so far. Any ideas.

---

### Post by pmasiar on 2008-06-23
google can suggest dozens of "free chat server" apps. BTW why you expect someone will pay you for something what they can have better for free elsewhere?

---

### Post by TorchlightJay on 2008-06-23
our niche

---

### Post by Wybiral on 2008-06-23
> **TorchlightJay said:**
> our niche

It's only your niche until I decide to do the same thing for free :)

---

### Post by maibus2 on 2008-06-24
I second the previous suggestion for using Ruby on Rails, I have built a social networking app before using Rails and it was a breeze. Its even easier now with all the great free plugins available. You could do this in less than an hour, not counting some learning time.

User authentication / payment can be handled using the RESTFUL Authentication and Active Merchant plugins.

The database design is extremely simple with a one to many relationship between users and message, each message should have two user id's, one for the sender and one for the recipient. In addition I would suggest deleted and marked as read fields in the messages table.

For the inbox simply loop through and display all messages containing the currently logged in users id in the recipient's field (a current user method is provided using the RESTFUL Authentication plugin).

Good Luck

---

### Post by TorchlightJay on 2008-06-24
sounds easy enough. So what IS ruby on rails. I hear that term thrown around and I know that Ruby is a programming language much like how php, perl, python, java, etc are languages. What is ruby on rails? Is that a variation on ruby or something different altogether? 

On another side, let me make sure I understand you. Once a person logs in, I just program an inbox. This basically means I program a whole separate part of the website that is only accessible if you are a member and you log in. Part of this section would have a piece called "inbox". Each member has a member ID and a recipient ID and a sender ID (on a basic level). When you send a message, you are essentially sending a message to the recipient ID (which is a person's name to us people). I get the message and see whom the sender is. i have an option to delete the email and mark them. I have an idea on how to allow people to delete messages, as far as marking them, how would I do that?

---

### Post by Wybiral on 2008-06-24
> **TorchlightJay said:**
> sounds easy enough. So what IS ruby on rails. I hear that term thrown around and I know that Ruby is a programming language much like how php, perl, python, java, etc are languages. What is ruby on rails? Is that a variation on ruby or something different altogether?

Ruby on Rails is a web framework for ruby. Similar to Django or Turbogears for Python.

---

### Post by TorchlightJay on 2008-06-24
Ready for a dumb question, what is a framework?

---

### Post by henchman on 2008-06-25
hey, no question is dumb, isn't it :) Those who don't ask questions more or less stay dumb...

a framework is a software library which, by abstracting lower layers of the system, simplifies development of applications.

an example is for example with sessions, where you only have to say like (fictional)
```

Session s = new Session();
s.setVariable( "username", $user );
s.setVariable( "email", $mail );

```

and the code in the framework now checks if user has cookies enabled or not and then saves the information in a way you don't have to care about, because it just works :)

On the other hand, if you are using a framework, then you loose some functionality, if you cannot expand for example the session class. One (dumb, again fictional) example would be if you would like to store an object or an image or whatever and the session class is not able to handle such data. Then you would have to write it yourself again (or abandon the idea of doing so).

any other opinions? :popcorn:

---

### Post by Wybiral on 2008-06-25
Frameworks usually handle the dirty work and the repeating patterns in web development... Things that, from scratch, you would end up typing over and over for each application you develop. Usually things like sessions, users/groups/permissions, form construction/validation, search pagination, page template systems, and... You know... Things that you shouldn't have to write yourself. Most frameworks support some sort of plugin system to make them more extensible and reusable.

---

### Post by TorchlightJay on 2008-07-01
Sounds like a plan. 

Hey, what do you think about a programming language? I keep hearing about Ruby (Ruby On Rails Framework) and Python (using the Django or the Turbogears framework). What do you all think?

---

### Post by pmasiar on 2008-07-01
There are couple of threads about comparing those languages in web development in last week - just check them.

---

### Post by TorchlightJay on 2008-07-09
Hey, i just thought of this. On the backend of the site, would I need like LDAP or something to log all the users to my site or is that just unneccessary. Maybe I should examine something like WordpRess and see how they log users? I don't know.

---

### Post by mssever on 2008-07-09
> **TorchlightJay said:**
> Sounds like a plan. 

Hey, what do you think about a programming language? I keep hearing about Ruby (Ruby On Rails Framework) and Python (using the Django or the Turbogears framework). What do you all think?I love Ruby as a language, but the Rails documentation is poor. I think that Python/Django is probably better suited for beginners.

> **TorchlightJay said:**
> Hey, i just thought of this. On the backend of the site, would I need like LDAP or something to log all the users to my site or is that just unneccessary. Maybe I should examine something like WordpRess and see how they log users? I don't know.
LDAP is great for managing authentication for a large corporation with many machines and servers and such. For a web service, it's serious overkill. Your framework of choice should provide user-management facilities. If not, it isn't too difficult to write them yourself.

---

### Post by pmasiar on 2008-07-09
[http://en.wikipedia.org/wiki/Google_App_Engine](http://en.wikipedia.org/wiki/Google_App_Engine) provides you with user authentication (via google user ID) and all other features (AFAICT), including the language (Python, of course), web framework, and free hosting. just add code :-)

---

### Post by TorchlightJay on 2008-07-09
> **pmasiar said:**
> [http://en.wikipedia.org/wiki/Google_App_Engine](http://en.wikipedia.org/wiki/Google_App_Engine) provides you with user authentication (via google user ID) and all other features (AFAICT), including the language (Python, of course), web framework, and free hosting. just add code :-)

I've heard about that one. Believe it or not, I joined up with that one. That sounds like a good idea, my only concern is intellectual property and also how would I integrate it into a website, wouldn't it always be a part of google? Keep in mind, I am new to the Google App Engine, I barely know how to use it lol.

---

### Post by pmasiar on 2008-07-09
> **TorchlightJay said:**
> my only concern is intellectual property

1) "intellectual property" is misleading term, used by lawyers to confuse other lawyers. It mixes three separate branches of law, with different and contradictory rules: patent, copyright, trademark. Saying "what about IP" tells you less than saying nothing.

2) you keep your "IP" and Google keeps theirs.

> how would I integrate it into a website, 

What other website you need?

> wouldn't it always be a part of google? 

You can buy own domain if you want to.

>  I am new to the Google App Engine, I barely know how to use it

So don't worry about "IP" and start hacking. You have no "IP" to protect.

Wybiral is GAE expert, has popular app for it. But you probably need to start another thread (with better title: use 'GAE' and 'Python') to get his attention :-)

---

### Post by TorchlightJay on 2008-07-09
True, well I am trying to build a sort of social networking site with a buddy. The domain is purchased and the site itself exists already in terms of HTML. We want to make it more of a social networking site. My concern is if we build the site on Google App Engine, will we still be able to integrate our domain and current website?

---

### Post by mssever on 2008-07-09
> **TorchlightJay said:**
> My concern is if we build the site on Google App Engine, will we still be able to integrate our domain and current website?
Yes, but it sounds like you have things a bit backward. Your backend framework will dictate your HTML code. At the least, it will dictate your template system to some extent. Furthermore, the HTML needs for a webapp are different from the needs of a static, HTML-only site, it's very possible that you'll end up throwing away a good portion of your HTML.

On the other hand, a strong, well tested (read: usability tests) front end will be critical to your success. And the overall UI design is independent of your backend.

---

### Post by Mickeysofine1972 on 2008-07-09
I recommend Code Igniter which is an existing php frame work that allows you to define web content in a very straightforward way and can make a large part of your web code re-usable.

I have used this in quite a few of my latest work projects and has made this sort of thing an absolute dream.

Its Open Source and you dont need to worry about IP. Its easily integrated with AJAX too.

Mike

---

### Post by TorchlightJay on 2008-07-09
Ya, i am kind of just picking up on this project lol. Someone else built the HTML site with no application setup. Makes no sense to throw away perfectly good code so i want to find a way to still use the code we have. I will look at that code igniter since I have familiarity with PHP. 

Will it allow me to build a site/app that allows me to add and manage users, enable messaging, so on and so forth?

---

### Post by mssever on 2008-07-09
> **TorchlightJay said:**
> Will it allow me to build a site/app that allows me to add and manage users, enable messaging, so on and so forth?
I don't remember if it has user management or not. Code Igniter is likewise my choice for PHP frameworks. The biggest advantage it has is that it's well-documented. However, it isn't as complete as, say, Rails. Plus, coding PHP in OO style is annoying.

---

