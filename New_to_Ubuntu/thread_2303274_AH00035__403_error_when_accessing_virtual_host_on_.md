---
title: "AH00035 / 403 error when accessing virtual host on micro sd card"
date: 2015-11-17
forum: New to Ubuntu
---

### Post by Wolly_daKotzah on 2015-11-17
Hi

I've just set up three virtual servers on my intel compute stick under Ubuntu 14.04 LTS.
I am using the standard apache2 configuration with directives in sites-available.

The first two virtual websites are in /var/www and work just fine.

The third virtual website -- togo.eu -- is installed on a micro sd card, formatted using gparted with a large ext3 partition 

[Tue Nov 17 17:08:18.090792 2015] [core:error] [pid 2994:tid 139919758452480] (13) Permission denied: 
[client 127.0.0.1:57731] AH00035: access to / denied 
(filesystem path '/media/<myname>/<partition label>') 
because search permissions are missing on a component of the path

I have followed the advice about AH00035 / 403 errors and checked that all files and directories in the path up to media have the "x' bit set.
I have chowned all directories and the html index file then restarted apache2 using sudo.

I still get the message:
Forbidden
You don't have permission to access / on this server.
Apache/2.4.7 (Ubuntu) Server at togo.eu Port 80

I have spent many hours trying to get this to work: I don't have enough space to host my website on the intel stick, so was wondering if any of you experts could help?

All the best
Wolly

---

### Post by Wolly_daKotzah on 2015-11-18
Solved thus:
( from: [https://askubuntu.com/questions/691119/virtual-host-apache2-403-error](https://askubuntu.com/questions/691119/virtual-host-apache2-403-error) )

This error occures when your web server hasn't access to DocumentRoot  folder. you must check permissions of parent folders of folder that you  specify in DocumentRoot variable. www-data must access read and execute  to parent folders and also access read to files under DocumentRoot  directory. you can solve this by changing the owner of files and folders  to www-data or give read and execute access to all others.

So I moved to root ( / ) and entered in the terminal:
sudo chown -R www-data:www-data /media

Many thanks to [Ghasem Pahlavan]("https://askubuntu.com/users/417680/ghasem-pahlavan") for this!

---

