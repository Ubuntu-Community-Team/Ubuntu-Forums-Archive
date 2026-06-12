---
title: "Debian package installer has stopped working"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Beth1957 on 2008-10-23
[COLOR="Navy"][SIZE="3"]I've managed to bodge up my system (HH 8.04) somehow lately & have a few programmes misbehaving (I just can't resist fiddling <sigh>. Craving your indulgence, I'll post them separately. As a comparative noob trying to learn I'd be grateful for any help to get me going in the right direction!

I've downloaded a couple of different .deb files lately but when I've tried to open them (with Debian Package Installer, as usual nothing happens. Gdebi doesn't work either.
And because of the fiddling I've done while trying to fix that, Debian Package Installer doesn't even appear on the "open with other application" menu any more... help! ](*,)[/SIZE][/COLOR]

---

### Post by gimlithedwarf on 2008-10-23
Could you please go to applications->accessories->terminal
and type:
```
sudo apt-get update
```
to help us figure out how to help you?

---

### Post by Duck2006 on 2008-10-23
What happens when you double click on the deb pack?

---

### Post by Beth1957 on 2008-10-23
> **Duck2006 said:**
> What happens when you double click on the deb pack?

Nothing at all :(

---

### Post by Beth1957 on 2008-10-23
> **gimlithedwarf said:**
> Could you please go to applications->accessories->terminal
and type:
```
sudo apt-get update
```
to help us figure out how to help you?

Right, done that... output as follows :-
```
liz@liz-laptop:~$ sudo apt-get update
Hit http://apt.last.fm debian Release.gpg                                      
Ign http://apt.last.fm debian/stable Translation-en_GB                         
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_GB               
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Hit http://archive.ubuntu.com hardy Release.gpg                                
Get: 1 http://archive.ubuntu.com hardy/main Translation-en_GB [19.6kB]         
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_GB               
Hit http://apt.last.fm debian Release                                          
Hit http://archive.canonical.com hardy Release                                 
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Hit http://wine.budgetdedicated.com hardy Release                              
Get: 2 http://ppa.launchpad.net hardy Release [27.6kB]                         
Get: 3 http://ppa.launchpad.net hardy Release [27.6kB]                         
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                 
Get: 4 http://archive.ubuntu.com hardy/restricted Translation-en_GB [1956B]    
Get: 5 http://archive.ubuntu.com hardy/universe Translation-en_GB [4368B]      
Get: 6 http://archive.ubuntu.com hardy/multiverse Translation-en_GB [36.1kB]   
Ign http://apt.last.fm debian/stable Packages                                  
Get: 7 http://ppa.launchpad.net hardy Release [27.6kB]                         
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_GB             
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_GB       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_GB         
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_GB       
Hit http://archive.ubuntu.com hardy-security Release.gpg                       
Ign http://archive.ubuntu.com hardy-security/main Translation-en_GB            
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_GB      
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_GB        
Ign http://packages.medibuntu.org hardy/non-free Translation-en_GB             
Hit http://apt.wicd.net hardy Release.gpg                                      
Ign http://apt.wicd.net hardy/extras Translation-en_GB                         
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://apt.last.fm debian/stable Packages                                  
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Packages                               
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://packages.medibuntu.org hardy Release                                
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Packages                               
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_GB      
Hit http://archive.ubuntu.com hardy Release    
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-security Release
Hit http://apt.wicd.net hardy Release                                          
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/restricted Packages                        
Hit http://archive.ubuntu.com hardy/main Sources                               
Hit http://packages.medibuntu.org hardy/non-free Packages            
Hit http://archive.ubuntu.com hardy/restricted Sources                         
Hit http://archive.ubuntu.com hardy/universe Packages                          
Hit http://archive.ubuntu.com hardy/universe Sources                           
Hit http://archive.ubuntu.com hardy/multiverse Packages                        
Hit http://archive.ubuntu.com hardy/multiverse Sources                         
Hit http://archive.ubuntu.com hardy-updates/main Packages                      
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                
Hit http://archive.ubuntu.com hardy-updates/main Sources                       
Hit http://archive.ubuntu.com hardy-updates/restricted Sources                 
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://archive.ubuntu.com hardy-updates/universe Sources                   
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources                 
Hit http://archive.ubuntu.com hardy-security/main Packages                     
Hit http://apt.wicd.net hardy/extras Packages                                  
Hit http://archive.ubuntu.com hardy-security/restricted Packages               
Hit http://archive.ubuntu.com hardy-security/main Sources                      
Hit http://archive.ubuntu.com hardy-security/restricted Sources                
Hit http://archive.ubuntu.com hardy-security/universe Packages                 
Hit http://archive.ubuntu.com hardy-security/universe Sources                  
Hit http://archive.ubuntu.com hardy-security/multiverse Packages               
Hit http://archive.ubuntu.com hardy-security/multiverse Sources                
Fetched 62.0kB in 6s (9590B/s)                                                 
Reading package lists... Done
```

Hope this helps...

---

### Post by Beth1957 on 2008-10-25
Right, I got out my trusty command line cheat card and tried running ```
gdebi-gtk
```
I got the following output:-

```
liz@liz-laptop:~$ gdebi-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/gdebi-gtk", line 31, in <module>
    from GDebi.GDebi import GDebi
  File "/usr/lib/python2.5/site-packages/GDebi/GDebi.py", line 34, in <module>
    pygtk.require("2.0")
AttributeError: 'module' object has no attribute 'require'
liz@liz-laptop:~$ 
```

Does any of this mean anything to anyone, and is it fixable, please? :confused:

---

