---
title: "Apache does not have permission to access webpage."
date: 2015-07-20
forum: Programming Talk
---

### Post by pavelexpertov on 2015-07-20
Apologies if you think I haven't researched about this issue, but I believe it's to do with file/folder permissions, which I am not capable to do (yet).
Basically I have a LAMP set up (apache2 and php5) and I tried to change a documentroot folder to one in my home directory and when I try to access a site file, the apache complained I 'do not have permission' to access this site.
Can anyone help me with this permission issue?
Thanks

---

### Post by spjackson on 2015-07-20
> **pavelexpertov said:**
> Apologies if you think I haven't researched about this issue, but I believe it's to do with file/folder permissions, which I am not capable to do (yet).
Basically I have a LAMP set up (apache2 and php5) and I tried to change a documentroot folder to one in my home directory and when I try to access a site file, the apache complained I 'do not have permission' to access this site.
Can anyone help me with this permission issue?
Thanks
Let's assume for now that the problem is to do with permissions within the filesystem and not within apache configuration. In this case, paste the following into a script file e.g. ~/bin/pathperms.sh
```

#!/bin/bash

filename="$1"
if [ "$filename" = "" ] ; then
    echo Usage: pathperms.sh filename
    exit 1
fi

ls -ld "$filename"
dir=$( realpath "$filename")
dir=$( dirname "$dir")
while [ "$dir" != "/" ]
do
    ls -ld "$dir"
    dir=$( dirname "$dir")
done
exit 0

```
Then run e.g.
```

chmod +x ~/bin/pathperms.sh
~/bin/pathperms.sh /path/to/the/site/file

```
and post the output.

---

### Post by Lars Noodén on 2015-07-20
> **pavelexpertov said:**
> Apologies if you think I haven't researched about this issue, but I believe it's to do with file/folder permissions, which I am not capable to do (yet).
Basically I have a LAMP set up (apache2 and php5) and I tried to change a documentroot folder to one in my home directory and when I try to access a site file, the apache complained I 'do not have permission' to access this site.
Can anyone help me with this permission issue?
Thanks

It's probably permissions.  You can see the exact error message in Apache's error log and from that know which directory it is trying and exactly why it is failing.

```

tail -f /var/log/apache2/error.log 

```

If your DocumentRoot is /home/pavelexpertov/www/htdocs/ then you need to make sure that the web server has read (rx) access to it and lookup access (x) to those above it.   The simplest way is to provide that access to Other rather than a specific group or trying with ACLs.  

```

sudo chmod o+x /home/
sudo chmod o+x /home/pavelexpertov/
chmod o+rx /home/pavelexpertov/www/
chmod o+rx /home/pavelexpertov/www/htdocs/

```

---

### Post by pavelexpertov on 2015-07-20
I have created the script and ran it (/home/adminpav/bin/pathperms.sh /home/adminpav/webfolder/index.html) and then I got an error message I believe:
/home/adminpav/bin/pathperms.sh: line 3: filename: command not found
Usage: pathperms.sh filename

---

### Post by spjackson on 2015-07-20
> **pavelexpertov said:**
> I have created the script and ran it (/home/adminpav/bin/pathperms.sh /home/adminpav/webfolder/index.html) and then I got an error message I believe:
/home/adminpav/bin/pathperms.sh: line 3: filename: command not found
Usage: pathperms.sh filename
It would appear that on line 3 of my script you have a space between the filename and the =. I don't know how that could have occurred using copy and paste since it's definitely not there in what I posted.

The strategy outlined by Lars Noodén should suffice for you. More than likely it is your home directory that is drwx------ or drwxr-x--- but in the absence of information we can only guess.

---

### Post by pavelexpertov on 2015-07-20
Lars nooden, I tried your code with chmod and unfortunately that does not solve the problem, should I try to tail down the error message by using tail command.
spjackson, sorry I used vi to do the thing :P

---

### Post by Lars Noodén on 2015-07-20
Yes, with the exact error message from error.log we can make our guesses more precise. ;)

---

### Post by pavelexpertov on 2015-07-20
spjackson: I just copied and pasted the code and I ran the shell script (after applying Lars's code) and the terminal is now printing the same message in a loop:
drwxr-xr-x 22 adminpav adminpav 4096 Jul 20 15:26 .

PS I am running lubuntu 14.04

---

### Post by pavelexpertov on 2015-07-20
Right, I ran the tail command and that's what I got ( i believe 
it's two lines at the end):
1:51316] AH01630: client denied by server configuration: /home/adminpav/webfolder/favicon.ico
[Mon Jul 20 15:21:59.940874 2015] [authz_core:error] [pid 2317] [client 127.0.0.1:51317] AH01630: client denied by server configuration: /home/adminpav/webfolder/index.html
[Mon Jul 20 15:22:26.131643 2015] [authz_core:error] [pid 2318] [client 127.0.0.1:51318] AH01630: client denied by server configuration: /home/adminpav/webfolder/index.html
[Mon Jul 20 15:23:30.209217 2015] [authz_core:error] [pid 2319] [client 127.0.0.1:51319] AH01630: client denied by server configuration: /home/adminpav/webfolder/index.html
[Mon Jul 20 15:23:31.005270 2015] [authz_core:error] [pid 2319] [client 127.0.0.1:51319] AH01630: client denied by server configuration: /home/adminpav/webfolder/index.html
[Mon Jul 20 15:26:03.456387 2015] [mpm_prefork:notice] [pid 1204] AH00169: caught SIGTERM, shutting down
[Mon Jul 20 15:26:15.957460 2015] [mpm_prefork:notice] [pid 1208] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.11 configured -- resuming normal operations
[Mon Jul 20 15:26:15.958164 2015] [core:notice] [pid 1208] AH00094: Command line: '/usr/sbin/apache2'
[Mon Jul 20 15:26:36.343288 2015] [authz_core:error] [pid 1220] [client 127.0.0.1:60650] AH01630: client denied by server configuration: /home/adminpav/webfolder/index.html
[Mon Jul 20 15:26:36.421646 2015] [authz_core:error] [pid 1220] [client 127.0.0.1:60650] AH01630: client denied by server configuration: /home/adminpav/webfolder/favicon.ico

---

### Post by Lars Noodén on 2015-07-20
Ok.  Do you have a [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory) or [Location](http://httpd.apache.org/docs/2.4/mod/core.html#location) directive set for  /home/adminpav/webfolder/ in your Apache2 virtual host's configuration file?  You can try copying the stanza for the old document root and using that.  In addition to having read access via the filesystem, the virtual host has to be told that it is ok to read the files there.

---

### Post by pavelexpertov on 2015-07-20
Lars, apologies if I am a bit damn on this matter (since it's my first time playing with apache config files), but I read the default config file (which is 000-default.conf from sites-available directory) and I believe it is a virtual host's config file (that is where I changed the documentroot) and I could not find <Directory> or <Location> directives there. However, I decided to read apache.conf file (after reading files in conf-available and sites-available) I found the <Directory> directive but no <location> one. Am I supposed to add the directives to the 000-default.conf file?

---

### Post by Lars Noodén on 2015-07-20
Yes, 000-default.conf is where the modifications for your first vhost go.  So something like this would be added before the </VirtualHost>

```

<Directory /home/adminpav/webfolder/ >
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

```

---

### Post by pavelexpertov on 2015-07-20
Yay it works thank you very much !!!!!!
Just two more questions:
1. So do I still have to change permissions of the folders? Or can I just add this directive?
2. sites-availalbe folder is where I create different config for each virtual host (if I plan to host many websites, right?). So what's the point config-available then? is it use for apache server only?

Thank you very much!!!!!

---

### Post by Lars Noodén on 2015-07-20
No worries.  I'm glad it works.  

1) the two provide different levels and granularity of access.  The file system permissions affect the web server as a whole.  The configuration level permissions can apply to logged in users or client ips or more.  See [Limit](http://httpd.apache.org/docs/2.4/mod/core.html#limit) and [Require](http://httpd.apache.org/docs/2.4/mod/mod_authz_core.html#require) directives.

2) sites-available is where you would have a separate file for each virtual host, one per web site.  Then in sites-enabled, there is a symlink back to the file sites-available when the site is enabled.  See [a2ensite](http://manpages.ubuntu.com/manpages/trusty/en/man8/a2ensite.8.html) and [a2dissite](http://manpages.ubuntu.com/manpages/trusty/en/man8/a2ensite.8.html)

---

### Post by pavelexpertov on 2015-07-20
Thanks, now it's solved.

---

