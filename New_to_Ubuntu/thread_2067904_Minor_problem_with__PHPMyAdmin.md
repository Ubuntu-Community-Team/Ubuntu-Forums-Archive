---
title: "Minor problem with  PHPMyAdmin"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by richpri on 2012-10-07
I am using PHPMyAdmin version 3.4.10.1deb1 to
access a local host mysql server version 5.5.24
via Apache/2.2.22 and Firefox 

When I create new columns in a table the collation
field is set to latin1_swedish_ci.  I have tried
to reset it to utf8_general_ci with no success.

How can i correct this default?

---

### Post by richpri on 2012-10-10
Apparently this is not a problem with PHPMYADMIN.  I get the same error when accessing MYSQL from the command line.  I did some more work on this and posted the results to [http://forums.mysql.com/read.php?10,570569,570569#msg-570569](http://forums.mysql.com/read.php?10,570569,570569#msg-570569)  

Please look there and let me know if you have any suggestions.

---

### Post by richpri on 2012-10-15
This is an apparmor issue that is fully described here.

[http://www.tek-tips.com/viewthread.cfm?qid=1695450](http://www.tek-tips.com/viewthread.cfm?qid=1695450)

The solution is to modify the  local apparmor security profile for mysql in the /etc/apparmor.d/local directory.

See the above link for details. :biggrin:

---

