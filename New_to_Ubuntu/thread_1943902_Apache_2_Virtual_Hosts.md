---
title: "Apache 2 Virtual Hosts"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by bediinderjit on 2012-03-20
Hi,
I am using Ubuntu 10.04 64 Bit and I have Installed:
Apache
MySQL
PHP

I followed the standard document :


First install tasksel... 

sudo apt-get install tasksel



... and then the LAMP stack:
sudo tasksel install lamp-server

Now when I am trying to Change the Virtual Hosts:
gksudo gedit /etc/apache2/sites-available/mysite

I get error :

(gedit:18259): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:18259): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KXD7AW': No such file or directory

(gedit:18259): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:18259): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.4TB9AW': No such file or directory

(gedit:18259): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by kimberlite on 2012-03-20
I would not care with those **warnings**. If you would like to get rid of them, check out this [topic]("http://ubuntuforums.org/archive/index.php/t-1864688.html").

---

### Post by bediinderjit on 2012-03-20
Even if I don't care of those warnings, I am still not able to get the **[http://localhost/](http://localhost/) **working.

I get this error : **Forbidden**

 You don't have permission to access / on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80


[FONT=Arial][SIZE=2]**I have tried chmod 777 -R /path**[/SIZE]
[/FONT]

---

### Post by Lars Noodén on 2012-03-20
(If you've set the permission to 777, then they are wrong and need to be made safe again. ) 

Your web data should be in /var/www if it is still in the default location.  Looking at your log files will help give details about what is wrong.  You can open up another terminal window and then run the following:

```

tail -f /var/log/apache2/error.log

```

Then with that window open, try accessing the web page and getting the error.  The log message should contain considerably more detail.

---

### Post by bediinderjit on 2012-03-20
I have changed my web data to:

/home/inderjit/Desktop/PHPProject/public_html

I have changed my DocumentRoot:

DocumentRoot /home/inderjit/Desktop/PHPProject/public_html

/Directory:
<Directory /home/inderjit/Desktop/PHPProject/public_html/>

sudo a2dissite default && sudo a2ensite mysite

sudo /etc/init.d/apache2 restart

When I run tail -f /var/log/apache2/error.logThe Error Log shows:

[Wed Mar 21 09:12:02 2012] [error] [client 127.0.0.1] (13)Permission denied: access to / denied

---

### Post by bediinderjit on 2012-03-27
How Do I get a solution to my problem, I have been waiting for someone to response.

---

### Post by Lars Noodén on 2012-03-27
Have you verified that Apache can actually read your directories?

```

chmod o+rx /home/inderjit/Desktop/
chmod o+rx /home/inderjit/Desktop/PHPProject/
chmod o+rx /home/inderjit/Desktop/PHPProject/public_html/

```

---

### Post by d4m1r on 2012-03-27
Are you logged in as root? If not, try sudo command_here

---

### Post by bediinderjit on 2012-03-28
Still same error:
**Forbidden**

 You don't have permission to access /index.php on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80


I am logged in as root and have run the below code.
 
    Code:

     chmod o+rx /home/inderjit/Desktop/ 
chmod o+rx /home/inderjit/Desktop/PHPProject/ 
chmod o+rx /home/inderjit/Desktop/PHPProject/public_html/

---

