---
title: "lamp apache2 developer mode? no 500!"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by dako541 on 2013-02-04
hi, just installed lamp for local php testing.  

when i code a bug, localhost does big "Server Error 500" instead of the developer mode telling me what exact line I goofed my php on.  What was that one liner i'm supposed to add to some config file (and what config file?).  Thanks!

ps: lamp by default isn't serving requests from the web is it?  I just want to dev locally.

---

### Post by SeijiSensei on 2013-02-04
The errors are logged to /var/log/apache2/error.log.  The simplest solution is to open a terminal window, then run "sudo tail -f /var/log/apache2/error.log" and try your application.  You'll see the errors appear in the terminal window.  You can alternatively activate "display_errors = on" in /etc/php5/apache2/php.ini.  Make sure to restart Apache after making that change.  Then the errors will appear within the page itself.

---

### Post by dako541 on 2013-02-05
yes, thank you.  this is resolved.

note the cmd to restart is  sudo /etc/init.d/apache2 restart
note in the php.ini file display_errors is mentioned twice, so On latter

---

### Post by SeijiSensei on 2013-02-05
> **dako541 said:**
> yes, thank you.  this is resolved.

note the cmd to restart is  sudo /etc/init.d/apache2 restart
note in the php.ini file display_errors is mentioned twice, so On latter

You must be using an older version of Ubuntu.  The /etc/init.d/daemon_name method has been deprecated in favor of the /sbin/service command since the introduction of [Upstart]("http://upstart.ubuntu.com/faq.html").

---

