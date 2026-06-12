---
title: "503  Service Unavailable experienced when trying to update"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by JC1056 on 2013-02-17
I've been experiencing several 503  Service Unavailable [IP: 91.189.91.13 80] when trying to run "sudo apt-get udpate" or when trying to run any installs for anything through the cli.  I'm running 12.04.

Below is an excerpt from my latest update attempt:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
  503  Service Unavailable [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  503  Service Unavailable [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  503  Service Unavailable [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  503  Service Unavailable [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  503  Service Unavailable [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

Has anyone else been experiencing this?

---

### Post by kc1di on 2013-02-17
Hello JC1056 and welcome to Ubuntu,

I've seen quite a few mirrors today that seem to be having problems.
I don't think it's your machine think it's the mirror your using
you can change mirrors by going to software center clicking on edit
and then software sources.  about half way down the box that comes up you'll see a dropdown box called download from click on it and select a different server and try again.

---

### Post by JC1056 on 2013-02-19
Hello kc1di and thank you!
I tried what you advised and at first it seemed like this was going to resolve my issue.  Previously my update would halt at around 63% complete and I would start seeing the first of the errors.  This time it reached 100% and paused there before spitting out the following:
 sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                       
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [8,130 B]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                     
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [10.8 kB]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources     
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages
  503  Service Unavailable [IP: 91.189.92.202 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Fetched 30.9 kB in 19min 46s (26 B/s)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  503  Service Unavailable [IP: 91.189.92.202 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
***Note - I switched from U.S. Server to main server

---

### Post by JC1056 on 2013-02-20
Alright, so I think the issue is resolved now. I ran the select best server tool in the software sources menu. After the tool ran, it automatically selected a server for me in Hungary. I'm assuming since I'm in Afghanistan right now, there was an issue with ttl or possibly something else in trying to reach back to a server in the U.S.
 
After this I ran another apt-get update and the update completed with only two errors this time. I believe they were for precise/main Sources and precise/main i386 Packages. I can now install the programs I was trying to install. 
 
Thanks for the help!

---

