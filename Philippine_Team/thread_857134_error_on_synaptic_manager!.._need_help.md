---
title: "error on synaptic manager!.. need help"
date: 2008-07-12
forum: Philippine Team
---

### Post by killer_d76 on 2008-07-12
i was trying to install "skype".. although i was not able to install it.. i found  out that i have "skype" on synaptic package manager.. but when i opened synaptic package manager i got an "error" message

```
E: Type '--18:17:49--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```

patulong naman po mga bossing!.

---

### Post by loell on 2008-07-12
there's something wrong with your medibuntu repo


can you, 

```
cat /etc/apt/sources.list.d/medibuntu.list
  
```

---

### Post by rogier.de.groot on 2008-07-12
It's just saying the content of file /etc/apt/sources.list.d/medibuntu.list is wrong. Post the content of said file please.

---

### Post by jeffimperial on 2008-07-12
> **killer_d76 said:**
> i was trying to install "skype".. although i was not able to install it.. i found  out that i have "skype" on synaptic package manager.. but when i opened synaptic package manager i got an "error" message

```
E: Type '--18:17:49--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```

patulong naman po mga bossing!.
Paki-post naman ang contents ng iyong /etc/apt/sources.list.d/medibuntu.list file

---

### Post by killer_d76 on 2008-07-12
thanks for the quick reply guys.. 

```
--18:17:49--  http://www.medibuntu.org/sources.list.d/gutsy.list
           => `gutsy.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

    0K                                                       100%   23.42 MB/s

18:18:12 (23.42 MB/s) - `gutsy.list' saved [223/223]
```

ito po ba yun?.. and tanong ko lang po kung may conflict po yata ito since it says 'gutsy" eh ang gamit ko po eh hardy..

---

### Post by loell on 2008-07-12
heheh, i think you had just executed,

```
wget http://www.medibuntu.org/sources.list.d/gutsy.list

```

:D

---

### Post by loell on 2008-07-12
anyway, try replacing it with the hardy one

[http://www.medibuntu.org/sources.list.d/hardy.list]("http://www.medibuntu.org/sources.list.d/hardy.list")

it would seem, you are currently following a tutorial?

---

### Post by killer_d76 on 2008-07-12
mukhang ganun nga po ang nangyari :oops: is there fix for this issue?.. thanks po ulit.

---

### Post by jeffimperial on 2008-07-12
> **killer_d76 said:**
> mukhang ganun nga po ang nangyari :oops: is there fix for this issue?.. thanks po ulit.
Pwede mong gawin ang suggestion ni kuya loell ^

OR

Pwede mo naman pong i-post ang laman ng file na /etc/apt/sources.list.d/medibuntu.list

```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
``` Then copy and paste it as a reply on this thread :)

---

### Post by loell on 2008-07-12
well you can delete the sources.list in question

```
sudo rm /etc/apt/sources.list.d/medibuntu.list

```

then just do a quick update

```
sudo apt-get update
```

then that should fix it.

and..

if you  still want to have the medibuntu repo, the right one for hardy heron, your on hardy heron right?

download medibuntu hardy
```
wget http://www.medibuntu.org/sources.list.d/hardy.list
```

then copy it to **/etc/apt/sources.list.d/**

by 

```
sudo cp hardy.list /etc/apt/sources.list.d/medibuntu.list
```

then update

```
sudo apt-get update
```

there, then you can resume to the tutorial your using. :)

---

### Post by killer_d76 on 2008-07-12
```
--18:17:49--  http://www.medibuntu.org/sources.list.d/gutsy.list
           => `gutsy.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

    0K                                                       100%   23.42 MB/s

18:18:12 (23.42 MB/s) - `gutsy.list' saved [223/223]
```

eto po bossing..

i tried loells suggestion by replacing wget _[http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)_ with  

wget _[http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)_

but error still remains.. i've also restarted my computer.. :(

---

### Post by killer_d76 on 2008-07-12
when i try to open synaptic, here's the error i get.


```
E: Type '--18:17:49--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

---

### Post by jeffimperial on 2008-07-12
Pwede mo po gawin:

```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
```

Magbubukas siya ng Text Editor window na laman ang menu.list. I-paste mo ang contents na iyon bilang reply dito :D

---

### Post by killer_d76 on 2008-07-12
> **loell said:**
> well you can delete the sources.list in question

```
sudo rm /etc/apt/sources.list.d/medibuntu.list

```

then just do a quick update

```
sudo apt-get update
```

then that should fix it.

and..

if you  still want to have the medibuntu repo, the right one for hardy heron, your on hardy heron right?

download medibuntu hardy
```
wget http://www.medibuntu.org/sources.list.d/hardy.list
```

then copy it to **/etc/apt/sources.list.d/**

by 

```
sudo cp hardy.list /etc/apt/sources.list.d/medibuntu.list
```

then update

```
sudo apt-get update
```

there, then you can resume to the tutorial your using. :)



....ooopppsss am very sorry Loell, i did not see this post earlier.. am doing it right now and it is still updating!.. sorry bossing.

---

### Post by jeffimperial on 2008-07-12
Just curious, is [this the HowTo Install Skype tutorial]("http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/") you're following?

---

### Post by loell on 2008-07-12
> **killer_d76 said:**
> ....ooopppsss 

K, lang ;) 

no worries, kuya jeff will also assist you. :)

---

### Post by killer_d76 on 2008-07-12
whew it's working now.. thanks loell, rogier.de.groot and jeffimperial.. it's back to normal now.. by the way jeff.. i guess that's where my friend got the installation process.. but i would try to install skype using synaptic later.. thanks guys! :guitar:

---

### Post by jeffimperial on 2008-07-12
Nice to know you got it working. I think it's (Skype) also available from Applications > Add/Remove...
:D

---

### Post by dfmalh on 2008-07-13
I just spend an hour typing out my problem just for my browser to crash :-#

So I will try to explain my problem in short. 

_First some background_:
- this is a fresh install of Ubuntu, with all the updates and upgrades done.
- I am behind a firewall and need a proxy to use the internet (the proxy settings are correct and works, and I can even get to the medibuntu website to get the medibuntu.list file info)
- my general repositories are downloaded from my university's mirror (no proxy nesesary)

_Now my problem_:

I can't connect to the Medibuntu repositories...

Input terminal:
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Output terminal:
> --18:50:56--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... 


This creates the medibuntu.list file, but it is empty...

If I get the relevant info for this file form: [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)

and inserted it into the medibuntu.list file and run:

Input terminal:
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update


This is what I get:

Output terminal:
> Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy Release.gpg
Get:1 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/main Translation-en_ZA  
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/main Translation-en_ZA                           
Get:2 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/restricted Translation-en_ZA                   
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/restricted Translation-en_ZA                     
Get:3 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/universe Translation-en_ZA                     
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/universe Translation-en_ZA                       
Get:4 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/multiverse Translation-en_ZA                   
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/multiverse Translation-en_ZA                     
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates Release.gpg                              
Get:5 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/main Translation-en_ZA
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/main Translation-en_ZA                   
Get:6 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/restricted Translation-en_ZA           
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/restricted Translation-en_ZA             
Get:7 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/universe Translation-en_ZA             
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/universe Translation-en_ZA               
Get:8 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/multiverse Translation-en_ZA           
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/multiverse Translation-en_ZA             
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security Release.gpg                             
Get:9 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/main Translation-en_ZA
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/main Translation-en_ZA                  
Get:10 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/restricted Translation-en_ZA         
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/restricted Translation-en_ZA            
Get:11 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/universe Translation-en_ZA           
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/universe Translation-en_ZA              
Get:12 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/multiverse Translation-en_ZA         
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/multiverse Translation-en_ZA            
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed Release.gpg                             
Get:13 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/main Translation-en_ZA
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/main Translation-en_ZA                  
Get:14 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/restricted Translation-en_ZA         
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/restricted Translation-en_ZA            
Get:15 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/universe Translation-en_ZA           
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/universe Translation-en_ZA              
Get:16 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/multiverse Translation-en_ZA         
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/multiverse Translation-en_ZA            
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports Release.gpg                            
Get:17 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/main Translation-en_ZA
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/main Translation-en_ZA                 
Get:18 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/restricted Translation-en_ZA        
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/restricted Translation-en_ZA           
Get:19 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/universe Translation-en_ZA          
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/universe Translation-en_ZA             
Get:20 [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/multiverse Translation-en_ZA        
Ign [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/multiverse Translation-en_ZA           
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy Release                                          
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates Release            
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security Release                                
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed Release                                 
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports Release                                
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/main Packages                                   
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/restricted Packages                             
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/universe Packages                               
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy/multiverse Packages                             
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/main Packages                            
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/restricted Packages                      
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/universe Packages                       
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-updates/multiverse Packages                     
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/main Packages                           
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/restricted Packages                     
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/universe Packages                      
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-security/multiverse Packages                    
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/main Packages                           
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/restricted Packages                     
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/universe Packages                      
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-proposed/multiverse Packages                    
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/main Packages                         
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/restricted Packages
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/universe Packages
Hit [ftp://ftp.sun.ac.za](ftp://ftp.sun.ac.za) hardy-backports/multiverse Packages
92% [Connecting to packages.medibuntu.org (88.191.30.43)]


Not connecting...and no packages are updated...

In Software Sources, the Medibuntu entry is made, and "ticked" under "Third-party Software"

In Synaptic Package Manager the packages are also not listed...

Any help would be greatly appreciated.

---

### Post by dfmalh on 2008-07-13
Hi, and update to my problem... I could not connect to Medibuntu from home, where I am not behind a firewall.

---

### Post by dfmalh on 2008-07-13
Hi, good news! 

I could update and install packages from Medibuntu. I found another post after get as far as seeing this error message:

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? n


Then on another Ubuntu Thread (GPG error/medibuntu), some with similar problems.

By entering the following in a terminal after you added the Medibuntu repository, *the key is added*, and you can update and receive packages:

> sudo wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

I will see if I can do updates tomorrow from behind the firewall.

---

