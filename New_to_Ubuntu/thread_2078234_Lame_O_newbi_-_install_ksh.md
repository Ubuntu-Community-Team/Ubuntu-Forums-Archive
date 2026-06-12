---
title: "Lame O newbi - install ksh"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by wannbenixdude on 2012-10-30
I have started a new job with which provides no access to nix servers. 
Ive loaded Ubuntu via a virtual machine. Ive never had to do much setup ... 

I want to install some packages. 

chris@chris-VirtualBox:~$ sudo apt-get install ksh
[sudo] password for chris: 
Sorry, try again.
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ksh
chris@chris-VirtualBox:~$ 

How do I fix this. 

Thanks in advance !!! 

Ksh for one and receive the following

---

### Post by wojox on 2012-10-30
You may just need a refresh:
```
sudo apt-get update; sudo apt-get install ksh
```

---

### Post by wannbenixdude on 2012-10-30
I entered the given command and received the following 
```
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ksh
```

---

### Post by wojox on 2012-10-30
Wow, do you have any network connection? Run this:
```
ping -c 5 example.com
```

---

### Post by wannbenixdude on 2012-10-30
Yes. I can ping that and internal and external devices 

chris@chris-VirtualBox:~$ ping -c 1 example.com
PING example.com (148.171.53.111) 56(84) bytes of data.
64 bytes from phxipclog003.ipc.us.aexp.com (148.171.53.111): icmp_req=1 ttl=60 time=1.90 ms

--- example.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.902/1.902/1.902/0.000 ms


I want to load Ksh because that is the shell Im most familiar with .. I am trying to use this simple script and echos new lines arent working with or with out the -e 

#!/bin/bash
DOIT () {
echo "myname"
echo "mypassword"
sleep 1
#echo "en\n" 
echo -e "en\n" 
sleep 1 
echo "sh run\n"
sleep 10 
echo "exit"
}
#
while read x
do
  DOIT | telnet $x | tee $x.sul
done

---

### Post by Lars Noodén on 2012-10-30
What about the archive you are trying to reach?

```

host us.archive.ubuntu.com
ping -c 1 -w 1 us.archive.ubuntu.com

```

---

### Post by wannbenixdude on 2012-10-30
chris@chris-VirtualBox:~$ host us.archive.ubuntu.com
Host us.archive.ubuntu.com not found: 3)
chris@chris-VirtualBox:~$ ping -c 1 -w 1 us.archive.ubuntu.com
ping: unknown host us.archive.ubuntu.com

---

### Post by COMECON on 2012-10-30
Maybe you should change your DNS servers to Google's servers. For doing that, open the Control Panel, then Network, then Wireless (or Wired, if you use a Wired connection) and then the Options button.
On the window that's shown, click on *IPv4 Settings* tab and then change **Method** to **Just** **automatic directions (DHCP)**. Finally, enter the following text to the DNS Servers textbox:
```
8.8.8.8., 8.8.4.4
```
And click on *Save*. Try again doing:
```
$ sudo apt-get update && sudo apt-get install ksh
```
Hope it works to you!

---

