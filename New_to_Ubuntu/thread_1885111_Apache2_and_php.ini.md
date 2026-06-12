---
title: "Apache2 and php.ini"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by girishd on 2011-11-22
I have a question on how the php.ini is located by Apache2. Here are the steps I took.

- Installed apache2 package
- Installed php5 package

I understand that symbolic links are created to load the php5 module in "/etc/apache2/mods-enabled". What I don't understand is how does apache2 know that the php.ini file is in /etc/php/apache2/php.ini. And then how does it know to check /etc/php/apache2/conf.d to pick up additional .ini files? Without package management, I used to set the "PHPIniDir" directive and so I knew where it was looking for php.ini.

---

### Post by satanselbow on 2011-11-22
A stock Ubuntu LAMP does not install in the locations you mention; '/etc/httpd' instead of '/etc/apache2' - you may be thinking of RHEL/Fedora...

You might find something useful in here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

you can symlink php.ini to wherever you see fit to maintain portability ;)

---

### Post by girishd on 2011-11-22
I've read that help page and I followed to exact steps. I guess it doesn't matter where Apache HTTP server is installed. I am more curious to find out how the HTTP server knows where my php.ini file is. If anyone can point me towards a line in some configuration of the HTTP server which says the php-ini file is in "/foo/bar/php.ini", that'll be helpful. Thanks.

---

