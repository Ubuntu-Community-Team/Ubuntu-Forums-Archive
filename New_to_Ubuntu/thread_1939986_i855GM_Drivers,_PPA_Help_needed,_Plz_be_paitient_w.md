---
title: "i855GM Drivers, PPA Help needed, Plz be paitient with me"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by bipolaric on 2012-03-12
Hello Again,  I hope you are not getting sick of me, but we all have to start somewhere right ?

I think I have found 2 drivers/files that might solve my problems....
One is called  (libdrm) and the other is called (xserver-xorg-video-intel).

the page url is: [https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=maverick](https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=maverick)

I typed $sudo add-apt-repository ppa:glasen/intel-driver

And I got this:

[sudo] password for bipolaric: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 60F8DC87DD22304528F5AB6F0F2D1009066ADE1D
gpg: requesting key 066ADE1D from hkp server keyserver.ubuntu.com
gpg: key 066ADE1D: public key "Launchpad PPA for Stefan Glasenhardt" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


What do I do next ? ...Please explain, as an idiot would understand, as this is all new to me........Thanks Again.....Mark****

---

### Post by alphacrucis2 on 2012-03-12
Now you have the ppa you need to do:


```
sudo apt-get update
```

That refreshes the package database inlcuding any packages available in the ppa.

Then 

```
sudo apt-get upgrade
```

That will install any packages from the ppa that are newer than what you have installed. If you want to install a package you don't already have:

```
sudo apt-get install <package name>
```

don't type the < > just whatever the package name you want to install

---

### Post by oldos2er on 2012-03-12
[S]Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=1939823](http://ubuntuforums.org/showthread.php?t=1939823)[/S]

Edit: Thread reopened, the two threads are not duplicates. Sorry bipolar!

---

### Post by bipolaric on 2012-03-13
Hi, 

I did everything you said, and everything was correct.  The only thing was the fact that the terminal said either files were too old or missing, so now I am back to square one :(  I don't know if PPA's can be broken, but I still have no graphics driver.  What would you suggest ?  Can I find another PPA, in order to get my i855GM working properly ?

By the way, everything I typed I copied and pasted into a document for future reference, but after this did not work, I tried installing something to do with xorg-edge 'something or other' and when I did that and rebooted I had no screen at all and only sound.  I had to re-install the whole Operating system in the early hours.  In fact 'Square One' is an understatement.  I am perplexed.

I wish someone could help.

Thank you for all your input - Regards - Mark

---

### Post by bipolaric on 2012-03-13
Here is the log:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

bipolaric@Laptop:~$ sudo add-apt-repository ppa:glasen/intel-driver
[sudo] password for bipolaric: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 60F8DC87DD22304528F5AB6F0F2D1009066ADE1D
gpg: requesting key 066ADE1D from hkp server keyserver.ubuntu.com
gpg: key 066ADE1D: public key "Launchpad PPA for Stefan Glasenhardt" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
bipolaric@Laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [39.8kB]            
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en  
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB 
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg [198B]       
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,754B]                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release [39.8kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [1,252B]                  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [104kB]        
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [2,713B]           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse i386 Packages
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources [177kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [33.0kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [1,755B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [326kB] 
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources [778B] 
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources [63.7kB]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources [2,513B]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main i386 Packages [461kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [112kB]
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe i386 Packages [200kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [4,026B]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [5,475B]
Fetched 1,589kB in 3s (472kB/s)                          
Reading package lists... Done
bipolaric@Laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gdm-guest-session libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2
  xserver-xorg-video-intel
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 314kB of archives.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main gdm-guest-session all 0.17ubuntu0.1 [7,864B]
Get:2 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main libdrm2 i386 2.4.25~glasen~maverick~ppa1 [22.0kB]
Get:3 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main libdrm-intel1 i386 2.4.25~glasen~maverick~ppa1 [23.1kB]
Get:4 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main libdrm-nouveau1 i386 2.4.25~glasen~maverick~ppa1 [13.1kB]
Get:5 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main libdrm-radeon1 i386 2.4.25~glasen~maverick~ppa1 [13.7kB]
Get:6 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main xserver-xorg-video-intel i386 2:2.15.0~maverick~ppa1 [234kB]
Fetched 314kB in 0s (341kB/s)                   
(Reading database ... 145072 files and directories currently installed.)
Preparing to replace gdm-guest-session 0.17 (using .../gdm-guest-session_0.17ubuntu0.1_all.deb) ...
Unpacking replacement gdm-guest-session ...
Preparing to replace libdrm2 2.4.21-1ubuntu2.1 (using .../libdrm2_2.4.25~glasen~maverick~ppa1_i386.deb) ...
Unpacking replacement libdrm2 ...
Preparing to replace libdrm-intel1 2.4.21-1ubuntu2.1 (using .../libdrm-intel1_2.4.25~glasen~maverick~ppa1_i386.deb) ...
Unpacking replacement libdrm-intel1 ...
Preparing to replace libdrm-nouveau1 2.4.21-1ubuntu2.1 (using .../libdrm-nouveau1_2.4.25~glasen~maverick~ppa1_i386.deb) ...
Unpacking replacement libdrm-nouveau1 ...
Preparing to replace libdrm-radeon1 2.4.21-1ubuntu2.1 (using .../libdrm-radeon1_2.4.25~glasen~maverick~ppa1_i386.deb) ...
Unpacking replacement libdrm-radeon1 ...
Preparing to replace xserver-xorg-video-intel 2:2.12.0-1ubuntu5.2 (using .../xserver-xorg-video-intel_2%3a2.15.0~maverick~ppa1_i386.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for man-db ...
Setting up gdm-guest-session (0.17ubuntu0.1) ...
Setting up libdrm2 (2.4.25~glasen~maverick~ppa1) ...
Setting up libdrm-intel1 (2.4.25~glasen~maverick~ppa1) ...
Setting up libdrm-nouveau1 (2.4.25~glasen~maverick~ppa1) ...
Setting up libdrm-radeon1 (2.4.25~glasen~maverick~ppa1) ...
Setting up xserver-xorg-video-intel (2:2.15.0~maverick~ppa1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
bipolaric@Laptop:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bipolaric@Laptop:~$ 

Still no desktop effects, any ideas ?

---

### Post by bipolaric on 2012-03-13
Anyone have a clue on how to get my intel855GM working ?
After everything I have read, I will have to make it stable too.

I'm open to any suggestions.

Thanks Again - Mark

---

