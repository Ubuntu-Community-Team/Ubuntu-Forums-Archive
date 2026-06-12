---
title: "apache and .php"
date: 2005-04-14
forum: Programming Talk
---

### Post by T31 on 2005-04-14
I have this problem i cant make my firefox or mozilla executes a .php creating a local website all the time try to download it and open it as a text file, ive been googling and asking in the irc channels but noone seems to be able to solve, should be a problem with httpd.conf, which i have 2 one in /etc/apache-perl and one in etc/apache2, should be this last one to modify by adding in the <ifModule mod_dir.c>
this:

AddType application/x-httpd-php .php .php3 .php4 .phtml
 AddType application/x-httpd-php-source .phps

the point is there is not such section this is paste of my whole httpd.conf file in /etc/apache2

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

as u can see is nothing but a huge comment

please any idea how to help me :(

Thanks in advance

 [-o<

---

### Post by rostved on 2005-04-14
Where do you place the php file you want to parse and view in your browser?

The files must be under your document root - the default is /var/www. Other directories can be added by creating virtual hosts in /etc/apache2/sites-available. Otherwise php wont parse the files.

The Apache config file is /etc/apache2/apache2.conf

Check that file for these lines:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

You should also have a file named php4.conf in /etc/apache2/mods-enabled containing these lines:
<IfModule mod_php4.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

---

### Post by T31 on 2005-04-14
thx rostved

Ive been checking and I lack this php4.conf file, shoud I create a blank one and add the lines u gave me?

---

### Post by rostved on 2005-04-15
You're welcome

I've just noticed that /etc/apache2/mods-enabled/php4.conf is just a link to the actual file in /etc/apache2/mods-available/

But if you lack the file, you've probably not installed the Apache PHP module, which is the package named libapache2-mod-php4. Installing this should setup PHP as a module for Apache. Just apt-get for it.

Maybe you should take a look at this thread:
[http://ubuntuforums.org/archive/index.php/t-17875.html](http://ubuntuforums.org/archive/index.php/t-17875.html) 

I hope this is helpful

---

### Post by T31 on 2005-04-15
I already have that package in my system, I was reading that link but is for apache Im using apache 2 :( :?

---

### Post by jdonnell on 2005-04-15
What folder are you saving your php file in?

What do you get when you run this command?
```
ls /etc/apache2/mods-enabled/
```

---

### Post by T31 on 2005-04-16
I was saving in /var/www but I solved it at last doing this

/etc/apache2/mods-enabled #  ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/php4.conf


etc/apache2/mods-enabled #  ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/php4.load

/etc/apache2/mods-enabled # /etc/init.d/apache2 restart  * Forcing reload of web server  (Apache2)...                                 [ ok ]
 
xD thx very much to all of you were helping me xD

---

### Post by Nolgthorn on 2005-05-18
I'm sorry but I have this same problem, I am saving in /var/www and how do I fix this? I didn't understand T31's solution. Thank you.

---

### Post by Nolgthorn on 2005-05-18
Just to be clear I did everything I read in this thread trying to fix this same problem. Then I went into Root terminal and inputted the above commands:

ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/php4.conf

ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/php4.load

/etc/init.d/apache2 restart

Which created the appropriate links I needed in mods-enabled then restarted the web server. But I still get the message popping up telling me it needs to know what to open the file as.

The strange thing is I've had this working before, but when I updated my apache2 version this started happening. My old install of phpmyadmin (which is linked to in /var/www) works! but none of my websites (which are also linked to in /var/www) do.

[img]http://ubuntuforums.org/images/smilies/eusa_whistle.gif[/img]

Please help!

---

### Post by Nolgthorn on 2005-05-18
hmm, nevermind! It fixed itself after about 20mins... damn that's annoying yet relieving. Too bad ONE of my websites still doesn't come up. it's got to be a cache problem but that doesn't seem to be fixing it. I'll turn off my computer and come back to it in the morning.

Thanks you guys (women) nevermind me. Carry on.

---

### Post by LordHunter317 on 2005-05-18
No, it means you still have a configuration issue of some sort.

Everyone read this post, as I don't intend on repeating this information about how Debian's Apache2 configuration works again.

The "master" configuration file is in /etc/apache2/apache2.conf.  As a rule, you shouldn't play with this file unless you know exactly what you're doing (and if you're reading this, you don't) or if you need to make a change that effects everything and everyone.  The OOB configuration is just fine as is. 

Modules are enabled via files named *.load in /etc/apache2/modules-enabled.  Clever, eh?  The configuration for a module will be in a .conf file in the same directory that matches the name of the load file.  
What modules are available to you are listed in /etc/apache2/modules-available.  To enable a module run a2enmod.  To disable one, run a2dismod.

Finally, the stock configuration is setup for VirtualHosting.  When you add a site, add it to /etc/apache2/sites-available.  Sites currently running will be under /etc/apache2/sites-enabled.  You can use a2ensite and a2dissite to enable and disable sites.

The default site is in /etc/apache2/sites-available/default, or /etc/apache2/sites-enabled/000default (this is a symlink to the former).  As a rule, this should be the only file you ever edit in the stock configuration.  It'll be the only one you need to edit.

After you make a change, you must restart or reload apache.  Adding/removing modules and sites will require a restart.  Just about everything else requires only a reload.

---

### Post by ensenadaubuntulover on 2005-06-02
libapache2-mod-php4.[B]


THIS IS IT!!!


looking for my firefox to recognize .php spend days con

php4.ini and httpd.conf and lots of places and finally


install  libapache2-mod-php4. 

/etc/init.d/apache2 stop
etc/init.d/apache2 start 

AND WORKED!!!


many thanks good point for you

---

### Post by slowboy on 2006-12-21
I am having a related problem to this post.  I have damaged my apache2, php4, Ubuntu hoary server by attempting to update to PHP5 without being smart enough.  At this point I have apache2 back up and running, but PHP is not working correctly.  When I try to load the test page "http://localhost/info.php" it prompts me to save the file. So I believe my problem is that the PHP module is not loaded in apache2.

The easiest solution seems to be to run

[INDENT]# apt-get install libapache2-mod-php4
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu15 is to be installed
E: Broken packages[/INDENT]

I get this error here and the module will not install.  I get the same error when attemping with PHP5.

So my next attempt was to load the modules directly so I added the aliases using the following commands:

[INDENT]# ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/php4.load
# ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/php4.conf[/INDENT]

then I reload the apache2 and get the following:

[INDENT]>/etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)...
Syntax error on line 1 of /etc/apache2/mods-enabled/php5.0.load:
Cannot load /usr/lib/apache2/modules/libphp4.so into server: /usr/lib/apache2/mo *les/libphp4.so: undefined symbol: ap_block_alarms                      [fail][/INDENT]

So I guess my question at this point is how to I get the 
[INDENT]libapache2-mod-php4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu15[/INDENT]fixed so that i can use the
[INDENT]apt-get install libapache2-mod-php4[/INDENT]
to get my php4 working again!?

Thanks !

Matt

---

### Post by phenylhydride on 2007-04-10
I was having the same issue with getting a php test page to work, and having the browser try to download the .php file.  Like it said in another post, mine seems to have magically started working after around 20 minutes too!  


:confused:            I don't get it...

---

### Post by SyncMaster on 2007-04-14
Just for info, for people who try to run php4 within a .html file on apache2 (not a .php file, but .html!):

I edited /etc/apache2/mods-enabled/php4.conf and added .html.

<IfModule mod_php4.c>
# Rainer added .html
  AddType application/x-httpd-php .php .phtml .php3 .html
  AddType application/x-httpd-php-source .phps
</IfModule>


After restarting Apache, it worked.
This was after trying unsuccesfully to edit apache2.conf and adding .html.

I don't know if this is *the way" to do it, it just worked for me.

Gruess
Rainer

---

### Post by iqpoxy on 2009-07-18
i solved this problem by uninstalling php5-suhosin.  hope this info helps.

---

### Post by infamousnation on 2009-08-07
I have problems with it too.  I have the mods enabled, but it serves the .php file instead of generating an html file.  I don't really understand why.  My experience with debian running apache2/php/mysql is that index.php should be run, cached, converted to index.html and served to your user when they visit your site.  They should never get the .php file so something is wrong.  php workes, i checked it from the cli, the apache2 mod is installed, and still nothing.  This is my first attempt at installing php on Ubuntu though.  Debian always worked fine so I don't see what the difference would be.

and it magically starts working after 20 minutes?  i kinda laughed when i read that in other peoples posts but um yeah...it works?  k

---

