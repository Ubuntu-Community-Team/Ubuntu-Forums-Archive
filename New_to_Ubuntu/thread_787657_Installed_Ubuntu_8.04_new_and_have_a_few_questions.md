---
title: "Installed Ubuntu 8.04 new and have a few questions"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Gr3ghammett on 2008-05-09
As the title states, Installed ubuntu 8.04 (Hardy Heron), and I'm pretty new to linux in general and am having some issues that I'm hoping I can get some guidance with.

First to give you an idea of what I'm working with, I'll give you a summary of my laptop and internet situation.

Personal laptop - Partitioned 1/2 Win Vista (X^P) and Ubuntu (Hardy Heron).  I can connect to the internet via wirless on my win vista partition, but currently messing with ndiswrapper to get my wireless interface to work on the ubuntu version.  I can not get a wired connection to the internet, only wireless (because of my location). (wireless card is a Atheros AR5007EG)

I installed ndiswrapper and loaded the win driver.  But when I type the command "modprobe ndiswrapper" I get no messages, but the interface does not enable.  Wlan0 does not show up in iwconfig or ifconfig.

My major question is is there anyway I can download kernel updates to a flash drive using my win partition to put on my ubuntu partition to help get ndiswrapper to install correctly (as well as other things like .mp3 codecs, and DVD playability).

Another question I do have applies to another laptop with wireless issues.  Drivers are installed and seen by ubuntu, but when the interface is manually enabled thru the gui, the interface enables for a split second then disables.  Ndiswrapper is used and the wireless card is a built in one (Broadcom model).

Any guidance is greatly appreciated.  I'm just trying to get ubuntu on the net wirelessly so I can get win apps to work in ubuntu and ditch Vista!  Thanks in advance

---

### Post by pro003 on 2008-05-09
did you try

```
ifconfig wlan0 up
``` 


i would recommend you to install madwifi...

---

### Post by subzero316 on 2008-05-09
> I installed ndiswrapper and loaded the win driver. But when I type the command "modprobe ndiswrapper" I get no messages, but the interface does not enable. Wlan0 does not show up in iwconfig or ifconfig

+1  pro003 on madwifi

Check [this thread]("http://ubuntuforums.org/showthread.php?t=512828") thats how i got my WIFI enabled.
For d/lz in that thread i used diff location..

---

### Post by Gr3ghammett on 2008-05-09
I did do that and it said no such interface.  Right now working on installing madwifi.  Just waiting for the download to finish before switching to the other partition. I'll let you know how it goes.  :: crosses fingers::

---

### Post by Gr3ghammett on 2008-05-09
Followed the instructions on setting up madwifi from the link given.  Downloaded it, switched to ubuntu with the instructions and tar file, extracted installed, no problems.  Next I had to type two commands, and it's where it got a little weird.

I typed:
sudo modprobe ath_pci - no messages, so must mean it worked fine
sudo modprobe wlan_scan_sta - error. Unknown symbol in something.  

I reset the laptop.  Next time around it was reversed.  Ath_pci got the error and wlan_scan_sta didn't.  I diabled the atheros driver and tried again starting with sudo make install, still ath_pci got the error.  Reset the laptop tried again, same results.

---

### Post by Gr3ghammett on 2008-05-10
Thank you very much.  I installed madwifi (had to download build essential package [got the dependencies for build essential off of the cd] then install madwifi again).  After the fresh install the errors I got that I mentioned in my last post went away and I got a wireless internet connection.  Thanks again for guiding me in the right direction!!!!!!!!

---

