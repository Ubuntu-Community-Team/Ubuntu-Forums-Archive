---
title: "[SOLVED] Screen flash/Speakers Pop"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Sava8420 on 2008-08-26
So okay I bought a new laptop and dual booted 8.04 and Vista.  All went good and am working on getting all hardware up and running.  With that said, there is one thing that I'm really not liking at all.  Whenever I shutdown or restart from Ubuntu at the point when it cycles or switches off the power it acts as though there is a powersurge that backfeeds through the screen and speakers.  The screen flashes white for split second and speakers scratch/pop at the same time.  So far I have resorted to closing the lid and the screen won't flash at least but there is obviously a problem and I'd rather address it now than down the road.  Doesn't happen with Vista only Ubuntu.  
System Information:
- HP Pavilion dv5z Entertainment Notebook
- AMD Turion( X2 Ultra Dual-Core Mobile Processor ZM-80 (2.1 GHz)
- 15.4" WSXGA+ High-Definition HP BrightView Widescreen Display
- 3GB DDR2 System Memory (2 Dimm)
- 256MB ATI Radeon(TM) HD 3450 Graphics
- Wireless LAN 802.11a/b/g/n and Bluetooth
- 250GB 5400RPM SATA Hard Drive 
- 64bit Vista and Ubuntu 8.04 AMD64
THANK YOU in advance for any help offered.  Also, Thanks for the numerous tutorials and posts that have made my experience with Ubuntu so much easier.  Would still be trying to setup my desktop with 7.04 without them. ](*,)

---

### Post by nicedude on 2008-08-26
I don't fully understand under what circumstances this is happening. Is this happening anytime you shutdown the PC ? What about when you start the PC ? Or is this happening when PC goes into Suspend or Hibernate only? This would help me or others here try and see if we can help you out.

---

### Post by Sava8420 on 2008-08-26
> **nicedude said:**
> I don't fully understand under what circumstances this is happening. Is this happening anytime you shutdown the PC ? What about when you start the PC ? Or is this happening when PC goes into Suspend or Hibernate only? This would help me or others here try and see if we can help you out.

This is happening everytime I either shutdown or restart the laptop from Ubuntu only.  Has never happened when shutting down or restarting from Vista which is what has got me confused.  If it did it would be obviously a hardware problem.  

Also, when attempting to use flash drive on usb it will mount for a couple seconds and then disconnect.  It seems that there is a configuration problem with board.  How do I check configuration of USB controllers and PCI to USB controller?

---

### Post by nicedude on 2008-08-26
This is happening everytime I either shutdown or restart the laptop from Ubuntu only. Has never happened when shutting down or restarting from Vista which is what has got me confused. If it did it would be obviously a hardware problem. 

Your absolutely right that this is obviously a software related problem. The only thing I could tell you would be to make sure you have updated everything after you installed. If it is only a momentary thing than I might just learn to live with it until I figured out why.


Also, when attempting to use flash drive on usb it will mount for a couple seconds and then disconnect. It seems that there is a configuration problem with board. How do I check configuration of USB controllers and PCI to USB controller?

You don't for the most part, they don't give you the configuration applets that do nothing like they do in windows. I would bet it is a disk mounting issue anyway over a USB one.

To see what controls are available this will show you most of the Gnome configs if you run it in a terminal
gnome-control-center

And if it is a mount issue then you can either learn the mount command or the simple way is install pysdm and use it to mount the disk, here are the commands for that

sudo apt-get install pysdm

& TO RUN IT
sudo pysdm

then select the drive and click mount.


Hope this info helps you out

---

### Post by boothby on 2008-09-12
Sava, I get the same scratch/pop on my HP dv5z.  Also, volume control & mute don't work for me.  Do they work for you?  The touch panel seems to work, but I have zero control over the volume.  Very frustrating.  Note, I currently have sound completely disabled, but when I shut down / restart, I still get the scratch/pop.

---

### Post by Sava8420 on 2008-09-12
> **boothby said:**
> Sava, I get the same scratch/pop on my HP dv5z.  Also, volume control & mute don't work for me.  Do they work for you?  The touch panel seems to work, but I have zero control over the volume.  Very frustrating.  Note, I currently have sound completely disabled, but when I shut down / restart, I still get the scratch/pop.

So you didn't mention if your display flashes but I'm assuming it probably does.  So I originally didn't have control with touchpad volume and mute but if you go to -system -preferences -keyboard shortcuts   you can set up the buttons to work.  The only button not working for me is the wireless button but wireless is working.  So I'm pretty sure last night when I shut down it didn't happen.  Otherwise to my knowledge it still does it every time.  I just close the screen so it doesn't flash and really don't see it causing any damage.  If it does well that is what extended warrenty is for.  Since I dualbooted (actually triple I guess)  I was able to keep the HP recovery partition.  So can reset system with that if need to send in for warrenty.  So I am wondering what options you went with on your dv5z?  I had quite the fun time setting up mine as I decided to get ATI HD3450 graphics card, the Atheros 802.11 a/b/g/n wireless with bluetooth and the 1680x1050 display.  The bluetooth was the only one to function after initial install.  If you are having any difficulties  with any of these problems let me know.  At the same time if you ask me I will link you to a thread that is on this great forum.  Most importantly I see this was your #1 post,  Welcome to the Community!  You'll find alot of good people here.

---

