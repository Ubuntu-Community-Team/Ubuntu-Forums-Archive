---
title: "RubyOnRails, Apache, FastCGI"
date: 2006-04-25
forum: Programming Talk
---

### Post by skeeterbug on 2006-04-25
I used dapper repositories and installed ruby 1.8.4, rails is at version 1.1.2. Those seem to be ok. I followed this tutorial in the wiki: 
[https://wiki.ubuntu.com/ApacheRailsFcgi?highlight=%28rails%29](https://wiki.ubuntu.com/ApacheRailsFcgi?highlight=%28rails%29)

However, when I go to access a controller method, I am getting a file not found error in my apache log: "[Tue Apr 25 16:23:19 2006] [error] [client 192.168.1.3] File does not exist: /var/www/rt/public/test". Am I missing something from the tutorial? I have tried googling around a bit, but other guides want you to edit .htaccess (the wiki wants you to remove it). Thanks in advance to anyone that can help me out! :)

---

### Post by hotani on 2006-05-05
I'm having the exact same problem it seems. Everything looked to install fine, rails created the test application, the test page comes up (why wouldn't it? It's just html!), but nothing seems to work correctly. Accessing a test controller brings up the 404.

I've been all over the .htaccess, tried fastcgi vs fcgid, nothing seems to change. 

Everywhere I've been says "use fcgid instead of fastcgi for apache2" but neither seems to be doing anything.

---

### Post by Luke Psywalker on 2006-05-09
I made it a little bit futher, I'm just getting a rails application error :-|

I'm pretty sure its just a permissions problem, because I didn't understand this line of the wiki tutorial:

> Then, verify that apache will be able to reach the files (ie. they are either world-readable, or "group-readable" by the www-data group).

What 'files' are they refering to? I have chgrp'ed <app>/public/dispatch.fcgi into the www-data group but is there anything else I need to do?

---

