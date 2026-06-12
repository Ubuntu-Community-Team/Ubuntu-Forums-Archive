---
title: "Beta 2"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MARP1961 on 2011-09-22
Does anyone know at what time today Oneiric Ocelot Beta 2 is available for download?

---

### Post by tekstr1der on 2011-09-22
Yes, I do.

---

### Post by MARP1961 on 2011-09-22
Don't tease the impatient! Would you please tell us.

---

### Post by lachild on 2011-09-22
From my experience if all is going well with the build it's usually available late in the afternoon (central time).  If they're having issues, it comes in the early or late evening, depending on how it's going.

For the really impatient, keep an eye on the forums.  Some distribution methods are available before others and there is always someone on here that finds a d/l before it's officially announced.  ;)

---

### Post by jerrrys on 2011-09-22
14 hours ago

[https://launchpad.net/ubuntu/+milestone/ubuntu-11.10-beta-2](https://launchpad.net/ubuntu/+milestone/ubuntu-11.10-beta-2)

---

### Post by MARP1961 on 2011-09-22
Many thanks for the information. I suppose this means wait until tomorrow (23rd September) here in the UK.

---

### Post by tobluntoo on 2011-09-22
will this require or benefit from a fresh install or can one just update via the manager?

---

### Post by MARP1961 on 2011-09-22
You shouldn't need a fresh install. Just try:```
sudo apt-get update
```
then
```
sudo apt-get upgrade
``` or ```
sudo apt-get dist-upgrade
```

---

### Post by philinux on 2011-09-22
> **tobluntoo said:**
> will this require or benefit from a fresh install or can one just update via the manager?

It's just a milestone snapshot. Just keep updated.

---

### Post by tobluntoo on 2011-09-22
Many thanks.

---

### Post by jbicha on 2011-09-22
The official release announcements are posted to [this list]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/").

---

### Post by lachild on 2011-09-22
It's out..

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview ]("http://https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview")


Update:

Correction...  Only the page has been updated...  Most links are still broken.   Sorry for jumping the gun.

---

### Post by Lars Noodén on 2011-09-22
Where is the torrent for beta2 ?

---

### Post by jerrrys on 2011-09-22
not finding a torrent for beta2, only beta1

---

### Post by ventrical on 2011-09-22
> **MARP1961 said:**
> You shouldn't need a fresh install. Just try:```
sudo apt-get update
```then
```
sudo apt-get upgrade
``` or ```
sudo apt-get dist-upgrade
```


  I tried this and got the following:

```
dale@ubuntu:~$ sudo apt-get update
[sudo] password for dale: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                   
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [39.8 kB]                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_CA                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_CA             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en_CA         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages [4,461 kB]      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages [7,992 B]     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_CA                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en [3,920 kB]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_CA             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_CA             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_CA               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en_CA           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en          
Fetched 9,773 kB in 42s (230 kB/s)                                             
Reading package lists... Done
dale@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  binutils gir1.2-pango-1.0 libgnomekbd-common libgnomekbd7 libpango1.0-0
  libyelp0 yelp
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,025 kB of archives.
After this operation, 20.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libpango1.0-0 i386 1.29.3+git20110916-0ubuntu1 [367 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main binutils i386 2.21.53.20110810-0ubuntu3 [2,387 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main gir1.2-pango-1.0 i386 1.29.3+git20110916-0ubuntu1 [22.7 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libgnomekbd-common all 3.1.92-0ubuntu1 [8,240 B]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libgnomekbd7 i386 3.1.92-0ubuntu1 [57.3 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libyelp0 i386 3.1.4-0ubuntu1 [127 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main yelp i386 3.1.4-0ubuntu1 [55.7 kB]
Fetched 3,025 kB in 12s (249 kB/s)                                             
(Reading database ... 150181 files and directories currently installed.)
Preparing to replace libpango1.0-0 1.29.3-0ubuntu3 (using .../libpango1.0-0_1.29.3+git20110916-0ubuntu1_i386.deb) ...
Unpacking replacement libpango1.0-0 ...
Preparing to replace binutils 2.21.53.20110810-0ubuntu2 (using .../binutils_2.21.53.20110810-0ubuntu3_i386.deb) ...
Unpacking replacement binutils ...
Preparing to replace gir1.2-pango-1.0 1.29.3-0ubuntu3 (using .../gir1.2-pango-1.0_1.29.3+git20110916-0ubuntu1_i386.deb) ...
Unpacking replacement gir1.2-pango-1.0 ...
Preparing to replace libgnomekbd-common 3.1.90-1 (using .../libgnomekbd-common_3.1.92-0ubuntu1_all.deb) ...
Unpacking replacement libgnomekbd-common ...
Preparing to replace libgnomekbd7 3.1.90-1 (using .../libgnomekbd7_3.1.92-0ubuntu1_i386.deb) ...
Unpacking replacement libgnomekbd7 ...
Preparing to replace libyelp0 3.1.3-0ubuntu1 (using .../libyelp0_3.1.4-0ubuntu1_i386.deb) ...
Unpacking replacement libyelp0 ...
Preparing to replace yelp 3.1.3-0ubuntu1 (using .../yelp_3.1.4-0ubuntu1_i386.deb) ...
Unpacking replacement yelp ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Setting up libpango1.0-0 (1.29.3+git20110916-0ubuntu1) ...
Setting up binutils (2.21.53.20110810-0ubuntu3) ...
Setting up gir1.2-pango-1.0 (1.29.3+git20110916-0ubuntu1) ...
Setting up libgnomekbd-common (3.1.92-0ubuntu1) ...
Setting up libgnomekbd7 (3.1.92-0ubuntu1) ...
Setting up libyelp0 (3.1.4-0ubuntu1) ...
Setting up yelp (3.1.4-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dale@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dale@ubuntu:~$
```

---

### Post by ventrical on 2011-09-22
Then on a whim I opened Update Manager and there were 35 updates waiting for me there // mostly gtk and python bindings ?/!

---

### Post by jerrrys on 2011-09-22
change server?  software sources

---

### Post by ventrical on 2011-09-22
It's all working really good after distro upgrades!

---

### Post by ventrical on 2011-09-22
> **jerrrys said:**
> change server?  software sources


Ok..now what !!??

---

### Post by oldos2er on 2011-09-22
I would wait a little while; the repositories and/or your particular mirror might not be fully updated yet.

---

### Post by ventrical on 2011-09-22
Ahhhh..oy  vey .. there it is !

:)

---

### Post by joopie on 2011-09-22
is their a download available yet? nm =) i see it!

---

