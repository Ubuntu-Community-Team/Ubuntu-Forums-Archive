---
title: "adobe flash install problems"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by stum22 on 2012-07-23
I have tried to update via terminal and via Flash Aid with no luck. No luck with things posted on the forum either.

Here is the output from Flash Aid
```
--2012-07-23 13:59:27--  http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.236/install_flash_player_11_linux.x86_64.tar.gz
Resolving fpdownload.macromedia.com (fpdownload.macromedia.com)... 125.252.194.70
Connecting to fpdownload.macromedia.com (fpdownload.macromedia.com)|125.252.194.70|:80... failed: Connection timed out.
Retrying.

```etc

```
--2012-07-23 14:21:51--  (try:20)  http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.236/install_flash_player_11_linux.x86_64.tar.gz
Connecting to fpdownload.macromedia.com (fpdownload.macromedia.com)|125.252.194.70|:80... failed: Connection timed out.
Giving up.

md5sum: *flash*: No such file or directory
Flash 64bit installation aborted, due to md5 checksum mismatch!
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
[sudo] password for stum: 

```

---

### Post by upsla on 2012-07-23
Why don't you update your Flash through "Software Center"  or "PPA's".

---

### Post by stum22 on 2012-07-23
That didnt seem to work either.

---

### Post by NikTh on 2012-07-23
Hi , 
please open a terminal and give the output of this command 

```
apt-cache policy adobe-flashplugin flashplugin-installer
``` 

Thanks.

---

### Post by stum22 on 2012-07-23
```
stum@stum:~$ apt-cache policy adobe-flashplugin flashplugin-installer
adobe-flashplugin:
  Installed: (none)
  Candidate: (none)
  Version table:
flashplugin-installer:
  Installed: 11.2.202.236ubuntu0.12.04.1
  Candidate: 11.2.202.236ubuntu0.12.04.1
  Version table:
 *** 11.2.202.236ubuntu0.12.04.1 0
        500 http://au.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     11.2.202.233ubuntu2 0
        500 http://au.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages
stum@stum:~$ 

```

Thanks!

---

### Post by NikTh on 2012-07-23
Hi , 
try something .. i am not sure if work . 

Open Update manager and go to "Settings" > "Other Software" and enable "Canonical Partners" repository. ( i assume you have it disabled) 

Then close update manager and open a terminal... 
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` 

Thanks

---

### Post by lakona on 2012-07-23
I have always had the best success with installing flash from the adobe Web site: [http://get.adobe.com/flashplayer/otherversions/. ]("http://get.adobe.com/flashplayer/otherversions/")

This link should take you to the adobe site where you can select your operating system (linux 32 or 64 bit), and which type of installer (select Ubuntu (apt))

There will be a pop-up asking what to use to open the link, just use the default **apturl.**
[]("http://get.adobe.com/flashplayer/otherversions/")

---

### Post by stum22 on 2012-07-23
> **NikTh said:**
> Hi , 
try something .. i am not sure if work . 

Open Update manager and go to "Settings" > "Other Software" and enable "Canonical Partners" repository. ( i assume you have it disabled) 

Then close update manager and open a terminal... 
```
sudo apt-get update 
sudo apt-get dist-upgrade
```Thanks

I had it disabled and then did both but still says I need flash...

```

stum@stum:~$ sudo apt-get update
[sudo] password for stum: 
Ign http://au.archive.ubuntu.com precise InRelease
Ign http://au.archive.ubuntu.com precise-updates InRelease          
Ign http://au.archive.ubuntu.com precise-backports InRelease         
Hit http://au.archive.ubuntu.com precise Release.gpg                 
Hit http://au.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://au.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://au.archive.ubuntu.com precise Release                               
Hit http://au.archive.ubuntu.com precise-updates Release                       
Hit http://au.archive.ubuntu.com precise-backports Release                     
Hit http://au.archive.ubuntu.com precise/main Sources                          
Hit http://au.archive.ubuntu.com precise/restricted Sources                    
Ign http://archive.canonical.com precise InRelease                             
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://au.archive.ubuntu.com precise/universe Sources                      
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://au.archive.ubuntu.com precise/multiverse Sources                    
Hit http://au.archive.ubuntu.com precise/main amd64 Packages                   
Get:1 http://archive.canonical.com precise Release.gpg [198 B]                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://au.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://au.archive.ubuntu.com precise/universe amd64 Packages               
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://au.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://au.archive.ubuntu.com precise/main i386 Packages                    
Get:4 http://archive.canonical.com precise Release [7,078 B]         
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://au.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://au.archive.ubuntu.com precise/universe i386 Packages                
Get:6 http://extras.ubuntu.com precise Release [11.9 kB]                       
Hit http://au.archive.ubuntu.com precise/multiverse i386 Packages              
Get:7 http://archive.canonical.com precise/partner Sources [3,430 B]           
Hit http://au.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://au.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://au.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://au.archive.ubuntu.com precise/universe TranslationIndex             
Get:8 http://archive.canonical.com precise/partner amd64 Packages [4,314 B]    
Hit http://au.archive.ubuntu.com precise-updates/main Sources                  
Hit http://au.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://au.archive.ubuntu.com precise-updates/universe Sources              
Hit http://au.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://au.archive.ubuntu.com precise-updates/main amd64 Packages           
Get:9 http://archive.canonical.com precise/partner i386 Packages [4,982 B]     
Hit http://au.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Get:10 http://extras.ubuntu.com precise/main Sources [1,489 B]                 
Hit http://au.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://au.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Get:11 http://security.ubuntu.com precise-security/main Sources [30.0 kB]
Hit http://au.archive.ubuntu.com precise-updates/main i386 Packages            
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://au.archive.ubuntu.com precise-updates/restricted i386 Packages      
Get:12 http://extras.ubuntu.com precise/main amd64 Packages [1,709 B]          
Hit http://au.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://au.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://au.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://au.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Get:13 http://extras.ubuntu.com precise/main i386 Packages [1,726 B]           
Get:14 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Hit http://au.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://au.archive.ubuntu.com precise-backports/main Sources                
Hit http://au.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://au.archive.ubuntu.com precise-backports/universe Sources   
Hit http://au.archive.ubuntu.com precise-backports/multiverse Sources 
Hit http://au.archive.ubuntu.com precise-backports/main amd64 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://au.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://au.archive.ubuntu.com precise-backports/universe amd64 Packages
Get:15 http://security.ubuntu.com precise-security/universe Sources [7,849 B]  
Hit http://au.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://au.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://au.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://au.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://au.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://au.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://au.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://au.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Hit http://au.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://au.archive.ubuntu.com precise/main Translation-en_AU                
Hit http://au.archive.ubuntu.com precise/main Translation-en                   
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en_AU          
Get:17 http://security.ubuntu.com precise-security/main amd64 Packages [95.0 kB]
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://au.archive.ubuntu.com precise/restricted Translation-en_AU          
Hit http://au.archive.ubuntu.com precise/restricted Translation-en             
Hit http://au.archive.ubuntu.com precise/universe Translation-en               
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en_AU        
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://au.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://au.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/universe Translation-en     
Get:18 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Ign http://archive.canonical.com precise/partner Translation-en_AU             
Get:19 http://security.ubuntu.com precise-security/universe amd64 Packages [24.2 kB]
Ign http://archive.canonical.com precise/partner Translation-en                
Get:20 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Ign http://extras.ubuntu.com precise/main Translation-en_AU                    
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [97.6 kB]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [24.4 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 369 kB in 12s (28.9 kB/s)                                              
Reading package lists... Done
stum@stum:~$ sudo apt-get dist-update
E: Invalid operation dist-update
stum@stum:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stum@stum:~$ 
```

I tried: sudo apt-get update; sudo apt-get install flashplugin-installer

Then get 

```
Ign http://au.archive.ubuntu.com precise InRelease
Ign http://extras.ubuntu.com precise InRelease
Ign http://au.archive.ubuntu.com precise-updates InRelease
Ign http://au.archive.ubuntu.com precise-backports InRelease         
Hit http://au.archive.ubuntu.com precise Release.gpg                 
Hit http://au.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://au.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://au.archive.ubuntu.com precise Release                     
Hit http://au.archive.ubuntu.com precise-updates Release                       
Hit http://au.archive.ubuntu.com precise-backports Release                     
Hit http://au.archive.ubuntu.com precise/main Sources                          
Hit http://au.archive.ubuntu.com precise/restricted Sources                    
Hit http://au.archive.ubuntu.com precise/universe Sources            
Hit http://au.archive.ubuntu.com precise/multiverse Sources          
Hit http://au.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://extras.ubuntu.com precise Release.gpg                               
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                   
Hit http://au.archive.ubuntu.com precise/restricted amd64 Packages   
Hit http://au.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://au.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://au.archive.ubuntu.com precise/main i386 Packages          
Hit http://extras.ubuntu.com precise Release                                   
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:2 http://archive.canonical.com precise Release.gpg [198 B]       
Hit http://au.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://au.archive.ubuntu.com precise/universe i386 Packages                
Hit http://au.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://au.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://au.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://au.archive.ubuntu.com precise/restricted TranslationIndex           
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]  
Get:4 http://archive.canonical.com precise Release [7,078 B]         
Hit http://au.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/main Sources                  
Hit http://au.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://au.archive.ubuntu.com precise-updates/universe Sources              
Hit http://au.archive.ubuntu.com precise-updates/multiverse Sources            
Get:5 http://archive.canonical.com precise/partner Sources [3,430 B]           
Hit http://au.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://au.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://au.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://au.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Get:6 http://archive.canonical.com precise/partner amd64 Packages [4,314 B]    
Hit http://au.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://au.archive.ubuntu.com precise-updates/restricted i386 Packages
Ign http://extras.ubuntu.com precise/main Translation-en_AU           
Ign http://extras.ubuntu.com precise/main Translation-en              
Get:7 http://archive.canonical.com precise/partner i386 Packages [4,982 B]
Get:8 http://security.ubuntu.com precise-security/main Sources [30.0 kB]       
Hit http://au.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://au.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://au.archive.ubuntu.com precise-updates/main TranslationIndex         
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://au.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Get:9 http://security.ubuntu.com precise-security/restricted Sources [14 B]
Hit http://au.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://au.archive.ubuntu.com precise-backports/main Sources       
Hit http://au.archive.ubuntu.com precise-backports/restricted Sources          
Get:10 http://security.ubuntu.com precise-security/universe Sources [7,849 B]  
Hit http://au.archive.ubuntu.com precise-backports/universe Sources            
Hit http://au.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://au.archive.ubuntu.com precise-backports/main amd64 Packages         
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Hit http://au.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://au.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://au.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://au.archive.ubuntu.com precise-backports/main i386 Packages
Get:12 http://security.ubuntu.com precise-security/main amd64 Packages [95.0 kB]
Hit http://au.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://au.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://au.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://au.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://au.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://au.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://au.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://au.archive.ubuntu.com precise/main Translation-en_AU                
Hit http://au.archive.ubuntu.com precise/main Translation-en                   
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en_AU          
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en             
Get:13 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Hit http://au.archive.ubuntu.com precise/restricted Translation-en_AU          
Hit http://au.archive.ubuntu.com precise/restricted Translation-en             
Hit http://au.archive.ubuntu.com precise/universe Translation-en               
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en_AU        
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en           
Get:14 http://security.ubuntu.com precise-security/universe amd64 Packages [24.2 kB]
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://au.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://au.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/universe Translation-en     
Ign http://archive.canonical.com precise/partner Translation-en_AU             
Get:15 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Ign http://archive.canonical.com precise/partner Translation-en                
Get:16 http://security.ubuntu.com precise-security/main i386 Packages [97.6 kB]
Get:17 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:18 http://security.ubuntu.com precise-security/universe i386 Packages [24.4 kB]
Get:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 352 kB in 14s (24.6 kB/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Websites still ask for flash after closing modzilla.

Thanks!

---

### Post by NikTh on 2012-07-23
Hi , 
ok lets try to install the other package.. 

```
sudo apt-get install adobe-flashplugin
``` 
give here the results . 

Thanks

---

### Post by stum22 on 2012-07-23
I keep getting:

```

Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

```

This pops up after you press 'run this action' then it loops.

---

### Post by NikTh on 2012-07-23
Hi , 
remove packages so we can start over again.. 
```
sudo apt-get purge adobe-flashplugin flashplugin-installer 
```i assume that now you have "Canonical Partners" Enabled. 

Remove Flash - Aid from Firefox. 

Then open a terminal and..
```
sudo apt-get update 
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
sudo apt-get install -f 
sudo apt-get clean && sudo apt-get autoclean
sudo dpkg --configure -a 
apt-cache policy adobe-flashplugin flashplugin-installer 
uname -r
```Give the results of 2 last commands here.. 

Copy-Paste commands from here to your terminal (for more accuracy) 
Thanks.

---

### Post by stum22 on 2012-07-23
Thanks Nik!

```
stum@stum:~$ apt-cache policy adobe-flashplugin flashplugin-installer 
adobe-flashplugin:
  Installed: (none)
  Candidate: 11.2.202.236-0precise1
  Version table:
     11.2.202.236-0precise1 0
        500 http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages
flashplugin-installer:
  Installed: (none)
  Candidate: 11.2.202.236ubuntu0.12.04.1
  Version table:
     11.2.202.236ubuntu0.12.04.1 0
        500 http://au.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/multiverse amd64 Packages
     11.2.202.233ubuntu2 0
        500 http://au.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages
stum@stum:~$ uname -r
3.2.0-26-generic
stum@stum:~$ 

```

---

### Post by NikTh on 2012-07-23
Hi , 
try to install again now 

```
sudo apt-get install flashplugin-installer
``` 

give the full results here

Thanks.

---

### Post by Stanwilliamsmusic on 2012-07-23
The flash plugin update (last one Adobe made available for Linux) was broken or has been for me on all my Linux  computers.
and they are not going to make any more.
oh well
I am using old version of flash player even if it has security issues I use it some times to listen to my music or something(I am a composer), I reckon it is still more secure than using windows;)
I saw this on the forums a minute ago (changing the subjec ) but it will Not let me post foe some reason or change anything about my profile or CP
anyway :
I didn't know and had the forum linked from Several of my websites I will remove them promptly.. I only had the links in place to help people find this forum,  I have been here since  6.06  but only joined a few years ago.
Oh well,   I will leave that up to the forum admins.
So,
later...

[http://ubuntuforums.org/showthread.php?t=1949027](http://ubuntuforums.org/showthread.php?t=1949027)

                                  **Continuing changes to Tutorials and Tips - please read**             
                                                                [COLOR=Red]Update 7/3/2012: 

1. As we are progressing in the transition some people choose to move  their tutorials out of ubuntu space, to various third party web sites  (blogs, web pages, etc). We have no problem with this decision, however,  posting a link back to the fourms, without permission from staff, is  considered spam.[/COLOR]

---

### Post by stum22 on 2012-07-24
```
stum@stum:~/Desktop/xtallog/mosflm708$ sudo apt-get install package-manager
[sudo] password for stum: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package package-manager
stum@stum:~/Desktop/xtallog/mosflm708$ sudo -s
[sudo] password for stum: 
root@stum:~/Desktop/xtallog/mosflm708# cd
root@stum:~# sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,316 B of archives.
After this operation, 139 kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com/ubuntu/ precise-updates/multiverse flashplugin-installer amd64 11.2.202.236ubuntu0.12.04.1 [8,316 B]
Fetched 8,316 B in 0s (228 kB/s)                   
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 196081 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.236ubuntu0.12.04.1_amd64.deb) ...
Processing triggers for update-notifier-common ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
Setting up flashplugin-installer (11.2.202.236ubuntu0.12.04.1) ...
root@stum:~# 

```

then

```
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz

```

---

### Post by lakona on 2012-07-24
> **lakona said:**
> I have always had the best success with installing flash from the adobe Web site: [http://get.adobe.com/flashplayer/otherversions/. ]("http://get.adobe.com/flashplayer/otherversions/")

This link should take you to the adobe site where you can select your operating system (linux 32 or 64 bit), and which type of installer (select Ubuntu (apt))

There will be a pop-up asking what to use to open the link, just use the default **apturl.**


Did you try to install the latest version from the adobe site?

It only takes a minute and it works for me every time. Why don't you give it a try?

---

### Post by NikTh on 2012-07-24
Hi , 
is this a specific problem with flash ? can you try to install another package ? 

**Are you behind of a proxy server **? 

Here you are.. i think --> [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/983559](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/983559)

so try what @lakona suggest , go to adobe's site and try to install flash..from there.
If this not work .. i have one last suggestion that might work. But let us know if @lakona's suggestion worked . 

Thanks

---

### Post by stum22 on 2012-07-24
Just flash. MyUnity dl fast. I had tried the site and got the same problems:

```
root@stum:~# sudo apt-get install myunity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gambas2-gb-form gambas2-gb-gtk gambas2-gb-gtk-ext gambas2-gb-gui
  gambas2-gb-qt gambas2-gb-settings gambas2-runtime libqt3-mt
Suggested packages:
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc
The following NEW packages will be installed:
  gambas2-gb-form gambas2-gb-gtk gambas2-gb-gtk-ext gambas2-gb-gui
  gambas2-gb-qt gambas2-gb-settings gambas2-runtime libqt3-mt myunity
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,332 kB of archives.
After this operation, 13.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com/ubuntu/ precise/universe gambas2-runtime amd64 2.23.1-1ubuntu3 [192 kB]
Get:2 http://au.archive.ubuntu.com/ubuntu/ precise/main libqt3-mt amd64 3:3.3.8-b-8ubuntu3 [3,288 kB]
Get:3 http://au.archive.ubuntu.com/ubuntu/ precise/universe gambas2-gb-qt amd64 2.23.1-1ubuntu3 [243 kB]
Get:4 http://au.archive.ubuntu.com/ubuntu/ precise/universe gambas2-gb-gtk amd64 2.23.1-1ubuntu3 [223 kB]
Get:5 http://au.archive.ubuntu.com/ubuntu/ precise/universe gambas2-gb-gui amd64 2.23.1-1ubuntu3 [11.3 kB]
Get:6 http://au.archive.ubuntu.com/ubuntu/ precise/universe gambas2-gb-settings all 2.23.1-1ubuntu3 [7,748 B]
Get:7 http://au.archive.ubuntu.com/ubuntu/ precise/universe gambas2-gb-form all 2.23.1-1ubuntu3 [815 kB]
Get:8 http://au.archive.ubuntu.com/ubuntu/ precise/universe gambas2-gb-gtk-ext amd64 2.23.1-1ubuntu3 [9,710 B]
Get:9 http://au.archive.ubuntu.com/ubuntu/ precise/universe myunity all 3.1.3-0ubuntu1 [542 kB]
Fetched 5,332 kB in 2s (2,127 kB/s)
Selecting previously unselected package gambas2-runtime.
(Reading database ... 196101 files and directories currently installed.)
Unpacking gambas2-runtime (from .../gambas2-runtime_2.23.1-1ubuntu3_amd64.deb) ...
Selecting previously unselected package libqt3-mt.
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8-b-8ubuntu3_amd64.deb) ...
Selecting previously unselected package gambas2-gb-qt.
Unpacking gambas2-gb-qt (from .../gambas2-gb-qt_2.23.1-1ubuntu3_amd64.deb) ...
Selecting previously unselected package gambas2-gb-gtk.
Unpacking gambas2-gb-gtk (from .../gambas2-gb-gtk_2.23.1-1ubuntu3_amd64.deb) ...
Selecting previously unselected package gambas2-gb-gui.
Unpacking gambas2-gb-gui (from .../gambas2-gb-gui_2.23.1-1ubuntu3_amd64.deb) ...
Selecting previously unselected package gambas2-gb-settings.
Unpacking gambas2-gb-settings (from .../gambas2-gb-settings_2.23.1-1ubuntu3_all.deb) ...
Selecting previously unselected package gambas2-gb-form.
Unpacking gambas2-gb-form (from .../gambas2-gb-form_2.23.1-1ubuntu3_all.deb) ...
Selecting previously unselected package gambas2-gb-gtk-ext.
Unpacking gambas2-gb-gtk-ext (from .../gambas2-gb-gtk-ext_2.23.1-1ubuntu3_amd64.deb) ...
Selecting previously unselected package myunity.
Unpacking myunity (from .../myunity_3.1.3-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up gambas2-runtime (2.23.1-1ubuntu3) ...
Setting up libqt3-mt (3:3.3.8-b-8ubuntu3) ...
Setting up gambas2-gb-qt (2.23.1-1ubuntu3) ...
Setting up gambas2-gb-gtk (2.23.1-1ubuntu3) ...
Setting up gambas2-gb-gui (2.23.1-1ubuntu3) ...
Setting up gambas2-gb-settings (2.23.1-1ubuntu3) ...
Setting up gambas2-gb-form (2.23.1-1ubuntu3) ...
Setting up gambas2-gb-gtk-ext (2.23.1-1ubuntu3) ...
Setting up myunity (3.1.3-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by NikTh on 2012-07-24
Hi , 
ok lets try one last thing.. i hope work.. 

Click here --> [http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.i386.tar.gz](http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.i386.tar.gz) to download the package.. "Save file" .. 

then open a terminal and..do 
```
 cd Downloads 
tar -xvzf flashplayer_11_plugin_debug.i386.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```Open Firefox and see if flash player work. 

If any of the commands returns error , DO NOT proceed , copy-paste the error here. 

THanks

---

### Post by stum22 on 2012-07-24
error on the second command

```
root@stum:~# cd Downloads
root@stum:~/Downloads# tar -xvzf flashplayer_11_plugin_debug.i386.tar.gz
libflashplayer.so
readme.txt
usr/
usr/bin/
usr/bin/flash-player-properties
usr/share/
usr/share/kde4/
usr/share/kde4/services/
usr/share/kde4/services/kcm_adobe_flash_player.desktop
usr/share/applications/
usr/share/applications/flash-player-properties.desktop
usr/share/icons/
usr/share/icons/hicolor/
usr/share/icons/hicolor/22x22/
usr/share/icons/hicolor/22x22/apps/
usr/share/icons/hicolor/22x22/apps/flash-player-properties.png
usr/share/icons/hicolor/48x48/
usr/share/icons/hicolor/48x48/apps/
usr/share/icons/hicolor/48x48/apps/flash-player-properties.png
usr/share/icons/hicolor/24x24/
usr/share/icons/hicolor/24x24/apps/
usr/share/icons/hicolor/24x24/apps/flash-player-properties.png
usr/share/icons/hicolor/32x32/
usr/share/icons/hicolor/32x32/apps/
usr/share/icons/hicolor/32x32/apps/flash-player-properties.png
usr/share/icons/hicolor/16x16/
usr/share/icons/hicolor/16x16/apps/
usr/share/icons/hicolor/16x16/apps/flash-player-properties.png
usr/share/pixmaps/
usr/share/pixmaps/flash-player-properties.png
usr/lib/
usr/lib/kde4/
usr/lib/kde4/kcm_adobe_flash_player.so
root@stum:~/Downloads# cd  flashplayer_11_plugin_debug.i386/
bash: cd: flashplayer_11_plugin_debug.i386/: No such file or directory

```

thanks

---

### Post by NikTh on 2012-07-24
Ok . 

give the result of 
```
ls Downloads
```**EDIT: **My mistake .. sorry.. 
give this command
```
sudo cp Downloads/libflashplayer.so /usr/lib/mozilla/plugins/ 
```

or this command (if you are connected to Downloads).. 
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

---

