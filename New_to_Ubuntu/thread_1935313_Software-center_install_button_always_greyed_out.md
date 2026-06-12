---
title: "Software-center install button always greyed out"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by DisappearingOak on 2012-03-04
Mine is a Ubuntu 11.10 fresh install, and since the beginning I've noticed that I can't install any software from the Software Center because the install button is always greyed out and unclickable. What could the problem be? Also, sometimes when I'm doing something, a dialog box pops up saying that the login-keyring did not get unlocked when I logged in and tells me to input my password. What does this mean?

Also, I can't get the wallpaper on my desktop to change when right-clicking an image and setting to to wallpaper, but setting the wallpaper in the 'change desktop background' option works but I can't use anything other than the default wallpapers. What do I do?

---

### Post by Diametric on 2012-03-04
It sounds as if you're not remembering the root account/password you created upon installation.  When you install Ubuntu, it asks for both user account credentials and root credentials.  Try that and see if it works.

---

### Post by raja.genupula on 2012-03-04
for login keyring issue 
[http://ubuntuforums.org/showthread.php?t=1533830](http://ubuntuforums.org/showthread.php?t=1533830)

are you able to install any software from terminal  ?

please give me the output of ```
sudo apt-get update
```.

---

### Post by DisappearingOak on 2012-03-04
> **raja.genupula said:**
> for login keyring issue 
[http://ubuntuforums.org/showthread.php?t=1533830](http://ubuntuforums.org/showthread.php?t=1533830)

are you able to install any software from terminal  ?

please give me the output of ```
sudo apt-get update
```.

I can download .deb packages and install with the dpkg command, but I'm not sure about other methods.
Here's the output: 
```
oak@Oak:~$ sudo apt-get update
[sudo] password for oak: 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://in.archive.ubuntu.com oneiric InRelease                             
Ign http://in.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://in.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://in.archive.ubuntu.com oneiric Release.gpg                 
Ign http://security.ubuntu.com oneiric-security InRelease            
Ign http://ppa.launchpad.net oneiric Release.gpg                     
Hit http://extras.ubuntu.com oneiric Release.gpg                     
Hit http://in.archive.ubuntu.com oneiric-updates Release.gpg         
Hit http://security.ubuntu.com oneiric-security Release.gpg          
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://in.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://ppa.launchpad.net oneiric Release                         
Hit http://in.archive.ubuntu.com oneiric Release                     
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://in.archive.ubuntu.com oneiric-updates Release             
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://in.archive.ubuntu.com oneiric-backports Release           
Hit http://in.archive.ubuntu.com oneiric/main Sources                          
Hit http://in.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://in.archive.ubuntu.com oneiric/universe Sources                      
Hit http://in.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://in.archive.ubuntu.com oneiric/main amd64 Packages         
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://in.archive.ubuntu.com oneiric/restricted amd64 Packages   
Hit http://in.archive.ubuntu.com oneiric/universe amd64 Packages     
Hit http://in.archive.ubuntu.com oneiric/multiverse amd64 Packages   
Hit http://in.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://in.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://in.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://in.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://in.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://in.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/main Translation-en  
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://in.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://in.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://in.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://in.archive.ubuntu.com oneiric-updates/main amd64 Packages 
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://in.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://in.archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://in.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://in.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://in.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://in.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://in.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://in.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://in.archive.ubuntu.com oneiric-backports/main Sources      
Hit http://in.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://in.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://in.archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://in.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://in.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://in.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://in.archive.ubuntu.com oneiric/main Translation-en         
Hit http://in.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://in.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://in.archive.ubuntu.com oneiric/universe Translation-en     
Hit http://in.archive.ubuntu.com oneiric-updates/main Translation-en 
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://in.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://in.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://in.archive.ubuntu.com oneiric-backports/restricted Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://in.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
oak@Oak:~$ 

```

---

### Post by Jake5 on 2012-03-04
Just trying to learn here, sorry to interject, looks to me like the machine is trying to download the 32 bit and 64 bit packages. Is this correct, raja? it also looks like you figured out what your password was, so congrats. Is this another case where ```
sudo apt-get remove
sudo apt-get install
``` is going to be the resolver? Just trying to learn, don't run these commands. Very interested and I won't ask any more questions, but I am gonna keep an eye on this.

---

### Post by raja.genupula on 2012-03-04
@Jake yes .
@op you have to switch your update manager server .
open update manager -> settings -> at 1st TAB look you'll found something like download from at that change your mirror to main server or best server from your location.

do this also 

```
sudo apt-get install --reinstall software-center
```

all the best .

---

### Post by DisappearingOak on 2012-03-04
> **raja.genupula said:**
> @Jake yes .
@op you have to switch your update manager server .
open update manager -> settings -> at 1st TAB look you'll found something like download from at that change your mirror to main server or best server from your location.

do this also 

```
sudo apt-get install --reinstall software-center
```

all the best .

I did both of the above; set the server to main and reinstalled the software center. Did not fix the issue. Any other ideas?

---

### Post by raja.genupula on 2012-03-04
> a dialog box pops up saying that the login-keyring 

actually if you got like that then you have to  give your password . 

and for software center issue [http://ubuntuforums.org/showthread.php?t=1340014&page=2](http://ubuntuforums.org/showthread.php?t=1340014&page=2)

---

### Post by DisappearingOak on 2012-03-08
> **raja.genupula said:**
> actually if you got like that then you have to  give your password . 

and for software center issue [http://ubuntuforums.org/showthread.php?t=1340014&page=2](http://ubuntuforums.org/showthread.php?t=1340014&page=2)

Hi, I searched online and it seems the problem in Software Center is due to internet access. Software Center says there is no internet connection present. I connect with wvdial software since network manager doesn't work with my wireless modem. But I can browse the web and use apt-get just fine. Is there a way to get Software Center to work? :(

---

