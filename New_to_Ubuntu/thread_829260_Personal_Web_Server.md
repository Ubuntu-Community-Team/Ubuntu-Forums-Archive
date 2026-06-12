---
title: "Personal Web Server"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by chiraag on 2008-06-14
Hi

I have been using Ubuntu for about a month now.
I am currently running the Desktop edition of Hardy Heron on my laptop.
I want to set up a small Apache based server to host a few web pages. I am not expecting high traffic. Also I do not intend to keep this server online 24/7. I want to create this server more like a proof-of-principle project rather than for any functional use. 
Also since I intend to use the same laptop for my day-to-day work I do not want to install the server version of Ubuntu.I have already installed the LAMP pack using synaptic. 
However I am clueless about the actual procedure of setting up a server.
Can anyone guide me to a tutorial on how to proceed from this point onwards. I have very little knowledge of the exact inner workings of a server and I do not know what changes are to be made to the numerous config files. Although given the changes I will be able to implement them.

P. S.
I am not averse to doing things in the terminal as I already do most of micro-controller coding from the terminal.

---

### Post by kalesh7 on 2008-06-14
install webmin (using package manager or sudo apt-get install webmin)
open [https://localhost:10000](https://localhost:10000) in browser (if you get a warning or something about a certificate, as you most probably will, click accept, install or similar, its no problem since you are connection to your own pc)
enter your username and password(same as your ubuntu user and pass)
click on servers, apache webserver, modify the default server to point to where you want to store files to be served. apply changes(top right)

there are other ways but I have found this the easiest.

---

### Post by cariboo on 2008-06-14
You have basically set everything up already. To access your wweb server just open a browser and type in the address bar **[http://localhost](http://localhost)** A web page should pop up saying **it works!**

All of the web page files are located in /var/www. You can just copy your web pages to that location, or the way I do it is to create all the files in my home directory and just create a sym-link to them in /var/www eg:

```
jimk@intrepid:/var/www$ ln -s /home/jimk/web_pages web_pages
```

Them to access the page you would enter in your browser [http://localhost/web_pages](http://localhost/web_pages)

Have fun

Jim

---

### Post by chiraag on 2008-06-14
Hi

Seemingly webmin is not included in any of the repositories I have. Any specific repository that I need to add?
Alternatively should I just get it from their site and compile from source. Also could you direct me to some place where I can learn some networking concepts.

Chiraag

---

### Post by chiraag on 2008-06-14
@cariboo907
How do i manage to access these pages from some other computer. Do I need to allocate some static IP or something (I have no idea as to how). As I understand it, localhost should only work from my machine. 

Chiraag

---

### Post by inportb on 2008-06-14
IP allocation needs to be done on your router. You may also need to set up port-forwarding. Depending on the router you have, the procedures would be different.

Webmin is quite a useful browser-based server management tool, but it looks like eBox works similarly. I have zero experience with eBox, but I can tell you that it's in the repositories and is easier to install.

[http://webmin.com/deb.html](http://webmin.com/deb.html)
[http://ebox-platform.com/](http://ebox-platform.com/)

---

### Post by Frenske on 2008-06-14
One of the biggest names in web management is Joomla! I have tried it to set up a test website for myself (stopped doing it since I was in the middle of a move). It is quiet easy and the websites it produces looks nice.

---

### Post by inportb on 2008-06-14
Joomla! is not a server management tool; it's a content management system (think: it's basically a really fancy templating system with lots of nifty tools for running up a website). It is indeed quite popular. It's also infamous for sucking performance down the drain if you don't tune it properly. You should have no trouble running it on a dedicated server, though.

Drupal is another nice CMS; it seems to be lighter on the resources.

Wordpress is blog-only, but it has a really simple interface and plugins that provide CMS-like behavior; I'd go with Wordpress if there are no specific requirements that it cannot meet.

---

