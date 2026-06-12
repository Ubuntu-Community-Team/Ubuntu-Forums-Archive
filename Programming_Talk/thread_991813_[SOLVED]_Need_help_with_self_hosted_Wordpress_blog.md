---
title: "[SOLVED] Need help with self hosted Wordpress blog"
date: 2008-11-24
forum: Programming Talk
---

### Post by black3ug on 2008-11-24
I'm trying to learn about self-hosting a site. So far, this is what i've done:

1. set up a LAMP server
2. made it visible to the net ([http://briananthony.serveblog.net/](http://briananthony.serveblog.net/)) using no-ip
3. installed Wordpress at /var/www/wordpress

My next problem is linking to my wordpress blog. On the main page of my site, put in a link to my blog but it does not work.

Can anybody help, please?

---

### Post by black3ug on 2008-11-24
Okay, i solved this myself. For those who are interested in the solution, here it is.


In my experience, there were two problems.

1. I could not access the subfolders
2. I had a problem with the Wordpress settings.

To solve problem 1, I created a "non-root" site. the /var/www/ directory is not really very easy to acces, i think. This link has all the goodies: [http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

To solve problem 2, I had to go to do the following:

1. go into the Wordpress dashboard
2. go to "Settings" then "General" tab
3. scroll to "Wordpress Address (URL)" field
4. change the link (usually [http://localhost/wordpress](http://localhost/wordpress)) to your web address.

so if you're URL is "http://myname.serveblog.net/", then you'd change the entry to "http://myname.serveblog.net/wordpress"

5. do the same with the "Blog Address (URL)" field
6. save and you're done

Also, if you want access to your Wordpress blog from your LAMP server, change don't use "localhost" in your 'href' tag.

Hope this helps someone. Now I have to figure out how to secure a LAMP server/ :)

---

