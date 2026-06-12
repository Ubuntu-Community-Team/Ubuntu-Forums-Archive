---
title: "[Python] Simple Server"
date: 2011-07-11
forum: Programming Talk
---

### Post by ki4jgt on 2011-07-11
I stumbled on SimpleHTTPServer (wonderful tool by the way) and was wondering if you guys could recommend any tutorials for HTTP servers. Basically, I'm wanting the server to initially ask the user for their email, and then ask them questions that they may answer by clicking buttons.

Question. . .
[A] . . .
[B] . . .
[C] . . .
[D] . . .

If the question is correct, the server emails the user.

I do not wish for you guys to do this for me, just to send me off in the right direction. If you think another software would be better for this, please suggest it, but I DO NOT want anything as complex as xampp or apache. Thanks guys :-)

---

### Post by nmaster on 2011-07-11
> **ki4jgt said:**
> I DO NOT want anything as complex as xampp or apache

i know this doesn't answer your question, but it is much easier to do this by installing apache2 and then just writing some HTML and cgi scripts. 

just "apt-get install apache2" and then start working in /var/www/.  super simple.  why does this seem "complex"?

---

### Post by ki4jgt on 2011-07-11
> **nmaster said:**
> i know this doesn't answer your question, but it is much easier to do this by installing apache2 and then just writing some HTML and cgi scripts. 

just "apt-get install apache2" and then start working in /var/www/.  super simple.  why does this seem "complex"?

I don't know LOL, it's just the whole concept of databases, PHP, plus xmapp adds this and that tool. I'm running it through Tor and I was told that Apache doesn't work great with Tor (Tor Website) So, I'm trying to use something where I can specify port w/o having security issues. If this is the best route though, I would much rather go with xampp. I've seen tuts online for it. I pretty much like the idea of simple drag and drop hosting, but also want the complexities of configurability + (Possibly a GUI)

---

### Post by nmaster on 2011-07-11
> **ki4jgt said:**
> I don't know LOL, it's just the whole concept of databases, PHP, plus xmapp adds this and that tool. I'm running it through Tor and I was told that Apache doesn't work great with Tor (Tor Website) So, I'm trying to use something where I can specify port w/o having security issues. If this is the best route though, I would much rather go with xampp. I've seen tuts online for it. I pretty much like the idea of simple drag and drop hosting, but also want the complexities of configurability + (Possibly a GUI)

i've used tor bundled with firefox but i don't have much experience with it and i've never used xampp.

in any case, using a proper web server makes life easy. you can look at the website in my signature to see examples of forms that i've make with html, css, and javascript.  i use php for the cgi, but its quite effective. you can also use reCAPTCHAs to prevent bots from messing with you. this is definitely a security boost.

---

### Post by ki4jgt on 2011-07-11
> **nmaster said:**
> i've used tor bundled with firefox but i don't have much experience with it and i've never used xampp.

in any case, using a proper web server makes life easy. you can look at the website in my signature to see examples of forms that i've make with html, css, and javascript.  i use php for the cgi, but its quite effective. you can also use reCAPTCHAs to prevent bots from messing with you. this is definitely a security boost.

ICYDK - XAMPP is just apache bundle with extra stuff. Database support and so forth. I'm running a hidden service on Tor. I like the fact of having a domain name for a dynamic IP address. I know DDNS works too, but I like the fact of actually being able to setup and control that aspect of the service too. Thanks for the reCAPTCHA advice. I've been wondering how to go about swarting bots.

---

### Post by cgroza on 2011-07-11
Bottle seems what you are looking for.

It works by mapping functions to URL, but it is far more versatile.
I have only taken a superficial look over it but I think you will like it.

You should be able to find the documentation and tutorials with no problem.

---

### Post by juancarlospaco on 2011-07-11
> **cgroza said:**
> Bottle seems what you are looking for.


**+1 [http://bottlepy.org](http://bottlepy.org)**

---

### Post by nmaster on 2011-07-11
bottle looks tight ;)

---

### Post by ki4jgt on 2011-07-11
> **cgroza said:**
> Bottle seems what you are looking for.

It works by mapping functions to URL, but it is far more versatile.
I have only taken a superficial look over it but I think you will like it.

You should be able to find the documentation and tutorials with no problem.

I like this :-)

---

### Post by juancarlospaco on 2011-07-11
> **ki4jgt said:**
> I like this :-)

35 Seconds...
[http://www.youtube.com/watch?v=vfzz36Hbetg](http://www.youtube.com/watch?v=vfzz36Hbetg)

---

### Post by cgroza on 2011-07-12
> **juancarlospaco said:**
> 35 Seconds...
[http://www.youtube.com/watch?v=vfzz36Hbetg](http://www.youtube.com/watch?v=vfzz36Hbetg)
VIM! I gave it thumbs down.:D

---

### Post by ki4jgt on 2011-07-12
Went with Apache. Installed PHP and MySQL. Bound it to localhost. Spent the better half of the morning figuring out which files to edit to bind it. Then had to find out where to place my URL from Tor. Now it's all good. I'm taking a PHP tut from thenewboston.

---

### Post by nmaster on 2011-07-12
> **ki4jgt said:**
> Went with Apache. Installed PHP and MySQL.

LAMP! i hope my suggestion works out for you ;)

---

### Post by ki4jgt on 2011-07-12
The LAMP/XAMPP (according to XAMPP it's the same project) people said not to use it on productive machines. They said it was just setup for practice coding and had some security issues in an actual field environment. So, I installed all three individually. My next question of course is, what can I do to thwart my own security issues? What safety precautions should I take?

---

### Post by TwoEars on 2011-07-12
> **ki4jgt said:**
> The LAMP/XAMPP (according to XAMPP it's the same project) people said not to use it on productive machines. They said it was just setup for practice coding and had some security issues in an actual field environment. So, I installed all three individually. My next question of course is, what can I do to thwart my own security issues? What safety precautions should I take?

The best way to learn is to practice. Get a friend to try all sorts of things on your server, and report back everything he runs into. You won't learn everything, but it's much better than me just telling you what you need to watch out for. ;)

---

### Post by ki4jgt on 2011-07-12
> **TwoEars said:**
> The best way to learn is to practice. Get a friend to try all sorts of things on your server, and report back everything he runs into. You won't learn everything, but it's much better than me just telling you what you need to watch out for. ;)

Don't have friends in the tech world :-( The only thing I could think of currently is DDOS. My bandwidth is limited to a measly 500KB/s connection. The fact that all the resources on the server are only a few bytes helps a lot, but other than that, I don't have people to test my server's strengths and weaknesses. I'm running through Tor, so the port 80 which the connections come in on is only a virtual port. The actual server is on a different port (if that's secure enough) However, I may recruit some people over at Hackforums for their assistance :-)

---

### Post by nmaster on 2011-07-12
> **ki4jgt said:**
> The LAMP/XAMPP (according to XAMPP it's the same project) ...

i didn't realize it was a project. I thought LAMP was just an acronym for a particular set of software packages that are often used together: [http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29](http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29)

---

### Post by ki4jgt on 2011-07-12
> **nmaster said:**
> i didn't realize it was a project. I thought LAMP was just an acronym for a particular set of software packages that are often used together: [http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29](http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29)

I'm a noob. You'll have to excuse my ignorance/educate me LOL. That's what their site said, but they did spell it with an extra P. So, their spelling is LAMPP.

---

### Post by juancarlospaco on 2011-07-12
LAMP = Linux Apache MySQL Python

Everyone knows that  ;)

---

### Post by TwoEars on 2011-07-12
> **ki4jgt said:**
> Don't have friends in the tech world :-( The only thing I could think of currently is DDOS. My bandwidth is limited to a measly 500KB/s connection. The fact that all the resources on the server are only a few bytes helps a lot, but other than that, I don't have people to test my server's strengths and weaknesses. I'm running through Tor, so the port 80 which the connections come in on is only a virtual port. The actual server is on a different port (if that's secure enough) However, I may recruit some people over at Hackforums for their assistance :-)

DDoS is currently the most reported "hacking" attack as it is the simplest to perform and requires only resources on the primary node's behalf. It's also hard to defend against, provided there are enough nodes. If not, it's the simplest to defend against - just ban the nodes' from your site.

If you intend on becoming a system administrator, you're going to have to learn about these things. There are quite a few websites to learn from - hackthissite, etc. Python challenge is also quite good, it involves manipulating a website in ways you might not think of automatically. Also, read security releases and try doing things to websites that you shouldn't be able to do. Learn about sql injections - for this, I suggest a simple Python program using SQLite.

---

