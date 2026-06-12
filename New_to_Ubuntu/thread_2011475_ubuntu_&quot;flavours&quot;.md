---
title: "ubuntu &quot;flavours&quot;"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by godfreezone on 2012-06-27
Couple of questions:
1. If I am running ubuntu, do things like KDE gnome Xubuntu have anything to do with me?
2. I  have a version of Linux Mint on a DVD; can i safely wack it in the DVD drive and try it without risking cataclysmic reprocussions in my newly stable, windows-free!!! ubuntu environment

thx
Godfree

---

### Post by Frogs Hair on 2012-06-27
I have tried all the Ubuntu flavors , but came back to Ubuntu with a mix of desktop environments . I currently run Unity the Gnome Shell, and E17 on 12.04. All the flavors have appeal to different users for different reasons. I may try Kubuntu again in the future .[http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce/](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce/)

Mint is Ubuntu based and shouldn't cause problems if you follow the instructions.

---

### Post by cortman on 2012-06-27
> **godfreezone said:**
> Couple of questions:
1. If I am running ubuntu, do things like KDE gnome Xubuntu have anything to do with me?
2. I  have a version of Linux Mint on a DVD; can i safely wack it in the DVD drive and try it without risking cataclysmic reprocussions in my newly stable, windows-free!!! ubuntu environment

thx
Godfree

1. KDE and XFCE (the desktop environment that Xubuntu uses) are separate desktop environments. If you're using stock Ubuntu you're using Unity, which is based on the Gnome DE.
2. Yes, use VirtualBox.

```
sudo apt-get install virtualbox
```

Or else just boot from the live CD.

---

### Post by philinux on 2012-06-27
> **godfreezone said:**
> Couple of questions:
1. If I am running ubuntu, do things like KDE gnome Xubuntu have anything to do with me?
2. I  have a version of Linux Mint on a DVD; can i safely wack it in the DVD drive and try it without risking cataclysmic reprocussions in my newly stable, windows-free!!! ubuntu environment

thx
Godfree

1. not unless you want to try a different desktop environment. And it can get messy with more than one installed. 

2. Try without installing does not mess with your install.

---

### Post by Megaptera on 2012-06-27
> **godfreezone said:**
> Couple of questions:
1. If I am running ubuntu, do things like KDE gnome Xubuntu have anything to do with me?
2. I  have a version of Linux Mint on a DVD; can i safely wack it in the DVD drive and try it without risking cataclysmic reprocussions in my newly stable, windows-free!!! ubuntu environment

thx
Godfree

A good explanation of Kubuntu, Xubuntu etc here: [http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

I like your caution I used to worry about live CDs/DVDs but as long as you don't click 'Install' they are fun and harmless :p

---

### Post by mastablasta on 2012-06-27
live media (CD/DVD/USB) loads the whole system into ram on boot. ther eis persistance option on USB (where poriton of USB device can be used to save some settings) however even persistance has no effect on the installed operating system. Since it is all in RAM once oyu turn it off all changes are lost (except if you use persistant USB stick in which case the are saved to dedicated part of USB stick)

---

### Post by godfreezone on 2012-06-27
thx guys for the help;
tried virtualmachine only to discover that I had not burnt disc properly from my last windows machine; will have to wait till next data cycle to afford another d.load, when i will start to experiment using virtualmachine, "to my heart's content"

Godfrey

---

### Post by cortman on 2012-06-28
> **godfreezone said:**
> thx guys for the help;
tried virtualmachine only to discover that I had not burnt disc properly from my last windows machine; will have to wait till next data cycle to afford another d.load, when i will start to experiment using virtualmachine, "to my heart's content"

Godfrey

You don't need to burn a CD for virtualbox; you can boot directly from the ISO. Simply click "Devices>CD/DVD Devices>Choose a Virtual CD/DVD disk file..." and find the downloaded ISO image. The virtual machine will first boot from it.

---

### Post by godfreezone on 2012-06-28
Thanks man for taking time to respond.
The thing is, which i didn't explain well, I hadn't correctly burnt an iso image to my old windows system, hence the disk i had made from that (faulty) operation was itself faulty.
So, when i loaded disk in new ubuntu machine running VM, nothing happened: just got a mint screen, perfect, but no options to do anything.

Godfree


> **cortman said:**
> You don't need to burn a CD for virtualbox; you can boot directly from the ISO. Simply click "Devices>CD/DVD Devices>Choose a Virtual CD/DVD disk file..." and find the downloaded ISO image. The virtual machine will first boot from it.

---

