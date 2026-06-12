---
title: "Duplicate Sources List Help"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by darthideut on 2012-09-15
I tried to run  sudo apt-get update on 12.04 and I am getting the duplicate sources error and don't have any idea on how to fix this.  Anyone have any ideas?

```
hayden@hayden-ubuntu:~$ sudo apt-get update
[sudo] password for hayden: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                                                                     
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                                                                                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                                                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                                                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                                                                                                    
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                                                                                                           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                                                                                                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                                                                                                      
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex                                                                               
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex                                                                                
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                                                            
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex                                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex                                                     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                      
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                             
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                                      
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                                                             
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources/DiffIndex                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources/DiffIndex                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources/DiffIndex                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages/DiffIndex                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages/DiffIndex                                        
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                               
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                      
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                              
  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages/DiffIndex                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                        
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [164 kB]                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [42.8 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [51.8 kB]                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]           
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [383 kB]                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [13.5 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B]         
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [161 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [6,755 B]   
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [130 kB]         
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]     
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [388 kB]                                                                                                                                     
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]                                                                                                                              
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [43.8 kB]                                                                                                                                
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,180 B]                                                                                                                              
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [165 kB]                                                                                                                                      
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]                                                                                                                               
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [43.9 kB]                                                                                                                                 
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]                                                                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                                                                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                                                                                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                                                                                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                                                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                                                                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                                                                                                                             
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]                                                                                                                              
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [131 kB]                                                                                                                                 
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [131 kB]                                                                                                                                 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]                                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources/DiffIndex                                                                                                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex                                                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex                                                                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex                                                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages/DiffIndex                                                                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages/DiffIndex                                                                                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages/DiffIndex                                                                                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages/DiffIndex                                                                                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex                                                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex                                                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex                                                                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex                                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                                                                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                                                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                                                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                                                                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                                                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages                                                                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages                                                                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages                                                                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                                                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                                                                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                                                                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                                                                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                                                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                                                                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources                                                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources                                                                                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources                                                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages                                                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages                                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages                                                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages                                                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages                                                                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                                                                                                          
Fetched 1,868 kB in 17s (109 kB/s)                                                                                                                                                                                  
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 6C843CCE8505D44B Launchpad PPA for glennric
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages)
```

---

### Post by Frogs Hair on 2012-09-15
See this thread and use the search filter because there are other threads about this problem. [http://ubuntuforums.org/showthread.php?t=2010871&highlight=duplicate+sources+list](http://ubuntuforums.org/showthread.php?t=2010871&highlight=duplicate+sources+list)

---

### Post by wojox on 2012-09-15
```
sudo cp /etc/apt/sources.list{,.backup}
```
```
sudo rm /etc/apt/sources.list && sudo apt-get update
```

[Duplicate sources.list entry but cannot find the duplicates?]("http://askubuntu.com/a/159371/2973")

---

### Post by darthideut on 2012-09-15
Thanks, guys.  Wojox, I did your solution, but now I'm down to 3 errors with the package lists.

```
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 6C843CCE8505D44B Launchpad PPA for glennric

```

---

### Post by wojox on 2012-09-15
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

This will rebuild the cache !

---

### Post by darthideut on 2012-09-15
> **wojox said:**
> ```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```This will rebuild the cache !
  Thanks, wojox! It fixed it!:guitar:

---

