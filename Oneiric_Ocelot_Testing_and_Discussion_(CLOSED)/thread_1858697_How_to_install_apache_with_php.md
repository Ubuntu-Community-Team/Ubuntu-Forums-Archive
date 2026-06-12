---
title: "How to install apache with php?"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cpbl on 2011-10-12
(Problem is that the server is (still) not properly restarted after installing php. So you need to manually restart it to avoid serving PHP source code to the world! There's an old unfixed bug in launchpad about this...)

---

### Post by alphacrucis2 on 2011-10-12
> **cpbl said:**
> I've just installed what I thought should be a php-ready web server on the latest update of 11.10 , by doing
apt-get install libapache2-mod-php5
and saying yes (to also install php5, apache2, etc).

After doing that (and optionally restarting apache2), the web server sends out php code, uninterpreted. For me this is a big security hazard. Have I not done a somewhat intuitive thing? If this is a regression, it would constitute a security problem.

What have you got under /etc/apache2/mods-enabled?


Edit: Sorry. I replied before seeing your edit

---

### Post by cpbl on 2011-10-12
> **alphacrucis2 said:**
> What have you got under /etc/apache2/mods-enabled?


Edit: Sorry. I replied before seeing your edit


Well, sorry for erasing so much text in a post. Probably doesn't make sense. I'm actually still completely befuddled. Part of the problem was seeminly that Chrome needs its cache cleared more than firefox (where reload does something useful).

But here's where I'm stuck now:

If I put

DirectoryIndex  index.php index.html  

in sites-available/default  and restart the server, then it serves my index.php unprocessed.
But it does alright with other php files.

If I put

DirectoryIndex   index.html index.php  

then it does the right thing, reading index.php and processing it...


The answer to your question is:
```

alias.conf@            authz_user.load@  dir.load@          php5.load@
alias.load@            autoindex.conf@   env.load@          reqtimeout.conf@
auth_basic.load@       autoindex.load@   mime.conf@         reqtimeout.load@
authn_file.load@       cgi.load@         mime.load@         setenvif.conf@
authz_default.load@    deflate.conf@     negotiation.conf@  setenvif.load@
authz_groupfile.load@  deflate.load@     negotiation.load@  status.conf@
authz_host.load@       dir.conf@         php5.conf@         status.load@


```

---

