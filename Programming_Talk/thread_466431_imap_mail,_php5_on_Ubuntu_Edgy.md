---
title: "imap_mail, php5 on Ubuntu Edgy"
date: 2007-06-06
forum: Programming Talk
---

### Post by ozpak on 2007-06-06
Hey all

I am relatively new to LAMP setups so bear with me...

I need to get imap_mail operational on Ubuntu Edgy / php5 / apache2. 

I currently receive an error message:

*Fatal error: Call to undefined function imap_mail() in (filepath deleted).php on line 83*

I know I have not configured anything to do with imap_mail - but I can't seem to find any how-to's - any ideas?

---

### Post by ozpak on 2007-06-06
Well that was easy:

At terminal:

1. apt-cache search imap | grep php

   This gave me a list of available packages of which php5-imap was one...

2. sudo apt-get install php5-imap

   Installed all good - now restart apache2...

3. sudo /etc/init.d/apache2 restart

  Code now working just need to set correct smtp details in php.ini I guess

---

