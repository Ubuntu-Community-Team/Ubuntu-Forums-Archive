---
title: "Crash course in Web App development?"
date: 2014-01-24
forum: Programming Talk
---

### Post by paradox2 on 2014-01-24
Hey guys,

I didn't quite know where to ask this question, so I come to you, the reliable people of Ubuntu for answers. I have recently written a mobile application that is doing well, and I would like to now take that application and reimagine it as a web app. I have no experience with web programming outside of basic HTML and CSS. I do however come from a strong background in iOS programming, Java, and C++. I would like to find some sort of crash course into creating a web app. I know I need not only a fast clean front end, but I believe I would best be served if I had a database that my web app, iOS app, and future apps on other platforms could pull from. I have no experience with databases either. I do however have time and motivation. 

Where should I start? What do you recommend I use? Any advice?

Thanks,

An entrepreneur

---

### Post by tfrue on 2014-01-24
When I was super into learning web apps, I went to codecademy. Here is there link:
[http://www.codecademy.com/](http://www.codecademy.com/)

Look around there because they have a lot of stuff to teach you.

If you want your own server to play with, then I recommend getting an Ubuntu distro, I used the server .iso since it would support what I want to do, installing LAMP (Linux Apache MySQL PHP),
and reading through the man pages, and examples on the internet.

Chris

---

### Post by tgalati4 on 2014-01-24
Why don't you share us the link for the app so that we can see what it does?  That would help us steer you to the best framework to host your app.  

I agree with *tfrue* and I would set up my own server install the LAMP stack then start playing with some [services]("bitnami.org/stacks") to see which comes closest to handling your use cases.

---

### Post by zobayer1 on 2014-01-27
As you've mention you have quite good base on Java, I think you should try something like "Spring", or "EJB" for web app development. There are lots of resources on these things over the net. For servers, JBOSS, TomCat, Oracle Weblogic would also come in handy. For Database, you can learn anything you like, but if you target production level, give a go for Oracle as well. And for what you want to use, you do not need to learn database that hard as most of the database thing will be done through java code if you use spring or ejb like frameworks. Learning curve for these are bit bumpy though.

And if you go for php (as you have strong c++ skills, won't be a problem), go for apache server as someone also mentioned, you can install LAMP, WAMP, XAMP or whatever you like. Popular database would be mysql in this scenario, easily capable of handling lightweight requests.

In all of the cases, you need to learn javascript libraries and json a bit as well, because now-a-days, people tend to do most of the computations or rendering on the client side, instead of overloading the remote servers, as many server and cloud services will charge you according to resource utilizations.

---

