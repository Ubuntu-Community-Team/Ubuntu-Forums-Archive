---
title: "Wireless prob + Ipod 6th Gen with Amarok prob + hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by stueau on 2008-04-26
Hey, I've just upgraded to Hardy (ubuntu) from Gutsy via a clean install and are having 2 problem.

First the wireless: worked perfectly with Gutsy, but now refuses to connect to my home network. The wireless card finds the network (+the neighbour's aswell) and shows good signal and also asks for the WEP key when trying to connect. However, when putting in the WEP key nothing happens for a while, then I'm prompted for the key again. The network icon looks like it's working, but hen the pointer is hovered over it the message "Waiting for network key" comes up... It all seems a bit weird. Wireless card is Broadcom B43 (with restricted drivers enabled and "in use". Any suggestion very much appreciated.

Second: I installed Hardy mainly because of the Ipod 6th gen support with gtkpod. Good news is, after plugging in the ipod and playing a track off it, my ipod no longer says there is no music. However, I'm having problems getting Amarok to work properly. Thought changing the mount point to something without a space in it would work, but now I've done that wrong and the ipod no longer mounts and tells me "mount_point cannot contain the following characters...etc". I tried to change the mount point to /media/ipod but i think I've messed it up royally.


Sorry for the convoluted post... thought I'd try and give you as much detail as possible...

Thanks for any help!

[EDIT: The second problem is solved. It seems to be a common problem because of the slightly confusing nature of changing the mount point by right-clicing the device and going through the menus. Easy way to solve it is to log in as a different user, remount the ipod/device the log back in as yourself, and then change the mount point.... Still nowhere with the wireless problem though!]

---

### Post by chogoria on 2008-04-26
I'm having exactly the same wireless problems. Please help us!

---

### Post by stueau on 2008-04-26
I'm being slightly cheeky and replying to put this back near the top of the forum posts....

Is this problem with NDISwrapper? I'm assuming that if System->Administration->Hardware drivers shows the card enabled, plus the fact that the card is picking up wireless networks that this isn't the problem...

---

### Post by stueau on 2008-04-26
It seems a few people are having this problem (although with a different wireless card): [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/221970](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/221970)

---

### Post by stueau on 2008-04-26
I'm sort of half solving these problems... found that when trying to change the mount point of the ipod I entered '/media/ipod' for the Mount Point, when in fact all that was needed was 'ipod'... Slightly frustrating since I thought this was pretty misleading... 

Anyway, is there any way to revert the mount point? Or is this something that will require an entire system reinstall?

Any help out there?

---

### Post by chogoria on 2008-04-27
stueau, I've solved my problem. I really don't believe how stupid I've been. After following a few guides online that basically tell me the same thing, I was using the wrong encryption type when connecting to my router. The automatic setting in Ubuntu is "WEP 128 bit" encryption but my router is configured to use "WEP 64 bit" (feel free to laugh at me - I never had any experience in Linux until 4 days ago). Hopefully this will work for you. (My wireless card is a Broadcom 4318 Air Force One and I'm using a BT Home Hub). That guide I was using can be found [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

At least I'm now connected, but it says my wifi speed is 1 Mb/s. How do I up this to 54 Mb/s? Can anyone help?

---

### Post by stueau on 2008-04-28
I've managed to solve my problem aswell... I uninstalled the restricted drivers and then installed the windows driver via ndiswrapperusing [this guide]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html"). After resetting my router, it's started working.

Is this a common problem with Hardy?... Anyway, aslong as it's working I don't mind.

---

