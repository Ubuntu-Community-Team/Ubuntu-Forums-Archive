---
title: "error installing ruby-rvm in ubuntu 12.04"
date: 2013-07-19
forum: Repositories &amp; Backports
---

### Post by theunknown12381 on 2013-07-19
[LEFT][COLOR=#000000][FONT=Arial]when i try to install ruby-rvm in ubuntu 12.04 using this command[/FONT][/COLOR][/LEFT]
```
sudo apt-get install ruby-rvm
```  [LEFT][COLOR=#000000][FONT=Arial]it downloads the packages correctly but then gives this error[/FONT][/COLOR][/LEFT]
```
dpkg-statoverride: error: syntax error: unknown group 'admin' in statoverride file
dpkg: error processing ruby-rvm (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ruby-rvm
E: Sub-process /usr/bin/dpkg returned an error code (1)



```[LEFT][COLOR=#000000][FONT=Arial]the contents of stateoverride file are as follows[/FONT][/COLOR][/LEFT]
```
root mlocate 2755 /usr/bin/mlocate
hplip root 755 /var/run/hplip
root ssl-cert 710 /etc/ssl/private
root crontab 2755 /usr/bin/crontab

```
any help would be appreciated

---

