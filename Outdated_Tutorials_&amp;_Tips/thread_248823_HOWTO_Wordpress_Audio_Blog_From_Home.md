---
title: "HOWTO: Wordpress Audio Blog From Home"
date: 2006-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by peabody on 2006-09-01
I had the bright idea to run a Blog using WordPress from my home computer since it's hooked up to the Internet 24/7 and I have a domain with dyndns.org.  I was hoping to use Wordpress to run an audio blog (podcast).  I decided on WordPress because it seemed to have the mind share; every where I went I heard about WordPress, and it supported enclosures in rss2 so podcasting with it is a snap.  I also wanted the option to blog regularly, in case I grew tired of recording my voice.  It's also packaged in Ubuntu, so why not?

Now, setting up WordPress should be easy, and it is ***IF*** you're virtual hosting it right on the root of your domain.  If you want to have your site on a different path, however (say /blog), things break quickly.

This proved to be the biggest pain in the *** LAMP app deployment I've ever had to suffer through from packaged software.  Here's how I managed:

**Step 1: Get php5, apache2, and MySQL working, and for good measure install phpmyadmin.**

```

sudo apt-get install php5 php5-mysql mysql-server-4.1 mysql apache2 phpmyadmin

```

When I originally set out to setup WordPress I just tried a "sudo aptitude install wordpress".  This seemed to go through fine, but it didn't download and install php5-mysql, it downloaded and installed php4-mysql.  Php4 wasn't setup on my machine to run under apache, while php5 was.  Depending on what you've installed, your mileage may vary, but regardless, get php/mysql/apache2 working.  You can test by putting a file called index.php into /var/www with the following content:

```

<?php phpinfo(); ?>

```

Now browse to localhost.  Look for a mysql section.  If it doesn't seem to be working, make sure the extension=mysql.so line is uncommented in the /etc/php5/apache2/php5.ini file.  And be sure to restart apache after each change:

```

sudo /etc/init.d/apache2 restart

```

**Step 2: Setup a MySQL user for WordPress**

This is where phpmyadmin comes in very handy.  I don't know about you guys, but dealing with mysql through the mysql commandline gives me absolute fits.  With phpmyadmin, it's very easy to setup a new user account and database for WordPress.  You could always use the root user, but such things are never really a good idea.  Also, phpmyadmin can be used to fix your admin password in WordPress in case you forget it.  Also, in case your install goes poorly, just drop all the tables in the wordpress database and restart the install.  If you installed phpmyadmin, just point your browser localhost/phpmyadmin.  If you haven't setup a password for root yet, just type root as the username and leave the password blank (you should change the root password for mysql as soon as you can though).

**Step 3: Download and install WordPress.**

```

sudo apt-get install wordpress.

```

Now for things to get weird.  The Debian package has its own way of dealing with WordPress.  One advantage to this is that it works very well, out of the box, for Virtual Hosting (allowing you to host several blogs on one machine under multiple domain names without having to have several different copies/installs of WordPress).  Nice that, except very few Ubuntu users probably need this.  Oh well, a Debian side-effect.  The master copy of WordPress is kept in /usr/share/wordpress.  We're going to be aliasing that directory for apache.  Put the following in a brand new file: /etc/apache2/conf.d/wordpress.

```

Alias /blog /usr/share/wordpress

# I'll talk about this line later.  You're probably going to need it
Alias /wp-content /usr/share/wordpress/wp-content

<Directory /usr/share/wordpress>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
  DirectoryIndex index.php
</Directory>

```

This provides an path to the blog called blog, so after the next few steps, my blog should be available from [http://locahost/blog](http://locahost/blog)

**Step 4: Run the configure script from examples.**

There's a script in /usr/share/doc/wordpress/examples that will setup a config file you'll need for your machine.  You run it like so:

```

sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n name localhost

```

where name is the name of *both* the wordpress database and user.  I personally don't like this because I like the name of the database and username to be separate.  However, that can be changed later, so for now, just use one or the other and then fix it in the config file manually.

The config it creates is /etc/wordpress/config-localhost.php.  Here's where the virtual host setup bites us.  This works great from our machine, but we're trying to make a blog that the rest of the web can get to!  Once again, the symlink saves us.

```

sudo ln -s /etc/wordpress/config-localhost.php /etc/wordpress/config-my.domain-name.org.php

```

Viola, same file for two different host names, locahost and our public domain name.

**Step 5: Configure WordPress**

The first part to installing WordPress is to navigate your browser to [http://localhost/blog/wp-admin/install.php](http://localhost/blog/wp-admin/install.php).  Once there, proceed to setup the admin account and settings.

Once your WordPress has been baptized, it would be a good idea to go into the options and change the localhost in the site url to whatever your domain name is.

**Step 6: File Uploads**

Now it seems like your blog is ready to go.  But we're not just blogging, we're podcasting baby!  However, we need to upload files for this.  If you tried to upload a file you probably realized it failed.  That's because Apache, of course, doesn't have write privileges to the uploads folder in /usr/share/wordpress/wp-content.  There are several solutions to this problem.

1) You could just set /usr/share/wordpress/wp-content/uploads world writable or owned by apache and be done with it.  This is probably the easiest solution, however it's probably the least desirable one unless you have one big / partition, in which case, it doesn't matter where you put those files and /usr/share/wordpress/wp-content/uploads is as good a place as any.

```

sudo mkdir /usr/share/wordpress/wp-content/uploads
sudo chmod 777 /usr/share/wordpress/wp-content/uploads

```

2) You could symlink /usr/share/wordpress/wp-content/uploads elsewhere and make it world writable or owned by apache.  This is the second simplest solution.

```

sudo ln -s /home/me/wordpress_uploads /usr/share/wordpress/wp-content/uploads
chmod 777 /home/me/wordpress_uploads

```

3) You could go for the gusto and keep to the spirit of the original Debian package by creating a folder called uploads somewhere, symlinking to it, and creating subfolders for every Virtual Host you may end up having.  This requires that the miscellaneous settings be adjusted for each WordPress site to point to this sub folder for their install.

```

sudo mkdir -p /var/cache/uploads/my_site
sudo chmod 777 /var/cache/uploads/my_site
sudo ln -s /var/cache/uploads /usr/share/wordpress/wp-content/uploads

```

Whatever works, pick what's right for you.

Now, you'd think we'd be done.  But we're not.  Our file uploads work now.  However, in my case, the links to my file uploads were broken!  It took me a while to figure out how to fix this.  Remember this line in the WordPress apache2 conf I had you add?

```

# I'll talk about this line later.  You're probably going to need it
Alias /wp-content /usr/share/wordpress/wp-content

```

Time to talk about it.  The WordPress file upload mechanism seems to assume that you'll be running a WordPress site at the root of the site.  It other words, the WordPress blog starts at /.  In our case it doesn't.  You would think that we could just go into the miscellaneous options and change the upload folder to blog/wp-content/uploads.  However, this doesn't work, because this also affects the path that it looks for the files within the filesystem.  This is basically broken in my opinion.  There needs to be someway of specifying the filesystem path for uploads separately from the url.  But for now, the line above works around it by aliasing a wp-content folder to the root.  I've thought about filing a bug report on this in Launchpad.  The apache2 conf for WordPress that I have presented is taken almost verbatim from the README.Debian in the /usr/share/doc/wordpress folder.  The Alias of /wp-content I added myself.  If WordPress isn't going to fix this problem, it would be nice if the README.Debian were updated to mention this problem.  Not all of us are running a straight-up WordPress site.  Some of us have a need to keep the root of the site different from the blog.

Now then, record something in Audacity, save as an mp3 or ogg, create a blog entry and upload the audio file and link to it in the blog post.  Viola, now your friends just need to put [http://yoursite.com/blog/wp-rss2.php](http://yoursite.com/blog/wp-rss2.php) into their podcatchers and they're good to go.

**Alternative Way**

If the above method sounds very messy, you can simplify it by copying WordPress from the /usr/share/wordpress folder, and pointing apache to that folder instead:

```

cp -r /usr/share/wordpress/* my_new_wordpress_location

```

If you do this I recommend you remove the wp-config.php after copying the files.  Copy the wp-config-sample.php over to wp-config.php and set it up manually and separately from the Debian system.  If you don't do this, you're going to be tied to having to work within /usr/share/wordpress.  You will still need the /wp-content alias in apache for file uploads to work.

Good luck, happy blogging.  Criticisms and comments both welcome.

---

### Post by exiledsoul on 2006-11-26
I was trying to find how to make a wordpress instalation, so this is really helpful, as I've never ran it on my computer.

---

