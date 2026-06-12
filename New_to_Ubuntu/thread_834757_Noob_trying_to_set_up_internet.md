---
title: "Noob trying to set up internet"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by evannumber7 on 2008-06-19
hi, im actually not a COMPLETE noob, i've tried ubuntu in the past (about 5 or 6 or so), but never installed it before. so, i installed hardy heron 8.04 last night without any problems. but when i tried to set up the internet, it wouldn't work. No wireless, no ethernet, nothing. i dont completely understand the whole ndiswrapper thing either, but i tried it. but shouldnt ubuntu be able to configure my ethernet connection automatically? I've tried both plugging it into the router and directly into the modem. I didn't think i was so inept until i tried doing this. lol. so if you could please help me, i would appreciate it very much. and remember i AM pretty new at this.
oh, p.s., I'm on a Dell Inspiron B130, 248(?) RAM, i have broadcom ethernet/wi-fi, but i also have a Netopia SWL-2300U if i could just use that (which i tried)
thanks in advance.:)

--Edit: i tried installing ndisgtk, but i received this error: "Dependency is not satisfiable: ndiswrapper-utils-1.9"

---

### Post by moore.bryan on 2008-06-19
have you checked-out this page yet?
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by KenBW2 on 2008-06-19
> 
shouldnt ubuntu be able to configure my ethernet connection automatically?

Yes, but it needs the drivers to be able to do this. Although I've never heard of ethernet not working.
With regard to ndiswrapper - I've had a quick play with it but fortunately never needed to use it. If I understand it rightly you need to select the (it is?) bin file and then it installs it for you. But I'm probably wrong.

I'm not sure how you tried to install ndisgtk but the right way in linux is to either:
**GUI:**
System > Administration > Synaptic Package Manager
Search for ndisgtk and tick the box next to it. Click Apply and OK everything

**CLI:**
sudo aptitude install ndisgtk

They both do the same thing and importantly they resolve dependencies, which seems to be your problem. Dependencies are basically packages, or groups of files that an application relies on.

> 
I didn't think i was so inept until i tried doing this.

Don't worry, we've all been there! But believe me, in the last 7-8 months since I made the switch I've learned a lot more about computers tha I did when I was "protected" by Windows

---

### Post by Dr Small on 2008-06-19
Have you tried to configure the network at all? Things generally just don't happen when things are plugged in.

---

### Post by Victormd on 2008-06-19
Without the internet connection, aptitude or apt-get won't work...
We need to figure out how to get the wired going, then we can work on the wireless. I personally have never seen ubuntu not recognize an ethernet card. Can you open a terminal and type:
```
lspci |grep eth*
```
and see what you get, better yet, paste the results here.
This is what I get:
> 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

---

### Post by evannumber7 on 2008-06-19
ok, so i figured out the whole ndisgtk thing. I had installed the "common" package but not the "utilities" package, which kinda makes sense now (duh). but anyways. i typed in  lspci |grep eth* and got: "02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 02:03.0 Network Controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" I have no idea what to do now. and wasnt there supposed to be something where you found the driver for the device and found the .inf file? I dont understand that either. thanks for all your help.:)

---

### Post by evannumber7 on 2008-06-20
"02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network Controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)"

---

### Post by evannumber7 on 2008-06-23
okay, so i installed my ethernet & wireless drivers using ndisgtk, and it says theyre present, but when i try to search for our network (which i'm sure i'm within range b/c it works on XP) it will act like its connecting, but it wont connect, and... its just really annoying... so anything will probably help at this point because i've got no clue. thanks.

---

