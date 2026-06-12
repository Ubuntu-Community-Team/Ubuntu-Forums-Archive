---
title: "ruby php apache2 lighttpd -- one big family"
date: 2005-12-07
forum: Programming Talk
---

### Post by viniosity on 2005-12-07
I've tried a bunch of things trying to get ruby/apache2 and php working 
together.  I looked an earlier post and followed the instructions 
on a website to install lighttpd on debian.  I've gotten really far 
but I think there is one bit missing.  Here's where I am:

1. I got apache2 and php working together
2. I got lighttpd working on port 3000 and my rails app launches ok 
there

So at this stage, both PHP and Ruby are on the same server except that 
ruby is on port 3000 while the rest is going on port 80.

3. I copied/pasted this recommended vhost section into my apache2/sites-enabled  folder in order to pass the sites that will be using ruby to lighttpd

<VirtualHost *:80>
     ServerName example.com
     ServerAlias [www.example.com](www.example.com)
     #ProxyPreserveHost on #<-apache2 only
     ProxyPass / [http://example.com:8000/](http://example.com:8000/)
     ProxyPassReverse / [http://example.com:8000/](http://example.com:8000/)
</VirtualHost>

(notice no documentroot is set.. weird!)
(changing the example.com to my URL.)

4. I got an error so I used a2enmod proxy. Stopped and restarted apache2

That's where everything busted..

5. After doing that when I go to my URL I get a 403 error: Forbidden

In fact, I can't go to any IP/URL on that server without seeing a 403. 
So even the PHP stuff broke at that stage.

It's linked to the ProxyPass statements somehow.  I've tried messing 
with proxy.conf in my apache2/mods-enabled folder but that didn't seem 
to do anything.

I also changed lighttpd.conf to run on port 8000 in case that was the 
error but that also didn't change anything.

So now I'm at the stage where if I keep the proxy module I get the 403 
error and if I don't I can get to my PHP stuff, but can't get to my 
rails app.

Is there some last step I'm missing?

Has anyone had luck getting both PHP and Ruby working on the same server?

---

