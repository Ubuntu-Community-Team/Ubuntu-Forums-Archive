---
title: "Help With connecting to internet"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by Joshua Parsons on 2012-06-29
Please Listen read this article to get the story / my idea.

Story: I have been jumping Operating systems trying to get internet vista didn't work, went to xp worked but, I lagged, got ubuntu 12.04 and, worked well but, My wireless adapter is for windows platforms so was not supported I googled WINE but, everything I found to get it required internet. So I went back to Vista. Now I lag on the internet. I want ubuntu but, not if I can't get the internet on it. 

My Idea: I have a 16Gig Flashdrive - more like 10Gig now but - and vista on my main hard drive so I was wondering If I install ubuntu 12.04 on my flashdrive and goto vista download Wine from it then switch over to Ubuntu and try running it off a different os could that work? Or is there a way I can get Wine on Ubuntu with no internet connection. exception for laptop / desktop (Vista).

---

### Post by Joshua Parsons on 2012-06-29
Sorry double post

---

### Post by mapes12 on 2012-06-29
I don't think Wine is intended for wifi adapters. If your wifi adapter is not supported by Ubu then your only hope is to use an application called [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by Joshua Parsons on 2012-06-29
Still neeed help I am trying NdisWrapper
 
*Keep in mind I am doing this from a windows based laptop so im putting them on a fd then transfering over
 
Step 2.2 Installing Packages (With Internet access on another computer)
 
**2.2.1. Currently Supported Releases**

[LIST=1]
[*]For 12.04 Precise Pangolin [LIST=1]
[*][http://packages.ubuntu.com/precise/misc/ndiswrapper-common](http://packages.ubuntu.com/precise/misc/ndiswrapper-common) 
[*][http://packages.ubuntu.com/precise/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/precise/misc/ndiswrapper-utils-1.9) 
[*][http://packages.ubuntu.com/precise/net/ndisgtk](http://packages.ubuntu.com/precise/net/ndisgtk) 
[/LIST]
[/LIST]I select a and it takes mt to the site 
 
it says Download Ndiswrapper-Content
 
-----------------------------------------------------------------
|Architucture| Package Size| Installed Size| Files          |
------------------------------------------------------------------
_|All_              | 5.8Kb           | 71.0KB         | [List of Files]
-------------------------------------------------------------------
 
I selcted All and now I don't understand what to do... It hsa a section for north america and europe and above it says
 
> You can download the requested file from the pool/main/n/ndiswrapper/ subdirectory at any of these sites:

---

### Post by steeldriver on 2012-06-29
OK let's back up here - what wireless adapter do you have exactly? you can find out with

```
lsusb

lspci -nnv | grep -e "\[0200\]" -e "\[0280\]"
```

depending whether it is a USB or PCI device

---

### Post by Joshua Parsons on 2012-06-29
Netgear wna3100(v1) Wireless-N 300 [broadcom BCM43231]
 
I figured out the previious part I put the .deb files into directory /Documents
 
How do I do type this out properly
> 
Sudo dpkg -i /Documents/ndiswrapper-common_1.57-1ubuntu_all.deb


---

### Post by Joshua Parsons on 2012-06-29
I think I figured out how to install the .deb files but i don't think it worked not sure. if so please tell me so i can continue to the next step.
 
Here is a photo of the output. [http://www.flickr.com/photos/81514544@N07/7467287600/in/photostream](http://www.flickr.com/photos/81514544@N07/7467287600/in/photostream)

---

### Post by Joshua Parsons on 2012-06-29
What went wrong? Or how can I fix.
 
> 
[EMAIL="joshua@joshua-c6535:~$"]joshua@joshua-c6535:~$[/EMAIL] sudo dpkg -i cd Documents/libwine-alsa-unstable_1.5.5-0.1_i386.deb
dpkg: error processing cd (--install):
     cannot access archive: No such file or directory
(Reading database ... 140555 files and directories currently installed.)
Preparing to replace linewine-alsa-unstable 1.5.5-0.1 (using .../libwine-alsa-unstable_1.5.5-0.1_i386.deb)...
Unpacking replacement libwine-alsa-unstable ...
dpkg: dependency problems prevent configuration of libwine-alsa-unstable:
     libwine-alsa-unstable depends on libwine-unstable (= 1.5.5-0.1); however:
          Package libwine-unstable is not installed.
dpkg: error processing libwine-alsa-unstable (--install):
     dependency problems - leaving unconfigured
Errors were encountered while processing:
     cd
     libwine-alsa-unstable
[EMAIL="joshua@joshua-c6535:~$"]joshua@joshua-c6535:~$[/EMAIL] 


---

