---
title: "Software Center has trust issues"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by babbagevigniere on 2012-12-25
Tried to install a package that would give me MTP support and let me use my Kindle etc. with my Ubuntu 12.04.1 laptop today, when the Software Center told me that it did not trust the package. I nodded and accepted that some packages were just not trustworthy, so I moved on to another, which had the same error message (the 'details' saying only the names of the package in both cases). 

Starting to suspect something was up, I tried to install SuperTuxKart, and that too was not trusted... apparently my faithful laptop Nigel has developed crippling social anxiety disorder verging on paranoia and doesn't even trust our friendly mascot Tux any more.

If anyone has any suggestions on how I can restore Nigel's faith in humanity (and packages) that would be greatly appreciated. Hope to hear back from you soon, and Merry Christmas! (Happy Hannukah, Joyous Kwanzaa, etc.)

---

### Post by oldos2er on 2012-12-25
Can you run the following command in a terminal (Ctrl-Alt-t) and copy and paste all its output here? ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by munkedal on 2012-12-27
I have a similar problem.  When I try and install something from the Ubuntu Software centre, I get the message, "Requires instalation of untrusted packages - The action would require the installation of packages from not authenticated sources"

---

### Post by Elfy on 2012-12-27
> **munkedal said:**
> I have a similar problem.  When I try and install something from the Ubuntu Software centre, I get the message, "Requires instalation of untrusted packages - The action would require the installation of packages from not authenticated sources"

So why don't you instead of just jumping on the end of someone else's thread, actually run the two commands in post #2, post the results and both of you might get some help.

---

### Post by munkedal on 2012-12-27
> **oldos2er said:**
> Can you run the following command in a terminal (Ctrl-Alt-t) and copy and paste all its output here? ```
sudo apt-get update && sudo apt-get upgrade
```

I ran the terminal command suggested by oldos2er and this was the output

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                    
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise InRelease    
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates InRelease
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release.gpg  
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates Release.gpg
  Unable to connect to nz.archive.ubuntu.com:http:
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates Release
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main TranslationIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe TranslationIndex
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to nz.archive.ubuntu.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.

  Help would be appreciated.

---

### Post by deadflowr on 2012-12-27
> **babbagevigniere said:**
> Tried to install a package that would give me MTP support and let me use my Kindle etc. with my Ubuntu 12.04.1 laptop today, when the Software Center told me that it did not trust the package. I nodded and accepted that some packages were just not trustworthy, so I moved on to another, which had the same error message (the 'details' saying only the names of the package in both cases). 

Starting to suspect something was up, I tried to install SuperTuxKart, and that too was not trusted... apparently my faithful laptop Nigel has developed crippling social anxiety disorder verging on paranoia and doesn't even trust our friendly mascot Tux any more.

If anyone has any suggestions on how I can restore Nigel's faith in humanity (and packages) that would be greatly appreciated. Hope to hear back from you soon, and Merry Christmas! (Happy Hannukah, Joyous Kwanzaa, etc.)

How are you trying to install them?

Through a deb? 
Third party repositories?
Can you follow oldos2er's advice and then copy and paste/post(please use the code tags{#}.

---

### Post by lenHo on 2012-12-27
I have a similar issue to babbagevigniere when trying to install 'bridge-utils'.
It gives me a "packages cannot be authenticated" warning.
Also tried installing 'SuperTuxKart' (and other programs) and get the same warning, followed by a "failed to fetch" message.

I have been using Ubuntu for a few months now and have installed plenty of programs, but this is the first time that I have encountered this problem.

Using the command:
```
sudo apt-get update && sudo apt-get upgrade
```

I get a similar output to munkedal. 
Is there something wrong with the New Zealand Ubuntu archive? 
Any help will be greatly appreciated. :p

```
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://packages.x2go.org squeeze InRelease                                 
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://packages.x2go.org squeeze/main Sources                              
Hit http://extras.ubuntu.com precise Release                                   
Hit http://security.ubuntu.com precise-security Release                        
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://packages.x2go.org squeeze/main i386 Packages                        
Ign http://packages.x2go.org squeeze/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://extras.ubuntu.com precise/main Translation-en_NZ                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://extras.ubuntu.com precise/main Translation-en_AU                 
Ign http://packages.x2go.org squeeze/main Translation-en_NZ                 
Ign http://extras.ubuntu.com precise/main Translation-en_GB                 
Ign http://packages.x2go.org squeeze/main Translation-en                    
Ign http://packages.x2go.org squeeze/main Translation-en_AU                 
Ign http://packages.x2go.org squeeze/main Translation-en_GB                 
Ign http://nz.archive.ubuntu.com precise InRelease                          
Ign http://nz.archive.ubuntu.com precise-updates InRelease
Ign http://nz.archive.ubuntu.com precise-backports InRelease
Err http://nz.archive.ubuntu.com precise Release.gpg
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates Release.gpg
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports Release.gpg
  Unable to connect to nz.archive.ubuntu.com:http:
Ign http://nz.archive.ubuntu.com precise Release
Ign http://nz.archive.ubuntu.com precise-updates Release
Ign http://nz.archive.ubuntu.com precise-backports Release
Ign http://nz.archive.ubuntu.com precise/main Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise/restricted Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise/universe Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise/multiverse Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise/main i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise/universe i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise/main TranslationIndex
Ign http://nz.archive.ubuntu.com precise/multiverse TranslationIndex
Ign http://nz.archive.ubuntu.com precise/restricted TranslationIndex
Ign http://nz.archive.ubuntu.com precise/universe TranslationIndex
Ign http://nz.archive.ubuntu.com precise-updates/main Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/restricted Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/universe Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/multiverse Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/main i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/restricted i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/universe i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/multiverse i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-updates/main TranslationIndex
Ign http://nz.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Ign http://nz.archive.ubuntu.com precise-updates/restricted TranslationIndex
Ign http://nz.archive.ubuntu.com precise-updates/universe TranslationIndex
Ign http://nz.archive.ubuntu.com precise-backports/main Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/restricted Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/universe Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/multiverse Sources/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/main i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/restricted i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/universe i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/multiverse i386 Packages/DiffIndex
Ign http://nz.archive.ubuntu.com precise-backports/main TranslationIndex
Ign http://nz.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Ign http://nz.archive.ubuntu.com precise-backports/restricted TranslationIndex
Ign http://nz.archive.ubuntu.com precise-backports/universe TranslationIndex
Err http://nz.archive.ubuntu.com precise/main Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/restricted Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/universe Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/multiverse Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/main i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/restricted i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/universe i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/multiverse i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/main Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/main Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/main Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/main Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/multiverse Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/multiverse Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/multiverse Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/multiverse Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/restricted Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/restricted Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/restricted Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/restricted Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/universe Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/universe Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/universe Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise/universe Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/main Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/restricted Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/universe Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/multiverse Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/main i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/restricted i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/universe i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/multiverse i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/main Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/main Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/main Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/main Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/multiverse Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/multiverse Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/multiverse Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/restricted Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/restricted Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/restricted Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/restricted Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/universe Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/universe Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/universe Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-updates/universe Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/main Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/restricted Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/universe Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/multiverse Sources
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/main i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/restricted i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/universe i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/multiverse i386 Packages
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/main Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/main Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/main Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/main Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/multiverse Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/multiverse Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/multiverse Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/multiverse Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/restricted Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/restricted Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/restricted Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/restricted Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/universe Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/universe Translation-en
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/universe Translation-en_AU
  Unable to connect to nz.archive.ubuntu.com:http:
Err http://nz.archive.ubuntu.com precise-backports/universe Translation-en_GB
  Unable to connect to nz.archive.ubuntu.com:http:
W:  Failed to fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Unable to  connect to nz.archive.ubuntu.com:http:

W: Failed to fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_NZ   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_AU   Unable to connect to nz.archive.ubuntu.com:http:

W: Failed to  fetch  http://nz.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_GB   Unable to connect to nz.archive.ubuntu.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by zombifier25 on 2012-12-27
You can try switching to the main server in Software Sources. Open Update Manager, choose Settings to open it. Then run those commands again.

---

### Post by lenHo on 2012-12-27
> **zombifier25 said:**
> You can try switching to the main server in Software Sources. Open Update Manager, choose Settings to open it. Then run those commands again.

Hi zombifier25,

That solved my problem. There are no more errors with apt-get update/upgrade and everything installs fine.

Thank you for your help. ):P

---

### Post by munkedal on 2012-12-27
Thanks zombifier25,

Your advice resolved my issues with the Ubuntu Software Centre downloads.

:D

---

