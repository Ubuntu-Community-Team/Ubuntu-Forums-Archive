---
title: "Getting started-First time doing this."
date: 2011-05-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Dutch70 on 2011-05-05
Edit: Looks like I've got it upgraded anyway...
```
dave@ubuntu-oneiric:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
dave@ubuntu-oneiric:~$ 
```

I'm getting a couple of errors "404 not found" errors while updating. Do I need to change anything else in my sources.lst? I've included the complete output of the update.

```
dave@ubuntu-oneiric:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for dave: 
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://us.archive.ubuntu.com oneiric InRelease                  
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://extras.ubuntu.com oneiric Release.gpg                     
Get:1 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]       
Hit http://security.ubuntu.com oneiric-security Release.gpg
Ign http://extras.ubuntu.com oneiric Release                         
Hit http://security.ubuntu.com oneiric-security Release              
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg
Get:2 http://us.archive.ubuntu.com oneiric Release [39.8 kB]
Hit http://security.ubuntu.com oneiric-security/main Sources                 
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex          
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Get:3 http://us.archive.ubuntu.com oneiric/main Sources [866 kB]               
Err http://extras.ubuntu.com oneiric/main Sources                             
  404  Not Found
Err http://extras.ubuntu.com oneiric/main amd64 Packages                       
  404  Not Found
Ign http://security.ubuntu.com oneiric-security/main Translation-en_US         
Ign http://security.ubuntu.com oneiric-security/main Translation-en            
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_US   
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_US   
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_US     
Ign http://security.ubuntu.com oneiric-security/universe Translation-en        
Get:4 http://us.archive.ubuntu.com oneiric/restricted Sources [4,104 B]        
Get:5 http://us.archive.ubuntu.com oneiric/universe Sources [4,566 kB]         
Get:6 http://us.archive.ubuntu.com oneiric/multiverse Sources [150 kB]         
Get:7 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,570 kB]      
Get:8 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [9,017 B] 
Get:9 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [6,076 kB]  
Get:10 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [176 kB] 
Ign http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Ign http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Ign http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Ign http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Ign http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Ign http://us.archive.ubuntu.com oneiric/main Translation-en_US                
Ign http://us.archive.ubuntu.com oneiric/main Translation-en
Ign http://us.archive.ubuntu.com oneiric/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Ign http://us.archive.ubuntu.com oneiric/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric/restricted Translation-en
Ign http://us.archive.ubuntu.com oneiric/universe Translation-en_US
Ign http://us.archive.ubuntu.com oneiric/universe Translation-en
Ign http://us.archive.ubuntu.com oneiric-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com oneiric-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Fetched 13.5 MB in 1min 44s (129 kB/s)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
dave@ubuntu-oneiric:~$ 

```

---

### Post by dino99 on 2011-05-06
a working sources.list, follow these steps to do it:

1) edit sources.list:
sudo gedit /etc/apt/sources.list

2) replace your sources by these below (copy/paste) then save and update


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe
  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security restricted main multiverse universe
# deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) natty main
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe

---

### Post by Dutch70 on 2011-05-07
Thank you, but how do I get a working sources.list for Oneiric?

Maybe I'm getting in over my head here, but with a little help I can figure it out.
I just don't know much about this sort of thing, but I would love to learn.

---

### Post by DougieFresh4U on 2011-05-07
> **Dutch70 said:**
> Thank you, but how do I get a working sources.list for Oneiric?

Maybe I'm getting in over my head here, but with a little help I can figure it out.
I just don't know much about this sort of thing, but I would love to learn.

The 2 lines in your sources need to be ## out.
Or go to Software Sources and uncheck the box for 'extras' reload Synaptic and should be good to go :)

---

### Post by Dutch70 on 2011-05-07
Thank you 

I commented them out, here is my sources.list.
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#deb http://extras.ubuntu.com/ubuntu oneiric main
#deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

I got the following in my terminal when I saved it. Should I be concerned with this? 
```
dave@ubuntu-oneiric:~$ sudo gedit /etc/apt/sources.list
[sudo] password for dave: 

(gedit:3200): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KFWWUV': No such file or directory

(gedit:3200): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3200): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.7319UV': No such file or directory

(gedit:3200): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3200): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BK3XUV': No such file or directory

(gedit:3200): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
dave@ubuntu-oneiric:~$ 

```

---

### Post by dino99 on 2011-05-07
see details added in post #2 above

---

### Post by Dutch70 on 2011-05-07
Well, I must be doing something very wrong.

This is the bottom part of update && upgrade.
The top one was actually repeated a over & over. 

```
(gtk-update-icon-cache:4844): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

(gtk-update-icon-cache:4844): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

(gtk-update-icon-cache:4844): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

(gtk-update-icon-cache:4844): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory
Processing triggers for shared-mime-info ...
Processing triggers for libglib2.0-0 ...
Processing triggers for python-support ...
Setting up libgomp1 (4.6.0-6ubuntu3) ...
Setting up lib32gcc1 (1:4.6.0-6ubuntu3) ...
Setting up lib32stdc++6 (4.6.0-6ubuntu3) ...
Setting up libmpfr4 (3.0.1-3) ...
Setting up cpp-4.6 (4.6.0-6ubuntu3) ...
Setting up libquadmath0 (4.6.0-6ubuntu3) ...
Setting up binutils (2.21.51.20110421-0ubuntu5) ...
Setting up gcc-4.6 (4.6.0-6ubuntu3) ...
Setting up libcairo2 (1.10.2-2ubuntu4) ...
Setting up libcairo-gobject2 (1.10.2-2ubuntu4) ...
Setting up libgdk-pixbuf2.0-0 (2.23.3-0ubuntu2) ...
Setting up libnss3 (3.12.9+ckbi-1.82-0ubuntu3) ...
Setting up libnss3-1d (3.12.9+ckbi-1.82-0ubuntu3) ...
Setting up libplymouth2 (0.8.2-2ubuntu23) ...
Setting up plymouth (0.8.2-2ubuntu23) ...
update-initramfs: deferring update (trigger activated)
Setting up plymouth-label (0.8.2-2ubuntu23) ...
Setting up ca-certificates (20110421ubuntu1) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
Exception in thread "main" java.security.ProviderException: Could not initialize NSS
	at sun.security.pkcs11.SunPKCS11.<init>(SunPKCS11.java:201)
	at sun.security.pkcs11.SunPKCS11.<init>(SunPKCS11.java:103)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at sun.security.jca.ProviderConfig$3.run(ProviderConfig.java:262)
	at sun.security.jca.ProviderConfig$3.run(ProviderConfig.java:244)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.security.jca.ProviderConfig.doLoadProvider(ProviderConfig.java:244)
	at sun.security.jca.ProviderConfig.getProvider(ProviderConfig.java:224)
	at sun.security.jca.ProviderList.getProvider(ProviderList.java:232)
	at sun.security.jca.ProviderList.getService(ProviderList.java:330)
	at sun.security.jca.GetInstance.getInstance(GetInstance.java:157)
	at java.security.Security.getImpl(Security.java:696)
	at java.security.AlgorithmParameters.getInstance(AlgorithmParameters.java:130)
	at sun.security.x509.AlgorithmId.decodeParams(AlgorithmId.java:121)
	at sun.security.x509.AlgorithmId.<init>(AlgorithmId.java:114)
	at sun.security.x509.AlgorithmId.parse(AlgorithmId.java:381)
	at sun.security.x509.X509Key.parse(X509Key.java:168)
	at sun.security.x509.CertificateX509Key.<init>(CertificateX509Key.java:75)
	at sun.security.x509.X509CertInfo.parse(X509CertInfo.java:705)
	at sun.security.x509.X509CertInfo.<init>(X509CertInfo.java:169)
	at sun.security.x509.X509CertImpl.parse(X509CertImpl.java:1747)
	at sun.security.x509.X509CertImpl.<init>(X509CertImpl.java:196)
	at sun.security.provider.X509Factory.engineGenerateCertificate(X509Factory.java:107)
	at java.security.cert.CertificateFactory.generateCertificate(CertificateFactory.java:322)
	at sun.security.provider.JavaKeyStore.engineLoad(JavaKeyStore.java:763)
	at sun.security.provider.JavaKeyStore$JKS.engineLoad(JavaKeyStore.java:55)
	at java.security.KeyStore.load(KeyStore.java:1201)
	at UpdateCertificates.createKeyStore(UpdateCertificates.java:65)
	at UpdateCertificates.main(UpdateCertificates.java:51)
Caused by: java.io.FileNotFoundException: /usr/lib/libnss3.so
	at sun.security.pkcs11.Secmod.initialize(Secmod.java:186)
	at sun.security.pkcs11.SunPKCS11.<init>(SunPKCS11.java:197)
	... 31 more
E: /etc/ca-certificates/update.d/jks-keystore exited with code 1.
done.
Setting up openssh-client (1:5.8p1-4ubuntu1) ...
Setting up plymouth-theme-ubuntu-text (0.8.2-2ubuntu23) ...
update-initramfs: deferring update (trigger activated)
Setting up gir1.2-gdkpixbuf-2.0 (2.23.3-0ubuntu2) ...
Setting up liba52-0.7.4 (0.7.4-15) ...
Setting up libupower-glib1 (0.9.10-1) ...
Setting up linux-libc-dev (2.6.39-1.6) ...
Setting up plymouth-theme-ubuntu-logo (0.8.2-2ubuntu23) ...
update-initramfs: deferring update (trigger activated)
Setting up ssh-askpass-gnome (1:5.8p1-4ubuntu1) ...
Setting up upower (0.9.10-1) ...
Installing new version of config file /etc/UPower/UPower.conf ...
Setting up wpasupplicant (0.7.3-3) ...
Installing new version of config file /etc/wpa_supplicant/functions.sh ...
Setting up libdconf0 (0.7.3-4) ...
Setting up mobile-broadband-provider-info (20110424-1) ...
Setting up libmtp-runtime (1.0.6-5) ...
Setting up libstdc++6-4.6-dev (4.6.0-6ubuntu3) ...
Setting up libmtp8 (1.0.6-5) ...
Setting up banshee (2.0.1-1ubuntu1) ...
Setting up banshee-extension-soundmenu (2.0.1-1ubuntu1) ...
Setting up banshee-extension-ubuntuonemusicstore (2.0.1-1ubuntu1) ...
Setting up g++-4.6 (4.6.0-6ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.39-0-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169
dave@ubuntu-oneiric:~$ 

```

I did add the ubuntu restricted extras btw, should I remove them? Reinstall & start over perhaps?

---

### Post by Dutch70 on 2011-05-07
> **dino99 said:**
> see details added in post #2 above

I just saw your post dino, thanks again. :)

---

### Post by Dutch70 on 2011-05-07
Ok, after replacing my sources.list with post #2 sources. I got this when running the update.

```
dave@ubuntu-oneiric:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for dave: 
Ign http://download.virtualbox.org natty InRelease
Ign http://archive.canonical.com natty InRelease                               
Get:1 http://download.virtualbox.org natty Release.gpg [197 B]                 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-proposed InRelease                       
Ign http://ppa.launchpad.net natty InRelease                                   
Get:2 http://download.virtualbox.org natty Release [5,381 B]                   
Get:3 http://archive.canonical.com natty Release.gpg [198 B]                   
Ign http://download.virtualbox.org natty Release                               
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Get:4 http://archive.ubuntu.com oneiric Release.gpg [198 B]                    
Get:5 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Get:6 http://download.virtualbox.org natty/contrib amd64 Packages [988 B]      
Ign http://download.virtualbox.org natty/contrib TranslationIndex              
Get:7 http://archive.canonical.com natty Release [5,916 B]                     
Hit http://security.ubuntu.com oneiric-security Release                        
Get:8 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]            
Get:9 http://ppa.launchpad.net natty Release [9,744 B]                         
Get:10 http://archive.ubuntu.com oneiric-proposed Release.gpg [198 B]          
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Ign http://ppa.launchpad.net natty Release                                     
Get:11 http://archive.canonical.com natty/partner amd64 Packages [6,740 B]     
Get:12 http://archive.ubuntu.com oneiric Release [39.8 kB]                     
Get:13 http://ppa.launchpad.net natty/main amd64 Packages [2,408 B]            
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex          
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://download.virtualbox.org natty/contrib Translation-en_US             
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://download.virtualbox.org natty/contrib Translation-en                
Get:14 http://archive.ubuntu.com oneiric-updates Release [23.2 kB]             
Get:15 http://archive.ubuntu.com oneiric-proposed Release [23.2 kB]            
Get:16 http://archive.ubuntu.com oneiric/restricted amd64 Packages [9,001 B]   
Get:17 http://archive.ubuntu.com oneiric/main amd64 Packages [1,574 kB]        
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://security.ubuntu.com oneiric-security/main Translation-en_US         
Ign http://security.ubuntu.com oneiric-security/main Translation-en            
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_US   
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_US
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_US
Ign http://security.ubuntu.com oneiric-security/universe Translation-en
Get:18 http://archive.ubuntu.com oneiric/multiverse amd64 Packages [176 kB]    
Get:19 http://archive.ubuntu.com oneiric/universe amd64 Packages [6,076 kB]    
Ign http://archive.ubuntu.com oneiric/main TranslationIndex                    
Ign http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Ign http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Ign http://archive.ubuntu.com oneiric/universe TranslationIndex                
Get:20 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [14 B]
Get:21 http://archive.ubuntu.com oneiric-updates/main amd64 Packages [14 B]    
Get:22 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [14 B]
Get:23 http://archive.ubuntu.com oneiric-updates/universe amd64 Packages [14 B]
Ign http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Ign http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Ign http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex      
Ign http://archive.ubuntu.com oneiric-updates/universe TranslationIndex        
Get:24 http://archive.ubuntu.com oneiric-proposed/restricted amd64 Packages [14 B]
Get:25 http://archive.ubuntu.com oneiric-proposed/main amd64 Packages [14 B]   
Get:26 http://archive.ubuntu.com oneiric-proposed/multiverse amd64 Packages [14 B]
Get:27 http://archive.ubuntu.com oneiric-proposed/universe amd64 Packages [14 B]
Ign http://archive.ubuntu.com oneiric-proposed/main TranslationIndex           
Ign http://archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex     
Ign http://archive.ubuntu.com oneiric-proposed/restricted TranslationIndex     
Ign http://archive.ubuntu.com oneiric-proposed/universe TranslationIndex       
Ign http://archive.ubuntu.com oneiric/main Translation-en_US                   
Ign http://archive.ubuntu.com oneiric/main Translation-en
Ign http://archive.ubuntu.com oneiric/multiverse Translation-en_US
Ign http://archive.ubuntu.com oneiric/multiverse Translation-en
Ign http://archive.ubuntu.com oneiric/restricted Translation-en_US
Ign http://archive.ubuntu.com oneiric/restricted Translation-en
Ign http://archive.ubuntu.com oneiric/universe Translation-en_US
Ign http://archive.ubuntu.com oneiric/universe Translation-en
Ign http://archive.ubuntu.com oneiric-updates/main Translation-en_US
Ign http://archive.ubuntu.com oneiric-updates/main Translation-en
Ign http://archive.ubuntu.com oneiric-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Ign http://archive.ubuntu.com oneiric-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Ign http://archive.ubuntu.com oneiric-updates/universe Translation-en_US
Ign http://archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://archive.ubuntu.com oneiric-proposed/main Translation-en_US
Ign http://archive.ubuntu.com oneiric-proposed/main Translation-en
Ign http://archive.ubuntu.com oneiric-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com oneiric-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com oneiric-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com oneiric-proposed/restricted Translation-en
Ign http://archive.ubuntu.com oneiric-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com oneiric-proposed/universe Translation-en
Fetched 7,953 kB in 1min 10s (112 kB/s)
Reading package lists... Done
W: GPG error: http://download.virtualbox.org natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
dave@ubuntu-oneiric:~$ 

```

Update Manager won't even open now. Nothing at all happens when I click on it.
Hahaa, I'm having fun already :P

---

### Post by wilee-nilee on 2011-05-07
To get these keys.
```
W: GPG error: http://download.virtualbox.org natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
```

Do this.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

I have Oneiric with the restricted extras a spinning beautiful cube, wobbling windows running great, the upgrade brought back the darn side panel lol.

---

### Post by Dutch70 on 2011-05-07
Ok, this is what I got from that command.

```
dave@ubuntu-oneiric:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
[sudo] password for dave: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys KEYID
gpg: "KEYID" not a key ID: skipping
dave@ubuntu-oneiric:~$ 

```

LOL, I just realized I was supposed to replace "KEYID" with an actual key id, I'm embarrassed to say, I'm not exactly sure where to get that at.

Edit: I'm on my launchpad account reading about it now...lol.

---

### Post by dino99 on 2011-05-07
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

these KEYID are of course: 54422A4B98AB5139  &  5A9A06AEF9CB8DB0

note: if you want to play with numerous issues/troubles/headaches related to each new alpha/beta distro (and oneiric is not yet alpha :)) you need first some knowledge and be used with bugs. So dont only use oneiric because it will break many times before final release.

---

### Post by Dutch70 on 2011-05-07
Well the first Alpha I installed was Natty with Ubuntu & Kubuntu. So that's when I started reporting bugs, it's somewhat new to me, but I'm learning as I go. 

I have no intention of depending on Oneiric. Thanks for the warning though. I actually have about 10 distro's on 2 hard drives. That's counting 3 instances of Natty. One for regular use, one to try Gnome3 *(I was going to delete it anyway)* & one for Oneiric.

As I said though, this is very new to me. I had no idea we could start with Oneiric before the Alpha.

---

