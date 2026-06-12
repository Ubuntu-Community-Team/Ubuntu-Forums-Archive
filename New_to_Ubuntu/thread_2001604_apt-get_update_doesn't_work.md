---
title: "apt-get update doesn't work"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-11
Hi,

I have an Ubuntu 12.04 on Amazon AWS. WHen I log into the box, 
it says:  


> 3 packages can be updated.
3 updates are security updates.


When I do```
 sudo apt-get update
``` and ```
sudo apt-get upgrade
```. It goes through all the list. 

But once I exit and come back to the box, it still shows the same message.

Why doesn't it get updated?

---

### Post by mcduck on 2012-06-11
Could you please attach here the complete output from apt-get update" ans "apt-get upgrade" commands?

---

### Post by bhaskar123 on 2012-06-11
hai guys,
          iam new to linux,am using ubuntu 10.10.....
whenever am trying to execute my program i got following error msg...
please give me solution...........


/usr/bin/ld: cannot find -libpthread
/usr/bin/ld: cannot find -lm
/usr/bin/ld: cannot find -lrt
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
make: *** [exe] Error 1
:(

thanks in advance.........

---

### Post by Houmie on 2012-06-11
> **mcduck said:**
> Could you please attach here the complete output from apt-get update" ans "apt-get upgrade" commands?

Sure thanks for your help:

```
3 packages can be updated.
3 updates are security updates.

Get cloud support with Ubuntu Advantage Cloud Guest
  http://www.ubuntu.com/business/services/cloud
ubuntu@ip-xx-xx-xxx-xxx:~$ sudo apt-get update
Ign http://us-east-1.ec2.archive.ubuntu.com precise InRelease
Ign http://us-east-1.ec2.archive.ubuntu.com precise-updates InRelease
Hit http://us-east-1.ec2.archive.ubuntu.com precise Release.gpg
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates Release.gpg
Hit http://us-east-1.ec2.archive.ubuntu.com precise Release
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates Release            
Hit http://us-east-1.ec2.archive.ubuntu.com precise/main Sources               
Hit http://us-east-1.ec2.archive.ubuntu.com precise/universe Sources           
Hit http://us-east-1.ec2.archive.ubuntu.com precise/main amd64 Packages        
Hit http://us-east-1.ec2.archive.ubuntu.com precise/universe amd64 Packages    
Hit http://us-east-1.ec2.archive.ubuntu.com precise/main i386 Packages         
Hit http://us-east-1.ec2.archive.ubuntu.com precise/universe i386 Packages   
Hit http://us-east-1.ec2.archive.ubuntu.com precise/main TranslationIndex    
Hit http://us-east-1.ec2.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/main Sources     
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe Sources 
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us-east-1.ec2.archive.ubuntu.com precise/main Translation-en
Hit http://us-east-1.ec2.archive.ubuntu.com precise/universe Translation-en
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe Translation-en
Ign http://security.ubuntu.com precise-security InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:3 http://security.ubuntu.com precise-security/main Sources [15.7 kB]
Get:4 http://security.ubuntu.com precise-security/universe Sources [4,935 B]
Get:5 http://security.ubuntu.com precise-security/main amd64 Packages [49.6 kB]
Get:6 http://security.ubuntu.com precise-security/universe amd64 Packages [11.6 kB]
Get:7 http://security.ubuntu.com precise-security/main i386 Packages [50.8 kB]
Get:8 http://security.ubuntu.com precise-security/universe i386 Packages [11.6 kB]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 194 kB in 1s (128 kB/s)
Reading package lists... Done

```

```
ubuntu@ip-xx-xx-xxx-xxx:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-image-virtual linux-virtual
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

### Post by Cheesemill on 2012-06-11
To update the kernel you need to do:
```
sudo apt-get dist-upgrade
```

This should update the packages that have been held back

---

### Post by mcduck on 2012-06-11
> **Cheesemill said:**
> To update the kernel you need to do:
```
sudo apt-get dist-upgrade
```

This should update the packages that have been held back

yes, this should work. "upgrade" is not allowed to add new packages, only to replace exisitng ones with a new version. And a kernel upgrade always adds the new kernel alongside of the old one, so a dist-upgrade is required.

---

### Post by Houmie on 2012-06-11
thanks a lot. that worked. :)

---

