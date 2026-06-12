---
title: "Programming(java to start, + 1 other)"
date: 2007-06-13
forum: Programming Talk
---

### Post by Brendan Hart on 2007-06-13
Ok im doing an adv diploma in Infotech: Web Development(covers bit of software).
I need to cash up on 1 Semester of Java(from the beggining) and do it all in this next semester.

I also want to learn a programming language so i can build stuff like web browsers for windows and linux, and other Linux programs. but mainly enough to get a webbrowser, as i want to be a web developer when i finish my studies i feel i should have knowledge of how the browser is made and how it works.

---

### Post by nyvalbanat on 2007-06-13
That's a great (although somewhat ambitious) undertaking. I wouldn't dive straight into browsers because they tend to be quite complex (anything that renders graphics can easily go to the nth degree). Instead, I would learn about http, which is what most of the web uses to deliver information. Read up on http GET and POST (which is what browsers and other applications typically use to communicate with web servers) and try utilities like wget. That way you can gain solid understanding how content is delivered from servers to browsers, without getting into the rendering part.

There are distinct client-side and server-side technologies. Client-side (html, css, javascript, ajax) are generally concerned with the presentation of the content in a browser; server-side components (java/jsp/servlets, php, etc) implement business logic (which is a broad and somewhat misleading term). You can serve straight html/javascript/css (sometimes called dhtml). By adding business logic, you can do much more, like hooking up a database to store all sorts of information, like order processing; you can also use backend technologies (like servlets) generate dhtml on-the-fly, etc.

I would definitely take a look at html and javascript first (if you haven't already). If you really want to use Java, you should learn about jsp and/or servlets. I hear Ruby on Rails is easier to work with instead of java and php is another alternative.

---

### Post by Brendan Hart on 2007-06-13
um I know html/css already pretty well, I dont think you understand, in my web development course there is:

Java for software programming mainly.(which i have half a year to catch up on they did 4hrs a week in class)

and next year we will be doing:
asp.net
vb
databases, and 10hrs a week of java(thats why i have to catch up)

i just wanted to learn another proggramming language to build in linux and also eventually get onto building a browser

---

### Post by pmasiar on 2007-06-13
> **nyvalbanat said:**
> server-side components (java/jsp/servlets, php, etc) 

... and small little pieces of SQL maybe?

It is funny how language so inflexible for text processing as java, is used for text processing (web pages generation). 

Don't get brainwashed to believing "java everywhere forever" - learn Ruby or Python so you can see how different (and much simpler) web app development can be.

---

### Post by Brendan Hart on 2007-06-13
ok what kind of applications can python get me into?

---

### Post by pmasiar on 2007-06-13
In Python you can do any application you can imagine - anything except drivers and kernel hacking. After you are done, you may identify 5% of code which uses most of running time and reimplement it (that code only!) as C library -- so you have almost C-like speed with Python-like flexibility.

- Web or GUI frontend for a commandline app
- whole applications: OLPC uses Python as main language
- games: pygame is library for that
- commandline utilities (instead of bash)

For web apps, Django, Turbogears and Pylons are most popular frameworks. They differ slightly in target audience and philosophy:

Django is closer to content management, and reinvents all parts to have them tightly integrated. Guido hates XML, so he pronounced Django ans "main" framework, whatever it buys you.
TG and Pylons are less heavy, for more flexible apps, and they integrate "best of breed" parts as plugins. TG has really wickedly smart XML template engine Kid.

---

### Post by kpolice on 2007-06-13
> **pmasiar said:**
> ... and small little pieces of SQL maybe?

It is funny how language so inflexible for text processing as java, is used for text processing (web pages generation). 

Don't get brainwashed to believing "java everywhere forever" - learn Ruby or Python so you can see how different (and much simpler) web app development can be.

The truth is that Ruby and/or Python are not used in real world applications (at least not here in México) and it is either Java, .NET or PHP (just a little bit). 

For desktop applications in Linux Python is great and I've used it a few times but now that I'm looking for a job you have to know as I told you Java, .NET, PHP or C/C++.

---

### Post by kknd on 2007-06-13
> **Brendan Hart said:**
> Ok im doing an adv diploma in Infotech: Web Development(covers bit of software).
I need to cash up on 1 Semester of Java(from the beggining) and do it all in this next semester.

I also want to learn a programming language so i can build stuff like web browsers for windows and linux, and other Linux programs. but mainly enough to get a webbrowser, as i want to be a web developer when i finish my studies i feel i should have knowledge of how the browser is made and how it works.

Browser? C++.

---

### Post by Brendan Hart on 2007-06-14
uhm i never said c++, im enrolled in the course now, I have to catch up on 1 semester of java, woot i rpl'ed like 9hrs a week of schooling, so that will mean im full time except only doing like 11 hrs a week, thats less than 2 school days!! I am happy, but my outside study must be so much more!!

---

### Post by Tomosaur on 2007-06-14
The Java API has pretty much everything you need to build a browser readily available. It's simply a matter of picking the objects which best suit your browser, and then lumping them altogether. Some aspects may need extra coding, but the bulk of the work is there for you to piece together. I suppose the biggest advantage of a Java web browser is the ability to easily add experimental features - you won't have to worry so much about all the run of the mill stuff.

That being said, you can probably find the same stuff for any of the popular languages, it's just that Java has all of it in the main classes. However, I'm doing software development in uni - the first semester of Java was really, really basic stuff - nothing at all like building a browser. If it's web development you want to go into, then you don't really need to know how a browser works - you just need to know how browsers interpret the information given in web pages, and, of course, the differences between browsers which cause broken web pages.

---

