---
title: "how to ubuntu server"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by theRightNee on 2008-05-09
well i do not know if this is the best place to ask this...but the ubuntuforums are really my onestop source to answer my computer questions nowadays =]

i am thinking of turning my old pc into a server, and ,of course, using ubuntu server to do it

the problem is not setting up the server (i found a great howtoforge article), the problem is using it

question: how does one go about using a server to host websites? never done it before, and well...i feel very noob right now

---

### Post by tamoneya on 2008-05-09
websites are served by http.  The most common server for this is apache.  This should be installed by default in the server edition.  Then if you put the IP address of your server into the web browser of another computer it will display whatever file is located at /var/www/index.html or index.php.  This is the very simplified version of things but it gets you started.  You should probably also look into getting a domain name for your IP address so people can just type in a name instead of a set of numbers in their browser.

---

### Post by spiderbatdad on 2008-05-10
This is the link I use for setting up apache.[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) Also once you have your server running, for access from outside localhost, you will need to log into your router [http://www.phenoelit-us.org/dpl/dpl.html](http://www.phenoelit-us.org/dpl/dpl.html) from a browser and open port 80 to forward requests to the local ip of your server. Additionally, If you want to be able to navigate to your webpages by name, You will need to register the name with a DNS...like DYNDNS (free) or  you can purchase domains very reasonably (around 10.00 US. a year.)

---

### Post by Xiong Chiamiov on 2008-05-10
> **spiderbatdad said:**
> This is the link I use for setting up apache. Also once you have your server running, for access from outside localhost, you will need to log into your router from a browser and open port 80 to forward requests to the local ip of your server. Additionally, If you want to be able to navigate to your webpages by name, You will need to register the name with a DNS...like DYNDNS (free) or  you can purchase domains very reasonably (around 10.00 US. a year.)
The link seems to be, eh, missing. ;)

---

### Post by theRightNee on 2008-05-10
> **tamoneya said:**
> websites are served by http.  The most common server for this is apache.  This should be installed by default in the server edition.  Then if you put the IP address of your server into the web browser of another computer it will display whatever file is located at /var/www/index.html or index.php.  This is the very simplified version of things but it gets you started.  You should probably also look into getting a domain name for your IP address so people can just type in a name instead of a set of numbers in their browser.

thanks! now if i want to begin several websites on the same server, how would i do that?

---

### Post by tamoneya on 2008-05-10
you should take a look into virtual hosts:
[http://www.ubuntugeek.com/ubuntu-linux-apache2-virtual-hosts-syslog-server.html](http://www.ubuntugeek.com/ubuntu-linux-apache2-virtual-hosts-syslog-server.html)

---

### Post by theRightNee on 2008-05-10
great! now...if i wanted to create a personalized e-mail address (e.g. [email]theRightNee@theRightnee.com[/email] as opposed to [email]theRightNee@yahoo.com[/email]) how would i go about doing that?

---

### Post by DrPppr242 on 2008-05-10
e-mail would be a whole separate service from web mainly smtp, which in my opinion postfix is what your looking for.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by theRightNee on 2008-05-11
thanks!

---

### Post by theRightNee on 2008-05-16
hey, sorry to reopen this thread

but if i wanted to be able to remotely edit the website, would i have to access the server? i only need to access the /var/www/ folder, so i am wondering if there is an easier way to accomplish this task

---

