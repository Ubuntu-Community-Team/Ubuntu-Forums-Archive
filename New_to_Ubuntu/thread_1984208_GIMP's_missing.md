---
title: "GIMP's missing"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by czgirb on 2012-05-21
Yesterday, I don;t see my **GIMP** in **Application > Graphic** anymore.
And I tried to re-install the application from **Software Center**.
But when I click install, the following information showed:

> [I]
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/I]


What it means? How can I solve the problem? Please guide me

---

### Post by Lynceus on 2012-05-21
Hello, it seems others have had the same problem on this forum

Try out this thread=> [http://ubuntuforums.org/showthread.php?t=1931201](http://ubuntuforums.org/showthread.php?t=1931201)

If it works, can you please post how you did it.

---

### Post by czgirb on 2012-05-21
> **Rodney9 said:**
> 
Try ```
sudo apt-get update && sudo apt-get upgrade
``` in the terminal.
Rodney

**This is my result**
***@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
***@ubuntu:~$ 


> **sudodus said:**
> 
```
sudo apt-get install gimp
```

***@ubuntu:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: gimp-data (<= 2.6.8-z) but 2.8.0-1ubuntu0ppa4~precise is to be installed
E: Broken packages
***@ubuntu:~$

> **sudodus said:**
> 
```
sudo apt-get purge gimp
``````
sudo apt-get install gimp
```Edit: Did you get any error messages when running the update and upgrade commands suggested by Rodney9

***@ubuntu:~$ sudo apt-get purge gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gimp is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgimp2.0 gimp-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
***@ubuntu:~$

---

### Post by Purplerob on 2012-05-21
Maybe you should try to install it from the ppa:
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

---

### Post by sandyd on 2012-05-21
Have you removed any PPAs recently? 
You are currently having a ppa version conflict, where you have installed gimp from the ppa, then removed it incompletely. Since the version in the ppa is different, Ubuntu just won't install gimp because it is incompatible.

Post output of
```

lsb_release -a
ls /etc/apt/sources.list.d

```

---

### Post by czgirb on 2012-05-22
> **sandyd said:**
> Have you removed any PPAs recently? 
You are currently having a ppa version conflict, where you have installed gimp from the ppa, then removed it incompletely. Since the version in the ppa is different, Ubuntu just won't install gimp because it is incompatible.

Post output of
```

lsb_release -a
ls /etc/apt/sources.list.d

```

***@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

***@ubuntu:~$ ls /etc/apt/sources.list.d
awn-core-ppa-lucid.list
awn-core-ppa-lucid.list.save
awn-testing-ppa-lucid.list
awn-testing-ppa-lucid.list.save
banshee-team-ppa-lucid.list
banshee-team-ppa-lucid.list.save
bisigi-ppa-lucid.list.save
handbrake-ubuntu-ppa-lucid.list
handbrake-ubuntu-ppa-lucid.list.save
happyaron-amule-dlp-lucid.list
happyaron-amule-dlp-lucid.list.save
mozillateam-firefox-next-lucid.list
mozillateam-firefox-next-lucid.list.save
n-muench-firefox-daily-lucid.list
n-muench-firefox-daily-lucid.list.save
otto-kesselgulasch-gimp-precise.list
otto-kesselgulasch-gimp-precise.list.save
sevenmachines-flash-lucid.list
sevenmachines-flash-lucid.list.save
songbird-daily-ppa-lucid.list
songbird-daily-ppa-lucid.list.save
stebbins-handbrake-snapshots-lucid.list
stebbins-handbrake-snapshots-lucid.list.save
tualatrix-ppa-lucid.list
tualatrix-ppa-lucid.list.save
ubuntu-mozilla-daily-firefox-aurora-oneiric.list
ubuntu-mozilla-daily-firefox-aurora-oneiric.list.save
ubuntu-tweak-stable.list.save
ubuntu-tweak-testing-ppa-lucid.list.save
ubuntu-wine-ppa-lucid.list.save

> banshee-team-ppa-lucid.list
banshee-team-ppa-lucid.list.save
I installed banshee ... but it was removed a month ago.
How can it be there?

> happyaron-amule-dlp-lucid.list
happyaron-amule-dlp-lucid.list.save
n-muench-firefox-daily-lucid.list
n-muench-firefox-daily-lucid.list.save
otto-kesselgulasch-gimp-precise.list
otto-kesselgulasch-gimp-precise.list.save
sevenmachines-flash-lucid.list
sevenmachines-flash-lucid.list.save
songbird-daily-ppa-lucid.list
songbird-daily-ppa-lucid.list.save
What is this? Songbird? It never installed.

---

### Post by czgirb on 2012-05-22
> **Purplerob said:**
> Maybe you should try to install it from the ppa:
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

***@ubuntu:~$ sudo add-apt-repository ppa:otto-kesselgulasch/gimp
[sudo] password for ***: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv FB97E9C3A97F85C095AEA7903BDAAC08614C4B38
gpg: requesting key 614C4B38 from hkp server keyserver.ubuntu.com
gpg: key 614C4B38: "Launchpad otto06217" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

***@ubuntu:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://ppa.launchpad.net/n-muench/firefox-daily/ubuntu/](http://ppa.launchpad.net/n-muench/firefox-daily/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/) lucid/main Translation-en_US
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316B]            
Ign [http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/) oneiric/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,771B]                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [412kB]          
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Packages [9,056B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  404  Not Found
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]             
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB]              
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,855B]                                                                              
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [122kB]                                                                                      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,259B]                                                                               
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [130kB]                                                                                 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [40.5kB]                                                                                 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,368B]                                                                              
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,323B]                                                                               
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,208B]                                                                                     
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                                                                                             
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B]                                                                                      
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB]                                                                                      
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]                                                                                       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]                                                                                      
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]                                                                                       
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [613kB]                                                                                    
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,617B]                                                                             
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [221kB]                                                                                     
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,194B]                                                                              
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [269kB]                                                                                
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [99.6kB]                                                                                
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.3kB]                                                                             
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,537B]                                                                              
Fetched 13.1MB in 3min 24s (64.0kB/s)                                                                                                                      
W: Failed to fetch [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

***@ubuntu:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: gimp-data (<= 2.6.8-z) but 2.8.0-1ubuntu0ppa4~precise is to be installed
E: Broken packages

---

### Post by buzzingrobot on 2012-05-22
Using PPA's involves a degree of risk. if nothing else, you are giving the PPA owner administrative access to your system.  Not to be paranoid, but when you grabbed gimp 2.8 off that PPA, how did you know it was really gimp?  When you do installs from official repositories, you are entitled to assume everything has been tested and works on a stock Ubuntu system.  Adding PPA's to your sources.list means you are not running a stock system.  Neither Ubuntu nor the PPA's developer can test for your configuration because they can't know what it is.

It seems apt wants to install dependencies for Gimp 2.6 but also needs to handle the 2.8 version that's in the PPA. Files needed for one version rule out using  files the other version needs, so apt can do nothing except complain. 

If it's 2.8 you want to use, be sure you've removed and purged all of 2.6.

---

### Post by czgirb on 2012-05-23
> **buzzingrobot said:**
> Using PPA's involves a degree of risk. if nothing else, you are giving the PPA owner administrative access to your system.  Not to be paranoid, but when you grabbed gimp 2.8 off that PPA, how did you know it was really gimp?  When you do installs from official repositories, you are entitled to assume everything has been tested and works on a stock Ubuntu system.  Adding PPA's to your sources.list means you are not running a stock system.  Neither Ubuntu nor the PPA's developer can test for your configuration because they can't know what it is.

It seems apt wants to install dependencies for Gimp 2.6 but also needs to handle the 2.8 version that's in the PPA. Files needed for one version rule out using  files the other version needs, so apt can do nothing except complain. 

If it's 2.8 you want to use, be sure you've removed and purged all of 2.6.

I  never care it was 2.6 or 2.8 ... all I want is have my GIMP back.
Cos I need this software to do my work. Please guide me, bro!

---

### Post by jtarin on 2012-05-23
Two sources:

[Instructions]("http://www.techdrivein.com/2010/06/install-new-gimp-269-in-ubuntu-1004.html")
[Source]("http://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid")

[Instructions]("http://www.howtogeek.com/howto/12047/install-gimp-2.7.1-on-lucid-lynx-using-ppa/")
[Source]("http://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn?field.series_filter=lucid)

Remove: ppa: otto-kesselgulasch/gimp

---

### Post by sandyd on 2012-05-23
Use ppa-purge to purge the ppa.
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:otto-kesselgulasch/gimp
```

---

