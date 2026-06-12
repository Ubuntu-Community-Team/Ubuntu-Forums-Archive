---
title: "proftpd and vsftpd issue connecting"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by lcashmer on 2013-03-06
I am setting up a test server on my own network with LAMP to test my web and WrodPress sites and my PHP and mysql efforts. The server will never be open to the net.

I have tried proftpd and vsftpd for two days now. The server seems to run but I can't log in from other machines on my network LInux or Windows. I get the following error:

Status:    Connecting to 192.168.1.86:21...
Status:    Connection established, waiting for welcome message...
Response:    220 ProFTPD 1.3.4a Server (192.168.1.86) [192.168.1.86]
Command:    USER LouisC
Response:    331 Password required for LouisC
Command:    PASS **********
Response:    530 Login incorrect.
Error:    Critical error
Error:    Could not connect to server

Also, in the proftpd gui, he can't seem to find his config file or his security files. I have used CLI and can edit the config directly and they are where proftpd should expect them to be.

I know this must be really simple, but I am stumped. Especially considering I get the very same error with either program.

Thanks,
Louis

---

### Post by dryicebomb on 2013-03-06
Without looking at your vsftpd.conf file, I can only really guess what is going on. Have you enabled local users? The line you need in your conf file is "local_enable=yes" also, make sure you have this line in your conf file. "pam_service_name=vsftpd"

---

### Post by lcashmer on 2013-03-06
Ooops! I was doing something really really stupid! UseR is not the same as user in the Linux world. Sorry for the post. Resolved!

---

