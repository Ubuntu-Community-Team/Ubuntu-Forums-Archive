---
title: "codec/installation problems on ubuntu 13.04"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by mymoodz on 2013-08-20
i had been thinking of switching over to ubuntu for the last many years but could not do so because i was not one of those people who thought it was a bit difficult one to grasp. I have finally installed it along with windows 7 on my computer. My computer is Dell XPS L502X which is a core i-7 with 8GB ram and 64 bit. i have installed 64-bit Ubuntu 13.04. so far i am not having a very good time because I can not watch any videos on it. the codecs are not there. and i tried to install vlc player but could not do it either. can someone please tell me how to install vlc or similar good player in 13.04 so that i can play my videos. also would it be possible to downgrade my ubuntu to an earlier version? would that solve the problem? or will someone sort out the bugs and stuff in Ubuntu 13.04 because I have tried to install several softwares using the codes avaialble on different websites but have not been able to do so.

---

### Post by SweetAurora on 2013-08-20
You have to install the codecs manually
```
sudo apt-get install ubuntu-restricted-extras
``` 
It's in a grey area when it comes to laws regarding patents and copyrights. Hence why it isn't installed by default. So be sure to check the laws for your country or area to dicerne the leagality of the package and it's contents.

---

### Post by papibe on 2013-08-20
Hi mymoodz.

Open the 'Software Center', look for the following package, and install it:
```
Ubuntu restricted extras
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by mymoodz on 2013-08-20
I put that command in the ternminal. got the following message

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ubuntu-restricted-extras' has no installation candidate
mahmood@mahmood-Dell-System-XPS-L502X:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

:(

---

### Post by mymoodz on 2013-08-20
tried installing Mplayer and here is the message i got:

package dependencies can not be resolved.

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
 details

The following packages have unmet dependencies:

gnome-mplayer: Depends: libasound2 (>= 1.0.16) but 1.0.25-4ubuntu3 is to be installed
               Depends: libc6 (>= 2.7) but 2.17-0ubuntu5 is to be installed
               Depends: libcairo2 (>= 1.2.4) but 1.12.14-0ubuntu1 is to be installed
               Depends: libcurl3-gnutls (>= 7.16.2) but 7.29.0-1ubuntu3.1 is to be installed
               Depends: libgda-5.0-4 (>= 5.0.2) but it is not going to be installed
               Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.28.0-0ubuntu1 is to be installed
               Depends: libglib2.0-0 (>= 2.35.9) but 2.36.0-1ubuntu2 is to be installed
               Depends: libgtk-3-0 (>= 3.0.0) but 3.6.4-0ubuntu8 is to be installed
               Depends: libmusicbrainz3-6 (>= 3.0.2) but it is not going to be installed
               Depends: libnautilus-extension1a (>= 1:2.91) but 1:3.6.3-0ubuntu16 is to be installed
               Depends: libxss1 but it is not going to be installed
               Depends: mplayer but it is not going to be installed

---

### Post by SweetAurora on 2013-08-20
Did you run:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
or use the Ubuntu Updater after installation?

You will have to do either one to update the list of packages that are installable.

---

### Post by mymoodz on 2013-08-20
there was some kind of update after teh installation. it was around 187 MB. before that update, i could not hear anything because my speakers were not working. now the speakers haev been working after that update. it was a big one, as i had earlier said.

---

### Post by mymoodz on 2013-08-20
```
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages                    
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse Translation-en      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages                
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted Translation-en      
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe Translation-en        
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [33.9 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,612 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main Translation-en          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse Translation-en    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted Translation-en    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US      
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main Sources                           
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse i386 Packages
  404  Not Found
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe Translation-en_US
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse i386 Packages
  404  Not Found
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe Translation-en_US
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse i386 Packages
  404  Not Found
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe Translation-en_US
Fetched 374 kB in 39s (9,452 B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
mahmood@mahmood-Dell-System-XPS-L502X:~$ sudo apt-get install gnome-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-mplayer : Depends: libgda-5.0-4 (>= 5.0.2) but it is not installable
                 Depends: libmusicbrainz3-6 (>= 3.0.2) but it is not installable
                 Depends: libxss1 but it is not installable
                 Depends: mplayer2 but it is not installable or
                          mplayer but it is not installable
E: Unable to correct problems, you have held broken packages.
mahmood@mahmood-Dell-System-XPS-L502X:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ubuntu-restricted-extras' has no installation candidate
mahmood@mahmood-Dell-System-XPS-L502X:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ubuntu-restricted-extras' has no installation candidate
mahmood@mahmood-Dell-System-XPS-L502X:~$ sudo apt-get update && sudo apt-get dist-upgrade
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring Release.gpg
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates Release.gpg                                                                                    
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports Release.gpg                                                                                  
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring Release                                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                                                                             
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]                                                                        
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates Release                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                                                                 
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports Release                                                                                      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                            
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release.gpg [198 B]                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                                                                                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                                                                                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                                                                                        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources [37.1 kB]                                                                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free amd64 Packages/DiffIndex                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free amd64 Packages/DiffIndex                                                                     
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources [14 B]                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                                                                                        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources [8,832 B]                                                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages/DiffIndex                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                            
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources [1,825 B]                                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                                                                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages/DiffIndex                                                                      
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main Translation-en                                 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages [97.0 kB]                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                 
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse Translation-en                                                
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted Translation-en                                                
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe Translation-en                                                                                
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages [14 B]                                                              
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages [33.3 kB]                                                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free amd64 Packages                                                                                   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages [3,426 B]                                                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free amd64 Packages                                                                               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [96.2 kB]                                                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages                                                                                    
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main Translation-en                                                                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages                                                                                
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse Translation-en                                                                      
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted Translation-en                                                                      
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe Translation-en                                                                        
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]                                                              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [33.9 kB]                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                                                                                     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,612 B]                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                                                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en                                                                             
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main Translation-en                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                                                                                        
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse Translation-en                                                                    
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted Translation-en                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en                                                                       
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe Translation-en                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en                                                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en_US                                                                                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en                                                                                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en_US                                                                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US                                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US                                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US                                                                      
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main Sources                                                                                           
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse i386 Packages
  404  Not Found
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring/universe Translation-en_US
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse i386 Packages
  404  Not Found
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-updates/universe Translation-en_US
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse Sources
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe i386 Packages
  404  Not Found
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse i386 Packages
  404  Not Found
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) raring-backports/universe Translation-en_US
Fetched 357 kB in 40s (8,826 B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by sandyd on 2013-08-20
Seems like there is an issue with your local ubuntu mirrors.
Try running (makes you use the main Ubuntu Mirrors)
```

sudo sed -i s/pk.archive.ubuntu.com/archive.ubuntu.com/ /etc/apt/sources.list
sudo apt-get update

```

---

### Post by mymoodz on 2013-08-20
sandyd

The first command did not do anything. the second one did download some things.

this is the dialog on the second command
 ```

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg [933 B]                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg [933 B]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg [933 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed Release.gpg [933 B]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release [40.8 kB]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources [37.1 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release.gpg [198 B]                 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources [14 B]    
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release [40.8 kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources [8,832 B]   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                               
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources [1,825 B] 
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release [40.8 kB]            
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages [97.0 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free amd64 Packages/DiffIndex         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free amd64 Packages/DiffIndex     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed Release [40.8 kB]             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages/DiffIndex          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages/DiffIndex      
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages [33.3 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Sources [963 kB]                  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages [3,426 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [96.2 kB] 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free amd64 Packages                   
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [33.9 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free amd64 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,612 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en         
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Sources [5,987 B]           
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Sources [5,838 kB]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en_US            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en               
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Sources [171 kB]            
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages [1,170 kB]         
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages [9,636 B]    
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages [5,396 kB]     
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages [130 kB]     
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages [1,168 kB]          
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages [9,623 B]     
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages [5,405 kB]      
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages [131 kB]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en                       
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en [98.4 kB]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en [3,736 kB]     
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Sources [61.6 kB]         
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Sources [14 B]      
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Sources [70.5 kB]     
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Sources [1,825 B]   
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages [158 kB]   
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages [136 kB]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,426 B]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages [157 kB]    
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages [137 kB]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,612 B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en [75.5 kB]  
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en [1,566 B]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en [14 B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en [72.9 kB]
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Sources [14 B]          
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Sources [14 B]    
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Sources [5,134 B]   
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Sources [1,403 B] 
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main amd64 Packages [14 B]   
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted amd64 Packages [14 B]
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe amd64 Packages [6,249 B]
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse amd64 Packages [1,357 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main i386 Packages [14 B]    
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted i386 Packages [14 B]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe i386 Packages [6,239 B]
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse i386 Packages [1,345 B]
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en [14 B]   
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en [1,040 B]
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en [14 B]
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en [4,983 B]
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe amd64 Packages [21.2 kB]
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main amd64 Packages [37.6 kB] 
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse amd64 Packages [14 B]
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted amd64 Packages [14 B]
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe i386 Packages [21.5 kB]
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main i386 Packages [36.5 kB]  
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse i386 Packages [14 B]
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted i386 Packages [14 B]
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main Translation-en [19.0 kB] 
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse Translation-en [14 B]
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted Translation-en [14 B]
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe Translation-en [8,999 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe Translation-en_US
Fetched 25.8 MB in 4min 32s (94.6 kB/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

---

### Post by mymoodz on 2013-08-20
i think ubuntu restricted extras are getting downloaded right now.

---

### Post by sandyd on 2013-08-20
> **mymoodz said:**
> sandyd

The first command did not do anything. the second one did download some things.

this is the dialog on the second command
 ```

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg [933 B]                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg [933 B]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg [933 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed Release.gpg [933 B]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release [40.8 kB]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources [37.1 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release.gpg [198 B]                 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources [14 B]    
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release [40.8 kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources [8,832 B]   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                               
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources [1,825 B] 
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release [40.8 kB]            
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages [97.0 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free amd64 Packages/DiffIndex         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free amd64 Packages/DiffIndex     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed Release [40.8 kB]             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages/DiffIndex          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages/DiffIndex      
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages [33.3 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Sources [963 kB]                  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages [3,426 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [96.2 kB] 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free amd64 Packages                   
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [33.9 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free amd64 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,612 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en         
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Sources [5,987 B]           
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Sources [5,838 kB]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en_US            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en               
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Sources [171 kB]            
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages [1,170 kB]         
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages [9,636 B]    
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages [5,396 kB]     
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages [130 kB]     
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages [1,168 kB]          
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages [9,623 B]     
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages [5,405 kB]      
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages [131 kB]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en                       
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en [98.4 kB]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en [3,736 kB]     
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Sources [61.6 kB]         
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Sources [14 B]      
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Sources [70.5 kB]     
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Sources [1,825 B]   
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages [158 kB]   
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages [136 kB]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,426 B]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages [157 kB]    
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages [137 kB]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,612 B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en [75.5 kB]  
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en [1,566 B]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en [14 B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en [72.9 kB]
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Sources [14 B]          
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Sources [14 B]    
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Sources [5,134 B]   
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Sources [1,403 B] 
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main amd64 Packages [14 B]   
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted amd64 Packages [14 B]
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe amd64 Packages [6,249 B]
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse amd64 Packages [1,357 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main i386 Packages [14 B]    
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted i386 Packages [14 B]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe i386 Packages [6,239 B]
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse i386 Packages [1,345 B]
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en [14 B]   
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en [1,040 B]
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en [14 B]
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en [4,983 B]
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe amd64 Packages [21.2 kB]
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main amd64 Packages [37.6 kB] 
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse amd64 Packages [14 B]
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted amd64 Packages [14 B]
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe i386 Packages [21.5 kB]
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main i386 Packages [36.5 kB]  
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse i386 Packages [14 B]
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted i386 Packages [14 B]
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main Translation-en [19.0 kB] 
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse Translation-en [14 B]
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted Translation-en [14 B]
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe Translation-en [8,999 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed/universe Translation-en_US
Fetched 25.8 MB in 4min 32s (94.6 kB/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```
First command has no output - Second command is to verify the first command worked

Might also want to run
```

sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
``` after installing
to make Medibuntu show up in the software center and become authenticated (which removes the error at the end)

---

### Post by craig10x on 2013-08-20
Would it not have been better to tell him to use ubuntu software center and just type the words ubuntu restricted...he would have seen it right on the menu and then would have had an easy and smooth install...even the window for mscorefonts would come up and ask him to say yes if he wanted it also installed and then that would have been that....

I don't usually feel comfortable asking someone who just started with ubuntu to start playing with terminal commands, as it is easy to type something in wrong and get all messed up on the install...
i am an old timer with ubuntu and only use terminal when absolutely necessary and even then i copy and paste the command in, to avoid any possible problems ;)

---

### Post by r_avital on 2013-08-20
> **craig10x said:**
> Would it not have been better to tell him to use ubuntu software center and just type the words ubuntu restricted...he would have seen it right on the menu and then would have had an easy and smooth install...
Craig,

The OP was in fact directed to look for ubuntu-restricted-extras in the software center.  This was the output he reported when he tried to install it (post #4 on this thread):
```
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

Seems there's either an issue with communication with his default mirror, or a DRM issue in his country (or both).

---

### Post by craig10x on 2013-08-21
Oops...sorry about that...i must have missed it...:roll:
Thanks for clarifying...if it's the mirror, he might try some others on his software sources to see if they will work better for him...

---

### Post by mymoodz on 2013-08-21
I have done it. the issue is resolved now when i used sandyd's suggestions. vlc player has been installed and it is working fine now. so i can watch movies on it. which is great for me. 

thank you guys.

---

### Post by MrSteve on 2013-08-21
you may require libdvdcss2 ...

this maybe of help
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

