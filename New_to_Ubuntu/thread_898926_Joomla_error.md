---
title: "Joomla error"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by skrap on 2008-08-23
I have been working on installing Joomla on Gutsy and I have run into a problem since I am a noob at linux and joomla any help would be appreciated

I am getting; Forbidden

You don't have permission to access /joomla/ on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 Server at localhost Port 80

Obviously I am doing a localhost installation

It seems that I need to change my permissions somehow.  I have installed joomla in the /var/www location in root.

It is probably something simple I am missing.   Please Help.

---

### Post by skrap on 2008-08-23
Ok I'm making some head way.  I resolved the permission problem.  Using gksudo nautilus.  Now I am getting this.  Could be I need to post to the Joomla forum but I'll try here first.  This is a much better forum.

Warning: session_start() [function.session-start]: open(/var/lib/php5/sess_29e087d6fe11f87013b2c057f3b2bd03, O_RDWR) failed: Permission denied (13) in /var/www/joomla/libraries/joomla/session/session.php on line 413

Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /var/www/joomla/libraries/joomla/session/session.php:413) in /var/www/joomla/libraries/joomla/session/session.php on line 413

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /var/www/joomla/libraries/joomla/session/session.php:413) in /var/www/joomla/libraries/joomla/session/session.php on line 413

Warning: Cannot modify header information - headers already sent by (output started at /var/www/joomla/libraries/joomla/session/session.php:413) in /var/www/joomla/libraries/joomla/session/session.php on line 416

Might still have to do with file permissions?  Cookies are enabled in firefox.

???????

---

