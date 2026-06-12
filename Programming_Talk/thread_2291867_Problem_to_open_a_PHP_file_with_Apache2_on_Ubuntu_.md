---
title: "Problem to open a PHP file with Apache2 on Ubuntu 14.04"
date: 2015-08-23
forum: Programming Talk
---

### Post by egonzalezgon on 2015-08-23
Good Morning to Everyone, 

Please I'm new user in apache2, I try to open a PHP file on Apache web server, but when I try to open my php file the following message is come (See Image), I know is something with apache.conf or the other things can be with the place where I save my php file, but I not sure what is the exactly problem. I made changes in my apache.conf adding some lines of "[COLOR=#000000][FONT=verdana]AddType application/x-httpd-php .php [/FONT][/COLOR][COLOR=#000000][FONT=verdana]AddType application/x-httpd-php-source .phps"

[/FONT][/COLOR]_**In conclusion:**_

I have made change in my apache.conf
I have made changes in orthers files of apache that I don't remember

Sorry for my english, my native language is other, but I try to push myself to learn it. 
 
[IMG]http://imageshack.com/a/img901/6286/d76qWc.png[/IMG]
[IMG]http://imageshack.com/a/img901/3848/OoZLhM.png[/IMG]
[IMG]https://imageshack.com/i/ipzxXRPQp[/IMG]







[COLOR=#000000][FONT=Ubuntubeta]

[/FONT][/COLOR]

---

### Post by Dimarchi on 2015-08-29
Those are correct responses. The first response happens when no file with the name of index.php is found under the supposed location (default being /var/www/html). This location can be changed, but I get the impression that you have not done that. The second happens when you try to open a PHP file by browsing to the file in question (file://) - you are not using any server at all. Whereas a normal plain HTML file can be successfully opened that way (with possible associated CSS and Javascript), this does not work with server side languages such as PHP. Therefore your browser asks to save the PHP file.

In short: are your files where they are supposed to be? Do they have correct permissions if they are where they should be? This is another potential show stopper.

Don't worry about your English...use it to learn it. I probably have made lots of mistakes, too, but I can't get my message across if I don't try. :)

---

### Post by flaymond on 2015-08-29
Hi,


Why don't try paste all of your PHP code, and put them into a single html file? 

unless you really don't  want people to view the source code, even the html file itself.

---

