---
title: "Something broken"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by jayrjay on 2012-02-02
This ubuntu is giving me as much (well maybe not as much) trouble as windows. I open update manager to download updates and got this.

  	 	 	 	 	 	   

 [LEFT][FONT=Arial][COLOR=Blue]The package system is broken [/COLOR][/FONT]
[FONT=Arial][COLOR=Blue] [/COLOR][/FONT]
 
[FONT=Arial][COLOR=Blue] [/COLOR][/FONT]
[FONT=Arial][COLOR=Blue]If you are using third party repositories then disable them, since they are a common source of problems. [/COLOR][/FONT]
[FONT=Arial][COLOR=Blue] [/COLOR][/FONT]
[FONT=Arial][COLOR=Blue]Now run the following command in a terminal: apt-get install -f[/COLOR][/FONT]
[FONT=Arial][COLOR=Blue] [/COLOR][/FONT][/LEFT]


  No idea what all that means but I ran apt-get install -f and it told me that it was broken?

So I clicked on the details part of the message and this is what I got

  	 	 	 	 	 	   [COLOR=Blue]The following packages have unmet dependencies: [/COLOR]
[COLOR=Blue] [/COLOR] 
[COLOR=Blue] [/COLOR][COLOR=Blue]libnux-1.0-0: Depends: libnux-1.0-common (= 1.16.0-0ubuntu1) but 1.16.0-0ubuntu1.1 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libglib2.0-0 (>= 2.25.14) but 2.30.0-0ubuntu4 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libpango1.0-0 (>= 1.18.0) but 1.29.3+git20110916-0ubuntu1 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libpcre3 (>= 8.10) but 8.12-3ubuntu2 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libsigc++-2.0-0c2a (>= 2.0.2) but 2.2.10-0ubuntu1 is installed [/COLOR]
[COLOR=Blue] [/COLOR][COLOR=Blue]              Depends: libstdc++6 (>= 4.6) but 4.6.1-9ubuntu3 is installed [/COLOR]
[COLOR=Blue]  [/COLOR]
Can anybody help? Thanks :confused:

---

### Post by oldos2er on 2012-02-02
Can you run ```
sudo apt-get update
``` and post all the terminal output here?

---

### Post by linuxsyst on 2012-02-02
Open your "synaptic package manager" then to edit then fix broken packages and exit, then open software sources and try reloading your dependancies list and it will display the errors, save the errors to a text file (to remember) then one by one edit/delet the problem PPA's but be carefull.

If you have not put in your own PPA's then just try fix broken packages and then a clean via computer janitor.

P.S. Try Ubuntu tweak it makes a lot of things easier.
[http://ubuntu-tweak.com](http://ubuntu-tweak.com)

---

### Post by jayrjay on 2012-02-02
> **oldos2er said:**
> Can you run ```
sudo apt-get update
``` and post all the terminal output here?

HI here is the result.

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources     
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_GB         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release.gpg            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main TranslationIndex
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en_GB
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en
Reading package lists... Done


Lot of it! Hope it makes sense

---

### Post by jayrjay on 2012-02-02
> **linuxsyst said:**
> Open your "synaptic package manager" then to edit then fix broken packages and exit, then open software sources and try reloading your dependancies list and it will display the errors, save the errors to a text file (to remember) then one by one edit/delet the problem PPA's but be carefull.

If you have not put in your own PPA's then just try fix broken packages and then a clean via computer janitor.

P.S. Try Ubuntu tweak it makes a lot of things easier.
[http://ubuntu-tweak.com](http://ubuntu-tweak.com)

Hi the ubuntu tweak sounded good but unfortunately I am using 11.10 and it only does 11.04 or earlier, still will try to find packet manager and have a go.:-k

---

### Post by oldos2er on 2012-02-02
'apt-get update' output looks ok. Can you try the same thing with ```
sudo apt-get upgrade
``` ?

---

### Post by linuxsyst on 2012-02-02
> **oldos2er said:**
> 'apt-get update' output looks ok. Can you try the same thing with ```
sudo apt-get upgrade
``` ?
Yes try to do what he said it might help but idk whats the problem it would need to work try to do ```
apt-get install -f
``` again maybe will work and if nothing helps do what I wrote in the 3rd post :/ I had that problem 1 time i think

---

### Post by jayrjay on 2012-02-03
> **oldos2er said:**
> 'apt-get update' output looks ok. Can you try the same thing with ```
sudo apt-get upgrade
``` ?

Hi did that and got

[COLOR=Blue]john@john-Ubuntu:~$ sudo apt-get upgrade
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 libnux-1.0-0 : Depends: libnux-1.0-common (= 1.16.0-0ubuntu1) but 1.16.0-0ubuntu1.1 is installed
E: Unmet dependencies. Try using -f.
[/COLOR]
So tried [COLOR=Black]apt-get -f install and got

[COLOR=Blue]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[/COLOR]
Thanks for looking :confused:

[/COLOR]

---

### Post by jayrjay on 2012-02-03
> **linuxsyst said:**
> Open your "synaptic package manager" then to edit then fix broken packages and exit, then open software sources and try reloading your dependancies list and it will display the errors, save the errors to a text file (to remember) then one by one edit/delet the problem PPA's but be carefull.

If you have not put in your own PPA's then just try fix broken packages and then a clean via computer janitor.

P.S. Try Ubuntu tweak it makes a lot of things easier.
[http://ubuntu-tweak.com](http://ubuntu-tweak.com)

Hi apparently synaptic package manager is not in 11.10 when I tried to download it from the market I got error tried apt-get but errors again. I think ubuntu has gone really wrong feel a reinstall is the only answer

---

### Post by jayrjay on 2012-02-03
Hi all well I've fixed it not sure how but here is the tale. Looking for similar problem I came across this [http://ubuntuforums.org/showthread.php?t=1876961](http://ubuntuforums.org/showthread.php?t=1876961)
It was similar but not the same result, oldos2er gave a very short answer that was

                                  **Re: Can't install from software center**             
                                                                     Code:
     sudo apt-get clean 
 cd /var/lib/apt
 sudo mv lists lists.old 
 sudo mkdir -p lists/partial
 sudo apt-get clean 
 sudo apt-get update 

So I copied and pasted the code (well what was the worst that could happen?) and lo and behold market worked and software updater worked.
So thanks all who helped me it is much appreciated, but hats off to oldos2er 
:popcorn:

---

