---
title: "How to install downloaded driver for Wlan"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by spaceman__ on 2008-11-21
I am complete new Ubuntu user, and have some problems using my Wlan hardware PCI card D-Link DWL-510. 
I have found and downloaded the driver on this address: "https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink"

But how do i install it??

---

### Post by drascus on 2008-11-21
Well one thing you are definitely going to need is Ndiswrapper. search for it under system -> administration -> Synaptic Packaging manager. then install all three packages ndisgtk the utils and the common. after that refer to this post: [http://ubuntuforums.org/showpost.php?p=4979569&postcount=2](http://ubuntuforums.org/showpost.php?p=4979569&postcount=2)

this is a difficult fix for a new person. So it might help if you get into direct contact with the person who made the post I refered you to. They maybe more then willing to walk you through all the steps. you can do that by clicking on their name in the post and then selecting send private message.

good luck 
I hope I put you on the right track.

---

### Post by muniak on 2008-11-21
Assuming you're using gnome... and remember to change [path] with the path to the directory your inf file is in.
```
gedit [path]/NET8180.INF
```

Now "replace all instances of 10ec with 1186 and all instances of 8180 with 3300 (only when it occurs next to 10ec -- 8180 is used to refer to the name of the chipset as well)."
Easiest way to do this is to Search > Replace enter "10ec" in the first and "1186" in the second... then the same with "8180" and "3300" except that you have to press find rather than replace at the bottom and only replace the ones that follow 10ec.

Quick how-to if you also don't know how to install ndisgtk:
Make sure [Menu] System > Administration > Software Sources, has the multiverse checked. Then in the terminal just type:
```
sudo apt-get install ndisgtk
```

Reference from here: [http://www.samwel.tk/bart/various/dwl-510-on-linux-2.6.html]("http://www.samwel.tk/bart/various/dwl-510-on-linux-2.6.html")

---

### Post by marshall.robert on 2008-11-21
> **drascus said:**
> Well one thing you are definitely going to need is Ndiswrapper. search for it under system -> administration -> Synaptic Packaging manager. then install all three packages ndisgtk the utils and the common.

even easier than that is to go Applications -> Add/Remove and then type ndiswrapper into the search box, wait a bit and tick the result and click apply.

but this will require internet, so if you can get yourself wired up, do so, if you cant then ill try a new approach...

---

