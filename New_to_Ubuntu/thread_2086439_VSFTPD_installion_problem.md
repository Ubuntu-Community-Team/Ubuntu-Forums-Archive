---
title: "VSFTPD installion problem"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by AJAYSARAF on 2012-11-20
Hi all,
I installed ftp service in my PC but it was not installed properly then i un-installed using command "sudo apt-get remove vsftpd".
I found vsftpd.conf and VSFTPD files even after removing service so i removed them by "rm" command  Then i installed service again but its not installing properly  showing the below error.
############## sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vsftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up vsftpd (2.3.5-1ubuntu2) ...
vsftpd user (ftp) already exists, doing nothing.

vsftpd directory (/srv/ftp) already exists, doing nothing.
invoke-rc.d: unknown initscript, /etc/init.d/vsftpd not found.
dpkg: error processing vsftpd (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

