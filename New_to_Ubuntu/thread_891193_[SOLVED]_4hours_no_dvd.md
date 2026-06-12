---
title: "[SOLVED] 4hours no dvd"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by intimatewipe on 2008-08-15
Hello Peeps,I'm tearing my hair out here,trying to get dvd playback going,yes I have gone through the tutorials and downloaded all the suggested codecs/applications etc,still no go,vlc will play ripped dvds but stutters,nothing will play movie (shop) dvds,I have movie player, mplayer movie player and vlc,mplayer is looking for gstreamer but when it tries to get it I get this error.I have googled this and others have had this problem and one suggestion said to find the locked file in the rpm download folder(there are a lot of folders with lock in the name)and delete it,I don't care if I can't play dvds on ubuntu(have 3 pcs) but I have put Ubuntu on on other peoples pcs and they will want this feature,best suggestion much appreciated:(

---

### Post by intimatewipe on 2008-08-15
sorry this is the error

---

### Post by iaculallad on 2008-08-15
On your terminal:

```
sudo rm -rf /var/cache/apt/archives/lock
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade

```

And make sure that there are no other Apt-get/Synaptics processes running in background.

---

### Post by intimatewipe on 2008-08-15
I'll try this mate:)

---

### Post by intimatewipe on 2008-08-15
this happened,blimey,will try and down load gstreamer now,let you know
kris@kris-desktop:~$ sudo rm -rf /var/cache/apt/archives/lock
[sudo] password for kris: 
kris@kris-desktop:~$ sudo rm -rf /var/cache/apt/archives/lock
kris@kris-desktop:~$ sudo dpkg --configure -a
kris@kris-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpurple0 pidgin pidgin-data
The following packages will be upgraded:
  gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 transmission-common
  transmission-gtk
7 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 15.3MB of archives.
After this operation, 2515kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp-python 2.4.6-1ubuntu1~hardy1 [195kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp-gnomevfs 2.4.6-1ubuntu1~hardy1 [8412B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp 2.4.6-1ubuntu1~hardy1 [3930kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main libgimp2.0 2.4.6-1ubuntu1~hardy1 [981kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp-data 2.4.6-1ubuntu1~hardy1 [9735kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main transmission-gtk 1.22-1ubuntu1~hardy1 [428kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main transmission-common 1.22-1ubuntu1~hardy1 [15.7kB]
Fetched 15.3MB in 19s (775kB/s)                                                
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 101150 files and directories currently installed.)
Preparing to replace gimp-python 2.4.5-1ubuntu2 (using .../gimp-python_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp-python ...
Preparing to replace gimp-gnomevfs 2.4.5-1ubuntu2 (using .../gimp-gnomevfs_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp-gnomevfs ...
Preparing to replace gimp 2.4.5-1ubuntu2 (using .../gimp_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp ...
Preparing to replace libgimp2.0 2.4.5-1ubuntu2 (using .../libgimp2.0_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement libgimp2.0 ...
Preparing to replace gimp-data 2.4.5-1ubuntu2 (using .../gimp-data_2.4.6-1ubuntu1~hardy1_all.deb) ...
Unpacking replacement gimp-data ...
Preparing to replace transmission-gtk 1.06-0ubuntu6 (using .../transmission-gtk_1.22-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement transmission-gtk ...
Preparing to replace transmission-common 1.06-0ubuntu6 (using .../transmission-common_1.22-1ubuntu1~hardy1_all.deb) ...
Unpacking replacement transmission-common ...
Setting up gimp-data (2.4.6-1ubuntu1~hardy1) ...

Setting up libgimp2.0 (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp-python (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp-gnomevfs (2.4.6-1ubuntu1~hardy1) ...
Setting up transmission-common (1.22-1ubuntu1~hardy1) ...
Setting up transmission-gtk (1.22-1ubuntu1~hardy1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kris@kris-desktop:~$

---

### Post by nicedude on 2008-08-15
To play DVD's you will need the dvdcss package from medibuntu then you can just install say VLC player and watch DVD's all you like. You see DVD's have a weak encryption scheme on them that you need that package for in order to decode them, then they should be playable in many players etc but I like VLC for DVD playback.

So google MEDIBUNTU and add those sources to yours so you can download from medibuntu and get what you need :-)

the actual name of the package exactly is libdvdcss2 and the player I mentioned will play just about anything and it is called vlc . you can find them by searching by name in the synaptic package manager

System -> Administration -> Synaptic Package Manager 

OR IN A TERMINAL

sudo synaptic

Hope this helps you out

---

### Post by dje on 2008-08-15
theres a very good guide for all codecs [here]("http://www.ubuntu1501.com/2008/04/easy-media-codec-installation-for-hardy.html")

dje

---

### Post by iaculallad on 2008-08-15
> **intimatewipe said:**
> this happened,blimey,will try and down load gstreamer now,let you know
kris@kris-desktop:~$ sudo rm -rf /var/cache/apt/archives/lock
[sudo] password for kris: 
kris@kris-desktop:~$ sudo rm -rf /var/cache/apt/archives/lock
kris@kris-desktop:~$ sudo dpkg --configure -a
kris@kris-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpurple0 pidgin pidgin-data
The following packages will be upgraded:
  gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 transmission-common
  transmission-gtk
7 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 15.3MB of archives.
After this operation, 2515kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp-python 2.4.6-1ubuntu1~hardy1 [195kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp-gnomevfs 2.4.6-1ubuntu1~hardy1 [8412B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp 2.4.6-1ubuntu1~hardy1 [3930kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main libgimp2.0 2.4.6-1ubuntu1~hardy1 [981kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main gimp-data 2.4.6-1ubuntu1~hardy1 [9735kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main transmission-gtk 1.22-1ubuntu1~hardy1 [428kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main transmission-common 1.22-1ubuntu1~hardy1 [15.7kB]
Fetched 15.3MB in 19s (775kB/s)                                                
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 101150 files and directories currently installed.)
Preparing to replace gimp-python 2.4.5-1ubuntu2 (using .../gimp-python_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp-python ...
Preparing to replace gimp-gnomevfs 2.4.5-1ubuntu2 (using .../gimp-gnomevfs_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp-gnomevfs ...
Preparing to replace gimp 2.4.5-1ubuntu2 (using .../gimp_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp ...
Preparing to replace libgimp2.0 2.4.5-1ubuntu2 (using .../libgimp2.0_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement libgimp2.0 ...
Preparing to replace gimp-data 2.4.5-1ubuntu2 (using .../gimp-data_2.4.6-1ubuntu1~hardy1_all.deb) ...
Unpacking replacement gimp-data ...
Preparing to replace transmission-gtk 1.06-0ubuntu6 (using .../transmission-gtk_1.22-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement transmission-gtk ...
Preparing to replace transmission-common 1.06-0ubuntu6 (using .../transmission-common_1.22-1ubuntu1~hardy1_all.deb) ...
Unpacking replacement transmission-common ...
Setting up gimp-data (2.4.6-1ubuntu1~hardy1) ...

Setting up libgimp2.0 (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp-python (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp-gnomevfs (2.4.6-1ubuntu1~hardy1) ...
Setting up transmission-common (1.22-1ubuntu1~hardy1) ...
Setting up transmission-gtk (1.22-1ubuntu1~hardy1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kris@kris-desktop:~$

With that output, you're good to go. Next step for you is to try what nicedude had suggested.

---

### Post by intimatewipe on 2008-08-15
Thanks iaculallad,they freed up my thingy, :)
still no luck with the dvds,will try again tomorrow,lots of people saying vlc is great so I'll follow that trail,all the other media stuff I downloaded works fine,will try flash/streaming vid as well,most important the error message is gone thanks.:)

---

### Post by intimatewipe on 2008-08-15
thanks dje/nice dude,will be on that tomorrow,least I can access the 
duberrywhatsits,I hate errors :mad:

Thanks again

---

