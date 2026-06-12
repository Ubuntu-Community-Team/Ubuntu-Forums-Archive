---
title: "How to play DVD in Ubuntu 12.04"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by afz12 on 2012-05-12
I have Ubuntu 12.04 installed but can't play DVD's as yet. I have tried the following programs

Movie Player, Bino, Braesero Disc Burner, Dragon Player, Kaffeine, KPlayer, VLC media Player, xine.

These programs all claim to play DVD's (non encrypted) but none work - some play halting audio, none play video. I have all GStreamer's installed. I can convert to avi and mp4 formats using XP virtualized and these play OK in Ubuntu. What do I need to do in order to make videos play in Ubuntu 12.04 (please don't comment "it works fine on my computer!" as such comments offer no solution)

---

### Post by kc1di on 2012-05-12
Dvd's are encrypted with Css2 format and you have to install restricted codecs to play them here a page that will tell you how to do that. but understand it can be illegal is some countries.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
the format you looking for is this:
sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by afz12 on 2012-05-12
Hi kc1di

Thanks for the suggestion. I tried it - the codec was installed but the second terminal entry didn't connect as shown . So is there another way to get this DVD to play? In the meantime I'll try some others that worked on previous versions of Ubuntu.

---

### Post by kc1di on 2012-05-12
> **afz12 said:**
> Hi kc1di

Thanks for the suggestion. I tried it - the codec was installed but the second terminal entry didn't connect as shown . So is there another way to get this DVD to play? In the meantime I'll try some others that worked on previous versions of Ubuntu.

some possible reasons. 
1. you dont have internet connection
2. you do not have ubuntu-restricted-addons installed
3. you do not have ubuntu-restircted-extras installed.
Try that and run the command again.

---

### Post by Frogs Hair on 2012-05-12
If the restricted extras don't work install the repository at the link and then install the package shown. 

[http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/](http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/)

```
sudo apt-get install libdvdcss2
```

---

### Post by afz12 on 2012-05-12
Thanks for the replies. I've tried them all and nothing works still

"sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update"

The second last command didn't connect and I am obviously connected to the Internet as per this reply!

I tried other disks - still no play on 12.04 - this was a fresh install from a recent download. The notebook is an hp dv6 with 6 GB RAM / quad core i5. It should be able to play a DVD!

---

### Post by oldos2er on 2012-05-12
Can you copy and paste all the terminal output from ```
sudo apt-get update && sudo apt-get install libdvdcss2
``` ?

---

### Post by afz12 on 2012-05-12
Hi oldos2er

sudo apt-get update

downloaded 95% but the last entries had proxy errors - I'll try later from a different location



sudo apt-get install libdvdcss2 produced the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

sudo apt-get update && sudo apt-get install libdvdcss2 produced much the same. I think I'll try these on another notebook later - also running Ubuntu 12.04 in case this is notebook specific.

---

### Post by deadflowr on 2012-05-12
I think oldos2er means copy your output and paste it into one of these.

```
I'm the hashtag _#_ symbol above, paste your info inbetween code and /code
```

To copy all your terminal output open the menu option edit and select all then copy, then paste as above.
 The reason is so we can get a better sense of what's happening in terms of your connection to the repostitories. 
If you want to edit out any personal information like Dave@Mywackyubuntumachine: ~$ feel free as that isn't important for us.

---

### Post by Frogs Hair on 2012-05-12
The package libdvdcss2 is part of the medibuntu repository and won't be found until the repository is successfully added.

---

### Post by afz12 on 2012-05-13
I'm not sure if the following is what is asked for - "/ /" ? Anyway, I tried an older notebook running Ubuntu 12.04 and this DVD played OK on Movie Player. I checked the region setting for it and this notebook and both are correct. This notebook runs 12.04 but only plays halting audio but no video. I opened XP using Virtualbox and the DVD played with VLC media player. Therefore the DVD drive is OK, U12.04 can work on an older notebook, can work on this one but only using a VM / XP but never in 12.04!

Connecting to Medibuntu seems problematic. Also 
'Package 'libdvdcss2' has no installation candidate" doesn't seem helpful.


Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                       
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed InRelease             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release.gpg           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe TranslationIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_NZ             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_NZ                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_NZ           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe Translation-en
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en
Reading package lists... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate

---

### Post by Rodney9 on 2012-05-13
Follow this help  wiki - [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jtarin on 2012-05-13
From Medibuntu's Documentation
> You may also wish to add the following packages. The first will cause many apps from the Medibuntu repository to appear in Ubuntu Software Center. The second will allow users to generate crash reports against Medibuntu packages and submit them to the Medibuntu bugtracker.

sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

**_Please note you may have to use --force-yes instead of --yes in order for this command to succeed._** 

---

### Post by kc1di on 2012-05-13
If all else fails you can down load the package from here and install it manually using dpkg.

[http://download.videolan.org/pub/libdvdcss/1.2.10/deb/]("http://download.videolan.org/pub/libdvdcss/1.2.10/deb/")

---

### Post by oklokl on 2012-05-13
```
sudo add-apt-repository ppa:nilarimogard/webupd8    ## audacious    https://launchpad.net/~nilarimogard/+archive/webupd8

sudo apt-get update
sudo atp-get install audacious smplayer
```


I this use these two.

---

### Post by kc1di on 2012-05-13
> **kc1di said:**
> If all else fails you can down load the package from here and install it manually using dpkg.

[http://download.videolan.org/pub/libdvdcss/1.2.10/deb/]("http://download.videolan.org/pub/libdvdcss/1.2.10/deb/")

Someone PM'd me asking how to install it using dpkg. since there may be others desiring to know It is like this

first in terminal cd to the folder where you downloaded the package. Then,

In terminal:
```
sudo dpkg -i <complete package Name>
```

Where complete package name is the exact package you wish to install with out the <>

in this case it would be as follows

dpkg -i libdvdcss2_1.2.9-1_i386.deb  

let it do it's stuff and you should be good to go.
the major problem with this method is that if package has other dependencies it will not pull them like apt-get or software center. thus if you have a string of dependencies you'll have to install each one for the program to work.

---

### Post by afz12 on 2012-05-13
Thanks to all those who have replied with suggestions - although I'm not familiar with Linux the replies have been educational! Also, I have had some limited success now with some DVD's, presumably after a number of reboots? Accessing medibuntu is still problematic regardless of location but I'll try later etc. I have enough to go on now in any case and can play DVD's either on 12.04 sometimes, XP/Virtualbox almost always, convert to AVI on XP/Virtualbox, always or on another notebook! Again, thanks to all.

---

### Post by AshleyGD on 2012-05-16
Hi

Just had the same problem, but was able to download a libdvdcss2 package direct from [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

DVD playback works now for me, hope this is helpful?

---

### Post by Baity on 2012-11-12
Worked a treat here!  Thanks, Guys!  :)

---

### Post by 577 Jersey on 2012-11-13
I would try a different DVD/drive,,maybe your drive is flakey,,just saying:guitar:

---

### Post by mike16 on 2013-10-12
I FINALLY FIXED IT!

The Same Problem as guys were having above.

With all the best intentions, I think some of the advice doesn't work because MEDINBUNTU has been shut down - see [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Finally worked out what to do but it took me all night as an ammateur.

Step 1:

Follow these instructions here:  [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

Step 2:

Then go back and do this again (?):  [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Step 3:

Reboot and bingo!

VLC and Gnome player work straight away, but still no joy with Totem - it might need a de and re-install?



GOOD LUCK DUDES!

---

### Post by mike16 on 2013-10-14
Even after a remove and re-instal (with shut down inbetween) Totme wont play DVDs any longer.

EVERY other player I have tried now works though.

---

### Post by nassah on 2013-10-14
Similar problems here, fresh install of 12.04. Medibuntu not being there did feature in some error messages. Difficult to pinpoint exactly which solution worked, but after trying everything in the links at Steps 1 and 2, VLC still wouldn't play. 

1. Went to Synaptic, completely uninstalled everything with VLC in it.
2. Fresh install *VLC* using terminal [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
3. Reinstalled *libdvdread4* and *css* using terminal [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

At last! Didn't test other players, only need the one

---

### Post by moshefeit on 2013-10-14
Oh, maybe you need to install restricted extras?

take a try for:

> sudo apt-get install ubuntu-restricted-extras

---

### Post by agriyanto-dwi on 2013-11-07
> **afz12 said:**
> Hi oldos2er

sudo apt-get update

downloaded 95% but the last entries had proxy errors - I'll try later from a different location



sudo apt-get install libdvdcss2 produced the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

sudo apt-get update && sudo apt-get install libdvdcss2 produced much the same. I think I'll try these on another notebook later - also running Ubuntu 12.04 in case this is notebook specific.

try in terminal "**sudo /usr/share/doc/libdvdread4/install-css.sh**" but first you have done install "**sudo apt-get install ubuntu-restricted-extra"**

---

### Post by deadflowr on 2013-11-07
> **agriyanto-dwi said:**
> try in terminal "**sudo /usr/share/doc/libdvdread4/install-css.sh**" but first you have done install "**sudo apt-get install ubuntu-restricted-extra"**

Even more so then adding the restricted-extras packages is that you MUST install all updates to the system.

The install-css script used to enable the system to get the package from medibuntu, but that closed and the libdvdcss packages moved to videolan.
Older versions of Ubuntu, aka 12.04, need to be up to date so that the changes made to the install file are there, or else running it will result in a fail.

---

### Post by philinux on 2013-11-07
Closed. Ancient thread.

Anyone having problems please start a new thread. Thanks.

---

