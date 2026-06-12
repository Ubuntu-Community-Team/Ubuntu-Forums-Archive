---
title: "Ruby on Rails, am I missing something"
date: 2012-09-10
forum: Programming Talk
---

### Post by gregology on 2012-09-10
Hi all,
I am use to LAMP running on Ubuntu and I'm really struggling to get RoR working? When I want to run a php web application, I do a LAMP install and chuck a php file in /var/www/domain.tld and it works.

test.php
```
<?php echo "Hello World!"; ?>
```


I've been messing around with RoR for hours now and I can't even get a simple "hello world!" working.

test.rb
```
<%= puts "Hello World!" %>
```

either downloads or displays the text '<%= puts "Hello World!" %>'

I've created

```
rails new /var/www/test.domain.tld 
```

which has given me heaps of files none of which execute when visited from a browser.

Here is my /etc/apache2/httpd.conf settings:

```
<VirtualHost *:80>
ServerName test3.domain.tld
ServerAlias test3.domain.tld *.test3.domain.tld
DocumentRoot /var/www/test.domain.tld
RailsBaseURI /var/www/test3.domain.tld
</VirtualHost>
```

Am I missing something? Is there a huge difference between PHP and RoR? Is there something fundamentally different between the two and how they operate on a web server?


**Server info.**

I am running an Ubuntu 10.04 VPS hosted by Linode. The server is running a successful LAMP stack and I was trying to add RoR so I can install Ruby web applications. I've tried using the installation guide from linode and I have installed the following packages.

[LIST]
[*]build-essential
[*]libapache2-mod-passenger
[*]apache2
[*]ruby
[*]rdoc
[*]ruby1.8-dev
[*]libopenssl-ruby
[*] libmysqlclient-dev
[*]libmysql-ruby
[*]libsqlite3-ruby
[*]libsqlite3-dev
[/LIST]

---

