---
title: "MySQL help needed ASAP"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by rguz10 on 2012-12-21
I cannot install MySQL to my computer. I am using the latest version.
I think this will tell the story.
[http://pastie.org/5563464](http://pastie.org/5563464)

---

### Post by DTSDeveloper on 2012-12-21
i cant see the picture so i dont know what the problem is, but if ur using it for php download lamp

---

### Post by rguz10 on 2012-12-21
Can you click the link?

---

### Post by DTSDeveloper on 2012-12-21
yes but the network im on right now has a webfilter and by default all of those image sharing websites are blocked

---

### Post by steeldriver on 2012-12-21
Based on your link it looks like your initial 'apt-get update' failed because you ran it without sudo - that *may* be why all the subsequent package URLs were not found - it would at least be worth a shot just starting over and using 'sudo apt-get update' at the top

---

### Post by rguz10 on 2012-12-21
ryan@ubuntu:~$ sudo apt-get install mysql-server
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaio1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient18
  libnet-daemon-perl libplrpc-perl libterm-readkey-perl mysql-client-5.5
  mysql-client-core-5.5 mysql-common mysql-server-5.5 mysql-server-core-5.5
Suggested packages:
  libipc-sharedcache-perl tinyca mailx
The following NEW packages will be installed:
  libaio1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient18
  libnet-daemon-perl libplrpc-perl libterm-readkey-perl mysql-client-5.5
  mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5
  mysql-server-core-5.5
0 upgraded, 14 newly installed, 0 to remove and 181 not upgraded.
Need to get 26.1 MB/27.2 MB of archives.
After this operation, 97.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main mysql-common all 5.5.28-0ubuntu0.12.10.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main mysql-common all 5.5.28-0ubuntu0.12.10.1
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main libmysqlclient18 amd64 5.5.28-0ubuntu0.12.10.1
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main mysql-client-core-5.5 amd64 5.5.28-0ubuntu0.12.10.1
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main mysql-client-5.5 amd64 5.5.28-0ubuntu0.12.10.1
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main mysql-server-core-5.5 amd64 5.5.28-0ubuntu0.12.10.1
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main mysql-server-5.5 amd64 5.5.28-0ubuntu0.12.10.1
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main mysql-server all 5.5.28-0ubuntu0.12.10.1
  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-common_5.5.28-0ubuntu0.12.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-common_5.5.28-0ubuntu0.12.10.1_all.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/libmysqlclient18_5.5.28-0ubuntu0.12.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/libmysqlclient18_5.5.28-0ubuntu0.12.10.1_amd64.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-client-core-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-client-core-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-client-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-client-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server-core-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server-core-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server-5.5_5.5.28-0ubuntu0.12.10.1_amd64.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server_5.5.28-0ubuntu0.12.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server_5.5.28-0ubuntu0.12.10.1_all.deb)  404  Not Found [IP: 91.189.92.200 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ryan@ubuntu:~$

---

### Post by rguz10 on 2012-12-21
I just posted it. Sorry for the sorta spam.

---

### Post by DTSDeveloper on 2012-12-21
ur missing packages google a tutorial

---

### Post by rguz10 on 2012-12-21
Google what exactly? I'm not following.

---

### Post by pqwoerituytrueiwoq on 2012-12-21
the op needs to close synatic/wait for another software instillation to finish and run [FONT=Courier New]sudo apt-get update;sudo apt-get install mysql-server[/FONT]

---

### Post by rguz10 on 2012-12-21
Thanks! That worked :D

---

