---
title: "how to execute perl in a browser?"
date: 2009-11-23
forum: Programming Talk
---

### Post by abhilashm86 on 2009-11-23
i want to execute web html along with perl in browser, so i saved it in /var/www/pgm1.pl
this is program i want to run,
```
#! /usr/bin/perl
use CGI':standard';
print "content-type:text/html \n \n";
print "<head><title> Server info </head></title>","<br />";
print "<body><h1><center> Server informaiton </center></h1></body>";
print "Server name :", $ENV{'SERVER_NAME'};
print "Server port :", $ENV{'SERVER_PORT'};
print "SERVER software :", $ENV{'SERVER_SOFTWARE'};
print "server cgi revision :", $ENV{'GATEWAY_INTERFACE'};
print "</body></html>\n";
exit(0);

```
when i type in browser like ```
http://localhost/pgm1.pl
``` 
error is given in browser like,
```
Forbidden

You don't have permission to access /pgm1.pl on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch Server at localhost Port 80
```

and when i try executing from other directory, i can't execute....
how to execute, help please.....

---

### Post by Reiger on 2009-11-23
First read up on file permissions because no-permission is probably just that.
Second you will need a special module for using Perl in combination with Apache -- namely mod_perl if I am not mistaken.

---

### Post by abhilashm86 on 2009-11-23
> **Reiger said:**
> First read up on file permissions because no-permission is probably just that.
Second you will need a special module for using Perl in combination with Apache -- namely mod_perl if I am not mistaken.

the permission is correct, 
```
abhilash@abhi:~$ ls pgm2.pl -l
-rwxr-xr-x 1 abhilash abhilash 102 2009-11-23 12:12 pgm2.pl*

```
yes i installed mod_perl in beggining.......
can you tell where should i save perl programs? like in windows i save in /programfiles/Apache2/htdocs.......

i get something like, what u want to do to file, save or open with?

---

### Post by abhilashm86 on 2009-11-23
i checked apache2 logs, found this error, how do i make ExecCGI on, if that is problem creating error........
please help

 ```
[Mon Nov 23 12:43:40 2009] [error] Options ExecCGI is off in this directory/var/www/pgm2.pl
[Mon Nov 23 12:43:43 2009] [error] Options ExecCGI is off in this directory/var/www/favicon.ico
[Mon Nov 23 12:44:46 2009] [error] Options ExecCGI is off in this directory/var/www/pgm2.pl
[Mon Nov 23 12:45:59 2009] [notice] caught SIGTERM, shutting down
[Mon Nov 23 12:46:00 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Mon Nov 23 12:46:00 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
```

---

### Post by CptPicard on 2009-11-23
A little clarification here... the perl will not run *in the browser*, it runs on the server, and the produced html is displayed in the browser...

---

### Post by KeLa on 2009-11-23
You need to put those perl scripts to cgi-bin directory under /var/www
Or you have to edit apache settings to allow scripts running from anywhere in directory structure.

---

### Post by abhilashm86 on 2009-11-24
there was a configration in apache2, now i corrected it so perl is working, php is not working.........

---

### Post by A_Fiachra on 2009-11-24
> **abhilashm86 said:**
> i checked apache2 logs, found this error, how do i make ExecCGI on, if that is problem creating error........
please help

 ```
[Mon Nov 23 12:43:40 2009] [error] Options ExecCGI is off in this directory/var/www/pgm2.pl
[Mon Nov 23 12:43:43 2009] [error] Options ExecCGI is off in this directory/var/www/favicon.ico
[Mon Nov 23 12:44:46 2009] [error] Options ExecCGI is off in this directory/var/www/pgm2.pl
[Mon Nov 23 12:45:59 2009] [notice] caught SIGTERM, shutting down
[Mon Nov 23 12:46:00 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Mon Nov 23 12:46:00 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
```

Find the place in your httpd.conf file that sets the DocumentRoot directory, add a directive for ExecCGI on that directory, something like:

<Directory blah.blah.blah>
    Options +ExecCGI
</Directory>

See apache.org for details on how to get CGI programs working outside the cgi-bin directory and getting apache to recognize the .pl extension as a CGI program.

You probably do NOT want suEXEC running, unless you actually know what you are doing.

Mod_perl is another beast altogether.

What you are doing is asking the Apache Web Server (httpd) to execute a Perl source file (it must be executable, since Apache knows nothing about perl).  Don't use exit() it's not needed, when Apache has finished executing your Perl code, it will exit for you.

You should look at a tutorial on Perl-CGI.

---

### Post by A_Fiachra on 2009-11-24
> **abhilashm86 said:**
> there was a configration in apache2, now i corrected it so perl is working, php is not working.........


Of course, you backed up your config files before editing them, so it will be no problem undoing what you have done.

Right?

---

### Post by wojox on 2009-11-24
[http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html)

---

### Post by abhilashm86 on 2009-11-24
i've configured and not made back-up of my apache2?? so i;m removing and installing apache2 again!! since i'm working perl and php, i messed up things!!

---

### Post by slavik on 2009-11-24
> **A_Fiachra said:**
> Of course, you backed up your config files before editing them, so it will be no problem undoing what you have done.

Right?
sudo apt-get install etckeeper ;)

---

### Post by meson2439 on 2009-11-24
Since its using cgi why don't you put them on /usr/lib/cgi-bin. hope it works.

---

