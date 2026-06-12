---
title: "FTP Setting"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by malware7 on 2008-06-05
hello all..
i just want to ask..see the picture below

[IMG]http://img2.freeimagehosting.net/image.php?30f2f5df91.jpg[/IMG]

how to make the user cannot go up the folder (left red arrow)
(the default folder is var/www/html)

because at the momment when i click the up button folder, i'm able to go to the root linux folder...and i can access the folder such root,bin,usr,sys etc...
i want to restrict access to html folder only...plz someone help me

//sorry for poor english

if u cant see the picture,the url is:
[http://img2.freeimagehosting.net/image.php?30f2f5df91.jpg](http://img2.freeimagehosting.net/image.php?30f2f5df91.jpg)

---

### Post by Rocket2DMn on 2008-06-05
What ftp server program are you using?  vsftpd?  proftpd?  Basically what you will need to do is configure the server to lock users in a chroot, which will limit them to subdirectories of their default or assigned directory.

---

### Post by malware7 on 2008-06-05
i'm use proftpd..and have webmin in my server
where/what file should i configure?
and if i want to add ftp user,should i add linux user 1st?

---

### Post by Rocket2DMn on 2008-06-05
There are some nice links on google for setting up proftpd with chroot, for example:
[http://archiv.debianhowto.de/en/proftpd/c_proftpd.html#proftpdkonfig](http://archiv.debianhowto.de/en/proftpd/c_proftpd.html#proftpdkonfig)
This has you create a group called ftpuser, adding all users that can access with ftp to that group, and via the config file you can tell it to use chroot.
The configuration file is called proftpd.conf and should be located at /etc/proftpd.conf

Other good resources are the community wiki and ubuntugeek.com
[https://help.ubuntu.com/community/ProFTPD](https://help.ubuntu.com/community/ProFTPD)
[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

---

### Post by FuturePilot on 2008-06-05
You need to edit the /etc/proftpd/proftpd.conf file.
```
gksudo gedit /etc/proftpd/proftpd.conf
```
Find this line
```
# Use this to jail all users in their homes
DefaultRoot                     /var/www

```
You can change /var/www to whatever directory you want, but I think /var/www is what you want anyway. Save the file and restart the ftp daemon
```
sudo /etc/init.d/proftpd restart
```
Now your user shouldn't be able to go above the www directory

---

### Post by malware7 on 2008-06-05
tq...i try 1st

---

