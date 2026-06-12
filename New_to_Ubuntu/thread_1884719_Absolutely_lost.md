---
title: "Absolutely lost"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by Waelkin on 2011-11-21
I just started using Ubuntu 11.10 (downloaded and installed using a LiveCD) on a Macbook Pro 8,2 and I am absolutely confused and frustrated with it. I downloaded a couple .mp3 files from Firefox but can't seem to get them to play in Banshee Media Player; it just does absolutely nothing when I double click or right-click>play an .mp3 in the Music folder.

Another problem is that I can't seem to understand how to install Gecko in Wine, or just how to properly use Wine. The tutorials by themselves are pretty confusing since I'm new to Linux and don't know the proper commands to input in Terminal.

I can update the regular graphics driver update but when I try to download and install the "post release updates" version it denies it an says that I can't download it saying "/var/log/jockey.log" and I have no idea what that means. After I "update/install" a graphics driver from "Additional Drivers" I have this "Unsupported hardware" watermark with the AMD/ATI logo on the top right of the watermark on the bottom-right of my screen.

I can't seem to get Steam to work properly, I "attempted" to use Wine and can get the program to run but it just disappears (I take it that it either crashes or auto-exits) by itself. League of Legends is also a problem as after I downloaded and installed the client it says that "There was an error launching the Application" - "Failed to change directory".

I also tried to follow the Ubuntu-wiki tutorial on how to find my networking adapter (Macbook Pro) but it got way to confusing way to fast and most of the commands I input don't work, so I'm stuck with just having to put up with ethernet cable only.


I want to get to used to Ubuntu, but the necessity to constantly use google search (which usually doesn't turn out the answers I need) and Terminal makes it difficult to understand.
Your help will undoubtedly be appreciated.

---

### Post by beew on 2011-11-21
To paly mp3 and other proprietary formats you need to install the proper libraries and codecs.

Install  the package ubuntu-restricted-extras and also activate the medibuntu ppa and install the package nonfree-codecs.

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)

You should be able to install things with WINE just by right clicking the .exe files (installers) like in Windows if you have installed WINE properly.

I have no idea about the "post install update" driver stuffs. In my case only that one would install, the "ordinary" one failed (nvidia)

Some of your problems may be specific to 11.10, it is quite buggy at the moment for me. things is, with previous versions of Ubuntu I can assume that most things would work without having to test all of them, but with 11.10 I can't make this assumption based on the few things that I did test.  Usually it takes a few months after release for them to sort out all the bugs.

---

### Post by Waelkin on 2011-11-21
I installed Wine through the Ubuntu Software Center and did nothing else. Was there something that I needed to do? I can't even get passed the first step of downloading a .gpg key when following the tutorial you linked. I have no idea how to do any of these things and the tutorials assume that I'm going to know or have already done these things before.

---

### Post by beew on 2011-11-21
The WINE people advise you to install from their ppa because the Ubuntu's version is outdated 

[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

The easy way to add ppas and manage software packages would be to use the synaptic package manager but they have removed it in 11.10, in order to showcase the "new" Ubuntu Software Center. The USC, in my view is bloated, slow and quite inferior, it only looks pretty.

To get synaptic, open a terminal and type 
```
sudo apt-get install synaptic
```Then open Synaptic, go to Settings > Repositories > Other Software and click "add' then add the ppa for WINE
> ppa:ubuntu-wine/ppa, then close the dialogue and click the "Reload" button, and then you should find that there are updates for WINE (go to the left panel, choose status, upgradable) then upgrade and that's it.

**EDITED** Bear in mind that many WIndows program don't work in WINE at all or only partially, so even if you install the proper WINE packages things may still not work. You should consult the WINEhq list and the WINE subforum here for specific software.

---

### Post by dFlyer on 2011-11-21
First welcome to linux. Now forget everything you know about windows and Mac. Now to get your mp3 files to run you need to install ubuntu-restricted-extra from the archives along with w32codecs from the [http://medibuntu.org/](http://medibuntu.org/) web site. This will get your music to play. As far as wine goes I can't help as I haven't used anything windows since the 90's. Just remember linux is not windows or mac, you just need to go slow and have fun. When problem arise just use this forum or google which should answer most of your questions.

---

