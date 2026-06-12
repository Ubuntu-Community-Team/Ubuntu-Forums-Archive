---
title: "Can't update: untrusted source: libnspr4-0d"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by waxcan on 2012-03-14
Hi all

I can't get update manger to update.

The error reads:
 
Requires installation of untrusted packages
The action would require the installation of packages from sources that are not authenticated.
Details
libnspr4-0d

Unchecking various boxes hasn't fixed it.



Sudo apt-get update:

```
sudodarren@Linux:~$ sudo apt-get update
[sudo] password for darren: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_AU
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://archive.canonical.com oneiric Release                               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://au.archive.ubuntu.com oneiric InRelease                             
Ign http://au.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://au.archive.ubuntu.com oneiric-backports InRelease
Get:1 http://au.archive.ubuntu.com oneiric Release.gpg [198 B]
Hit http://au.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://au.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://au.archive.ubuntu.com oneiric Release           
Ign http://au.archive.ubuntu.com oneiric Release                               
Hit http://au.archive.ubuntu.com oneiric-updates Release                       
Hit http://au.archive.ubuntu.com oneiric-backports Release                     
Ign http://archive.canonical.com oneiric/partner Translation-en_AU             
Ign http://au.archive.ubuntu.com oneiric/main Sources/DiffIndex                
Ign http://au.archive.ubuntu.com oneiric/restricted Sources/DiffIndex          
Ign http://au.archive.ubuntu.com oneiric/universe Sources/DiffIndex            
Ign http://au.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex          
Ign http://au.archive.ubuntu.com oneiric/main amd64 Packages/DiffIndex         
Ign http://au.archive.ubuntu.com oneiric/restricted amd64 Packages/DiffIndex   
Ign http://au.archive.ubuntu.com oneiric/universe amd64 Packages/DiffIndex     
Ign http://au.archive.ubuntu.com oneiric/multiverse amd64 Packages/DiffIndex   
Ign http://au.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex          
Ign http://au.archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex    
Ign http://au.archive.ubuntu.com oneiric/universe i386 Packages/DiffIndex      
Ign http://au.archive.ubuntu.com oneiric/multiverse i386 Packages/DiffIndex    
Hit http://au.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://au.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://au.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://au.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://au.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://au.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://au.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://au.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://au.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://au.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://au.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://au.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://au.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://au.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://au.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://au.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://au.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://au.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://au.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://au.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://au.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://au.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://au.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://au.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://au.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://au.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://au.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://au.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Hit http://au.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://au.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://au.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://au.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://au.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://au.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://au.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://au.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://au.archive.ubuntu.com oneiric/main Sources                          
Hit http://au.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://au.archive.ubuntu.com oneiric/universe Sources                      
Hit http://au.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://au.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://au.archive.ubuntu.com oneiric/restricted amd64 Packages             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://au.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://au.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://au.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://au.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://au.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://au.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://au.archive.ubuntu.com oneiric/main Translation-en_AU                
Hit http://au.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://au.archive.ubuntu.com oneiric/multiverse Translation-en_AU          
Hit http://au.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://au.archive.ubuntu.com oneiric/restricted Translation-en_AU          
Hit http://au.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://au.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://au.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://au.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://au.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://au.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://au.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://au.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://au.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://au.archive.ubuntu.com oneiric-backports/universe Translation-en     
Ign http://extras.ubuntu.com oneiric InRelease                                 
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://extras.ubuntu.com oneiric/main Translation-en_AU                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Fetched 270 B in 17s (15 B/s)                                                  
W: GPG error: http://au.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Any help much appreciated!

---

### Post by jldoll on 2012-03-14
This has happened to me when libraries for software I installed outside of the repositories has updates that the update manager recognizes. You should have the ability to uncheck each item of the update. Uncheck any item the log throws an error for. All remaining item should then update.  You can then go into synaptic or ubuntu software center and manually update the files that were installed outside the standard repositories.

---

### Post by jldoll on 2012-03-14
My previous response assumes you would use the update manager gui rather than command line.  Alternatively you may be able to individually update libnspr4-0d first through synaptic or software center, then perform a general update from the command line.

---

### Post by waxcan on 2012-03-25
Hi guys, 
Unchecking the box (and unchecking all but one from canical) doesn't work. And I can't install anything from the software centre. It says there was an internet connection error - but the connection is fine.

Any tips? I'm stumped.

---

### Post by oldos2er on 2012-03-25
Try [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by NikTh on 2012-03-25
> **waxcan said:**
> Hi all
```

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Hello,
except the GPG error (follow oldos2er suggestion)

try to disable CD-ROM from software sources. Open Update manager and go to settings , then at "Ubuntu Software" section untick  CD-ROM . Go to terminal and do
```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by waxcan on 2012-04-18
Sorry for the slow update.

I followed instructions on [http://www.ubuntugeek.com/how-to-fix...or-badsig.html](http://www.ubuntugeek.com/how-to-fix...or-badsig.html) and it worked. Uninstalled a few unnecessary apps. The CDROM sources was already disabled.

Thanks all for your help.

---

