---
title: "Lamp-server problem"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by dep0 on 2011-11-29
Hi, i have just installed lamp-server on my pc but i am not able to make any changes to the directory /var/www where i am supposed to put my files.
Please help!

---

### Post by dave0109 on 2011-11-30
You have a few options.

First, you can change the permissions of /var/www in order that you can add files in there...
```

cd /var/www
sudo chmod o+rwx .

```

This isn't a great idea, but I mention it for completeness.  It will allow anyone/thing to write files to that directory, leaving your web files vulnerable.

Second, you can change the owner of /var/www...
```

cd /var/www
sudo chown dep0:dep0 .

```

This changes the ownership of the directory to 'dep0' and the group to 'dep0'.  If that is not your username, then you need to change the command above.  The advantage is that you don't need to configure anything else.  The disadvantage is that because your user is doing nearly everything else on the computer, the area is potentially at risk from inadvertant change.  Another issue is that you must ensure that all files are readable by the user or group www-data, so that Apache can read and serve the files.

Thirdly, you can extend the config of Apache itself.
```

cd /etc/apache2/sites-available
sudo gedit default

```
If you don't have gedit, you can obviously use thunar, emacs, vi, notepad, whatever you have.

Here you can either add an alias that can be used insead.  You can add a virtual site, you can change the main root to reside in your home directory, the options are vast.

E.g. replace the 2 instances of /var/www to be /home/dep0/www

Or add the following, inside the VirtualHost tag:
```

    Alias /dep0/ "/home/dep0/"
    <Directory "/home/dep0/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
	Order allow,deny
	allow from all
    </Directory>

```

What I do is create a virtual server per domain that I look after.  This requires a bit more tinkering as you need to set up a hostname alias as well as creating a new virtual host settings for Apache.  If you're interested in going that route, I can tell you how I did it.

---

### Post by dep0 on 2011-11-30
Thank you very much for your time.
I think i'll try to extend the config of Apache.
The only thing i have to do is run this command on the terminal right?


```
cd /etc/apache2/sites-available
sudo gedit default
```

I don't need to add an alias, create a virtual server per domain etc, do i?

---

### Post by dave0109 on 2011-11-30
Correct, run those 2 commands and then alter the configuration as per your requirements.  There's much more detailed information about the config file on the Apache Server website if you want additional reading.

---

### Post by dep0 on 2011-12-01
Could you recomend me some sites where i can read about apache config?
I'm a little bit confused cause it's the first time i deal with this kind of stuff.

---

### Post by mcduck on 2011-12-01
> **dep0 said:**
> Could you recomend me some sites where i can read about apache config?
I'm a little bit confused cause it's the first time i deal with this kind of stuff.

Ubuntu's own server guide has very good instructions for basic Apache configuration: [https://help.ubuntu.com/11.10/serverguide/C/httpd.html]("https://help.ubuntu.com/11.10/serverguide/C/httpd.html")

---

### Post by Lars Noodén on 2011-12-01
If you are the only person using that machine, then the second option mentioned by dave0109 above would be suitable.  That is by far the simplest.

If you choose the third option above instead, there is some documentation on configuring virtual hosts at the Apache project's web site:

[http://httpd.apache.org/docs/2.3/vhosts/](http://httpd.apache.org/docs/2.3/vhosts/)
[http://httpd.apache.org/docs/trunk/](http://httpd.apache.org/docs/trunk/)

---

### Post by dep0 on 2011-12-01
Well i've done the second one and it works just fine. 
Thank you all.

---

