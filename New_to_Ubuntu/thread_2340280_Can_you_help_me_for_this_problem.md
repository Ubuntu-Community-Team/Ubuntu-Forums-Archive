---
title: "Can you help me for this problem?"
date: 2016-10-17
forum: New to Ubuntu
---

### Post by iqro on 2016-10-17
```
root@155150207111047:/home/d_iqro# apt-get install mailutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mailutils is already the newest version (1:2.99.99-1ubuntu2).
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic
  linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up postfix (3.1.0-3) ...
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
Use of uninitialized value $destinations in scalar chomp at /var/lib/dpkg/info/postfix.config line 221.
Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/Client/ConfModule.pm line 121.
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
Use of uninitialized value $mynetworks in scalar chomp at /var/lib/dpkg/info/postfix.config line 285.
Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/Client/ConfModule.pm line 121.
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
Use of uninitialized value $protos in scalar chomp at /var/lib/dpkg/info/postfix.config line 387.
Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/Client/ConfModule.pm line 121.
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailutils:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

dpkg: error processing package mailutils (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                   Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 postfix
 mailutils
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@155150207111047:/home/d_iqro#
```

---

### Post by jeremy31 on 2016-10-17
*Thread moved to **New to Ubuntu**.*

Please use code tags on terminal output, see link in my signature

Welcome to the forums

You might want to explain what you are trying to do and what you have done

---

### Post by iqro on 2016-10-17
I want to install mail

root@155150207111047:/home/d_iqro# mail
The program 'mail' is currently not installed. You can install it by typing:
apt install mailutils

When installing mailutils always error

Errors were encountered while processing:
 postfix
 mailutils
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can you help me?

---

### Post by Impavidus on 2016-10-17
What is the complete output of apt install mailutils? Error messages on Ubuntu are usually helpful.

---

### Post by iqro on 2016-10-17
root@155150207111047:/home/d_iqro# apt install mailutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mailutils is already the newest version (1:2.99.99-1ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up postfix (3.1.0-3) ...
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
Use of uninitialized value $destinations in scalar chomp at /var/lib/dpkg/info/postfix.config line 221.
Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/Client/ConfModule.pm line 121.
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
Use of uninitialized value $mynetworks in scalar chomp at /var/lib/dpkg/info/postfix.config line 285.
Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/Client/ConfModule.pm line 121.
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
Use of uninitialized value $protos in scalar chomp at /var/lib/dpkg/info/postfix.config line 387.
Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/Client/ConfModule.pm line 121.
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
postconf: warning: valid_hostname: numeric hostname: 155150207111047
postconf: fatal: unable to use my own hostname
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailutils:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

dpkg: error processing package mailutils (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                   Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 postfix
 mailutils
E: Sub-process /usr/bin/dpkg returned an error code (1)

That's the output

---

### Post by oldrocker99 on 2016-10-17
If you have 2 programs not fully installed, do this:```
sudo apt-get -f install
```

---

