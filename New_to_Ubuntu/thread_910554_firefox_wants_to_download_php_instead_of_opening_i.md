---
title: "firefox wants to download php instead of opening it"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-09-04
I'm just installed a lamp server and set up wordpress on it.

When I try to open it the index.php file wordpess has, firefox wants to download it instead of opening it.

What's wrong?

---

### Post by billgoldberg on 2008-09-04
When I open it in opera, it says:

> <?php
// Silence is golden.
?>

---

### Post by OffAxis on 2008-09-04
php isn't installed correctly.

you could try installing it as a module

```
sudo a2enmod
php5
```

and in case you need it, 

```
sudo a2dismod
php5
```

would disable it.

---

### Post by OffAxis on 2008-09-04
was that the contents of your php testfile?

---

### Post by billgoldberg on 2008-09-04
The standard wordpress index.php.

Opera does open it and says 

<?php
// Silence is golden.
?> 

--

OffAxis: The module php5 is already installed.

---

### Post by OffAxis on 2008-09-04
I haven't used wordpress (on linux) before, but I would imagine there should be a lot more in the default index.php than that...

Could you create a file called phpinfo.php and put this is in it:

<?php
phpinfo()
?>

It'll check to see if your mysql functionality is set up correctly as well.

---

### Post by billgoldberg on 2008-09-04
When opening that file in opera, it reads

<?php
phpinfo()
?>

I'm guessing it's something with php not working properly.

But have no idea what to do.

(noob at this)

---

### Post by Nepherte on 2008-09-04
phpinfo() just gives information of the server as to what version is running, what values of a couple of variables are, what functions are enabled. It is commonly used to as default test file for php to see if it's working. So it's certainly not index.php file of wordpress. That doesn't mean you shouldn't be able to view the file in a web browser. You say php is installed, but is it enabled as well (cfr. post #)?

---

### Post by billgoldberg on 2008-09-04
> **Nepherte said:**
> phpinfo() just gives information of the server as to what version is running, what values of a couple of variables are, what functions are enabled. It is commonly used to as default test file for php to see if it's working. So it's certainly not index.php file of wordpress. That doesn't mean you shouldn't be able to view the file in a web browser. You say php is installed, but is it enabled as well (cfr. post #)?

How would I check it if is enabled?

Could it be related to me setting up the database up wrong in phpmyadmin?

---

### Post by OffAxis on 2008-09-04
so phpmyadmin works correctly?

---

### Post by billgoldberg on 2008-09-04
> **OffAxis said:**
> so phpmyadmin works correctly?

Yes, also when I run a php testfile from /var/www/testphp.php it gets displayed good.

But when I put that same file in /var/www/wordpress/

It doesn't work.

When I put all the content from the wordpress folder in /var/www it doesn't work anymore also.

---

### Post by OffAxis on 2008-09-04
Is the wordpress folder a link to the /usr/share/wordpress folder or is it a folder in your /var/www/ folder in its own right?

Either way, the php in that folder isn't being processed how it should. It's either an ownership problem for the file/folder or the apache directives are stopping it from being processed.
It escapes me at the moment how to correct the directives, hopefully someone who remembers will jump in.

How do you have the permissions for that folder set up in apache? There's a 'link' option that may be giving you trouble...

---

### Post by tuxulin on 2008-09-04
clear your browser cache

Tux

---

### Post by billgoldberg on 2008-09-04
> **OffAxis said:**
> Is the wordpress folder a link to the /usr/share/wordpress folder or is it a folder in your /var/www/ folder in its own right?

Either way, the php in that folder isn't being processed how it should. It's either an ownership problem for the file/folder or the apache directives are stopping it from being processed.
It escapes me at the moment how to correct the directives, hopefully someone who remembers will jump in.

How do you have the permissions for that folder set up in apache? There's a 'link' option that may be giving you trouble...

Wordpress is just in the /var/www folder, not anywhere else.

I have no idea on the rest, I just followed a guide.

---

### Post by ianhaycox on 2008-09-04
Try looking in the apache log files it might provide a clue.

---

### Post by billgoldberg on 2008-09-04
> **ianhaycox said:**
> Try looking in the apache log files it might provide a clue.

The apache2 error log:

> Thu Sep 04 22:14:46 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Thu Sep 04 22:15:14 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Sep 04 22:15:17 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Sep 04 22:15:55 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Sep 04 22:16:00 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Thu Sep 04 22:16:02 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Sep 04 22:16:02 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Thu Sep 04 22:16:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Sep 04 22:17:40 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Sep 04 22:19:32 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Sep 04 22:20:48 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Sep 04 22:22:15 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Sep 04 22:27:08 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Sep 04 22:27:08 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Sep 04 22:28:39 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Sep 04 22:30:23 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Sep 04 22:31:51 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Sep 04 22:31:54 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Sep 04 22:53:37 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Sep 04 22:54:54 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Sep 04 23:16:22 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Sep 04 23:26:19 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: [http://localhost/testphp.php](http://localhost/testphp.php)

---

### Post by OffAxis on 2008-09-04
try adding this line to (or creating if it doesn't exist) a file named **.htaccess** in the **/var/www/wordpress** folder

```
AddHandler application/x-httpd-php5 .html .htm
```

you'll need to restart the server after.

```
sudo /etc/init.d/apache2 restart
```

---

### Post by billgoldberg on 2008-09-04
> **OffAxis said:**
> try adding this line to (or creating if it doesn't exist) a file named **.htaccess** in the **/var/www/wordpress** folder

```
AddHandler application/x-httpd-php5 .html .htm
```

you'll need to restart the server after.

```
sudo /etc/init.d/apache2 restart
```

Still the same

---

### Post by OffAxis on 2008-09-04
did you clear the browser's cache?

If you have a tab open in the background to the page it'll still carry the error over. you'll need to shut down every tab to the site you're troubleshooting and then clear the cache.

---

### Post by billgoldberg on 2008-09-04
> **OffAxis said:**
> did you clear the browser's cache?

Yes

---

### Post by ianhaycox on 2008-09-04
Have you got the links php5.conf and php5.load in /etc/apache2/mods-enabled/

e.g.

```
$ ls -l /etc/apache2/mods-enabled/php*
lrwxrwxrwx 1 root root 27 2008-08-30 12:02 /etc/apache2/mods-enabled/php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root 27 2008-08-30 12:02 /etc/apache2/mods-enabled/php5.load -> ../mods-available/php5.load
```

and I assume that everything is owned by www-data in /var/www

---

### Post by billgoldberg on 2008-09-04
> **ianhaycox said:**
> Have you got the links php5.conf and php5.load in /etc/apache2/mods-enabled/

e.g.

```
$ ls -l /etc/apache2/mods-enabled/php*
lrwxrwxrwx 1 root root 27 2008-08-30 12:02 /etc/apache2/mods-enabled/php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root 27 2008-08-30 12:02 /etc/apache2/mods-enabled/php5.load -> ../mods-available/php5.load
```

and I assume that everything is owned by www-data in /var/www

This is what I get.

lrwxrwxrwx 1 root root 27 2008-09-04 22:16 /etc/apache2/mods-enabled/php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root 27 2008-09-04 22:16 /etc/apache2/mods-enabled/php5.load -> ../mods-available/php5.load

---

### Post by Tux.Ice on 2008-09-04
get apache2

```
sudo apt-get install apache2
```

then put your wordpress files in /var/www

(make sure /var/www permissions are 777) then access word press by going to 127.0.0.1 in a browser window

---

### Post by Nepherte on 2008-09-05
There's absolutely no need for 777 permissions. The default permissions (755 for a map, 644 for a file) are more than ok. It's very strange it doesn't work for you, I know it did over here :s I didn't install any lamp packages though, just installed everything separately. What guide did you use?

---

### Post by OffAxis on 2008-09-15
Don't know if you found any resolution to this, but I found this one in the archives with a recent post (with a fix) from bodhi.zazen
[http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

---

### Post by vancouverite on 2008-09-15
I get this same thing when trying to open [www.freefem.org/ffw/index.php](www.freefem.org/ffw/index.php)

I couldn't find the firefox log file, but if I run FF3 from terminal I get the following when I try to visit the page:

[INDENT]debugger.onModuleDeactivate Attempt to deactive context that is not active [http://www.freefem.org/ffw/](http://www.freefem.org/ffw/)
GCJ PLUGIN: thread 0x805f168: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f168: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f168: NP_GetValue
GCJ PLUGIN: thread 0x805f168: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f168: NP_GetValue return
GCJ PLUGIN: thread 0x805f168: NP_GetValue
GCJ PLUGIN: thread 0x805f168: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f168: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)[/INDENT]

I have php5 installed, but since php should be processed server side I don't think this should matter.

Cheers,
Van

---

### Post by Dougie187 on 2008-09-15
Yeah it should be an issue on the server. The server doesn't appear to have PHP5 installed correctly for use with their web server.

I had this issue two days ago when I was setting up eyeOS, and the post mentioned two posts up fixed my issue.

---

### Post by Brerlapn on 2008-09-17
I am having the same problem sporadically with certain web pages where I will hit a button on a page that is supposed to trigger an action, the page spins as if it is loading, and minutes later I either receive a:

1) Page Load Error: "The connection to the server was reset while the page was loading.  The network link was interrupted while negotiating a connection. Please try again."

OR

2) The box comes up as if I had clicked a link for a file and says "You have selected Compose.PHP.  Would you like to open or download as a file."



Perhaps the problem is in Firefox/Ubuntu/both, and not in the OP's PHP installation, since all of the web pages from which I am receiving this error are running server-side (obviously).

One example of this is the "settings" button on Facebook, which just spins and serves up a page load error.  My other example would be my webmail or my blog software (Wordpress), which bring up the "You have selected the Compose.php file.  Would you like to: open with... or Save as..." dialog box.

Neither error occurs when I boot into Windows to perform those tasks.  Opera doesn't play nicely with any of the Facebook scripts, so I can't tell if I'm getting the same failure there or not, but Konqueror is able to pull up the Facebook Settings pages and navigate around them.

Also, I had to reboot into Windows to post this, because the "Submit Reply" button below does the no. 2 error above by opening the "you have chosen to open NewReply.php .. . What should Firefox do with this file?" dialog box.  I tried posting this using Konqueror, but it just cycled the page when I hit Submit Reply without ever returning a result.

---

