---
title: "problem installing netbeans 6 beta"
date: 2007-10-19
forum: Programming Talk
---

### Post by emillekorea on 2007-10-19
I used ubuntu and netbeans 5.5 and try to upgrade 
netbeans 6.0 beta for ruby.

I use below command to install netbeans in ubuntu 7.04

[I]sudo sh netbeans-6.0beta1-linux.sh --javahome /usr/lib/jdk1.6.0_03
[/I]
new window appear and start processing for install
after typing the directory of netbeans and glassfish
"back" and "cancel" button become avilable however, "next" button not available 
below warning happen. So, I can't install netbeans 6 beta.

*Base IDE is set up to be installed to /usr/local/netbeans which does not belong to any of the file system roots *

Surely, I tried to change the directory of netbeans install like /home/****/netbeans, /usr/local/netbeans and so on 
However, I can not gain the good result. before I install the program, I would make the directory and try to change 
the permission like 766. it also did not work. 

install guide say like this.
Note: The installation directory you specify must be empty, and the user profile you are using to run the installer must have read/write permissions for this directory.



Someone ? let me , linux beginer, know how to fix the problem.

---

### Post by emillekorea on 2007-10-23
I wrote at netbeans site 
=====================================
Thank you ...

I found it and solved with ur hint

please understand...mistake as a linux newbie
I thought that I can use UBUNTU new version without a problem.
So, I don know mounting has a problem.
--------------------------------------------------------------------------
as df -h, I found a little strange
and I can check out the same thing at the end of installer log file
according to ur advice.
--------------------------------------------------------------------------

there is no / (root)      when df -h

so, I check again /etc/fstab
I search for the UUID of dev with below command
1) ls /dev/disk/by-uuid/ -alh
2) blkid
there is a mistake at /etc/fstab

fault UUID can be changed and at df-h view /

that problem would be solved.

I am aprreciated for ur hint and advice

God bless with u

2007/10/23, 

IT KIM

---

