---
title: "Transferring website to linux VPS"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Depaq on 2013-02-19
Hello. Complete linux noob here. I picked Ubuntu after doing some research.

So, I bought a VPS and after a few hours I managed to get Webmin installed on it - after trying out several different "Guides"..  

Anyway...

Now I'm needing to transfer my website over to it, and I'm clueless. I can't for the life of me find a guide that is useful. All the ones I can find and make sense want both hosting accounts to have cpanel - which I only have on one of them - the old shared hosting plan.

I am running a vbulletin website. So, I just need to know how to transfer the entire thing - users, posts, everything - to this new server. If anyone can point me in the right direction for this, that would be awesome.

Thanks.

---

### Post by Cheesemill on 2013-02-19
A quick Google for 'vbulletin migration' pulls up some likely looking results...

[http://www.hostucan.com/webmaster-tutorials/how-to-migrate-vbulletin-site](http://www.hostucan.com/webmaster-tutorials/how-to-migrate-vbulletin-site)

Basically it is the same process with any web app, you copy the database to the new machine and then copy over all the content. Once you have checked it's working then change  your DNS settings to point to the new site.

---

### Post by Depaq on 2013-02-19
Well, apparently the VPS was actually not ready for transferring. It didn't even have mysql or PHP on it.

I have now done the following commands

apt-get install mysql-server
apt-get install php5-mysql
apt-get install php5
apt-get install libapache2-mod-php5
apt-get install phpmyadmin

This, however, leaves me with PHP 5.3 and MySQL 5.1. MyWebmin is not finding updates, so where can I get the latest versions? I have tried many different google results, but all of them end up telling me some kind of error. Mostly saying the file cannot be found, or 404 not found.

Am I better off just letting my webhost get more money from me so they can do it for me? #-oIt seems I would have to switch to CentOS + Cpanel for them to do it.

---

