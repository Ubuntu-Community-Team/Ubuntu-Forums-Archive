---
title: "Software updater stuck in installing updates"
date: 2016-01-15
forum: New to Ubuntu
---

### Post by pianist4him2 on 2016-01-15
Dear ubuntu community,

Though, I'm new with linux - I find it more attractive day by day. It might be a simple question, but we all have been learners at some point in life.
I have 64 bits OS Ubuntu 14.04 LTS installed which used to work fine before. However, unintentionally, I've unplugged the power without proper shutting down the system while I had VMware another Linux OS based running. Since then, my Software updater gets stuck in installing updates and the wheel keeps spinning and spinning. I've tried to force a file system check at reboot, it doesn't seem to help/nor confirm it's done it and last night - my ubuntu simply became inaccessible - I left it over night - all CPU fans were working at full speed - it was not pingable the system - both mouse and keyboard stuck at authentication. I had to forcefully powercycle it again.

Where do you start troubleshooting this: is there a Event viewer equivalent in Linux - such as dmesg, how can I make sure my linux is 100% functional and in a complete full health status?
I prefer working in command/bash, so that I start learning as well.

Thank you for your time.
Kind regards, Pianist4Him.

---

### Post by grahammechanical on 2016-01-15
There are things that are not clear. How many operating systems on this  machine? Do you get a Grub boot menu? Can you load into Ubuntu? 

If you can load into Ubuntu run these commands & post the output in your thread enclosed in code tags

```
sudo apt-get update
sudo apt-get upgrade
```

Regards.

---

### Post by pianist4him2 on 2016-01-15
Thank you, grahammechanical. 
Yes, I can load into Ubuntu. It's a  machine with two hdd, I'm booting from the one where Linux is installed  (by changing the order into Bios).
What do you mean by: 'post the output in your thread enclosed in code tags'?

---

### Post by pianist4him2 on 2016-01-18
> **grahammechanical said:**
> There are things that are not clear. How many operating systems on this  machine? Do you get a Grub boot menu? Can you load into Ubuntu? 

If you can load into Ubuntu run these commands & post the output in your thread enclosed in code tags

```
sudo apt-get update
sudo apt-get upgrade
```

Regards.

update
```

Ign http://gb.archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                               
Get:1 http://gb.archive.ubuntu.com trusty-updates InRelease [64.4 kB]       
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://gb.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty/main i386 Packages                
Get:2 http://gb.archive.ubuntu.com trusty-updates/main Sources [248 kB]        
Get:3 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B] 
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Ign http://extras.ubuntu.com trusty/main Translation-en               
Get:4 http://gb.archive.ubuntu.com trusty-updates/universe Sources [147 kB]
Hit http://security.ubuntu.com trusty-security InRelease                     
Get:5 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [5,161 B]
Get:6 http://gb.archive.ubuntu.com trusty-updates/main amd64 Packages [683 kB] 
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe Sources           
Hit http://security.ubuntu.com trusty-security/multiverse Sources        
Hit http://security.ubuntu.com trusty-security/main amd64 Packages        
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages    
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages    
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages  
Get:7 http://gb.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Get:8 http://gb.archive.ubuntu.com trusty-updates/universe amd64 Packages [334 kB]
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en         
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:9 http://gb.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:10 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [659 kB]
Get:11 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:12 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [336 kB]
Get:13 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en   
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en     
Hit http://gb.archive.ubuntu.com trusty Release   
Hit http://gb.archive.ubuntu.com trusty/main Sources
Hit http://gb.archive.ubuntu.com trusty/restricted Sources
Hit http://gb.archive.ubuntu.com trusty/universe Sources
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources
Hit http://gb.archive.ubuntu.com trusty/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/main Translation-en
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en
Fetched 2,539 kB in 6s (363 kB/s)                                              
Reading package lists... Done 
```

upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-45-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-45-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade. 
```

---

### Post by sandyd on 2016-01-18
> **pianist4him2 said:**
> Thank you, grahammechanical. 
Yes, I can load into Ubuntu. It's a  machine with two hdd, I'm booting from the one where Linux is installed  (by changing the order into Bios).
What do you mean by: 'post the output in your thread enclosed in code tags'?

Hi,

Is the one you are currently booting from (and getting the info from) having issues, or is the one installed in vmware having issues.

---

### Post by maxinstuff2 on 2016-01-18
upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-45-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-45-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade. 
```[/QUOTE]

That's interesting. According to that you are all up to date.
Are you sure the updater is getting "stuck"?

You could try repairing broken packages with:
```
sudo apt-get -f install
```
And see if that sorts you out.

---

### Post by pianist4him2 on 2016-02-04
Thank you. It seems to be working fine now. I've noticed issue occurs  only when my admin/root password is not required - but it goes through  and starts downloading the updates packages but then gets stuck at  installing packages. I'm confident I haven't missed the auth. window -  it simply won't display/prompt me to.

---

