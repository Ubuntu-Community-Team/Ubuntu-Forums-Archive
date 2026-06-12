---
title: "Running a live web server"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by MaxVK on 2012-02-01
Hi guys. I'm a (fairly) long time user of Ubuntu, but not greatly experienced at the more complex setups that are possible.

I have been asked to set up a web server for a small company. The server will have Apache/PHP/mySQL etc and it will be used to run a web application that is being used for their database needs. They would like this machine to be connected to the internet so that field workers can log into the web app and their diaries etc.

My question(s):
I have Ubuntu 10.04 right now, not the server version, just desktop. Is the the server version essential or will this be enough?

What are the various security aspects that I will need to consider to make this system secure? I have complete access to all user laptops, so if I need to get information or put software on them there is no problem. The server machine will be behind a hardware firewall (we are looking at some Sonicwall kit) and I have been given total control of setting up whatever I need.

Whatever I put in place needs to be easily usable 24/7 for the staff in the head office (with the server) and the field workers (about 10 of them) who *might* need to log in every now and then.

Any advice, tips or tricks that might help would be very gratefully received.

Cheers

Max

---

### Post by partloer on 2012-02-01
Hi Max,

Well you are on the right track.  You don't need Ubuntu Server either version will work.  

As for security...well that is an ongoing challenge.  One of the main things to do is remember to change all of your default passwords and to use a strong password.  

Other than that it really depends on what your website will do and how it will be configured which requires a lot of learning.

---

### Post by sandyd on 2012-02-01
> **MaxVK said:**
> Hi guys. I'm a (fairly) long time user of Ubuntu, but not greatly experienced at the more complex setups that are possible.

I have been asked to set up a web server for a small company. The server will have Apache/PHP/mySQL etc and it will be used to run a web application that is being used for their database needs. They would like this machine to be connected to the internet so that field workers can log into the web app and their diaries etc.

My question(s):
I have Ubuntu 10.04 right now, not the server version, just desktop. Is the the server version essential or will this be enough?

What are the various security aspects that I will need to consider to make this system secure? I have complete access to all user laptops, so if I need to get information or put software on them there is no problem. The server machine will be behind a hardware firewall (we are looking at some Sonicwall kit) and I have been given total control of setting up whatever I need.

Whatever I put in place needs to be easily usable 24/7 for the staff in the head office (with the server) and the field workers (about 10 of them) who *might* need to log in every now and then.

Any advice, tips or tricks that might help would be very gratefully received.

Cheers

Maxa)The desktop version is enough, but it is not as secure as the server version.

For security, you might want to consider how they are connecting (i.e. over openvpn?).

What do you mean by easily usable? easily administrated? easily accessed?

---

### Post by MaxVK on 2012-02-01
Thanks guys:

> For security, you might want to consider how they are connecting (i.e. over openvpn?).
Right now I'm assuming that field workers will navigate to the correct page as normal, then log in and view their diary entries, and...

> What do you mean by easily usable? easily administrated? easily accessed?
The users/admins in the HQ will open the web page as localhost so that diaries can be updated, client details logged etc, etc.

As long as both field workers and HQ workers can log in there should be no problems. I just don't want a system that slow to use because it is bogged down with security software etc - maybe I'm remembering back to the bad old days of windows.

> Other than that it really depends on what your website will do and how it will be configured which requires a lot of learning. 
I touched on this above - the plan is to have a domain that will display the company website, and alongside it, possibly on a different domain or perhaps access via just an IP address, the database app that every one will want to use.

For the most part the only users will be in the HQ, booking clients, logging inventory, updating workers diaries etc, etc, but at some point field workers will want to check their diary entries.

I don't see there being huge amounts of traffic to the website, and the vast majority of access to the database app will be at HQ - there are no more than five people there all the time anyway, and they wont all be using it at the same time.

I'm open to suggestions about connections etc, and any 'right' ways of doing things.

I anticipated a steep learning curve to get the configuration right, but I wanted to check in here first in case there were any potential issues at the very start with the way Ubuntu needed to be set up.

Always open for suggestions,

cheers

Max

---

### Post by sandyd on 2012-02-01
> **MaxVK said:**
> Thanks guys:


Right now I'm assuming that field workers will navigate to the correct page as normal, then log in and view their diary entries, and...


The users/admins in the HQ will open the web page as localhost so that diaries can be updated, client details logged etc, etc.

As long as both field workers and HQ workers can log in there should be no problems. I just don't want a system that slow to use because it is bogged down with security software etc - maybe I'm remembering back to the bad old days of windows.


I touched on this above - the plan is to have a domain that will display the company website, and alongside it, possibly on a different domain or perhaps access via just an IP address, the database app that every one will want to use.

For the most part the only users will be in the HQ, booking clients, logging inventory, updating workers diaries etc, etc, but at some point field workers will want to check their diary entries.

I don't see there being huge amounts of traffic to the website, and the vast majority of access to the database app will be at HQ - there are no more than five people there all the time anyway, and they wont all be using it at the same time.

I'm open to suggestions about connections etc, and any 'right' ways of doing things.

I anticipated a steep learning curve to get the configuration right, but I wanted to check in here first in case there were any potential issues at the very start with the way Ubuntu needed to be set up.

Always open for suggestions,

cheers

MaxIn this case, if your not worried about intrusions, you should be fine.

Otherwise, look up snort + ossec.

---

### Post by MaxVK on 2012-02-02
> look up snort + ossec
Thanks for the links - Iv not seen them before.

---

