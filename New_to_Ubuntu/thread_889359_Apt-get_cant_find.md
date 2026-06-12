---
title: "Apt-get cant find???"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Drezard on 2008-08-14
Hello,

Im running Linux Ubuntu server 8.04 or 2.6.24-12-server i think they are one and the same. Now, when i try and run:

> 
sudo apt-get install build-essential linux-headers-`uname -r` xinetd


it says it cant find the linux-headers-... bit. 

Why is that? what can I do to fix this?

Daniel

---

### Post by ercferret18 on 2008-08-14
it is saying that there isn't a package with that name that it knows of... try doing 'sudo apt-get update'

---

### Post by Mister.Vash on 2008-08-14
one other thing to double check is to make that the grave accent is coming across correctly

from the terminal do
uname -r

which should output something along the lines of
2.6.24-20-generic

after doing that, do the command to get the headers again
sudo apt-get install linux-headers-`uname -r`

if it doesn't come back with something like this where it combines the linux-headers and the uname output, the accents around uname -r are not correct
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-20-generic

---

### Post by iaculallad on 2008-08-14
-Disregard-

---

### Post by Drezard on 2008-08-14
Heres the exact output. I added the apt-get update to make sure im not missing anything there either...

> 
administrator@virtualserver:/etc/apt$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release.gpg                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_AU                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_AU                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_AU            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_AU              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_AU            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Translation-en_AU               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Translation-en_AU                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports Release                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Sources     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/multiverse Sources
Reading package lists... Done                           
administrator@virtualserver:/etc/apt$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.24-12-server



---

### Post by y@w on 2008-08-14
Did you install a custom kernel? Mine is at 2.6.24-16 and I'm on a default 8.04 server install. Looks to me like the Hardy repositories only go back to 2.6.24-14, not -12.

```
aptitude search linux-headers
v   linux-headers                                                                                    -                                                                                                           
v   linux-headers-2.6                                                                                -                                                                                                           
i   linux-headers-2.6.22-14                                                                          - Header files related to Linux kernel version 2.6.22                                                       
i   linux-headers-2.6.22-14-generic                                                                  - Linux kernel headers for version 2.6.22 on x86/x86_64                                                     
p   linux-headers-2.6.24-16                                                                          - Header files related to Linux kernel version 2.6.24                                                       
p   linux-headers-2.6.24-16-386                                                                      - Linux kernel headers for version 2.6.24 on i386                                                           
p   linux-headers-2.6.24-16-generic                                                                  - Linux kernel headers for version 2.6.24 on x86/x86_64                                                     
p   linux-headers-2.6.24-16-openvz                                                                   - Linux kernel headers for version 2.6.24 on OpenVZ Virtualization enabled kernel                           
p   linux-headers-2.6.24-16-rt                                                                       - Linux kernel headers for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.3-rt3)   
p   linux-headers-2.6.24-16-server                                                                   - Linux kernel headers for version 2.6.24 on x86/x86_64                                                     
p   linux-headers-2.6.24-16-virtual                                                                  - Linux kernel headers for version 2.6.24 on x86                                                            
p   linux-headers-2.6.24-16-xen                                                                      - Linux kernel headers for version 2.6.24 on This kernel can be used for Xen dom0 and domU                  
p   linux-headers-2.6.24-18                                                                          - Header files related to Linux kernel version 2.6.24                                                       
p   linux-headers-2.6.24-18-386                                                                      - Linux kernel headers for version 2.6.24 on i386                                                           
p   linux-headers-2.6.24-18-generic                                                                  - Linux kernel headers for version 2.6.24 on x86/x86_64                                                     
p   linux-headers-2.6.24-18-openvz                                                                   - Linux kernel headers for version 2.6.24 on OpenVZ Virtualization enabled kernel                           
p   linux-headers-2.6.24-18-rt                                                                       - Linux kernel headers for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.3-rt3)   
p   linux-headers-2.6.24-18-server                                                                   - Linux kernel headers for version 2.6.24 on x86/x86_64                                                     
p   linux-headers-2.6.24-18-virtual                                                                  - Linux kernel headers for version 2.6.24 on x86                                                            
p   linux-headers-2.6.24-18-xen                                                                      - Linux kernel headers for version 2.6.24 on This kernel can be used for Xen dom0 and domU                  
i   linux-headers-2.6.24-19                                                                          - Header files related to Linux kernel version 2.6.24                                                       
p   linux-headers-2.6.24-19-386                                                                      - Linux kernel headers for version 2.6.24 on i386                                                           
i   linux-headers-2.6.24-19-generic                                                                  - Linux kernel headers for version 2.6.24 on x86/x86_64                                                     
p   linux-headers-2.6.24-19-openvz                                                                   - Linux kernel headers for version 2.6.24 on OpenVZ Virtualization enabled kernel                           
p   linux-headers-2.6.24-19-rt                                                                       - Linux kernel headers for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.3-rt3)   
p   linux-headers-2.6.24-19-server                                                                   - Linux kernel headers for version 2.6.24 on x86/x86_64                                                     
p   linux-headers-2.6.24-19-virtual                                                                  - Linux kernel headers for version 2.6.24 on x86                                                            
p   linux-headers-2.6.24-19-xen                                                                      - Linux kernel headers for version 2.6.24 on This kernel can be used for Xen dom0 and domU                  
p   linux-headers-386                                                                                - Linux kernel headers on 386                                                                               
p   linux-headers-686                                                                                - Upgrade dummy package. Can be removed                                                                     
i   linux-headers-generic                                                                            - Generic Linux kernel headers                                                                              
p   linux-headers-k7                                                                                 - Upgrade dummy package. Can be removed                                                                     
v   linux-headers-lbm                                                                                -                                                                                                           
v   linux-headers-lbm-2.6                                                                            -                                                                                                           
p   linux-headers-lbm-2.6.24-16-386                                                                  - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-16-generic                                                              - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-16-openvz                                                               - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-16-rt                                                                   - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-16-server                                                               - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-16-virtual                                                              - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-16-xen                                                                  - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-18-386                                                                  - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-18-generic                                                              - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-18-openvz                                                               - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-18-rt                                                                   - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-18-server                                                               - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-18-virtual                                                              - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-18-xen                                                                  - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-19-386                                                                  - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-19-generic                                                              - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-19-openvz                                                               - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-19-rt                                                                   - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-19-server                                                               - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-19-virtual                                                              - Header files related to linux-backports-modules version 2.6.24                                            
p   linux-headers-lbm-2.6.24-19-xen                                                                  - Header files related to linux-backports-modules version 2.6.24                                            
v   linux-headers-lum                                                                                -                                                                                                           
v   linux-headers-lum-2.6                                                                            -                                                                                                           
p   linux-headers-lum-2.6.24-16-386                                                                  - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-16-generic                                                              - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-16-openvz                                                               - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-16-rt                                                                   - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-16-server                                                               - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-16-virtual                                                              - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-16-xen                                                                  - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-18-386                                                                  - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-18-generic                                                              - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-18-openvz                                                               - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-18-rt                                                                   - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-18-server                                                               - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-18-virtual                                                              - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-18-xen                                                                  - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-19-386                                                                  - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-19-generic                                                              - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-19-openvz                                                               - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-19-rt                                                                   - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-19-server                                                               - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-19-virtual                                                              - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-lum-2.6.24-19-xen                                                                  - Header files related to linux-ubuntu-modules version 2.6.24                                               
p   linux-headers-openvz                                                                             - openvz Linux kernel headers                                                                               
p   linux-headers-rt                                                                                 - rt Linux kernel headers                                                                                   
p   linux-headers-server                                                                             - Linux kernel headers on Server Equipment.                                                                 
p   linux-headers-virtual                                                                            - Linux kernel headers for the virtual flavour                                                              
p   linux-headers-xen                                                                                - xen Linux kernel headers   
```

---

### Post by prshah on 2008-08-14
> **Drezard said:**
> 
it says it cant find the linux-headers-... bit. 


Just install linux-headers; it is a meta-package (virtual package) that will choose and install the correct headers for your system. ```
sudo apt-get install linux-headers
```

EDIT: Nope sorry, this doesn't work.

---

### Post by mcduck on 2008-08-14
Actually you should just get the "linux-server" metapackage, which depends on lates versions of _all_ kernel-related packages (kernel image, headers & restricted modules).

---

### Post by Mister.Vash on 2008-08-17
Like y@w said earlier, I could not find the linux-headers- for your version in the repositories either - do you have a specific reason for running on your current kernel version?  If not try updating to the latest version.
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Riffer on 2008-08-17
Sometimes it could be a problem with the server, try changing it.  You do this by going to drop down menu System > Administration > Software Sources.

---

### Post by cariboo on 2008-08-18
I looks like your are in for a kernel up grade. From y@w's listing your kernel is not supported any more, have you been doing updates or just putting them off? The current hardy server kernel version is:

```
2.6.24-19
```

Jim

---

