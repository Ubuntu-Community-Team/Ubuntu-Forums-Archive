---
title: "[php][apache] starting graphical program on local server"
date: 2013-05-24
forum: Programming Talk
---

### Post by The Squig on 2013-05-24
edit: solved.
for anyone else working on a similar solution you need to:

set DISPLAY=:0
remove memory limit in php.ini (set to -1)
(possibly)add home variable in apache2/envvars
(possibly) edit sudoers file to set admin permissions
---------
Hi. So i recently set up my old computer as a htpc running ubuntu 13.04 and xbmc. Now I also want it to run some emulators and other programs but i really don't want to have to use a keyboard and mouse to control it. To solve this i decided to also let it serve webpaqges on my local network, using php to generate links to my apps and game library and launch them.

Ive setup up a test page but im having some trouble. Ive changed the "APACHE_RUN_USER" and "APACHE_RUN_GROUP" params  (/etc/apache/envvars)  to my current user account but i have to manually stop and start apache before my code works. Any help with this would be appreciated. 

Also, i know that this is probably super bad practice but this will be a local server only available on my lan network.

example: 
```
exec("zsnes"); 
```
this only works after i have restarted apache.

---

