---
title: "a long list of errors"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by ozz1243 on 2013-04-14
hi all im trying to install ubuntu on my sisters kids laptop its not going well. im a noob on linux

The problem cannot be reported:

```
You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

apt-utils, at-spi2-core, gcc-4.7-base, gcr, libapt-inst1.5, libapt-pkg4.12, libatk-bridge2.0-0, libatspi2.0-0, libcups2, libgcc1, libgck-1-0, libgcr-3-1, libgcr-3-common, libglib2.0-0, libglib2.0-bin, libglib2.0-data, libgudev-1.0-0, libpython-stdlib, libpython2.7-minimal, libpython2.7-stdlib, libstdc++6, libudev1, python, python-gi, python-minimal, python-twisted-bin, python-twisted-core, python2.7, python2.7-minimal, tar
```

iv tryed updating python with
```
sudo apt-get update && sudo apt-get upgrade
``` 



```
Get:1 http://gb.archive.ubuntu.com raring Release.gpg [933 B]
Hit http://security.ubuntu.com raring-security Release.gpg                     
Hit http://gb.archive.ubuntu.com raring-updates Release.gpg
Hit http://security.ubuntu.com raring-security Release     
Hit http://gb.archive.ubuntu.com raring-backports Release.gpg
Get:2 http://gb.archive.ubuntu.com raring Release [40.8 kB]                    
Hit http://security.ubuntu.com raring-security/main Sources                    
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://security.ubuntu.com raring-security/restricted Sources
Hit http://extras.ubuntu.com raring Release                                    
Hit http://security.ubuntu.com raring-security/universe Sources                
Hit http://gb.archive.ubuntu.com raring-updates Release               
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://security.ubuntu.com raring-security/multiverse Sources     
Hit http://gb.archive.ubuntu.com raring-backports Release
Hit http://extras.ubuntu.com raring/main amd64 Packages                        
Get:3 http://gb.archive.ubuntu.com raring/main Sources [959 kB]       
Hit http://security.ubuntu.com raring-security/main amd64 Packages         
Hit http://extras.ubuntu.com raring/main i386 Packages                     
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages    
Hit http://security.ubuntu.com raring-security/universe amd64 Packages      
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages
Ign http://extras.ubuntu.com raring/main Translation-en                      
Hit http://security.ubuntu.com raring-security/main i386 Packages            
Hit http://security.ubuntu.com raring-security/restricted i386 Packages
Hit http://security.ubuntu.com raring-security/universe i386 Packages
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages
Hit http://security.ubuntu.com raring-security/main Translation-en
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://security.ubuntu.com raring-security/universe Translation-en
Get:4 http://gb.archive.ubuntu.com raring/restricted Sources [6863 B]
Get:5 http://gb.archive.ubuntu.com raring/universe Sources [5706 kB]
Get:6 http://gb.archive.ubuntu.com raring/multiverse Sources [167 kB]          
Get:7 http://gb.archive.ubuntu.com raring/main amd64 Packages [1172 kB]        
Get:8 http://gb.archive.ubuntu.com raring/restricted amd64 Packages [10.5 kB]  
Get:9 http://gb.archive.ubuntu.com raring/universe amd64 Packages [5445 kB]    
Get:10 http://gb.archive.ubuntu.com raring/multiverse amd64 Packages [129 kB]  
Get:11 http://gb.archive.ubuntu.com raring/main i386 Packages [1171 kB]        
Get:12 http://gb.archive.ubuntu.com raring/restricted i386 Packages [10.5 kB]  
Get:13 http://gb.archive.ubuntu.com raring/universe i386 Packages [5453 kB]    
Get:14 http://gb.archive.ubuntu.com raring/multiverse i386 Packages [131 kB]   
Hit http://gb.archive.ubuntu.com raring/main Translation-en                    
Hit http://gb.archive.ubuntu.com raring/multiverse Translation-en              
Hit http://gb.archive.ubuntu.com raring/restricted Translation-en              
Hit http://gb.archive.ubuntu.com raring/universe Translation-en                
Hit http://gb.archive.ubuntu.com raring-updates/main Sources                   
Hit http://gb.archive.ubuntu.com raring-updates/restricted Sources             
Hit http://gb.archive.ubuntu.com raring-updates/universe Sources               
Hit http://gb.archive.ubuntu.com raring-updates/multiverse Sources             
Hit http://gb.archive.ubuntu.com raring-updates/main amd64 Packages            
Hit http://gb.archive.ubuntu.com raring-updates/restricted amd64 Packages      
Hit http://gb.archive.ubuntu.com raring-updates/universe amd64 Packages        
Hit http://gb.archive.ubuntu.com raring-updates/multiverse amd64 Packages      
Hit http://gb.archive.ubuntu.com raring-updates/main i386 Packages             
Hit http://gb.archive.ubuntu.com raring-updates/restricted i386 Packages       
Hit http://gb.archive.ubuntu.com raring-updates/universe i386 Packages         
Hit http://gb.archive.ubuntu.com raring-updates/multiverse i386 Packages       
Hit http://gb.archive.ubuntu.com raring-updates/main Translation-en            
Hit http://gb.archive.ubuntu.com raring-updates/multiverse Translation-en      
Hit http://gb.archive.ubuntu.com raring-updates/restricted Translation-en      
Hit http://gb.archive.ubuntu.com raring-updates/universe Translation-en        
Hit http://gb.archive.ubuntu.com raring-backports/main Sources                 
Hit http://gb.archive.ubuntu.com raring-backports/restricted Sources           
Hit http://gb.archive.ubuntu.com raring-backports/universe Sources             
Hit http://gb.archive.ubuntu.com raring-backports/multiverse Sources           
Hit http://gb.archive.ubuntu.com raring-backports/main amd64 Packages          
Hit http://gb.archive.ubuntu.com raring-backports/restricted amd64 Packages    
Hit http://gb.archive.ubuntu.com raring-backports/universe amd64 Packages      
Hit http://gb.archive.ubuntu.com raring-backports/multiverse amd64 Packages    
Hit http://gb.archive.ubuntu.com raring-backports/main i386 Packages           
Hit http://gb.archive.ubuntu.com raring-backports/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com raring-backports/universe i386 Packages       
Hit http://gb.archive.ubuntu.com raring-backports/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com raring-backports/main Translation-en          
Hit http://gb.archive.ubuntu.com raring-backports/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com raring-backports/restricted Translation-en    
Hit http://gb.archive.ubuntu.com raring-backports/universe Translation-en      
Fetched 20.4 MB in 27s (755 kB/s)                                              
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: Problem opening /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_raring-updates_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
```  
 this i way beyond me now iv tryed reinstalling ubuntu i just get the same message. is there a way to format the harddrive and try to start fresh

iv tryed upgrading the packages with
```
sudo dpkg --configure -a sudo apt-get install -f
```

i get the package list could not be phrsed or opened

i cant open firefox  softwear center closes down. when i open the search your computer (ubuntu sign top left corner) theres nothing in there

is there a way of formating the hard drive and staring fresh

---

### Post by ibjsb4 on 2013-04-15
The package lists or status file could not be parsed or opened

[http://ubuntuforums.org/showthread.php?t=2131178&p=12583395&viewfull=1#post12583395](http://ubuntuforums.org/showthread.php?t=2131178&p=12583395&viewfull=1#post12583395)

---

### Post by deadflowr on 2013-04-15
You should try installing a stable version, and not one that's still in the development stages.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Even though raring is only weeks away from its release date, it is still in the process of maturing.

---

### Post by fantab on 2013-04-15
[INDENT]Run the following from the Terminal one by one:

```
$ sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update 
# cd
# exit

```

Then:

```
$ sudo apt-get update && sudo apt-get dist-upgrade
```
[/INDENT]

---

### Post by ozz1243 on 2013-04-15
> **deadflowr said:**
> You should try installing a stable version, and not one that's still in the development stages.  [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)  Even though raring is only weeks away from its release date, it is still in the process of maturing.  i think it could be the harddrive thats stuffed. i tryed 11.10 12.10, mint, kubuntu, puppy, xubunt. 13 is the only one i could get to load up

---

### Post by ozz1243 on 2013-04-15
when i put in   apt-get clean   i get   not using locking for for read only lock file /var/cache/apt/archives/lock

---

### Post by ozz1243 on 2013-04-15
thanks for the replys. im going to go and put 11.04 see i that one works. i couldn't even get it booting up before so ill try a new instal now to see if it works.

---

### Post by oldos2er on 2013-04-15
11.04 is no longer supported, you should install 12.04 (which will be supported for five years) or 12.10.

What are the machine's hardware specs?

---

### Post by ozz1243 on 2013-04-16
hi iv tryed 12.10 again theres a problem with kernal and this computer, i had lubuntu working a part from the wifi i fix that and lubuntu crashed and never came back on. im back on 13 now iv tryed updating and im getting the same problems

```
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock

```

---

### Post by ozz1243 on 2013-04-18
i kept getting The package lists or status file could not be parsed or opened. i did
```

sudo mkdir /var/lib/apt/lists/partial
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f


```

that got firefox working not a clue what it did. still cant get software center working, it opens  then closes and libreoffice writer wont open at all

---

