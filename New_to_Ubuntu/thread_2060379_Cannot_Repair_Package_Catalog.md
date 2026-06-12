---
title: "Cannot Repair Package Catalog"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by TDalton on 2012-09-20
Ubuntu 12.04
Asus - U43F

"Items cannot be installed...until package catalog is repaired"

Ok...clicking repair fails. Here is the error:
```
 installArchives() failed: dpkg: error processing libk5crypto3 (--configure): 
 libk5crypto3:amd64 1.10+dfsg~beta1-2ubuntu0.3 cannot be configured because libk5crypto3:i386 is in a different version (1.10+dfsg~beta1-2ubuntu0.1) 
dpkg: error processing libk5crypto3:i386 (--configure): 
 libk5crypto3:i386 1.10+dfsg~beta1-2ubuntu0.1 cannot be configured because libk5crypto3:amd64 is in a different version (1.10+dfsg~beta1-2ubuntu0.3) 
dpkg: dependency problems prevent configuration of libkrb5-3: 
 libkrb5-3 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however: 
  Package libk5crypto3 is not configured yet. 
dpkg: error processing libkrb5-3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgssapi-krb5-2: 
 libgssapi-krb5-2 depends on libk5crypto3 (>= 1.8+dfsg); however: 
  Package libk5crypto3 is not configured yet. 
 libgssapi-krb5-2 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however: 
  Package libkrb5-3 is not configured yet. 
dpkg: error processing libgssapi-krb5-2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgssrpc4: 
 libgssrpc4 depends on libgssapi-krb5-2 (>= 1.10+dfsg~); however: 
  Package libgssapi-krb5-2 is not configured yet. 
dpkg: error processing libgssrpc4 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkadm5srv-mit8No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
: 
 libkadm5srv-mit8 depends on libgssapi-krb5-2 (>= 1.6.dfsg.2); however: 
  Package libgssapi-krb5-2 is not configured yet. 
 libkadm5srv-mit8 depends on libgssrpc4 (>= 1.6.dfsg.2); however: 
  Package libgssrpc4 is not configured yet. 
 libkadm5srv-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however: 
  Package libk5crypto3 is not configured yet. 
 libkadm5srv-mit8 depends on libkrb5-3 (>= 1.9+dfsg~beta1); however: 
  Package libkrb5-3 is not configured yet. 
dpkg: error processing libkadm5srv-mit8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkadm5clnt-mit8: 
 libkadm5clnt-mit8 depends on libgssapi-krb5-2 (>= 1.10+dfsg~); however: 
  Package libgssapi-krb5-2 is not configured yet. 
 libkadm5clnt-mit8 depends on libgssrpc4 (>= 1.6.dfsg.2); however: 
  Package libgssrpc4 is not configured yet. 
 libkadm5clnt-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however: 
  Package libk5crypto3 is not configured yet. 
 libkadm5clnt-mit8 depends on libkrb5-3 (>= 1.8+dfsg); however: 
  Package libkrb5-3 is not configured yet. 
dpkg: error processing libkadm5clnt-mit8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of krb5-multidev: 
 krb5-multidev depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libkrb5-3 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libk5crypto3 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libk5crypto3 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libgssapi-krb5-2 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libgssapi-krb5-2 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libgssrpc4 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libgssrpc4 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libkadm5srv-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libkadm5srv-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libkadm5clnt-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libkadm5clnt-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
dpkg: error processing krb5-multidev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkrb5-dev: 
 libkrb5-dev depends on krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Package krb5-multidev is not configured yet. 
dpkg: error processing libkrb5-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkrb5-3:i386: 
 libkrb5-3:i386 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however: 
  Package libk5crypto3:i386 is not configured yet. 
dpkg: error processing libkrb5-3:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:i386: 
 libgssapi-krb5-2:i386 depends on libk5crypto3 (>= 1.8+dfsg); however: 
  Package libk5crypto3:i386 is not configured yet. 
 libgssapi-krb5-2:i386 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however: 
  Package libkrb5-3:i386 is not configured yet. 
dpkg: error processing libgssapi-krb5-2:i386 (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 libk5crypto3 
 libk5crypto3:i386 
 libkrb5-3 
 libgssapi-krb5-2 
 libgssrpc4 
 libkadm5srv-mit8 
 libkadm5clnt-mit8 
dpkg: dependency problems prevent configuration of krb5-multidev: 
 krb5-multidev depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libkrb5-3 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libk5crypto3 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libk5crypto3 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libgssapi-krb5-2 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libgssapi-krb5-2 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libgssrpc4 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libgssrpc4 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libkadm5srv-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libkadm5srv-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
 krb5-multidev depends on libkadm5clnt-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of libkadm5clnt-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3. 
dpkg: error processing krb5-multidev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: error processing libk5crypto3 (--configure): 
 libk5crypto3:amd64 1.10+dfsg~beta1-2ubuntu0.3 cannot be configured because libk5crypto3:i386 is in a different version (1.10+dfsg~beta1-2ubuntu0.1) 
dpkg: error processing libk5crypto3:i386 (--configure): 
 libk5crypto3:i386 1.10+dfsg~beta1-2ubuntu0.1 cannot be configured because libk5crypto3:amd64 is in a different version (1.10+dfsg~beta1-2ubuntu0.3) 
dpkg: dependency problems prevent configuration of libkadm5srv-mit8: 
 libkadm5srv-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however: 
  Package libk5crypto3 is not configured yet. 
dpkg: error processing libkadm5srv-mit8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkadm5clnt-mit8: 
 libkadm5clnt-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however: 
  Package libk5crypto3 is not configured yet. 
dpkg: error processing libkadm5clnt-mit8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkrb5-dev: 
 libkrb5-dev depends on krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Package krb5-multidev is not configured yet. 
dpkg: error processing libkrb5-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkrb5-3: 
 libkrb5-3 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however: 
  Package libk5crypto3 is not configured yet. 
dpkg: error processing libkrb5-3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkrb5-3:i386: 
 libkrb5-3:i386 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however: 
  Package libk5crypto3:i386 is not configured yet. 
dpkg: error processing libkrb5-3:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgssapi-krb5-2: 
 libgssapi-krb5-2 depends on libk5crypto3 (>= 1.8+dfsg); however: 
  Package libk5crypto3 is not configured yet. 
 libgssapi-krb5-2 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however: 
  Package libkrb5-3 is not configured yet. 
dpkg: error processing libgssapi-krb5-2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:i386: 
 libgssapi-krb5-2:i386 depends on libk5crypto3 (>= 1.8+dfsg); however: 
  Package libk5crypto3:i386 is not configured yet. 
 libgssapi-krb5-2:i386 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however: 
  Package libkrb5-3:i386 is not configured yet. 
dpkg: error processing libgssapi-krb5-2:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgssrpc4: 
 libgssrpc4 depends on libgssapi-krb5-2 (>= 1.10+dfsg~); however: 
  Package libgssapi-krb5-2 is not configured yet. 
dpkg: error processing libgssrpc4 (--configure): 
 dependency problems - leaving unconfigured 

```I have tried to run ```
 sudo apt-get  -f install 
```This produces another error. Here is the result:

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunity6 libqapt-runtime libboost-program-options1.46.1
  akonadi-backend-mysql libqapt1 shared-desktop-ontologies libntrack0
  ntrack-module-libnl-0 libntrack-qt4-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  krb5-multidev libk5crypto3:i386 libkrb5-dev
Suggested packages:
  krb5-doc krb5-doc:i386 krb5-user:i386
The following packages will be upgraded:
  krb5-multidev libk5crypto3:i386 libkrb5-dev
3 upgraded, 0 newly installed, 0 to remove and 302 not upgraded.
11 not fully installed or removed.
Need to get 213 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libkrb5-dev amd64 1.10+dfsg~beta1-2ubuntu0.3 [11.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main krb5-multidev amd64 1.10+dfsg~beta1-2ubuntu0.3 [125 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libk5crypto3 i386 1.10+dfsg~beta1-2ubuntu0.3 [77.4 kB]
Fetched 213 kB in 0s (387 kB/s)      
dpkg: error processing libk5crypto3 (--configure):
 libk5crypto3:amd64 1.10+dfsg~beta1-2ubuntu0.3 cannot be configured because libk5crypto3:i386 is in a different version (1.10+dfsg~beta1-2ubuntu0.1)
dpkg: error processing libk5crypto3:i386 (--configure):
 libk5crypto3:i386 1.10+dfsg~beta1-2ubuntu0.1 cannot be configured because libk5crypto3:amd64 is in a different version (1.10+dfsg~beta1-2ubuntu0.3)
dpkg: dependency problems prevent configuration of libkrb5-3:
 libkrb5-3 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however:
  Package libk5crypto3 is not configured yet.
dpkg: error processing libkrb5-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:
 libgssapi-krb5-2 depends on libk5crypto3 (>= 1.8+dfsg); however:
  Package libk5crypto3 is not configured yet.
 libgssapi-krb5-2 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however:
  Package libkrb5-3 is not configured yet.
dpkg: error processing libgssapi-krb5-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssrpc4:
 libgssrpc4 depends on libgssapi-krb5-2 (>= 1.10+dfsg~); however:
  Package libgssapi-krb5-2 is not configured yet.
dpkg: error processing libgssrpc4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkadm5srv-mit8No apport report written because the error message indicates its a followup error from a previous failure.
             No apport report written because the error message indicates its a followup error from a previous failure.
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             :
 libkadm5srv-mit8 depends on libgssapi-krb5-2 (>= 1.6.dfsg.2); however:
  Package libgssapi-krb5-2 is not configured yet.
 libkadm5srv-mit8 depends on libgssrpc4 (>= 1.6.dfsg.2); however:
  Package libgssrpc4 is not configured yet.
 libkadm5srv-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is not configured yet.
 libkadm5srv-mit8 depends on libkrb5-3 (>= 1.9+dfsg~beta1); however:
  Package libkrb5-3 is not configured yet.
dpkg: error processing libkadm5srv-mit8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkadm5clnt-mit8:
 libkadm5clnt-mit8 depends on libgssapi-krb5-2 (>= 1.10+dfsg~); however:
  Package libgssapi-krb5-2 is not configured yet.
 libkadm5clnt-mit8 depends on libgssrpc4 (>= 1.6.dfsg.2); however:
  Package libgssrpc4 is not configured yet.
 libkadm5clnt-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is not configured yet.
 libkadm5clnt-mit8 depends on libkrb5-3 (>= 1.8+dfsg); however:
  Package libkrb5-3 is not configured yet.
dpkg: error processing libkadm5clnt-mit8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of krb5-multidev:
 krb5-multidev depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libkrb5-3 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libk5crypto3 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libk5crypto3 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libgssapi-krb5-2 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libgssapi-krb5-2 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libgssrpc4 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libgssrpc4 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libkadm5srv-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libkadm5srv-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libkadm5clnt-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libkadm5clnt-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3.
dpkg: error processing krb5-multidev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-dev:
 libkrb5-dev depends on krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Package krb5-multidev is not configured yet.
dpkg: error processing libkrb5-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:i386:
 libkrb5-3:i386 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however:
  Package libk5crypto3:i386 is not configured yet.
dpkg: error processing libkrb5-3:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:i386:
 libgssapi-krb5-2:i386 depends on libk5crypto3 (>= 1.8+dfsg); however:
  Package libk5crypto3:i386 is not configured yet.
 libgssapi-krb5-2:i386 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however:
  Package libkrb5-3:i386 is not configured yet.
dpkg: error processing libgssapi-krb5-2:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libk5crypto3
 libk5crypto3:i386
 libkrb5-3
 libgssapi-krb5-2
 libgssrpc4
 libkadm5srv-mit8
 libkadm5clnt-mit8
 krb5-multidev
 libkrb5-dev
 libkrb5-3:i386
 libgssapi-krb5-2:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Don't know what the hell to do with this. I understand that libk4crypto3 is a package for Kerberos. Do I just remove the packages?

Thanks for any help

---

### Post by GeForce 9500GT on 2012-09-20
Try if this helps:
```
sudo dpkg --configure -a
```

---

### Post by TDalton on 2012-09-20
This was the result of the command:

sudo dpkg --configure -a

```
 dpkg: dependency problems prevent configuration of krb5-multidev:
 krb5-multidev depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libkrb5-3 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libk5crypto3 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libk5crypto3 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libgssapi-krb5-2 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libgssapi-krb5-2 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libgssrpc4 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libgssrpc4 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libkadm5srv-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libkadm5srv-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3.
 krb5-multidev depends on libkadm5clnt-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Version of libkadm5clnt-mit8 on system is 1.10+dfsg~beta1-2ubuntu0.3.
dpkg: error processing krb5-multidev (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libk5crypto3 (--configure):
 libk5crypto3:amd64 1.10+dfsg~beta1-2ubuntu0.3 cannot be configured because libk5crypto3:i386 is in a different version (1.10+dfsg~beta1-2ubuntu0.1)
dpkg: error processing libk5crypto3:i386 (--configure):
 libk5crypto3:i386 1.10+dfsg~beta1-2ubuntu0.1 cannot be configured because libk5crypto3:amd64 is in a different version (1.10+dfsg~beta1-2ubuntu0.3)
dpkg: dependency problems prevent configuration of libkadm5srv-mit8:
 libkadm5srv-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is not configured yet.
dpkg: error processing libkadm5srv-mit8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkadm5clnt-mit8:
 libkadm5clnt-mit8 depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is not configured yet.
dpkg: error processing libkadm5clnt-mit8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-dev:
 libkrb5-dev depends on krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2); however:
  Package krb5-multidev is not configured yet.
dpkg: error processing libkrb5-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:
 libkrb5-3 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however:
  Package libk5crypto3 is not configured yet.
dpkg: error processing libkrb5-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:i386:
 libkrb5-3:i386 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however:
  Package libk5crypto3:i386 is not configured yet.
dpkg: error processing libkrb5-3:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:
 libgssapi-krb5-2 depends on libk5crypto3 (>= 1.8+dfsg); however:
  Package libk5crypto3 is not configured yet.
 libgssapi-krb5-2 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however:
  Package libkrb5-3 is not configured yet.
dpkg: error processing libgssapi-krb5-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:i386:
 libgssapi-krb5-2:i386 depends on libk5crypto3 (>= 1.8+dfsg); however:
  Package libk5crypto3:i386 is not configured yet.
 libgssapi-krb5-2:i386 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.3); however:
  Package libkrb5-3:i386 is not configured yet.
dpkg: error processing libgssapi-krb5-2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssrpc4:
 libgssrpc4 depends on libgssapi-krb5-2 (>= 1.10+dfsg~); however:
  Package libgssapi-krb5-2 is not configured yet.
dpkg: error processing libgssrpc4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 krb5-multidev
 libk5crypto3
 libk5crypto3:i386
 libkadm5srv-mit8
 libkadm5clnt-mit8
 libkrb5-dev
 libkrb5-3
 libkrb5-3:i386
 libgssapi-krb5-2
 libgssapi-krb5-2:i386
 libgssrpc4

```

---

### Post by TDalton on 2012-09-23
Shamelessly bumping this thread.

---

### Post by jerrrys on 2012-09-23
Shamelessly answering bump thread :)

Give this a try:

sudo apt-get clean

sudo apt-get update

---

### Post by jrog on 2012-09-23
If it **still** doesn't work after trying what jerrrys said, try these commands (yep, all of them, some of which you've already tried, but let'st just be thorough):

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get dist-upgrade
```If that **still** doesn't work, try:

```
sudo apt-get purge libk5crypto3 libk5crypto3:i386 libkrb5-3 libgssapi-krb5-2 libgssrpc4 libkadm5srv-mit8 libkadm5clnt-mit8 krb5-multidev libkrb5-dev libkrb5-3:i386 libgssapi-krb5-2:i386
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```If that didn't work, my question is: have you been installing packages from other sources without using apt-get? If so (or if you're just not sure), try this command:

```
sudo dpkg --remove --force-remove-reinstreq libk5crypto3 libk5crypto3:i386 libkrb5-3 libgssapi-krb5-2 libgssrpc4  libkadm5srv-mit8 libkadm5clnt-mit8 krb5-multidev libkrb5-dev  libkrb5-3:i386 libgssapi-krb5-2:i386
```and then ```
sudo apt-get update && sudo apt-get dist-upgrade
```If you're still having issues at this point, post again to say so. :)

---

### Post by TDalton on 2012-09-24
Hey thanks y'all. 

Here is the result of the command:
```
sudo dpkg --remove --force-remove-reinstreq libk5crypto3 libk5crypto3:i386 libkrb5-3 libgssapi-krb5-2 libgssrpc4  libkadm5srv-mit8 libkadm5clnt-mit8 krb5-multidev libkrb5-dev  libkrb5-3:i386 libgssapi-krb5-2:i386

```

```
dpkg: dependency problems prevent removal of libk5crypto3:
 libkdb5-6 depends on libk5crypto3 (>= 1.7+dfsg); however:
  Package libk5crypto3 is to be removed.
 samba-common-bin depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is to be removed.
 smbclient depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is to be removed.
 libsmbclient depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is to be removed.
 winbind depends on libk5crypto3 (>= 1.6.dfsg.2); however:
  Package libk5crypto3 is to be removed.
dpkg: error processing libk5crypto3 (--remove):
 dependency problems - not removing
(Reading database ... 350037 files and directories currently installed.)
Removing libk5crypto3:i386 ...
dpkg: dependency problems prevent removal of libkrb5-3:
 cups depends on libkrb5-3 (>= 1.6.dfsg.2); however:
  Package libkrb5-3 is to be removed.
 libkdb5-6 depends on libkrb5-3 (>= 1.7dfsg); however:
  Package libkrb5-3 is to be removed.
 samba-common-bin depends on libkrb5-3 (>= 1.10+dfsg~); however:
  Package libkrb5-3 is to be removed.
 evolution-exchange depends on libkrb5-3 (>= 1.6.dfsg.2).
 smbclient depends on libkrb5-3 (>= 1.10+dfsg~); however:
  Package libkrb5-3 is to be removed.
 libsmbclient depends on libkrb5-3 (>= 1.10+dfsg~); however:
  Package libkrb5-3 is to be removed.
 winbind depends on libkrb5-3 (>= 1.10+dfsg~); however:
  Package libkrb5-3 is to be removed.
 dnsutils depends on libkrb5-3 (>= 1.6.dfsg.2).
dpkg: error processing libkrb5-3 (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libgssapi-krb5-2:
 cups depends on libgssapi-krb5-2 (>= 1.8+dfsg).
 libdns81 depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 openssh-client depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 libcamel-1.2-29 depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 samba-common-bin depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 libgnomevfs2-extra depends on libgssapi-krb5-2 (>= 1.7+dfsg).
 libcurl3 depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 smbclient depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 libcups2 depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 libsmbclient depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 libneon27-gnutls depends on libgssapi-krb5-2 (>= 1.7+dfsg).
 libcurl3-nss depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 winbind depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
 libcurl3-gnutls depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
dpkg: error processing libgssapi-krb5-2 (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libgssrpc4:
 libkdb5-6 depends on libgssrpc4 (>= 1.7dfsg~alpha1).
dpkg: error processing libgssrpc4 (--remove):
 dependency problems - not removing
Removing libkadm5srv-mit8 ...
Removing libkadm5clnt-mit8 ...
Removing krb5-multidev ...
dpkg: dependency problems prevent removal of libkrb5-dev:
 libcups2-dev depends on libkrb5-dev.
dpkg: error processing libkrb5-dev (--remove):
 dependency problems - not removing
Removing libkrb5-3:i386 ...
dpkg: dependency problems prevent removal of libgssapi-krb5-2:i386:
 libcups2:i386 depends on libgssapi-krb5-2 (>= 1.10+dfsg~).
dpkg: error processing libgssapi-krb5-2:i386 (--remove):
 dependency problems - not removing
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libk5crypto3
 libkrb5-3
 libgssapi-krb5-2
 libgssrpc4
 libkrb5-dev
 libgssapi-krb5-2:i386

```

I tried all the commands. Tried to remove the packages and then did 'apt-get update'.
The software center still had errors. Attempts to fix it gave this result:

```
installArchives() failed: dpkg: dependency problems prevent configuration of libkrb5-dev: 
 libkrb5-dev depends on krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2); however: 
  Version of krb5-multidev on system is 1.10+dfsg~beta1-2ubuntu0.3. 
dpkg: error processing libkrb5-dev (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 libkrb5-dev 

```

---

### Post by jrog on 2012-09-24
Can you please post the contents of /etc/apt/sources.list here? Also, are you using any PPAs? Finally, can you say a bit about what you were doing prior to encountering this message? For example, have you manually installed .deb packages from non-Ubuntu sources, or that sort of thing? (I ask because, in some of the error messages, it is saying that you have packages on your system that are newer than those in the repos.)

---

### Post by TDalton on 2012-09-24
I usually dont try to install anything without the software center, since I don't know how to fully use Ubuntu linux and wouldn't want to **** it up. I was trying to install some stuff for customizing Gnome3, but I wouldn't understand how that is connected to this problem.


/etc/apt/sources.list
```
 # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.umd.edu/ubuntu/ precise main restricted
deb-src http://mirror.umd.edu/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.umd.edu/ubuntu/ precise-updates main restricted
deb-src http://mirror.umd.edu/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.umd.edu/ubuntu/ precise universe
deb-src http://mirror.umd.edu/ubuntu/ precise universe
deb http://mirror.umd.edu/ubuntu/ precise-updates universe
deb-src http://mirror.umd.edu/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.umd.edu/ubuntu/ precise multiverse
deb-src http://mirror.umd.edu/ubuntu/ precise multiverse
deb http://mirror.umd.edu/ubuntu/ precise-updates multiverse
deb-src http://mirror.umd.edu/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://mirror.umd.edu/ubuntu/ precise-security main restricted
deb-src http://mirror.umd.edu/ubuntu/ precise-security main restricted
deb http://mirror.umd.edu/ubuntu/ precise-security universe
deb-src http://mirror.umd.edu/ubuntu/ precise-security universe
deb http://mirror.umd.edu/ubuntu/ precise-security multiverse
deb-src http://mirror.umd.edu/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu precise main # disabled on upgrade to precise
```

---

### Post by jrog on 2012-09-24
Thanks. I can see that you upgraded from Natty. Does this mean that upgraded from Natty directly to Precise? 

Also, do you have any idea why the system wants to install these development packages, like krb5-multidev, in the first place? Are you building applications that have to work with Kerberos? I see that you have -dev packages for CUPS, too -- are you developing/compiling applications that have to work with CUPS? It looks like there's a lot of oddness going on here.

---

### Post by jrog on 2012-09-24
Here's another option for you to try out, but it's a bit more drastic than the stuff we've tried so far (in case you're losing patience).

At the command line:

```
sudo rm -f /var/lib/apt/lists/*
sudo mv /var/lib/dpkg/{status,status-bad}
sudo cp /var/lib/dpkg/{status-old,status}
sudo apt-get update
sudo apt-get dist-upgrade

```

This will delete any package lists you have stored on the system, and it will revert dpkg's package status list back to an old version. You may then be able to get things back on track.

A next step, if that still doesn't work, is to manually go through /var/lib/dpkg/status and delete the sections for the broken packages, then update and dist-upgrade again. But hopefully it won't come to that, as editing that file is a bit dangerous.

---

### Post by TDalton on 2012-09-24
Thanks for the response. Naw, I'm not losing patience here, just worried that y'all are going to leave me in the dust!

For the ```
sudo rm -f /var/lib/apt/lists/*
```

I get 
```
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

```

Don't know what I'm doing wrong.

As far as the other questions go, I'm not trying to compile anything with kerberos. I didn't even know what the heck it was until it started acting a fool...

---

### Post by jrog on 2012-09-25
> **TDalton said:**
> Thanks for the response. Naw, I'm not losing patience here, just worried that y'all are going to leave me in the dust!

For the ```
sudo rm -f /var/lib/apt/lists/*
```I get 
```
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

```Don't know what I'm doing wrong.

As far as the other questions go, I'm not trying to compile anything with kerberos. I didn't even know what the heck it was until it started acting a fool...
The error with 'var/lib/apt/lists/partial' shouldn't matter; continue with the rest of the commands.

---

### Post by TDalton on 2012-09-26
```
krb5-multidev
```
Is still ******* with me. All other dependency problems are handled
```
The following packages have unmet dependencies:
 libkrb5-dev : Depends: krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by HiImTye on 2012-09-26
> libkrb5-dev : Depends: krb5-multidev ([COLOR=DarkRed]**=**[/COLOR] 1.10+dfsg~beta1-2ubuntu0.[COLOR=DarkRed]**2**[/COLOR]) but 1.10+dfsg~beta1-2ubuntu0.[COLOR=DarkRed]**3**[/COLOR] is installed

the problem is that it depends on a *specific* version of that package, not a version greater than. download and install the specific version and it should work

---

### Post by jrog on 2012-09-26
> **TDalton said:**
> ```
krb5-multidev
```Is still ******* with me. All other dependency problems are handled
```
The following packages have unmet dependencies:
 libkrb5-dev : Depends: krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
E: Unmet dependencies. Try using -f.

```
Well, it's great that we're making progress! What HilmTye suggested above may work (that is, you may be able to download the specific version it is requesting after the '=' sign and install it to fix the problem), but there are other things you might try first. Remember the earlier commands that we tried to remove various packages? They are much more likely to work now that only one package is having problems, so you might try them again. To be thorough, here's what I'd try (**stopping** if one of the earlier ones in this list seems to work, and **continuing** through them all even if an earlier one fails):

```
sudo apt-get update
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get purge libkrb5-dev
sudo dpkg --remove --force-remove-reinstreq libkrb5-dev
sudo apt-get install libkrb5-dev=1.10+dfsg~beta1-2ubuntu0.2
```After this, try to 'sudo apt-get update' and 'sudo apt-get dist-upgrade' (both without quotes). If none of that works, then you may have to try manually downloading the specific .deb and installing it. That might bring problems of its own, so we'll see -- I think it should be a resort after trying the above.

---

### Post by TDalton on 2012-09-27
I have tried all the above commands.

```
sudo apt-get purge libkrb5-dev
```
So, I can't purge libkrb5-dev.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libcups2-dev : Depends: libkrb5-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So libcups2-dev depends on libkrb5-dev?

Same problem arises with ```
sudo dpkg --remove --force-remove-reinstreq libkrb5-dev
```

```
dpkg: dependency problems prevent removal of libkrb5-dev:
 libcups2-dev depends on libkrb5-dev.
dpkg: error processing libkrb5-dev (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libkrb5-dev

```

```
 sudo apt-get install libkrb5-dev=1.10+dfsg~beta1-2ubuntu0.2

```
output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libkrb5-dev is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libkrb5-dev : Depends: krb5-multidev (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by jrog on 2012-09-27
> **TDalton said:**
> I have tried all the above commands.

```
sudo apt-get purge libkrb5-dev
```So, I can't purge libkrb5-dev.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libcups2-dev : Depends: libkrb5-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```So libcups2-dev depends on libkrb5-dev?
```
sudo apt-get purge libcups2-dev libkrb5-dev
```

---

### Post by HiImTye on 2012-09-28
> **TDalton said:**
> libkrb5-dev : Depends: krb5-multidev (= **1.10+dfsg~beta1-2ubuntu0.2**) but 1.10+dfsg~beta1-2ubuntu0.3 is to be installed
[/CODE]
install that package first, repeat with any new packages that pop up.

---

### Post by jrog on 2012-09-28
> **HiImTye said:**
> install that package first, repeat with any new packages that pop up.
As I mentioned before, this remains an option for you, OP. However, the -dev packages probably should not be on your system in the first place (unless you are compiling/building software yourself), in which case it is probably best to simply remove them (see my above suggestion about purging **both** libcups2-dev and libkrb5-dev). If that doesn't work for some reason, though, then trying to install the specific package listed in the error message would likely fix the problem (assuming that this specific package doesn't have dependency issues of its own! -- that's perhaps another reason to avoid trying to install it manually as the first option).

---

### Post by TDalton on 2012-10-01
[IMG]http://i.imgur.com/Tpjrg.gif[/IMG]
touche, sir, touche.

---

### Post by jrog on 2012-10-02
Great that it worked out! Which part was the final step? :)

---

### Post by fsears on 2012-11-24
What was the solution exactly?

---

