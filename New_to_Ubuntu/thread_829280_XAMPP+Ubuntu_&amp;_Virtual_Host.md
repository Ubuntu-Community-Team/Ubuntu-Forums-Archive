---
title: "XAMPP+Ubuntu &amp; Virtual Host"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by php-zbatev on 2008-06-14
hi,

I have just installed Xampp in my Ubuntu (Hardy) and I wanted to make Virtual Hosts but my problem is that everytime I access my virtual host it brings me to xampp page, which goes like this:
if i enter [http://myvirtualhost](http://myvirtualhost)
the browser brings me to [http://myvirtualhost/xampp](http://myvirtualhost/xampp)

my etc/hosts has:
  127.0.0.1 myvirtualhost localhost

my /extra/httpdconf-vhosts.conf has:

<VirtualHost *:80>
    DocumentRoot /htdocs/myvirtualhostdocroot/
    ServerName myvirtualhost

</VirtualHost>


what else should I need to do, I hope there is a how-to guide also on this specific to XAMPP in Ubuntu which would include vistual hosting in the topic. Please help me out... Thank you

---

### Post by cariboo on 2008-06-14
Have you had a look at this?

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Jim

---

### Post by php-zbatev on 2008-06-15
yes I have... my installation was actually successful I also tried that section in that thread were it discuss the virtual host but I pretty much end up with the same situation.

---

