---
title: "Get D-Link WUA-1340 USB Wireless Networking Adapter Working"
date: 2007-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by stillstanding on 2007-07-22
This concerns installing D-link wua-1340 wireless G adapter. It's my attempt at a tutorial so that other people won't run into problems that I did because it took me over 24 hours of messing around and yet it was all so easy and should only take a few minutes if all goes problem free. You shouldn't have to search any further because I tried to do all the work and put it here. 
 
    I am a beginner with Ubuntu. I'm long time Windows user and have pretty much no experience with anything else. I have the book Beginning Ubuntu Linux SE by Keir Thomas. With that I got Ubuntu 6.1 Edgy. I know its not the latest and I plan to upgrade after I finish this book and have a bit of knowledge under my belt. This book has been pretty helpful and a good read so far.
 
    Anyways I installed Ubuntu and found I needed network support but can only access network through wireless. I have the wua-1340 wireless G adapter that already works fine with Windows. I read some posts on this forum about running card installer through wine in order to get drivers into Ubuntu. Getting wine on my computer was a bit of a problem since I didn't have Internet access with this comp. Let me say that wine is only one option. There are a ways to go about getting things to work. I do not know of any way around using ndiswrapper but it seems to work for myself and others.
 
You can install drivers in windows and find files, copy them to cd or usb drive, rewritable media etc. Then in Ubuntu copy files from rewritable media to hard disk that runs Ubuntu. If you are dual booting Windows w/Ubuntu you can also mount your windows disk to make it available to Ubuntu. If necessary copy files to Ubuntu disk. I don't know if it is necessary) . If you do not have disk the d-link installer can be found @ [http://www.dlink.com]("http://www.dlink.com/products/support.asp?pid=477&sec=0#drivers").
 
You can install Wine @ [winehq.org]("http:///winehq.org/site/download-deb") This would have do be done on a computer with Internet access. I got source to compile from but I don't know how to compile from source yet and I ran into problems, so I took easier route of downloading package installer. Run card installer in wine. Find the driver files, copy to /home (if necessary). Files are now available for ndiswrapper. 
 
 
    1. Install ndiswrapper on your system. [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/) [http://ndiswrapper.sourceforge.net/joomla](http://ndiswrapper.sourceforge.net/joomla) I used ndiswrapper 1.8 with no problems. I also installed ndiswrapper using 'synaptic package manager'
 
    2. Before going on with ndiswrapper you will need to blacklist the current driver that linux is using. This will probably be 'rt73usb'. 
 
    3. Some people are reporting the location of there d-link driver files as being in 'Program Files-- D Link &#8211; drivers. However mine were not. This folder contained Config.dat, DeviceInst.exe, Dr71WU.cat, Dr71WU.sys, Dr71WU98.sys, LogFile.ini, rt73bin. Not the Dr71WU.inf file that I needed to use with ndiswrapper. Windows stores most of device drivers in 'Windows &#8211; System32' folder I believe So you might need to run a file search in system32. I found my 'Dr71WU.inf' in 'Windows&#8212;system32--inf' folder. All these should be copied to new folder in /home
    -If you used wine you must first go to /home/.wine/ (wine is a hidden folder so you must view hidden content) in Nautilus.
 
    -install Dr71wu.inf with ndiswrapper. When you type in command prompt, everything is case sensitive so you must make sure that you type exact. I did this all in terminal, so I was able to open 'file-- properties' in Nautilus and copy file name, paste it in terminal so that it was correct.
 
    -run command 'sudo ndiswrapper -l'. You should see &#8220;driver installed, hardware present.&#8221; if it worked.
 
    Go to configure network devices and enter info for your network under your card. Mine was was simply wireless connection. Previously it was listed as wlan0 or something like that. This might be case if you have two wireless cards in your computer. I do not know why anyone would need this though. All worked well for me after this. I never used wine even though I installed it and I was curious how this works and I now understand.
 
Some more detailed posts you might want to read over. These go into more detail about how each process is carried out. 
 
-[Trying to get D-Link Wireless 1340 to work]("http://ubuntuforums.org/showthread.php?t=270756&highlight=wua-1340")
(also includes info on blacklisting)
 
-[Trying to get D-Link WUA 1340 to work]("http://ubuntuforums.org/showpost.php?p=159661&postcount=1")
 
-[USB WiFi - D-Link WUA-1340 - SOL maybe?]("http://ubuntuforums.org/showthread.php?t=146278")
 
-[[SOLVED] Installing ndiswrapper manually via packages]("http://ubuntuforums.org/showthread.php?t=498739&highlight=installing+ndiswrapper")
 
I read all of these in addition to the previously mentioned book. However I don't want to be redundant or commit any copy write infringement. I largely had to figure this out on my own and feel I should share because no one should have to go through what I went through. Any questions or need more specific detail just message me. I will not post anything too explicit here.
 
If anything is wrong, or anyone needs to add anything feel free.

---

### Post by nutz on 2008-03-04
Has this adapter been tested with 64 bit Ubuntu?

---

### Post by nutz on 2008-03-06
Anyone?

---

### Post by natravis on 2009-01-23
> **stillstanding said:**
> This concerns installing D-link wua-1340 wireless G adapter. It's my attempt at a tutorial so that other people won't run into problems that I did because it took me over 24 hours of messing around and yet it was all so easy and should only take a few minutes if all goes problem free. You shouldn't have to search any further because I tried to do all the work and put it here. 
 
    I am a beginner with Ubuntu. I'm long time Windows user and have pretty much no experience with anything else. I have the book Beginning Ubuntu Linux SE by Keir Thomas. With that I got Ubuntu 6.1 Edgy. I know its not the latest and I plan to upgrade after I finish this book and have a bit of knowledge under my belt. This book has been pretty helpful and a good read so far.
 
    Anyways I installed Ubuntu and found I needed network support but can only access network through wireless. I have the wua-1340 wireless G adapter that already works fine with Windows. I read some posts on this forum about running card installer through wine in order to get drivers into Ubuntu. Getting wine on my computer was a bit of a problem since I didn't have Internet access with this comp. Let me say that wine is only one option. There are a ways to go about getting things to work. I do not know of any way around using ndiswrapper but it seems to work for myself and others.
 
You can install drivers in windows and find files, copy them to cd or usb drive, rewritable media etc. Then in Ubuntu copy files from rewritable media to hard disk that runs Ubuntu. If you are dual booting Windows w/Ubuntu you can also mount your windows disk to make it available to Ubuntu. If necessary copy files to Ubuntu disk. I don't know if it is necessary) . If you do not have disk the d-link installer can be found @ [http://www.dlink.com]("http://www.dlink.com/products/support.asp?pid=477&sec=0#drivers").
 
You can install Wine @ [winehq.org]("http:///winehq.org/site/download-deb") This would have do be done on a computer with Internet access. I got source to compile from but I don't know how to compile from source yet and I ran into problems, so I took easier route of downloading package installer. Run card installer in wine. Find the driver files, copy to /home (if necessary). Files are now available for ndiswrapper. 
 
 
    1. Install ndiswrapper on your system. [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/) [http://ndiswrapper.sourceforge.net/joomla](http://ndiswrapper.sourceforge.net/joomla) I used ndiswrapper 1.8 with no problems. I also installed ndiswrapper using 'synaptic package manager'
 
    2. Before going on with ndiswrapper you will need to blacklist the current driver that linux is using. This will probably be 'rt73usb'. 
 
    3. Some people are reporting the location of there d-link driver files as being in 'Program Files-- D Link – drivers. However mine were not. This folder contained Config.dat, DeviceInst.exe, Dr71WU.cat, Dr71WU.sys, Dr71WU98.sys, LogFile.ini, rt73bin. Not the Dr71WU.inf file that I needed to use with ndiswrapper. Windows stores most of device drivers in 'Windows – System32' folder I believe So you might need to run a file search in system32. I found my 'Dr71WU.inf' in 'Windows—system32--inf' folder. All these should be copied to new folder in /home
    -If you used wine you must first go to /home/.wine/ (wine is a hidden folder so you must view hidden content) in Nautilus.
 
    -install Dr71wu.inf with ndiswrapper. When you type in command prompt, everything is case sensitive so you must make sure that you type exact. I did this all in terminal, so I was able to open 'file-- properties' in Nautilus and copy file name, paste it in terminal so that it was correct.
 
    -run command 'sudo ndiswrapper -l'. You should see “driver installed, hardware present.” if it worked.
 
    Go to configure network devices and enter info for your network under your card. Mine was was simply wireless connection. Previously it was listed as wlan0 or something like that. This might be case if you have two wireless cards in your computer. I do not know why anyone would need this though. All worked well for me after this. I never used wine even though I installed it and I was curious how this works and I now understand.
 
Some more detailed posts you might want to read over. These go into more detail about how each process is carried out. 
 
-[Trying to get D-Link Wireless 1340 to work]("http://ubuntuforums.org/showthread.php?t=270756&highlight=wua-1340")
(also includes info on blacklisting)
 
-[Trying to get D-Link WUA 1340 to work]("http://ubuntuforums.org/showpost.php?p=159661&postcount=1")
 
-[USB WiFi - D-Link WUA-1340 - SOL maybe?]("http://ubuntuforums.org/showthread.php?t=146278")
 
-[[SOLVED] Installing ndiswrapper manually via packages]("http://ubuntuforums.org/showthread.php?t=498739&highlight=installing+ndiswrapper")
 
I read all of these in addition to the previously mentioned book. However I don't want to be redundant or commit any copy write infringement. I largely had to figure this out on my own and feel I should share because no one should have to go through what I went through. Any questions or need more specific detail just message me. I will not post anything too explicit here.
 
If anything is wrong, or anyone needs to add anything feel free.

Thanks for the post. Good tutorial got me going!

---

### Post by cariboo on 2009-01-24
I've used the wua-1340 on both 32bit and 64bit, all I did was plug it in and it worked, no extra configuration needed. Intrepid desktop and server as well as Jaunty are the versions I'm using. I have it currently hooked ot an Intel atom powered system running Intrepid 32bit, but I plan to upgrade to Jaunty 64bit as soon as it is available, if the Intel video drivers get fixed by then.

Jim

---

