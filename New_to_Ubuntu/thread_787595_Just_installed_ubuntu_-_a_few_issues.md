---
title: "Just installed ubuntu - a few issues"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-09
I installed ubuntu to dual boot with XP on my 2006 desktop. I had previously set it up on n incredibly old computer with no poblems. Everything worked fine. This time, there are a few problems. For one, the resolution. The highest it offers is 800x600....which is so low and makes everything huge on my 17" monitor. Can this even be fixed? 

The other big problem is the wireless home network. On the other one I used a cheap belkin wireless usb thingy, and I was able to select our home network from a list very easily. This computer has a belkin card....and it doesn't seem to want to connect to the same network. It's right by the other old computer with ubuntu. How come it's not working when the other did? Is there any way to fix this?

So, yeah....lots of problems with ubuntu for me.  Please keep in mind that I don't know much about hardware or 'drivers" and stuff like that.

EDIT: okay, out of 3 drivers listed...one does not work: nvidea_new.  Does this have something to do with the resolution?

I'm not sure if these have anything to do with...anything....but here are the drivers relating to network:

1394 net adapter
Belkin wireless G desktop Card
Nvidea nforce networking controller

and then here's my graphics card: Geforce 6150

---

### Post by dmub82 on 2008-05-09
> **Rukaru said:**
> I installed ubuntu to dual boot with XP on my 2006 desktop. I had previously set it up on n incredibly old computer with no poblems. Everything worked fine. This time, there are a few problems. For one, the resolution. The highest it offers is 800x600....which is so low and makes everything huge on my 17" monitor. Can this even be fixed?

First, are you running Hardy or Gutsy? So 800x600 the highest resolution available in System-Preferences-Screen Resolution (or Screens & Graphics, I think it was called, in Gutsy)? Look in System-Administration-Hardware Drivers (or Restricted Driver Manager). Is there a driver available there for your video card?

> **Rukaru said:**
> The other big problem is the wireless home network. On the other one I used a cheap belkin wireless usb thingy, and I was able to select our home network from a list very easily. This computer has a belkin card....and it doesn't seem to want to connect to the same network. It's right by the other old computer with ubuntu. How come it's not working when the other did? Is there any way to fix this?

Specifically what cheap Belkin card do you have? I've got the F5D7050 version 3002; it works right out of the box in Hardy, but I did have to manually enter my wireless settings in System-Administration-Network (select wireless connection, click properties, uncheck "enable roaming" and then fill in the blanks for your setup). If you're running Gutsy, it may be more complicated.


> **Rukaru said:**
> Another thing that I am concerned about is this weird clicking noise my tower makes when I start up ubuntu. It doesn't do that when I start up XP! It isn't random either. Each of the 3 times I've started ubuntu, it made that clicking noise. it's like a series of 3 clicks that sound kind of like a clock.
Speaking of a clock.....after I reset the clock in ubuntu....ubuntu froze up.  only the cursor worked.  I couldn't click anything.

That's weird. I'm useless there.

---

### Post by Rukaru on 2008-05-09
> **dmub82 said:**
> First, are you running Hardy or Gutsy? So 800x600 the highest resolution available in System-Preferences-Screen Resolution (or Screens & Graphics, I think it was called, in Gutsy)? Look in System-Administration-Hardware Drivers (or Restricted Driver Manager). Is there a driver available there for your video card?



Specifically what cheap Belkin card do you have? I've got the F5D7050 version 3002; it works right out of the box in Hardy, but I did have to manually enter my wireless settings in System-Administration-Network (select wireless connection, click properties, uncheck "enable roaming" and then fill in the blanks for your setup). If you're running Gutsy, it may be more complicated.




That's weird. I'm useless there.

I don't know what card I have. I looked in Hardware drivers (I have Hardy Heron by the way) and it shows 3.  The one that is not inse is "nvidea_new", so I guess that's my graphics card.  Anything I can do here to make it so ubuntu can use it?

---

### Post by Rukaru on 2008-05-09
Oh yeah...and I don't know how to check what wireless card I have.  Again, I really need assistance here.

---

### Post by dmub82 on 2008-05-09
> **Rukaru said:**
> I don't know what card I have. I looked in Hardware drivers (I have Hardy Heron by the way) and it shows 3.  The one that is not inse is "nvidea_new", so I guess that's my graphics card.  Anything I can do here to make it so ubuntu can use it?

If you go into Hardware Drivers and check the box next to "Nvidea new", that will tell Ubuntu to download and enable that driver (after you reboot). If it works, that should give you more options for screen resolution. It may look weird at first, as long as you can log in take a look at Screen Resolutions and see if you find a suitable option. If the setting you want isn't working, play around with the options for Refresh Rate on that same screen.

---

### Post by dmub82 on 2008-05-09
For your wireless, open a terminal (Applications-Accessories-Terminal) and type ```
lshw -C network
```. Post what you get here.

---

### Post by Rukaru on 2008-05-09
> **dmub82 said:**
> If you go into Hardware Drivers and check the box next to "Nvidea new", that will tell Ubuntu to download and enable that driver (after you reboot). If it works, that should give you more options for screen resolution. It may look weird at first, as long as you can log in take a look at Screen Resolutions and see if you find a suitable option. If the setting you want isn't working, play around with the options for Refresh Rate on that same screen.

It didn't work.  It was already enabled, but it won't go to "in use".  I think its restricted.  Anything I can do without messig anything up for XP? I also really need that internet...if anyone knows anything...let me know.

---

### Post by Rukaru on 2008-05-09
> **dmub82 said:**
> For your wireless, open a terminal (Applications-Accessories-Terminal) and type ```
lshw -C network
```. Post what you get here.
It said something like "warning, you should run this program as super user."

---

### Post by dmub82 on 2008-05-09
> **Rukaru said:**
> It said something like "warning, you should run this program as super user."

MY bad, try ```
sudo lshw -C network
```

---

### Post by Rukaru on 2008-05-09
> **dmub82 said:**
> MY bad, try ```
sudo lshw -C network
```Okay.....it asked for my password...I gave it...it showed some text..I closed it.  Nothing is different.  Maybe I should give up on ubuntu.  There are no problems with my XP and Vista.

---

### Post by Rukaru on 2008-05-09
I'm not sure if these have anything to do with...anything....but here are the drivers relating to network:

1394 net adapter
Belkin wireless G desktop Card
Nvidea nforce networking controller

and then here's my graphics card: Geforce 6150

---

### Post by dmub82 on 2008-05-09
Yeah, that text is what we want to see. That command lists your network hardware so we know what we're working with. 

First, try going to System-Administration-Network, click "Unlock" and enter your password, select Wireless Network, click Properties, uncheck the box at the top that says "Enable roaming" and fill in the information for your router if you know it (you should know it if you're the one that set up the router). You might not be able to select your network off a list but try entering it manually and see if that works.

If it doesn't... run these commands, and post the output of each here:
```
lsusb
``` (you said it was a USB wireless thing right?)

```
sudo iwconfig
```

```
sudo ifconfig
```

These won't fix it, but they'll tell us information we need.

---

### Post by Rukaru on 2008-05-09
> **dmub82 said:**
> Yeah, that text is what we want to see. That command lists your network hardware so we know what we're working with. 

First, try going to System-Administration-Network, click "Unlock" and enter your password, select Wireless Network, click Properties, uncheck the box at the top that says "Enable roaming" and fill in the information for your router if you know it (you should know it if you're the one that set up the router). You might not be able to select your network off a list but try entering it manually and see if that works.

If it doesn't... run these commands, and post the output of each here:
```
lsusb
``` (you said it was a USB wireless thing right?)

```
sudo iwconfig
```

```
sudo ifconfig
```

These won't fix it, but they'll tell us information we need.
I don't have a USB...that was for the first computer I set it up with.  This computer has a card.  A belkin wireless G desktop card.

---

### Post by dmub82 on 2008-05-09
> **Rukaru said:**
> I don't have a USB...that was for the first computer I set it up with.  This computer has a card.  A belkin wireless G desktop card.

Ok, skip lsusb, run the others, post what you get.

---

### Post by potatan on 2008-05-09
> **Rukaru said:**
> Okay.....it asked for my password...I gave it...it showed some text..I closed it.  Nothing is different.  Maybe I should give up on ubuntu.  There are no problems with my XP and Vista.

I think the original poster wanted you to paste the output of that command so he can help with your problem.

Type the command again (with the "sudo" prefix), then copy and paste the output into a new post.

---

### Post by Rukaru on 2008-05-09
> **potatan said:**
> I think the original poster wanted you to paste the output of that command so he can help with your problem.

Type the command again (with the "sudo" prefix), then copy and paste the output into a new post.

Okay...I will. This may take a while.

---

### Post by Rukaru on 2008-05-09
> **potatan said:**
> I think the original poster wanted you to paste the output of that command so he can help with your problem.

Type the command again (with the "sudo" prefix), then copy and paste the output into a new post.

I don't know if I want to post all this information for all to see.  It has a serial number.

---

### Post by RyanBFS on 2008-05-09
copy the text and paste it on the forum.  Some of the wireless chipsets are  harder than others to get working in linux.  You have to remember that it's not the operating system that is having the trouble, but that the developers of your hardware made the drivers for Windows and now Linux is having to adapt to them.  If you stick it out for a bit and be patient you will become much happier with Ubuntu than Windows.

And once you get that g-card working you can start playing with compiz and emerald.. that's when you start having fun.

---

### Post by valke on 2008-05-09
Also, that "serial number" is not something any of us here can use aside from identifying your wireless card. All it does is identify your card. It's not like a software key or anything like that.

---

### Post by Rukaru on 2008-05-09
> **RyanBFS said:**
> copy the text and paste it on the forum.  Some of the wireless chipsets are  harder than others to get working in linux.  You have to remember that it's not the operating system that is having the trouble, but that the developers of your hardware made the drivers for Windows and now Linux is having to adapt to them.  If you stick it out for a bit and be patient you will become much happier with Ubuntu than Windows.

And once you get that g-card working you can start playing with compiz and emerald.. that's when you start having fun.

That's exactly what I want.  I need someone to walk me through this stuff.  It's so confusing and stressful.  Apparently I just got the internet working by entering stuff about my network or whatever.  I wasn't sure about one thing though...is gateway the same as default route?  I also can't find the thing that shows connection...with the bars.  I had removed it accidentally.

Now...can someone just tell me...if that nvidea_new card is not working, does that mean there is no hope without buying new hardware?

---

### Post by Rukaru on 2008-05-09
> **valke said:**
> Also, that "serial number" is not something any of us here can use aside from identifying your wireless card. All it does is identify your card. It's not like a software key or anything like that.

Okay.....I'll post it.  Now that I apparently have connection...I can copy and paste it.  I've been using my laptop with vista to post stuff.

---

### Post by phr0ze on 2008-05-09
> **Rukaru said:**
> Okay.....I'll post it.  Now that I apparently have connection...I can copy and paste it.  I've been using my laptop with vista to post stuff.

So you got connected? Was it the manual configuration?

---

### Post by Rukaru on 2008-05-09
> **phr0ze said:**
> So you got connected? Was it the manual configuration?
yeah I had to do that.  Id like to undo all this though because I just used info from the other ubuntu computer.  I'm sure there'll be conflicts here.  I'd like to find another way.  This is just temperary.  I want it to auto connect and get the info it needs by itself like it did with the first computer I set up with ubuntu.  Okay, now here is what I got after doing the sudo lshw -C network command:

       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: wifi0
       version: 01
       serial: 00:11:50:d4:d8:96
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.107 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by RyanBFS on 2008-05-09
also from what I can find on the forums it looks like your graphics car should work once you activate the restricted driver and reboot.  gforce chips are usually the best with linux I'm 9 for 9 with them.  Now ATI.... well that's a different story.  I posted a reply to someone who seems to have been having the same problem as you here [http://ubuntuforums.org/showthread.php?t=746619 ]("http://ubuntuforums.org/showthread.php?t=746619") but it's 4 weeks old

---

### Post by valke on 2008-05-09
Don't worry, we'll get there.

What everyone is trying to get you to do is post your results so that 1. people in your position right now can look a this and say, hey that's what's wrong with my computer! and 2. so that we can identify and resolve your problem and educate you at the same time. But we can't if we don't have all the information. :D

---

### Post by Rukaru on 2008-05-09
> **RyanBFS said:**
> also from what I can find on the forums it looks like your graphics car should work once you activate the restricted driver and reboot.  gforce chips are usually the best with linux I'm 9 for 9 with them.  Now ATI.... well that's a different story.  I posted a reply to someone who seems to have been having the same problem as you here [http://ubuntuforums.org/showthread.php?t=746619 ]("http://ubuntuforums.org/showthread.php?t=746619") but it's 4 weeks old

please tell me how to do that.  All I've heard is how to enable it, but it's already enabled!

---

### Post by valke on 2008-05-09
now just reboot!

---

### Post by RyanBFS on 2008-05-09
try lspci in command line and paste results

---

### Post by Rukaru on 2008-05-09
> **valke said:**
> now just reboot!
Dude it has always been enabled! I've rebooted it about 10 times! I even tried disabling then enabling then rebooting again, and that didn't work.  Again, It is already enabled and has already been enabled and rebooted.

---

### Post by Rukaru on 2008-05-09
> **RyanBFS said:**
> try lspci in command line and paste results

This what you wanted?

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:08.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
03:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
tyler@tyler-desktop:~$

---

### Post by RyanBFS on 2008-05-09
ya if it says that it's enabled then reboot. and if still having the problem go to system/preference/appearance and try and change visual effects to extra.  It may be that it is enabled but you don't have the rez in your xorg.conf file

---

### Post by Rukaru on 2008-05-09
> **RyanBFS said:**
> ya if it says that it's enabled then reboot. and if still having the problem go to system/preference/appearance and try and change visual effects to extra.  It may be that it is enabled but you don't have the rez in your xorg.conf file

Like I said, I had already rebooted.  I did what you said....and I also made my system up to date. Now something has changed.  The nvidia_new is gone, and is replaced with Nvidia accelerated graphics driver (latest cards).  Now this one wasn't enabled.  I tried enabling it and it said "W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new)

I don't want to put the rest because it might be my IP address.  it ends with i386.deb

One reason this may not have worked is because I lost internet connection after rebooting.  Like I said, what I did was only temperary.  I had to take info from another computer with ubuntu and I wasn't sure about what I did.  The info is still there, but firefox no longer works.  

Another reason this may not have worked is because I don't have an accelerated driver.  It might just say that because it needs it for advanced effects.  Do you really need an accelerated card for compiz to work?  I really wanted compiz! Now, I can't remember what card I have...but I posted it somewhere in this thread.

---

### Post by RyanBFS on 2008-05-09
I'd try sending a pm to ShakeyJake from the link I sent you on the first page.  Also you can look at your xorg file by typing: sudo gedit /etc/X11/xorg.conf but be carefull in there you can mess things up bad.  I'm fairly new to Ubuntu so you may have better luck asking someone else.

---

### Post by Rukaru on 2008-05-09
> **RyanBFS said:**
> I'd try sending a pm to ShakeyJake from the link I sent you on the first page.  Also you can look at your xorg file by typing: sudo gedit /etc/X11/xorg.conf but be carefull in there you can mess things up bad.  I'm fairly new to Ubuntu so you may have better luck asking someone else.

ok I will.  Thanks.

---

### Post by SunnyRabbiera on 2008-05-09
Jusy remember to be patient, remember we are volunteers here :D

---

### Post by lswest on 2008-05-09
> **Rukaru said:**
> Like I said, I had already rebooted.  I did what you said....and I also made my system up to date. Now something has changed.  The nvidia_new is gone, and is replaced with Nvidia accelerated graphics driver (latest cards).  Now this one wasn't enabled.  I tried enabling it and it said "W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new)

I don't want to put the rest because it might be my IP address.  it ends with i386.deb

One reason this may not have worked is because I lost internet connection after rebooting.  Like I said, what I did was only temperary.  I had to take info from another computer with ubuntu and I wasn't sure about what I did.  The info is still there, but firefox no longer works.  

Another reason this may not have worked is because I don't have an accelerated driver.  It might just say that because it needs it for advanced effects.  Do you really need an accelerated card for compiz to work?  I really wanted compiz! Now, I can't remember what card I have...but I posted it somewhere in this thread.

Do you have internet when you try to install the graphics drivers? because it needs to download a package, if it still doesn't work, go to system-->administration-->software sources and try choosing a server closer to where you live.

---

### Post by maramot on 2008-05-09
If you have upgraded to 8.04 from an older ubuntu version, make sure you are loading the right kernel for 8.04. The solution could be a very simple one, take a look here: [http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19)

---

### Post by dmub82 on 2008-05-09
> **Rukaru said:**
> Like I said, I had already rebooted.  I did what you said....and I also made my system up to date. Now something has changed.  The nvidia_new is gone, and is replaced with Nvidia accelerated graphics driver (latest cards).  Now this one wasn't enabled.  I tried enabling it and it said "W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new)

I don't want to put the rest because it might be my IP address.  it ends with i386.deb

That definitely sounds like Ubuntu was unable to download the driver when you tried to enable it. Verify your connection is working on that machine and keep trying (occasionally, the Ubuntu servers get bogged down and a request might time out). Are you still getting that error?

---

