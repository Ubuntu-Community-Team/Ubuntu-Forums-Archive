---
title: "lincity-ng"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-02
Here's my attempt in trying to install lincity-ng via the terminal command from [http://lincity-ng.berlios.de/wiki/index.php/Download/Installation](http://lincity-ng.berlios.de/wiki/index.php/Download/Installation), sudo aptitude install lincity-ng lincity-ng-data.

zopiac@zopiac:~$ sudo aptitude install lincity-ng lincity-ng-data
[sudo] password for zopiac: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
zopiac@zopiac:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
zopiac@zopiac:~$ sudo aptitude install lincity-ng lincity-ng-data

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
zopiac@zopiac:~$ 




?

---

### Post by perlluver on 2008-05-02
> **Zopiac said:**
> Here's my attempt in trying to install lincity-ng via the terminal command from [http://lincity-ng.berlios.de/wiki/index.php/Download/Installation](http://lincity-ng.berlios.de/wiki/index.php/Download/Installation), sudo aptitude install lincity-ng lincity-ng-data.

zopiac@zopiac:~$ sudo aptitude install lincity-ng lincity-ng-data
[sudo] password for zopiac: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
zopiac@zopiac:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
zopiac@zopiac:~$ sudo aptitude install lincity-ng lincity-ng-data

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
zopiac@zopiac:~$ 




?

Run in terminal sudo dpkg --configure -a

---

