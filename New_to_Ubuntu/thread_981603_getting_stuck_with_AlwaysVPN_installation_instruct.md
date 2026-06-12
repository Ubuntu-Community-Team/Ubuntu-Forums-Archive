---
title: "getting stuck with AlwaysVPN installation instructions"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by hanzj on 2008-11-13
hi. I'm trying to install/set-up AlwaysVPN on my system. 


I'm at the part on the short Readme which says:

> ------------------------------------------------------
## Move all config, certificate and key files to
/etc/openvpn/


----------------------------------------------------------(I've pasted the Readme to [http://pastebin.com/m74f35278](http://pastebin.com/m74f35278) . Refer to lines 27 and 28.)

My question: How do I know which/what/where-from "config, certificate, and key files" are to be moved?


 You can download the small tar.gz file at [https://ssl.alwaysvpn.com/downloads/download.php?AlwaysVPN_linux.tar.gz](https://ssl.alwaysvpn.com/downloads/download.php?AlwaysVPN_linux.tar.gz)

---

### Post by Kheops_74 on 2008-11-26
Copy all the file in /etc/openvpn. I'm able to browse the net but it's slow.


Here the files in my directory:

?-desktop:~$ cd /etc/openvpn
?-desktop:/etc/openvpn$ ls -l
total 32
-rw------- 1 root root 1233 2008-11-25 21:33 alwaysvpn_ca.crt
-rw------- 1 root root  757 2008-11-26 21:19 alwaysvpn-tcp-Compatible.conf
-rw------- 1 root root  755 2008-11-26 21:13 alwaysvpn-tcp-Compatible.conf~
-rw------- 1 root root  752 2008-11-25 21:33 alwaysvpn-udp-Faster.conf
-rw------- 1 root root 3782 2008-11-25 21:33 client_grp2.crt
-rw------- 1 root root  887 2008-11-25 21:33 client_grp2.key
-rw-r--r-- 1 root root 2597 2008-11-25 21:33 README.txt
-rwxrwxrwx 1 root root 1352 2008-11-25 21:33 update-resolv-conf
?-desktop:/etc/openvpn$

---

