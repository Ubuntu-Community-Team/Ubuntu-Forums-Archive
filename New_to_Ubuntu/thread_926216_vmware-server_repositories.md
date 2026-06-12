---
title: "vmware-server repositories"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by krisfrajer on 2008-09-21
Ubuntuers,
I am trying to install vmware-server but I cannot get the installation started because it cannot find the vmware-server package. Maybe something wrong with my actual setup of my repositories? I had uncommented the canonical repositories as described in the instalation posting for vmware but that did not work. Any suggestions?
I am running Ubuntu 8.04,
Kris

cristian@NARUTO:~$ sudo apt-get update && sudo apt-get install vmware-server
[sudo] password for cristian: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware-server

---

### Post by spiderbatdad on 2008-09-21
vmware-server is not in the repos. You get it directly from [http://www.vmware.com/](http://www.vmware.com/)
You have to accept a license agreement and get an installation code emailed to you. Alternatively you can try virtual-box from the repos.

In case you are reading an old blog or tutorial, once upon a time, vmware-server was in the repos.

---

### Post by krisfrajer on 2008-09-21
Thxs spiderb for the quick reply. I will do it the other way as you suggested.
Kris

---

