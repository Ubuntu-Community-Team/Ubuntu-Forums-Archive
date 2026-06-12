---
title: "HOWTO: Apache+suExec+FastCgi+php4+php5 on Dapper"
date: 2007-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by JoachimDurchholz on 2007-01-18
This is for installations that need to support both PHP4 and PHP5 on virtual hosts.
It keeps the virtual hosts separated via suExec, and retains performance by using the Worker MPM for Apache2 and FastCgi for PHP.
A nice side effect is that people can select PHP4 or PHP5 on a per-subdirectory basis.

This Howto does not cover FastCgi for languages other than PHP, or web servers other than Apache 2.
I do not expect any specific problems though. I'm not aware of any interactions that this configuration might have.

**1. Packages needed**

[LIST]
[*]apache2-mpm-worker
[*]libapache2-mod-fastcgi (from Multiverse)
[*]php4-cgi (from Universe)
[*]php5-cgi
[/LIST]

**2. Alternate packages**

You can replace apache2-mpm-worker with apache2-prefork. This will allow either PHP4 or PHP5 to run as a module inside Apache 2.
You can even downgrade to Apache 1.3 (with the apache or apache-ssl package); this may even be sensible because the prefork MPM of Apache 2 isn't substantially better than Apache 1.3. You'd need to use libapache-mod-fastcgi instead of libapache2-mod-fastcgi.

Even though I'd have preferred it over mod_fastcgi, libapache2-mod-fcgid *won't work very well* at this time. Dapper comes with version 1.07, which has some unfixed bugs, and even the most current version of mod_fcgid seems to need a starter script in every directory that has a PHP file.

**3. Configuration**

**mod_fastcgi**

No configuration needed other than adding a line of ```
FastCgiConfig -pass-header HTTP_AUTHORIZATION
``` so that HTTP authorization will work.

You may want to review the other settings here. Some of the timeouts are too low on a heavily loaded server and may result in 500 errors. You might also want to disable the section that configures /cgi-bin if you think that this kind of configuration belongs inside the virtual hosts (as I happen to do).

**Virtual Host**

Each virtual host needs a SuexecUserGroup directive: suExec will refuse to work for virtual hosts without it.

Virtual hosts also need to know where to find the script that handles PHP4 and PHP5, respectively. This is done with these directives inside the <VirtualHost> section:```
<IfModule mod_fastcgi.c>
  <Location /php5-fcgi>
    SetHandler fastcgi-script
    Options ExecCGI
  </Location>
  <Location /php4-fcgi>
    SetHandler fastcgi-script
    Options ExecCGI
  </Location>
</IfModule>
```This makes sure that the URLs /php4-fcgi and /php5-fcgi are run through mod_fastcgi.

You need to install starter scripts in the virtual host's DocumentRoot. The scripts must be readable and executable by everyone, not writable by anyone except their owner, and owned by the user given in SuexecUserGroup (these requirements are too far on the paranoid side for the setup we're doing here, but can't be changed without recompiling mod_suexec).
The should have contents like this:```
#!/bin/bash
export PHPRC=”/etc/php4/cgi”
export PHP_FCGI_MAX_REQUESTS=499
exec /usr/bin/php4-cgi
```for PHP4, and the obvious variant for PHP5.
Again: make sure that they are owned by the right user, are executable, and not readable by anyone except their owner (they must not even be group writable). If you get 500 errors when testing, take a look at /var/log/apache2/suexec.log, it will tell you whether there are permission problems with the starter scripts.

We also need to tell Apache which of these starter scripts will be responsible for .php files. If you need PHP4, add these directives inside a <Directory> section of the virtual host:```
<IfModule mod_fastcgi.c>
  AddHandler php4-fcgi .php
  Action     php4-fcgi /php4-fcgi
</IfModule>
```If you need PHP5, use the php5 equivalents.
Alternatively, you can leave this section out. In that case, PHP won't work unless explicitly enabled for a directory.

**PHP4**

PHP4 needs a specific configuration so that it won't try to execute the starter script.
Edit /etc/php4/cgi/php.ini, search for cgi.fix_pathinfo and set it to 1.

If you don't do this, PHP5 will work fine (it has cgi.fix_pathinfo compiled right in), but PHP4 will simply output the starter script. (You can even put <?php phpinfo (); ?> inside the starter script and will see the PHP information.)

**Directory**

You can enable either PHP4 or PHP5 in a directory. Enabling either will automatically disable the other, so you can enable PHP4 for a virtual host and use PHP5 in the one directory that needs it, or vice versa.

Enabling PHP4 for a directory is done inside the .htaccess file like this:```
AddHandler php4-fcgi .php
Action php4-fcgi /php4-fcgi
```
Modify in the obvious places to get PHP5 instead.

**4. Test**

Restart Apache.

Create a phpinfo.php with this one-liner:```
<?php phpinfo();
```, place it in the root directory and two subdirectories.
Call each from their URLs. If you have made PHP4 or PHP5 the default, the output should show you this.

Restart Apache.

Place a .htaccess file in each subdirectory; one for PHP4 and one for PHP5.
Again, call each phpinfo.php and check that the root directory URL returns the default for the virtual host (or fails if the virtual host does not have PHP activated), and that the phpinfo from the PHP4 directory indeed reports PHP4 and the other PHP5.

If you have another Linux box, go there and run```
ab -c 100 -n 1000 http://your.virtual.host/phpinfo.php
```
If you have no other Linux box, do it on the same machine; you'll mostly benchmark how fast ab (Apache Bench) can process the server responses, but you'll still be able to see whether the whole construction will process everything correctly even under heavy load. (If you wish to see the fun, open another console on the server machine and run the "top" program. There's a "load average" output on the right side of the first line, which will give you a rough average statistic about how many processes have been competing for the CPU at any given time. On a single-machine test, I get load averages between 10 and 20; normally, load averages should stay slightly below 1, but driving the machine to a high load average will more likely expose errors.)

The output from ab should report only "Length" errors (it seems that the output from phpinfo can occasionally be a byte shorter than usual - I don't know what exactly varies here, but haven't investigated further).

---

