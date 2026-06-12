---
title: "MySQL Connector/ODBC won't connect to internal network"
date: 2012-01-09
forum: Programming Talk
---

### Post by memilanuk on 2012-01-09
I've got MySQL Connector/ODBC 5.1 installed on my Windows Vista laptop. I have MySQL 5.5.19 installed on the laptop, and was able to connect to it via the Windows Data Source Administrator app and the MySQL Connector/ODBC using a TCP/IP connection to 'localhost'. I could connect to the MySQL database both via the command-line client and via M$ Access and Excel.

I also have Virtualbox installed with a LAMP server running on a host-only network. I can connect to the LAMP server via cmd.exe, PuTTY, Firefox, etc. I've modified the mysql configuration on the LAMP server to accept connections from other than just (its) localhost, and can connect to it across the (virtual) network via the mysql command line client.

What I can't seem to do is create an ODBC connection to the mysql database on the LAMP server from the host PC. Specifically, when I type in the IP address for the LAMP server on the host-only network '192.168.56.101' and click 'Test', I get an error message that the connector couldn't establish a connection to '192.168.56.1'...

I'm not sure why its dropping the last couple digits of the ip address... any ideas how to get around/over this?

---

### Post by memilanuk on 2012-01-11
Turns out the problem was the user privileges on the LAMP server only allowing connections from 'localhost' (the guest VM), hence it bouncing connection attempts from 192.168.56.1...  nothing to do with Virtualbox or ODBC  :oops:

---

