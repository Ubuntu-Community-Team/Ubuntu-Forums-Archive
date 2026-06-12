---
title: "Update manager problem"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by toxictex on 2012-11-23
Hi, I'm relatively new to ubuntu so please be gentle with me. My problem is updating, when I run the update manager I get an error message which says "failed to down load repository info. and to check my internet connection, which is fine. I have looked on the forums and tried one or two things. I went to download manager and tried the main server then I did a scan for the best mirror site but still got the same error. Next I launched the terminal and tried the ```
sudo apt-get update
``` command that someone recommended and this is the code that I got from that command
```
text@text-Dell-DE051:~$ sudo apt-get update
[sudo] password for text: 
Ign http://mirror.sov.uk.goscomb.net natty InRelease
Ign http://mirror.sov.uk.goscomb.net natty-updates InRelease
Ign http://mirror.sov.uk.goscomb.net natty-security InRelease
Ign http://mirror.sov.uk.goscomb.net natty-backports InRelease
Hit http://mirror.sov.uk.goscomb.net natty Release.gpg
Hit http://mirror.sov.uk.goscomb.net natty-updates Release.gpg
Hit http://mirror.sov.uk.goscomb.net natty-security Release.gpg
Hit http://mirror.sov.uk.goscomb.net natty-backports Release.gpg
Hit http://mirror.sov.uk.goscomb.net natty Release
Hit http://mirror.sov.uk.goscomb.net natty-updates Release
Hit http://mirror.sov.uk.goscomb.net natty-security Release                    
Hit http://mirror.sov.uk.goscomb.net natty-backports Release                   
Hit http://mirror.sov.uk.goscomb.net natty/main Sources                        
Hit http://mirror.sov.uk.goscomb.net natty/restricted Sources                  
Hit http://mirror.sov.uk.goscomb.net natty/universe Sources                    
Hit http://mirror.sov.uk.goscomb.net natty/multiverse Sources                  
Hit http://mirror.sov.uk.goscomb.net natty/main i386 Packages                  
Hit http://mirror.sov.uk.goscomb.net natty/restricted i386 Packages            
Hit http://mirror.sov.uk.goscomb.net natty/universe i386 Packages              
Hit http://mirror.sov.uk.goscomb.net natty/multiverse i386 Packages            
Ign http://mirror.sov.uk.goscomb.net natty/main TranslationIndex               
Ign http://mirror.sov.uk.goscomb.net natty/multiverse TranslationIndex         
Ign http://mirror.sov.uk.goscomb.net natty/restricted TranslationIndex         
Ign http://mirror.sov.uk.goscomb.net natty/universe TranslationIndex           
Hit http://mirror.sov.uk.goscomb.net natty-updates/main Sources                
Hit http://mirror.sov.uk.goscomb.net natty-updates/restricted Sources          
Hit http://mirror.sov.uk.goscomb.net natty-updates/universe Sources            
Hit http://mirror.sov.uk.goscomb.net natty-updates/multiverse Sources          
Hit http://mirror.sov.uk.goscomb.net natty-updates/main i386 Packages          
Hit http://mirror.sov.uk.goscomb.net natty-updates/restricted i386 Packages    
Hit http://mirror.sov.uk.goscomb.net natty-updates/universe i386 Packages      
Hit http://mirror.sov.uk.goscomb.net natty-updates/multiverse i386 Packages    
Ign http://mirror.sov.uk.goscomb.net natty-updates/main TranslationIndex       
Ign http://mirror.sov.uk.goscomb.net natty-updates/multiverse TranslationIndex 
Ign http://mirror.sov.uk.goscomb.net natty-updates/restricted TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty-updates/universe TranslationIndex
Hit http://mirror.sov.uk.goscomb.net natty-security/main Sources
Hit http://mirror.sov.uk.goscomb.net natty-security/restricted Sources
Hit http://mirror.sov.uk.goscomb.net natty-security/universe Sources
Hit http://mirror.sov.uk.goscomb.net natty-security/multiverse Sources
Hit http://mirror.sov.uk.goscomb.net natty-security/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net natty-security/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net natty-security/universe i386 Packages
Hit http://mirror.sov.uk.goscomb.net natty-security/multiverse i386 Packages
Ign http://mirror.sov.uk.goscomb.net natty-security/main TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty-security/multiverse TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty-security/restricted TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty-security/universe TranslationIndex
Hit http://mirror.sov.uk.goscomb.net natty/main Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net natty/multiverse Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net natty/restricted Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net natty/universe Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net natty-backports/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net natty-backports/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net natty-backports/multiverse i386 Packages
Hit http://mirror.sov.uk.goscomb.net natty-backports/universe i386 Packages
Ign http://mirror.sov.uk.goscomb.net natty-backports/main TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty-backports/multiverse TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty-backports/restricted TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty-backports/universe TranslationIndex
Ign http://mirror.sov.uk.goscomb.net natty/main Translation-en
Ign http://mirror.sov.uk.goscomb.net natty/multiverse Translation-en
Ign http://mirror.sov.uk.goscomb.net natty/restricted Translation-en
Ign http://mirror.sov.uk.goscomb.net natty/universe Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-updates/main Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-updates/main Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-updates/multiverse Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-updates/multiverse Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-updates/restricted Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-updates/restricted Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-updates/universe Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-updates/universe Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-security/main Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-security/main Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-security/multiverse Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-security/multiverse Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-security/restricted Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-security/restricted Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-security/universe Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-security/universe Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-backports/main Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-backports/main Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-backports/multiverse Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-backports/multiverse Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-backports/restricted Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-backports/restricted Translation-en
Ign http://mirror.sov.uk.goscomb.net natty-backports/universe Translation-en_GB
Ign http://mirror.sov.uk.goscomb.net natty-backports/universe Translation-en
Ign http://extras.ubuntu.com natty InRelease
Ign http://extras.ubuntu.com natty Release.gpg
Ign http://extras.ubuntu.com natty Release
Ign http://extras.ubuntu.com natty/main Sources/DiffIndex
Ign http://extras.ubuntu.com natty/main i386 Packages/DiffIndex
Ign http://extras.ubuntu.com natty/main TranslationIndex
Err http://extras.ubuntu.com natty/main Sources
  404  Not Found
Err http://extras.ubuntu.com natty/main i386 Packages
  404  Not Found
Ign http://extras.ubuntu.com natty/main Translation-en_GB
Ign http://extras.ubuntu.com natty/main Translation-en
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
text@text-Dell-DE051:~$ 
```I have no idea what this means or what to do next, please help

---

### Post by snowpine on 2012-11-23
The error is related to this announcement:

[http://fridge.ubuntu.com/2012/09/17/ubuntu-11-04-natty-narwhal-reaches-end-of-life-on-october-28-2012/](http://fridge.ubuntu.com/2012/09/17/ubuntu-11-04-natty-narwhal-reaches-end-of-life-on-october-28-2012/)

Recommend to back up all data to an external drive and do a fresh reinstall of a supported release. (12.04 long-term support might be a good choice for you.)

---

### Post by NikTh on 2012-11-23
Hi , 
As I can see from the results , you have Ubuntu 11.04 (natty) . Ubuntu 11.04 is EOL now. End Of Life . Not supported anymore , so its normal that you cannot update as the repositories either deleted of moved. 
It is time for upgrade :) to a newer supported release. 
Personally suggest a new fresh install of Ubuntu 12.04 LTS (supported until April 2017). 
See here about Ubuntu releases - EOL - etc :  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
You can grab 12.04 LTS from here: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
and then you have to burn the iso to a CD/DVD or USB . 
For USB you have to use a program like [Unetbootin](http://unetbootin.sourceforge.net/)

Do not forget to backup all your personal-important data , like Documents , Videos , Pictures ...etc to an external media (Usb-Flash , USB-HDD...) before you install the new Ubuntu release. 

Thanks

---

### Post by toxictex on 2012-11-23
Thank you for the prompt reply, I have already downloaded the distro you recommended but have put off installing it because I had a graphics problem when I upgraded from maverick meerkat to natty narwhal basically my integrated graphics card couldn't handle unity 3d but with help from Rubi 1200 on these forums I managed with difficulty to download Unity 2d and I have had no problems since. Is there anything I can do to avoid this happening again, when I upgrade

---

### Post by snowpine on 2012-11-23
Test-drive the Live CD/USB before you install the new version, is my recommendation. If it doesn't work on your hardware, then keep test-driving until you find a distro that works well. (For example the "lightweight" Xubuntu or Lubuntu)

Also never hurts to use the forum Search feature on your specific video card to see if others are having the same problem, and if so, how they solved it. :)

---

### Post by toxictex on 2012-11-23
Thank you, I will try what you have suggested.Sorry didn't realize Natty Narwhal was out of date, I thought it was supported for two years not eighteen months

---

### Post by toxictex on 2012-11-23
Thank you for your quick response. I will follow your advice.

---

### Post by newb85 on 2012-11-23
Non-LTS releases are all supported for eighteen months.  If you prefer to stick with a release for over a year, 12.04 (LTS) is probably your best option.

---

