---
title: "very random - apache2 web server went down?"
date: 2009-05-10
forum: Programming Talk
---

### Post by gfunkera on 2009-05-10
all of a sudden my apache2 web server is acting up and wont load my web site..

i have been workin on the site all day and updating, opening, closing html and php files with no problem..

i stepped away to eat dinner and when i came back i tried opening my web site, but it doesnt work! the tab in firefox says "loading..." and the status bar at the bottom says "Connecting to <MYIPADDRESS>".. i restarted the computer and same thing is happening...

how can i fix this?

---

### Post by slavik on 2009-05-10
can you post the last 20 lines of the error log for apache?

---

### Post by gfunkera on 2009-05-10
here is the end of the error log...

[Sun May 10 15:15:24 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun May 10 15:15:27 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun May 10 16:49:29 2009] [error] [client my _ip_address] File does not exist: /var/www/favicon.ico
[Sun May 10 16:49:32 2009] [error] [client my _ip_address] File does not exist: /var/www/favicon.ico
[Sun May 10 16:49:32 2009] [error] [client my _ip_address] File does not exist: /var/www/favicon.ico
[Sun May 10 18:35:10 2009] [error] [client my _ip_address] script '/var/www/outputInfo_color.php' not found or unable to stat
[Sun May 10 18:49:26 2009] [notice] caught SIGTERM, shutting down
[Sun May 10 18:50:16 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sun May 10 18:51:06 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun May 10 18:51:07 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun May 10 19:02:31 2009] [error] [client my _ip_address] File does not exist: /var/www/favicon.ico
[Sun May 10 19:02:34 2009] [error] [client my _ip_address] File does not exist: /var/www/favicon.ico
[Sun May 10 20:11:24 2009] [notice] caught SIGTERM, shutting down
[Sun May 10 20:12:13 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sun May 10 20:14:02 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun May 10 20:21:44 2009] [notice] caught SIGTERM, shutting down
[Sun May 10 20:21:45 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sun May 10 20:27:13 2009] [notice] caught SIGTERM, shutting down
[Sun May 10 20:27:14 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sun May 10 20:35:50 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun May 10 20:35:50 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun May 10 20:38:27 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

---

### Post by slavik on 2009-05-10
are you trying to access PHP page that connects to a database?

---

### Post by gfunkera on 2009-05-10
i figured out what happened...

somehow, my LAN IP address was changed and i had to update that in the DMZ and port forwarding setup of my router...

thanks anyway!!

---

