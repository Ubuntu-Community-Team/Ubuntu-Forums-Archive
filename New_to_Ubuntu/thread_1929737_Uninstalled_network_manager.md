---
title: "Uninstalled network manager"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by cluelesswonder on 2012-02-22
I read another post about this (here: [http://ubuntuforums.org/showthread.php?t=1888715&highlight=uninstalled+network+manager](http://ubuntuforums.org/showthread.php?t=1888715&highlight=uninstalled+network+manager)) but I couldn't figure out the instructions. 

I was having a lot of problems with my wireless network connection dropping and being really slow upon installation of ubuntu 11.10 and followed instructions here to hopefully make it faster: [http://wiki.geteasypeasy.com/How_to_use_Wicd_instead_of_Network_Manager](http://wiki.geteasypeasy.com/How_to_use_Wicd_instead_of_Network_Manager)
. . .but it has disabled my wireless functioning entirely.
Probably should have read the discussion page first (>.<)

I don't know what to do to get my network up and running again.  I downloaded this: [https://launchpad.net/ubuntu/+source/network-manager](https://launchpad.net/ubuntu/+source/network-manager)
network manager package. . .put it on a USB and think maybe I could install is somehow? But I don't know how to do that. . .yet!

Please help if you can!

---

### Post by wolfen69 on 2012-02-22
Got to the bottom of [this]("http://packages.ubuntu.com/oneiric/network-manager") page and select 1386 (32bit) or AMD64 (64bit). And run it just by clicking it.

---

### Post by cluelesswonder on 2012-02-22
That you so much wolfen69 :)  We must have had telepathic communication or something because I actually found that and did it before I even got the message somehow!  I had to install network manager gnome as well but am communicating from my previously network-less computer :D
I still have 1 or 2 questions though.
1: The network is running off of wicd and wireless doesn't seem to be detected by the network manager. . .?  Is this a problem?
2: I can't download synaptic because of a "internet connection problem"  not sure why that is.
3: Is there a way to display the network connections in my tray?

Thanks so much for your help!!!

---

### Post by wolfen69 on 2012-02-22
> **cluelesswonder said:**
> 
1: The network is running off of wicd and wireless doesn't seem to be detected by the network manager. . .?  Is this a problem?
Yes and no. It's a problem in the sense that network manager won't see wireless, but as long as you can get online via wicd and stay connected, you are probably OK.

> 2: I can't download synaptic because of a "internet connection problem"  not sure why that is.
Try
```
sudo apt-get update
``` and then try to install synaptic.
> 3: Is there a way to display the network connections in my tray?
Try
```
unity --reset
```

---

### Post by cluelesswonder on 2012-02-22
Ok.  awesome!!

unity --reset made my system go crazy. I wasn't able to access the side panel and the tray was gone as well. . .but I rebooted and it seems to be fine now.  The wireless signal has also reappeared!  Thanks so much for your help! :D

---

