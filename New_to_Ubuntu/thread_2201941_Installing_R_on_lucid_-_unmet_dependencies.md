---
title: "Installing R on lucid - unmet dependencies"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by Philip_Reed on 2014-01-26
I would like to install the R programming language, and then RStudio. Following directions at [http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README), I've tried three different mirrors (the last two with similar results). After adding the mirror to my sources.list, and attempting a [FONT=courier new]sudo apt-get update[/FONT], I get the following: 


```
$ sudo apt-get update
Ign http://cran.stat.ucla.edu lucid/ Release.gpg
Ign http://cran.stat.ucla.edu/CRAN/bin/linux/ubuntu/ lucid/ Translation-en_US  
Ign http://cran.stat.ucla.edu lucid/ Release                                   
Ign http://cran.stat.ucla.edu lucid/ Packages                       
Hit http://security.ubuntu.com precise-security Release.gpg         
Ign http://security.ubuntu.com/ubuntu/ precise-security/main Translation-en_US 
Ign http://security.ubuntu.com/ubuntu/ precise-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ precise-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ precise-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Ign http://us.archive.ubuntu.com/ubuntu/ precise/main Translation-en_US        
Ign http://us.archive.ubuntu.com/ubuntu/ precise/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ precise/universe Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ precise/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted Translation-en_US
Ign http://cran.stat.ucla.edu lucid/ Packages                                  
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse Translation-en_US
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://archive.canonical.com/ precise/partner Translation-en_US            
Hit http://archive.canonical.com precise Release.gpg                           
Err http://cran.stat.ucla.edu lucid/ Packages                                  
  404  Not Found
Hit http://security.ubuntu.com precise-security Release                        
Hit http://us.archive.ubuntu.com precise Release                     
Ign http://archive.canonical.com/ubuntu/ precise/partner Translation-en_US     
Hit http://archive.canonical.com precise Release                     
Hit http://security.ubuntu.com precise-security/main Packages                  
Hit http://us.archive.ubuntu.com precise-updates Release             
Hit http://archive.canonical.com precise Release                               
Hit http://security.ubuntu.com precise-security/restricted Packages            
Hit http://security.ubuntu.com precise-security/main Sources         
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Packages    
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Packages  
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://us.archive.ubuntu.com precise/main Packages
Hit http://us.archive.ubuntu.com precise/restricted Packages
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Packages
Hit http://archive.canonical.com precise/partner Packages
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Packages
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise-updates/main Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted Packages
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Packages
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://us.archive.ubuntu.com precise-updates/multiverse Packages
Hit http://archive.canonical.com precise/partner Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
W: Failed to fetch http://cran.stat.ucla.edu/CRAN/bin/linux/ubuntu/lucid/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

Unsure of whether this is a really a problem or not (it had been missing on another mirror, too), I press on: 

```
sudo apt-get install r-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libasound2: Breaks: libasound2-plugins (< 1.0.24) but 1.0.22-0ubuntu6 is to be installed
  libglib2.0-0: Breaks: gnome-control-center (< 1:3) but 1:2.30.1-0ubuntu1 is to be installed
                Breaks: gvfs (< 1.8) but 1.6.1-0ubuntu1build1 is to be installed
  libgstreamer-plugins-bad0.10-0: Breaks: gstreamer0.10-plugins-bad (< 0.10.22.3-2) but 0.10.18-1ubuntu1 is to be installed
  libpango1.0-0: Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu2 is to be installed
  ppp: Breaks: network-manager (<= 0.8.0.999-1) but 0.8-0ubuntu3 is to be installed
       Breaks: network-manager-pptp (<= 0.8.0.999-1) but 0.8-0ubuntu3 is to be installed
E: Broken packages


```

Ubuntu version is

```
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid


```
What's the next step?

(I'm not sure if this is an Absolute Beginners question, but I'm pretty new to Ubuntu and feel totally incompetent any time these dependency issues arise, so hopefully this is the right place.)

---

### Post by grahammechanical on 2014-01-26
Now, here is a strange thing. You are runing Ubuntu 10.04 (Lucid Lynx) but your repositories are those of Ubuntu 12.04 (precise pangolin). There is another strange thing in that README document that you link to.

> R packages for Ubuntu on i386 and amd64 are available for all stable
Desktop releases of Ubuntu _until their official end of life date_.
However, only the latest Long Term Support (LTS) release is fully
supported.  [COLOR=#222222][FONT=Verdana]

[SIZE=2]But the readme document goes on to say
[/SIZE]
[/FONT][/COLOR]> 
As of October 17, 2013, the supported releases are Saucy
Saucy Salamander (13.10), Raring Ringtail (13.04), Quantal Quetzal 
(12.10), Precise Pangolin (12.04; LTS), and _Lucid Lynx (10.04; LTS_).[COLOR=#222222][FONT=Verdana]

[SIZE=2]Ubuntu 10.04 reached end of life May 9th 2013. Unless this is a server edition that you are using.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

What the unmet dependencies message is telling you is that there are packages on your system that depend on newer packages than the ones that you are going to install. 

Regards.[/SIZE][/FONT][/COLOR]

---

