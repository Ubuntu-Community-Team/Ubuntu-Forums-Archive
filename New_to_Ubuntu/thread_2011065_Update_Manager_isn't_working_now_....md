---
title: "Update Manager isn't working now ..."
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Rob Sayer on 2012-06-26
I tried to run it a few minutes ago ... I think there may have been a hiccup in the wireless connection.

I got a message, along with a suggestion to check the internet connection:

> 'Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with  MergeList  /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages,  E:The package lists or status file could not be parsed or opened.'Now I'm getting the above message every time I try to run Update Manager.  Other web access is working fine.

I don't know where to report bugs, and frankly I'm more concerned with getting update manager working again.  There's no menu, anything, just a close button.

BTW this is the result of my sudo apt get:

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise InRelease                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg [198 B]                 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                          
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages/DiffIndex             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages/DiffIndex              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                     
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [1,020 B]                  
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages [1,232 B]           
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,056 B]                  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages/DiffIndex               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [1,249 B]           
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [1,260 B]            
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [1,229 B]           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release                       
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release                       
  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release                     
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release                     
  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                    
Get:11 [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages [808 B]    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA           
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_CA
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en
Fetched 8,646 B in 2s (3,762 B/s)
Reading package lists... Error!
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following  signatures were invalid: BADSIG A7E13D78E4A4F4F4 Launchpad PPA named  smplayer for rvm
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following  signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive  Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following  signatures were invalid: BADSIG AAFF4A5B336064B5 Opera Software Archive  Automatic Signing Key 2012 <packager@opera.com>
W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used. GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used. GPG error:  [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release: The following signatures  were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing  Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used. GPG error:  [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used. GPG error:  [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release](http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.



Edit: I don't know why there's a smiley face in the quote ...

---

### Post by mapes12 on 2012-06-26
What version of Ubu do you have?

---

### Post by dgharmon on 2012-06-26
> **Rob Sayer said:**
> Now I'm getting the above message every time I try to run Update Manager.  Other web access is working fine.

Try ...

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by wildmanne39 on 2012-06-26
Hi, please try:
```
sudo rm /var/lib/apt/lists/* -vf
```

The first command will remove the damaged list and when you run the second command it will replace it with a new list.

```
sudo apt-get update
```
Thanks

---

### Post by Rob Sayer on 2012-06-27
> **wildmanne39 said:**
> Hi, please try:
```
sudo rm /var/lib/apt/lists/* -vf
```The first command will remove the damaged list and when you run the second command it will replace it with a new list.

```
sudo apt-get update
```Thanks

It worked.  Update complete.  Making a note of first sudo parameters now ...

Thanks.

---

### Post by wildmanne39 on 2012-06-27
Your welcome!

---

### Post by chamjinislro on 2012-07-02
Hi, I have the same problems as well, and when I do this it comes up with

rm: cannot remove `/var/lib/apt/lists': Is a directory

what to do? completely new to ubuntu and struggling...

---

### Post by wildmanne39 on 2012-07-02
Hi, please do:
```
sudo apt-get update
```
then post the results here by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

