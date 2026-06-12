---
title: "Errors apt-get update"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by iceman1992 on 2012-05-02
When I try to update using the command

```
sudo apt-get update
```There are errors, everytime I do this. Something about cdroms. Why is that? And when I try to check for updates through the update manager, it will download repository informations from several sources then fail at the last second. Can anyone help?

```
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted Translation-en
Ign http://archive.canonical.com precise InRelease                             
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://extras.ubuntu.com precise InRelease                       
Ign http://id.archive.ubuntu.com precise InRelease                   
Ign http://id.archive.ubuntu.com precise-updates InRelease           
Ign http://id.archive.ubuntu.com precise-backports InRelease         
Hit http://archive.canonical.com precise Release.gpg                 
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://extras.ubuntu.com precise Release.gpg                     
Hit http://archive.canonical.com precise Release                     
Hit http://id.archive.ubuntu.com precise Release.gpg                           
Hit http://security.ubuntu.com precise-security Release              
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://security.ubuntu.com precise-security/main Sources         
Hit http://id.archive.ubuntu.com precise-updates Release.gpg         
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex    
Hit http://extras.ubuntu.com precise/main Sources                    
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://id.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://id.archive.ubuntu.com precise Release                               
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://id.archive.ubuntu.com precise-updates Release             
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://id.archive.ubuntu.com precise-backports Release                     
Hit http://id.archive.ubuntu.com precise/main Sources                          
Hit http://id.archive.ubuntu.com precise/restricted Sources                    
Hit http://id.archive.ubuntu.com precise/universe Sources                      
Hit http://id.archive.ubuntu.com precise/multiverse Sources                    
Hit http://id.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://id.archive.ubuntu.com precise/restricted amd64 Packages   
Hit http://id.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://id.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://id.archive.ubuntu.com precise/main i386 Packages
Hit http://id.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://id.archive.ubuntu.com precise/universe i386 Packages      
Hit http://id.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://id.archive.ubuntu.com precise/main TranslationIndex
Hit http://id.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://id.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://id.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://id.archive.ubuntu.com precise-updates/main Sources        
Hit http://id.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://id.archive.ubuntu.com precise-updates/universe Sources    
Hit http://id.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://id.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://id.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://id.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://id.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://id.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://id.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://id.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://id.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://id.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://id.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://id.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://id.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://id.archive.ubuntu.com precise-backports/main Sources      
Hit http://id.archive.ubuntu.com precise-backports/restricted Sources
Hit http://id.archive.ubuntu.com precise-backports/universe Sources
Ign http://archive.canonical.com precise/partner Translation-en_US   
Hit http://id.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://id.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://id.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://id.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://id.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://id.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://id.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://id.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://id.archive.ubuntu.com precise-backports/multiverse i386 Packages
Ign http://archive.canonical.com precise/partner Translation-en      
Hit http://id.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://id.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://id.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://id.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://id.archive.ubuntu.com precise/main Translation-en
Hit http://id.archive.ubuntu.com precise/multiverse Translation-en
Hit http://id.archive.ubuntu.com precise/restricted Translation-en
Hit http://id.archive.ubuntu.com precise/universe Translation-en
Hit http://id.archive.ubuntu.com precise-updates/main Translation-en
Hit http://id.archive.ubuntu.com precise-updates/multiverse Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Hit http://id.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://id.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://id.archive.ubuntu.com precise-backports/main Translation-en
Hit http://id.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://id.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://id.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by cortman on 2012-05-02
I doubt the cdrom is going to do you any good. In a terminal run

```
gksu gedit /etc/apt/sources.list
```

And comment out all the lines referring to cdrom. By comment out, I mean put a hash mark # at the beginning of each line. Save, and run apt-get update again.

---

### Post by wojox on 2012-05-02
Go into Update Manager -> Software Sources and disable the cd-rom section:

---

### Post by iceman1992 on 2012-05-02
Okay, that fixed it. Thank you very much cortman and wojox! :D

---

### Post by cortman on 2012-05-02
Great! Mark this thread [SOLVED] using the thread tools in the upper right. Thanks!

---

