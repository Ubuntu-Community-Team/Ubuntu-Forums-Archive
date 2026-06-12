---
title: "[SOLVED] Netgear usb adapter"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by steve allen on 2008-05-12
OK I am trying to sort out a wireless connection using a netgear WG111v2 on 8.04hardy

In terminal lshw -C network showed that the driver was not installed.

How do I use ndiswrapper to install the netgear(windows)driver. In words of one syllable please, this command line stuff is all new to me.

I tried using wine to install the driver with no success.

Would I be better off just getting a different usb adapter which is ubuntu compatible, if so which one.

thanks in advance

regards

steve

---

### Post by hellomoto on 2008-05-12
hey, I'll give it a shot at giving you a hand. 

first a few things.

1, do you have your ubuntu CD to hand? and if so which version is it? _ we can use the CD to get ndiswrapper.

2. in a terminal please paste in here the output for the following command:

```


lsusb


```

--please make sure that you have your wifi usb stick in when you put in this command. Then we can move onto the next phase.

---

### Post by steve allen on 2008-05-13
Thanks Hellomoto

It is difficult to copy and paste as I'm using a different computer to get online.

The lsusb spots the wifi stick the problem is loading the driver I think

Have loaded ndiswrapper and I've found out that the windows 98 driver should work I have this driver in disc and also loaded into wine. 

What is the command in terminal to load the driver using ndiswrapper (ndisgtk) and how do I make sure that it loads the win98 driver instead of the ithers on the disc. In wine I deleted the other drivers only leaving the win98 one but can I find the driver from wine or is it better to use the cd

thanks again

regards
steve

---

### Post by Balachmar on 2008-05-18
Just to add to this, I am having the same problem.
Though I know this usb dongle worked fine in feisty.
That is why I have filed a bug at launchpad.
[https://bugs.launchpad.net/ubuntu/+bug/231662](https://bugs.launchpad.net/ubuntu/+bug/231662)
Any help is greatly appreciated. I do think that this should not be solved with ndiswrapper.

---

### Post by shifty_powers on 2008-05-18
whats wrong with using ndiswrapper?

---

### Post by steve allen on 2008-05-18
Sorry have neglected this thread whilst sorting other things.

Got the netgear usb adapter drivers loaded.

The secret seems to be to use the WIN98 drivers load to home and then use ndiswrapper to install.

Having said that I am still not connected wirelessly but hopefully I am one step closer

regards

steve

---

### Post by steve allen on 2008-05-18
Have just got the wireless sorted lord knows how!

---

### Post by Balachmar on 2008-05-21
> **shifty_powers said:**
> whats wrong with using ndiswrapper?

I feel that since most wifi cards are recognized out of the box, this one should as well.
Also if I am not mistaken, this worked previously, but not in hardy anymore.

---

### Post by mcgarry83 on 2008-06-03
I have the wg111v2 and it did work out of the box with Hardy, and I do get internet with it. However it continuously drops the connection. When it drops the network manager still shows that I am connected and signal strength is good, but no internet. The only way I have found to get it back is to unplug the adapter and plug it back in. I posted this on another thread.

---

### Post by reech on 2008-06-04
Same problem with dropped connections here - would also rather avoid ndiswrapper - if anyone else experiences this please add details to the bugreport : [https://bugs.launchpad.net/ubuntu/+bug/231662](https://bugs.launchpad.net/ubuntu/+bug/231662)

---

### Post by steve allen on 2008-06-06
After loading the edubuntu desktop and having trouble with that I reinstalled ubuntu hardy and managed to load the netgear usb driver with no problems at all using ndiswrapper and synaptic. IT is working fine have had no problem with it. I think the important thing is to make sure you use the windows 98 driver so be careful which drivers you upload from the cd rom.good luck all

regards steve

---

### Post by shifty_powers on 2008-06-06
glad to hear it all got sorted. and yes, ndiswrapper can be a godsend ;)

---

