---
title: "tinyos installation problem"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by nawaz1 on 2012-08-27
hi
i am using ubuntu 12.04 
i try to install  by inserting command in the following file
cd /etc/apt/sources.list
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) precise main
but that command shows error 

plz help

---

### Post by Cheesemill on 2012-08-27
```
cd /etc/apt/sources.list
```Isn't a valid command, /etc/apt/sources.list is a file, not a directory.
To edit it you should do:
```
gksudo gedit /etc/apt/sources.list
```and add the following line at the bottom of the file:
```
deb http://tinyos.stanford.edu/tinyos/dists/ubuntu precise main
```Then run the following commands:
```
sudo apt-get update
sudo apt-get install tinyos
```


Edit - I've just had a look at their repository, they haven't built a version of TinyOS for Precise, the last version was for 11.04.
You can try replacing precise with natty in the above instructions but it may not install properly due to different software versions.

---

### Post by nawaz1 on 2012-08-27
i do the same but get errors whe try to use
sudo apt-get update

---

### Post by Cheesemill on 2012-08-27
Can you actually post the errors please.
We're not psychic you know.

Post the full output of 'sudo apt-get update' inbetween [NOPARSE]```
  
```[/NOPARSE] tags please to make it more readable.

---

### Post by nawaz1 on 2012-08-28
nawazbaig@ubuntu:~$ sudo apt-get update
[sudo] password for nawazbaig: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Ign [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Ign [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                
Ign [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
Ign [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise/main TranslationIndex         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Err [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise/main amd64 Packages
  404  Not Found
Err [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise/main i386 Packages
  404  Not Found
Ign [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise/main Translation-en_US
Ign [http://tinyos.stanford.edu](http://tinyos.stanford.edu) precise/main Translation-en
W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/precise/main/binary-amd64/Packages](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/precise/main/binary-i386/Packages](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Cheesemill on 2012-08-28
I did cover this in my first post.
> I've just  had a look at their repository, they haven't built a version of TinyOS  for Precise, the last version was for 11.04.
You can try replacing precise with natty in the above instructions but  it may not install properly due to different software versions

Edit your /etc/apt/sources.list file and replace:
```
deb http://tinyos.stanford.edu/tinyos/dists/ubuntu precise main
```
with
```
deb http://tinyos.stanford.edu/tinyos/dists/ubuntu natty main
```

---

