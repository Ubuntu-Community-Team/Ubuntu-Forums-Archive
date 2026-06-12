---
title: "Getting Apache, PHP, and whatever else set up for local development"
date: 2007-10-03
forum: Programming Talk
---

### Post by King_Critter on 2007-10-03
Right, so today I finally got around to starting to learn PHP. *cue cheering and clapping* I have a web host that supports PHP -- however, to cut down on the strain of having to upload a php file a gazillion times in the span of five minutes while following a tutorial, I decided to install it on my desktop. First, I googled for some tutorials on doing such a thing. Did I find any? Yes, I did. Did I find any that didn't soar completly over my head? Sadly, I did not. Then I took a look through Synaptic and saw the PHP5 and apache2 packages. So I'm like, whatever -- and installed them. I figured I'd now just be able to open a PHP file stored on my hard drive and it would "just work." No such luck, which leads me to assume that I need to do some more tinkering. Or something. Help, please?

---

### Post by Koybe on 2007-10-04
You need to open your php file trough your browser for your local server to understand the php coding.

Be sure you have these packages : apache2 libapache2-mod-php5

---

### Post by King_Critter on 2007-10-04
Well, yeah, of course I'm opening them in my browser...

And all those packages are installed, by the way.

---

### Post by mssever on 2007-10-04
Are you putting your files in /var/www/apache2-default? Also, for convinience, you might want to either make yourself owner of /var/www/apache2-default and symlink it somewhere you like, or change Apache's DocumentRoot to a more convenient location and restart Apache.

---

### Post by King_Critter on 2007-10-04
No, I wasn't. Unfortunatly, doing so doesn't help. :( But for future reference, how do you change the DocumentRoot?

---

### Post by King_Critter on 2007-10-04
M'kay... I really hate to nag, but this thread has ended up on the abyss known as the second page. Is there anyone here that can help me?

---

### Post by mssever on 2007-10-04
When you browse to [http://localhost/](http://localhost/), do you see the default Apache start page?
> **King_Critter said:**
> But for future reference, how do you change the DocumentRoot?
It's in /etc/apache2/sites-enabled/000-default. I think that I told you the wrong default document root, but if you look there, you'll see what it's set to.

Note: Any time you change Apache's configuration, restart apache: ```
sudo apache2ctl graceful
```

---

### Post by King_Critter on 2007-10-05
w00t! I didn't know about the [http://localhost/](http://localhost/) thing -- now it works! Thank you *so* much! :D

---

### Post by rawlyn on 2008-10-23
For what it's worth...

I use Apache, PHP and MySQL for local development too. I'm kind of new to it, but have found that by changing the line in /etc/apache2/ports.conf that reads

Listen 80

to

Listen localhost:80

it makes Apache listen to local requests only. Before doing this I found that I could point the browser on another machine to my IP address and Apache would happily dish out the HTML!

(I know it's a long time since this thread was active, but it's been something I've been struggling with this morning - I figure putting this information here might help others one day.)

---

### Post by drubin on 2008-10-23
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) This might also help.

I as a standard store my default files in 
/var/www/html 
I have a 
/var/www/vhosts for virtual hosting for bassed on site.

---

