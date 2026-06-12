---
title: "Application install taking forever"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by michael63 on 2013-09-15
I am following the instructions to install owncloud on my 12.04 Ubuntu machine from [http://www.slsmk.com/how-to-install-owncloud-to-ubuntu-12-04/](http://www.slsmk.com/how-to-install-owncloud-to-ubuntu-12-04/)

When I entered
echo 'deb [http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_12.04/](http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_12.04/) /' >> /etc/apt/sources.list.d/owncloud.list

I got some sort of error, so I just went on to the next step.

Then at the command prompt in terminal I typed:
gksu apt-get install owncloud

The result is as follows

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gwibber-service libgtkspell-3-0 libgwibber-gtk2 gwibber-service-twitter
  libgwibber2 gwibber-service-identica python-libproxy
  python-egenix-mxdatetime python-egenix-mxtools gwibber-service-facebook
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common
  libapache2-mod-php5 libdbd-mysql-perl libdbi-perl libhtml-template-perl
  libmysqlclient18 libnet-daemon-perl libplrpc-perl libssl-dev libssl-doc
  libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common
  mysql-server mysql-server-5.5 mysql-server-core-5.5 php-pear php-xml-parser
  php5 php5-cli php5-common php5-dev php5-gd php5-mysql shtool zlib1g-dev
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom libipc-sharedcache-perl
  tinyca mailx php5-suhosin
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common
  libapache2-mod-php5 libdbd-mysql-perl libdbi-perl libhtml-template-perl
  libmysqlclient18 libnet-daemon-perl libplrpc-perl libssl-dev libssl-doc
  libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common
  mysql-server mysql-server-5.5 mysql-server-core-5.5 owncloud php-pear
  php-xml-parser php5 php5-cli php5-common php5-dev php5-gd php5-mysql shtool
  zlib1g-dev
0 upgraded, 31 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.0 MB/40.3 MB of archives.
After this operation, 140 MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Them I waited for probably 3 or more hours, and still nothing.  And, I can't tell if it is still doing anything, like downloading or installing, or if it has crashed or something.

Anyhelp is appreciated.  Is there anyproblem with doing the install over and over (well, hopefully just one more time)

Thanks,
Michael

---

### Post by deadflowr on 2013-09-15
Is that the exact deb line you added to the owncloud.list?
Because it does not match and a repo with that line does not exist.
remove it and start over
You can probably just run nano and delete the old line and replace it with the line from the tutorial.
```
sudo nano /etc/apt/sources.list.d/owncloud.list
```
press ctrl + x to save and exit.

Then run 
```
sudo apt-get update
```
look it over for any errors.
If errors come up posts 'em here, if not and everything is fine
Then run
```
sudo apt-get install owncloud
```
You're not running a graphical root so no need to use gksu.

---

### Post by nerdtron on 2013-09-16
After getting owncloud installed, the tutorial to configure it isn't enough.
I followed this. [http://linuxg.net/how-to-install-owncloud-5-on-ubuntu-13-04-and-linux-mint-14/](http://linuxg.net/how-to-install-owncloud-5-on-ubuntu-13-04-and-linux-mint-14/) 
Still works on 12.04 as I have tested.

---

