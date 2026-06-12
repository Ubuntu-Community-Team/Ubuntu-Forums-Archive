---
title: "can't download in software center"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by stum22 on 2012-07-16
I'm very new to this, so please bear with me. I'm using a work computer trying to set up a ubuntu part to my windows 7. I have the Internet set up (so I can file this) but I can't seem to download any files. 

I tried solutions here but no avail: [http://askubuntu.com/questions/156936/12-04-ubuntu-software-center-wont-download-when-i-click-install](http://askubuntu.com/questions/156936/12-04-ubuntu-software-center-wont-download-when-i-click-install)

smills@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                              
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages                                       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages                                 
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages                                   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages                                 
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                                        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages                                  
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages                                    
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages                                  
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US                                    
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

smills@ubuntu:~$ ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (74.125.237.147) 56(84) bytes of data.

Thanks!

---

### Post by NikTh on 2012-07-17
Hi , 
try to change download server . Go to Update Manager > Settings and from first section "Ubuntu Software" change the "Download from:" to something more appropriate or even try the main server.
Thanks

---

### Post by stum22 on 2012-07-17
I got this:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.'

I downloaded using the web version so maybe something happened?

Thanks, Stu

---

### Post by stum22 on 2012-07-17
Also software center just keeps crashing and not opening at the moment...

---

### Post by NikTh on 2012-07-17
> **stum22 said:**
> 

'E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.'

Hi , 
try to run these commands one at time , by copy-paste form here to your terminal (for more accuracy) and see how it goes 
```
sudo rm -rf /var/lib/apt/lists/*
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update ; sudo apt-get dist-upgrade
```Post back here the **results of last command**. (One line = one command)
**Please put the results inside [CODE] tags , by highlighting the text and click at [SIZE=3]#[/SIZE] symbol on top of message pane.**
Thanks

---

### Post by stum22 on 2012-07-17
```
smills@ubuntu:~$ sudo apt-get update ; sudo apt-get dist-upgrade
Ign http://security.ubuntu.com precise-security InRelease           
Err http://security.ubuntu.com precise-security Release.gpg         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign http://security.ubuntu.com precise-security Release
Ign http://security.ubuntu.com precise-security/main TranslationIndex
Ign http://security.ubuntu.com precise-security/multiverse TranslationIndex
Ign http://security.ubuntu.com precise-security/restricted TranslationIndex
Ign http://security.ubuntu.com precise-security/universe TranslationIndex
Err http://security.ubuntu.com precise-security/main amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/main i386 Packages  
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/main Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/main Translation-en 
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign http://archive.ubuntu.com precise InRelease       
Ign http://archive.ubuntu.com precise-updates InRelease
Err http://archive.ubuntu.com precise Release.gpg     
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Ign http://archive.ubuntu.com precise Release
Ign http://archive.ubuntu.com precise-updates Release
Ign http://archive.ubuntu.com precise/main TranslationIndex
Ign http://archive.ubuntu.com precise/multiverse TranslationIndex
Ign http://archive.ubuntu.com precise/restricted TranslationIndex
Ign http://archive.ubuntu.com precise/universe TranslationIndex
Ign http://archive.ubuntu.com precise-updates/main TranslationIndex
Ign http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com precise-updates/universe TranslationIndex
Err http://archive.ubuntu.com precise/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err http://archive.ubuntu.com precise-updates/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.24 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
[sudo] password for smills: 
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.

```

Thanks!

---

### Post by stum22 on 2012-07-17
Dont know if the specs will help:

```
description: Laptop
    product: Latitude E6410 ()
    vendor: Winbond Electronics
    version: 0001
    serial: 5YQ35Q1
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=laptop uuid=44454C4C-5900-1051-8033-B5C04F355131
  *-core
       description: Motherboard
       vendor: Winbond Electronics
       physical id: 0
       serial: /5YQ35Q1//
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A06
          date: 11/20/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GH
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1199MHz
          capacity: 4GHz
          width: 64 bits
          clock: 533MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 0
             serial: 1030110E
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 1
             serial: A52E110F
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:7110(size=8)
        *-network
             description: Ethernet interface
             product: 82577LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 05
             serial: 5c:26:0a:43:ac:b1
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.12-1 ip=136.154.16.91 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:40 memory:f6900000-f691ffff memory:f6970000-f6970fff ioport:7020(size=32)
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f6960000-f69603ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f6950000-f6953fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:6000(size=4096) memory:f5500000-f68fffff ioport:f6e00000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:5000(size=4096) memory:f4100000-f54fffff ioport:f6c00000(size=2097152)
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6200
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 35
                serial: 18:3d:a2:37:a8:ec
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:42 memory:f4100000-f4101fff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=8192) memory:f0400000-f2cfffff
           *-pcmcia
                description: CardBus bridge
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:18 memory:f2c40000-f2c40fff ioport:2400(size=256) ioport:2000(size=256) memory:f0400000-f17fffff memory:f1800000-f1bfffff
           *-generic
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:f2c30000-f2c300ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 PCIe IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:f2c00000-f2c007ff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:4000(size=4096) memory:f2d00000-f40fffff ioport:f6a00000(size=2097152)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:17 memory:f6940000-f69403ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:70f0(size=8) ioport:70e0(size=4) ioport:70d0(size=8) ioport:70c0(size=4) ioport:70b0(size=16) ioport:70a0(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG SSD PM81
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AXM0
                serial: S0NRNEAB400090
                size: 119GiB (128GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=814a3d33
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /host
                   version: 3.1
                   serial: a87b976b-a9e9-594e-9268-155e5d6d6f5a
                   size: 119GiB
                   capacity: 119GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-09-28 03:01:27 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-U633J
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: D400
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6930000-f69300ff ioport:7000(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:7090(size=8) ioport:7080(size=4) ioport:7070(size=8) ioport:7060(size=4) ioport:7050(size=16) ioport:7040(size=16)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:f6920000-f6920fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
  *-battery
       product: DELL G6M0W13
       vendor: Samsung SDI
       physical id: 1
       version: 3/24/2011
       serial: 7A54
       slot: Sys. Battery Bay
       capacity: 56000mWh
       configuration: voltage=11.2V
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
```

---

### Post by jmfal on 2012-07-17
Welcome to Ubuntu

Go back to the Update center and in the first tab ( ubuntu sofrware)
remove check from the >>CD With Precise Pangolin <<< box at bottom of window

In the >>Other Sofrware <<< tab remove check from top two >>CD
With Precise Pangolin.

And run commands from NikTh  again

---

### Post by stum22 on 2012-07-17
You mean update manager? I cant open that - see the second message.

---

### Post by jmfal on 2012-07-17
Close the Software center and terminal, and try to open Update Manager.

---

### Post by stum22 on 2012-07-17
Same message:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.'
```

Even when I turned off the computer and relogged on

---

### Post by bobsan on 2012-07-17
Hi, what do you mean by trying to set up Ubuntu inside Windows7? Are you using WUBI?

---

### Post by stum22 on 2012-07-17
> **bobsan said:**
> Hi, what do you mean by trying to set up Ubuntu inside Windows7? Are you using WUBI?

Yes I installed it using WUBI. But havent fiddled after that. I'll check again in the morning thanks for suggestions!

---

### Post by NikTh on 2012-07-17
> **stum22 said:**
> 
```

'E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.'
```
Hi , 
this is the mistake. This file must be there from beginning. I don't know how you missed this file. As alternative you can copy the status-old file to the missing file . 
Open terminal and run these commands (anything else must be closed, only terminal open)
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
sudo rm /var/lib/dkpg/lock 
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update ; sudo apt-get upgrade
ls /var/lib/dpkg/
``` 
give the results of last command. 
Thanks

---

### Post by stum22 on 2012-07-17
```
smills@ubuntu:~$ ls /var/lib/dpkg/
alternatives   cmethopt    diversions-old  lock   statoverride  triggers
available-bad  diversions  info            parts  status-bad    updates

```

There was still lots of failing....

---

### Post by matt_symes on 2012-07-17
Hi

If you don't have a backup status file (status-old) in 

```
/var/lib/dpkg/
```

then look in 

```
/var/backups
```

I have a number in mine.
```

matthew@matthew-Aspire-7540 ~ % ls /var/backups/dpkg*
/var/backups/dpkg.status.0     /var/backups/dpkg.status.2.gz  /var/backups/dpkg.status.4.gz  /var/backups/dpkg.status.6.gz
/var/backups/dpkg.status.1.gz  /var/backups/dpkg.status.3.gz  /var/backups/dpkg.status.5.gz
matthew@matthew-Aspire-7540 ~ % 
```

Kind regards

---

### Post by stum22 on 2012-07-17
I have 1 it seems:

```
smills@ubuntu:~$ ls /var/backups/dpkg*
/var/backups/dpkg.status.0

```

---

### Post by matt_symes on 2012-07-17
Hi

Make sure software center is closed and update manager is not running.

From the command line...

```

sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status 
``````
sudo apt-get update
```Post back any errors.

Kind regards

---

### Post by stum22 on 2012-07-17
Thanks for the help. Plenty of errors:

```
smills@ubuntu:~$ sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
[sudo] password for smills: 
smills@ubuntu:~$ sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease                      
Err http://security.ubuntu.com precise-security Release.gpg                    
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign http://security.ubuntu.com precise-security Release
Ign http://security.ubuntu.com precise-security/main TranslationIndex
Ign http://security.ubuntu.com precise-security/multiverse TranslationIndex
Ign http://security.ubuntu.com precise-security/restricted TranslationIndex
Ign http://security.ubuntu.com precise-security/universe TranslationIndex
Err http://security.ubuntu.com precise-security/main amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe amd64 Packages        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse amd64 Packages      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/main i386 Packages             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe i386 Packages         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/main Translation-en_US         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/multiverse Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted Translation-en_US   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/restricted Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe Translation-en_US     
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://security.ubuntu.com precise-security/universe Translation-en        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease
Err http://archive.ubuntu.com precise Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Ign http://archive.ubuntu.com precise Release
Ign http://archive.ubuntu.com precise-updates Release
Ign http://archive.ubuntu.com precise/main TranslationIndex
Ign http://archive.ubuntu.com precise/multiverse TranslationIndex
Ign http://archive.ubuntu.com precise/restricted TranslationIndex
Ign http://archive.ubuntu.com precise/universe TranslationIndex
Ign http://archive.ubuntu.com precise-updates/main TranslationIndex
Ign http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com precise-updates/universe TranslationIndex
Err http://archive.ubuntu.com precise/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
Err http://archive.ubuntu.com precise-updates/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.155 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by matt_symes on 2012-07-17
Hi

Now try changing to a different server as explained in post #2.

Kind regards

---

### Post by stum22 on 2012-07-17
Thanks Matt.

I can get into update manager I changed to American servers which was the only one I could pick, but I still cant seem to download. Is there something wrong with the internet connection? Although I'm using the internet to do this....work firewall?

---

### Post by stum22 on 2012-07-18
using the US server I still get

```
W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.154 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by matt_symes on 2012-07-18
Hi

> work firewall?Are you behind a proxy server ? 

[http://www.lagado.com/proxy-test](http://www.lagado.com/proxy-test)

This is not a foolproof check above so double check

If you are have you set up the proxy settings for apt ?

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

Can you get a file manually ?

```
cd && wget security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en.bz2
```Kind regards

---

### Post by stum22 on 2012-07-18
I am somewhere close now. Proxy set up and then I used the commands to update.

Then  I get this from update manager after it asks me to install the updates:

```
installArchives() failed: E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 20%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 41%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 62%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 83%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 100%% 
E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 20%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 41%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 62%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 83%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 100%% 
E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 20%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 41%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 62%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 83%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 100%% 
E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 20%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 41%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 62%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 83%%E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: Illegal seek 
 Extracting templates from packages: 100%% 
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory 

```

Thanks for the help!

---

### Post by stum22 on 2012-07-18
bump

---

### Post by jmfal on 2012-07-19
Try using synaptic  
It doesn't have the eye candy that software center has but is more efficient.

I've had nothing but problems using software center, just like you are right now.

```
  sudo apt-get install synaptic    
```

---

### Post by stum22 on 2012-07-19
almost getting there maybe.

Had another problem though:

```
Extracting templates from packages: 100%
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
smills@ubuntu:~$ sudo apt-get install debconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apt-utils coreutils debconf-i18n dpkg gcc-4.6-base libacl1 libapt-inst1.4 libapt-pkg4.12
  libattr1 libbz2-1.0 libc-bin libc6 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1
  libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl multiarch-support
  perl-base tar tzdata xz-utils zlib1g
Suggested packages:
  debconf-doc debconf-utils whiptail dialog gnome-utils libterm-readline-gnu-perl libgtk2-perl
  libnet-ldap-perl libqtgui4-perl libqtcore4-perl apt glibc-doc locales bzip2 ncompress xz-lzma
The following NEW packages will be installed:
  apt-utils coreutils debconf debconf-i18n dpkg gcc-4.6-base libacl1 libapt-inst1.4
  libapt-pkg4.12 libattr1 libbz2-1.0 libc-bin libc6 libdb5.1 libgcc1 liblocale-gettext-perl
  liblzma5 libselinux1 libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl
  multiarch-support perl-base tar tzdata xz-utils zlib1g
0 upgraded, 28 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/15.1 MB of archives.
After this operation, 44.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Somethings failing at the end?

---

### Post by matt_symes on 2012-07-19
Hi

You ave a very broken package version :( How did it get in this state :confused:

I think we are making progress though so let's work through the problems you have left. It may not be a quick fix though.

Let's try 2 solutions for the last error message about the available file.

1.

First let's see if you have an old available file.

```
sudo  cp /var/lib/dpkg/available-old  /var/lib/dpkg/available
``````
sudo apt-get update
```2.

If that does not fix the missing available file then you will have to manually wget the package list files, unzip them and use dpkg.

Here is an example

```
http://91.189.92.184/ubuntu/dists/precise-security/main/binary-amd64/Packages.gz
``````
gunzip -d Packages.gz
```This will produce a file called Packages.

Finally...

```
dpkg --update-avail Packages
```You will need to do this for main, universe and multiverse for the two missing repostiories (and any others you may have).

Do all this from the terminal and then we can look at the last of the errors returned from software-center and synaptic.

Kind regards

---

### Post by stum22 on 2012-07-19
I don't know how :(

OK so I think 1. worked but then I couldn't update Packages?

```
smills@ubuntu:~$ sudo cp /var/lib/dpkg/available-old /varlib/dpkg/available
[sudo] password for smills: 
cp: cannot stat `/var/lib/dpkg/available-old': No such file or directory
smills@ubuntu:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://security.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:4 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:5 http://us.archive.ubuntu.com precise Release [49.6 kB]        
Get:6 http://security.ubuntu.com precise-security/main amd64 Packages [95.0 kB]
Get:7 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:8 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:9 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]      
Get:10 http://security.ubuntu.com precise-security/universe amd64 Packages [24.2 kB]
Get:11 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Get:12 http://security.ubuntu.com precise-security/main i386 Packages [97.6 kB]
Get:13 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:14 http://security.ubuntu.com precise-security/universe i386 Packages [24.4 kB]
Get:15 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:16 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:17 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:18 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:19 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:20 http://security.ubuntu.com precise-security/main Translation-en [50.5 kB]
Get:21 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:22 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:23 http://security.ubuntu.com precise-security/universe Translation-en [15.6 kB]
Get:24 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:25 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:26 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:27 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:28 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:29 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [328 kB]
Get:30 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:31 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [94.7 kB]
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,829 B]
Get:33 http://us.archive.ubuntu.com precise-updates/main i386 Packages [330 kB]
Get:34 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:35 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [95.2 kB]
Get:36 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Get:37 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:38 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:39 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:40 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Fetched 13.7 MB in 40s (338 kB/s)                                              
Reading package lists... Done
smills@ubuntu:~$ dpkg --update-avail Packages
dpkg: error: bulk available update requires write access to dpkg status area
smills@ubuntu:~$ 

```

Thanks!

---

### Post by matt_symes on 2012-07-19
Hi

That did not work stum22 as you did not have the backup file

```
/var/lib/dpkg/available-old
```Just to double check something, please post the output of

```
ls -l /var/lib/dpkg/available
```We are going to have to use method 2.

First though please post the output of this so we can see what files you need to get.

```
grep -v "^#" /etc/apt/sources.list
```Kind regards

---

### Post by stum22 on 2012-07-19
Thanks again Matt.

```
smills@ubuntu:~$ ls -l /var/lib/dpkg/available
ls: cannot access /var/lib/dpkg/available: No such file or directory
smills@ubuntu:~$ grep -v "^#" /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

```

---

### Post by Rsjc741 on 2012-07-19
You said you can access the internet?

try pinging the IP's listed in your posts.

To do this, do:

CRTL+ALT+T

ping XX.XXX.XXX (for instance, X's should be replaced with actual IP's)

You should either get a "All packets lost, or something opposite of that.

If your getting an XX% packets lost (not a full 100% or 0%), it could mean a problem with your connection.

If you get a "Connection refused", then maybe it's an issue with either their ports, the way youre connecting with the servers, or your ports.

---

### Post by madjr on 2012-07-19
was this an upgrade from a previous version (like 11.10) or you did a fresh install of 12.04 ?

---

### Post by matt_symes on 2012-07-19
Hi

I think we are making progress.

I'm writing you a script that will recreate your available package list for you. I'll test it and post it back.

Do you have any idea why your package system is so broken ? You are missing some very important dpkg files. I am interested if you can shed any light on this.

> was this an upgrade from a previous version (like 11.10) or you did a fresh install of 12.04 ?

This is a good question.

Kind regards

---

### Post by matt_symes on 2012-07-19
Hi

Open gedit and copy and paste this into it. Save the file in your home directory as script.sh.

```

#!/bin/bash

# Create an empty available list.
touch /var/lib/dpkg/available

#http://us.archive.ubuntu.com
for i in "precise" "precise-updates" 
do
    for j in "main" "universe" "multiverse" "restricted" 
    do
        for k in "binary-amd64" "binary-i386" 
        do
            filename="$i.$j.$k.Packages";

            # get package.
            wget "http://us.archive.ubuntu.com/ubuntu/dists/$i/$j/$k/Packages.gz" -O "/tmp/${filename}.gz"; # 2&>1 log.log;
            
            # unzip filename            
            gunzip -d "/tmp/${filename}.gz";

            # update the availabe list with the new package information
            dpkg --merge-avail "/tmp/$filename"
        done;
    done;
done;

#http://security.ubuntu.com/
for j in "main" "universe" "multiverse" "restricted" 
do
    for k in "binary-amd64" "binary-i386" 
    do
        filename="sec.$i.$j.$k.Packages";

        wget "http://security.ubuntu.com/ubuntu/dists/precise-security/$j/$k/Packages.gz" -O "/tmp/${filename}.gz"; # 2&>1 log.log;

        # unzip filename            
        gunzip -d "/tmp/${filename}.gz";

        # update the availabe list with the new package information
        dpkg --merge-avail "/tmp/$filename"
    done;
done;

# clean up
sudo rm /tmp/{sec.,}precise*
```

Open a termina and type

```
chmod 755 script.sh
```

then type

```
sudo ./script.sh
```

It will chug away recreating your available package list file. I have not bothered with translation files.

Then type

```
sudo apt-get update
```

and finally

```
sudo apt-get install htop
```

Post back any errors from the terminal.

Kind regards

---

### Post by stum22 on 2012-07-20
It was a fresh install, all I did was download then try to use.

Busy doing the files. BRB!

---

### Post by stum22 on 2012-07-20
More problems connecting?

```
 smills@ubuntu:~$ ls -l /var/lib/dpkg/available
ls: cannot access /var/lib/dpkg/available: No such file or directory
smills@ubuntu:~$ grep -v "^#" /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
smills@ubuntu:~$ chmod 755 script.sh
smills@ubuntu:~$ sudo ./script.sh
[sudo] password for smills: 
--2012-07-20 14:11:48--  http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages.gz
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.92.151, 91.189.92.152, 91.189.92.153, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.151|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.152|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.153|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.154|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.155|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.176|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.177|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.179|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.180|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.181|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.182|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.183|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.184|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.192|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.193|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.23|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.24|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.25|:80... failed: Connection timed out.
Retrying.

--2012-07-20 14:31:49--  (try: 2)  http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages.gz
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.151|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.152|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.153|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.154|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.155|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.176|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.177|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.179|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.180|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.181|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.182|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.183|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.184|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.192|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.193|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.23|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.24|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.25|:80... failed: Connection timed out.
Retrying.

--2012-07-20 14:51:50--  (try: 3)  http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages.gz
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.151|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.152|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.153|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.154|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.155|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.176|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.177|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.179|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.180|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.181|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.182|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.183|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.184|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.192|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.193|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.23|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.24|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.25|:80... failed: Connection timed out.
Retrying.

--2012-07-20 15:11:52--  (try: 4)  http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages.gz
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.151|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.152|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.153|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.154|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.155|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.176|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.177|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.179|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.180|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.181|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.182|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.183|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.184|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.192|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.92.193|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.23|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.24|:80... failed: Connection timed out.
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.25|:80... failed: Connection timed out.
Retrying.

```

---

### Post by stum22 on 2012-07-20
> **Rsjc741 said:**
> You said you can access the internet?

try pinging the IP's listed in your posts.

To do this, do:

CRTL+ALT+T

ping XX.XXX.XXX (for instance, X's should be replaced with actual IP's)

You should either get a "All packets lost, or something opposite of that.

If your getting an XX% packets lost (not a full 100% or 0%), it could mean a problem with your connection.

If you get a "Connection refused", then maybe it's an issue with either their ports, the way youre connecting with the servers, or your ports.

I can ping say my home institution but if I ping ubuntu sites noting seems to happen. After waiting 10+minutes nothing happens in terminal for say 
91.189.92.184 
Sigh!

---

### Post by matt_symes on 2012-07-20
Hi

Blimey !!!

Connection problems again ? I thought we had that sorted out when you mentioned you had set up the proxy settings :confused: Post #29 shows connectivity.

> I can ping say my home institution but if I ping ubuntu sites  noting  seems to happen. After waiting 10+minutes nothing happens in  terminal  for say 
91.189.92.184 What do you mean by your home institution ? Can  you ping any external sites at the moment such as googles dns server.

```
ping -c2 8.8.4.4
```Is your company blocking all access to the  internet ? Can i be 100% sure; this computer with Ubuntu on it is being  used at your place of work ?

Can you tell me how you changed the proxy settings please. Have you spoken to your IT staff at work ?

This is a fresh install and you are having so many problems with your package system ? Can you provide a link to where you downloaded the iso from please.

Did you check the downdown iso for errors ? md5 or sha  checksum check ? There is not way on this planet you should be having so many problems with the package manager on a fresh install. Connectivity is a different issue though.

Can you run this command and post the output.

```
cd && wget http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages.gz 
```I suspect it will fail though.

Kind regards

---

### Post by stum22 on 2012-07-22
Looks like everything is solved for the moment!

Step 1. Delete ubuntu
Step 2. Reinstall via mounted CD
Step 3. Redo proxy settings
Step 4. Update as per posts.

No more errors!

Thanks especially Matt for helping! And making it possible for me to fix it when I tried to reinstall. How my last version was so broken I have no idea?

Cheers, Stu

---

