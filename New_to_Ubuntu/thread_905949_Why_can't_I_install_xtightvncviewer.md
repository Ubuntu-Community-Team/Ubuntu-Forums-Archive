---
title: "Why can't I install xtightvncviewer?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Jheffrey on 2008-08-30
Is this not the command I would use to install it?

> user@Ubuntu:~$ sudo apt-get xtightvncviewer

This is the what I get after return. 

```
E: Invalid operation xtightvncviewer
```

Any thoughts? 

Thanks,



Jheffrey

---

### Post by cariboo on 2008-08-30
Try:

```
sudo apt-get install xtightvncviewer
```

Jim

---

### Post by Jheffrey on 2008-08-30
> **cariboo907 said:**
> Try:

```
sudo apt-get install xtightvncviewer
```

Jim

Thanks, Jim. I feel pretty stupid right now. I have a feeling it wont work, not that you're wrong, but something else. I will post the results in a bit.

---

### Post by Jheffrey on 2008-09-01
Thanks Jim. We are now one step closer to soving the problem. 

```
user@Ubuntu:~$ sudo apt-get install xtightvncviewer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xtightvncviewer
```

The above is what I got after return. 

Could it be due to a possible lack of repositories?

---

### Post by t0p on 2008-09-01
I did a Synaptic search and found xtightvncviewer there, so maybe you are missing the right repository.

According to its Properties in Synaptic, xtightvncviewer is 

> Priority: Optional
Section: Miscellaneous - Graphical (universe)

Maybe someone who knows can tell us: which repo is this likely to be in?

**EDIT:** Try doing

```
sudo apt-get update
```

first.  That might bring it out of hiding.

---

### Post by Jheffrey on 2008-09-01
> **t0p said:**
> I did a Synaptic search and found xtightvncviewer there, so maybe you are missing the right repository.

According to its Properties in Synaptic, xtightvncviewer is 



Maybe someone who knows can tell us: which repo is this likely to be in?

**EDIT:** Try doing

```
sudo apt-get update
```

first.  That might bring it out of hiding.

Thank you, t0p. 

I will try this when I can get to my ubuntu box.

---

### Post by Mister.Vash on 2008-09-01
> Priority: Optional
Section: Miscellaneous - Graphical **(universe)**

Indicates it is in the universe repository.  Since your system couldn't find it, it probably means that you don't have that repository enabled.  To enabled it, open Synaptic package manager, goto Settings -> Repositories and check the option for 'Community-maintained open source software (universe)'

At that point, either click reload in Synaptic to get the updated list of files and then find xtightvncviewer, or go back to the command prompt and do a 'sudo apt-get update' followed by 'sudo apt-get install xtightvncviewer'

---

### Post by Jheffrey on 2008-09-01
> **t0p said:**
> I did a Synaptic search and found xtightvncviewer there, so maybe you are missing the right repository.

According to its Properties in Synaptic, xtightvncviewer is 



Maybe someone who knows can tell us: which repo is this likely to be in?

**EDIT:** Try doing

```
sudo apt-get update
```

first.  That might bring it out of hiding.

Thank you t0p. I ran the command and this was the result:
```
user@Ubuntu:~$ sudo apt-get update
Get:1 http://wine.budgetdedicated.com edgy Release.gpg [191B]                  
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US                                                   
Ign http://flomertens.keo.in edgy Release.gpg                                                                     
Ign http://flomertens.keo.in edgy/main Translation-en_US                                                        
Ign http://flomertens.keo.in edgy/main-all Translation-en_US                                                    
Ign http://security.ubuntu.com edgy-security Release.gpg                                                          
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                               
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                                         
Ign http://us.archive.ubuntu.com edgy Release.gpg                                                                 
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                                                      
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US                                                
Hit http://wine.budgetdedicated.com edgy Release                                                                  
Err http://wine.budgetdedicated.com edgy Release                                                                  
  
Ign http://flomertens.keo.in edgy Release                                                                         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US                                       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                                         
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US                                                
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US                                                  
Ign http://us.archive.ubuntu.com edgy-updates Release.gpg                                                         
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US                                              
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US                                        
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US                                        
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US                                          
Ign http://security.ubuntu.com edgy-security Release                                                              
Ign http://us.archive.ubuntu.com edgy Release                                                                     
Ign http://flomertens.keo.in edgy/main Packages                                                                   
Get:2 http://wine.budgetdedicated.com edgy Release [680B]                                                         
Ign http://wine.budgetdedicated.com edgy Release                                                                  
Ign http://security.ubuntu.com edgy-security/main Packages                                                        
Err http://ntfs-3g.sitesweetsite.info edgy Release.gpg                                                            
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Ign http://us.archive.ubuntu.com edgy-updates Release                                                             
Ign http://flomertens.keo.in edgy/main-all Packages                                                               
Ign http://wine.budgetdedicated.com edgy/main Packages                                                          
Ign http://security.ubuntu.com edgy-security/restricted Packages                                                
Ign http://security.ubuntu.com edgy-security/multiverse Packages                                                  
Ign http://security.ubuntu.com edgy-security/universe Packages                                                    
Ign http://us.archive.ubuntu.com edgy/main Packages                                                             
Ign http://us.archive.ubuntu.com edgy/restricted Packages                                                         
Ign http://us.archive.ubuntu.com edgy/multiverse Packages                                                         
Ign http://us.archive.ubuntu.com edgy/universe Packages                                                           
Err http://flomertens.keo.in edgy/main Packages                                                                   
  404 Not Found
Ign http://wine.budgetdedicated.com edgy/main Sources                                                             
Err http://security.ubuntu.com edgy-security/main Packages                                                        
  404 Not Found
Ign http://us.archive.ubuntu.com edgy-updates/main Packages                                                       
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages                                                 
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Packages                                                 
Ign http://us.archive.ubuntu.com edgy-updates/universe Packages                                                   
Err http://flomertens.keo.in edgy/main-all Packages                                                               
  404 Not Found
Hit http://wine.budgetdedicated.com edgy/main Packages                                                            
Err http://security.ubuntu.com edgy-security/restricted Packages                                                  
  404 Not Found
Err http://security.ubuntu.com edgy-security/multiverse Packages                                                
  404 Not Found
Err http://us.archive.ubuntu.com edgy/main Packages                                                             
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages                                                       
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/multiverse Packages                                                       
  404 Not Found [IP: 91.189.88.45 80]
Hit http://wine.budgetdedicated.com edgy/main Sources                                                           
Err http://security.ubuntu.com edgy-security/universe Packages                                                    
  404 Not Found
Err http://us.archive.ubuntu.com edgy/universe Packages                                                           
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/main Packages                                                       
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages                                                 
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/multiverse Packages                                                 
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/universe Packages                                                   
  404 Not Found [IP: 91.189.88.45 80]
Err http://ntfs-3g.sitesweetsite.info edgy/main Translation-en_US                                                 
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Err http://ntfs-3g.sitesweetsite.info edgy/main-all Translation-en_US                                             
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Ign http://ntfs-3g.sitesweetsite.info edgy Release                                                                
Ign http://ntfs-3g.sitesweetsite.info edgy/main Packages                                                          
Ign http://ntfs-3g.sitesweetsite.info edgy/main-all Packages                                                      
Err http://ntfs-3g.sitesweetsite.info edgy/main Packages                                                          
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Err http://ntfs-3g.sitesweetsite.info edgy/main-all Packages                                                      
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Fetched 871B in 17s (51B/s)                                                                                       
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/Release.gpg  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz  Could not resolve 'ntfs-3g.sitesweetsite.info'
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```




> **Mister.Vash said:**
> Indicates it is in the universe repository.  Since your system couldn't find it, it probably means that you don't have that repository enabled.  To enabled it, open Synaptic package manager, goto Settings -> Repositories and check the option for 'Community-maintained open source software (universe)'

At that point, either click reload in Synaptic to get the updated list of files and then find xtightvncviewer, or go back to the command prompt and do a 'sudo apt-get update' followed by 'sudo apt-get install xtightvncviewer'

Thank you as well Mister.Vash. I have enabled "Community maintained Open Source software (univierse)", but I get this message:
```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

(I think it is the same message as above, but I could be wrong)

and
```

W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
``` 
after clicking reload.

Thanks.

---

### Post by Mister.Vash on 2008-09-02
The gpg error for the wine repositories means that you don't have the public key for them in your key list.  If you want details about how apt works with keys, you can read up on the here:
[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

To fix the issue, you can either remove the wine repositories from your list or you can add their public key in.  Here is the reference on adding it.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Basically, if you want to add the key, just do the following:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo apt-get update

```
Then try installing the program again

---

### Post by Jheffrey on 2008-09-02
> **Mister.Vash said:**
> The gpg error for the wine repositories means that you don't have the public key for them in your key list.  If you want details about how apt works with keys, you can read up on the here:
[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

To fix the issue, you can either remove the wine repositories from your list or you can add their public key in.  Here is the reference on adding it.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Basically, if you want to add the key, just do the following:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo apt-get update

```
Then try installing the program again

Thank you.

I ran ```
sudo wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```, I got OK.

Then I ran ```
sudo apt-get update
``` and this where the results:
```
user@Ubuntu:~$ sudo apt-get update
Get:1 http://wine.budgetdedicated.com edgy Release.gpg [191B]                  
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US                
Ign http://flomertens.keo.in edgy Release.gpg                                  
Ign http://flomertens.keo.in edgy/main Translation-en_US                       
Ign http://flomertens.keo.in edgy/main-all Translation-en_US                   
Ign http://archive.ubuntu.com edgy Release.gpg                                 
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Ign http://security.ubuntu.com edgy-security Release.gpg                       
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Hit http://wine.budgetdedicated.com edgy Release                               
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy-updates Release.gpg                         
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://flomertens.keo.in edgy Release                                      
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy Release                                     
Ign http://security.ubuntu.com edgy-security Release                           
Ign http://wine.budgetdedicated.com edgy/main Packages                         
Ign http://flomertens.keo.in edgy/main Packages                                
Ign http://security.ubuntu.com edgy-security/main Packages                     
Ign http://archive.ubuntu.com edgy-updates Release                             
Hit http://wine.budgetdedicated.com edgy/main Packages                         
Err http://ntfs-3g.sitesweetsite.info edgy Release.gpg                         
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Ign http://flomertens.keo.in edgy/main-all Packages                            
Ign http://security.ubuntu.com edgy-security/restricted Packages               
Ign http://archive.ubuntu.com edgy/main Packages                               
Ign http://archive.ubuntu.com edgy/restricted Packages                         
Ign http://archive.ubuntu.com edgy/multiverse Packages                         
Ign http://security.ubuntu.com edgy-security/multiverse Packages               
Ign http://security.ubuntu.com edgy-security/universe Packages                 
Ign http://archive.ubuntu.com edgy/universe Packages                           
Err http://flomertens.keo.in edgy/main Packages                                
  404 Not Found
Err http://security.ubuntu.com edgy-security/main Packages                     
  404 Not Found
Ign http://archive.ubuntu.com edgy-updates/main Packages                       
Ign http://archive.ubuntu.com edgy-updates/restricted Packages                 
Ign http://archive.ubuntu.com edgy-updates/multiverse Packages                 
Ign http://archive.ubuntu.com edgy-updates/universe Packages                   
Err http://flomertens.keo.in edgy/main-all Packages                            
  404 Not Found
Err http://archive.ubuntu.com edgy/main Packages                               
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/restricted Packages                         
  404 Not Found [IP: 91.189.88.46 80]
Err http://security.ubuntu.com edgy-security/restricted Packages               
  404 Not Found
Err http://archive.ubuntu.com edgy/multiverse Packages                         
  404 Not Found [IP: 91.189.88.46 80]
Err http://security.ubuntu.com edgy-security/multiverse Packages               
  404 Not Found
Err http://archive.ubuntu.com edgy/universe Packages                           
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/main Packages                       
  404 Not Found [IP: 91.189.88.46 80]
Err http://security.ubuntu.com edgy-security/universe Packages                 
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/restricted Packages                 
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/multiverse Packages                 
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/universe Packages                   
  404 Not Found [IP: 91.189.88.46 80]
Err http://ntfs-3g.sitesweetsite.info edgy/main Translation-en_US              
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Err http://ntfs-3g.sitesweetsite.info edgy/main-all Translation-en_US
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Ign http://ntfs-3g.sitesweetsite.info edgy Release
Ign http://ntfs-3g.sitesweetsite.info edgy/main Packages
Ign http://ntfs-3g.sitesweetsite.info edgy/main-all Packages
Err http://ntfs-3g.sitesweetsite.info edgy/main Packages
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Err http://ntfs-3g.sitesweetsite.info edgy/main-all Packages
  Could not resolve 'ntfs-3g.sitesweetsite.info'
Fetched 1B in 59s (0B/s)                      
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/Release.gpg  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://wine.budgetdedicated.com/apt/dists/edgy/Release  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Could not resolve 'ntfs-3g.sitesweetsite.info'
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz  Could not resolve 'ntfs-3g.sitesweetsite.info'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Thank you Mister.Vash!

---

