---
title: "problem with system running slow"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by ccdavis77 on 2016-05-26
Hello--
Having a problem with my system running slow and not sure what the problem is or how to fix it.  My media center platform has become very slow, but now even "sudo-apt get update", which used to be a very fast operation, takes a long time (see output below, this one took over 4 minutes).  I attached the output to see if this may help.  I can access data on this hard drive that is running Linux so I'm wondering if there is instead a problem with the microprocessor, etc.? How do I troubleshoot this?  Thanks for any help!!!
```

davismc@davismc:~$ sudo apt-get update
Ign [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty InRelease
Get:1 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates InRelease [65.9 kB]         
Hit [http://repo.steampowered.com]("http://repo.steampowered.com/") precise InRelease                             
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports InRelease                   
Get:2 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security InRelease [65.9 kB]        
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty InRelease                                  
Hit [http://repo.steampowered.com]("http://repo.steampowered.com/") precise/steam Sources                         
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty Release.gpg                           
Get:3 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/main Sources [275 kB]       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty InRelease                                  
Hit [http://repo.steampowered.com]("http://repo.steampowered.com/") precise/steam amd64 Packages                  
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty InRelease                                  
Hit [http://repo.steampowered.com]("http://repo.steampowered.com/") precise/steam i386 Packages                   
Get:4 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/restricted Sources [5,352 B]
Get:5 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/universe Sources [156 kB]   
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty InRelease                                  
Get:6 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/multiverse Sources [5,939 B]
Get:7 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/main amd64 Packages [768 kB]
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty Release.gpg                                
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main amd64 Packages                        
Get:8 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/restricted amd64 Packages [15.9 kB]
Get:9 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/universe amd64 Packages [360 kB]
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main i386 Packages                         
Get:10 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:11 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/main i386 Packages [736 kB]
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en                        
Get:12 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/restricted i386 Packages [15.6 kB]
Get:13 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/universe i386 Packages [361 kB]
Get:14 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/multiverse i386 Packages [13.6 kB]
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main amd64 Packages                        
Get:15 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/main Translation-en [384 kB]
Ign [https://private-ppa.launchpad.net]("https://private-ppa.launchpad.net/") trusty InRelease                         
Get:16 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/multiverse Translation-en [7,227 B]
Get:17 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/restricted Translation-en [3,699 B]
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main i386 Packages                         
Get:18 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-updates/universe Translation-en [189 kB]
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/main Sources                
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en                        
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/restricted Sources          
Hit [https://private-ppa.launchpad.net]("https://private-ppa.launchpad.net/") trusty Release.gpg                       
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/universe Sources            
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/multiverse Sources          
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main amd64 Packages                        
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/main amd64 Packages         
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/restricted amd64 Packages   
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main i386 Packages                         
Hit [https://private-ppa.launchpad.net]("https://private-ppa.launchpad.net/") trusty Release                           
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/universe amd64 Packages     
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/multiverse amd64 Packages   
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en                        
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/main i386 Packages          
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/restricted i386 Packages    
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/universe i386 Packages      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty Release                                    
Hit [https://private-ppa.launchpad.net]("https://private-ppa.launchpad.net/") trusty/main amd64 Packages               
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/multiverse i386 Packages    
Ign [http://repo.steampowered.com]("http://repo.steampowered.com/") precise/steam Translation-en_US               
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/main Translation-en         
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main amd64 Packages                        
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/multiverse Translation-en   
Ign [http://repo.steampowered.com]("http://repo.steampowered.com/") precise/steam Translation-en                  
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/restricted Translation-en   
Hit [https://private-ppa.launchpad.net]("https://private-ppa.launchpad.net/") trusty/main i386 Packages                
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main i386 Packages                         
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-backports/universe Translation-en     
Get:19 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/main Sources [115 kB]     
Get:20 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/restricted Sources [4,035 B]
Get:21 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/universe Sources [36.9 kB]
Get:22 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/multiverse Sources [2,760 B]
Get:23 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/main amd64 Packages [480 kB]
Get:24 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/restricted amd64 Packages [13.0 kB]
Get:25 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/universe amd64 Packages [129 kB]
Get:26 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/multiverse amd64 Packages [4,978 B]
Get:27 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/main i386 Packages [454 kB]
Get:28 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/restricted i386 Packages [12.7 kB]
Get:29 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/universe i386 Packages [129 kB]
Get:30 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/multiverse i386 Packages [5,168 B]
Get:31 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/main Translation-en [264 kB]
Get:32 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/multiverse Translation-en [2,570 B]
Get:33 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/restricted Translation-en [3,206 B]
Get:34 [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty-security/universe Translation-en [76.0 kB]
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty Release                               
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/main Sources                          
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en_US                     
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/restricted Sources                    
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/universe Sources                      
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en                        
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/multiverse Sources                    
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/main amd64 Packages                   
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/restricted amd64 Packages             
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/universe amd64 Packages               
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/multiverse amd64 Packages             
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/main i386 Packages                    
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/restricted i386 Packages              
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/universe i386 Packages                
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/multiverse i386 Packages              
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/main Translation-en                   
Ign [https://private-ppa.launchpad.net]("https://private-ppa.launchpad.net/") trusty/main Translation-en_US            
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/multiverse Translation-en             
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/restricted Translation-en             
Hit [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/universe Translation-en               
Ign [https://private-ppa.launchpad.net]("https://private-ppa.launchpad.net/") trusty/main Translation-en               
Ign [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/main Translation-en_US                
Ign [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/multiverse Translation-en_US          
Ign [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/restricted Translation-en_US          
Ign [http://archive.linux.duke.edu]("http://archive.linux.duke.edu/") trusty/universe Translation-en_US            
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy InRelease                                   
Get:35 [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy Release.gpg [72 B]                       
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy Release                                     
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy/main Sources                                
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy/main amd64 Packages                         
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy/main i386 Packages                          
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy/main Translation-en_US                      
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") saucy/main Translation-en                         
Hit [http://archive.canonical.com]("http://archive.canonical.com/") saucy InRelease                               
Hit [http://archive.canonical.com]("http://archive.canonical.com/") saucy/partner Sources             
Hit [http://archive.canonical.com]("http://archive.canonical.com/") saucy/partner amd64 Packages
Hit [http://archive.canonical.com]("http://archive.canonical.com/") saucy/partner i386 Packages                   
Ign [http://archive.canonical.com]("http://archive.canonical.com/") saucy/partner Translation-en_US               
Ign [http://archive.canonical.com]("http://archive.canonical.com/") saucy/partner Translation-en                  
Fetched 5,174 kB in 4min 2s (21.3 kB/s)                                        
Reading package lists... Done
davismc@davismc:~$
```
**EDIT**
...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by RobGoss on 2016-05-26
Hello and welcome to the forum, first off we don't know what version of Ubuntu you're running

Second, you will need to provide us with the** specs** so we can try to figure out what's oing on with your machine

---

### Post by ccdavis77 on 2016-05-26
Hi, sorry.  I am running Trusty 14.04.3.  Which specs do you need?  The HTPC has an Intel i3-3225 dual core processor, ASRock DDr3 intel motherboard.  I run linux system and my media center interface on a WD green 2TB hard drive for now but I will soon be moving my media to a NAS.

---

### Post by grahammechanical on 2016-05-26
The speed of the apt-get update operation might not be related the general sense that stuff is running slow. 

You are using 14.04 which has the code name of "trusty". So, all the Ubuntu repositories with "trusty" as part of the URL are fine. But you also have some Ubuntu repositories with the code name of "saucy" and that is 13.10 and it has been out of life since July 17th 2014. Why do you have them in your sources list file?

Then there are the Steam repositories with the code name of "precise." That is 12.04 and it is still supported until April next year. But does Steam still support their own "precise" repositories?

There are also PPAs. Which are fine for installing software but not always useful for updating the software that can from the PPA.

 But why do you have all those repositories? Accessing repositories takes time and if the OS has to make repeated attempts before getting access or giving up trying, it all causes the operation to take longer than we think it should. 

As regards the statement that the system is running slow, in what way is it running slow? Is it data transfers on and off of the hard disks? Is it the user interface where the drop down menus are slow to appear. Or is it the movement of application windows?

System Settings>Details will tell you what video driver is being used. If it says llvmpipe then it is a fall back open source video driver that is being used because of some video driver conflict. Even on powerful video adapters llvmpipe can seem slow.

Regards.

---

### Post by ccdavis77 on 2016-05-26
Thanks for responding. I'm not sure why I have all of those repositories...should I get rid of them and how? RE slowness: ...Internet connection remains fast and local media access also seems fine. When accessing apps within my media center, however, I usually get a never ending spinning progress wheel when previously everything ran quickly and smoothly, much like the extended time it takes to complete "sudo-apt get update"...earlier, within the Ubuntu desktop I browsed the Internet quickly and ran YouTube videos without a problem as well.

---

### Post by pfeiffep on 2016-05-26
> **ccdavis77 said:**
> .should I get rid of them and how? 
Got to system settings > software and updates > Authentication
Remove the saucy references and the ppa's you don't need or use

---

### Post by mörgæs on 2016-05-26
You have a processor of the Ivy Bridge family. Though 14.04 works performance has improved in the later releases: 
[https://openbenchmarking.org/result/1412288-LI-IVYBRIDGE10](https://openbenchmarking.org/result/1412288-LI-IVYBRIDGE10)

I would give it a fresh install of 16.04.

---

### Post by ccdavis77 on 2016-05-27
Thanks so much for the help! Probably another dumb question but I can get rid of amd64 packages as well since I have an Intel processor, no? I will try the above suggestions a little later today and let you know...

---

### Post by him610 on 2016-05-27
> but I can get rid of amd64 packages as well since I have an Intel processor, no? 

No. You don't want to do that.  
Refer to this link to explain difference between amd64 and i386 versions of Ubuntu....
[http://askubuntu.com/questions/54296/difference-between-the-i386-download-and-the-amd64]("http://askubuntu.com/questions/54296/difference-between-the-i386-download-and-the-amd64")

Even though it references Ubuntu 11.04, it still applies to Ubuntu 16.04.

---

### Post by ccdavis77 on 2016-05-27
Ok, got rid of all the saucy repos (I think). I'm in the process of trying to upgrade to 16.04 but running the software updater as part of that process is just taking FOREVER now when it used to just zip along. Just seems like there is a bigger problem than just the OS all of a sudden...

---

### Post by mörgæs on 2016-05-27
An upgrade in itself can cause a big problem. My suggestion was a fresh install.

---

### Post by ccdavis77 on 2016-05-28
Okay, guess I have to wipe the drive to do that right? Only asking bc all my media (music, movies, photos, etc.) are on the drive as well (for now).

---

### Post by ccdavis77 on 2016-05-28
Well, I went ahead with the upgrade before I read your last post and now I have a new problem--the screen flickers every 2 seconds...having trouble figuring out what to do about THAT now...

---

### Post by mörgæs on 2016-05-29
If you do a live boot you can get access to your personal files for backing up.
After that install 16.04.

---

