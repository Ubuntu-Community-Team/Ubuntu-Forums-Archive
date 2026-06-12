---
title: "Not sure what the problem is"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by granit5 on 2012-10-18
> The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 16.0.1+build1-0ubuntu0.12.04.1) but 18.0~a2~hg20121018r113467-0ubuntu1~umd1~precise is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Hello!
I'm completely frustrated, don't know much about Ubuntu, and everything seem to going downhill here!
Any advice will be greatly appreciated.


Thanks a lot.

---

### Post by Bashing-om on 2012-10-18
granit5; Hi Welcome to the forum.

Have you tried what dpkg suggest ?
terminal command (ctl+alt+t)
```
sudo apt-get -f install
```Please post back with results/error if any .
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by granit5 on 2012-10-18
> **Bashing-om said:**
> granit5; Hi Welcome to the forum.

Have you tried what dpkg suggest ?
terminal command (ctl+alt+t)
```
sudo apt-get -f install
```Please post back with results/error if any .
[INDENT]just try'n to help <==BDQ

[/INDENT]




```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox firefox-globalmenu
Suggested packages:
  latex-xft-fonts firefox-gnome-support
The following NEW packages will be installed:
  firefox
The following packages will be upgraded:
  firefox-globalmenu
1 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 24.4 MB of archives.
After this operation, 50.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/ precise/main firefox-globalmenu i386 18.0~a2~hg20121018r113467-0ubuntu1~umd1~precise [143 kB]
Get:2 http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/ precise/main firefox i386 18.0~a2~hg20121018r113467-0ubuntu1~umd1~precise [24.3 MB]
Fetched 24.4 MB in 32s (745 kB/s)                                              
(Reading database ... 457176 files and directories currently installed.)
Unpacking firefox (from .../firefox_18.0~a2~hg20121018r113467-0ubuntu1~umd1~precise_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_18.0~a2~hg20121018r113467-0ubuntu1~umd1~precise_i386.deb (--unpack):
 trying to overwrite '/usr/lib/firefox/plugins', which is also in package adobe-flashplugin 11.2.202.243-0precise1
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_18.0~a2~hg20121018r113467-0ubuntu1~umd1~precise_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by audiomick on 2012-10-18
Did you try and install a different (newer?) version of Firefox than the one that Ubuntu supplies by itself?

Have you tried the apt-get command that is suggested in the error message?

You would have to put sudo in front of it

Ah, wait on, I see that Bashing om has just posted that...

---

### Post by jerrrys on 2012-10-18
Try this

sudo apt-get autoremove

sudo apt-get install -f

---

### Post by audiomick on 2012-10-18
you posted whilst I was posting, so

I can see from your output that you have a PPA or two relating to firefox enabled. This answers my first question.

I looked back a your first post, and noticed that the dependency that is not being met is actually older than the version of that package that is to be installed. This is a danger when you start using PPA's. If you stick exclusively to the ubuntu repositories, then all the stuff get shoul work. When you start using ppa's, you rung the danger of things wanting dependecies other than what is available in the repositories. I think that is what is happening to you.

Just of the top of my head, I see two possibilities. One is to give up on the PPA and be content with the version of Firefox that is in the standard repository. The other, and I don't really know how to do this, is to revert to the package is required, and lock so that it stays with that version and doesn't get updated. Then you would have to keep an eye on things to see when the available packages all match up again.

---

### Post by jerrrys on 2012-10-18
@audiomick:  Is ppa-purge what your thinking about

---

### Post by granit5 on 2012-10-18
> **jerrrys said:**
> @audiomick:  Is ppa-purge what your thinking about

Okay, newb here. what's PPA, and what to do with it?
Sorry, liftime windows user up until recently :/

---

### Post by audiomick on 2012-10-18
> **jerrrys said:**
> @audiomick:  Is ppa-purge what your thinking about

Well, I'm not familiar with that as such, so I can't say it is, but it might well lead to the same end. ;)

Point is, I can see in the first post the same sort of silly dependency problem that I have had a couple of times. I don't know really how to get around it. I tend to just resign myself and go back to using the version of whatever program it is that is in the repos.

---

### Post by granit5 on 2012-10-18
I'm trying to get ANY firefox, doesn't matter what version.
I can't even do a standard update to my system without getting some weird error.

---

### Post by buckyaustin on 2012-10-18
Try uninstalling it, by typing this in terminal. "sudo apt-get remove firefox && sudo apt-get install firefox". Then reinstalling it. This should do the trick. Also make sure to run "sudo apt-get update" first.

---

### Post by oldos2er on 2012-10-18
granit5, if you haven't run sudo apt-get update, give it a try ```
sudo apt-get update && sudo apt-get install firefox
```

---

### Post by Bashing-om on 2012-10-18
granit5; I agree with the others, lets do away with the ppa (personal package archive), then see if you can update (wait to remove/install firefox)

look at your Software Sources and unmark the related ppa.
in version 12.04: ubuntu software center->edit (top task bar)->Software Sources->other software.
other software is where the conflicting source is located.

when the ppa is unmarked-> from terminal again:
```
sudo apt-get update
```post any errors and we go again.
[INDENT][INDENT]BDQ

[/INDENT][/INDENT]

---

### Post by jerrrys on 2012-10-18
You have installed FireFox thru this PPA:

Get:1 [http://ppa.launchpad.net/ubuntu-mozilla-daily/](http://ppa.launchpad.net/ubuntu-mozilla-daily/)

You can remove this PPA with ppa-purge.  This program disables a PPA from your Software Sources and reverts your system back to the official Ubuntu packages. You can use this to return your system to normal after testing a new version from a PPA.  To install ppa-purge enter:

sudo apt-get install ppa-purge

To use it:

sudo ppa-purge ppa:ubuntu-mozilla-daily/firefox-aurora

or

sudo ppa-purge ppa:firefox-aurora

Im not sure which command works in this case.

EDIT:  wait for Ann to reply

---

### Post by granit5 on 2012-10-18
I really appreciate all of your responses.


None of the codes you suggested work for me (purge, update, install),
each of them gives me some sort of error.
I can't even install different stuff (tried another browser just to check).
Cant uninstall, install, or update *anything* as far as I can tell.
Is there a basic program I can run that will detect issues? 
Don't even know where to begin...

---

### Post by oldos2er on 2012-10-18
> **granit5 said:**
> None of the codes you suggested work for me (purge, update, install),
each of them gives me some sort of error.

Can you please copy and paste all the terminal output so we can see?

---

### Post by granit5 on 2012-10-18
> **oldos2er said:**
> Can you please copy and paste all the terminal output so we can see?

**this code:**
```
sudo apt-get update && sudo apt-get install firefox
```

**gave me:**
```
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease                        
Ign http://archive.ubuntu.com precise-backports InRelease                      
Ign http://archive.ubuntu.com precise-security InRelease                       
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://archive.ubuntu.com precise-updates Release.gpg                      
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://extras.ubuntu.com precise Release.gpg                               
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://deb.opera.com stable InRelease                                      
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://archive.ubuntu.com precise-security Release.gpg                     
Hit http://archive.ubuntu.com precise Release                                  
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://archive.canonical.com precise/partner i386 Packages                 
Get:1 http://packages.medibuntu.org precise InRelease [7,096 B]                
Hit http://archive.ubuntu.com precise-updates Release                          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://packages.medibuntu.org precise InRelease                            
Hit http://deb.opera.com stable Release                                        
Hit http://archive.ubuntu.com precise-backports Release                        
Hit http://archive.ubuntu.com precise-security Release                         
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Hit http://archive.ubuntu.com precise-updates/main Sources                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex         
Hit http://archive.ubuntu.com precise-updates/restricted Sources               
Hit http://archive.ubuntu.com precise-updates/universe Sources                 
Hit http://archive.ubuntu.com precise-updates/multiverse Sources               
Hit http://archive.ubuntu.com precise-updates/main i386 Packages               
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages           
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages         
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com precise-security/main Sources                    
Hit http://archive.ubuntu.com precise-security/restricted Sources              
Hit http://archive.ubuntu.com precise-security/universe Sources                
Hit http://archive.ubuntu.com precise-security/multiverse Sources              
Hit http://archive.ubuntu.com precise-security/main i386 Packages              
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages        
Hit http://archive.ubuntu.com precise-security/universe i386 Packages          
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages      
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en    
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Fetched 7,096 B in 9s (719 B/s)                                                
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 16.0.1+build1-0ubuntu0.12.04.1) but 18.0~a2~hg20121018r113467-0ubuntu1~umd1~precise is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


**this code:**
```
sudo apt-get update
```


**gave me:**
```
Ign http://extras.ubuntu.com precise InRelease
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://deb.opera.com stable InRelease                                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease                        
Ign http://archive.ubuntu.com precise-backports InRelease                      
Ign http://archive.ubuntu.com precise-security InRelease                       
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://archive.ubuntu.com precise-updates Release.gpg                      
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://archive.ubuntu.com precise-security Release.gpg                     
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Get:1 http://packages.medibuntu.org precise InRelease [7,096 B]                
Hit http://deb.opera.com stable Release                                        
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://archive.ubuntu.com precise Release                                  
Hit http://archive.ubuntu.com precise-updates Release                          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://packages.medibuntu.org precise InRelease                            
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.ubuntu.com precise-backports Release                        
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise-security Release                         
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex         
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Hit http://archive.ubuntu.com precise-updates/main Sources                     
Hit http://archive.ubuntu.com precise-updates/restricted Sources               
Hit http://archive.ubuntu.com precise-updates/universe Sources                 
Hit http://archive.ubuntu.com precise-updates/multiverse Sources               
Hit http://archive.ubuntu.com precise-updates/main i386 Packages               
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages           
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages         
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com precise-security/main Sources                    
Hit http://archive.ubuntu.com precise-security/restricted Sources              
Hit http://archive.ubuntu.com precise-security/universe Sources                
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://archive.ubuntu.com precise-security/multiverse Sources              
Hit http://archive.ubuntu.com precise-security/main i386 Packages              
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages        
Hit http://archive.ubuntu.com precise-security/universe i386 Packages          
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://deb.opera.com stable/non-free Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Fetched 7,096 B in 9s (722 B/s)                                                
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)

```


**this code:**
> sudo apt-get install ppa-purge

or

sudo ppa-purge ppa:ubuntu-mozilla-daily/firefox-aurora

or

sudo ppa-purge ppa:firefox-aurora

(3 of them separately)


gave me:
```
command not found

```

---

### Post by granit5 on 2012-10-18
**and this code:**
```
sudo apt-get autoremove

sudo apt-get install -f
```



**gave me:**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 16.0.1+build1-0ubuntu0.12.04.1) but it is not installed
E: Unmet dependencies. Try using -f.
 
```

---

### Post by jerrrys on 2012-10-18
OK, lets just manually remove FireFox.  In terminal enter:

gksudo gedit /etc/apt/sources.list

And look for any lines containing  "http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora"
and remove the entire line.  Then save and close.  Now again in terminal:

gksudo gedit /etc/apt/sources.list.d

And look for the same line and remove/save/close.  NOW  ..  in terminal enter:

sudo apt-get remove --purge firefox

Then just to be sure its all gone:

gksudo nautilus

Go to "filesystem" (on the left side of the window) and then do a nautilus search on firefox and remove/delete ALL firefox files (if any exist).  Then ..

sudo apt-get install firefox

Good night  :)

---

### Post by buckyaustin on 2012-10-19
I have had similar problems. I tried to fix it. by using sudo apt-get update --fix-missing. sudo apt-get update -f. sudo apt-get update. then sudo apt-get autoclean. then sudo apt-get clean. Then at the last step I tried sudo apt-get update & sudo apt-get upgrade.

If that fails then you are unable to connect to the update sources. This litterally just means changing the location you download your updates. You can do this by going into Ubuntu Software Center and editing your sources and change the server from there.

Hope thats it solved.

---

### Post by granit5 on 2012-10-19
Thanks guys. That's what I tried:

> gksudo gedit /etc/apt/sources.list

And look for any lines containing "http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora"
and remove the entire line. Then save and close. 

-nothing by that name inside.


> Now again in terminal:

gksudo gedit /etc/apt/sources.list.d

And look for the same line and remove/save/close.


-File would'nt open, got an error message saying 
"/etc/apt/sources.list.d is a directory."


> NOW .. in terminal enter:

sudo apt-get remove --purge firefox

-I got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 16.0.1+build1-0ubuntu0.12.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


> Then just to be sure its all gone:

gksudo nautilus

Go to "filesystem" (on the left side of the window) and then do a nautilus search on firefox and remove/delete ALL firefox files (if any exist). Then ..

-didn't find any firefox files.


> sudo apt-get install firefox


-I got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 16.0.1+build1-0ubuntu0.12.04.1) but 18.0~a2~hg20121019r113499-0ubuntu1~umd1~precise is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```



and-
> I have had similar problems. I tried to fix it. by using sudo apt-get update --fix-missing. sudo apt-get update -f. sudo apt-get update. then sudo apt-get autoclean. then sudo apt-get clean. Then at the last step I tried sudo apt-get update & sudo apt-get upgrade.


-Nada. Same as before.

I don't know what I did,
but I messed it up pretty bad huh?

---

### Post by granit5 on 2012-10-19
Does this mean anything to anybody here:


> E: /var/cache/apt/archives/firefox_18.0~a2~hg20121019r113499-0ubuntu1~umd1~precise_i386.deb: trying to overwrite '/usr/lib/firefox/plugins', which is also in package adobe-flashplugin 11.2.202.243-0precise1


---

### Post by Bashing-om on 2012-10-19
I am still concerned with this issue..and thinking about it...
do not see how any action on your part precipitated this situation.

seems we always come back to the common point of problems with firefox's globalmenu.
at this time I do not comprehend why it has not been found/removed with all the actions you have undertaken. I will review these steps taken and see what I can advise further..
[INDENT]problems=solutions <==BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-10-19
summary:
 It seems you have been experimenting and pushing your horizons - a good thing-
you can not install/update-> therefore cannot comply with jerrys's post #19 instruction:

firefox-globalmenu -> my system has it in the docs directory --how can that interfere with updates ? -> see if it still exist on your system thus:
```
sudo find / -name "firefox-globalmenu"

``` will take a while to complete, wait ! :

the ppa for mozilla is loaded from somewhere !
why is the repo for medibuntu loaded ?
why do you have the repo for deb.opera.com ? is it conflicting with firefox ? :

I do not at this time know why /var/cache/apt/archives ->comes into play
what is the source of conflict ->/usr/lib/firefox/plugins (opera ???) :

in conclusion: lets look at the sources.list file -
sources.list.d -> directory ...is it empty at this time ?

post your /etc/apt/sources.list to us,to take a look at it.
will take it up from there.
[INDENT]puzzling thing, no ? <==BDQ
[/INDENT]

---

### Post by nsturdev on 2012-10-19
> E: /var/cache/apt/archives/firefox_18.0~a2~hg20121019r113499-0ubuntu1~umd1~precise_i386.deb: trying to overwrite '/usr/lib/firefox/plugins', which is also in package adobe-flashplugin 11.2.202.243-0precise1 

Would imply that you have a package that created and controls the folder in question.  You might be able to use:

```
 sudo apt-get remove adobe-flashplugin 
``` to remove it.

I would however use

```
 sudo dpkg -l |grep firefox 
```

to verify that firefox-globalmenu is actually installed.  If so i would then use 

```
 sudo apt-get remove firefox-globalmenu 
```

to try to remove it.  Then use the suggestions above to remove whatever ppa you have installed for firefox.

Then run

```
 sudo apt-get install firefox 
```

and see what happens.

---

### Post by Bashing-om on 2012-10-19
@ nsturdev: excellent ! - I had not given dpkg a thought .. slippage on my part, no doubt, as I am aware of what a great tool dpkg can be. Good to keep this reminder in mind.

@ granit5; The above advise is valid...

[INDENT]awaiting response ==> BDQ

[/INDENT]

---

