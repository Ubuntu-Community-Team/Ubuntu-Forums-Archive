---
title: "Home Server URL question"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-11-25
I've set up an Apache home web server successfully, and I have all the html and css files for my website inside /var/www. Now, how do I make it so that when someone types "mydomain.com" inside their browser, it goes to my home server?

I have already purchased a domain name, hosted by GoDaddy.

Thank you!

---

### Post by nhasian on 2008-11-25
you have to set that up in your GoDaddy account.  you'll need the ip address to your computer.  hopefully you have a static ip address :)

---

### Post by doctorbighands on 2008-11-25
My IP is dynamic, but I did set up a DynDNS account. Will that work?

I'm combing through my GoDaddy account, and I don't know what to change to direct URL requests to my home server. I'm such a dolt sometimes, and don't I know it...

---

### Post by Olivier2371 on 2008-11-25
Yes it will. Now all you need to do is make sure you point your Dynamic DNS host to your external IP and you should be good to go.

for futher help I recommend you to [http://www.dyndns.com/support/kb/]("http://www.dyndns.com/support/kb/")

---

### Post by doctorbighands on 2008-11-25
I'm confused.

I can access my website by typing "<myaccount>.dyndns.org" into a browser, so I know I configured DynDNS right. That's not what I want, though. I purchased a separate domain name, and I want to be able to type IT into a browser and have it directed to my home server. That's what I can't figure out how to do.

*whimper*

---

### Post by amauk on 2008-11-25
you need to add a CNAME DNS entry

CNAME = Canonical Name
it's an alias from one domain name to another

Using a CNAME record, point www to your dyndns domain

---

### Post by doctorbighands on 2008-11-25
Where do I add that?

---

### Post by halitech on 2008-11-25
I'm not sure about linking it so yourdomainname.com will hit your dyndns account to get the IP so it knows to go to your home computer but what I used to do was buy my domain, then sign up with Zone Edit and use their DNS names on my domain DNS info and then as required, update the IP address on ZoneEdit. I found it was pretty quick in making changes and would usually be available in about 15-20 minutes after making an update.

edit: okay, sounds like amauk has a better way of doing it then mine :)

---

### Post by amauk on 2008-11-25
> **doctorbighands said:**
> Where do I add that?
I have no experience with GoDaddy, but most hosting companies allow you to edit your DNS records
(usually a web interface somewhere in your account settings)

If not, then you'll have to ask them to do it for you

---

### Post by doctorbighands on 2008-11-25
On GoDaddy, I can change "Name Servers," and that seems to do the trick. I apparently need two Name Server addresses, and I have no idea what those would be.

This all seems really difficult.

---

### Post by halitech on 2008-11-25
they allow you to do it yourself. Log into your account, go to manage hosting account, click on Settings then DNS Manager and it will allow you to add a CNAME.

---

### Post by halitech on 2008-11-25
> **doctorbighands said:**
> On GoDaddy, I can change "Name Servers," and that seems to do the trick. I apparently need two Name Server addresses, and I have no idea what those would be.

This all seems really difficult.

Leave the name servers, that is what talks to all the other DNS Servers to tell the world where to find your site. follow my instructions on my previous post to add a cname.

---

### Post by amauk on 2008-11-25
no, leave the name servers as they are
you need the domain DNS records

Maybe best if you contact them and ask them to do it

---

### Post by doctorbighands on 2008-11-25
Okay, I figured out the CNAME thing. WHEW! :) I pointed "www" to my dyndns domain name.

Now, the only thing is a section called "Host." There's an entry with an @ symbol and what looks to be a random IP address. Should I delete this, should I change it to my current IP, or should I do something else?

---

### Post by amauk on 2008-11-25
if you don't know what it does, I'd find out before changing it

---

### Post by halitech on 2008-11-25
> **doctorbighands said:**
> Okay, I figured out the CNAME thing. WHEW! :) I pointed "www" to my dyndns domain name.

Now, the only thing is a section called "Host." There's an entry with an @ symbol and what looks to be a random IP address. Should I delete this, should I change it to my current IP, or should I do something else?

I think you'll find that IP address is the IP address of their server. will check when I can get into my account

---

