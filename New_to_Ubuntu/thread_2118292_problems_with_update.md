---
title: "problems with update"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by Jainvamoo on 2013-02-20
Hi,
i'm relatively new to my Xubuntu, which I'm running on my EeePC. It's much better than the 'Eeebuntu' that was on here originally, but i can't always just fix my problems...help...

Ive had several problems with trying to run 
'sudo apt-get update'
in the terminal.
when i do this, many of the locations it is looking at come up as 
'Err (url)
      Connection failed'
some of the url's that it fails to connect to look fairly important, e.g. 'http://security.ubuntu.com'

how can i make it connect to these locations. i definitely have a internet connection, because most of the locations are fine and don't come up with errors...
Thanks
Jainvamoo

---

### Post by snowpine on 2013-02-20
Welcome to the forums!

Please copy & paste the full output of the "sudo apt-get update" command. The details may seem unimportant to you, but will give the gurus necessary information that will help us help you. :)

---

### Post by Jainvamoo on 2013-02-20
hi,
i can try give you what it's showing so far...its still trying.....

> Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                               
  Connection failed
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                          
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex                                      
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                      
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                      
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                                                         
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                                                   
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                   
  Connection failed
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                         
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                              
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                         
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex 
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en      
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
19% [Waiting for headers] [Waiting for headers]
sorry, this is all i can get at...it won't let me scroll up the page properly...
thanks 
Jainvamoo

---

### Post by Jainvamoo on 2013-02-20
once its finished...ill post the whole output of the command...
thanks
Jainvamoo

---

### Post by Jainvamoo on 2013-02-20
hi,
finally finished...
```
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                               
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                 
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                             
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources/DiffIndex                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages/DiffIndex                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                      
  Connection failed
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                                      
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex                                                      
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex                                                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed InRelease                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                          
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                                                             
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources/DiffIndex                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources/DiffIndex                                       
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg                                                     
  Connection failed
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg                                                   
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources/DiffIndex                                     
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed Release.gpg                                                    
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages/DiffIndex                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages/DiffIndex                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages/DiffIndex                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages/DiffIndex                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed Release                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources/DiffIndex                                                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources/DiffIndex                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources/DiffIndex                                              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources/DiffIndex                                            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages/DiffIndex                                            
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                                                         
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                   
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex                                      
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                               
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                               
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                  
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex                                        
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                          
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                     
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                             
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                    
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex                       
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                        
  Connection failed
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                             
  Bad header line
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_US
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
  Connection failed
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/restricted i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/main i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/multiverse i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/universe i386 Packages
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/main Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/main Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/multiverse Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/multiverse Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/restricted Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/restricted Translation-en
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/universe Translation-en_US
  Unable to connect to localhost:4001:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-proposed/universe Translation-en
  Unable to connect to localhost:4001:
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en_US](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Bad header line

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/main/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/binary-i386/Packages)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en_US](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en_US)  Unable to connect to localhost:4001:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en)  Unable to connect to localhost:4001:

E: Some index files failed to download. They have been ignored, or old ones used instead.
```hope this helps
thanks
Jainvamoo

---

### Post by DuckHook on 2013-02-21
It looks like your mirror site in Great Britain may be down. This problem could be resolved in hours or it may take days.

I would not normally recommend this, but:

1. go to Update Manager>Settings>Ubuntu Software.
2. Click on the "Download from:" dropdown list.
3. Choose: Main Server
4. Close all dialogue boxes
5. Open terminal and do:```
sudo apt-get update
```

You should now be able to update from Ubuntu's main mirror site. This is not a good long-term solution because you are downloading all your updates from across the ocean. As soon as the GB site is back up, you should point your software sources back to your local GB mirror.

If you want to try finding the fastest mirror, then repeat steps 1 & 2 above but instead of choosing "main mirror", choose "other". This opens a further dialogue box, "Choose a Download Server". Click on the "Select Best Server" button. Ubuntu will take a few minutes checking which server yields the best download throughput. It is usually okay to accept the result unless the search returns the main server for GB (which is your current problematic site). Continue with steps 4 & 5.

Please let us know how it goes.

---

### Post by DuckHook on 2013-02-21
Just took a closer look at your second posting. In first post, I'd just assumed they were 403 errors, but you have localhost:4001 errors.

Can you browse? Can you ping gb.archive.canonical.com? Did you install any proxy service or anonymizer like TOR or anon-proxy just before update? Is this a brand-new install or has it been running for some time? If updates initially worked but then stopped, do you remember what system change occurred at that time? Update? New SW? The more details, the better.

Please do:```
cat /etc/hostname
cat /etc/hosts
```...and post output back to this thread.

Your problem may be related to [this]("http://ubuntuforums.org/archive/index.php/t-1088736.html") thread and [this]("http://ubuntuforums.org/archive/index.php/t-1021112.html") thread. On both occasions, the problem was anon-proxy.

---

### Post by Jainvamoo on 2013-02-21
Hi,
here's the results...a little worrying methinks...
> jen@Orthopaedix:~$ cat /ect/hostname
cat: /ect/hostname: No such file or directory
jen@Orthopaedix:~$ cat /ect/hosts
cat: /ect/hosts: No such file or directory
jen@Orthopaedix:~$ 

in answer to your other questions,
ive been running xubuntu for a little while...but no longer than about 6-8months...certainly less than a year...
the only stuff im aware that i have to do with anything proxy related is that on my firefox, i have the settings set to automatically detect proxy settings, because i use my laptop (what im using to post these messages...) at school, where there is a proxy, and at home where there isnt...
ive had a few problems with stuff not updating and a friend, who is far more knowledged in ubuntu than me, and hes fixed them for me...i try to understand as much as possible...
thanks
Jainvamoo

---

### Post by snowpine on 2013-02-21
it's /etc/ not /ect/, try to use copy & paste in the future to avoid typos. :)

---

### Post by Jainvamoo on 2013-02-21
whoops hehe...ill try that again...but at the moment i was trying the changing server bit...its still looking...

---

### Post by DuckHook on 2013-02-21
As I mentioned, my first post was more than likely a misdiagnosis due to not having read your second post (with the more complete info) and therefore my jumping to a wrong conclusion. Most cases where a user cannot access a mirror site is due to the mirror being down. However, the info in your second post points to a different problem. I doubt that changing mirrors is going to make any difference. Your problem is that something has redirected requests to localhost port 4001. It's often proxies that do this sort of thing, ergo question about recently installed proxies. You can wait for the server update to complete, but doubt you will get any different result.

Try looking for *anon-proxy* in synaptic. If it somehow snuck in there, remove it completely.

---

### Post by Jainvamoo on 2013-02-22
hi,
this is the hosts thingmy...
> jen@Orthopaedix:~$ cat /etc/hostname
Orthopaedix
jen@Orthopaedix:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    Orthopaedix

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
jen@Orthopaedix:~$ 
hope this helps :)

---

### Post by Jainvamoo on 2013-02-22
hi, went into synaptic and removed the [italic]anon-proxy[/italic]
what do you suggest i try next, re-run the sudo apt-get update?

---

### Post by DuckHook on 2013-02-22
So, you are confirming that it was somehow installed... I wonder how it got in there?

Anyways, to complete, simply reboot. Afterwards, sudo apt-get update. But you must reboot first to clear proxy.

Let us know how it goes.

<edit>
BTW, your *hosts* and *hostname* files look perfectly fine. Were I a betting man, I would bet that anon-proxy was the culprit.
</edit>

---

### Post by Jainvamoo on 2013-02-22
i ran the *sudo apt-get update* again and heres what i gotted...
```
jen@Orthopaedix:~$ sudo apt-get update
[sudo] password for jen: 
Ign http://dl.google.com stable InRelease
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease                        
Ign http://archive.ubuntu.com precise-backports InRelease                      
Ign http://archive.ubuntu.com precise-security InRelease                       
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://archive.canonical.com precise Release.gpg [198 B]                 
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://archive.ubuntu.com precise-proposed InRelease                       
Hit http://archive.canonical.com precise Release                               
Get:4 http://dl.google.com stable Release [1,347 B]                            
Hit http://extras.ubuntu.com precise Release                                   
Get:5 http://repo.steampowered.com precise InRelease [2,837 B]        
Get:6 http://archive.ubuntu.com precise Release.gpg [198 B]           
Get:7 http://archive.ubuntu.com precise-updates Release.gpg [198 B]      
Get:8 http://archive.ubuntu.com precise-backports Release.gpg [198 B]          
Hit http://archive.canonical.com precise/partner Sources                       
Get:9 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Get:10 http://dl.google.com stable/main i386 Packages [1,217 B]                
Hit http://extras.ubuntu.com precise/main Sources                              
Get:11 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]          
Get:12 http://archive.ubuntu.com precise Release [49.6 kB]                     
Hit http://archive.canonical.com precise/partner i386 Packages                 
Get:13 http://repo.steampowered.com precise/steam Sources [536 B]              
Ign http://dl.google.com stable/main TranslationIndex                          
Get:14 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:15 http://archive.ubuntu.com precise-backports Release [49.6 kB]           
Get:16 http://repo.steampowered.com precise/steam i386 Packages [528 B]        
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Get:17 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Get:18 http://archive.ubuntu.com precise-proposed Release [49.6 kB]            
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:19 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Ign https://private-ppa.launchpad.net precise InRelease                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Ign http://dl.google.com stable/main Translation-en_US                         
Hit https://private-ppa.launchpad.net precise Release                          
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:20 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:21 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Get:22 http://archive.ubuntu.com precise/multiverse Sources [155 kB]           
Get:23 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:24 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:25 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:26 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:27 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:28 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B] 
Get:29 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B] 
Get:30 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]   
Get:31 http://archive.ubuntu.com precise-updates/main Sources [367 kB]         
Get:32 http://archive.ubuntu.com precise-updates/restricted Sources [5,135 B]  
Get:33 http://archive.ubuntu.com precise-updates/universe Sources [79.2 kB]    
Get:34 http://archive.ubuntu.com precise-updates/multiverse Sources [4,725 B]  
Get:35 http://archive.ubuntu.com precise-updates/main i386 Packages [593 kB]   
Get:36 http://archive.ubuntu.com precise-updates/restricted i386 Packages [9,503 B]
Get:37 http://archive.ubuntu.com precise-updates/universe i386 Packages [184 kB]
Get:38 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Get:39 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:40 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:41 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:42 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:43 http://archive.ubuntu.com precise-backports/main Sources [2,422 B]      
Get:44 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]   
Get:45 http://archive.ubuntu.com precise-backports/universe Sources [23.1 kB]  
Get:46 http://archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:47 http://archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:48 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:49 http://archive.ubuntu.com precise-backports/universe i386 Packages [22.8 kB]
Get:50 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:51 http://archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:52 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:53 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:54 http://archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Get:55 http://archive.ubuntu.com precise-security/main Sources [63.1 kB]       
Get:56 http://archive.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:57 http://archive.ubuntu.com precise-security/universe Sources [22.2 kB]   
Get:58 http://archive.ubuntu.com precise-security/multiverse Sources [1,382 B] 
Get:59 http://archive.ubuntu.com precise-security/main i386 Packages [237 kB]  
Get:60 http://archive.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:61 http://archive.ubuntu.com precise-security/universe i386 Packages [69.9 kB]
Get:62 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,368 B]
Get:63 http://archive.ubuntu.com precise-security/main TranslationIndex [74 B] 
Get:64 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:65 http://archive.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:66 http://archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:67 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]
Get:68 http://archive.ubuntu.com precise-proposed/main i386 Packages [38.9 kB] 
Get:69 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [1,449 B]                                        
Get:70 http://archive.ubuntu.com precise-proposed/universe i386 Packages [14.8 kB]                                          
Get:71 http://archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]                                           
Get:72 http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]                                     
Get:73 http://archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]                                     
Get:74 http://archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]                                       
Get:75 http://archive.ubuntu.com precise/main Translation-en [726 kB]                                                       
Get:76 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                                
Get:77 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                                
Get:78 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                                 
Get:79 http://archive.ubuntu.com precise-updates/main Translation-en [260 kB]                                               
Get:80 http://archive.ubuntu.com precise-updates/multiverse Translation-en [5,694 B]                                        
Get:81 http://archive.ubuntu.com precise-updates/restricted Translation-en [2,328 B]                                        
Get:82 http://archive.ubuntu.com precise-updates/universe Translation-en [108 kB]                                           
Get:83 http://archive.ubuntu.com precise-backports/main Translation-en [1,244 B]                                            
Get:84 http://archive.ubuntu.com precise-backports/multiverse Translation-en [1,476 B]                                      
Get:85 http://archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                                         
Get:86 http://archive.ubuntu.com precise-backports/universe Translation-en [16.0 kB]                                        
Get:87 http://archive.ubuntu.com precise-security/main Translation-en [111 kB]                                              
Get:88 http://archive.ubuntu.com precise-security/multiverse Translation-en [995 B]                                         
Get:89 http://archive.ubuntu.com precise-security/restricted Translation-en [978 B]                                         
Get:90 http://archive.ubuntu.com precise-security/universe Translation-en [43.2 kB]                                         
Get:91 http://archive.ubuntu.com precise-proposed/main Translation-en [23.3 kB]                                             
Get:92 http://archive.ubuntu.com precise-proposed/multiverse Translation-en [787 B]                                         
Get:93 http://archive.ubuntu.com precise-proposed/restricted Translation-en [14 B]                                          
Get:94 http://archive.ubuntu.com precise-proposed/universe Translation-en [8,865 B]                                         
Fetched 19.1 MB in 5min 58s (53.3 kB/s)                                                                                     
Reading package lists... Done
jen@Orthopaedix:~$ 
```
seems to have fixed it...
should i leave the server it fetches the data from as *main server* or should i switch it back before i run *sudo apt-get install...*

---

### Post by DuckHook on 2013-02-22
Congrats! You are back up and off to the races. There's still a niggling part of me that wants to know how anon-proxy wormed its way into your system, but let's leave sleeping dogs to lie.

This is a great opportunity to use the extra procedure to find the fastest mirror for your location. I've given those instructions in the last paragraph of post #6.

Good Luck and Happy Xubuntuing!

---

