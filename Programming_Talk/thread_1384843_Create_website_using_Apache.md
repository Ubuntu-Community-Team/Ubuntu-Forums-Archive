---
title: "Create website using Apache"
date: 2010-01-18
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2010-01-18
Hello all, I post this in the general help section not really knowing where to put it, but I doubt I'll get any real help there, so hopefully you guys can help me out.
I'm looking to create a website using Apache. The only problem is that I don't really know where to start. Can any one help me get started?; how to create your domain name, where to put your html files, how implement python scripts in your code, etc. 
Any help would be appreciated!

---

### Post by Hellkeepa on 2010-01-18
HELLo!

You don't use Apache to create a website, you use it to serve (send) a webpage to other people. What you want to do is to find yourself a (x)HTML and CSS tutorial, and learn these two languages. Use any text editor you'd like to write the code, and remember to use [W3C's validation service](http://validator.w3.org).

Happy syncin'!

---

### Post by c0mput3r_n3rD on 2010-01-18
> **Hellkeepa said:**
> HELLo!

You don't use Apache to create a website, you use it to serve (send) a webpage to other people. What you want to do is to find yourself a (x)HTML and CSS tutorial, and learn these two languages. Use any text editor you'd like to write the code, and remember to use [W3C's validation service]("http://validator.w3.org").

Happy syncin'!


Alright I've been looking at tutorials and got something working (I'm not sure what).  I followed [this]("http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2") tutorial and that all works.  A more refined question is how do I make my site visible to other users.  When I'm on my computer I can put in the web address and it connects, but I can't connect to it from a different computer.  Once I figure that out I'll be up and running.

Edit: When I click on rapache from Applications -> System Tools -> rapache it says that there are unresolved issues with my site.  It says I have to normalize the site to manage it.  When I click Resolve it freezes.  Hope that helps.

---

### Post by Hellkeepa on 2010-01-18
HELLo!

Trust me when I say that Apache is not necessary at all. It's somewhat similar to ordering a catering firm, just to have them watch you make your own supper.

What you need to do, is to go to sites like [W3 Schools](http://w3schools.com), and learn how to use the basic tools first. Once you know HTML and CSS, you can begin to expand into server side scripting languages (like PHP, Python, Ruby (on rails), or similiar). That's the only time you really need to have a web server running locally.
Static HTML-pages are equally well tested when opening them locally form the hard drive, as from a web server.

Happy codin'!

---

### Post by c0mput3r_n3rD on 2010-01-18
> **Hellkeepa said:**
> HELLo!

Trust me when I say that Apache is not necessary at all. It's somewhat similar to ordering a catering firm, just to have them watch you make your own supper.

What you need to do, is to go to sites like [W3 Schools]("http://w3schools.com"), and learn how to use the basic tools first. Once you know HTML and CSS, you can begin to expand into server side scripting languages (like PHP, Python, Ruby (on rails), or similiar). That's the only time you really need to have a web server running locally.
Static HTML-pages are equally well tested when opening them locally form the hard drive, as from a web server.

Happy codin'!


I know html and I'm learning Python.  I really just need to know how to publish my site on the web so the world can see. :)

---

### Post by slavik on 2010-01-18
have you tried searching for an apache howto on [https://wiki.ubuntu.com](https://wiki.ubuntu.com) ?

---

### Post by Hellkeepa on 2010-01-19
HELLo!

I would recommend paying for a web host then, or perhaps see if you can find a free one if money is the object. Running a web server comes with a host of security issues, and you really have to know what you're doing in order to run a public web server.

For testing and development, follow **slavik**'s recommendation.

Happy codin'!

---

### Post by c0mput3r_n3rD on 2010-01-19
> **slavik said:**
> have you tried searching for an apache howto on [https://wiki.ubuntu.com](https://wiki.ubuntu.com) ?

No I haven't but I will.  Thank you for the link.

---

### Post by HeadlessZombie on 2012-09-10
If you are behind a router or firewall, you need to place the web server inside the DMZ.

---

### Post by overdrank on 2012-09-10
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

