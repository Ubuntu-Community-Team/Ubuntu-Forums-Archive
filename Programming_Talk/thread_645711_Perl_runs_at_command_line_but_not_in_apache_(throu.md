---
title: "Perl runs at command line but not in apache (through browser)"
date: 2007-12-20
forum: Programming Talk
---

### Post by darcy on 2007-12-20
Hello everyone.

I'm trying to run perl in my Ubuntu-Server. It runs at the command line but not in the Web browser.

This is what my configuration look like for my Web root.

mkdir /home/darcy/www
sudo rm -r /var/www
sudo ln -s /home/darcy/www /var/www

sudo apt-get install libapache2-mod-perl2

In /etc/apache2/apache2.conf I added:
AddHandler cgi-script .cgi
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>

<IfModule mod_perl.c>
<IfModule mod_alias.c>
Alias /perl/ /home/darcy/www/perl/
</IfModule>
<Location /perl>
SetHandler perl-script
PerlHandler Apache::Registry
Options +ExecCGI
</Location>
</IfModule>


sudo /etc/init.d/apache2 restart

When I visit my file in a web browser it just tries to download the file rather than running it.

[http://myserver.com/perl.pl](http://myserver.com/perl.pl)
[http://myserver.com/perl/perl.pl](http://myserver.com/perl/perl.pl)
[http://myserver.com/cgi-bin/perl.pl](http://myserver.com/cgi-bin/perl.pl)

Actually, with the cgi-bin directory, it doesn't let me view the directory and when I try and run the file in there it gives me a 404.

So what do I do if I want to run perl in ubuntu?

So far ubuntu's been easy for everything but I'm finding it hard to find a clear answer on what to do for this.

Darcy

---

### Post by LaRoza on 2007-12-20
I don't know exactly what the reason is, but you can try giving it a .cgi extension, and putting the correct shebang line

#! /usr/bin/perl

---

### Post by darcy on 2007-12-20
The answer is to go to the  httpd.conf file in /etc/apache2 and add the following lines:

ScriptAlias /perl/ /home/darcy/www/perl/

<Directory /home/darcy/www/perl>
  Options +ExecCGI
</Directory>

AddHandler cgi-script cgi pl


I then rebooted apache:
sudo /etc/init.d/apache2 restart

works now. Yippie, I can fool around with Perl in my spare time!

---

