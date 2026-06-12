---
title: "problem in intalling R- program in ubuntu 10.04"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by ngchandrasekhar on 2013-05-16
I tried to install R- program in my ubuntu 10.04.. but after that i tried to update using sudo apt- get update that  I am have the following problem. please help me to sort it out. Thank you
sekhar@sekhar-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_IN              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg [198B]  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Ign [http://cran.r-project.org](http://cran.r-project.org) lucid/ Release.gpg                               
Ign [http://cran.r-project.org/mirrors.html/bin/linux/ubuntu/](http://cran.r-project.org/mirrors.html/bin/linux/ubuntu/) lucid/ Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Ign [http://cran.r-project.org](http://cran.r-project.org) lucid/ Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://cran.r-project.org](http://cran.r-project.org) lucid/ Packages                                  
Ign [http://cran.r-project.org](http://cran.r-project.org) lucid/ Packages                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [481kB]          
Err [http://cran.r-project.org](http://cran.r-project.org) lucid/ Packages                               
  404  Not Found
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release [58.3kB]           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources                      
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages [672kB]         
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [234kB]           
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B]  
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources [329kB]         
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [146kB]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [45.4kB]     
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]  
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages [294kB]    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,366B]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,347B]   
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources [109kB]     
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources [5,817B]  
Fetched 2,462kB in 36s (67.3kB/s)                                              
W: Failed to fetch [http://cran.r-project.org/mirrors.html/bin/linux/ubuntu/lucid/Packages.gz](http://cran.r-project.org/mirrors.html/bin/linux/ubuntu/lucid/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead

---

### Post by Lars Noodén on 2013-05-16
That would be because [support for 10.04 (lucid) on the Desktop ended last week](https://wiki.ubuntu.com/Releases) on the 9th. There won't be any software or security updates coming for that release any more.

The short answer is that you'll have to upgrade.  You'll probably want to try the Live DVD first before upgrading to be sure you like the changes.  If not, you can try the Live discs for Xubuntu, Kubuntu or Lubuntu and then take the one that suits you best.

---

### Post by Lars Noodén on 2013-05-16
Just to get you through to the end of the week, you might be able point your sources file to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) where the lucid packages now reside.  But please put it next on your list to upgrade to 12.04 LTS because the old distro is unsupported and will not be patched or updated.

---

### Post by papibe on 2013-05-16
Hi ngchandrasekhar. Welcome to the forum ):P

Ubuntu 10.04 has reached EOL. I think either upgrading or installing a new version may be the easiest way so solve your problem.

Having said that, I noticed that this is the wrong URL to download the package:
```
http://cran.r-project.org/mirrors.html/bin/linux/ubuntu/lucid/Packages.gz
```
If you go to the Cran-R proyect you would notice the the proper URL is:
```
http://cran.r-project.org/bin/linux/ubuntu/lucid/Packages.gz
```
I'd start checking your source files. Could you post the result of this command?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by ngchandrasekhar on 2013-05-18
> **papibe said:**
> Hi ngchandrasekhar. Welcome to the forum ):P

Ubuntu 10.04 has reached EOL. I think either upgrading or installing a new version may be the easiest way so solve your problem.

Having said that, I noticed that this is the wrong URL to download the package:
```
http://cran.r-project.org/mirrors.html/bin/linux/ubuntu/lucid/Packages.gz
```
If you go to the Cran-R proyect you would notice the the proper URL is:
```
http://cran.r-project.org/bin/linux/ubuntu/lucid/Packages.gz
```
I'd start checking your source files. Could you post the result of this command?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.
Thank you very much.. It was very helpful But after installation of  R as you said from cran some warning is comming while updating using sedo get apt- update. The following warning is there.. hope you can help me again... Thank you with regards.
W: GPG error: [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/ Release: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY 51716619E084DAB9
W: Duplicate sources.list entry  [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages  (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages

---

### Post by ngchandrasekhar on 2013-05-18
Thank you very much.. It was very helpful But after installation of  R  as you said from cran some warning is comming while updating using sedo  get apt- update. The following warning is there.. hope you can help me  again... Thank you with regards.
> W: GPG error: [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in)  lucid/ Release: The following  signatures couldn't be verified because  the public key is not available:  NO_PUBKEY 51716619E084DAB9
W: Duplicate sources.list entry  [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages  (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_b  inary-i386_Packages

---

