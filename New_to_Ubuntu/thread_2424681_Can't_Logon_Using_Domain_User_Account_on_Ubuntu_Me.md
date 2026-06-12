---
title: "Can't Logon Using Domain User Account on Ubuntu Member Server"
date: 2019-08-12
forum: New to Ubuntu
---

### Post by wilsont on 2019-08-12
Hello, 
First, here is some basic info about versions and modules on the server:
Server OS: Ubuntu 18.04.02 LTS
Samba ver. 4.7.6
Winbind is installed.
NTP is installed and configured.

I'm new to using Ubuntu and find the OS amazing. I have joined this server to an Active Directory domain as a member server. I installed kerberos, can verify the security, and have the smb.conf (using security = ads), krb5.com, sssd.conf, and nsswitch.conf configured. So far, I have generated the kerberos ticket with kinit and can view the info with klist successfully. Joining the domain was successful and the Ubuntu server is listed in Active Directory Users and Groups app. The trust account was successfully validated using wbinfo -t.
I have verified a user authentication request using wbinfo -a "DOMAIN\username%password" (substituting in the real values for DOMAIN, username, and password.)
I can verify the NSS library using the following command --> getent passwd "DOMAIN\username."

Where I am missing it is probably with the user mappings and am unsure what to do.
Whenever I try logging in with a username (in either of these formats) it is not recognized: DOMAIN\username or [EMAIL="username@DOMAIN.COM"]username@DOMAIN.COM[/EMAIL]
I would appreciate some assistance with this basic task and need an example of how user and/or groups need to be mapped into the /etc/groups and /etc/passwd file. 
_The goal here is to simply logon to the Ubuntu server with an ALLOWED domain user account to eliminate the need to create more local accounts._
Thanks in advance, 
Tim

---

