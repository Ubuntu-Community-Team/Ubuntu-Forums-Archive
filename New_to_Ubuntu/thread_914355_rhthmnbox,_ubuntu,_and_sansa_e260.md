---
title: "rhthmnbox, ubuntu, and sansa e260"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by antgul338 on 2008-09-08
i have a sansa e260 mp3 player and i filled it with windows and now all i have is ubuntu.....rhythmnbox recognizes it but none of the files.....how can i format the player so it will be empty and i can start new with ubuntu and rhythmnbox? thanks in advance

---

### Post by antgul338 on 2008-09-08
all i wanna know how to do is empty the thing..........

---

### Post by kostkon on 2008-09-08
> **antgul338 said:**
> i have a sansa e260 mp3 player and i filled it with windows and now all i have is ubuntu.....rhythmnbox recognizes it but none of the files.....how can i format the player so it will be empty and i can start new with ubuntu and rhythmnbox? thanks in advance
Do you mean WMAs and that Rhythmbox cannot play them?

---

### Post by TrikeKid on 2008-09-08
If you want to simply delete all the files on the player, put it in MSC mode and it will show up on your desktop when it's plugged in, then just open it and delete the files you want gone like normal. You should be able to sync it with Rythmbox, but I can't remember if I did or not. I'm pretty sure I copied all the files onto my hard drive and loaded them into Amarok so I'd be independent of my Sansa.

---

### Post by lddm00 on 2008-09-23
Hi, I recently bought a sansa e260 and I can't get to work in Ubuntu 8.04. I configure MSC mode in the player and when I connect it says "connected" in the player but in the pc doesn't mount automatically. When I type lsusb in the console doesn't appear also the player as connected. Any help would be good.
Cheers.
Luis

---

### Post by Mornedhel on 2008-09-23
I have a Sansa e260 as well. It works for me.

Note that I have installed Rockbox on the player, but I could mount it fine before as well.

Basically, my only contribution to this thread will be : "it can be done since it works for me" and "the e260 can run Rockbox". Sorry.

---

### Post by lddm00 on 2008-09-23
Yes, I know most of the people use it with any problems in Ubuntu. But I don't know why when I connect the player its seems that Ubuntu recognizes it, as it doesn't appear in lsusb.

---

### Post by lddm00 on 2008-09-24
I was looking the Rockbox project, in your opinions is better than the original firmware?? Anyway I see that I can't install in my Sansa, as the one I have is a e260V2....and they doesn't have yet Rockbox for Version 2. Anyone has come to a solution or a idea in why my Sansa doesn't automont??

---

### Post by lddm00 on 2008-09-25
When I do: "dmesg | grep usb" the following errors appears:
[ 1754.333002] usb 4-4: new high speed USB device using ehci_hcd and address 4
[ 6105.022364] usb 4-4: new high speed USB device using ehci_hcd and address 5
[ 6255.121369] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 6255.241296] usb 3-1: device descriptor read/64, error -71
[ 6255.465186] usb 3-1: device descriptor read/64, error -71
[ 6255.681300] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 6255.800995] usb 3-1: device descriptor read/64, error -71
[ 6256.024870] usb 3-1: device descriptor read/64, error -71
[ 6256.240760] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 6256.648530] usb 3-1: device not accepting address 4, error -71
[ 6256.760483] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 6257.168323] usb 3-1: device not accepting address 5, error -71
[ 6272.216139] usb 3-1: new full speed USB device using uhci_hcd and address 6
[ 6272.336083] usb 3-1: device descriptor read/64, error -71
[ 6272.559951] usb 3-1: device descriptor read/64, error -71
[ 6272.775838] usb 3-1: new full speed USB device using uhci_hcd and address 7
[ 6272.895773] usb 3-1: device descriptor read/64, error -71
[ 6273.119653] usb 3-1: device descriptor read/64, error -71
[ 6273.335538] usb 3-1: new full speed USB device using uhci_hcd and address 8
[ 6273.743311] usb 3-1: device not accepting address 8, error -71
[ 6273.855268] usb 3-1: new full speed USB device using uhci_hcd and address 9
[ 6274.267035] usb 3-1: device not accepting address 9, error -71
[ 6327.438408] usb 4-1: new high speed USB device using ehci_hcd and address 8
Does anybody know how to solve this??

---

