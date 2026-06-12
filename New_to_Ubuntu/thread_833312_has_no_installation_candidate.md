---
title: "has no installation candidate"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Torn on 2008-06-18
I have had my installation of hardy for a few weeks now, and im finding that this install cannot find/install applications that a fresh install can.

Sidenote, just tried to add/remove with a popup that it cannot use all of my repositories.

---

### Post by ibutho on 2008-06-18
Try running Applications -> Accessories -> Terminal and enter
```
sudo aptitude update
```
Does that finish successfully? If not post the error messages and if its successful, try to install an application using aptitude or synaptic.

---

### Post by Torn on 2008-06-18
jason@jason-laptop:~$ sudo aptitude update

[sudo] password for jason: 

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy Release.gpg                                     

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                              

Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                    

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                  

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Translation-en_US                          

Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]              

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US      

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                  

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                 

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US              

Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]                       

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                 

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Translation-en_US                    

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                           

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US                

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US            

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US      

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US        

Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]                

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                     

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                           

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Translation-en_US                      

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                               

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                          

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                                

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                       

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Translation-en_US                    

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                         

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                          

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates Release.gpg                             

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources                          

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Translation-en_US                  

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                         

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Translation-en_US

Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6156B]

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Translation-en_US   

Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [28.0kB]

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports Release.gpg

Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3465B]

Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [15.2kB]      

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Translation-en_US          

Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [906B]       

Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [7291B]           

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Translation-en_US                

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Translation-en_US

Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]

Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [2246B]

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy Release       

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates Release

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports Release

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Packages                             

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Packages                           

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Packages                     

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Sources                      

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Sources                            

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Sources                      

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Sources                        

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Packages                       

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Packages                     

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Packages                   

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Packages                         

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Packages                   

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Packages                     

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Sources                    

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Sources

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Sources

  301 Moved Permanently

Fetched 122kB in 18s (6729B/s)

Reading package lists... Done

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: You may want to run apt-get update to correct these problems

jason@jason-laptop:~$ sudo apt-get update 

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy Release.gpg                                    

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             

Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Translation-en_US                         

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             

Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]                      

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Translation-en_US                   

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Translation-en_US                     

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources                         

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Translation-en_US                   

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates Release.gpg                            

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports Release.gpg

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Translation-en_US

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy Release

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates Release

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports Release

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Packages

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Sources

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Sources                           

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Sources                     

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Sources                       

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Packages                      

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Packages                    

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Packages                  

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Packages                        

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Packages                  

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Packages                    

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Sources                   

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Sources                         

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Sources                   

Ign [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Sources                     

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Packages                                  

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Packages                            

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/restricted Sources                             

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/main Sources                                   

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Sources                             

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Sources                               

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/universe Packages                              

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy/multiverse Packages                            

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Packages                          

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Packages                    

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/restricted Sources                     

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/main Sources                           

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Sources                     

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Sources                       

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/universe Packages                      

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-updates/multiverse Packages                    

  301 Moved Permanently

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Packages                  

  301 Moved Permanently

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                        

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Packages

  301 Moved Permanently

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                   

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Packages            

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Packages

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/restricted Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/main Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/multiverse Sources

  301 Moved Permanently

Err [http://ftp.caliu.info](http://ftp.caliu.info) hardy-backports/universe Sources

  301 Moved Permanently

Fetched 190B in 13s (14B/s)

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/restricted/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/main/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/main/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/multiverse/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/universe/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/universe/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/main/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/main/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  301 Moved Permanently



W: Failed to fetch [http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/dists/hardy-backports/universe/source/Sources.gz)  301 Moved Permanently



E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Hospadar on 2008-06-18
you may want to go into System->Administration->Software sources and pick a different mirror.  Also, be sure to select the universe, multiverse, and restricted repos (and any others you want).

Also, I'd get rid of the CD from your APT list if you have a good internet connection.

After you do that, be sure to update your APT (it should prompt you, if not, use "sudo apt-get update")

As for medibuntu, it sounds like there may be some funny key things going on there, you may want to remove that repo and use the instructions from their website to re-add it.

---

