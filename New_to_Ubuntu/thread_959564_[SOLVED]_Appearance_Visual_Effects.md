---
title: "[SOLVED] Appearance: Visual Effects"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by EvanRogers on 2008-10-26
When i go into Appearance and Preferences and click on Visual Effects it says they are off, i try to change it to the normal effects and then the screen flickers for a few seconds then it sais that it coulnd't change the visual effects. Why would this be happening? 

Also when i first installed Ubuntu i accidentally right clicked on the top pannel and clicked remove from pannel and now when i open up a application it doesn't show up in the top panel. This was really usefull to me and i would be really greatfull if someone could tell me how to get it back. Thanks guys.

---

### Post by DrMelon on 2008-10-26
The Appearance problem is caused by not having the right video drivers or perhaps not having a powerful enough graphics card.

What video card do you have?

---

### Post by EvanRogers on 2008-10-26
> **DrMelon said:**
> The Appearance problem is caused by not having the right video drivers or perhaps not having a powerful enough graphics card.

What video card do you have?

I have no clue what video card i have, but i know that it works, because before i re installed ubuntu it worked fine, and a couple of times before the re-install i had it set at extra. Thats why this is confusing me.

---

### Post by SunnyRabbiera on 2008-10-26
> **EvanRogers said:**
> I have no clue what video card i have, but i know that it works, because before i re installed ubuntu it worked fine, and a couple of times before the re-install i had it set at extra. Thats why this is confusing me.

well there is a way to check your video card
What is your computer model?
Brand?

---

### Post by EvanRogers on 2008-10-26
> **SunnyRabbiera said:**
> well there is a way to check your video card
What is your computer model?
Brand?

I dont know how to check it, but if you do you could tell me please. I have a Dell Dimension 3000.

---

### Post by ubername on 2008-10-26
> **EvanRogers said:**
> I have no clue what video card i have, but i know that it works, because before i re installed ubuntu it worked fine, and a couple of times before the re-install i had it set at extra. Thats why this is confusing me.

Do you have 'Hardware Drivers' as an option from your 'System' menu? if so, go there and see if any drivers are listed. If more than one, get back to the forum to ask for advice, otherwise enable the driver.

---

### Post by Amazona aestiva on 2008-10-26
Run this in terminal:
```
lspci
```
This should give you a list of your hardwares including your graphics card.

---

### Post by EvanRogers on 2008-10-26
> **ubername said:**
> Do you have 'Hardware Drivers' as an option from your 'System' menu? if so, go there and see if any drivers are listed. If more than one, get back to the forum to ask for advice, otherwise enable the driver.

None are listed.

---

### Post by EvanRogers on 2008-10-26
> **Amazona aestiva said:**
> Run this in terminal:
```
lspci
```
This should give you a list of your hardwares including your graphics card.

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by Amazona aestiva on 2008-10-26
> **EvanRogers said:**
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 **VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)**
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

There it is!
Could you try this:
```
gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
```
This should be able to install the restricted drivers of a graphics card. (as for nVidia, because I've that)

Regards

---

### Post by EvanRogers on 2008-10-26
> **Amazona aestiva said:**
> There it is!
Could you try this:
```
gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
```
This should be able to install the restricted drivers of a graphics card. (as for nVidia, because I've that)

Regards

I did that but all that happened was the hardware drivers interface poped up and it still has nothing listed. I copy and pasted that into the terminal.

---

### Post by Amazona aestiva on 2008-10-26
Well, check if compiz is installed, but I haven't got any further idea.

All the best

PS:
One more thing, what happens if you run the following in terminal:
```
compiz --replace
```

---

### Post by EvanRogers on 2008-10-26
> **Amazona aestiva said:**
> Well, check if compiz is installed, but I haven't got any further idea.

All the best

PS:
One more thing, what happens if you run the following in terminal:
```
compiz --replace
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by Amazona aestiva on 2008-10-26
> **EvanRogers said:**
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

I'm not sure, but you may need this:
```
sudo apt-get install xserver-xgl
```

Regards

---

### Post by EvanRogers on 2008-10-26
> **Amazona aestiva said:**
> I'm not sure, but you may need this:
```
sudo apt-get install xserver-xgl
```

Regards

Well, hasn't worked, i've restarted and everything and its just not working, i dont know what to do.

---

### Post by Amazona aestiva on 2008-10-26
> **EvanRogers said:**
> Well, hasn't worked, i've restarted and everything and its just not working, i dont know what to do.

Try reinstalling the graphics drivers, and/or compiz. As I know the order of their installation is important.
Install emerald too.(just try out everything)

Regards

---

### Post by EvanRogers on 2008-10-26
> **Amazona aestiva said:**
> Try reinstalling the graphics drivers, and/or compiz. As I know the order of their installation is important.
Install emerald too.(just try out everything)

Regards

Well, i fixed it, by doing a clean install of Ubuntu. I didn't want to do that but i couldn't deal with the horrible looking interface anymore. Now i can use visual effects again, hmm doesn't make sense to me, oh well, Solved.

---

### Post by Amazona aestiva on 2008-10-27
> **EvanRogers said:**
> Well, i fixed it, by doing a clean install of Ubuntu. I didn't want to do that but i couldn't deal with the horrible looking interface anymore. Now i can use visual effects again, hmm doesn't make sense to me, oh well, Solved.

Nice to hear that, but please mark this thread as solved then. (Thread tools menu)

Regards

---

