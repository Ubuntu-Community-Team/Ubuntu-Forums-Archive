---
title: "nVidia help."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by parkar on 2008-04-27
Ok so I'm just having a terrible time getting things up and running. I have an e1705 Dell Laptop with a 7900 GS vid card. 

I finally got WIFI to work in Ubuntu Hardy which put so much more faith back into me but now not getting my video card drivers to work really sucks. Basically, I have tried a couple tutorials but they are outdated. I don't have the "Restricted Drivers Manager" in 8.04 making all the instructions hard to follow.

So can anyone help me out here with this. I just want this to be installed!! Thank you so much.

---

### Post by Perfect Storm on 2008-04-27
It's now called "Hardware drivers". Give it a try.

---

### Post by parkar on 2008-04-27
Right I see that but it just shows nvidia_new.

It's enabled but it's not properly supported. Not to mention whenever I use Synaptics and attempt to download the most recent updates I get a connection error. This happened with my wired and wireless connection...not sure whats going on with that.

Anyways, I know that can't be the right driver. I can't even enable the 'extra' special effects to be enabled.

Like really, I just want this to work but I don't want to give up either.

---

### Post by Perfect Storm on 2008-04-27
which card do you have? You should be able to install nvidia-glx-new (nvidia driver 169.12)

is it only now you have trouble connecting with synaptic (only 8.04). If so it may be because people went frenzy with downloading/upgrading because of the new release which have stampeded the servers well.

---

### Post by parkar on 2008-04-27
I have the Geforce GO 7900 GS 

The nvidia-glx-new has a ton of pre-reqs that I don't have installed and I'm not sure why that is either...like unless my install went wrong but everything else seems fine.

---

### Post by Perfect Storm on 2008-04-27
But by installing the driver from nvidia, you need to uninstall restricted drivers which you'll may loose wireless connection.


Anyway.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common
sudo apt-get install build-essential xserver-xorg-dev
```

and remember that when the kernel gets updated you'll need to go to CLI and reinstall the nvidia driver.

---

### Post by rubenverweij on 2008-04-27
I have Hardy too, and I got my nVidia GeForce 6200 card working by installing nvidia-glx and nvidia-settings. With the nvidia-settings, you can configure your card and monitor graphically. I hope it works for you as well as it worked for me!

---

### Post by parkar on 2008-04-27
I should've probably mentioned that this is a fresh install of Hardy so there aren't any other drivers than what come stock. I will give what you've said a try and see what happens.

---

### Post by Perfect Storm on 2008-04-27
...and ofcause the standard: **build-essential** is needed as well.

---

### Post by Ub1476 on 2008-04-27
I have nvidia 7900 gs as well and can assure you that checking the driver in Hardware Drivers and rebooting worked like a treat.

```
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
```

---

### Post by parkar on 2008-04-27
^ So are you using the driver that came with Ubuntu or what? I still would like to be able to update it though...I'm going to try and get nvidia-glx working. :)

So right now it's also saying that nvidia_new is enabled but the Status is : Not in Use...not sure what that means.

---

### Post by parkar on 2008-04-28
So the solution to my problem was re-install Ubuntu and when I turned Ubuntu on for the first time I had a wired connection ready to go. This allowed it to find the newest drivers right away and install them and everything worked. 

So it's been a good night for me and linux.

---

