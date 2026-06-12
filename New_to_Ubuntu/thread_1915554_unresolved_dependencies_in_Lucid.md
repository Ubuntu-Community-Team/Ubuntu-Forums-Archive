---
title: "unresolved dependencies in Lucid"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-01-26
I have a couple of programs that won't install because of unresolved dependencies.
Am at a loss as to how to resolve this problem. Any ideas?:confused:

---

### Post by ngubk on 2012-01-26
What are those programs? Sometimes, it's maybe because these dependent packages are not in your repository. Try using
 ```
sudo apt-get your_program_name
```
and post the result here.

---

### Post by Bumpalot on 2012-01-26
bump@bumpyputer:~/Downloads$ sudo apt-get teamviewer_linux_x64.deb
[sudo] password for bump: 
E: Invalid operation teamviewer_linux_x64.deb
bump@bumpyputer:~/Downloads$

---

### Post by oldos2er on 2012-01-26
Have you tried double-clicking the *.deb file?

---

### Post by Bumpalot on 2012-01-26
On double-click Deb Installer reports: Error: Cannot Install 'lib32asound2'
Searchec Synaptic - tried to mark the file for installation, got message "Could not mark all packages for installation or upgrade ... because listed packages have unresolved dependencies & displays the following list
lib32asound2-dev:
 Depends: lib32asound2 but it is not going to be installed
  Depends: libasound2-dev (=1.0.22-0ubuntu7) but 1.0.24.1-0ubuntu6~lucid1 is to be installed

---

### Post by oldos2er on 2012-01-26
Can you run ```
sudo apt-get update && sudo apt-get install lib32asound2
``` in a terminal, and if there are errors, post them here?

---

### Post by Bumpalot on 2012-01-26
bump@bumpyputer:~$ sudo apt-get update && sudo apt-get install lib32asound2
[sudo] password for bump: 
Ign cdrom://[APTonCD for ubuntu lucid - amd64 (2012-01-19 07:34) DVD1]  Release.gpg
Ign cdrom://[APTonCD for ubuntu lucid - amd64 (2012-01-19 07:34) DVD1]/  Translation-en_CA
Ign cdrom://[APTonCD for ubuntu lucid - amd64 (2012-01-19 07:34) DVD1]  Release
Hit [http://apt.spideroak.com](http://apt.spideroak.com) release Release.gpg                               
Ign [http://apt.spideroak.com/ubuntu-spideroak-hardy/](http://apt.spideroak.com/ubuntu-spideroak-hardy/) release/restricted Translation-en_CA
Hit [http://apt.spideroak.com](http://apt.spideroak.com) release Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) lucid/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA          
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA      
Ign [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted Packages                       
Ign [http://ppa.launchpad.net/inkscape.dev/trunk/ubuntu/](http://ppa.launchpad.net/inkscape.dev/trunk/ubuntu/) lucid/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release                                 
Hit [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release [57.3kB]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages [550kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources [210kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages [259kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources [86.5kB]
Fetched 1,163kB in 4s (248kB/s)                   
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  lib32asound2: Depends: libasound2 (= 1.0.22-0ubuntu7)
E: Broken packages
bump@bumpyputer:~$

---

### Post by hhh on 2012-01-26
> **Bumpalot said:**
> bump@bumpyputer:~/Downloads$ sudo apt-get teamviewer_linux_x64.deb
This will only work with a package from a repository in your sources.list, and the syntax is sudo apt-get *install* teamviewer.

What is "spideroak", why is it showing "hardy" (an old Ubuntu relelase) and what's it doing in your sources.list?

In short, you sources.list is kind of a mess. Both lib32asound2 and libasound2 are in the Lucid repo and should install no problem...
[http://packages.ubuntu.com/lucid/lib32asound2](http://packages.ubuntu.com/lucid/lib32asound2)
[http://packages.ubuntu.com/lucid/libasound2](http://packages.ubuntu.com/lucid/libasound2)

I'd suggest backing up your sources.list, generating a new one using the following links and then using the final link's instructions to try installing TeamViewer again...

Info on /etc/apt/sources.list...
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

sources.list generator (don't go nuts with this, keep it simple to start and add sources later and carefully as you need them!!!)...
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Install TeamViewer in Lucid...
[http://www.liberiangeek.net/2010/07/install-teamviewer-5-ubuntu-10-04-lucid-lynx-connect-windows/](http://www.liberiangeek.net/2010/07/install-teamviewer-5-ubuntu-10-04-lucid-lynx-connect-windows/)

Post back with questions or problems, someone will sort you out.

***EDIT*** I went ahead and input Canada, Lucid and the official main and security repos in the generator and it came back with this...```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
```
That should be suitable for at least 90% of what you'd want to install. Add your PPA sources with care. Cheers.

---

