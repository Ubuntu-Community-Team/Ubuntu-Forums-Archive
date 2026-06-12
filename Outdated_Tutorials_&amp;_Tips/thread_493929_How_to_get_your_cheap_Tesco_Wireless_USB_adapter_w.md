---
title: "How to get your cheap Tesco Wireless USB adapter working in Ubuntu"
date: 2007-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by djhworld on 2007-07-06
**Please note this is a tutorial for Feisty users, I'm not sure on the compatibility with older versions!**

Now I'm unsure as to where this abomination of hardware has reached in the world, but here in the UK they used to sell it (and probably still do) in Tesco, a supermarket. 

The adapter in question is white in colour and holds the following information on the back (I've attached two photos as well)

[B]Belkin
802.11g Wireless USB Adapter
Model No: F5D7050 E[/B]

Now before anyone quickly dismisses this post as a duplicate (the F5D7050 chipset seems to come up a load on these forums), let me clear up one thing;

**This adapter has [COLOR="Red"]NOTHING[/COLOR] to do with Belkin, the chipset inside it isn't even the one marked on the label and to be entirely honest I have no idea who has actually made it. **

I must have spent hours trying to get this damn thing to work using the rt2000 drivers and all the other suggestions that have been offered, when the reality is that you're wasting your time.

Upon a simple lsusb, the card reveals itself as 

```
Bus 004 Device 002: ID 083a:f503 Accton Technology Corp. 
```

Still, finding drivers is elusive as proving the existence of unicorns, I realised this when I lost the driver disc for it on Windows, I literally spent over 3 hours trawling the Internet to find a Windows driver but failing. 

Luckily, a few days ago I found the driver disc and I'm happy to report that this USB stick works fine under Ubuntu with ndiswrapper. However please note this is for 32bit systems only. 

It's (obviously) recommended you have another computer with Internet access to download the packages.

**Step 1: **

Download the following packages from [http://packages.ubuntu.com](http://packages.ubuntu.com)
[URL="http://packages.ubuntu.com/feisty/misc/ndiswrapper-common"]
ndiswrapper-common_1.38-1ubuntu1_all.deb[/URL]
[ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb]("http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9")

Put them in a folder in your /home directory, call it "wireless" or something. 

Grab the driver CD that came with your stick, if you don't have it, don't worry, I've packaged them up for you to download at the bottom (drivers.tar.gz). 

If you have the CD, pop it into your drive and copy the "Driver" folder across into your wireless directory. 

If you haven't, extract the tar.gz linked at the bottom to a folder in your "wireless" directory that you created earlier, call it "drivers" or something. 

Open up a terminal and "cd" into the wireless directory

```
cd Wireless
```

**Step 2: **

```
 sudo dpkg -i ndiswrapper-common_1.38-1ubuntu1_all.deb 
```

```
 sudo dpkg -i ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
```

** Step 3: **

"cd" into your driver directory that you made earlier, with the drivers in it.

```
 cd drivers 
``` 

Then simply perform the following commands 

```
 sudo ndiswrapper -i A4501A.inf 
```
```
 sudo ndiswrapper -m 
```
```
 sudo ndiswrapper -mi 
``` 
```
 sudo modprobe ndiswrapper 
``` 

If all goes well, you should be able to connect to your wireless network! Try hovering over the network icon in the top right corner, see if it sees any available networks.

....and that's that!

---

### Post by Tahakki on 2010-01-18
This just crashes with ndiswrapper 1.55 (the latest one).

---

