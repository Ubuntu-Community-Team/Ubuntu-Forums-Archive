---
title: "Brand new to linux and Ubuntu."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Vegadark on 2008-05-05
So let me start off by saying hello. I am completely new to linux, I have been using windows since 3.1. I wanted to try something new so I downloaded Ubuntu Hardy Heron yesterday and installed it, first formatting and pertitioning the HD for a completely fresh install. I got it running after having problems getting the installer CD to run (had to hit F4 to put it into safe graphics mode)

So here is the first of what I am sure will be many, many questions.

I have a netgear WG121 wireless USB adapter. I am unable to get it to work at all. Is there a device manager type thing like windows has? I cant even tell if the computer sees it plugged in. The green USB LED is on telling me it is getting USB power.

Would I be better off getting a different USB adapter that might work just by plugging it in?

Thank you for your time.

Mike P.

---

### Post by Monicker on 2008-05-05
There is some informtion about that wireless device here, in the USB section:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by Tatty on 2008-05-05
```
lsusb
``` will show you what is plugged into your usb ports.

Try this wireless troubleshooting guide from the community wiki [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Wireless problems are common but are usually fixable:)

---

### Post by nothingspecial on 2008-05-05
You will get your wireless working.
 If you don`t mind spending the money I can tell you that a Belkin G Plus Mimo USB Network Adapter works. It`s helped me get 2 laptops with different wireless cards up and running. If you post the output of -

```
lspci 
```

 - I`m sure the good people on these forums can help you. The line you are looking for begins Ethernet controller: For example here`s mine -

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Also try googling your wireless card -

I typed - Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter Ubuntu - and it brought me to a how to that had me up and running in about 5 minutes.   :)

Edit Sorry, you have told us your wireless card. This might work -
[https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121)

or this -
[http://www.ubuntuforums.org/showthread.php?t=177958](http://www.ubuntuforums.org/showthread.php?t=177958)

or this -
[http://ww.ubuntuforums.org/showthread.php?t=583690](http://ww.ubuntuforums.org/showthread.php?t=583690)

Good luck

---

### Post by Vegadark on 2008-05-05
Ok, thanks for all of your help. I did actually read through all of those links last night. Some seemed outdated, and I came across another one where an incompatibility between the WG121 and Hardy Heron came up. So I went out and bought the belkin adapter mentioned above. I'll try it out tonight and see what happenes when I get home from work.

Thanks a bunch!

Mike P.

---

### Post by SlappyPappy on 2008-05-05
Wow, that's taking charge of the situation! Hope that works out for you!

---

### Post by Vegadark on 2008-05-06
Ok, after messing with this thing all night and most likely screwing up alot of stuff that I don't know how to use, I have decided to start fresh and reinstall Ubuntu 8.04 again.

Ok, when installing Ubuntu, should my wireless USB adapter be plugged in or not?

I do not have a regular NIC so I am stuck trying to get this to work.

BTW, the chipset is RT73. Last night I tried doing what is covered in this thread: [http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236")
with absolutely no luck.

So bear with me here if you don't mind. I really appreciate all the help.

---

### Post by Vegadark on 2008-05-06
I read somewhere on these forums that 8.04 supports the RT73 chipset "out of the box." Does "out of the box" mean that it will show up automatically in the network config when plugged in with no other setup needed?

Is the howto I listed above outdated for 8.04?

I am home from work all day, so I have plenty of time to get this working.

Thanks again.

Mike P.

---

### Post by Vegadark on 2008-05-06
OK, so the fresh install is up and running. 

I have completely gone through the howto listed above to install the rt73 driver. Unfortunately something must have gone wrong, as I have NO network devices except the dialup modem in the network window.

if I type lsusb, the device is listed.

when I type ifconfig there is no mention of a wlan of any sort.

something that I found interesting: when going through the howto from above, one of the commands is:
```
sudo ifconfig wlan0 down
```

for which this is returned:
```
wlan0: ERROR while getting interface flags: no such device
```

Don't really know where to turn from here.:confused:

---

