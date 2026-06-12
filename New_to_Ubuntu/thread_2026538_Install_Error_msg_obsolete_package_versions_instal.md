---
title: "Install Error msg: obsolete package versions installed"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by AubreyT on 2012-07-15
Hello
I am trying to install Ubuntu 12.4. on a Dell Optiplex 740 (uses a AMD64)
I have recieved an error message "obsolete package versions installed. Please ugrade following packages and check if problem still occurs..." and there is a list of files such as unity, bamfdeamon,.... - see attached JPEG
Could anyone advise as to how I could finish the installation?
Thank you
AubreyT

---

### Post by z3nhakr on 2012-07-15
are you using wubi or a live cd? try redownloading ubuntu...also i remember a way to update the installer but i cant seem to find it anymore. :(

---

### Post by AubreyT on 2012-07-15
Thank you for trying to help! 
I used a cd which I downloaded from the Ubuntu site. 
I first installed the 32 version then realised there was a 64 version which I then try to install and this lead to current impasse! 
Any suggestions?
Thanks again!
A

---

### Post by jmfal on 2012-07-15
Welcome to Ubuntu

Open a terminal and run

```
 sudo apt-get update    
```

Then 
```
 sudo apt-get upgrade
```

If there are errors post between {CODE][CODE] using **#** in reply screen.

---

### Post by AubreyT on 2012-07-16
Thank you for helping out!
Sorry to be a novice but how do I "open a terminal and run". 
Be much obliged.
Thanks again
AubreyT

---

### Post by Shadius on 2012-07-16
> **AubreyT said:**
> Thank you for helping out!
Sorry to be a novice but how do I "open a terminal and run". 
Be much obliged.
Thanks again
AubreyT

The keyboard shortcut for opening the Terminal is **Ctrl Alt T**, press those keys together. This will open up the Terminal. Type the codes suggested to you in the Terminal and press **Enter**. Type in each code one at a time and press **Enter**, you'll be prompted to enter your password.

---

### Post by AubreyT on 2012-07-16
Thanks a mill! You're very kind - I'll try that...
AubreyT

---

### Post by Shadius on 2012-07-16
> **AubreyT said:**
> Thanks a mill! You're very kind - I'll try that...
AubreyT

Thank you, you're very welcome. Post back and let me know the results. :)

---

### Post by AubreyT on 2012-07-16
Hi
I booted up and saw a software update menu which I confirmed - it started download but finishing saying it coulod not complete. I then tried the Alt Ctrl T but the keyboard seemed to have been lost since the update (I can confirm password when I first boot up - so it works up until then!!)
I will come back with more later this afternoon once I have re-booted and see what files it indicates if any there is a problem with.
Thank you all again for your patience with this complete biginner!
AubreyT

---

### Post by AubreyT on 2012-07-16
Dear All
SUCCESS!!!
I am posting this from our NEW LINUX PC!!!!!
It worked and thank you all for the time and patience! Truly!!!!
I didn't get there exactly as you planned. I noticed a link on the password page which I clinked on and it offered Ubuntu or Ubuntu 2D. I clicked on the latter and that open a working system:D - I don't know why but it did.
I then did as you suggested and Alt Ctr l T later I had all the updates and then the upgrades.
It works a treat and my 7 yr and 11 yr old are going to be at last delighted as I have been months promising LINUX as best!!! It's fast and a new PC!
I also notice that there are still some software updates its asking for but afraid now to clink on the update button for fear of going backwards. Any advice?
Believe you me I have been trying to promote LINUX as an alternative to Windows and get my kids to understand PC through this way and it has been a long journey. 
Thank you again
From a proud Dad:P
AubreyT
PS From a new user there has to be a better way of doing this....that was painful!

---

### Post by NikTh on 2012-07-16
Hi , 
glad you corrected your problem and installed Ubuntu successfully.
I think its time for a little bit specifications . 
Please open a terminal (Ctrl+Alt+t) and copy-paste these commands from here to your terminal , one at time 
```
cat /etc/lsb-release && uname -r 
env | grep DESK 
lspci -nnk | grep -iA2 vga
```
Post the results back here . 
**Put the results inside [CODE] tags , by highlighting the text and click at # symbol on top of message pane. **
Thanks

---

### Post by Shadius on 2012-07-17
> **AubreyT said:**
> Dear All
SUCCESS!!!
I am posting this from our NEW LINUX PC!!!!!
It worked and thank you all for the time and patience! Truly!!!!
I didn't get there exactly as you planned. I noticed a link on the password page which I clinked on and it offered Ubuntu or Ubuntu 2D. I clicked on the latter and that open a working system:D - I don't know why but it did.
I then did as you suggested and Alt Ctr l T later I had all the updates and then the upgrades.
It works a treat and my 7 yr and 11 yr old are going to be at last delighted as I have been months promising LINUX as best!!! It's fast and a new PC!
I also notice that there are still some software updates its asking for but afraid now to clink on the update button for fear of going backwards. Any advice?
Believe you me I have been trying to promote LINUX as an alternative to Windows and get my kids to understand PC through this way and it has been a long journey. 
Thank you again
From a proud Dad:P
AubreyT
PS From a new user there has to be a better way of doing this....that was painful!

You should be fine with applying the software updates.

---

### Post by AubreyT on 2012-07-17
Hi
Thanks for helping out!
Here are the replies..
First response

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
3.2.0-27-generic
```

Second response

```
DESKTOP_SESSION=ubuntu-2d
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity
```

Third response

```
00:05.0 VGA compatible controller [0300]: NVIDIA Corporation C51 [GeForce 6150 LE] [10de:0241] (rev a2)
    Subsystem: Dell Device [1028:01ec]
    Kernel driver in use: nvidia
```

Hope this is what you wanted!
Look forward to hearing from you
Cheers
AubreyT

---

### Post by Shadius on 2012-07-17
> **AubreyT said:**
> Hi
Thanks for helping out!
Here are the replies..
First response

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
3.2.0-27-generic
```

Second response

```
DESKTOP_SESSION=ubuntu-2d
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity
```

Third response

```
00:05.0 VGA compatible controller [0300]: NVIDIA Corporation C51 [GeForce 6150 LE] [10de:0241] (rev a2)
    Subsystem: Dell Device [1028:01ec]
    Kernel driver in use: nvidia
```

Hope this is what you wanted!
Look forward to hearing from you
Cheers
AubreyT

It might have to do with your graphics card. Did you try to log in under the "Ubuntu" choice instead of the "Ubuntu 2D" choice? Also, check if you have installed the propietary drivers for your graphics card by going to ***System Settings***, and look for ***Additional Drivers***. It should give you the proprietary drivers to use. 

Also, please run this code in Terminal:
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by AubreyT on 2012-07-17
Thanks again! You're very kind!

I ran the code and answer was

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6150 LE/integrated/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.49

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```I have also access driver updates and installed other NVIDIA driver which was presented as updated but not yet recommended version

Will now try to see if Ubuntu boots - up until now I have got a blank screen.

Thanks again
A

---

### Post by Shadius on 2012-07-17
> **AubreyT said:**
> Thanks again! You're very kind!

I ran the code and answer was

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6150 LE/integrated/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.49

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```I have also access driver updates and installed other NVIDIA driver which was presented as updated but not yet recommended version

Will now try to see if Ubuntu boots - up until now I have got a blank screen.

Thanks again
A

You've gotten a blank screen upon booting?

---

### Post by AubreyT on 2012-07-17
Hi
Not any longer!!!
After the update on the NVIDIA, Ubuntu now boots and the screen is sharper and am I correct in saying the whole system is faster?!
You are a clever person!
Thank you... : - )

Other issues remain though and while I don't wish to intrude on your time...
Printers...is there a website or something...I have a Lexmark X1250 connected to the PC - The proposed driver doesn't work - is this a case of abandon as no Linux drivers exist and if so is there a list of Linux/Ubuntu compatible printers somewhere? Obviously need a printer for their school work : - ) 
Any advice - oh while I am at it - webcam? Tried the help line and they talk about a thing called cheese? But cannnot seem to find cheese whatever that is... 

Thank you again for all the help - hugely appreciated!!!
AubreyT

---

### Post by Shadius on 2012-07-17
> **AubreyT said:**
> Hi
Not any longer!!!
After the update on the NVIDIA, Ubuntu now boots and the screen is sharper and am I correct in saying the whole system is faster?!
You are a clever person!
Thank you... : - )

Other issues remain though and while I don't wish to intrude on your time...
Printers...is there a website or something...I have a Lexmark X1250 connected to the PC - The proposed driver doesn't work - is this a case of abandon as no Linux drivers exist and if so is there a list of Linux/Ubuntu compatible printers somewhere? Obviously need a printer for their school work : - ) 
Any advice - oh while I am at it - webcam? Tried the help line and they talk about a thing called cheese? But cannnot seem to find cheese whatever that is... 

Thank you again for all the help - hugely appreciated!!!
AubreyT

Not a problem. I can help as much as I can. :) Cheese, I believe, is an application for your webcam. You can find it in the Ubuntu Software Center, just do a search for "cheese." As for the printer, give me a second.

---

### Post by NikTh on 2012-07-17
Hi , 
you can try to install newer version of Nvidia driver by run these commands in terminal (one at time, and one line = one command)
```
sudo add-apt-repository *ppa*:ubuntu-*x*-*swat*/x-updates
sudo apt-get update ; sudo apt-get upgrade
``` 
These commands will add an exernal ppa to your sources.list and upgrade your nvidia driver to 302 . 
You can see the nvidia-current driver version from terminal by
```
apt-cache policy nvidia-current
```
Thanks

---

### Post by Shadius on 2012-07-17
I don't think the Lexmark X1250 is compatible with Ubuntu, according to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Printers_probably_working").

---

### Post by AubreyT on 2012-07-17
> **NikTh said:**
> Hi , 
you can try to install newer version of Nvidia driver by run these commands in terminal (one at time, and one line = one command)
```
sudo add-apt-repository *ppa*:ubuntu-*x*-*swat*/x-updates
sudo apt-get update ; sudo apt-get upgrade
```These commands will add an exernal ppa to your sources.list and upgrade your nvidia driver to 302 . 
You can see the nvidia-current driver version from terminal by
```
apt-cache policy nvidia-current
```Thanks


First line had follow response
You are about to add the following PPA to your system:
 ```
Updated versions of X.org drivers, libraries, etc. for Ubuntu.

This PPA is for stable upstream releases of X.org components.  If you're looking for something even more bleeding-edge, please see the xorg-edgers PPA.  Or, if you're actually wanting backports of the current stable X stack to an older Ubuntu release, see the x-backports PPA.

While Ubuntu-X does not officially support these packages, if you discover problems when installing these debs please feel free to report bugs to launchpad.  However, please make sure to clearly state that you are running packages from this PPA so we know the fixes need to come here.

If you are uprading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.
 More info: https://launchpad.net/~ubuntu-x-swat/+archive/x-updates
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.bEiQyWEaAT --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
oscar@oscar-OptiPlex-740:~$ sudo apt-get update ; sudo apt-get upgrade
Ign http://extras.ubuntu.com precise InRelease
Ign http://ppa.launchpad.net precise InRelease                      
Ign http://security.ubuntu.com precise-security InRelease            
Ign http://gb.archive.ubuntu.com precise InRelease                   
Ign http://gb.archive.ubuntu.com precise-updates InRelease           
Ign http://gb.archive.ubuntu.com precise-backports InRelease         
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]            
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                                          
Ign http://gb.archive.ubuntu.com precise-proposed InRelease                                           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]                      
Get:4 http://gb.archive.ubuntu.com precise Release.gpg [198 B]                             
Hit http://extras.ubuntu.com precise Release                                                          
Get:5 http://ppa.launchpad.net precise Release [11.9 kB]                                   
Get:6 http://security.ubuntu.com precise-security Release [49.6 kB]                                  
Get:7 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]                                        
Get:8 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]                                                  
Hit http://extras.ubuntu.com precise/main Sources                                                                         
Get:9 http://gb.archive.ubuntu.com precise-proposed Release.gpg [198 B]                                                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                        
Hit http://extras.ubuntu.com precise/main i386 Packages                                              
Get:10 http://ppa.launchpad.net precise/main Sources [2,228 B]                                       
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                 
Get:11 http://gb.archive.ubuntu.com precise Release [49.6 kB]                                        
Get:12 http://security.ubuntu.com precise-security/main Sources [26.1 kB]         
Get:13 http://ppa.launchpad.net precise/main amd64 Packages [3,671 B]                                           
Get:14 http://ppa.launchpad.net precise/main i386 Packages [3,675 B]                                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                 
Get:15 http://security.ubuntu.com precise-security/restricted Sources [14 B]                                               
Get:16 http://security.ubuntu.com precise-security/universe Sources [7,849 B]
Get:17 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]                                     
Get:18 http://security.ubuntu.com precise-security/multiverse Sources [713 B]                             
Get:19 http://security.ubuntu.com precise-security/main amd64 Packages [75.9 kB]                                           
Get:20 http://gb.archive.ubuntu.com precise-backports Release [49.6 kB]                                           
Get:21 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]                                        
Get:22 http://security.ubuntu.com precise-security/universe amd64 Packages [20.5 kB]                  
Get:23 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]                                     
Get:24 http://security.ubuntu.com precise-security/main i386 Packages [78.5 kB]                                            
Get:25 http://gb.archive.ubuntu.com precise-proposed Release [49.6 kB]                                                     
Get:26 http://gb.archive.ubuntu.com precise/main Sources [934 kB]                                                          
Get:27 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]                                         
Get:28 http://security.ubuntu.com precise-security/universe i386 Packages [20.7 kB]
Get:29 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]                                      
Get:30 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]                                            
Get:31 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]                                      
Get:32 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]                                      
Get:33 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]                                        
Hit http://security.ubuntu.com precise-security/main Translation-en                                                        
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                  
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                  
Ign http://extras.ubuntu.com precise/main Translation-en_GB                                                                
Get:34 http://security.ubuntu.com precise-security/universe Translation-en [14.1 kB]                                       
Ign http://extras.ubuntu.com precise/main Translation-en                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en_GB                                                                
Ign http://ppa.launchpad.net precise/main Translation-en                                                                   
Get:35 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]                                                   
Get:36 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]                                                    
Get:37 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]                                                    
Get:38 http://gb.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]                                                 
Get:39 http://gb.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]                                            
Get:40 http://gb.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]                                             
Get:41 http://gb.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]                                             
Get:42 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                  
Get:43 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                             
Get:44 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                              
Get:45 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                              
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                                                             
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex                                                       
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex                                                       
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex                                                         
Get:46 http://gb.archive.ubuntu.com precise-updates/main Sources [131 kB]                                                  
Get:47 http://gb.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]                                           
Get:48 http://gb.archive.ubuntu.com precise-updates/universe Sources [36.1 kB]                                             
Get:49 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]                                           
Get:50 http://gb.archive.ubuntu.com precise-updates/main amd64 Packages [323 kB]                                           
Get:51 http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]                                    
Get:52 http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages [93.5 kB]                                      
Get:53 http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,829 B]                                    
Get:54 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [325 kB]                                            
Get:55 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]                                     
Get:56 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [94.0 kB]                                       
Get:57 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]                                     
Get:58 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                        
Get:59 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                  
Get:60 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                  
Get:61 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                    
Get:62 http://gb.archive.ubuntu.com precise-backports/main Sources [1,845 B]                                               
Get:63 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                            
Get:64 http://gb.archive.ubuntu.com precise-backports/universe Sources [12.4 kB]                                           
Get:65 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]                                         
Get:66 http://gb.archive.ubuntu.com precise-backports/main amd64 Packages [1,271 B]                                        
Get:67 http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                     
Get:68 http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages [11.1 kB]                                    
Get:69 http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]                                    
Get:70 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]                                         
Get:71 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                      
Get:72 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [11.2 kB]                                     
Get:73 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]                                     
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex                                                   
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                             
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex                                             
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex                                               
Get:74 http://gb.archive.ubuntu.com precise-proposed/restricted amd64 Packages [14 B]                                      
Get:75 http://gb.archive.ubuntu.com precise-proposed/main amd64 Packages [168 kB]                                          
Get:76 http://gb.archive.ubuntu.com precise-proposed/multiverse amd64 Packages [14 B]                                      
Get:77 http://gb.archive.ubuntu.com precise-proposed/universe amd64 Packages [31.5 kB]                                     
Get:78 http://gb.archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]                                       
Get:79 http://gb.archive.ubuntu.com precise-proposed/main i386 Packages [169 kB]                                           
Get:80 http://gb.archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]                                       
Get:81 http://gb.archive.ubuntu.com precise-proposed/universe i386 Packages [31.5 kB]                                      
Hit http://gb.archive.ubuntu.com precise-proposed/main TranslationIndex                                                    
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse TranslationIndex                                              
Hit http://gb.archive.ubuntu.com precise-proposed/restricted TranslationIndex                                              
Hit http://gb.archive.ubuntu.com precise-proposed/universe TranslationIndex                                                
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                                                            
Hit http://gb.archive.ubuntu.com precise/main Translation-en                                                               
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB                                                      
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en                                                         
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB                                                      
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en                                                         
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB                                                        
Hit http://gb.archive.ubuntu.com precise/universe Translation-en                                                           
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB                                                    
Get:82 http://gb.archive.ubuntu.com precise-updates/main Translation-en [152 kB]                                           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en                                                 
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB                                              
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en                                                 
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB                                                
Get:83 http://gb.archive.ubuntu.com precise-updates/universe Translation-en [56.1 kB]                                      
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en                                                     
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en                                               
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en                                               
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en                                                 
Hit http://gb.archive.ubuntu.com precise-proposed/main Translation-en_GB                                                   
Hit http://gb.archive.ubuntu.com precise-proposed/main Translation-en                                                      
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse Translation-en_GB                                             
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse Translation-en                                                
Hit http://gb.archive.ubuntu.com precise-proposed/restricted Translation-en_GB                                             
Hit http://gb.archive.ubuntu.com precise-proposed/restricted Translation-en                                                
Hit http://gb.archive.ubuntu.com precise-proposed/universe Translation-en_GB                                               
Hit http://gb.archive.ubuntu.com precise-proposed/universe Translation-en                                                  
Get:84 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [94.2 kB]                                 
Fetched 20.7 MB in 2min 23s (144 kB/s)                                                                                     
W: Failed to fetch gzip:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en%5fGB  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en nvidia-current nvidia-settings xdiagnose
  xserver-xorg-video-intel
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 80.0 MB of archives.
After this operation, 454 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main firefox-globalmenu amd64 14.0.1+build1-0ubuntu0.12.04.1 [48.3 kB]
Get:2 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main nvidia-current amd64 302.17-0ubuntu1~precise~xup1 [58.8 MB]
Get:3 http://security.ubuntu.com/ubuntu/ precise-security/main firefox amd64 14.0.1+build1-0ubuntu0.12.04.1 [19.1 MB]
Get:4 http://security.ubuntu.com/ubuntu/ precise-security/main firefox-gnome-support amd64 14.0.1+build1-0ubuntu0.12.04.1 [9,258 B]
Get:5 http://security.ubuntu.com/ubuntu/ precise-security/main firefox-locale-en amd64 14.0.1+build1-0ubuntu0.12.04.1 [445 kB]
Get:6 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main nvidia-settings amd64 302.17-0ubuntu1~precise~xup3 [1,330 kB]
Get:7 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main xserver-xorg-video-intel amd64 2:2.19.0-0ubuntu1~xup1 [266 kB]
Get:8 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main xdiagnose all 2.6 [63.6 kB]                    
Fetched 80.0 MB in 9min 38s (138 kB/s)                                                                                     
(Reading database ... 168881 files and directories currently installed.)
Preparing to replace firefox-globalmenu 13.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_14.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 13.0.1+build1-0ubuntu0.12.04.1 (using .../firefox_14.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 13.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-gnome-support_14.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 13.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_14.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace nvidia-current 295.40-0ubuntu1 (using .../nvidia-current_302.17-0ubuntu1~precise~xup1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Preparing to replace nvidia-settings 295.33-0ubuntu1 (using .../nvidia-settings_302.17-0ubuntu1~precise~xup3_amd64.deb) ...
Unpacking replacement nvidia-settings ...
Preparing to replace xserver-xorg-video-intel 2:2.17.0-1ubuntu4 (using .../xserver-xorg-video-intel_2%3a2.19.0-0ubuntu1~xup1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Preparing to replace xdiagnose 2.5.2 (using .../archives/xdiagnose_2.6_all.deb) ...
Unpacking replacement xdiagnose ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up firefox (14.0.1+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (14.0.1+build1-0ubuntu0.12.04.1) ...
Setting up firefox-gnome-support (14.0.1+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (14.0.1+build1-0ubuntu0.12.04.1) ...
Setting up nvidia-current (302.17-0ubuntu1~precise~xup1) ...
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Dell Inc with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-302.17 DKMS files...
Building only for 3.2.0-27-generic
Building for architecture x86_64
Building initial module for 3.2.0-27-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-27-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-settings (302.17-0ubuntu1~precise~xup3) ...
Setting up xserver-xorg-video-intel (2:2.19.0-0ubuntu1~xup1) ...
Setting up xdiagnose (2.6) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```Second one produced following
```
Ign http://extras.ubuntu.com precise InRelease
Ign http://ppa.launchpad.net precise InRelease
Ign http://gb.archive.ubuntu.com precise InRelease                           
Ign http://gb.archive.ubuntu.com precise-updates InRelease                   
Ign http://gb.archive.ubuntu.com precise-backports InRelease                 
Ign http://gb.archive.ubuntu.com precise-proposed InRelease                  
Ign http://security.ubuntu.com precise-security InRelease            
Hit http://extras.ubuntu.com precise Release.gpg                     
Hit http://ppa.launchpad.net precise Release.gpg                     
Hit http://gb.archive.ubuntu.com precise Release.gpg
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg
Hit http://ppa.launchpad.net precise Release                         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg       
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://extras.ubuntu.com precise Release                         
Hit http://gb.archive.ubuntu.com precise-proposed Release.gpg                               
Hit http://security.ubuntu.com precise-security Release              
Hit http://extras.ubuntu.com precise/main Sources                    
Hit http://gb.archive.ubuntu.com precise Release                     
Hit http://ppa.launchpad.net precise/main Sources
Hit http://gb.archive.ubuntu.com precise-updates Release                                                          
Hit http://extras.ubuntu.com precise/main amd64 Packages                                   
Hit http://extras.ubuntu.com precise/main i386 Packages              
Hit http://ppa.launchpad.net precise/main amd64 Packages             
Hit http://ppa.launchpad.net precise/main i386 Packages              
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Hit http://security.ubuntu.com precise-security/main Sources         
Hit http://gb.archive.ubuntu.com precise-backports Release                                 
Ign http://extras.ubuntu.com precise/main TranslationIndex                                 
Hit http://gb.archive.ubuntu.com precise-proposed Release                                  
Hit http://gb.archive.ubuntu.com precise/main Sources
Hit http://gb.archive.ubuntu.com precise/restricted Sources
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise/restricted amd64 Packages                                                
Hit http://gb.archive.ubuntu.com precise/universe amd64 Packages                           
Hit http://gb.archive.ubuntu.com precise/multiverse amd64 Packages                         
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                    
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                  
Hit http://security.ubuntu.com precise-security/main i386 Packages                         
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                   
Hit http://security.ubuntu.com precise-security/universe i386 Packages                     
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                                
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                   
Hit http://security.ubuntu.com precise-security/main TranslationIndex                      
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/main Sources
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/main Sources      
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-proposed/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise-proposed/main amd64 Packages
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com precise-proposed/universe amd64 Packages
Hit http://gb.archive.ubuntu.com precise-proposed/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-proposed/main i386 Packages 
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-proposed/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-proposed/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise-proposed/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-proposed/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-proposed/main Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-proposed/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-proposed/universe Translation-en
Get:1 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [94.2 kB]
Fetched 1 B in 2s (0 B/s)                      
W: Failed to fetch gzip:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en%5fGB  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
oscar@oscar-OptiPlex-740:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Third one
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
oscar@oscar-OptiPlex-740:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


and Fourth

```
nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup1
  Candidate: 302.17-0ubuntu1~precise~xup1
  Version table:
 *** 302.17-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```


So seemed to have worked?
What do you think?
AubreyT

---

### Post by NikTh on 2012-07-17
Hi ,
> **AubreyT said:**
>      ```
nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup1
  Candidate: 302.17-0ubuntu1~precise~xup1
  Version table:
 *** 302.17-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```So seemed to have worked?
What do you think?
AubreyT
As you can see , yes , now you have the latest stable version of Nvidia Driver. 
but
i see an error here..
> **AubreyT said:**
> ```

W: Failed to fetch gzip:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en%5fGB  Encountered a section with no Package: header
```

Copy-paste this command from here to your terminal (for more accuracy) 
```
sudo rm -rf /var/lib/apt/lists/*
```Then run ```
sudo apt-get update
``` and give the results here.
Thanks

---

### Post by AubreyT on 2012-07-19
Dear All
Sorry for the lack of progress but have been away. Should be back tomorrow and will execute the advice :-) 
Thanks for your patience.
Huigely appreciated!
AubreyT

---

### Post by AubreyT on 2012-07-23
Dear All

Sorry for the delay in getting back to you all. I was away traveling and unable to get to the PC concerned but I am now posting all of the code as a result of your collective input which I hugely appreciate. I know you all have other things to do than sort us lot out. :-) So bear with us please!!!

```
Get:14 http://security.ubuntu.com precise-security/universe Sources [7,849 B]  
Get:15 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:16 http://security.ubuntu.com precise-security/main amd64 Packages [96.7 kB]
Get:17 http://gb.archive.ubuntu.com precise/main Sources [934 kB]              
Get:18 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:19 http://security.ubuntu.com precise-security/universe amd64 Packages [24.2 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [99.6 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [24.4 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:25 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:26 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:27 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:28 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:29 http://security.ubuntu.com precise-security/main Translation-en [51.3 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:30 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:31 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:32 http://security.ubuntu.com precise-security/universe Translation-en [15.6 kB]
Get:33 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:34 http://gb.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Get:35 http://gb.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:36 http://gb.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Get:37 http://gb.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:38 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:39 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:40 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:41 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:42 http://gb.archive.ubuntu.com precise-updates/main Sources [134 kB]      
Get:43 http://gb.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:44 http://gb.archive.ubuntu.com precise-updates/universe Sources [38.2 kB] 
Get:45 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:46 http://gb.archive.ubuntu.com precise-updates/main amd64 Packages [331 kB]
Get:47 http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:48 http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages [97.2 kB]
Get:49 http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,829 B]
Get:50 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [333 kB]
Get:51 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:52 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [97.7 kB]
Get:53 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Get:54 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:55 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:56 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:57 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:58 http://gb.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:59 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:60 http://gb.archive.ubuntu.com precise-backports/universe Sources [12.4 kB]
Get:61 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:62 http://gb.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:63 http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:64 http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages [11.1 kB]
Get:65 http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]
Get:66 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:67 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:68 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [11.2 kB]
Get:69 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Get:70 http://gb.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:71 http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex [71 B]
Get:72 http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:73 http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]
Get:74 http://gb.archive.ubuntu.com precise-proposed/restricted amd64 Packages [2,539 B]
Get:75 http://gb.archive.ubuntu.com precise-proposed/main amd64 Packages [160 kB]
Get:76 http://gb.archive.ubuntu.com precise-proposed/multiverse amd64 Packages [890 B]
Get:77 http://gb.archive.ubuntu.com precise-proposed/universe amd64 Packages [32.2 kB]
Get:78 http://gb.archive.ubuntu.com precise-proposed/restricted i386 Packages [2,531 B]
Get:79 http://gb.archive.ubuntu.com precise-proposed/main i386 Packages [160 kB]
Get:80 http://gb.archive.ubuntu.com precise-proposed/multiverse i386 Packages [886 B]
Get:81 http://gb.archive.ubuntu.com precise-proposed/universe i386 Packages [32.3 kB]
Get:82 http://gb.archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]
Get:83 http://gb.archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]
Get:84 http://gb.archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]
Get:85 http://gb.archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Get:86 http://gb.archive.ubuntu.com precise-updates/main Translation-en [157 kB]
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Get:87 http://gb.archive.ubuntu.com precise-updates/universe Translation-en [58.6 kB]
Get:88 http://gb.archive.ubuntu.com precise-backports/main Translation-en [1,244 B]
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://gb.archive.ubuntu.com precise-proposed/main Translation-en_GB       
Get:89 http://gb.archive.ubuntu.com precise-proposed/main Translation-en [48.2 kB]
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse Translation-en_GB 
Get:90 http://gb.archive.ubuntu.com precise-proposed/multiverse Translation-en [871 B]
Hit http://gb.archive.ubuntu.com precise-proposed/restricted Translation-en_GB 
Get:91 http://gb.archive.ubuntu.com precise-proposed/restricted Translation-en [719 B]
Hit http://gb.archive.ubuntu.com precise-proposed/universe Translation-en_GB   
Get:92 http://gb.archive.ubuntu.com precise-proposed/universe Translation-en [19.8 kB]
Get:93 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [94.2 kB]
Fetched 20.9 MB in 2min 23s (146 kB/s)                                         
W: Failed to fetch gzip:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en%5fGB  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc evince evince-common
  ghostscript ghostscript-cups ghostscript-x gir1.2-gudev-1.0
  gnome-control-center gnome-control-center-data gnome-desktop3-data
  gnome-games-data gnome-sudoku gnomine krb5-locales libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libevince3-3
  libexif12 libgnome-control-center1 libgnome-desktop-3-2 libgphoto2-2
  libgphoto2-l10n libgphoto2-port0 libgs9 libgs9-common libgssapi-krb5-2
  libgudev-1.0-0 libk5crypto3 libkrb5-3 libkrb5support0 liblightdm-gobject-1-0
  libtiff4 libudev0 lightdm mahjongg python-software-properties resolvconf
  software-properties-common software-properties-gtk udev
48 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.1 MB of archives.
After this operation, 54.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main libexif12 amd64 0.6.20-2ubuntu0.1 [94.0 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main resolvconf all 1.63ubuntu15 [53.7 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libudev0 amd64 175-0ubuntu9.1 [30.0 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libk5crypto3 amd64 1.10+dfsg~beta1-2ubuntu0.2 [79.9 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgssapi-krb5-2 amd64 1.10+dfsg~beta1-2ubuntu0.2 [118 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libkrb5-3 amd64 1.10+dfsg~beta1-2ubuntu0.2 [354 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libkrb5support0 amd64 1.10+dfsg~beta1-2ubuntu0.2 [23.5 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libcups2 amd64 1.5.3-0ubuntu2 [172 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libcupsmime1 amd64 1.5.3-0ubuntu2 [13.5 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libcupscgi1 amd64 1.5.3-0ubuntu2 [29.8 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main libtiff4 amd64 3.9.5-2ubuntu1.2 [144 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libcupsimage2 amd64 1.5.3-0ubuntu2 [51.8 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libcupsppdc1 amd64 1.5.3-0ubuntu2 [52.4 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgs9-common all 9.05~dfsg-0ubuntu4.1 [3,944 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main ghostscript-x amd64 9.05~dfsg-0ubuntu4.1 [38.3 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main ghostscript amd64 9.05~dfsg-0ubuntu4.1 [44.0 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgs9 amd64 9.05~dfsg-0ubuntu4.1 [2,255 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main cups-common all 1.5.3-0ubuntu2 [824 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main cups-bsd amd64 1.5.3-0ubuntu2 [44.8 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main cups-client amd64 1.5.3-0ubuntu2 [174 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main cups-ppdc amd64 1.5.3-0ubuntu2 [30.5 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main cups amd64 1.5.3-0ubuntu2 [1,292 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libcupsdriver1 amd64 1.5.3-0ubuntu2 [19.6 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgphoto2-l10n all 2.4.13-1ubuntu1.2 [7,654 B]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgphoto2-port0 amd64 2.4.13-1ubuntu1.2 [44.7 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgphoto2-2 amd64 2.4.13-1ubuntu1.2 [998 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgudev-1.0-0 amd64 1:175-0ubuntu9.1 [14.5 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main lightdm amd64 1.2.1-0ubuntu1.1 [98.4 kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main udev amd64 175-0ubuntu9.1 [323 kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main krb5-locales all 1.10+dfsg~beta1-2ubuntu0.2 [8,944 B]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main evince amd64 3.4.0-0ubuntu1.3 [204 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libevince3-3 amd64 3.4.0-0ubuntu1.3 [357 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main evince-common all 3.4.0-0ubuntu1.3 [476 kB]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main ghostscript-cups amd64 9.05~dfsg-0ubuntu4.1 [24.4 kB]
Get:35 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main gir1.2-gudev-1.0 amd64 175-0ubuntu9.1 [3,980 B]
Get:36 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgnome-control-center1 amd64 1:3.4.2-0ubuntu0.4 [79.2 kB]
Get:37 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main libgnome-desktop-3-2 amd64 3.4.2-0ubuntu0.1 [102 kB]
Get:38 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main gnome-desktop3-data all 3.4.2-0ubuntu0.1 [28.4 kB]
Get:39 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main gnome-control-center-data all 1:3.4.2-0ubuntu0.4 [1,121 kB]
Get:40 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main gnome-control-center amd64 1:3.4.2-0ubuntu0.4 [658 kB]
Get:41 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main mahjongg amd64 1:3.4.1-0ubuntu2.1 [2,330 kB]
Get:42 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main gnomine amd64 1:3.4.1-0ubuntu2.1 [412 kB]
Get:43 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main gnome-sudoku all 1:3.4.1-0ubuntu2.1 [765 kB]
Get:44 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main gnome-games-data all 1:3.4.1-0ubuntu2.1 [106 kB]
Get:45 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main liblightdm-gobject-1-0 amd64 1.2.1-0ubuntu1.1 [30.5 kB]
Get:46 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main python-software-properties all 0.82.7.2 [22.2 kB]
Get:47 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main software-properties-common all 0.82.7.2 [9,636 B]
Get:48 http://gb.archive.ubuntu.com/ubuntu/ precise-proposed/main software-properties-gtk all 0.82.7.2 [34.1 kB]
Fetched 18.1 MB in 1min 50s (165 kB/s)                                         
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 169954 files and directories currently installed.)
Preparing to replace resolvconf 1.63ubuntu14 (using .../resolvconf_1.63ubuntu15_all.deb) ...
Unpacking replacement resolvconf ...
Preparing to replace libudev0 175-0ubuntu9 (using .../libudev0_175-0ubuntu9.1_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace libk5crypto3 1.10+dfsg~beta1-2ubuntu0.1 (using .../libk5crypto3_1.10+dfsg~beta1-2ubuntu0.2_amd64.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace libgssapi-krb5-2 1.10+dfsg~beta1-2ubuntu0.1 (using .../libgssapi-krb5-2_1.10+dfsg~beta1-2ubuntu0.2_amd64.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.10+dfsg~beta1-2ubuntu0.1 (using .../libkrb5-3_1.10+dfsg~beta1-2ubuntu0.2_amd64.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.10+dfsg~beta1-2ubuntu0.1 (using .../libkrb5support0_1.10+dfsg~beta1-2ubuntu0.2_amd64.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libcups2 1.5.3-0ubuntu1 (using .../libcups2_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement libcups2 ...
Preparing to replace libcupsmime1 1.5.3-0ubuntu1 (using .../libcupsmime1_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement libcupsmime1 ...
Preparing to replace libcupscgi1 1.5.3-0ubuntu1 (using .../libcupscgi1_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement libcupscgi1 ...
Preparing to replace libtiff4 3.9.5-2ubuntu1.1 (using .../libtiff4_3.9.5-2ubuntu1.2_amd64.deb) ...
Unpacking replacement libtiff4 ...
Preparing to replace libcupsimage2 1.5.3-0ubuntu1 (using .../libcupsimage2_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace libcupsppdc1 1.5.3-0ubuntu1 (using .../libcupsppdc1_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement libcupsppdc1 ...
Preparing to replace libgs9-common 9.05~dfsg-0ubuntu4 (using .../libgs9-common_9.05~dfsg-0ubuntu4.1_all.deb) ...
Unpacking replacement libgs9-common ...
Preparing to replace ghostscript-x 9.05~dfsg-0ubuntu4 (using .../ghostscript-x_9.05~dfsg-0ubuntu4.1_amd64.deb) ...
Unpacking replacement ghostscript-x ...
Preparing to replace ghostscript 9.05~dfsg-0ubuntu4 (using .../ghostscript_9.05~dfsg-0ubuntu4.1_amd64.deb) ...
Unpacking replacement ghostscript ...
Preparing to replace libgs9 9.05~dfsg-0ubuntu4 (using .../libgs9_9.05~dfsg-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libgs9 ...
Preparing to replace cups-common 1.5.3-0ubuntu1 (using .../cups-common_1.5.3-0ubuntu2_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.5.3-0ubuntu1 (using .../cups-bsd_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace cups-client 1.5.3-0ubuntu1 (using .../cups-client_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement cups-client ...
Preparing to replace cups-ppdc 1.5.3-0ubuntu1 (using .../cups-ppdc_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement cups-ppdc ...
Preparing to replace cups 1.5.3-0ubuntu1 (using .../cups_1.5.3-0ubuntu2_amd64.deb) ...
cups stop/waiting
Moving obsolete conffile /etc/modprobe.d/blacklist-cups-usblp.conf out of the way...
Unpacking replacement cups ...
Preparing to replace libcupsdriver1 1.5.3-0ubuntu1 (using .../libcupsdriver1_1.5.3-0ubuntu2_amd64.deb) ...
Unpacking replacement libcupsdriver1 ...
Preparing to replace libexif12 0.6.20-2 (using .../libexif12_0.6.20-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libexif12 ...
Preparing to replace libgphoto2-l10n 2.4.13-1ubuntu1.1 (using .../libgphoto2-l10n_2.4.13-1ubuntu1.2_all.deb) ...
Unpacking replacement libgphoto2-l10n ...
Preparing to replace libgphoto2-port0 2.4.13-1ubuntu1.1 (using .../libgphoto2-port0_2.4.13-1ubuntu1.2_amd64.deb) ...
Unpacking replacement libgphoto2-port0 ...
Preparing to replace libgphoto2-2 2.4.13-1ubuntu1.1 (using .../libgphoto2-2_2.4.13-1ubuntu1.2_amd64.deb) ...
Unpacking replacement libgphoto2-2 ...
Preparing to replace libgudev-1.0-0 1:175-0ubuntu9 (using .../libgudev-1.0-0_1%3a175-0ubuntu9.1_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace lightdm 1.2.1-0ubuntu1 (using .../lightdm_1.2.1-0ubuntu1.1_amd64.deb) ...
Unpacking replacement lightdm ...
Preparing to replace udev 175-0ubuntu9 (using .../udev_175-0ubuntu9.1_amd64.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Preparing to replace krb5-locales 1.10+dfsg~beta1-2ubuntu0.1 (using .../krb5-locales_1.10+dfsg~beta1-2ubuntu0.2_all.deb) ...
Unpacking replacement krb5-locales ...
Preparing to replace evince 3.4.0-0ubuntu1.2 (using .../evince_3.4.0-0ubuntu1.3_amd64.deb) ...
Unpacking replacement evince ...
Preparing to replace libevince3-3 3.4.0-0ubuntu1.2 (using .../libevince3-3_3.4.0-0ubuntu1.3_amd64.deb) ...
Unpacking replacement libevince3-3 ...
Preparing to replace evince-common 3.4.0-0ubuntu1.2 (using .../evince-common_3.4.0-0ubuntu1.3_all.deb) ...
Unpacking replacement evince-common ...
Preparing to replace ghostscript-cups 9.05~dfsg-0ubuntu4 (using .../ghostscript-cups_9.05~dfsg-0ubuntu4.1_amd64.deb) ...
Unpacking replacement ghostscript-cups ...
Preparing to replace gir1.2-gudev-1.0 175-0ubuntu9 (using .../gir1.2-gudev-1.0_175-0ubuntu9.1_amd64.deb) ...
Unpacking replacement gir1.2-gudev-1.0 ...
Preparing to replace libgnome-control-center1 1:3.4.2-0ubuntu0.3 (using .../libgnome-control-center1_1%3a3.4.2-0ubuntu0.4_amd64.deb) ...
Unpacking replacement libgnome-control-center1 ...
Preparing to replace libgnome-desktop-3-2 3.4.1-0ubuntu1 (using .../libgnome-desktop-3-2_3.4.2-0ubuntu0.1_amd64.deb) ...
Unpacking replacement libgnome-desktop-3-2 ...
Preparing to replace gnome-desktop3-data 3.4.1-0ubuntu1 (using .../gnome-desktop3-data_3.4.2-0ubuntu0.1_all.deb) ...
Unpacking replacement gnome-desktop3-data ...
Preparing to replace gnome-control-center-data 1:3.4.2-0ubuntu0.3 (using .../gnome-control-center-data_1%3a3.4.2-0ubuntu0.4_all.deb) ...
Unpacking replacement gnome-control-center-data ...
Preparing to replace gnome-control-center 1:3.4.2-0ubuntu0.3 (using .../gnome-control-center_1%3a3.4.2-0ubuntu0.4_amd64.deb) ...
Unpacking replacement gnome-control-center ...
Preparing to replace mahjongg 1:3.4.1-0ubuntu2 (using .../mahjongg_1%3a3.4.1-0ubuntu2.1_amd64.deb) ...
Unpacking replacement mahjongg ...
Preparing to replace gnomine 1:3.4.1-0ubuntu2 (using .../gnomine_1%3a3.4.1-0ubuntu2.1_amd64.deb) ...
Unpacking replacement gnomine ...
Preparing to replace gnome-sudoku 1:3.4.1-0ubuntu2 (using .../gnome-sudoku_1%3a3.4.1-0ubuntu2.1_all.deb) ...
Unpacking replacement gnome-sudoku ...
Preparing to replace gnome-games-data 1:3.4.1-0ubuntu2 (using .../gnome-games-data_1%3a3.4.1-0ubuntu2.1_all.deb) ...
Unpacking replacement gnome-games-data ...
Preparing to replace liblightdm-gobject-1-0 1.2.1-0ubuntu1 (using .../liblightdm-gobject-1-0_1.2.1-0ubuntu1.1_amd64.deb) ...is
Unpacking replacement liblightdm-gobject-1-0 ...
Preparing to replace python-software-properties 0.82.7.1 (using .../python-software-properties_0.82.7.2_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace software-properties-common 0.82.7.1 (using .../software-properties-common_0.82.7.2_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.1 (using .../software-properties-gtk_0.82.7.2_all.deb) ...
Unpacking replacement software-properties-gtk ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...is
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0 ...
Processing triggers for shared-mime-info ...
Setting up resolvconf (1.63ubuntu15) ...
Installing new version of config file /etc/ppp/ip-up.d/000resolvconf ...
Installing new version of config file /etc/ppp/ip-down.d/000resolvconf ...
Setting up libudev0 (175-0ubuntu9.1) ...
Setting up libkrb5support0 (1.10+dfsg~beta1-2ubuntu0.2) ...
Setting up libk5crypto3 (1.10+dfsg~beta1-2ubuntu0.2) ...
Setting up libkrb5-3 (1.10+dfsg~beta1-2ubuntu0.2) ...
Setting up libgssapi-krb5-2 (1.10+dfsg~beta1-2ubuntu0.2) ...
Setting up libcups2 (1.5.3-0ubuntu2) ...
Setting up libcupsmime1 (1.5.3-0ubuntu2) ...
Setting up libcupscgi1 (1.5.3-0ubuntu2) ...is
Setting up libtiff4 (3.9.5-2ubuntu1.2) ...
Setting up libcupsimage2 (1.5.3-0ubuntu2) ...
Setting up libcupsppdc1 (1.5.3-0ubuntu2) ...
Setting up libgs9-common (9.05~dfsg-0ubuntu4.1) ...
Setting up libgs9 (9.05~dfsg-0ubuntu4.1) ...
Setting up ghostscript (9.05~dfsg-0ubuntu4.1) ...
Setting up ghostscript-x (9.05~dfsg-0ubuntu4.1) ...
Setting up cups-common (1.5.3-0ubuntu2) ...
Setting up cups-client (1.5.3-0ubuntu2) ...
Setting up cups-bsd (1.5.3-0ubuntu2) ...
Setting up cups-ppdc (1.5.3-0ubuntu2) ...
Setting up cups (1.5.3-0ubuntu2) ...
Removing obsolete conffile /etc/modprobe.d/blacklist-cups-usblp.conf ...
cups start/running, process 5552
Updating PPD files for cups ...
Updating PPD files for ghostscript-cups ...
Setting up libcupsdriver1 (1.5.3-0ubuntu2) ...
Setting up libexif12 (0.6.20-2ubuntu0.1) ...
Setting up libgphoto2-l10n (2.4.13-1ubuntu1.2) ...
Setting up libgphoto2-port0 (2.4.13-1ubuntu1.2) ...
Setting up libgphoto2-2 (2.4.13-1ubuntu1.2) ...
Setting up libgudev-1.0-0 (1:175-0ubuntu9.1) ...
Setting up lightdm (1.2.1-0ubuntu1.1) ...
Setting up udev (175-0ubuntu9.1) ...
udev stop/waiting
udev start/running, process 5956
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up krb5-locales (1.10+dfsg~beta1-2ubuntu0.2) ...
Setting up libevince3-3 (3.4.0-0ubuntu1.3) ...
Setting up evince-common (3.4.0-0ubuntu1.3) ...
Setting up evince (3.4.0-0ubuntu1.3) ...
Setting up ghostscript-cups (9.05~dfsg-0ubuntu4.1) ...
Setting up gir1.2-gudev-1.0 (175-0ubuntu9.1) ...
Setting up libgnome-control-center1 (1:3.4.2-0ubuntu0.4) ...
Setting up gnome-desktop3-data (3.4.2-0ubuntu0.1) ...
Setting up libgnome-desktop-3-2 (3.4.2-0ubuntu0.1) ...
Setting up gnome-control-center-data (1:3.4.2-0ubuntu0.4) ...
Setting up gnome-control-center (1:3.4.2-0ubuntu0.4) ...
Setting up gnome-games-data (1:3.4.1-0ubuntu2.1) ...
Setting up mahjongg (1:3.4.1-0ubuntu2.1) ...
Setting up gnomine (1:3.4.1-0ubuntu2.1) ...
Setting up gnome-sudoku (1:3.4.1-0ubuntu2.1) ...
Setting up liblightdm-gobject-1-0 (1.2.1-0ubuntu1.1) ...
Setting up python-software-properties (0.82.7.2) ...
Setting up software-properties-common (0.82.7.2) ...
Setting up software-properties-gtk (0.82.7.2) ...
Processing triggers for resolvconf ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
```The above is the return and as far as I can read they all seemed to work. Yes/ No?

Certainly this PC is booting much faster - thanks !!! - I will reboot and see what's next.

Given what we are trying to achieve here - any advice on a list of printers that are Unbuntu compatible or have drivers to download? Is there a site or app that gives this sort of thing. Be much obliged as after all this, a PC without a printer can be a limited thing :-( 

Again to you all - a huge thank you for all your patience and great inputs!

Sincerely

AubreyT

---

### Post by AubreyT on 2012-07-23
Hello

Sorry to intrude - any advice on tying to install the game Minecraft?
Much obliged!
AubreyT
PS I downloaded the jar file from the web site but am at a loss as to how it installs!!!:D

---

