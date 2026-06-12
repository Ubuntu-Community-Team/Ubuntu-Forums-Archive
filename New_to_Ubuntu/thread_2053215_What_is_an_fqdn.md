---
title: "What is an fqdn?"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by agszepp on 2012-09-04
I am completely new to Ubuntu. I would like to know what is an fqdn and how do I get one, because when I tried to install some updates, it said that an installation failed because it couldn't download some type of qmail package without an fqdn.

---

### Post by alphacrucis2 on 2012-09-04
It usual means fully qualified domain name

---

### Post by TheMTtakeover on 2012-09-05
[http://en.m.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.m.wikipedia.org/wiki/Fully_qualified_domain_name)

---

### Post by lisati on 2012-09-05
> **agszepp said:**
> I am completely new to Ubuntu. I would like to know what is an fqdn and how do I get one, because when I tried to install some updates, it said that an installation failed because it couldn't download some type of qmail package without an fqdn.

It sounds a bit like some setting has gone a bit wonky. Are you able to copy the error message into a reply or take a screen shot?

---

### Post by agszepp on 2012-09-05
Next time this happens I'll try to copy and paste the error message.

---

### Post by Bashing-om on 2012-09-05
The exact error message would be good. In the mean time...IRT "  when I tried to install some updates, it said that an installation failed " suggest that there may be an invalid entry in your source list.

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by agszepp on 2012-09-06
This is the error message that I got when I tried to install an update today:

  	 	 	 	 	 	   installArchives() failed: Selecting previously unselected package linux-image-3.2.0-30-generic-pae.  
 (Reading database ...  
 (Reading database ... 5%%  
 (Reading database ... 10%%  
 (Reading database ... 15%%  
 (Reading database ... 20%%  
 (Reading database ... 25%%  
 (Reading database ... 30%%  
 (Reading database ... 35%%  
 (Reading database ... 40%%  
 (Reading database ... 45%%  
 (Reading database ... 50%%  
 (Reading database ... 55%%  
 (Reading database ... 60%%  
 (Reading database ... 65%%  
 (Reading database ... 70%%  
 (Reading database ... 75%%  
 (Reading database ... 80%%  
 (Reading database ... 85%%  
 (Reading database ... 90%%  
 (Reading database ... 95%%  
 (Reading database ... 100%%  
 (Reading database ... 149403 files and directories currently installed.)  
 Unpacking linux-image-3.2.0-30-generic-pae (from .../linux-image-3.2.0-30-generic-pae_3.2.0-30.48_i386.deb) ...  
 Done.  
 Preparing to replace glib-networking-common 2.32.1-1ubuntu1 (using .../glib-networking-common_2.32.1-1ubuntu2_all.deb) ...  
 Unpacking replacement glib-networking-common ...  
 Preparing to replace glib-networking 2.32.1-1ubuntu1 (using .../glib-networking_2.32.1-1ubuntu2_i386.deb) ...  
 Unpacking replacement glib-networking ...  
 Preparing to replace glib-networking-services 2.32.1-1ubuntu1 (using .../glib-networking-services_2.32.1-1ubuntu2_i386.deb) ...  
 Unpacking replacement glib-networking-services ...  
 Preparing to replace linux-generic-pae 3.2.0.29.31 (using .../linux-generic-pae_3.2.0.30.32_i386.deb) ...  
 Unpacking replacement linux-generic-pae ...  
 Preparing to replace linux-image-generic-pae 3.2.0.29.31 (using .../linux-image-generic-pae_3.2.0.30.32_i386.deb) ...  
 Unpacking replacement linux-image-generic-pae ...  
 Selecting previously unselected package linux-headers-3.2.0-30.  
 Unpacking linux-headers-3.2.0-30 (from .../linux-headers-3.2.0-30_3.2.0-30.48_all.deb) ...  
 Selecting previously unselected package linux-headers-3.2.0-30-generic-pae.  
 Unpacking linux-headers-3.2.0-30-generic-pae (from .../linux-headers-3.2.0-30-generic-pae_3.2.0-30.48_i386.deb) ...  
 Preparing to replace linux-headers-generic-pae 3.2.0.29.31 (using .../linux-headers-generic-pae_3.2.0.30.32_i386.deb) ...  
 Unpacking replacement linux-headers-generic-pae ...  
 Preparing to replace linux-libc-dev 3.2.0-29.46 (using .../linux-libc-dev_3.2.0-30.48_i386.deb) ...  
 Unpacking replacement linux-libc-dev ...  
 Preparing to replace policykit-1-gnome 0.105-1ubuntu3 (using .../policykit-1-gnome_0.105-1ubuntu3.1_i386.deb) ...  
 Unpacking replacement policykit-1-gnome ...  
 Processing triggers for libglib2.0-0 ...  
 Setting up qmail (1.06-4) ...  
 

 The hostname -f command returned: $1  
 

 Your system needs to have a fully qualified domain name (fqdn) in  
 order to install the var-qmail packages.  
 

 Installation aborted.  
 

 dpkg: error processing qmail (--configure):  
  subprocess installed post-installation script returned error exit status 1  
 No apport report written because MaxReports is reached already  
 dpkg: dependency problems prevent configuration of qmail-run:  
  qmail-run depends on qmail (>= 1.06-2.1); however:  
   Package qmail is not configured yet.  
 dpkg: error processing qmail-run (--configure):  
  dependency problems - leaving unconfigured  
 No apport report written because MaxReports is reached already  
 Setting up linux-image-3.2.0-30-generic-pae (3.2.0-30.48) ...  
 Running depmod.  
 update-initramfs: deferring update (hook will be called later)  
 Examining /etc/kernel/postinst.d.  
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-30-generic-pae /boot/vmlinuz-3.2.0-30-generic-pae  
 update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic-pae  
 run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-30-generic-pae /boot/vmlinuz-3.2.0-30-generic-pae  
 run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-30-generic-pae /boot/vmlinuz-3.2.0-30-generic-pae  
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-30-generic-pae /boot/vmlinuz-3.2.0-30-generic-pae  
 Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae  
 Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae  
 Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae  
 Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae  
 Found memtest86+ image: /boot/memtest86+.bin  
 done  
 Setting up glib-networking-common (2.32.1-1ubuntu2) ...  
 Setting up glib-networking-services (2.32.1-1ubuntu2) ...  
 Setting up glib-networking (2.32.1-1ubuntu2) ...  
 Setting up linux-image-generic-pae (3.2.0.30.32) ...  
 Setting up linux-generic-pae (3.2.0.30.32) ...  
 Setting up linux-headers-3.2.0-30 (3.2.0-30.48) ...  
 Setting up linux-headers-3.2.0-30-generic-pae (3.2.0-30.48) ...  
 Setting up linux-headers-generic-pae (3.2.0.30.32) ...  
 Setting up linux-libc-dev (3.2.0-30.48) ...  
 Setting up policykit-1-gnome (0.105-1ubuntu3.1) ...  
 Errors were encountered while processing:  
  qmail  
  qmail-run  
 Error in function:  
 Setting up qmail (1.06-4) ...  
 

 The hostname -f command returned: $1  
 

 Your system needs to have a fully qualified domain name (fqdn) in  
 order to install the var-qmail packages.  
 

 Installation aborted.  
 

 dpkg: error processing qmail (--configure):  
  subprocess installed post-installation script returned error exit status 1  
 dpkg: dependency problems prevent configuration of qmail-run:  
  qmail-run depends on qmail (>= 1.06-2.1); however:  
   Package qmail is not configured yet.  
 dpkg: error processing qmail-run (--configure):  
  dependency problems - leaving unconfigured

---

### Post by Kopkins on 2012-09-06
Looks like it could be dependency issues. Try running ```
sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean 
sudo apt-get install -f

```

Kopkins

---

### Post by agszepp on 2012-09-07
I ran the code and this is what I got:

agoston@agoston-Inspiron-6000:~$ sudo apt-get update
[sudo] password for agoston: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release [49.6 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Sources                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex    
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Sources [159 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en       
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Sources [50.1 kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages [381 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                  
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages [127 kB]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 791 kB in 2s (277 kB/s)                  
Reading package lists... Done
agoston@agoston-Inspiron-6000:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del openjdk-6-jre 6b24-1.11.3-1ubuntu0.12.04.1 [231 kB]
Del icedtea-6-jre-jamvm 6b24-1.11.3-1ubuntu0.12.04.1 [530 kB]
Del icedtea-6-jre-cacao 6b24-1.11.3-1ubuntu0.12.04.1 [419 kB]
Del openjdk-6-jre-headless 6b24-1.11.3-1ubuntu0.12.04.1 [27.3 MB]
Del openjdk-6-jre-lib 6b24-1.11.3-1ubuntu0.12.04.1 [6,133 kB]
Del openjdk-6-jdk 6b24-1.11.3-1ubuntu0.12.04.1 [11.2 MB]
agoston@agoston-Inspiron-6000:~$ sudo apt-get clean
agoston@agoston-Inspiron-6000:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 qmail
 qmail-run
E: Sub-process /usr/bin/dpkg returned an error code (1)
agoston@agoston-Inspiron-6000:~$ ^C
agoston@agoston-Inspiron-6000:~$ ^C
agoston@agoston-Inspiron-6000:~$ 

I got an error message towards the end.

---

### Post by stmiller on 2012-09-07
You will want to edit the file /etc/hostname and give the computer a name. Then reboot!

---

### Post by agszepp on 2012-09-07
How would I edit the hostname?

---

### Post by SeijiSensei on 2012-09-07
First, what do you see if you run the command "hostname --fqdn"?  Either you'll see a single name like "cutebunny" or a "fully-qualified domain name" like "cutebunny.example.com".  Or you may see nothing at all.

If you want to set an fqdn, you need to put the name into the file /etc/hostname.  The simplest way to do this is to run the command:

```
sudo echo 'cutebunny.example.com' > /etc/hostname
```

Now all this presupposes that your computer is actually part of a domain.  If you are trying to install a mail server package like qmail, one would expect you already have a domain like "example.com" for which you intend to accept mail.  Is that what you are trying to do?  If you don't have a domain, why are you trying to install qmail?

---

### Post by agszepp on 2012-09-08
Thank-you. Now I know what an fqdn is for and how to get one.

---

