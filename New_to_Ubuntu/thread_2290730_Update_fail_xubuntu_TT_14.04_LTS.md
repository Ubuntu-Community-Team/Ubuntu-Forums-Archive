---
title: "Update fail xubuntu TT 14.04 LTS"
date: 2015-08-14
forum: New to Ubuntu
---

### Post by fotoflex on 2015-08-14
Hi, lately I get a orange warning triangle on top of the page.
Apparently, the laptop is not up-to-date.
So I follow the instructions and get the message that the laptop now is updated.
Also, I'm told to check my internet connection, which is fine.
But next day, I again get the triangle.
I tried to change to another update source and let it find the best source itself, but nothing changes..
Here is the terminal window result:

```
fotoflex@fotoflex-Toshiba:~$ sudo apt-get update
[sudo] password for fotoflex: 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates InRelease           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports InRelease         
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security InRelease          
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty Release.gpg                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates Release.gpg         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports Release.gpg       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates Release             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports Release           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security Release            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Sources                
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Sources          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex               
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Sources            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease                                  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Sources          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main i386 Packages          
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted i386 Packages    
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe i386 Packages      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse i386 Packages    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Translation-en   
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Translation-en   
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Translation-en     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main Sources        
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release                                    
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted Sources  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe Sources    
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse Sources  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main i386 Packages  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main Translation-en 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main amd64 Packages                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main Sources      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted Sources
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe Sources  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse Sources
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main Translation-en
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages            
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main Sources       
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted Sources 
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe Sources
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse Sources
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe Translation-en
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Translation-en_US
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_US        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en
W: Failed to fetch [http://ppa.launchpad.net/samrog131/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/samrog131/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by ajgreeny on 2015-08-14
That samrog131 ppa repository is no longer active so you will need to remove it from software-sources, then update refresh the repos again and you may find the warning triangle has disappeared.

---

### Post by howefield on 2015-08-14
I'm sure I read recently that the samrog ppa has been removed, but I may be wrong.

In any event, try opening up Software and Updates from the settings menu, then click on the Other Software tab and remove the samrog repository. Reload and you should be able to update your sources without error.

---

### Post by fotoflex on 2015-08-14
Thanks.

I've done all that.
Let's hope the problem is solved.

---

### Post by fotoflex on 2015-08-15
So, it's about seven hours later and not a sign of a sign. :)
I've done a shutdown and a restart to see if that would trigger the problem, but things seem to be okay so far.
If anything changes, I'll let you know.

Thanks, all!

---

### Post by howefield on 2015-08-15
And it will stay way until the next time you break it :)

By the way, here is the thread I alluded to above : [http://ubuntuforums.org/showthread.php?t=2287117](http://ubuntuforums.org/showthread.php?t=2287117)

---

### Post by fotoflex on 2015-08-15
I don't even know what a samrog is, how did I break it? :)

Good avatar, btw, I loved that show...

---

