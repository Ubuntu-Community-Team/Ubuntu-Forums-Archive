---
title: "Dependency problems while installing Wine 1.7 on Lubuntu 14.04 due to pk.archive.ubun"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by oldsmobile2 on 2014-04-26
I don't know much about instaling softwares on linux so i followed the steps on Wine's website 
*sudo add-apt-repository ppa:ubuntu-wine/ppa*
  Then update APT package information by running '**sudo apt-get  update**'. You can now install Wine by typing '**sudo apt-get  install wine1.7**'.

after the first command runs succesfully i enter sudo apt-get update and i does some work but after some time i gets stuck at 83% for one proxy and after that it stops and shows this 

```
Ign http://security.ubuntu.com trusty-security InRelease                      
Hit http://security.ubuntu.com trusty-security Release.gpg                    
Hit http://security.ubuntu.com trusty-security Release   
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Ign http://security.ubuntu.com trusty-security/main Translation-en_US          
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Err http://pk.archive.ubuntu.com trusty InRelease        
  
Err http://pk.archive.ubuntu.com trusty-updates InRelease
  
Err http://pk.archive.ubuntu.com trusty-backports InRelease
  
Err http://pk.archive.ubuntu.com trusty Release.gpg      
  Unable to connect to pk.archive.ubuntu.com:http:
Err http://pk.archive.ubuntu.com trusty-updates Release.gpg
  Unable to connect to pk.archive.ubuntu.com:http:
Err http://pk.archive.ubuntu.com trusty-backports Release.gpg
  Unable to connect to pk.archive.ubuntu.com:http:
Reading package lists... Done
W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Unable to connect to pk.archive.ubuntu.com:http:

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Unable to connect to pk.archive.ubuntu.com:http:

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Unable to connect to pk.archive.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

I googled around and found out that pk.archive.ubuntu is creating the problem and it can be solved by this method 

[http://www.linuxquestions.org/questions/linux-software-2/ubuntu-13-04-apt-get-update-problems-4175460316/](http://www.linuxquestions.org/questions/linux-software-2/ubuntu-13-04-apt-get-update-problems-4175460316/)

but i don't know how to change them into archive.ubuntu can any one give me the codes that i can run and edit it then..

---

### Post by bapoumba on 2014-04-26
[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)
One pic is better than a thousand words :)

---

### Post by oldsmobile2 on 2014-04-27
Thank you that worked perfectly.

---

### Post by bapoumba on 2014-04-27
Glad to see you got it to work. Would you please mark your thread as solved (under Thread Tools), thanks !

---

