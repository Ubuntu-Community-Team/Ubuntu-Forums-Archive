---
title: "GPG problem again and again"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by waleed.mohammed on 2012-04-28
as always from ubuntu 11.10 to 12.4 the same problem with update i tried a lot of solutions from 
[PHP]
apt-get clean 
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean 
apt-get update
[/PHP]to downloading this script
[http://ubuntuforums.org/attachment.php?attachmentid=102664&d=1234123501](http://ubuntuforums.org/attachment.php?attachmentid=102664&d=1234123501)

i am really sick about this after i failed with v 11.10 last year i was go to fedora now i want to use ubuntu but the same problem happened 
this is the error report
 W:GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message, W:GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message, W:GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease: File /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_InRelease doesn't start with a clearsigned message, W:GPG error: [http://sd.archive.ubuntu.com](http://sd.archive.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/sd.archive.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message, W:GPG error: [http://sd.archive.ubuntu.com](http://sd.archive.ubuntu.com) precise-updates InRelease: File /var/lib/apt/lists/partial/sd.archive.ubuntu.com_ubuntu_dists_precise-updates_InRelease doesn't start with a clearsigned message, W:GPG error: [http://sd.archive.ubuntu.com](http://sd.archive.ubuntu.com) precise-backports InRelease: File /var/lib/apt/lists/partial/sd.archive.ubuntu.com_ubuntu_dists_precise-backports_InRelease doesn't start with a clearsigned message, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by fantab on 2012-04-28
Try this:

```
$sudo rm /var/lib/apt/lists/* -vf
$sudo apt-get update
```

---

### Post by waleed.mohammed on 2012-04-28
> **fantab said:**
> Try this:

```
$sudo rm /var/lib/apt/lists/* -vf
$sudo apt-get update
```
no thing happened the same problem again :(

---

### Post by fantab on 2012-04-28
Change the server to Main or something else and try again. You can do this from update manager.

---

### Post by waleed.mohammed on 2012-04-28
no thing new
Fetched 22.8 MB in 4min 13s (89.8 kB/s)                                        
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_InRelease doesn't start with a clearsigned message
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Curtis6767 on 2012-04-28
Just a long shot here, but have you tried to go into the Update Manager/Settings/ Ubuntu Software

Change the server you're trying to update from and then try and run your updates again

---

### Post by waleed.mohammed on 2012-04-28
> **Curtis6767 said:**
> Just a long shot here, but have you tried to go into the Update Manager/Settings/ Ubuntu Software

Change the server you're trying to update from and then try and run your updates again
yes it was "server for Sudan" i changed it to "main server"

---

### Post by waleed.mohammed on 2012-04-28
BTW i can install programs from ubuntu software center very well without any problems

---

### Post by Curtis6767 on 2012-04-28
That's good news. 

At the top of the screen, under Thread Tools, could you please mark this thread as Solved.

Thanks

---

### Post by waleed.mohammed on 2012-04-28
> **Curtis6767 said:**
> That's good news. 

At the top of the screen, under Thread Tools, could you please mark this thread as Solved.

Thanks
no, the same error message appear

---

### Post by Curtis6767 on 2012-04-28
It was a long shot and sorry to hear it didn't work.

I'm trying to find a fix for your particular error message, but so far have been unsuccessful. I'll keep looking.

---

### Post by waleed.mohammed on 2012-04-28
> **Curtis6767 said:**
> It was a long shot and sorry to hear it didn't work.

I'm trying to find a fix for your particular error message, but so far have been unsuccessful. I'll keep looking.
thank you i tried a lot of thing but it didn't work it seems to me i have to go back to fedora

---

### Post by waleed.mohammed on 2012-05-02
please can any one help me

---

### Post by Baldrick_NZ on 2012-05-02
When you do ```
sudo apt-get update && sudo apt-get upgrade
``` in terminal, does the output record a series of letters and numbers after each GPG fail? Like: A7C883AB9?

---

### Post by waleed.mohammed on 2012-05-02
> **Baldrick_NZ said:**
> When you do ```
sudo apt-get update && sudo apt-get upgrade
``` in terminal, does the output record a series of letters and numbers after each GPG fail? Like: A7C883AB9?

when i changed my ISP this command worked fine without GPG  error can any one enplane to my the relation between ISP and GPG error? :confused:

---

### Post by waleed.mohammed on 2012-05-02
everybody hear me?

---

### Post by Baldrick_NZ on 2012-05-02
> **waleed.mohammed said:**
> when i changed my ISP this command worked fine without GPG  error can any one enplane to my the relation between ISP and GPG error? :confused:

Ok, but that didn't answer my question. 

When you do```
sudo apt-get update && sudo apt-get upgrade
``` in terminal, are there a series of numbers and letters (ie: 267A07BD677...) at the end of each GPG error?

---

### Post by waleed.mohammed on 2012-05-02
> **Baldrick_NZ said:**
> Ok, but that didn't answer my question. 

When you do```
sudo apt-get update && sudo apt-get upgrade
``` in terminal, are there a series of numbers and letters (ie: 267A07BD677...) at the end of each GPG error?
no i get GPG error without any numbers and letters

this is the report of sudo apt-get update && sudo apt-get upgrade:

Fetched 6,020 kB in 3min 16s (30.7 kB/s)
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease: File /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://sd.archive.ubuntu.com](http://sd.archive.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/sd.archive.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://sd.archive.ubuntu.com](http://sd.archive.ubuntu.com) precise-updates InRelease: File /var/lib/apt/lists/partial/sd.archive.ubuntu.com_ubuntu_dists_precise-updates_InRelease doesn't start with a clearsigned message
W: GPG error: [http://sd.archive.ubuntu.com](http://sd.archive.ubuntu.com) precise-backports InRelease: File /var/lib/apt/lists/partial/sd.archive.ubuntu.com_ubuntu_dists_precise-backports_InRelease doesn't start with a clearsigned message
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Index

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Baldrick_NZ on 2012-05-02
It's quite possible this is a result of a partial upgrade being performed on your part.

I'm not sure how changing ISP's could have contributed to this, it would seem possible but unlikely.

If it were caused by a partial upgrade, you might be wise to see if the prob clears up in few days with subsequent updates. 

Someone here might be better able to advise further.

---

### Post by amittan on 2012-08-28
Dear All,
Finding the similar error of GCG. Using DHCP settings instead of DNS.

sudo apt-get update
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease [2597 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise InRelease
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [2601 B]          
100% [2 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waiting for headbzip2: (stdin) is not a bzip2 file.
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates InRelease                              
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex [2597 B]            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports InRelease                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex [2601 B] 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
50% [2 Sources xz 0 B] [Waiting for headers] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [2601 B]                      
60% [5 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waiting for headbzip2: (stdin) is not a bzip2 file.
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                      
60% [2 Sources lzma 0 B] [Waiting for headers] [Waiting for headers] [Waiting for header/usr/bin/lzma: (stdin): File format not recognized
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                        
60% [5 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                      
60% [5 Packages lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages              
  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse i386 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main TranslationIndex                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse TranslationIndex          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted TranslationIndex          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe TranslationIndex            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Translation-en                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Translation-en                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Translation-en              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Translation-en              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Translation-en                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Translation-en                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Translation-en            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Translation-en            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 13.0 kB in 12s (1032 B/s)
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by MishMich on 2012-10-25
The solution is here:
[http://ubuntuforums.org/showthread.php?t=1983355&page=2](http://ubuntuforums.org/showthread.php?t=1983355&page=2)

---

