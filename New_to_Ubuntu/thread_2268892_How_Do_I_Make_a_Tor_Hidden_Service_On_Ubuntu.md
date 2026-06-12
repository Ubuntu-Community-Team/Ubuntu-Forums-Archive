---
title: "How Do I Make a Tor Hidden Service On Ubuntu?"
date: 2015-03-12
forum: New to Ubuntu
---

### Post by matthew78 on 2015-03-12
I have just installed ubuntu to my laptop and just installed Tor Browser to my desktop. But my question is how do I make my own hidden service on Tor? I have seen some guides but don't quite understand, I'm brand new to ubuntu this is my first Linux! So please if anyone could walk me step by step that would be awesome, because I don't understand all the commands yet so it is kinda hard right now. I'm sure it is quite easy though once I learn how. Thanks in advance guys!!

---

### Post by dino99 on 2015-03-12
if your real question is : will i'll be anonymous, then no.

 you'd be just as well protected as Tor... but you would not be anonymous. Be scary of the numerous fake onions.

---

### Post by matthew78 on 2015-03-12
> **9d9 said:**
> if your real question is : will i'll be anonymous, then no.

 you'd be just as well protected as Tor... but you would not be anonymous. Be scary of the numerous fake onions.Umm no lol my question is how do I make my own .Onion website using ubuntu lol...

---

### Post by matthew78 on 2015-03-12
So does anyone know?

---

### Post by JeQhdMD on 2015-03-13
Pre-Pre-requiste:   Setup Apache Web Server in Ubuntu:  [https://www.youtube.com/watch?v=-q8Jj4aAWYw](https://www.youtube.com/watch?v=-q8Jj4aAWYw)

Pre-requisite:  How to setup Apache Web Server in Linux:[http://www.htpcbeginner.com/how-to-setup-apache-web-server-on-ubuntu/](http://www.htpcbeginner.com/how-to-setup-apache-web-server-on-ubuntu/)

Hidden service setup:  [http://www.makeuseof.com/tag/create-hidden-service-tor-site-set-anonymous-website-server/](http://www.makeuseof.com/tag/create-hidden-service-tor-site-set-anonymous-website-server/)

edit:   suggest you actually setup a sandbox partition via gparted before doing any of the above.   Some admins don't like to use apache web server with Tor, but it's acceptable in a sandboxed environment if you follow the security protocols listed in the second link.    Note that running any web server is NOT recommended for the casual computer user - - some experience and skill is required otherwise it's a risk.    Or, you could install [http://www.acme.com/software/thttpd/](http://www.acme.com/software/thttpd/) instead of Apache.

---

