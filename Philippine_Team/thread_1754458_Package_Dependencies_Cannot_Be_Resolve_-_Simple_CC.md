---
title: "Package Dependencies Cannot Be Resolve - Simple CCSM Error"
date: 2011-05-10
forum: Philippine Team
---

### Post by galingsabundok on 2011-05-10
pa help po anu po pwede ko gawin kasi d po ma install yung Simple CCSM bago lang po ako user nang ubuntu... salamat po sa makaka tulong sa problema ko...ito po sabi "**This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time**."

---

### Post by tech-hero on 2011-05-10
[https://bugs.launchpad.net/ubuntu/+source/simple-ccsm/+bug/738168](https://bugs.launchpad.net/ubuntu/+source/simple-ccsm/+bug/738168)
 
I guess you are not the only one encountering this problem with natty.

---

### Post by galingsabundok on 2011-05-10
dome threads suggest 10.10 is good, im downloading it now... maybe because 11.04 is a new release and it still has bugs...thanks for the reply...

---

### Post by tech-hero on 2011-05-10
> **galingsabundok said:**
> dome threads suggest 10.10 is good, im downloading it now... maybe because 11.04 is a new release and it still has bugs...thanks for the reply...
yup. 10.04 and 10.10 are so far the best UBUNTU versions for me. thanks.

---

### Post by jepong on 2011-05-10
> **galingsabundok said:**
> pa help po anu po pwede ko gawin kasi d po ma install yung Simple CCSM bago lang po ako user nang ubuntu... salamat po sa makaka tulong sa problema ko...ito po sabi "**This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time**."

do you install via Software Center? try mo kaya sa terminal...

> sudo apt-get install simple-ccsm

---

### Post by antoniomiguel on 2011-05-14
you may also want to run this on a terminal:

*sudo apt-get update --fix-missing*

---

### Post by JCyberinux on 2011-05-15
Try first to uninstall conflicting packages. and also retry to reinstall simple ccsm packages. Maybe that should give the trick.

---

### Post by SignedAdam on 2011-06-20
> user@ubuntu:~$ sudo apt-get update --fix-missing
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB    
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,351 B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,252 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 2,801 B in 3s (765 B/s)
Reading package lists... Done


user@ubuntu:~$ sudo apt-get install simple-ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages
user@ubuntu:~$ 


I'm using Ubuntu 11.04 on a HP Mini 110-3100
I also tried the Ubuntu Software Center, but get the same error every time, Package Dependencies Cannot Be Resolve

---

### Post by Script Warlock on 2011-06-21
try sudo apt-get -f install or
install compizconfig-settings-manager.

---

### Post by beneathnylon on 2011-08-17
> **SignedAdam said:**
> I'm using Ubuntu 11.04 on a HP Mini 110-3100
I also tried the Ubuntu Software Center, but get the same error every time, Package Dependencies Cannot Be Resolve

I got the same error.
I am in ubuntu classic.


beneathnylon@ubuntu:~$ sudo apt-get install simple-ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages
beneathnylon@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by beneathnylon on 2011-08-17
> **beneathnylon said:**
> I got the same error.
I am in ubuntu classic.


beneathnylon@ubuntu:~$ sudo apt-get install simple-ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages
beneathnylon@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I found my solution.

From the "Ubuntu Software Center"
Search for "compiz"

You will need to install "Advanced Desktop Effects Settings (ccsm)"
-> this will configure Compize with CompizConfig

To configure Compiz - WATCH THIS VIDEO FIRST
[http://www.youtube.com/watch?v=O-iYoy1BGak](http://www.youtube.com/watch?v=O-iYoy1BGak)
-> be sure the reed the description.  Important info.

---

### Post by video editor on 2011-08-26
i have ubuntu10.04 and tried these fixes but no luck. trying to install plasma workspace

---

