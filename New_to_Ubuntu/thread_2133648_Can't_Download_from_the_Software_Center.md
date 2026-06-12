---
title: "Can't Download from the Software Center"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by mlv213 on 2013-04-08
I'm a complete beginner, so I've posted the step by step process of my problem. Please help :D.

Upon opening the software center I get a message that says "Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?"

I click *Repair* and the operation fails with the details:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 197101 files and directories currently installed.)
Unpacking firefox (from .../firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 12.04ubuntu1
No apport report written because MaxReports is reached already
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 20.0+build1-0ubuntu0.12.10.3); however:
  Package firefox is not installed.


dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured


If I ignore all of this stuff I can still maneuver through the software center, but when I try to download a program I get a popup that tells me that to install I need to remove "Safe and easy web browser from mozilla - unity menubar integration" with the subtitle(?) "firefox-globalmenu"

I hit *Install Anyway* and get the popup: 

The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The details section:

The following packages have unmet dependencies:


firefox-globalmenu: Depends: firefox (= 20.0+build1-0ubuntu0.12.10.3) but it is not installed

I go into the terminal and type in apt-get install -f  

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  language-pack-gnome-en language-pack-gnome-en-base libasprintf0c2:i386
  libcroco3:i386 libgomp1:i386 linux-headers-3.5.0-17
  linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts firefox-gnome-support
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
1 not fully installed or removed.
Need to get 0 B/24.8 MB of archives.
After this operation, 55.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 197101 files and directories currently installed.)
Unpacking firefox (from .../firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 12.04ubuntu1
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)






Any suggestions?

---

### Post by deadflowr on 2013-04-08
Have you tried to run the kubuntu-firefox-installer?

---

### Post by mlv213 on 2013-04-08
Yes and I receive this error: 

Package: /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.debError: trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 12.04ubuntu1

---

### Post by Habanero101 on 2013-04-08
Have you tried uninstalling firefox and then reinstalling it?

---

### Post by ibjsb4 on 2013-04-08
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo apt-get clean

sudo apt-get autoremove

sudo apt-get update
```

---

### Post by mlv213 on 2013-04-08
sudo apt-get autoremove



Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 20.0+build1-0ubuntu0.12.10.3) but it is not installed
E: Unmet dependencies. Try using -f.


Then I entered apt-get update and it seemed to go through:




sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg [933 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages                   
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages              
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources [86.8 kB]      
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources [1,302 B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources [81.5 kB]  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release.gpg                      
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources [2,933 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [38.2 kB]      
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages [226 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages                
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main amd64 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main i386 Packages               
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [3,048 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages [177 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [16.1 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [692 B]  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,946 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages [224 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [105 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages [3,067 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages [178 kB]
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,097 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en [108 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en [93.9 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [45.1 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1,150 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [104 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [45.8 kB]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en_US
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,396 B]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en [55.5 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en [28.1 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Fetched 1,744 kB in 8s (195 kB/s)                                              
Reading package lists... Done

---

### Post by mlv213 on 2013-04-08
Yes, it won't uninstall from the software center. I get the exact same error as when I try to download a program. [seen in first post]

---

### Post by ibjsb4 on 2013-04-08
Ok, do what it suggested

```
sudo apt-get -f install
```

Edit:  Just notice you have done that.  BB after dinner :)

---

### Post by mlv213 on 2013-04-08
Thanks :D. This problem's  really annoying :*(

---

### Post by ppjdee on 2013-04-09
Maybe uninstalling/purging and re installing Software Center will help?

---

### Post by mlv213 on 2013-04-09
How would I go about doing that? Through a terminal command?

---

### Post by mlv213 on 2013-04-09
I tried to uninstall the software center, but the same error popped up as when I try and uninstall/install any program. How can firefox screw up so much? :(

---

### Post by ppjdee on 2013-04-09
[http://askubuntu.com/questions/133456/can-i-uninstall-and-reinstall-ubuntu-software-center](http://askubuntu.com/questions/133456/can-i-uninstall-and-reinstall-ubuntu-software-center)

I "googled" and found this for removing/purging SC

---

### Post by mlv213 on 2013-04-09
I attempted this, but the same firefox error came up. I ran the apt-get -f install or whatever it really is and I think this is the crux of the error message? 

Errors were encountered while processing: /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is what I'm getting on all fronts. Is there a way to uninstall and reinstall it? Idk I'm really new to linux in general haha.

---

### Post by ppjdee on 2013-04-09
I'm clueless as to whats happening. Maybe someone more knowledgeable will see this thread shortly.

The only ideas I had in mind would be;

1: remove/re install FF
```
sudo apt-get purge firefox
sudo apt-get remove firefox
sudo apt-get update
sudo apt-get install firefox
```

2: re install OS :D

3: wait for someone more knowledgeable to answer.

But I'm sure you have tried the first. And I doubt you really want to do a fresh install of you'r OS. 
So, hang tight and wait for someone else to post an answer. Cheers and good luck!

---

### Post by mlv213 on 2013-04-09
Thanks for putting in the time to try, man. I appreciate that. I think there's a weird part of firefox that is tied to the software center (maybe how it reaches packages and other downloads) and I've fundamentally screwed that stuff up. Oh, well. I shall play the waiting game :D. Thanks again.

---

### Post by ibjsb4 on 2013-04-09
Good morning  :)

This package kubuntu-firefox-installer.  I suggest removing it.

```
sudo apt-get remove kubuntu-firefox-installer

sudo apt-get update
```

---

### Post by mlv213 on 2013-04-09
Good afternoon to you sir! No luck removing the installer. I'm getting the same error from before:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 20.0+build1-0ubuntu0.12.10.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

what's firefox-globalmenu and why is it completely evil? :(

---

### Post by tartalo on 2013-04-09
> **mlv213 said:**
> what's firefox-globalmenu and why is it completely evil? :(

firefox-globalmenu detatches the firefox menu to put it in Unity's top bar (And in KDE there is also a plasma widget called globalmenu, I think, that shows menus detatched from their aplications). 

If you use KDE and prefer your Firefox menu to be in Firefox, you don't need firefox-globalmenu at all and you can purge it safely.

---

### Post by mlv213 on 2013-04-09
> **tartalo said:**
> firefox-globalmenu detatches the firefox menu to put it in Unity's top bar (And in KDE there is also a plasma widget called globalmenu, I think, that shows menus detatched from their aplications). 

If you use KDE and prefer your Firefox menu to be in Firefox, you don't need firefox-globalmenu at all and you can purge it safely.

I purged the program and now the Software Center is running again. Any idea why this program caused such a block on the Software Center? I'm not sure if I screwed something up and caused the problem, or if it's something I can avoid in the future.

Thanks for the knowledge and help!

---

### Post by tartalo on 2013-04-09
> **mlv213 said:**
> I purged the program and now the Software Center is running again. Any idea why this program caused such a block on the Software Center? I'm not sure if I screwed something up and caused the problem, or if it's something I can avoid in the future.

> firefox-globalmenu : Depends: firefox (= 20.0+build1-0ubuntu0.12.10.3) but it is not going to be installed
It looks like a dependency conflict to me. It seems that firefox-globalmenu depends on an exact version of firefox but you have a different one available.

To see what version of firefox you have:
```
apt-cache show firefox
```

Are you using any ppa? That could explain the conflict.

---

### Post by mlv213 on 2013-04-09
I'm not entirely sure what a ppa is, but I don't think I'm using any :P. I checked what version I have in terminal and this came up:

Package: firefox
Priority: optional
Section: web
Installed-Size: 53913
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Version: 20.0+build1-0ubuntu0.12.10.3
Provides: gnome-www-browser, iceweasel, www-browser
Depends: lsb-release, libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.15), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.3.9), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.31.8), libgtk2.0-0 (>= 2.24.0), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.8), libstdc++6 (>= 4.6), libx11-6, libxext6, libxrender1, libxt6
Recommends: xul-ext-ubufox, firefox-globalmenu, libcanberra0
Suggests: latex-xft-fonts, libthai0, firefox-gnome-support
Filename: pool/main/f/firefox/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb
Size: 24766028
MD5sum: 43b48c952ea15bea62d53a1d57031216
SHA1: 22ea7f59cad505484178616a0e66ab39f7da3e93
SHA256: 4d6797243b5bf4fb6c3bc83c994b0ff4b289f45634964357900afba130e7063f
Description-en: Safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
Description-md5: 46b619f510631c4693dc09c1a3778a55
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-desktop-kde, edubuntu-usb, xubuntu-desktop, ubuntustudio-desktop


Package: firefox
Priority: optional
Section: web
Installed-Size: 44469
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Version: 16.0.1+build1-0ubuntu1
Replaces: kubuntu-firefox-installer
Provides: gnome-www-browser, iceweasel, www-browser
Depends: lsb-release, libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.15), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.3.9), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.31.8), libgtk2.0-0 (>= 2.24.0), libnotify4 (>= 0.7.0), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.8), libstdc++6 (>= 4.6), libx11-6, libxext6, libxrender1, libxt6
Recommends: xul-ext-ubufox, firefox-globalmenu, libcanberra0
Suggests: latex-xft-fonts, libthai0, firefox-gnome-support
Filename: pool/main/f/firefox/firefox_16.0.1+build1-0ubuntu1_amd64.deb
Size: 20538886
MD5sum: ea276b7bba8bae7a376d3bff1039bcba
SHA1: 9df0cffa7e3d24c856743f536ca408ed17cb5bce
SHA256: 7430a1f8d5735838a2a6bd4890d063a653bb88409a42655d01b8f6d7d855cf4f
Description-en: Safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
Description-md5: 46b619f510631c4693dc09c1a3778a55
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-desktop-kde, edubuntu-usb, xubuntu-desktop, ubuntustudio-desktop


firefox-globalmenu is recommended?

---

### Post by tartalo on 2013-04-09
My guess was wrong, you do have the exact version of firefox required by firefox-globalmenu, and that error was probably a side effect of the mess, not the cause. In fact, if I had read your first post carefully I could have avoided making a fool of myself, because it was mentioned there. 

I better admit that I don't know what caused your problem.

>  firefox-globalmenu is recommended?

firefox-global menu is recommended by firefox in Ubuntu because it "allows Firefox to take advantage of the Unity menubar". But you are not using Unity, so you don't need it anyway.

---

### Post by mlv213 on 2013-04-09
could you define 'the mess'? :P Was firefox in general not downloaded correctly?

---

### Post by carolinason on 2013-04-10
i had the same problem with a fresh install of Kubuntu 12.10 that was fully updated. the issue starts by using the kubuntu-firefox-installer in the K menu under the Internet section. i experienced the same error messages as in this thread.
I fixed the issue by reading some of this thread, but i couldn't install firefox with the globalmenu package and it install successfully. so i used the following
```
apt-get remove firefox-globalmenu
apt-get remove kubuntu-firefox-installer
apt-get remove firefox 
```
i didn't need the last command, but i just wanted to make sure the firefox package was not installed (partially or otherwise). i could have searched for it i suppose.
then i used aptitude with the --without-recommends option to not install the globalmenu package.
```
aptitude install --without-recommends firefox
```
firefox then installed correctly. i am not totally convinced this is a globalmenu issue. i was distro hoping and saw something similar with the kubuntu-firefox installer having a dependancy conflict. but i might be getting off subject.

---

