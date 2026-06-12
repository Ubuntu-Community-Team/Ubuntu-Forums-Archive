---
title: "Chrome install and error message"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by vasa1 on 2011-09-14
Ubuntu 11.04 in Unity mode:
I had downloaded the .deb for Google Chrome (not Chromium) from Google's official site. I used Firefox 6.02 for the download.

After the download was completed, I had to click on Tools, Downloads, and then right-click on the download for Chrome to "open" it. This led to the Ubuntu Software Center (USC) opening with the option to install "Chrome".

I clicked install but then got a pop-up (modal thingie?) indicating that there was a problem. In a bit of panic, I clicked "okay" but then tried to install again. This time it worked. But is there anyway I can dig out that error message at this time? I should have taken a screenshot at that time but I didn't :(

On more point ... re. USC
After installing most software, the "install" button changes to "remove". But this time, it showed "reinstall". Confusing ... since Chrome *seems* to be working just fine right now.

---

### Post by An Sanct on 2011-09-15
The dialog you saw was most probably a "oh no! installing from an unknown source, do you really want to do this?" type of dialog ;) (not really what it says, but that is the message) or maybe a "do you want to add this software source?"

The thing with the "reinstall" caption happens, when you use *deb* files to install applications instead of the software center, if you open the deb file again, SC sees, that it is already installed and proposes a reinstall, but if you go directly to SC and type "chrome", you can uninstall there. also, if it is in the list, then updates will be automatic if you can see a "google" section between the sources on the left.

ps. don't "miss" warnings and Ok/Yes/I agree is not always the best choice ;)

---

### Post by vasa1 on 2011-09-15
> **An Sanct said:**
> The dialog you saw was most probably a "oh no! installing from an unknown source, do you really want to do this?" type of dialog ;) (not really what it says, but that is the message) or maybe a "do you want to add this software source?"

The thing with the "reinstall" caption happens, when you use *deb* files to install applications instead of the software center, if you open the deb file again, SC sees, that it is already installed and proposes a reinstall, but if you go directly to SC and type "chrome", you can uninstall there. also, if it is in the list, then updates will be automatic if you can see a "google" section between the sources on the left.

ps. don't "miss" warnings and Ok/Yes/I agree is not always the best choice ;)

Hi! and thanks for responding :) From what I recall, it wasn't the type of dialog you suggest. I was more along the lines that something couldn't be done.

I also remember allowing Google to add it's own repository so that updates could take place. But I don't know where that is located. Sources.lst or something like that? It doesn't show up on the left side of the USC screen which has Canonical, partners, etc.

And you're absolutely correct about using one's judgement before going ok/accept/agree for a lot of things! We could end up with a lot of "toolbars" if not worse (especially in MS Windows)!

PS: Even Synaptic doesn't show that Chrome is installed but I see it when I click on the "dash" and then on "internet apps". That how I'm using Chrome right now.

---

### Post by vasa1 on 2011-09-15
> **vasa1 said:**
> ...
I also remember allowing Google to add it's own repository so that updates could take place. But I don't know where that is located. Sources.lst or something like that? It doesn't show up on the left side of the USC screen which has Canonical, partners, etc...
PS: Even Synaptic doesn't show that Chrome is installed but I see it when I click on the "dash" and then on "internet apps". That how I'm using Chrome right now.

The magic sauce was "sudo apt-get update". Now the USC shows it under "Other".

---

### Post by An Sanct on 2011-09-16
Good to hear :)

PS. Please mark this thread as solved, if you are satisfied with the answer and results.

---

### Post by vasa1 on 2011-09-18
> **vasa1 said:**
> The magic sauce was "sudo apt-get update". Now the USC shows it under "Other".

And after a restart, the "Other" became "Google".

Today, I was expecting that I'd be prompted to update to Chrome 14 but I've got nothing so far. On running "sudo apt-get update", I see this:

```

aes@aes-Inspiron-1545:~$ sudo apt-get update
[sudo] password for aes: 
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                              
Ign http://security.ubuntu.com natty-security InRelease                                                                            
Ign http://archive.canonical.com natty InRelease                                                                                   
Ign http://us.archive.ubuntu.com natty InRelease                                                                 
Ign http://ppa.launchpad.net natty InRelease                                                                                       
Ign http://us.archive.ubuntu.com natty-updates InRelease                                                                           
Ign http://extras.ubuntu.com natty InRelease                                                                     
Hit http://security.ubuntu.com natty-security Release.gpg                                                        
Hit http://archive.canonical.com natty Release.gpg                                                               
Hit http://us.archive.ubuntu.com natty Release.gpg                                                               
Hit http://ppa.launchpad.net natty Release.gpg                                                                   
Get:2 http://extras.ubuntu.com natty Release.gpg [72 B]                                                          
Hit http://security.ubuntu.com natty-security Release                                                                              
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                                                       
Hit http://archive.canonical.com natty Release                                                                   
Hit http://ppa.launchpad.net natty Release                                                                        
Hit http://extras.ubuntu.com natty Release                                                                        
Hit http://us.archive.ubuntu.com natty Release                                                                                     
Hit http://security.ubuntu.com natty-security/main Sources                                                                         
Hit http://archive.canonical.com natty/partner i386 Packages                                                                       
Hit http://ppa.launchpad.net natty/main Sources                                                                  
Hit http://extras.ubuntu.com natty/main Sources                                                                  
Hit http://us.archive.ubuntu.com natty-updates Release                                                           
Hit http://security.ubuntu.com natty-security/restricted Sources                                                                   
Hit http://security.ubuntu.com natty-security/universe Sources                                                                     
Hit http://security.ubuntu.com natty-security/multiverse Sources                                                                   
Hit http://security.ubuntu.com natty-security/main i386 Packages                                                                   
Hit http://security.ubuntu.com natty-security/restricted i386 Packages                                                             
Ign http://archive.canonical.com natty/partner TranslationIndex                                                                    
Hit http://ppa.launchpad.net natty/main i386 Packages                                                                              
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                           
Hit http://extras.ubuntu.com natty/main i386 Packages                                                                              
Ign http://extras.ubuntu.com natty/main TranslationIndex                                                         
Hit http://us.archive.ubuntu.com natty/main Sources                                                              
Hit http://us.archive.ubuntu.com natty/restricted Sources                                                        
Hit http://us.archive.ubuntu.com natty/universe Sources                                                          
Hit http://us.archive.ubuntu.com natty/multiverse Sources                                                                          
Hit http://us.archive.ubuntu.com natty/main i386 Packages                                                                          
Hit http://security.ubuntu.com natty-security/universe i386 Packages                                                               
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages                                                             
Ign http://security.ubuntu.com natty-security/main TranslationIndex                                                                
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                                                          
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex                                                          
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                                                            
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                                                                    
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                                                    
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                                                  
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                                                     
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex                                               
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex                                               
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex                                                                   
Hit http://us.archive.ubuntu.com natty-updates/main Sources                                                                        
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources                                                                  
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                                                                    
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources                                                                  
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages                                                                  
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages                                                            
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages                                                              
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages                                                            
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex                                                               
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex                                       
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex                                       
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex                                         
Get:3 http://dl.google.com stable Release [1,347 B]                                                                                
Ign http://ppa.launchpad.net natty/main Translation-en_US                                                                          
Ign http://ppa.launchpad.net natty/main Translation-en                                                                             
Ign http://archive.canonical.com natty/partner Translation-en_US                                                 
Ign http://security.ubuntu.com natty-security/main Translation-en_US                                             
Ign http://security.ubuntu.com natty-security/main Translation-en                          
Ign http://extras.ubuntu.com natty/main Translation-en_US                                                        
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US                                       
Ign http://security.ubuntu.com natty-security/multiverse Translation-en                    
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US                 
Ign http://extras.ubuntu.com natty/main Translation-en                                                                             
Ign http://security.ubuntu.com natty-security/restricted Translation-en                                                            
Ign http://security.ubuntu.com natty-security/universe Translation-en_US                                                           
Ign http://security.ubuntu.com natty-security/universe Translation-en                                                              
Ign http://archive.canonical.com natty/partner Translation-en                                                                      
Get:4 http://dl.google.com stable/main i386 Packages [1,192 B]                                                                     
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                                                                      
Ign http://us.archive.ubuntu.com natty/main Translation-en                                                                         
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US                                                                
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en                                                                   
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US                                                                
Ign http://us.archive.ubuntu.com natty/restricted Translation-en                                                                   
Ign http://dl.google.com stable/main TranslationIndex                                                                              
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US                                                                  
Ign http://us.archive.ubuntu.com natty/universe Translation-en                                                                     
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US                                                              
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en                                                                 
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US                                                        
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en                                                           
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US                                                        
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en                                                           
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US                                                          
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en                                                             
Ign http://dl.google.com stable/main Translation-en_US                                                                             
Ign http://dl.google.com stable/main Translation-en
Fetched 2,809 B in 29s (94 B/s)
Reading package lists... Done
aes@aes-Inspiron-1545:~$ 

```

Can someone kindly explain (or tell me where to look to know) what
**Ign**, **Get**, and **Hit** mean at the start of lines in the output?
And what do **InRelease**, **Release.gpg** [xyz B], and **Release** mean at the end of some lines?

Is there any thing wrong in the output that may explain why I have not been prompted to update? Is there some way to know if the update is actually ready or not? If it is ready, do I need to *force* it?

It seems that an update is available according to this site:
-http://www.ubuntuupdates.org/ppa/google_chrome?dist=stable-

---

### Post by westie457 on 2011-09-18
Can someone kindly explain (or tell me where to look to know) what
**Ign**, **Get**, and **Hit** mean at the start of lines in the output?
And what do **InRelease**, **Release.gpg** [xyz B], and **Release** mean at the end of some lines?

Is there any thing wrong in the output that may explain why I have not been prompted to update? Is there some way to know if the update is actually ready or not? If it is ready, do I need to *force* it?

It seems that an update is available according to this site:
-http://www.ubuntuupdates.org/ppa/google_chrome?dist=stable-[/QUOTE]


Hi, someone will correct me if I am wrong.

The **ign** means ignored, the **get** is an external source (not in the repositories) and **hit** is in the repositories.

Google Chrome updates itself quietly while it is running. The user never knows when this is happening and it is always upto date. Chromium-Browser on the other hand has minor updates while it is running and major updates to a newer version are applied through Update Manager.

---

### Post by vasa1 on 2011-09-18
> **westie457 said:**
> ...
The **ign** means ignored, the **get** is an external source (not in the repositories) and **hit** is in the repositories.

Google Chrome updates itself quietly while it is running. The user never knows when this is happening and it is always upto date. Chromium-Browser on the other hand has minor updates while it is running and major updates to a newer version are applied through Update Manager.

Hi Westie, I have a feeling you're right about the first part but I'm not sure about the silent updates. I know that that happens in MS Windows, but I don't think that happens, at least by default, in Linux as far as Chrome (or even Chromium) is concerned. Anyway, to be sure, I checked my version just now and it still is 13.0.782.220 (Official Build 99552) :(

---

### Post by Lisiano on 2011-09-18
Did you try running
```
sudo apt-get upgrade
``` after running update?
Btw my version is 14.0.835.163 and I don't know how chrome could update itself. If you look on it's owner, it is owned by Root and can not be overwritten. The auto updates only apply to Win.

---

### Post by vasa1 on 2011-09-18
> **Lisiano said:**
> Did you try running
```
sudo apt-get upgrade
``` after running update?
Btw my version is 14.0.835.163 and I don't know how chrome could update itself. If you look on it's owner, it is owned by Root and can not be overwritten. The auto updates only apply to Win.

After reading your advice, I did :)
```

aes@aes-Inspiron-1545:~$ sudo apt-get upgrade
[sudo] password for aes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  google-chrome-stable indicator-multiload
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.7 MB of archives.
After this operation, 1,114 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable i386 14.0.835.163-r101024 [27.5 MB]
Get:2 http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu/ natty/main indicator-multiload i386 0.2-0+33~14~15~natty1 [163 kB]
Fetched 27.7 MB in 13min 20s (34.6 kB/s)                                                                                           
(Reading database ... 151662 files and directories currently installed.)
Preparing to replace google-chrome-stable 13.0.782.220-r99552 (using .../google-chrome-stable_14.0.835.163-r101024_i386.deb) ...
Unpacking replacement google-chrome-stable ...
Preparing to replace indicator-multiload 0.2-0+33~13~15~natty1 (using .../indicator-multiload_0.2-0+33~14~15~natty1_i386.deb) ...
Unpacking replacement indicator-multiload ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Processing triggers for python-support ...
Setting up google-chrome-stable (14.0.835.163-r101024) ...
Setting up indicator-multiload (0.2-0+33~14~15~natty1) ...
aes@aes-Inspiron-1545:~$

```

Looking good. Now to restart Chrome and see!

Edit: All is good! Thank you!

I'll mark the thread [Solved] but I'd still appreciate knowing more about the output of "sudo apt-get update"

---

### Post by Lisiano on 2011-09-20
**Ign** - No changes in the Diff files, ignoring.
**Get** - Downloading the file
**Hit** - File seems to be the same (Timestamp) so ignoring.

Source: [http://www.linuxquestions.org/questions/debian-26/weird-apt-get-update-output-diffindex-ign-549310/#post3236352](http://www.linuxquestions.org/questions/debian-26/weird-apt-get-update-output-diffindex-ign-549310/#post3236352)

---

### Post by vasa1 on 2011-12-15
> **vasa1 said:**
> Ubuntu 11.04 in Unity mode:
I had downloaded the .deb for Google Chrome (not Chromium) from Google's official site. I used Firefox 6.02 for the download.

After the download was completed, I had to click on Tools, Downloads, and then right-click on the download for Chrome to "open" it. This led to the Ubuntu Software Center (USC) opening with the option to install "Chrome".

**I clicked install but then got a pop-up (modal thingie?) indicating that there was a problem. In a bit of panic, I clicked "okay" but then tried to install again. This time it worked. But is there anyway I can dig out that error message at this time? I should have taken a screenshot at that time but I didn't** :(

On more point ... re. USC
After installing most software, the "install" button changes to "remove". But this time, it showed "reinstall". Confusing ... since Chrome *seems* to be working just fine right now.
This seems to be the message I had got:
"the package might be corrupted or you are not allowed to open the file". It's not important now since subsequent updates have been just fine.

---

