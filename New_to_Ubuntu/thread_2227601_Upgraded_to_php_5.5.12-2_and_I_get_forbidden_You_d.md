---
title: "Upgraded to php 5.5.12-2 and I get forbidden You don't have permission to access....."
date: 2014-06-03
forum: New to Ubuntu
---

### Post by AskTell on 2014-06-03
I get the Forbidden you don't have permission to access {filename} on this server if I enter a file which doesn't exist or a php file

I used this guide to upgrade from 5.3 to 5.5.12-2 [http://phpave.com/upgrade-php-5-3-php-5-5-ubuntu-12-04-lts/](http://phpave.com/upgrade-php-5-3-php-5-5-ubuntu-12-04-lts/)

my current Apache version is 2.4.9

EDIT: found this in my apache error log "AH01630: client denied by server configuration:"  looking up now.

EDIT2: Found [http://dabase.com/blog/AH01630:_client_denied_by_server_configuration/](http://dabase.com/blog/AH01630:_client_denied_by_server_configuration/) which suggested I add
<Directory "/mydirectory/www">
Options All
AllowOverride All
Require all granted
</Directory>to my apache conf(which I did at the very end /w my directory) and it appears to be working for the time being... will this cause me any issues?

---

### Post by Duncubuntu on 2014-06-04
Your apache conf was probably overwritten with a new default one. This happened to me when upgrading to 14.04 from 13.10. It turns out, when I went to the conf folder, there was a file named apache2.confdpkg-old which contained my original conf file. Maybe this will help you out!

Also that setting should be fine depending on what you want to achieve, and your folder structure.

---

