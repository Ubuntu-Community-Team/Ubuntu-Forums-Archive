---
title: "Free webhosting by Google: App Engine (with Python and Django)"
date: 2008-04-08
forum: Programming Talk
---

### Post by pmasiar on 2008-04-08
**Python just become THE web app development language**. This is big: [What Is Google App Engine](http://code.google.com/appengine/docs/whatisgoogleappengine.html)
- no servers to maintain: You just upload your application, and it's ready to serve your users.
- free domain name on the appspot.com domain
- free account can use up to 500MB of persistent storage and enough CPU and bandwidth for about 5 million page views a month
- automatic scaling and load balancing
- APIs for authenticating users and sending email using Google Accounts
- a **fully featured local development environment** that simulates Google App Engine on your computer

In Python and Django. Amazing!

---

### Post by Steveway on 2008-04-08
Awesome, thank you very much for this information.
So it's like most free-webhoster only with python-support through Django? Yay for that!

---

### Post by pmasiar on 2008-04-08
Yes, but scalability and uptime guaranteed by Google! This changes game in web app development. Start for free, when you have more than 5M page wiews/month, pay fee to upgrade to pro account, done.

Game is over, Python won.

---

### Post by lnostdal on 2008-04-08
[quote=pmasiar]Game is over, Python won.[/quote]

oh, i didn't know there was a competition .. lisp missed the train again, eh? =)

(tbh. i don't care .. i'm actually glad; there will be more for me .. it's "my precious" ..  i'll "beat the averages", and all you boring "normal" people .. bwaahaha .. but seriously; i will .. it's happening -- right -- now)

edit:
..as a side note i'm running my lisps on VPS boxes .. root access .. cheap .. so, well .. you can have your crummy google accounts =)

PS: don't throw a fit now; i'm just teasin' you

---

### Post by Steveway on 2008-04-08
> **pmasiar said:**
> Yes, but scalability and uptime guaranteed by Google! This changes game in web app development. Start for free, when you have more than 5M page wiews/month, pay fee to upgrade to pro account, done.

Game is over, Python won.

Yup, the aspect that it is made by Google is a big bonus, I was very pleased when I saw that and just had to type in my password to get signed up to the waiting-list.
Can't wait to get approved, but I'll use the time to deepen my Python-knowledge.

---

### Post by pmasiar on 2008-04-08
> **lnostdal said:**
> oh, i didn't know there was a competition ...
PS: don't throw a fit now; i'm just teasin' you

I know. I just read article By Paul Graham about McCarthy: in last 20 years, big part of new language development was to add features which Lisp has in 1958. But since 1958, problem of List was how to serve the power so you don't have to be demi-god to use it. 

This announcement basically solves the argument  "but PHP is preinstalled on all cheap hosts" (and Google goes full-scale into business of cheap webhosting, BTW. Not sure what will be the consequances, but there will be). 

Also, Python+Django officially won over Ruby On Rails. Huge boost for Python. Earthquake completely changing lay of land in web app development. Non-MVC development in PHP will be more expensive than MVC in Django. Django is new PHP.

Time to look seriously at Django. The only downside is that Turbogears became niche player... :-(

---

### Post by jdonnell on 2008-04-08
"Also, Python+Django officially won over Ruby On Rails"

is this hyperbole?

---

### Post by Wybiral on 2008-04-08
Neat. But I like TG so much now, lol... I guess I'll have to get to know DJango a bit now.

---

### Post by pmasiar on 2008-04-08
> **jdonnell said:**
> "Also, Python+Django officially won over Ruby On Rails"

is this hyperbole?

No, it is just over-excitement :-) Google promises to support other languages later.

But still. Big win for Python, there is hardly any reason to use PHP.

---

### Post by LaRoza on 2008-04-08
> **pmasiar said:**
> 
But still. Big win for Python, there is hardly any reason to use PHP.

Good news, I've been wondering why nothing like this exists.

There is a big reason to use PHP, existing and working code :-)

---

### Post by Wybiral on 2008-04-08
> **LaRoza said:**
> There is a big reason to use PHP, existing and working code :-)

Python has tons of existing and working code too!

The difference is that Python is actually manageable :P

---

### Post by LaRoza on 2008-04-08
> **Wybiral said:**
> Python has tons of existing and working code too!

The difference is that Python is actually manageable :P

Rewrite phpBB in Python then :-)

---

### Post by Wybiral on 2008-04-08
> **LaRoza said:**
> Rewrite phpBB in Python then :-)

Using a web framework like TG or DJango, that would be painless actually. I suck at the interface side, the css and such, but the server-side code would take no time at all to write if you use a good enough framework.

---

### Post by LaRoza on 2008-04-08
> **Wybiral said:**
> Using a web framework like TG or DJango, that would be painless actually. I suck at the interface side, the css and such, but the server-side code would take no time at all to write if you use a good enough framework.

My point was that existing applications and sites would be very hard to convert.

Take this forum for instance. We are going to have an upgrade to the new vBulletin and there is so much that has to be done. The testing site is very messy and a lot is broken. 

This is a big change, and it is only a jump .2 version numbers I think. Imaging trying to convert this site to another framework.

Now that I mentioned it, when the upgrade comes, things may be a little different. Most of it is better, but as with all changes, there may be some negative aspects, at least for a little while. Try not to panic when it happens :-)

---

### Post by jdonnell on 2008-04-08
> **LaRoza said:**
> 

There is a big reason to use PHP, existing and working code :-)

Exactly! How do you add a wordpress blog to a django app?

---

### Post by jdonnell on 2008-04-08
> **Wybiral said:**
> Using a web framework like TG or DJango, that would be painless actually. .

This is how programmers get in trouble; grossly underestimating the effort required for something. 

Btw, how does django operate? Does it run separate processes like rails? How do you add more django apps into an existing django app under a url like mysite.com/blog/
?

---

### Post by LaRoza on 2008-04-08
> **jdonnell said:**
> This is how programmers get in trouble; grossly underestimating the effort required for something. 

Btw, how does django operate? Does it run separate processes like rails? How do you add more django apps into an existing django app under a url like mysite.com/blog/
?

I think that Wybiral was mostly referring to using it, not converting to.

---

### Post by Wybiral on 2008-04-08
Well that's porting a pre-existing project. It's different when you're starting an application. It seems to me like your PHP is already getting messy :)

---

### Post by jdonnell on 2008-04-08
> **Wybiral said:**
> n. It seems to me like your PHP is already getting messy :)

what are you referring to?

---

### Post by jdonnell on 2008-04-08
> **LaRoza said:**
> I think that Wybiral was mostly referring to using it, not converting to.

laroza said: Rewrite phpBB in Python then
wyrbiral said: Using a web framework like TG or DJango, that would be painless actually.

it would not be painless.

---

### Post by Wybiral on 2008-04-08
I didn't know LaRoza meant "rewrite this exact forum in Python".

But if it's just writing a forum, in general, that resembles / has the kinds of features this forum has... To begin with, there are pre-written forums for frameworks like DJango an TurboGears that you could use "off the bat" and extend as needed, but even using those frameworks alone it wouldn't even be that difficult to setup the database and get an interface running.

I wasn't implying that you could just go over all the PHP code and do a literal translation to Python (mostly because you would have to be able to read the PHP code that was written, which is hard enough :P )

---

### Post by jdonnell on 2008-04-08
> **Wybiral said:**
> 
I wasn't implying that you could just go over all the PHP code and do a literal translation to Python (mostly because you would have to be able to read the PHP code that was written, which is hard enough :P )

and I didn't think that you were. Software that has existed for a while and been used heavily will have a lot of features due to that experience. I will bet money that the preexisting forums written for django are missing these features and they are vital for many sites. I'll even wager that none of the pre-existing django boards would be a satisfactory replacement for this board we are using right now.

Yes, it's easy to write code that allows users to sign-up, make posts, and comment on those posts. A real forum system is far more than this overly simplistic view. I'm refuting the assertion that they are even remotely equivalent.

I'm still curious to know how django runs. Is it threaded? How does it handle two requests that come in simultaneously?

---

### Post by Wybiral on 2008-04-08
> **jdonnell said:**
> I'm still curious to know how django runs. Is it threaded? How does it handle two requests that come in simultaneously?

No, it blows up on multiple requests :)

Are we done hijacking this thread yet? I didn't mean to upset all the PHP fans out there :p

---

### Post by LaRoza on 2008-04-08
> **Wybiral said:**
> 
Are we done hijacking this thread yet? I didn't mean to upset all the PHP fans out there :p

I didn't mean to start it. Just a small comment (I thought) that PHP would exist because of its existing code base. 

Back on topic:

So, did you here that google is offering free webhosting with Python?

---

### Post by Wybiral on 2008-04-08
> **LaRoza said:**
> So, did you here that google is offering free webhosting with Python?

Yeah :), I just watched the [campfire videos]("http://www.youtube.com/watch?v=3Ztr-HhWX1c") on it. It looks good!

---

### Post by jdonnell on 2008-04-08
i'm not a php fan at all, but it has it's strong points. I guess it's easier for you to ignore my legitimate questions. 

Here is something the OP said.
> Game is over, Python won.

Is it thread hijacking if I point out why I don't believe this is true, along with why I disagree with some of your statements? I'm sorry, I thought this was a discussion board.

---

### Post by lnostdal on 2008-04-08
> **jdonnell said:**
> i'm not a php fan at all, but it has it's strong points. I guess it's easier for you to ignore my legitimate questions. 

Here is something the OP said.


Is it thread hijacking if I point out why I don't believe this is true, along with why I disagree with some of your statements? I'm sorry, I thought this was a discussion board.

php ain't even "in the game"

..think about it.. it's python vs. ruby..

..and it's for people that are fed up with php already .. so php ain't even participating here

---

### Post by LaRoza on 2008-04-08
> **jdonnell said:**
> i'm not a php fan at all, but it has it's strong points. I guess it's easier for you to ignore my legitimate questions. 

Is it thread hijacking if I point out why I don't believe this is true, along with why I disagree with some of your statements? I'm sorry, I thought this was a discussion board.

It was just an excited comment, I think. It wasn't meant to be a dogmatic statement.

---

### Post by pmasiar on 2008-04-08
> **jdonnell said:**
> and I didn't think that you were. Software that has existed for a while and been used heavily will have a lot of features due to that experience. I will bet money that the preexisting forums written for django are missing these features and they are vital for many sites. I'll even wager that none of the pre-existing django boards would be a satisfactory replacement for this board we are using right now.

Of course. App Engine uses own non-SQL persistence, Django people are working on adapting their ORM to it (so change will be transparent - beauty of using ORMs :-) ). Nobody is talking about running existing apps. Game is about future apps.

> I'm still curious to know how django runs. Is it threaded? How does it handle two requests that come in simultaneously?

**Whole point is that you don't care**. Google handles load balancing, server allocation, etc. You just write your app, upload it to **google cluster** and let it rip. It completely changes the game - you don't administer servers anymore, they do. For free. :-)

---

### Post by runningwithscissors on 2008-04-08
> **jdonnell said:**
> I'm still curious to know how django runs. Is it threaded? How does it handle two requests that come in simultaneously?
It can run either through FastCGI (using persistent processes) or through mod_python (where the interpreter is controlled by the webserver),
I think rails only does FastCGI.

Also, this Google thing has only just taken off. PHP is the super-heavyweight of the web development world (think of the most popular sites, nearly half are powered by PHP, I think). It'll take a lot of time and a lot of good reasons to displace it.

---

### Post by jdonnell on 2008-04-08
> **runningwithscissors said:**
> It can run either through FastCGI (using persistent processes) or through mod_python (where the interpreter is controlled by the webserver),
I think rails only does FastCGI.


Most rails sites these days don't use fastcgi. They use multiple mongrel processes behind some kind of balancer (apache, nginx, etc). It seems that django operates in a similar way (persistent processes). This is fine for a lot of situations, but not all. This is the point I've been trying to make. 

I've done a lot of contracting and a many companies want their main site, a blog at /blog/, a message board (SEO reasons), and maybe some other pre-made application. I loathe php as a language, but this is php's strong point and rails (i'm guessing django too) fall on their faces for this. I love rails, but I can't recommend it in these situations. 

To be clear, if you have your main app, a blog, and a message board using persistent processes for each then you need to run at absolute minimum 2 processes for each app. That is a lot of ram!

I don't believe this google setup solves this issue for various reasons. I know this situation is not indicative of web development as a whole, but I believe that php will continue to dominate for this reason. Most small to medium companies are not creating their sites from scratch with professional programmers and they don't mind spending $20/month to run their site.

As I said before, I loathe php as a language. I would love for ruby, python, or a lisp family language to take significant market share in the web sphere, but I don't see it happening anytime soon and not as a result of this google setup.

I don't think this google setup is bringing anything new to the table except for making it super easy or the python community. You could already do  the same thing on amazon's setup and there are a lot of great rails hosting companies that manage the servers and provide serious setups for real companies that are willing to pay. Engine yard is one example.

---

### Post by runningwithscissors on 2008-04-08
> **jdonnell said:**
> Most small to medium companies are not creating their sites from scratch with professional programmers and they don't mind spending $20/month to run their site.

As I said before, I loathe php as a language. I would love for ruby, python, or a lisp family language to take significant market share in the web sphere, but I don't see it happening anytime soon and not as a result of this google setup.They should probably use eRuby. Ruby off the rails and with all the hackish PHP code-mixed-with-markup goodness. Only problem is that it is a lot slower than PHP. :)

---

### Post by Wybiral on 2008-04-08
FWIW, you don't have to use DJango with Google App Engine. There is a google API that makes the CGI simple (a lot of this stuff was developed by Guido himself too), and it sounds like there will probably be other frameworks supported in the future. Not to mention other languages, but who wouldn't want to use Python? :p

---

### Post by skeeterbug on 2008-04-08
> **jdonnell said:**
> This is how programmers get in trouble; grossly underestimating the effort required for something. 

Btw, how does django operate? Does it run separate processes like rails? How do you add more django apps into an existing django app under a url like mysite.com/blog/
?

As someone mentioned, you can go FastCGI or mod_python. Doesn't really matter in this case, as Google is taking care of it.

URLs are configured using regular expressions. If you have a project with multiple apps, each app can control it's own URL scheme. It gives you more flexibility, at the cost of maintainability. Refactoring your URL scheme or controller names/methods could get pretty messy.

Neither Django or RoR have a perfect system for it. I guess it depends on what you are more comfortable with. Personally I like Django's. I almost never change my URL scheme. Using RoR's routes can be nice in views (using link_to).

---

### Post by jdonnell on 2008-04-08
i'm hoping they add javascript (server side) support to appEngine next. After all, it's a google sanctioned language :)

---

### Post by pmasiar on 2008-04-08
JS is just another tool - it is orthogonal, it runs in client, whatever your page templates send to browser, right? Django does dave JS toolkit, IIRC dojo. You can use any you like. You don't even have to use Django - do plain CGI yourself if you want.

---

### Post by jdonnell on 2008-04-09
you misunderstood. I'm talking about using javascript on the server side. Something like [rhino]("http://www.mozilla.org/rhino/") and there is also [rhino on rails]("http://steve-yegge.blogspot.com/2007/06/rhino-on-rails.html") floating around google.

---

### Post by pmasiar on 2008-04-09
> **jdonnell said:**
> you misunderstood. I'm talking about using javascript on the server side. 

Ohhh OK. Why would someone want JS when Python is available? Not me :-)

**edit: Python on the server, JS/AJAX on the client of course**

---

### Post by jdonnell on 2008-04-09
python is not the "be all and end all" of languages.

---

### Post by LaRoza on 2008-04-09
> **pmasiar said:**
> Ohhh OK. Why would someone want JS when Python is available? Not me :-)

Not sure, ECMAScript is great for client side scripting as that is what is was designed to do.

> **jdonnell said:**
> python is not the "be all and end all" of languages.

Yes, but in this area, I would see no reason (besides having existing code) to use JavaScript on the server over Python.

However, in the free world, we have choices.

---

### Post by tseliot on 2008-04-09
> **jdonnell said:**
> python is not the "be all and end all" of languages.
Of course not. Python is suitable for a number of tasks but not for any task.

---

### Post by pmasiar on 2008-04-09
As I am skimming through blog posts of smart people, I found interesting opinions:
- [why it is free](http://www.scripting.com/stories/2008/03/30/whyWouldGoogleWebServicesC.html) - Google saves on acquisition cost (when buing new companies) and training: companies and students build app using technology close to Google's own. Smart students can become millionaires before finishing college, with no cash investment, only time!
- [GAE is new BASIC](http://www.scripting.com/stories/2008/04/08/earlyNotesOnGoogleapps.html) : new market will emerge like with PCs, "normal" people can buy application, customize it a little, and deploy it for small company use into Google cloud. **Anyone **can deploy web apps now, like anyone can install Windows programs. **New application platform was defined, and this time it is not Windows.** This is even bigger than I thought previously!
- new tools specifically for GAE will emerge, like this [login decorator](http://www.djangosnippets.org/snippets/691/) for Django/GAE
- examples of apps for GAE: [blog](http://bret.appspot.com/entry/experimenting-google-app-engine)

---

### Post by jdonnell on 2008-04-09
> **LaRoza said:**
> 
Yes, but in this area, I would see no reason (besides having existing code) to use JavaScript on the server over Python.

One possible reason is to use the same code on both the client and the server. I've had to duplicate functionality in js and again in ruby for heavy ajax sites. Avoiding a duplication of effort is a big gain!

---

### Post by Wybiral on 2008-04-09
> **pmasiar said:**
>  ... 

Have you played with the SDK yet? It sets up a simple server for you and lets you use all the stuff you can use when you deploy (the google API, including the ability to use google accounts as your users!), so you can develop and test everything on your computer, then run an upload script that handles all the migrating for you!

I'm on the list to try it out, but I bet thousands of other developers are too :( Hopefully they will see the amount of demand for this and release the real thing soon. I can't wait!

---

### Post by skeeterbug on 2008-04-09
> **jdonnell said:**
> python is not the "be all and end all" of languages.

Who said it was?

---

### Post by jdonnell on 2008-04-09
> **skeeterbug said:**
> Who said it was?

Are we reading the same thread?

pmasiar:
> Game is over, Python won.
> Why would someone want JS when Python is available?

pmasiar regularly treats python as the best option over any other dynamic language. He is incredulous to the idea of using a language other than python.

---

### Post by lnostdal on 2008-04-09
> **jdonnell said:**
> pmasiar regularly treats python as the best option over any other dynamic language. He is incredulous to the idea of using a language other than python.

well, he's wrong .. so what?

or .. well, he's right .. so what?

there needs to be more than one person to start or maintain an argument

"yeah, i think i understand .. i got to (or i will) stick with c and pointers and stuff for now though .. will look into this later though, thanks!" 

..that's how you communicate (in particular when you want to end a discussion).. try it; you'll see that it works whether he's wrong or right, or you're wrong or right

edit: 
..just, never mind this part..

---

### Post by jdonnell on 2008-04-09
yeah, I need to remember to do that more often. Thanks for the friendly reminder.

---

### Post by pmasiar on 2008-04-09
1) **"Python won" in area of web application, not for all apps**. There are desktop apps, system utilities, drivers, kernal - I never suggested that Python is best language for all that. This thread is clearly about web application, and Google announcement is huge boost for popularity of  Python, no way to deny it. 

And later, I retracted, GAE will be available for other languages too sometime later.

But in terms of LAMP stack, P stands strongly for Python now.

2) JS on the client(AJAX) & Python on the server is fine. I never said "APAX" or anything. Don't try to misquote me.

Bottom line is, this IS huge boost for Python. This does take away wind from Ruby's sail, and RoR hype is mostly over. Perl becomes legacy language. And until PHP does not have GAE datastore bindings, PHP is legacy, too. It will be interesting what other languages will be implemented, and when. Google uses internally only C++, Java and Python. 

Python won in web application niche (where it was B level actor 3-4 years ago), and it is huge overturn. Now we can see consequances of Google hiring Guido in 2004. :-)

---

### Post by jdonnell on 2008-04-10
Here are a couple of good reads on GAE

[http://blog.ianbicking.org/2008/04/09/app-engine-and-open-source/]("http://blog.ianbicking.org/2008/04/09/app-engine-and-open-source/")

[http://blog.ianbicking.org/2008/04/09/app-engine-commodity-vs-proprietary/]("http://blog.ianbicking.org/2008/04/09/app-engine-commodity-vs-proprietary/")

---

### Post by mssever on 2008-04-10
> **pmasiar said:**
> Bottom line is, this IS huge boost for Python. This does take away wind from Ruby's sail, and RoR hype is mostly over.
This raises some interesting questions. As a language, I like Ruby MUCH better than Python. Yet, Ruby seems to lag a lot, and I've never managed to successfully use Rails. Good documentation for Rails is practically non-existent, and there's a lot of source to read before trying to understand it that way, especially since I don't fully grok MVC.

The question is, are the various Python frameworks any better documented? According to the [GAE docs]("http://code.google.com/appengine/docs/gettingstarted/usingwebapp.html"):[quote=Using the webapp Framework]Google App Engine supports any framework written in pure Python that speaks CGI (and any [WSGI]("http://www.google.com/url?sa=D&q=http://www.python.org/dev/peps/pep-0333/")-compliant framework using a CGI adaptor), including [Django]("http://www.google.com/url?sa=D&q=http://www.djangoproject.com/"), [CherryPy]("http://www.google.com/url?sa=D&q=http://www.cherrypy.org/"), [Pylons]("http://www.google.com/url?sa=D&q=http://pylonshq.com/"), and [web.py]("http://www.google.com/url?sa=D&q=http://webpy.org/").[/quote]So there appears to ne quite a bit of choice. But how are these choices for someone with no prior MVC experience?

I'm on the waiting list to get an account. Hopefully I'll get one soon.

---

### Post by jdonnell on 2008-04-10
> **mssever said:**
>  Good documentation for Rails is practically non-existent, 

I've been doing rails professionally for about 3 years. The free online documentation isn't good for learning. Most tutorials are out of date and the api docs are good, but not a good way to learn initially. The agile rails book is a good start and The Rails Way is the best rails book on the market.

---

### Post by mssever on 2008-04-10
> **jdonnell said:**
> The free online documentation isn't good for learning. Most tutorials are out of date and the api docs are good, but not a good way to learn initially. The agile rails book is a good start and The Rails Way is the best rails book on the market.
And that's the problem. Once I learned Ruby, I found the Ruby API docs to be convenient (much more so than Python's docs), but they were frustrating before I was familiar with Ruby.

When it comes to learning, however, decent documentation is lacking, as you noted. No treeware book, no matter how good, can qualify as decent documentation; if I'm working at the computer, I need the docs to be on-screen and searchable). And PDFs are no good, either, because they're difficult to read on-screen. A book available as HTML is fine.

---

### Post by pmasiar on 2008-04-10
> **mssever said:**
> especially since I don't fully grok MVC....The question is, are the various Python frameworks any better documented? 

Both Django and Python have very good documentation, couple books published, and active and friendly mailing list. Django was pronounced as "official" web app framework for beginners.

MVC is simple [HOW-TO: blog as GAE](http://bret.appspot.com/entry/experimenting-google-app-engine)

- define class for table: using Django's ORM, attributes are fields, all model code (setter/getters) are autogenerated using DB API, hiding which database is used (definition is same for MySQL, SQLite or Google's BigTable). TG is working on this wrapper.
- define templates (HTML sprinkled with access to response values)
- define mapping between URL and code handling the response and respective handlers.

In [Turbogears (demo wiki example)](http://docs.turbogears.org/1.0/Wiki20/Page1), in simple case you use @expose decorator to make function into URL, assign template, and fetch query parameters by name.

[example of template and controller](http://docs.turbogears.org/1.0/Wiki20/Page2) - in TG, templating language is kid.

Current TG is even little simpler, tg-admin wil generate sample code for you. Yes I know I promised that doc is good, it is not **that** good :oops:

> I'm on the waiting list to get an account. Hopefully I'll get one soon.

You can get SDK and try it on the desktop - deploying (when you get account) is single command. 

I hope I'll get time over the weekend to try it. :-(

---

### Post by jdonnell on 2008-04-10
> **mssever said:**
>  And PDFs are no good, either, because they're difficult to read on-screen.

They are? I use a mac for my desktop so is this pdf issue a linux thing? I use the pdf of the agile book in exactly the way you describe. But, i don't do that too often. Once I understand the basics of rails the documentation is usually sufficient for me.

---

### Post by runningwithscissors on 2008-04-11
> **pmasiar said:**
> But in terms of LAMP stack, P stands strongly for Python now.

And until PHP does not have GAE datastore bindings, PHP is legacy, too.lol. I guess it's time for Yahoo, Facebook, Wordpress et.al. to pack their bags then?

PHP is pretty much built for the web. Google offering free toys isn't going to change anything.

---

### Post by Wybiral on 2008-04-11
> **runningwithscissors said:**
> lol. I guess it's time for Yahoo, Facebook, Wordpress et.al. to pack their bags then?

PHP is pretty much built for the web. Google offering free toys isn't going to change anything.

Well, the older sites wont change anytime soon (just like some companies that started with COBOL code aren't bothering to change either). But most of these newer, 2.0 sites (not to mention some of the giants, like Youtube / Google themselves) are more and more moving to languages like Python and Ruby instead of PHP. This is only going to help push that forward.

---

### Post by pmasiar on 2008-04-11
> **runningwithscissors said:**
> lol. I guess it's time for Yahoo, Facebook, Wordpress et.al. to pack their bags then?

And you forgot Amazon's services. Yes, in opinion of many, GAE is aimed at them, and they will have much harder time to make profit now. Why pay $10/mo for shared hosting which is hard to set up and does not scale, if you can get simple setup for scalable site for free?

They are not packing, and should not, but 800 pound gorilla is in the city, and they are thinking hard about what to do next.

And Microsoft is concerned too: now we soon will have platform where anyone can create application and run it in the browser, regardless of desktop. Soon, MySQL will implement Google DB API for databases, and Dell will be selling "Google appliance" rack of web servers running software stack API-compatible with GAE, for companies to deploy and run their own web apps.

> PHP is pretty much built for the web. Google offering free toys isn't going to change anything.

"cheap toy computers" - this is exactly what said Digital Corp. (who remembers PDP and VAX?) about first IBM PC: "Digital owns department and group computing market, these toy computers cannot talk to each other, they will fade away". And curse of Digital is still strong: Compaq bought Digital, HP bought Compaq, HP is losing to Dell , in the same "department and group" computing market which Digital used to own. 

Never underestimate cheap and easy to use systems: people will learn how to use then on toy projects, so they will need no training to use them on production systems. BTW this is the same strategy which Canonical used so successfully in promoting free desktop Linux - ubuntu - to get foot in door for servers and corporate desktops. Free Linux GUI desktop 8 years ago was RH, remember?

And PHP has plenty of problems of it's own. Until now, beginners used it because PHP was the only dirt cheap hosting you can get. But now, if you can get free Python hosting with decent web app framework, like webapps or Django (with proper MVC and transactional object database) - who would pay for messy PHP with plain SQL database?

---

### Post by jdonnell on 2008-04-11
GAE also has a lot of shortcomings that you haven't mentioned. One big one is that there is not equivalent to cron.

---

### Post by pmasiar on 2008-04-11
GAE is beta, there is no equivalent of many things. Do you think that Google is not capable running cron? And even if not, it is simple to create cron job on your own server pinging specific URL to run that job.

---

### Post by jdonnell on 2008-04-11
> **pmasiar said:**
>  And even if not, it is simple to create cron job on your own server pinging specific URL to run that job.

And if I have my own server then why pay GAE? Here is a good run down on the [negatives]("http://www.tomstechblog.com/post/2008/04/Google-App-Engine-Free-and-still-barely-worth-it.aspx"). There are quite a few legitimate negatives. Don't get me wrong, this is a cool thing that has a lot of potential, but it isn't suited for all or even most serious developers.

---

### Post by pmasiar on 2008-04-11
> **jdonnell said:**
> And if I have my own server then why pay GAE?

GAE is free (up to 20GB/day, 5Mpages/mo) and are you sure that your server is as scalable as GAE? :-)

Obviously there are many negatives. If your plan is to compete with Google, GAE is not for you, etc. Obviously most serious developers, enterprise etc prefer handle all that. But for most of everybody else (50% of the developers, and 95% of curious learners), GAE is good enough. It lowers the barrier of entry to web apps, so many more people will try many more ideas. 99% of them will fail - but if they have no users, no traffic, they don't cost Google anything. And they don't cost developers anything - except of time of course, but it was learning experience.

Re: User accounts - you can implement your own, GAE docs mentions that. Most people will not bother. If you want to protect your data and users from Google, GAE is not for you.

Re: Image processing. Of course not: use your own CPU for numerically expensive calculations. Maybe something limited and simple will be added later, like cron will be.

Of course, maybe you are right and Google decides to go into cheap webhosting business and start charging $10 for simple account. But I don't think so. Here is why:

How many developers Google hires every year? say 1000? So how much is for them worth to shave 1 month of training costs? Say $20K, with all overhead. If they hire 1000 developers  already proficient (and proven experts) in their technology instead, they save $20M a year. Can they afford hosting 1M of projects, where they don't have any maintenance problems at all, for free? They spend $5M or so on "Summer of Code", and they have less direct return on that. Google will spend less than $20/y per account (they don't do any manual changes, everything is automated) and if they need, they can always use computing capacity for whatever they need, and say free users "sorry, today you have only 50%, servers are too busy". 

And if they want to buy any successful GAE project, it's easy - it already runs in their system, no conversion/redesign costs, saving them again millions a year - they buy companies like cakes. Free hosting is like recruiting and acquisition expenses - only it is cheaper.

This free hosting will 
- save money on recruiting and training
- create new opportunities, new niche industries for people creating data to be indexed and linked (new market for them), 
- force competition (Facebook, Amazon, Microsoft) react to their move. 

Cannot get any better than that!

It is exactly like those crappy IBM PC toy computers, mammal shrews in land of dinosaur mainframes: It changes rules of the game. :-)

Obviously GAE is not for "most serious developers". It is for the rest of developers, 95% of them :-)

---

### Post by Wybiral on 2008-04-12
> **pmasiar said:**
> And if they want to buy any successful GAE project, it's easy - it already runs in their system, no conversion/redesign costs, saving them again millions a year - they buy companies like cakes. Free hosting is like recruiting and acquisition expenses - only it is cheaper.

Exactly. Since most startups want to be acquired by a company like Google (for me it's PARTICULARLY Google) this makes starting easier for the actual startup (free hosting + no need to manage things = more time to worry about your actual web app) and easier on Google if they do end up wanting to acquire you (less effort to move / integrate into Google's infrastructure).

---

### Post by ruy_lopez on 2008-04-12
> **pmasiar said:**
> And if they want to buy any successful GAE project, it's easy - it already runs in their system, no conversion/redesign costs, saving them again millions a year - they buy companies like cakes. Free hosting is like recruiting and acquisition expenses - only it is cheaper.


> **Wybiral said:**
> Since most startups want to be acquired by a company like Google (for me it's PARTICULARLY Google) this makes starting easier for the actual startup (free hosting + no need to manage things = more time to worry about your actual web app) and easier on Google if they do end up wanting to acquire you (less effort to move / integrate into Google's infrastructure).

There's also value in propagating your development methodology beyond the direct benefit of exposing potential recruits/IPOs to your own frameworks. You are indirectly supporting the framework's associated ecosystem. If this produces new frameworks which are useful enough, and permissively enough licensed, Google will just adopt them for themselves, at little extra cost. Maintaining everything "in house" (which is what would happen if Google buys-out too many companies) will not produce frameworks of comparable utility to those potentially supported across the entire field of expertise.

---

### Post by jdonnell on 2008-04-12
> **pmasiar said:**
> GAE is free (up to 20GB/day, 5Mpages/mo) and are you sure that your server is as scalable as GAE? :-)


No, but it doesn't need to be in 99% of cases. My server is also a lot easier if I need cron, image manipulation, many other little things like this, and most importantly third party code/libraries. GAE, imo, is great for simple things that need to scale. I have an idea that fits that perfectly so I'll be giving GAE a go once I get my account :)

---

### Post by Wybiral on 2008-04-12
> **jdonnell said:**
> No, but it doesn't need to be in 99% of cases. My server is also a lot easier if I need cron, image manipulation, many other little things like this, and most importantly third party code/libraries. GAE, imo, is great for simple things that need to scale. I have an idea that fits that perfectly so I'll be giving GAE a go once I get my account :)

You can use any third-party libraries, they just have to be pure Python ATM.

---

### Post by jdonnell on 2008-04-12
> **Wybiral said:**
> You can use any third-party libraries, they just have to be pure Python ATM.

LOL. That's a severe limitation. What if I wanted to do full text search which I usually do with [lucene]("http://lucene.apache.org/java/docs/index.html") and [solr]("http://lucene.apache.org/solr/")

---

### Post by Wybiral on 2008-04-12
> **jdonnell said:**
> LOL. That's a severe limitation. What if I wanted to do full text search which I usually do with [lucene]("http://lucene.apache.org/java/docs/index.html") and [solr]("http://lucene.apache.org/solr/")

It's a limitation for certain things right now, but GAE hasn't even been released yet. Once that happens, I'm sure the third-party support will get better and better (especially as people keep GAE in mind when they're writing their libraries).

---

### Post by pmasiar on 2008-04-12
> **jdonnell said:**
> What if I wanted to do full text search which I usually do with lucene

Well, I have this gut feeling that Google may have full text search technology hiding somewhere just preparing to release it :-)

For $DEITY's sake, this is first beta. Release early release often - people can take a look and suggest when next. I bet that many of above mentioned things will be next (except image manipulation, which just soaks CPU time).

---

### Post by jdonnell on 2008-04-12
> **pmasiar said:**
> 

For $DEITY's sake, this is first beta. ... I bet that many of above mentioned things will be next (except image manipulation, which just soaks CPU time).

I agree completely, but you are saying that everyone should jump on this and that it should be everyones first choice now! Basically, I think your unbridled enthusiasm is a tad premature. As a business person I can't jump on this for a serious venture until I know that these missing pieces will be present and I know how much it will cost once I go beyond the limits of the free account.

I'm very excited about GAE, but we need to see how these things play out before we can say that this is a php killer as you have. Yes, google can add all these features, but will they, when, and how much will it cost? We don't know these things yet.

---

### Post by pmasiar on 2008-04-12
> **jdonnell said:**
> you are saying that everyone should jump on this and that it should be everyones first choice now! 

First choice for production? Not now, no way! But two years from now? Don't be surprised.

I just wanted to mention in how many interesting ways it changes status quo of hosted web based apps, and how it makes sense for Google to support creating this new ecosystem.

---

### Post by ago on 2008-04-16
I do not believe nobody mentioned pylons... THE glue framework at the moment IMHO (as opposed to django which is THE full-stack framework).

GAE will work with CGI and WSGI. Which means that the vast majority of python web-frameworks will run out of the box or almost (with some adjustments to their ORM and authentication layer). Pylons already works on GAE by the way: [http://code.google.com/p/appengine-monkey/wiki/Pylons](http://code.google.com/p/appengine-monkey/wiki/Pylons).

GAE is taking the best of PHP and the best of Python. See this very good article: [http://blog.ianbicking.org/2008/01/12/what-php-deployment-gets-right/](http://blog.ianbicking.org/2008/01/12/what-php-deployment-gets-right/)

In particular good features are: 

* CGI: 1 process per request, cannot do much damage... Yes I think that is good, and with big-tatble do you really need a global state? 
* File based deployment: no need to be admin to install system level software, juts upload a directroy with all the files you need. Yes that duplicates some libraries but then you also get to a consistent framework that will always work as expected when deployed, and no issue when you required a different version from the system libraries (which is not too uncommon given the pace of development in the python web frameworks sphere). Yes I know about virtualenv & co, but that is like cheating to me... 

You can now have that with GAE. And in python. No wonder Ian is so enthusiastic about it (he seems a bit less happy about the disabled modules though)...

---

### Post by pmasiar on 2008-04-16
Well, Turbogears is full-stack framework based on Pylons (TG2.0).

And in GAE, you **cannot have global state** if your app is to be seamlessly scalable to cluster.

And I do hope that Google can be cajoled to install some of the needed missing modules. We will see.

Edit: Excellent link explaining PHP and CGI. Ian is really smart and knows his stuff. Thanks.

---

### Post by ago on 2008-04-16
I'd love to see the ability to use local evnironments (local installation of eggs, file based deployments, sandboxing, insulation from system libraries and such amenities) without having to resort to virtualenv & co. Which is something not specific to GAE. GAE simply highlights the need to facilitate such setups.

PS1: I moved from TG to Pylons quite a few months back, after which I was pleased to see TG "following me" by being recoded on top of pylons, not sure what to make of TG 2 (does it really add much at this point over pylons? wouldn't it fit better if it produced "modules" to be used within pylons)... 

PS2: To be precise, by "full-stack" I mean frameworks that do not use reuse external components but have their own ORM, templating, routing... See [http://thinkhole.org/wp/2007/02/20/full-stack-vs-glue-vs-coupling/](http://thinkhole.org/wp/2007/02/20/full-stack-vs-glue-vs-coupling/) . According to this definition, TG should be positioned in the glue camp. I am in the glue camp.

---

### Post by ago on 2008-04-16
> **ago said:**
> I'd love to see the ability to use local evnironments (local installation of eggs, file based deployments, sandboxing, insulation from system libraries and such amenities) without having to resort to virtualenv & co. Which is something not specific to GAE. GAE simply highlights the need to facilitate such setups.
In fact I had posted this a few weeks before GAE announcement: [http://groups.google.com/group/comp.lang.python/browse_thread/thread/1d41355f5f02cf84/8c3492c163f172bb](http://groups.google.com/group/comp.lang.python/browse_thread/thread/1d41355f5f02cf84/8c3492c163f172bb)

didn't seem to attract much attention at the time :(

---

### Post by Steveway on 2008-05-06
I got invited and can now start building my apps.
Yay I'm so happy, perfect timing also cause I finished reading my book about Python yesterday!
For the interested ones, here is the mail I got:
> Hello,

Thanks for signing up to try Google App Engine!  Your account has been activated, so you can begin building applications!

To start creating applications with Google App Engine, simply follow this link (you may need to sign in with your ********@gmail.com Google Account):

[http://appengine.google.com/](http://appengine.google.com/)

Thanks!
The Google App Engine Team
(Censored my mail.)

---

### Post by airjaw on 2009-01-28
Boo, I'm using Django 1.02.. any idea when Google App Engine will support Django 1.02?  .96 is kinda old..

---

