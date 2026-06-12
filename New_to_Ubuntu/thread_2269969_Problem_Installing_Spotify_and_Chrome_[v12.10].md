---
title: "Problem Installing Spotify and Chrome [v12.10]"
date: 2015-03-19
forum: New to Ubuntu
---

### Post by jonathan76 on 2015-03-19
I'm new to Ubuntu and I was trying to install Chrome, but this happens:

[IMG]http://i.imgur.com/0zLURAZ.png[/IMG]


Same to Spotify, I followed the instructions and  this is what happens after sudo apt-get update:

> ~$ sudo apt-get update
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal InRelease                             
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports InRelease                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal Release.gpg                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Sources                      
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates Release.gpg                   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal Release                               
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates Release                       
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports Release                     
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en             
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources                   
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/main Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/restricted Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/universe Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/multiverse Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/main amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/restricted amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/universe amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/multiverse amd64 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/main i386 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/restricted i386 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/universe i386 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/multiverse i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/main Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/restricted Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal/universe Translation-en
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/main Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/restricted Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/universe Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/multiverse Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/main amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/restricted amd64 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/universe amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/main i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/restricted i386 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/universe i386 Packages
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
  404  Not Found
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-updates/universe Translation-en
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/main Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/restricted Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/universe Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/multiverse Sources
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/main amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/universe amd64 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/main i386 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/restricted i386 Packages
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/universe i386 Packages
  404  Not Found
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
  404  Not Found
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) quantal-backports/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Fetched 1,617 B in 18s (85 B/s)
W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.



Any help?

---

### Post by dino99 on 2015-03-19
quantal is fully dead since awhile; install either  'trusty' 'utopic' or the coming 'vivid'

[http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04/](http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04/)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This needs to be a fresh installation

---

