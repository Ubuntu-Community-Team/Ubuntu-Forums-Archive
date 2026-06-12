---
title: "Setting up a home server; can't access phpmyadmin or copy files to /var/www"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by JesseJones on 2014-05-12
Hi Everyone,

I'm pretty new to the whole linux thing and I suddenly find myself in need of a server. Unfortunatly I didn't realize my hosting plan was expiring and I just made some new buisness cards that I started to hand out last week so I now need to host my own site.

I know it's not ideal, slow upload speeds, time etc but I really don't have the extra cash right now to buy hosting so this is what I have to work with. I've actually done this before following a guide I can no longer find and I didn't have any trouble until it came to making my site visible to the outside world. I'll cross that bridge when I get there.

I installed Ubuntu Server Edition 14,04 on an old PC and selected OpenSSH and LAMP during the install.

After I was done the first thing I tried to do was access my server with Putty: Success

Then I typed in my servers IP and made it to the Apache2 Ubuntu default "it works" page.

(Side note: typing localhost instead of my servers IP I get a problem loading page error. Is local host only used when AMP are installed on the machine you are typing localhost from?)

I knew I would need to create a database for my Wordpress site so I installed phpmyadmin. After installation I went to myip/phpmyadmin but I get a 404 error. I tried my best google-fu and tried the command I found on this site: [http://tech2view.com/not-able-to-access-phpmyadmin-in-ubuntu-404-not-found-error/](http://tech2view.com/not-able-to-access-phpmyadmin-in-ubuntu-404-not-found-error/)

sudo ln -s /usr/share/phpmyadmin /var/www

Still can't access phpmyadmin

At this point I thought maybe I could just get away with using the database that myphpadmin had created during the install. Really I just wanted to move on the the next step while I puzzled out the php problem. So I tried to copy my wordpress installation folder to var/www/html (the location of the Apache2 index.html file. And I recieved an error for each file in the folder I was trying to copy.

Error:	/var/www/html/forrester/wordpress/wp-includes/js/tinymce/skins/wordpress/images/embedded.png: open for write: no such file or directory
Error:	File transfer failed

I fear I've messed something up, the last time I set this up it was much easier but I was using wAMP.

Sorry for the complete newbiness, I'm learning = )

---

### Post by TheFu on 2014-05-12
Start by learning about multi-user systems and file permissions. This knowledge will pay off the the rest of your life. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Might also review the OWASP security checklist before putting any server on the internet. Servers like this get owned pretty quickly these days. I helped someone a few months ago who's server had been owned for months, almost a year before he noticed.

---

### Post by JesseJones on 2014-05-12
Thanks, I'll start doing my homework. I knew that server security would be an issue however the site is only for my personal side buisness and the majority of my traffic would be through the dispersal of my buisness cards so I thought I might be safe for a short while while I figure things out.

---

### Post by TheFu on 2014-05-12
Sadly, no.  Anyone with a reasonable broadband connection can scan the entire internet for new servers every 24 hrs.  The days of assuming people are nice are over.

[http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/) will give you an idea of what we are up against.

---

