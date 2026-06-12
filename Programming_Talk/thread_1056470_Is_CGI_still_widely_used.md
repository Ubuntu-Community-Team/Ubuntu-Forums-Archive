---
title: "Is CGI still widely used?"
date: 2009-01-31
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-31
I have heard that servlets are more superior than CGI. Is CGI still widely used and is it going to be like this for a while?

Or are there newer technologies that would be better choices?

Thanks.

Paul

---

### Post by Nathan_M on 2009-01-31
I think there is a very slow movement away from CGI, but it is still used. I seem to remember there being a movement away from CGI in the early half of this decade, so it is very slow indeed. I'm not quite sure why you're asking the question, but if (as I would speculate) you're planning on giving yourself some kind of refresher and implementing CGI for something, I would just start again with servlets... future-proofing!

---

### Post by wmcbrine on 2009-01-31
CGI isn't going anywhere, because it's such a simple, straightforward system. That doesn't mean it's *always* the right answer.

---

### Post by Mr.Macdonald on 2009-01-31
CGI is the main way for programs to interface the the server app. Other that CGI you have servlets and what ever ruby gives you. But cgi lets you use any language you want, as long as it first prints "Content-type: text/html". Thus CGI works with anything that can read and write files (all programming languages). And you don't have to install a new module for each language.

This may be considered low tech, but so is languages like C, C++, Assembly. They don't have much features but are incredibly powerful. Java is way more "High tech" but lacks alot of power and low level abilities.

Servlets are nice but if you want to have a hacked up website, CGI is th way to go. I have a site that have a bash console, accessable via a password prompt that used dynamic keys (changed to random sequence upon every access and 2 failures.

I also don't believe that Java is the future, nothing will every outdate C, C++, Lisp's, Python. Java makes somethings very easy but other's impossible. You can do anything you want in C, C++, Python, Lisp. I guess it all comes down to Security or Freedom.

I chose freedom!

---

### Post by slavik on 2009-01-31
in a nutshell, what I understand about CGI from a practical standpoint is that the get string sets environment variables and post data comes in through STDIN. as long as you can read stdin, you can use any language. the big problem is keeping state between runs of your code ... this is where all those mod_language come in very handy.

---

### Post by CptPicard on 2009-02-01
CGI is a very ugly and way too rudimentary way to do web apps in 2009... I don't understand the C/C++ -comparison at all (well, I don't understand the whole supposed "power"-argument but let's not go there this time...). It's as if removing everything except a stdin and stdout gave you more "power" in web apps. It doesn't.

At least the last time I looked at it, you actually had to spawn an actual process for each request. Not good. Plus you have to build an entire architecture from totally scratch, using such process-per-request model. I do understand that the asm guys are going to come out of the woodwork declaring that they're so smart that they prefer doing that because it gives them all the power!!1 (that is, they have to do a lot of busy-work), but idle boasting is just that ;)  -- you could just as well argue that you would do better writing your web app directly using the OS socket API.

Anyway, check out something like TurboGears or Django. They can do quick and dirty and bigger apps, all with proper architecture, with a good language (python). Or Ruby on Rails if you are so inclined.

---

### Post by slavik on 2009-02-01
> **CptPicard said:**
> CGI is a very ugly and way too rudimentary way to do web apps in 2009... I don't understand the C/C++ -comparison at all (well, I don't understand the whole supposed "power"-argument but let's not go there this time...). It's as if removing everything except a stdin and stdout gave you more "power" in web apps. It doesn't.

At least the last time I looked at it, you actually had to spawn an actual process for each request. Not good. Plus you have to build an entire architecture from totally scratch, using such process-per-request model. I do understand that the asm guys are going to come out of the woodwork declaring that they're so smart that they prefer doing that because it gives them all the power!!1 (that is, they have to do a lot of busy-work), but idle boasting is just that ;)  -- you could just as well argue that you would do better writing your web app directly using the OS socket API.

Anyway, check out something like TurboGears or Django. They can do quick and dirty and bigger apps, all with proper architecture, with a good language (python). Or Ruby on Rails if you are so inclined.
umm, afaik, any mod_language has an interpreter running in the background, but only Java has something that can manage things under your app (like DB connections) whether your app is alive or not and you still have to use some kind of library in php/python/perl to create a DB connection every time your code runs.

---

### Post by CptPicard on 2009-02-01
OK. I haven't really done web apps in anything else than Java to be too well versed in that. TG at least does abstract nicely though, then...

---

### Post by slavik on 2009-02-01
> **CptPicard said:**
> OK. I haven't really done web apps in anything else than Java to be too well versed in that. TG at least does abstract nicely though, then...
is abstraction the point of your post? because java app servers abstract it so much that you don't even think about anything about a connection, you literally have no way of knowing where the DB is, or the type of the DB or what credentials are used, or whether the DB connection is even valid or not ...

```

         app     ||      app server                          ||      db server
api.connectdb(); -> connection pool -> data source -> socket -> socket -> DB engine

```

you can have multiple apps use the same data source (same db and same credentials for the db), and if the credentials or location of db changes, you change it in the app server and that's it. no need to change your app in any way what so ever. now you can package your app as a single "run anywhere" binary and not have to worry about documenting the DB config instructions since that is already done for you at the app server level.


EDIT:
Here's another architecture:

2 LB -> 10 WS -> 50 AS -> DBC

where:
LB = Load Balancer
WS = Web Server
AS = Application Server
DBC = DataBase Cluster

the number is the number of servers in each tier.

After having worked with Java app servers, Java starts to grow on you not as a language, but as the infrastructure that exists for it.

---

### Post by CptPicard on 2009-02-01
Eh, I know all of that. I do my web dev almost exclusively on Java. :)

And yes, it's all in the infrastructure, and that is both a good and a bad thing... there is absurdly much infrastructure in Java web apps. :) It's only recently started getting better when the abstraction is not just only about adding more layers and "stuff" and XML, but about cutting a lot of crap too.

---

