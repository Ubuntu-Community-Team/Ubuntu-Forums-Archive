---
title: "HELP! cant download software"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by salo_60 on 2008-06-08
im a beginner in this ubuntu thing and i am trying to get a hold of it. but i ran into a snag i cant download sofware. it worked fine for a few days but now its not.

this is wat happens and im using ubuntu 8.04 hardy heron

tyson@tyson-laptop:~$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsnack2 tcl tcl8.4 tcl8.5 tcltls tk8.5
Suggested packages:
  docker sox tclsh wish libsnack2-doc tclreadline
The following NEW packages will be installed:
  amsn libsnack2 tcl tcl8.4 tcl8.5 tcltls tk8.5
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7875kB of archives.
After this operation, 24.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tcl8.4 tcl tcl8.5 libsnack2 tcltls tk8.5 amsn
Install these packages without verification [y/N]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main tcl8.4 8.4.16-4ubuntu1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tcl 8.4.16-1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tcl8.5 8.5.0-2ubuntu1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libsnack2 2.2.10-dfsg1-5
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tcltls 1.5.0.dfsg-6
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tk8.5 8.5.0-3
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe amsn 0.97+final-0ubuntu5
  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltk-defaults/tcl_8.4.16-1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltk-defaults/tcl_8.4.16-1_all.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcl8.5/tcl8.5_8.5.0-2ubuntu1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcl8.5/tcl8.5_8.5.0-2ubuntu1_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2_2.2.10-dfsg1-5_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2_2.2.10-dfsg1-5_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tk8.5/tk8.5_8.5.0-3_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tk8.5/tk8.5_8.5.0-3_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97+final-0ubuntu5_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97+final-0ubuntu5_amd64.deb) 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

---

### Post by powerpleb on 2008-06-08
> **salo_60 said:**
> im a beginner in this ubuntu thing and i am trying to get a hold of it. but i ran into a snag i cant download sofware. it worked fine for a few days but now its not.

this is wat happens and im using ubuntu 8.04 hardy heron

tyson@tyson-laptop:~$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsnack2 tcl tcl8.4 tcl8.5 tcltls tk8.5
Suggested packages:
  docker sox tclsh wish libsnack2-doc tclreadline
The following NEW packages will be installed:
  amsn libsnack2 tcl tcl8.4 tcl8.5 tcltls tk8.5
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7875kB of archives.
After this operation, 24.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tcl8.4 tcl tcl8.5 libsnack2 tcltls tk8.5 amsn
Install these packages without verification [y/N]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main tcl8.4 8.4.16-4ubuntu1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tcl 8.4.16-1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tcl8.5 8.5.0-2ubuntu1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libsnack2 2.2.10-dfsg1-5
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tcltls 1.5.0.dfsg-6
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe tk8.5 8.5.0-3
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe amsn 0.97+final-0ubuntu5
  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltk-defaults/tcl_8.4.16-1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltk-defaults/tcl_8.4.16-1_all.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcl8.5/tcl8.5_8.5.0-2ubuntu1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcl8.5/tcl8.5_8.5.0-2ubuntu1_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2_2.2.10-dfsg1-5_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2_2.2.10-dfsg1-5_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tk8.5/tk8.5_8.5.0-3_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tk8.5/tk8.5_8.5.0-3_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97+final-0ubuntu5_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97+final-0ubuntu5_amd64.deb) 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

Did you try running
```
apt-get update
```
or
```
apt-get --fix-missing
```

---

### Post by cariboo on 2008-06-08
There seems to be a problem with some of the Canadian servers. Just go to System-->Administration-->Software Sources and choose a different server. I'm in BC and I'm using the Main Server with no problems. After changing servers do the:

```
sudo apt-get update
```

You should be good to go.

Jim

---

### Post by salo_60 on 2008-06-08
yes i tried both this is wat happens for the update

tyson@tyson-laptop:~$ sudo apt-get update
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Packages
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Packages
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Fetched 1B in 1s (1B/s)  
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-amd64/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by salo_60 on 2008-06-08
changing the software source worked i just changed it to the main server, thx im new at this, but am getting the hang of it

---

### Post by RequinB4 on 2008-06-08
The canada server is most likely down, as it is prone to do

If there's something you need NOW, try packages.ubuntu.com or archive.ubuntu.com

edit: main server works too, but I make it a principle to try not to leave it on there.

---

