---
title: "[SOLVED] wanna know if i am a 32 bits user or a 64 one."
date: 2008-11-09
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-11-09
hola!

im trying to change resolution for this reason :biggrin: :

[IMG]http://i36.tinypic.com/2hqautx.png[/IMG]

so im followin a thread GUI to set it right but it says i have to do sth if i am a 32 bits user and sth different if i am a 64 one.

so, my question is how to know it?

thanks!

---

### Post by mali2297 on 2008-11-09
In a terminal, type
```

uname -m

```
i386, i486 or i686 means 32bit. 
x86_64 means 64bit.

---

### Post by jsf_pp on 2008-11-09
> **mali2297 said:**
> In a terminal, type
```

uname -m

```
i386, i486 or i686 means 32bit. 
x86_64 means 64bit.

i686,
thanks mali!

---

### Post by AmbiguousOutlier on 2008-11-09
This app maybe useful to you.

Click System > Adminstration > Synaptic Package Manager.

Within the Synaptic Package Manager click the search button and type "gnome-device-manager"

Click the first entry and select “Mark for installation” Then click “Apply” on the toolbar.

---

### Post by jsf_pp on 2008-11-09
> **RhysGM said:**
> This app maybe useful to you.

Click System > Adminstration > Synaptic Package Manager.

Within the Synaptic Package Manager click the search button and type "gnome-device-manager"

Click the first entry and select “Mark for installation” Then click “Apply” on the toolbar.

ok, im doin it right now!

---

### Post by AmbiguousOutlier on 2008-11-09
Device manager will be found in Applications > System Tools

---

### Post by beercz on 2008-11-09
Thanks RhysGM

I didn't know about this utility.  I needed to find out my father's sound card on his ubuntu desktop over the phone, he could have done that using the gnome-device-manager rather than me telling him how to find out using the command line.

---

### Post by jsf_pp on 2008-11-09
[IMG]http://i36.tinypic.com/a1s5y8.png[/IMG]

nothin to select man!
am i that lost?

---

### Post by AmbiguousOutlier on 2008-11-09
click reload to make sure everything is upto date.

---

### Post by jsf_pp on 2008-11-09
> **RhysGM said:**
> click reload to make sure everything is upto date.

****! i pressed it and this happened!:

[IMG]http://i38.tinypic.com/aau7ex.png[/IMG]

and after that one, another one!:

[IMG]http://i36.tinypic.com/mrppp5.png[/IMG]

why?!?!?!
noooooooooooooo!
:lolflag:

---

### Post by AmbiguousOutlier on 2008-11-09
In the terminal try 

```

sudo apt-get update

```

EDIT:

just noticed you are on gutsy, and I have never used Gutsy, only Hardy. although from what I know it shouldn't matter.

---

### Post by jsf_pp on 2008-11-09
```
julio@julio-laptop:~$ sudo apt-get update
[sudo] password for julio:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-en_US                      
Ign http://dl.google.com stable/non-free Translation-en_US                     
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [189B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:3 http://packages.medibuntu.org hardy Release.gpg [189B]                   
Hit http://dl.google.com stable Release                                        
Err http://dl.google.com stable Release                                        
  
Get:4 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://ppa.launchpad.net gutsy Release                                     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Get:5 http://dl.google.com stable Release [1300B]                              
Ign http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net gutsy/main Packages                               
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://dl.google.com stable/non-free Packages                              
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Err http://ppa.launchpad.net gutsy/main Packages                               
  404 Not Found
Hit http://archive.ubuntu.com gutsy/main Sources                               
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://security.ubuntu.com gutsy-security/universe Sources 
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://packages.medibuntu.org hardy Release                                
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://packages.medibuntu.org hardy/non-free Packages      
Get:6 http://cl.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://cl.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://cl.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://cl.archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://cl.archive.ubuntu.com gutsy/universe Translation-en_US              
Get:7 http://cl.archive.ubuntu.com gutsy-updates Release.gpg [189B]            
Ign http://cl.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://cl.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Ign http://cl.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Ign http://cl.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Get:8 http://cl.archive.ubuntu.com gutsy-backports Release.gpg [189B]          
Ign http://cl.archive.ubuntu.com gutsy-backports/main Translation-en_US        
Ign http://cl.archive.ubuntu.com gutsy-backports/restricted Translation-en_US  
Ign http://cl.archive.ubuntu.com gutsy-backports/universe Translation-en_US    
Ign http://cl.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US  
Get:9 http://cl.archive.ubuntu.com gutsy-proposed Release.gpg [189B]           
Ign http://cl.archive.ubuntu.com gutsy-proposed/restricted Translation-en_US   
Ign http://cl.archive.ubuntu.com gutsy-proposed/main Translation-en_US         
Ign http://cl.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US   
Ign http://cl.archive.ubuntu.com gutsy-proposed/universe Translation-en_US     
Hit http://cl.archive.ubuntu.com gutsy Release                                 
Hit http://cl.archive.ubuntu.com gutsy-updates Release                         
Hit http://cl.archive.ubuntu.com gutsy-backports Release                       
Hit http://cl.archive.ubuntu.com gutsy-proposed Release                        
Hit http://cl.archive.ubuntu.com gutsy/main Packages                           
Hit http://cl.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://cl.archive.ubuntu.com gutsy/multiverse Packages                     
Hit http://cl.archive.ubuntu.com gutsy/restricted Sources                      
Hit http://cl.archive.ubuntu.com gutsy/main Sources                            
Hit http://cl.archive.ubuntu.com gutsy/multiverse Sources                      
Hit http://cl.archive.ubuntu.com gutsy/universe Sources                        
Hit http://cl.archive.ubuntu.com gutsy/universe Packages                       
Hit http://cl.archive.ubuntu.com gutsy-updates/main Packages                   
Hit http://cl.archive.ubuntu.com gutsy-updates/restricted Packages             
Hit http://cl.archive.ubuntu.com gutsy-updates/multiverse Packages             
Hit http://cl.archive.ubuntu.com gutsy-updates/restricted Sources              
Hit http://cl.archive.ubuntu.com gutsy-updates/main Sources                    
Hit http://cl.archive.ubuntu.com gutsy-updates/multiverse Sources              
Hit http://cl.archive.ubuntu.com gutsy-updates/universe Sources                
Hit http://cl.archive.ubuntu.com gutsy-updates/universe Packages               
Hit http://cl.archive.ubuntu.com gutsy-backports/main Packages                 
Hit http://cl.archive.ubuntu.com gutsy-backports/restricted Packages           
Hit http://cl.archive.ubuntu.com gutsy-backports/universe Packages             
Hit http://cl.archive.ubuntu.com gutsy-backports/multiverse Packages           
Hit http://cl.archive.ubuntu.com gutsy-backports/main Sources                  
Hit http://cl.archive.ubuntu.com gutsy-backports/restricted Sources            
Hit http://cl.archive.ubuntu.com gutsy-backports/universe Sources              
Hit http://cl.archive.ubuntu.com gutsy-backports/multiverse Sources            
Hit http://cl.archive.ubuntu.com gutsy-proposed/restricted Packages            
Hit http://cl.archive.ubuntu.com gutsy-proposed/main Packages                  
Hit http://cl.archive.ubuntu.com gutsy-proposed/multiverse Packages            
Hit http://cl.archive.ubuntu.com gutsy-proposed/universe Packages              
Hit http://cl.archive.ubuntu.com gutsy-proposed/restricted Sources             
Hit http://cl.archive.ubuntu.com gutsy-proposed/main Sources                   
Hit http://cl.archive.ubuntu.com gutsy-proposed/multiverse Sources             
Hit http://cl.archive.ubuntu.com gutsy-proposed/universe Sources               
Fetched 1496B in 13s (111B/s)                                                  
Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

it happened the same.
damn!
thanks for the help thou bro!

---

### Post by AmbiguousOutlier on 2008-11-09
I'm by no means an expert, so hopefully someone who knows what they are talking about will reply. But it appears to me as though you have something open that is stopping you updating your packages. Is everything else closed? 

My best answer is to install 8.04.

---

### Post by jsf_pp on 2008-11-09
let me see, im goin to close everything and try again.

and yes, i'll do change it as soon as i get my brand new 8.10 CD by the snail mail. :lolflag:

---

### Post by AmbiguousOutlier on 2008-11-09
you could try 

```

sudo aptitude update

```

this worked for me once when I was trying to install a utility when everything else failed.

---

### Post by jsf_pp on 2008-11-09
no, stil the same. damn!

ok, im postin a new thread, again thanks for your help mate!

---

### Post by Ptero-4 on 2008-11-09
For future reference. The 32bits that you saw in the zsnes window is color-depth (amount of unique colors your monitor/videocard can/are set to display), which aren't affected by your processor architecture (the 32 or 64bits you were asking about, which refers to the max supported instruction lenght).

---

### Post by ciscosurfer on 2008-11-11
> **RhysGM said:**
> This app maybe useful to you.

Click System > Adminstration > Synaptic Package Manager.

Within the Synaptic Package Manager click the search button and type "gnome-device-manager"

Click the first entry and select “Mark for installation” Then click “Apply” on the toolbar.A similar app that you might like is also in the repos and is called **hardinfo**.  There was another one also that I've used but can't think of it right now...it's another system profiler though.  hardinfo can do benchmarking and some other tests as well, but I think gnome-device-manager may just take the cake.  Thanks for the tip! gnome-device-manager looks like lspci -vv on sterioids...and formatted in a nice GUI.  Bravo!

---

