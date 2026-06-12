---
title: "Wireless Internet Connection"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by Mechatron on 2012-12-27
I literally just installed Ubuntu and know nothing at all. I'm running it off my USB stick for now- Vista is installed on the local drive.  This is an adventure, and the first thing I need is to get wireless Internet going to start playing.  I am currently wired into my ATT NVGS10 router with an ethernet cable, but want to set up wirelessly like on my WinOS.  I don't even know where to begin.  I do not see the wireless signal populating in any lists or settings.....  Any hints would be appreciated.

---

### Post by maruf7 on 2012-12-27
What type of wireless device you are going to use?

---

### Post by Mechatron on 2012-12-27
I want to connect my laptop wirelessly to my router instead of wired directly into it as I have it right now..  The laptop is running Ubuntu from my USB stick.

---

### Post by maruf7 on 2012-12-28
May try this, not sure whther it'll work or not:

click on the network button(located on the top bar of screen, beside volume icon)> click on Edit Connections> select Wireless and fill the necessary info there.........

---

### Post by audiomick on 2012-12-28
Most likely you are still missing the drivers for the wireless. Has the system not offered to let you install them?

Assuming you have a current ubuntu, you will have the Unity desktop. Click on the icon in the extreme right of the top panel, the one the includes the shut down button. Go into system settings and look for the "additional drivers" utility. Your computer needs to be connected to the internet for this, i.e. on the cable.

If you are running from the USB stick and it does not have persistance, you will most likely have to get those drivers every time you start Ubuntu. "Persistance" is basically a small amount of storage space that the system uses to remember stuff. It that is the case, it might be easier for you to just stay on the cable until you decide to do a proper install. Having said that, I think the USB gets created by default with persistance, depending on how you made it.

In order to get better assistance, open a terminal and do
```
sudo lshw -C network
```

You will be asked for a password. I think, in the live environment, you can just hit enter. If you have trouble with that, just do the command without sudo.
```
lshw -C network
```
It will complain that you should run lshw as root, but I don't think it will cause you any trouble in this instance. 

Anyway, post the result of that here. Use the # button about the post window to put code tags around it.

---

### Post by grahammechanical on 2012-12-28
As you are running a live session off of a USB stick and are connected to the router by ethernet cable, the Network Manager icon will look like two arrows pointing in the opposite directions.

Clicking on it should show you a list of Wifi Networks - wireless access points in range. If you see this list then Ubuntu recognises the wireless adapter in the machine and has drivers for it.

If you do not see that list of wireless access points then go to System Settings in the Power/Cog menu and open Software Sources. Go to the Additional Drivers tab. You may see 5 drivers for your video card one of which is in use but you might also see a driver for your wireless adapter that is not in use. Activate it. I am assuming Ubuntu 12.10. If it is 12.04 then look for the Additional Drivers utility.

This should all work in a live session but the moment you exit the live session you will lose any settings but it is a good way of experimenting with Ubuntu before you install it.

To set up wireless you simply click on your wireless network and enter the wireless key/passphrase that is needed to connect to the router when asked to authenticate. And Ubuntu should make a connection. Network Manager will do all the work of identifying the encryption method and storing the settings.

Regards.

---

