---
title: "plesk no longer workign after updating packages and package updating error"
date: 2017-06-24
forum: New to Ubuntu
---

### Post by thexnightmare on 2017-06-24
Dear,
I have a ubuntu vps
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty


I tried form plesk to update packages, this error appears
Update failed.
2017-06-17 07:47:11 INFO: pum is called with arguments: ['--update', '--json', '--', 'libgnutls-openssl27', 'libgnutls26']
2017-06-17 07:47:18 INFO: updating packages: libgnutls-openssl27 libgnutls26 libgnutls26:i386
saslpasswd2: user not found
dpkg: error processing package sasl2-bin (--configure):
subprocess installed post-installation script returned error exit status 20
Errors were encountered while processing:
sasl2-bin
Error in function:
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
2017-06-17 07:47:24 ERROR: installArchives() failed
2017-06-17 07:47:24 ERROR: Exited with returncode 1.


then now the plesk is not accessible any more, and if i ttry by ssh to apt-isntall upgrade, this eerror appears:


apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-headers-generic linux-headers-virtual linux-image-virtual
  linux-virtual python3-software-properties software-properties-common
  software-properties-gtk
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up sasl2-bin (2.1.25.dfsg1-17build1) ...
saslpasswd2: user not found
dpkg: error processing package sasl2-bin (--configure):
 subprocess installed post-installation script returned error exit status 20
Errors were encountered while processing:
 sasl2-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any idea !!!!

UPDATE1: Ive solved the pavckages update error by following this guide: [https://talk.plesk.com/threads/solved-plesk-update-error-12-5-30-mu-19.336640/](https://talk.plesk.com/threads/solved-plesk-update-error-12-5-30-mu-19.336640/), however plesk is not opening on [https://domain.com:8443]("https://domain.com:8443:") :
**This site can&#8217;t be reached**

[COLOR=#646464][FONT=&amp]**[www.bixma.com]("http://www.bixma.com")** refused to connect.[/FONT][/COLOR]
[COLOR=#646464][FONT=&amp]Try:

[LIST]
[*]Checking the connection
[*][Checking the proxy and the firewall]("http://data:text/html,chromewebdata#buttons")
[/LIST]
[/FONT][/COLOR]
[COLOR=#646464][FONT=&amp]ERR_CONNECTION_REFUSED[/FONT][/COLOR]

---

