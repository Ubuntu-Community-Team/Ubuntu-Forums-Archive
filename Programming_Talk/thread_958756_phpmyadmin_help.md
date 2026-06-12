---
title: "phpmyadmin help"
date: 2008-10-25
forum: Programming Talk
---

### Post by gingerj on 2008-10-25
Hi All,

I have installed phpmyadmin, and it has installed in /etc/phpmyadmin , the installation guide I used said once it has installed you can test it by doing [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) but that produces a 404. I have nothing in my localhost directory, so I was wondering how on Earth do I get this thing to work, I know it is installed on my machine I just cannot seem to get it to interact with anything. 

Any help would be greatly appreciated.

---

### Post by drubin on 2008-10-25
> **gingerj said:**
> Hi All,

I have installed phpmyadmin, and it has installed in /etc/phpmyadmin , the installation guide I used said once it has installed you can test it by doing [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) but that produces a 404. I have nothing in my localhost directory, so I was wondering how on Earth do I get this thing to work, I know it is installed on my machine I just cannot seem to get it to interact with anything. 

Any help would be greatly appreciated.

Try creating a symlinck to it in your  /var/www/ folder
```
ln -s /etc/phpmyadmin /var/www/
```

You might need sudo rights to do this depending on your systems set up.

---

### Post by reality1011 on 2008-10-25
the reason why you are getting a 404 error is because /etc/ does not contain the pages that apache hosts... by default the pages are located in /var/www 

If you follow what drubin said it should be resolved.

---

### Post by drubin on 2008-10-25
> **reality1011 said:**
> the reason why you are getting a 404 error is because /etc/ does not contain the pages that apache hosts... by default the pages are located in /var/www 

If you follow what drubin said it should be resolved.

I probably should have included those details :) Guess I just forgot and just posted the solution.

/me wonders why phpmyadmin is in the repos's and it does not create a symlink.... or at least ask the user were the webroot is located.

---

### Post by gingerj on 2008-10-27
hi sorry to be such a drain, but this hasn't worked :(

I used the following cmd: sudo ln -s /etc/phpmyadmin /var/www/

I didn't get a confirmation message or anything, but it says the link has been created if I try to run the same command.

when i try [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it still doesn't work should i restart apache2 or have I missed something?

---

### Post by drubin on 2008-10-27
> **gingerj said:**
> hi sorry to be such a drain, but this hasn't worked :(

I used the following cmd: sudo ln -s /etc/phpmyadmin /var/www/

I didn't get a confirmation message or anything, but it says the link has been created if I try to run the same command.

when i try [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it still doesn't work should i restart apache2 or have I missed something?

Just to confirm you can hit  [http://localhost](http://localhost) in a browser?

Sorry to be a pain. But please try download phpmyadmin and unzip it to that folder /var/www/. [http://www.phpmyadmin.net/home_page/downloads.php](http://www.phpmyadmin.net/home_page/downloads.php) it requires a lot less hastle to install it this way then via apt-get.

---

### Post by reality1011 on 2008-10-27
> **drubin said:**
> Just to confirm you can hit  [http://localhost](http://localhost) in a browser?

Sorry to be a pain. But please try download phpmyadmin and unzip it to that folder /var/www/. [http://www.phpmyadmin.net/home_page/downloads.php](http://www.phpmyadmin.net/home_page/downloads.php) it requires a lot less hastle to install it this way then via apt-get.


I agree.  You should install it in the correct directory the first time.

---

### Post by unutbu on 2008-10-27
If you installed phpmyadmin from the official repo, 
then:

Add

```
Include /etc/phpmyadmin/apache.conf

```
to the end of  /etc/apache2/apache2.conf

Then restart apache2:
```

sudo /etc/init.d/apache2 restart

```

You might receive some errors like this:
```

[Wed Oct 08 09:21:13 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

[Wed Oct 08 09:21:23 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
   ...done.
```

Despite the errors (which unfortunately I don't really understand) your phpmyadmin should now work when you point your browser to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

This information comes from [http://www.blog.highub.com/linux/install-and-configure-phpmyadmin-on-ubuntu-lamp/](http://www.blog.highub.com/linux/install-and-configure-phpmyadmin-on-ubuntu-lamp/)

---

### Post by drubin on 2008-10-27
> **unutbu said:**
> If you installed phpmyadmin from the official repo, 
then:

Add

```
Include /etc/phpmyadmin/apache.conf

```
to the end of  /etc/apache2/apache2.conf

Then restart apache2:
```

sudo /etc/init.d/apache2 restart

```

You might receive some errors like this:
```

[Wed Oct 08 09:21:13 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

[Wed Oct 08 09:21:23 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
   ...done.
```

Despite the errors (which unfortunately I don't really understand) your phpmyadmin should now work when you point your browser to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

This information comes from [http://www.blog.highub.com/linux/install-and-configure-phpmyadmin-on-ubuntu-lamp/](http://www.blog.highub.com/linux/install-and-configure-phpmyadmin-on-ubuntu-lamp/)

it bassically tells apache to "port" /phpMyAdmin/ to the installed location. but this is just a load of ....<rant_off/>

I am going to report the fact that this application is even in the official repo's as a bug. This is madness! apt-get is supposed to do all of this configuration and set ups. (I would **NOT** want apt-get modifying my apache2.conf file).

Any way I still recommend just downloading the "source" php is not even compiled so there cant really be issues. 

Ps Good luck. This method of installation has even confused the daylights out of me. :)

---

### Post by s.fox on 2008-10-28
@ orignal poster

Hi,  I had 404 problem with phpmyadmin a while ago that I was able to fix.  If memory serves I had to use [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)

I believe the capital M and A were important.  Hope you get it going.

-Ash R

---

### Post by drubin on 2008-10-28
> **gingerj said:**
> Hi All,

I have installed phpmyadmin, and it has installed in /etc/phpmyadmin , the installation guide I used said once it has installed you can test it by doing [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) but that produces a 404. I have nothing in my localhost directory, so I was wondering how on Earth do I get this thing to work, I know it is installed on my machine I just cannot seem to get it to interact with anything. 

Any help would be greatly appreciated.

> **Ash R said:**
> @ orignal poster

Hi,  I had 404 problem with phpmyadmin a while ago that I was able to fix.  If memory serves I had to use [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)
I believe the capital M and A were important.  Hope you get it going.
-Ash R

The reason for this is Linux is a Case Sensitive OS so phpmyadmin is not the same as phpMyAdmin.  From your original post you stated it installed to > /etc/phpmyadmin This might be the reason that none of the the other solutions worked.

---

### Post by bapoumba on 2008-10-28
I have moved one post to this pre-existing thread: [http://ubuntuforums.org/showthread.php?t=959035](http://ubuntuforums.org/showthread.php?t=959035)

and removed two not needed any longer.

---

### Post by gingerj on 2008-11-01
Many thanks unutbu I can now now view the phpmyadmin page.

Sorry to be a pain though, I have one small problem, it is asking me for a login and my root login doesn't seem to be sufficient and as far as I am aware I haven't been asked to save a password any where.

Where on Earth do I register the product or get a login?

---

### Post by whoelse on 2008-11-01
> **gingerj said:**
> Many thanks unutbu I can now now view the phpmyadmin page.

Sorry to be a pain though, I have one small problem, it is asking me for a login and my root login doesn't seem to be sufficient and as far as I am aware I haven't been asked to save a password any where.

Where on Earth do I register the product or get a login?
Try root as username and no pwd, at least it was that way a long time ago.

---

### Post by gingerj on 2008-11-01
Loving the swift response whoelse, logging in without supplying the password worked a treat.

Many thanks to all who have helped me out in setting up the phpmyadmin program! 

Have a lovely weekend.

---

