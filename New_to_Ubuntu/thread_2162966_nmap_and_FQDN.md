---
title: "nmap and FQDN"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by Cthulu2156 on 2013-07-16
Hello,    ThisJu is sort of a question about whether someone can hack my computer.  Just wondering what it is exactly that zenmap is showing me.  I was just trying to see if I could access my computer through a browser etc. I ran zenmap/nmap and as it is it comes up with something like "c-85.222.413.111.abc2.ri.comcast.net" - is that the FQDN?  It appears I do not have a domain name set, but was wondering if the IP address basically substitutes for that, and if so what does someone get if they are trying to get into my computer through my ip adress.  And when I run hostname it comes up with my computer name and no domain name set.  Just wondering if it is at all possible to just set up a domain name and just be able to type that into my browser - and also why if I type in what came up in zenmap can I not view anything on my computer?  Do I have to set up a domain name and pay for space on a server or can I just set one up myself?

---

### Post by newbie-user on 2013-07-16
No one can hack into your system until you start opening up ports that are available to the Internet, such as SSH, web, etc. Even then, there are ways to harden your system to prevent unauthorized access. You can't view anything on your computer through your browser because you're not hosting any Internet services.

"c-85.222.413.111.abc2.ri.comcast.net" is the name that comcast assigns to your connection. It has nothing to do with getting your own domain, which you are free to do by signing up with a domain name registrar. You don't have to pay for hosted server space if you don't want to. However, it is a good idea to do that if you want to run your own domain with web services and Comcast blocks port 80.

---

### Post by dannyboy79 on 2013-07-16
what type of equipement do you have? a modem/router? a modem and a separate router? only a modem?

---

### Post by Cthulu2156 on 2013-07-16
Ok, thanks for your replies.  I just have a cable modem, and then my ethernet on my laptop.  I was thinking of getting a domain like newbie-user suggests - then would I be able to actually host the website on my laptop, a way around paying for server space?  I don't know all the details about what comcast does regarding port 80.  As far as my hardware goes, it's just the cable modem (which I don't know all the details on) and a Broadcom gigabit ethernet adapter.  Any suggestions?

---

### Post by dannyboy79 on 2013-07-16
so you have no hardware firewall (normally built into a consumer grade router) which is protecting your computers "services" from the outside world. I would be very leary about running any services like a webserver or a ssh server IF you don't also run a software firewall OR purchase a home router with a built in firewall. 

i don't know if comcast blocks port 80 BUT if they did you can run a webserver from a non-standard port but when you want to access it, you'll have to enter for example: [www.mysite.com:8080](www.mysite.com:8080)
that would be if you ran apache2 on port 8080

you don't need a domain name per say unless you want to choose the exact name of it. i use dyn-dns and setup a hostname, for example to access my home server I enter mysite.dyndns-home.com. Doing it that way is much more affordable. I get to choose the beginning, but the end part is pre-defined. "dyndns-home.com" is not the only option, they have many to choose from.

---

