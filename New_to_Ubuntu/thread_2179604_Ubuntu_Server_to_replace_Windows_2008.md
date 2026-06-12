---
title: "Ubuntu Server to replace Windows 2008"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by divan-mohr on 2013-10-09
Hi all

I am in the process of replace two of my branch office Windows 2008 servers with Ubuntu Server.
My branch offices are small so they don't require a full Windows domain with all the bells and whistles so I am opting for Ubuntu as I feel I would probably be required to pay less attention to it than I would with Windows.

So what I have..

i7 3770
16GB RAM
2x 500GB HDD
2x 3TB HDD

What I have done up till now is install Ubuntu and configured software raid, the 2x 500GB drives where split in 2 partitions namely 32GB swap and the rest as / and where mirrored the 2x 3TB where left as one large partition and made as /home.
The installation went smooth as silk, IP have been configured, updates ran. 

Now, what I want to achive is to replace my Windows 2008 server, the server is used for DHCP, DNS, file sharing and MySQL so basically all that now needs to go to Ubuntu.. my question is how and is there an easy to use web interface with all those components in one place? 
The file sharing is simple, but, there are multiple sub folders under a certain share that have strict rights assigned to them - can this be done with Ubuntu.. how?
MySQL, our company has developed an application that use MySQL as a back end, the workstations on the network connect to it to retrieve data that has been entered from another workstation. - Is there a management interface for MySQL in Ubuntu similar to that of Windows? Can I backup the MySQL db on windows and just restore it on Ubuntu?

I have read loads of posts and other sites to try achive this and it has just confused me more; I installed Zentyal for the file sharing, DHCP, DNS and AV, that seem to be working nicely however I still have the issue of permissions on sub folders and the larger issue of MySQL

Please assist.

---

### Post by mastablasta on 2013-10-09
phpmyadmin is web tool for administering the database. database is data which should be OS agnostic.

as for permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
also check man pages for commands chown and chmod
there are a lot more options than in windows regarding permissions i believe.

why 32GB swap? it is not necessary to have it so big. but well since you have the disk space i guess it doesn't matter that much.

---

