---
title: "No Update!"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by vagelism on 2012-04-22
Hello since yesterday I see this warning in my task bar!
I have internet connection but it can not take any updates.
What is wrong?
Thank you!

---

### Post by r-senior on 2012-04-22
Have you tried doing what it suggests? The equivalent in a terminal is:

```
sudo apt-get update
```

See if there are any error messages and post them here (preferably not the whole thing) if you don't understand them.

---

### Post by vagelism on 2012-04-22
> **r-senior said:**
> Have you tried doing what it suggests? The equivalent in a terminal is:

```
sudo apt-get update
```

See if there are any error messages and post them here (preferably not the whole thing) if you don't understand them.

```
Ign http://gr.archive.ubuntu.com oneiric InRelease
Ign http://gr.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://gr.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://liveusb.info all InRelease                                          
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://gr.archive.ubuntu.com oneiric Release.gpg                           
Hit http://gr.archive.ubuntu.com oneiric-updates Release.gpg                   
Ign http://dl.google.com stable InRelease                                      
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://dl.google.com stable InRelease                                      
Hit http://gr.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://gr.archive.ubuntu.com oneiric Release                               
Hit http://liveusb.info all Release.gpg                                        
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://gr.archive.ubuntu.com oneiric-updates Release                       
Hit http://gr.archive.ubuntu.com oneiric-backports Release                     
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://liveusb.info all Release                                            
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://gr.archive.ubuntu.com oneiric/main Sources                          
Get:3 http://dl.google.com stable Release.gpg [198 B]                 
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://gr.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://gr.archive.ubuntu.com oneiric/universe Sources                      
Hit http://gr.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://gr.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://gr.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://gr.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://gr.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://gr.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://gr.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://gr.archive.ubuntu.com oneiric/restricted TranslationIndex           
Get:4 http://dl.google.com stable Release [1347 B]                             
Hit http://liveusb.info all/main i386 Packages                                 
Hit http://gr.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://gr.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://gr.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://gr.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://gr.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://gr.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://liveusb.info all/main TranslationIndex                              
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://gr.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://gr.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://gr.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://gr.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://gr.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://gr.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://gr.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://gr.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://gr.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://gr.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://gr.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://gr.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://gr.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://gr.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://gr.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://gr.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://gr.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://gr.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://gr.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://gr.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://gr.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://gr.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://gr.archive.ubuntu.com oneiric-backports/universe Translation-en     
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Get:5 http://dl.google.com stable Release [1338 B]                             
Ign http://liveusb.info all/main Translation-en_US                             
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Get:6 http://dl.google.com stable/main i386 Packages [1229 B]                  
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://liveusb.info all/main Translation-en                                
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:7 http://dl.google.com stable/main i386 Packages [464 B]
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Fetched 4846 B in 3s (1376 B/s)
W: Failed to fetch http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Silent Sam on 2012-04-22
Are you trying to update oneric? I checked one of the links you posted. theres no /oneric subfolder listed. in[FONT=monospace] [/FONT][http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/](http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/)[FONT=monospace]
[/FONT]

---

### Post by vagelism on 2012-04-22
I just added the results of the updade command! The storm was some days ago, so I dont think it has to do with this.

---

### Post by r-senior on 2012-04-22
There's no PPA build for your version of Ubuntu (Oneiric):

[https://launchpad.net/~ferramroberto/+archive/filezilla](https://launchpad.net/~ferramroberto/+archive/filezilla)

You could just remove that PPA entry from your software sources and let it use the standard Oneiric version, which is 3.5.0. It won't downgrade any existing installation of Filezilla so you'll keep 3.5.1 if you already have it. When you upgrade to Precise, you'll get upgraded to 3.5.3.

You can configure your software sources in Software Center: Edit -> Software Sources. Go to the second tab and uncheck the boxes next to that PPA (or remove it). Then try "sudo apt-get update" again.

---

### Post by Silent Sam on 2012-04-22
Sorry about the that. r-senior beat me to the post. It looks like the resource your trying to update from isn't carrying Oneiric any more. you might want to look for another source if its a important update[.]("http://ubuntuforums.org/member.php?u=713779")

---

### Post by vagelism on 2012-04-22
> **r-senior said:**
> There's no PPA build for your version of Ubuntu (Oneiric):

[https://launchpad.net/~ferramroberto/+archive/filezilla](https://launchpad.net/~ferramroberto/+archive/filezilla)

You could just remove that PPA entry from your software sources and let it use the standard Oneiric version, which is 3.5.0. It won't downgrade any existing installation of Filezilla so you'll keep 3.5.1 if you already have it. When you upgrade to Precise, you'll get upgraded to 3.5.3.

You can configure your software sources in Software Center: Edit -> Software Sources. Go to the second tab and uncheck the boxes next to that PPA (or remove it). Then try "sudo apt-get update" again.

Seems to work great now!
Thank you!

---

