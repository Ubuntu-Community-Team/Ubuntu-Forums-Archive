---
title: "playing dvds?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by SarahMarieNC2 on 2008-09-24
How do you play dvd movies on ubuntu? I tried doing it with MPlayer but it asks me to download a codec? I did so and then it says that I don't have permission to use it? Is there something else that will play dvds better? I have a lightscribe dvd super multi drive/cd-writer.

---

### Post by Crafty Kisses on 2008-09-24
Try installing this package:
```
sudo apt-get install ubuntu-restricted-extras
```
Once you have that package installed, try running the DVD with VLC.

---

### Post by halitech on 2008-09-24
personally I use VLC but any program should play them although you may need to enable the w32codecs first and the ubuntu-restricted-extras

---

### Post by lisati on 2008-09-24
Have a look [here]("https://help.ubuntu.com/8.04/musicvideophotos/C/video.html")

---

### Post by SarahMarieNC2 on 2008-09-24
What's VLC? Thanks for the information everyone :)

---

### Post by Crafty Kisses on 2008-09-24
VLC is a cross-platform media player and streaming server
```
sudo apt-get install vlc
```

---

### Post by SarahMarieNC2 on 2008-09-24
> **Codename said:**
> VLC is a cross-platform media player and streaming server
```
sudo apt-get install vlc
```
Okay but is it complicated? I installed it but it obviously isn't "click and play" like my old player was. And about the -restricted extras- I copied the code and it downloaded them and at the end gave me a message saying that something used deforma font and I would need to configure it if I was using it in X Window. WHatever that means... I just assumed it didn't apply to me because Im not running in WIndows. But, I also don't see the restricted extras anywhere. Where would they appear? SOrry for all the questions, I'm only a few days old when it comes to Linux and Ubuntu.

---

### Post by Crafty Kisses on 2008-09-24
You can check to see if the package was installed correctly by doing the following, **System --> Administration --> Synaptic Package Manager** and look for the package _"ubuntu-restricted-extras"_. You can type that in the search bar and look for the package and see if it's installed.

---

### Post by SarahMarieNC2 on 2008-09-24
> **Codename said:**
> VLC is a cross-platform media player and streaming server
```
sudo apt-get install vlc
```
Okay but is it complicated? I installed it but it obviously isn't "click and play" like my old player was. And about the -restricted extras- I copied the code and it downloaded them and at the end gave me a message saying that something used msttcore font and I would need to configure it if I was using it in X Window. WHatever that means... I just assumed it didn't apply to me because Im not running in WIndows. But, I also don't see the restricted extras anywhere. Where would they appear? SOrry for all the questions, I'm only a few days old when it comes to Linux and Ubuntu.

-----------------------------

Edited to add: I think I figured it out. Apparently it didn't like me going through the sudo command line. I was able to install them through Application> Add/Remove Applications>  Other> Restricted Extras though. :) Hopefully this'll work for what I need it for now :) And it's configuring those msttcorefont things I mentioned about.

---

### Post by Crafty Kisses on 2008-09-24
Please post back and tell us if it worked or not. :)

---

### Post by SarahMarieNC2 on 2008-09-24
Okay they installed, but I still cant get any dvd to play. MPlayer says "Error occured, could not read from source." VLC I can't figure out how to try and play the DVD. And Kaffeine (not sure how that got on there) says that it is encrypted and that it may be illegal to use decryption files to run the dvd. Oh fun!

---

### Post by Crafty Kisses on 2008-09-24
For VLC you can go to **File --> Open Disc**.

---

### Post by mike1234 on 2008-09-24
Try this.

Open your terminal and type in: sudo apt-get install ubuntu-restricted-extras 

And install file below this for playing encrypted DVD's. Encrypted DVD's will not play regardless of media player installed. VLC is a good choice. kaffeine isn't necessary.  (open with gdebi)

M.

---

### Post by SarahMarieNC2 on 2008-09-24
> For VLC you can go to File --> Open Disc.
__________________

Okay I did that and the dvd (My Girl) is spinning in the try but nothing is playing on the screen. I think I need an idiots guide to linux lol

---

### Post by mike1234 on 2008-09-24
Are you using VLC? Or Kaffeine? If the above steps have been taken, then you need to look at media player setup preferences. Totem is about the simplest player to use, and Ubuntu uses it as a default player. Try that. Open synaptic and search for it. Select box and install.

M.

---

### Post by eddietours on 2008-09-24
keep trying with VLC

---

### Post by angelsguitar on 2008-09-24
Hi!

Here's a more detailed guide on configuring Ubuntu to play most multimedia formats, including DVDs.  There's a section that explains how to enable DVD playback with VLC or Totem.  I'll recommend VLC though.

Here's the link:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Although it's a little bit long, I'll recommend that you follow it from start to finish (at least until the dvd burning part); it will save you form future trouble with other multimedia formats, including Microsoft's ;)

Hope this solves your problems once and for all

---

### Post by Bakon Jarser on 2008-09-24
Here's your complete guide to multimedia in Ubuntu.  

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Therion on 2008-09-24
Have you installed **libdvdcss** yet?  It's in Synaptic.

---

### Post by SarahMarieNC2 on 2008-09-25
> **angelsguitar said:**
> Hi!

Here's a more detailed guide on configuring Ubuntu to play most multimedia formats, including DVDs.  There's a section that explains how to enable DVD playback with VLC or Totem.  I'll recommend VLC though.

Here's the link:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Although it's a little bit long, I'll recommend that you follow it from start to finish (at least until the dvd burning part); it will save you form future trouble with other multimedia formats, including Microsoft's ;)

Hope this solves your problems once and for all

I tried this, it still won't play. It brings up VLC automatically when the dvd is inserted but it doesn't appear to be doing anything other than spinning the disc.

---

### Post by billgoldberg on 2008-09-25
Just run this command in a terminal.

I haven't come across a dvd I couldn't play.
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by johnsimmons on 2008-09-25
Nice post about the DVD's and briefly explained that how to play games in DVD's...I like very much these type of forums...I want to know more about playing games in DVD's...
==============================================================================
simmons
[MLS]("http://mls.fastrealestate.net")

---

### Post by SarahMarieNC2 on 2008-09-25
> **billgoldberg said:**
> Just run this command in a terminal.

I haven't come across a dvd I couldn't play.
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

This is the output from that, error at the bottom couple lines.

> sarah@sarah:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
[sudo] password for sarah: 
--14:14:18--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

14:14:18 (23.95 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

OK
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy-security Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy-security/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [55.3kB]         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy-security Release                       
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]                      
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6465B]    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy-security/multiverse Packages           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [13.6kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [5713B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [31.4kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [7926B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy-security/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy-security/multiverse Packages
  404 Not Found
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy-security/multiverse Sources
  404 Not Found
Fetched 190kB in 44s (4218B/s)                           
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy-security/multiverse/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/hardy-security/multiverse/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy-security/multiverse/source/Sources.gz](http://packages.medibuntu.org/dists/hardy-security/multiverse/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
sarah@sarah:~$ 



 EDITED TO ADD: Had a little icon that said I needed to install updates and then got an error similar to the one in this post. I think something got messed up somewhere. Ugh. Im too new to know where or how to fix it. Yuck!

---

