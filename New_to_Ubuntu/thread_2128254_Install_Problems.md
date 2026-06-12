---
title: "Install Problems"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by Timoteo32 on 2013-03-22
I have a Dell laptop I've had for a few years and I've upgraded my version of Ubuntu along the way. (Currently 12.04) But the new system doesn't work with my network card. In talking to a few friends they suggested I just go back tot he original OS I have a disk for. (8.10) I actually like that better so I tried but I got a weird error message when installing. It's like the 4th step but it says something like "No partition selected for root file". MY hard drive isn't partitioned at all so I'm not sure what that's about. It says to fix it in the Partition Menu but all of the buttons on that screen are grayed out and there's nothing I can click on.  Ideas?

I don't care if I have to wipe the harddrive and I don't want it partitioned.

---

### Post by fantab on 2013-03-22
8.10 is dead. It is no longer supported as it reached it end of life in 2010. I am afraid, but you were ill adviced. If you don't like the looks of Ubuntu then try Xubuntu or Lubuntu or Kubuntu. But only install and use OS that is supported with regular updates. 

Your problem is with your network card... if you could share more info about that and the problem you are having, perhaps we can help you.

---

### Post by Timoteo32 on 2013-04-14
Hmmmm, that is bad nbews. I didn't tell them the exact version so they might not have realized how old the boot disk I have it.

My problems have now multiplied though :(
1) My network card just won't work. I  read on other threads that there's a problem between this version of ubuntu and the drivers for some Dell network cards. I tried to follow the steps given to the person who posted the same problem but they didn't work for me. It does work fine if I'm connected with an ethernet cable though.

2) I was also recently getting error messages saying about not being able to install all packets and I clicked "Partial Upgrade" but then I got a message saying "Software Index Broken" and that nothing could be installed or removed and I should run the "Synaptec" package manger or it gave me a command line to run in terminal but that didn't seem to fix the problem. I opened Synaptec but I have no clue what packages I want to add/remove/edit/etc

I've actually enjoyed having Ubuntu on my laptop despite some initial frustrations but I'm beginning to wonder if just installing Windows 7 might be the easiest solution.

---

### Post by Timoteo32 on 2013-04-14
I went into Synaptec and since I dodn't know what I'm doing, I just checked "Mark all Upgrades".  I then got a message saying not all packages could be installed and asking if I wanted to continue, ignoring these packages. I said yes, hoping that maybe the changes to the others might fix something.  It started and then I got a pop up saying:> E: pdvdlinux: subprocess installed post-removal script returned error exit status 127

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_6.5ubuntu6.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_6.5ubuntu6.4_i386.deb)
  404  Not Found [IP: 91.189.91.13 80]

Then another pop up saying not all changes complete (or any I assume). Then it just exited.

---

### Post by monkeybrain2012 on 2013-04-14
Because your version is so old all the repositories are dead and so are the repos for the intermediate versions (9.04, 9.10) so upgrade is no go. Download a new iso and make a live  usb or CD to do a clean install.

---

### Post by Timoteo32 on 2013-04-15
No, the version I wanted to install is old. The version I'm currently running is 12.04. Although I'm not against a fresh install if that's what makes the most sense. Just might need to figure out how to do that without a CD.

---

### Post by fantab on 2013-04-15
Did you do a Fresh install, in the first place or did you just ran upgrade from the old version? If you have a fresh install then post the output of:
```
sudo apt-get update
```

If you haven't done a Fresh install then it is strongly recommended that you do.
In your case, you can [install with USB drive]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by deadflowr on 2013-04-15
> **Timoteo32 said:**
> No, the version I wanted to install is old. The version I'm currently running is 12.04. Although I'm not against a fresh install if that's what makes the most sense. Just might need to figure out how to do that without a CD.

You can do that by adding the iso to grub.
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

But that's an utter pita.

What we really should be trying to figure out though is what is wrong with the network card.

---

### Post by Timoteo32 on 2013-04-15
Sorry for the late resonse, I had to go to work last night.

I've just been upgrading as versions get released from when I installed 8.10 four years ago.  I'm actually fine doing a fresh install because I don't use this laptop for that many things and I already backed it up, but I'm curious what recommendations you guys would have on WHAT to install.  I really don't like this version. Most of them are UI complaints and I'm curious about those other variants fantab posted earlier.

My complaints with this version include:
1) Obviously the network card thing that created the initial problem although it's possible that's been patched
2) I don't like that I can't use my browser in a "windowed" state. Trying to switch between windows is REALLY unwieldy and not everything will run in a tab so I think it's a very poor design to force us into :-x
3) This version takes forever to boot up by comparison of older versions
4) I HATE the icon bar down the side and would prefer my old dropdown menus along the top

If it wasn't obvious from this post I come from a Windows background and HATE the shift towards a Mac interface. :P

---

### Post by Timoteo32 on 2013-04-15
Oh, and I think he said just post it in case I did a fresh install but in case this is still relevant here's my output from that entry:
> Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1347 B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1226 B]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex  
Get:7 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7078 B]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [377 kB]       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:9 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5853 B]      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5467 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [83.4 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [6562 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [610 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [196 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [267 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [7834 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en [2432 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [114 kB]
Fetched 1771 kB in 3s (445 kB/s)                                 
Reading package lists... Done

---

### Post by fantab on 2013-04-16
Your Output is fine.

Please **do a fresh Ubuntu 12.04 install**, if you haven't already. Perhaps the network problem you are having will be sorted out after "Fresh Install".

If you don't like Ubuntu_UNITY then you can try either install "Gnome-Classic desktop" or you can install "Cinnamon desktop" to run along side Unity. You pick the new desktop from login screen. More on this later.

Or

Try **Xubuntu 12.04** or **Lubuntu 12.04** both have desktop similar to older ubuntu desktop.

If you can tell us what 'Network Card' your computer has then perhaps we can narrow down to the problem you are having with it.

Post the Output of the following (please use the codes to do so; use # icon in the editor):

```
lspci -nn
```

```
sudo lshw -c network
```

---

### Post by Timoteo32 on 2013-04-16
Thank you so much fantab. You've been great :)  Here's my output. I have class and work tomorrow but I'll tackle the fresh install Wednesday

> 00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

 > *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:3f:97:2b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)

---

### Post by fantab on 2013-04-16
Your Network Card from the above outputs is:

[QUOTE=Timoteo32]0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
++
*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation[/QUOTE]

The follwing will help you understand what is going on and can help get your Network going:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)
[http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices)
[http://askubuntu.com/questions/80402/broadcom-bcm4312-not-working](http://askubuntu.com/questions/80402/broadcom-bcm4312-not-working)

The [info here]("http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312") is old but should give you ideas on how to go about it, just in case.

Broadcom drivers have, over the years, been well-supported by Open-Source. So a fresh install should take care of it.

I hope it helps.

---

### Post by Timoteo32 on 2013-04-17
So I think after doing some reading I'm going to try out Xubuntu. I  would hardly say I consider myself completely familiar with them all but I  like that it sounds like a faster and leaner OS since I don't do a ton  on this machine. And sounds like I can still run all the same  applications I can with Ubunutu? I just might have to download some  things that come standard as part of Ubuntu?

The torrent is dowloading now so I haven't done anything drastic if I'm making a mistake :P

---

### Post by fantab on 2013-04-17
Since the release of 12.04 there have been two UPGRADES to it. **12.04.1** and **12.04.2** and there is a difference between 'em. **12.04.2** comes with "[Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")", (HES) which supports wider and newer Hardware. However, there have been some issues with 12.04.2 with older hardware. So, 12.04.1 does not have HES (if you install 12.04.1 and then upgrade it to 12.04.2 you will not get HES ). And I suggest that you download both versions. 12.04.1 can be downloaded from [HERE]("http://www.ubuntu.com/download/desktop/alternative-downloads"). I forgot to mention this earlier. 

Ubuntu 13.04 beta final can be obtained from [here]("http://cdimage.ubuntu.com/daily-live/current/"). It is due for release shortly.

---

### Post by Timoteo32 on 2013-04-18
I actually downloaded Xubuntu 12.10. IT seems like 12.04 might have been the way to go but I wasn't watching close and I had already downloaded it but is there any reason not to try it?

I tried to install it but it looked like it froze up in the middle. I'm headed to bed so I didn't want to get engrossed in working on it any more tonight.

---

### Post by fantab on 2013-04-18
Personally, I consider 12.10 to be a forgetable version. My experience with it has not been good, to say the least. I replace it with 13.04 (development version) as soon as I could, and I must tell I have been very impressed until now with 13.04's development. We suggest 12.04 because it LTS, supported until 2017. That is all.

---

### Post by Timoteo32 on 2013-04-18
Okay, well I guess I'll see what the state of affairs is next time I log in. When I told the installer to quit, it actually loaded Xubuntu but I'm not sure if it was installed or just the "Try it" screen. It was incredibly slow which was disappointing because I read it's supposed to be faster. If it wasn't installed I'll go see if I can find a 12.04.2 distribution.

---

### Post by Mopar1973Man on 2013-04-18
If its a old laptop you might try Lubuntu or installing Ubuntu then add LXDE desktop to it.

---

### Post by Timoteo32 on 2013-04-21
So I may have fallen out of the frying pan into the fryer :(

I downloaded the Xubuntu 12.10 and created my boot drive on a USB. For some reason the installer was freezing but I took the opportunity to create a 12.04 drive as advised. That installer looked like it was working great and I thought I was in the home stretch. Right up until an erro box popped up saying "**Erno 5 Input/Output error**"  Then gave me some advice like clean the disk, burn the disc at a slower speed or if it's a hard drive move it to a cooler area or it may need replaced". I'm going to google the error but I'm unclear: Is it my flash drive that's bad or my harddrive? Since it was talking about CDs I assume it meant the source but now I'm a little worried I have a problem with my hard drive cause I'm not really trying to buy a new one of those :/

But the biggest problem is that it already erased Ubuntu off my laptop so now it won't boot at all. If I figure out what the problem is, I'm gonna have to figure out how to make another boot drive from my Windows PC I guess.

Just sucks cause through all this I was starting to get interested in Ubuntu and looking forward to exploring it.

---

### Post by Timoteo32 on 2013-04-21
I did some reading and looks like you can get that error from a bad ISO file as well. I'm currently downloading the 12.04 alternate instead of the desktop version cause one person said that worked for them.

I assume [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) is the best place to get my ISO?

So I created a boot drive from the 12.04 Xubuntu alternate file. It again made it most of the way through the installer but gave me an error at "Select and Install Software". However, unlike the Desktop version, it allowed me to skip it and go to the next step and install the GRUB loader. The end result was that my computer now boots up and asks me to log in at a terminal prompt and once I log in, I have a terminal prompt but I don't appear to have any real operating system. This is better than not booting at all though I suppose.

I then went back into the installer and selected the "Check disk for errors". I got the following pop up > .pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.14.99~git20111219.aacbd629-Oubuntu2_i385.deb file failed from the MD5 checksum verification. Your CD-Rom of this file may be corrupted
Which is all pretty much greek to me :P I'm stymied as to what I should do next.

---

### Post by Timoteo32 on 2013-04-22
I checked the MD5 sum on my iso and it appears to be fine.

---

### Post by Timoteo32 on 2013-04-27
I figured I'd post my solution here in case anyone googles this thread with a similar problem.  It seems like "Live Linux CD Creator" mentioned in the "Install With USB drive" link on page 1 only works with Ubuntu and not the other variants. At least I think that's why my Xubuntu boots were failing. I created an Ubuntu 12.04 drive and installed that. (Coincidentally I was still getting an error message with my wireless network driver) but I used the "Startup Disk Creator" app in Ubuntu to recreate my Xubuntu 12.04 boot drive. Installed that, activated the drivers for my network card, and all my problems seem to be fixed :)

---

