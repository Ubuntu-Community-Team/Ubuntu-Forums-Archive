---
title: "Software Center not working"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Maese909 on 2011-11-11
Hey all. I am using Ubuntu 11.04 and my software center is not working. It opens up fine, but when I search for something, the circle pattern thing keeps loading and goes on forever. I tried this..

kevin@ubuntu:~$ sudo apt-get update
[sudo] password for kevin: 
Sorry, try again.
[sudo] password for kevin: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by ikt on 2011-11-11
[http://ubuntuforums.org/showthread.php?t=1750755](http://ubuntuforums.org/showthread.php?t=1750755)

---

### Post by Maese909 on 2011-11-11
It worked! Finally, I can get vim installed :)
Thank you!

---

### Post by ikt on 2011-11-11
> **maese909 said:**
> it worked! Finally, i can get vim installed :)
thank you!

no problems, good to hear it is fixed! (+1 for using vim :D)

---

### Post by Rubi1200 on 2011-11-12
Glad you got things working :)

Please mark this Solved using the Thread Tools near the top of the page.

---

