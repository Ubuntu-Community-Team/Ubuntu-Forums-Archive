---
title: "PHP not working properly"
date: 2009-12-17
forum: Programming Talk
---

### Post by KevinM1 on 2009-12-17
Hi all, I have a linux Mint machine, but since that's built on top of Ubuntu, and there's more activity on this forum, I figure I'll ask my question here.

I've installed both apache2 and PHP.  PHP works from the cli, but won't process any PHP files in /var/www if I try clicking on them or feeding them to the browser.  Clicking opens gedit, and the browser wants me to download the file.  HTML in this folder works normally, however - the little test page that apache installs works fine.  So, I know that apache is running, and the PHP module is loaded, as, again, my test file works with the command line interface.

I've removed and installed apache a few different times.  I've also tried several versions of PHP.  The same problem crops up every time.

It seems as though apache doesn't know to handle PHP files in that directory properly.  Is there any setting or switch I should be aware of?

My system is 64-bit, if that makes a difference.

Thanks.

---

### Post by Hellkeepa on 2009-12-17
HELLo!

Sounds like you haven't installed the PHP module for apache. What you need to do, is to install "libapache2-mod-php5" using the package manager.

Happy codin'!

---

### Post by KevinM1 on 2009-12-17
> **Hellkeepa said:**
> HELLo!

Sounds like you haven't installed the PHP module for apache. What you need to do, is to install "libapache2-mod-php5" using the package manager.

Happy codin'!

Nope it's there.  Checked it earlier.  Besides, if it wasn't, wouldn't the PHP command line interface not work?

---

### Post by Hellkeepa on 2009-12-17
HELLo!

No, the Apache module and the CLI executable are two different packages.

Strange that it doesn't parse the PHP scripts even with that package installed, as it should have set up Apache's config file to do just this. Make sure that you can find a symlink to "php.conf" and "php.load" in "/etc/apache/mods-enabled", and try to restart apache manually just to be sure. Latter is done with "sudo apache2ctl restart"

Happy syncin'!

---

### Post by KevinM1 on 2009-12-17
> **Hellkeepa said:**
> HELLo!

No, the Apache module and the CLI executable are two different packages.

Strange that it doesn't parse the PHP scripts even with that package installed, as it should have set up Apache's config file to do just this. Make sure that you can find a symlink to "php.conf" and "php.load" in "/etc/apache/mods-enabled", and try to restart apache manually just to be sure. Latter is done with "sudo apache2ctl restart"

Happy syncin'!

I'm a newbie, so more detailed instructions are required.

How would I check a symlink?

---

### Post by j7%&lt;RmUg on 2009-12-17
If you are sure that libapache2-mod-php5 is installed the run the following command:

sudo /etc/init.d/apache2 restart

then try running your php script through your web browser again.

---

### Post by KevinM1 on 2009-12-17
> **nisshh said:**
> If you are sure that libapache2-mod-php5 is installed the run the following command:

sudo /etc/init.d/apache2 restart

then try running your php script through your web browser again.

Didn't work

---

### Post by j7%&lt;RmUg on 2009-12-17
Ok, can you explain to me exactly what you did just then, and what you mean by it didnt work.

---

### Post by KevinM1 on 2009-12-17
> **nisshh said:**
> Ok, can you explain to me exactly what you did just then, and what you mean by it didnt work.

I have:

Downloaded and installed apache2 from the repository.  I've done several fresh installs after completely removing it first.

Downloaded and installed several versions of PHP 5, both from the repository and from PHP.net.  Again, these are fresh installs.  Current  version installed is 5.2.10 from the repository.

I have checked for the existence of php5.conf and php5.load files in /etc/apache2/mods-available.  They are both there.

I have ensured that the php5 module is loaded by entering sudo a2enmod php5.  It is loaded.

I've restarted the server.

'Not working' means that my php file, which is located in /var/www is not being correctly processed by apache.  Again, like I said in my OP, double-clicking on it opens gedit for me to edit the contents of the file.  Going to Firefox and using File->Open File->myFile.php prompts me to download it.

When I restart the server, I get:

```
kevin@kevin-laptop ~ $ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
```

Apache error logs show:

```
[Thu Dec 17 08:51:46 2009] [notice] Apache/2.2.12 (Ubuntu) configured -- resuming normal operations
[Thu Dec 17 08:52:14 2009] [notice] caught SIGTERM, shutting down
[Thu Dec 17 08:52:19 2009] [notice] Apache/2.2.12 (Ubuntu) configured -- resuming normal operations
[Thu Dec 17 08:52:20 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 17 08:52:20 2009] [notice] Apache/2.2.12 (Ubuntu) configured -- resuming normal operations
[Thu Dec 17 08:53:06 2009] [notice] caught SIGTERM, shutting down
[Thu Dec 17 08:53:07 2009] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 17 08:53:45 2009] [notice] caught SIGTERM, shutting down
[Thu Dec 17 08:53:46 2009] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 17 10:47:35 2009] [notice] caught SIGTERM, shutting down
[Thu Dec 17 10:47:36 2009] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.3 with Suhosin-Patch configured -- resuming normal operations
```

Not sure what else to try.

---

### Post by Hellkeepa on 2009-12-17
HELLo!

I found the issue, right here:
> File->Open File->myFile.php
This completely circumvents Apache, and thus no parsing happens. If you want the PHP script to be executed, then you need to open it like any other web page and not like a local file.
[http://localhost/myFile.php](http://localhost/myFile.php) <- Write that in the address bar, and you'll see that things are indeed working.

Happy codin'!

---

### Post by KevinM1 on 2009-12-17
...man, I'm an idiot.  Thanks! :)

---

### Post by Hellkeepa on 2009-12-17
HELLo!

Hehe, you're welcome.

Happy syncin'!

---

### Post by Barriehie on 2009-12-17
Not trying to hijack your thread Kevin but I know when I was setting up my apache that 127.0.1.1 thing was really bugging me!

> **KevinM1 said:**
> 
...
```
kevin@kevin-laptop ~ $ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
```
...


If you decide to go with something like [www.dyndns.com](www.dyndns.com) to redirect url requests to your machine; i.e. your machine is web reachable, we can make that 127.0.1.1 thing go away with a qualified domain name.  Off the top of my head you could try 'ServerName localhost' in your apache2.conf.  

Barrie

---

