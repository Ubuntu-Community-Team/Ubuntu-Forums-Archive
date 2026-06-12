---
title: "Ubuntu 12.04 not able to update, upgrade or install anything after fresh installation"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by kuchakra on 2012-11-11
Hi, 
I installed ubuntu 12.04 LTS in my compaq presario 317tu , but not able to update or install anything. Whenever I am trying to install flash player or media codecs its showing errors. Ubuntu software centre is not working. I have changed it to main server, still noresult :-(  Please help me...

---

### Post by carl4926 on 2012-11-11
Post the result of

```
sudo apt-get update
```

---

### Post by Wim Sturkenboom on 2012-11-11
> 
Whenever I am trying to install flash player or media codecs its showing errors.

Next time, please provide details of the errors. My crystal ball is out-of-order at this moment ;)

---

### Post by kuchakra on 2012-11-11
Hi Thanks for your suggestion. Please see the output for the above code.

kunal@kunal:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                                       
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                                     
  Unable to connect to extras.ubuntu.com:http:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                           
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                     
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN                                                 
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                    
  Unable to connect to extras.ubuntu.com:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                          
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                        
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_IN
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed InRelease
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg     
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe TranslationIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_IN](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_IN)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en_IN](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en_IN)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/binary-i386/Packages)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en_IN)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.200 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
kunal@kunal:~$

---

### Post by carl4926 on 2012-11-11
you could try using google dns servers

---

### Post by kuchakra on 2012-11-11
> **carl4926 said:**
> you could try using google dns servers

Dear Carl , 
Will it be possible to give me the detail of the process. It will be really helpful for me.
Thanks in advance!

---

### Post by carl4926 on 2012-11-11
can you actually browse OK
Can you open this in Firefox
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by Jos.vh on 2012-11-11
Hi. I have the same problem here (unable to update, same type of error messages .....cannot connect...check you network connection......).
What to do next, when opening the link below in Firefox?

Best regards,
Jos


> **carl4926 said:**
> can you actually browse OK
Can you open this in Firefox
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by Bartender on 2012-11-11
carl4926 is trying to ascertain whether you're simply not getting on the internet at all, or if there's some problem specific to getting updates.

'Cause it sure looks like the updater failed to find anything.  Sometimes the servers are down for brief periods of time.

---

### Post by kuchakra on 2012-11-12
> **carl4926 said:**
> can you actually browse OK
Can you open this in Firefox
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Yes Carl I can open the quoted link.

---

### Post by carl4926 on 2012-11-12
> **kuchakra said:**
> Yes Carl I can open the quoted link.

so is apt-get still problematic?

---

### Post by carl4926 on 2012-11-12
> **carl4926 said:**
> so is apt-get still problematic?

to be sure
open a terminal and post result of

```
cat /etc/apt/sources.list
```

---

### Post by kuchakra on 2012-11-12
> **carl4926 said:**
> to be sure
open a terminal and post result of

```
cat /etc/apt/sources.list
```

Here is the result Carl

kunal@kunal:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by carl4926 on 2012-11-12
Configure your network dns to use googles

8.8.8.8 and 8.8.4.4

---

### Post by kuchakra on 2012-11-12
> **carl4926 said:**
> Configure your network dns to use googles

8.8.8.8 and 8.8.4.4

How to do that?! I have tried yesterday... googled that but coul not make any change in my dns server. Presently I am using wireless connections.

---

### Post by newb85 on 2012-11-12
From the Network menu, click "Edit Connections...".  Select the Wirleess tab, select the connection you're using and click "Edit...".  Select the "IPv4 Settings" tab and change the "Method" to "Automatic (DHCP) addresses only".  Then, for DNS servers, add "8.8.8.8, 8.8.4.4".  Hit Save and then hit Close.  I believe you'll need to reconnect to your router for the changes to take effect.

---

### Post by kuchakra on 2012-11-12
I changed the IPv4 settings but nothing is positive!

> **newb85 said:**
> From the Network menu, click "Edit Connections...".  Select the Wirleess tab, select the connection you're using and click "Edit...".  Select the "IPv4 Settings" tab and change the "Method" to "Automatic (DHCP) addresses only".  Then, for DNS servers, add "8.8.8.8, 8.8.4.4".  Hit Save and then hit Close.  I believe you'll need to reconnect to your router for the changes to take effect.

---

### Post by carl4926 on 2012-11-12
When you run the live cd
You can install a package with apt in a live session
Does apt work in the live session?

---

### Post by kuchakra on 2012-11-17
Hi, I reinstalled Ubuntu 12.04 LTS and now I have updated using a mobile broadband. Everything is running fine. Everything I can do with that. But whenever I change to the proxy settings of the wireless network  the same problem occurs again. How can I update using my same proxy server???

---

### Post by Wim Sturkenboom on 2012-11-18
Brilliant; couldn't you have told us before that you're using a proxy ;)

You can configure it in synaptic, so I assume you can also configure it in software center somewhere.

Note that that does not affect command line (at least it did not in 10.04)

PS
just had a look at software center in 12.04 and it's not there; there however is a proxy setting in system settings -> network that **might** do the trick.

---

### Post by kuchakra on 2012-11-18
Hi Wim,

Thanks a lot... It is working :-)  Thanks to carl again for continuous help...

---

### Post by carl4926 on 2012-11-18
> **kuchakra said:**
> Hi Wim,

Thanks a lot... It is working :-)  Thanks to carl again for continuous help...

Excellent!

---

