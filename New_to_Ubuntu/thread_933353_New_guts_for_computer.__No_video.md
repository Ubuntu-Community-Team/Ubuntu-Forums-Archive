---
title: "New guts for computer.  No video"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by grewolf on 2008-09-29
Hello my mother board croaked so I had to get new internals for my computer.  I have an Asus M3A mother board with a AMD dual core processor 5200 I think with a GeForce 9500 GT video card (PCI-E) manufactuted by EVGA.  I have Ubuntu Gutsy gibbon loaded on an IDE drive.  I think this link is what I need.  
[/URL]http://ubuntuforums.org/showthread.php?p=5825911&highlight=GeForce+9500+GT#post5825911[/URL]

I only have CLI when I boot into Ubuntu and not sure how to download the driver that way or how to install. I get a pci error when I am loading Ubuntu.  Will have to edit this message when I get back to my computer.  Had to borrow friends to post

---

### Post by Delvien on 2008-09-29
Have you attempted to install the Nvidia-glx-new packages?

---

### Post by LowSky on 2008-09-29
> **grewolf said:**
> I only have CLI when I boot into Ubuntu and not sure how to download the driver that way or how to install. I get a pci error when I am loading Ubuntu.  Will have to edit this message when I get back to my computer.  Had to borrow friends to post

At CLI log on then type

```
startx
```
that should get you to a GUI, if not at GRUB boot into recovery mode. and resetup Xorg

---

### Post by grewolf on 2008-09-29
> **Delvien said:**
> Have you attempted to install the Nvidia-glx-new packages?

How do I do this?  If I can get the GUI to work I will try this through synaptic.  I will try the suggestion of startx in the CLI

---

### Post by LowSky on 2008-09-29
New Nvidia Drivers can also be installed through the use of Envy (which is in the repos as well

---

### Post by grewolf on 2008-09-29
> **LowSky said:**
> At CLI log on then type

```
startx
```
that should get you to a GUI, if not at GRUB boot into recovery mode. and resetup Xorg

I get a fatal I/O error 104 no screens detected.  How do I reset up Xorg from the command line.  I have limited knowledge of command line.  I have bought an new drive and had to install XP and now switch back and forth between booting drives to see these posts.  Is there a way from the CLI to install these nvidia drivers.  I know sudo apt-get update to reload but not how to actually get the packages.

---

### Post by erickghint on 2008-09-29
Honestly I would recommend that you install the beta drivers from nVidia. [www.nvidia.com.drivers](www.nvidia.com.drivers)  . 

   It's pretty simple. Go to your login screen and press ctrl+alt+f1 to get to the command line. Then :

```
sudo apt-get install build-essential
```

```
 sudo /etc/init.d/gdm stop 
``` 
This will shut down your GDM. From there navigate to the folder you saved the driver in, and run it, like this:

```
sudo sh (name of file - example - NVIDIA-Linux-x86-177.16.pkg1.run)
```

Next, you're going to need to edit your restricted modules, so the driver stays in place. To do this:

```
sudo nano /etc/default/linux-restricted-modules-common
```

There are a pair of quotes at the end of the document, just put nv in the quotes.

```
 DISABLED MODULES = "nv"
```

 Next restart your GDM and have fun. 

```
 sudo /etc/init.d/gdm start 
```

---

### Post by JoshuaRL on 2008-09-29
Okay, try this from the recovery mode:
```

apt-get install nvidia-glx-new

```
See if that helps.

---

### Post by kansasnoob on 2008-09-29
This is probably really dumb, but did your new MOBO come with a BIOS disc? All newer boards do that I've ordered.

If so did you reconfigure BIOS with the new BIOS disc?

Don't shoot me! Sometimes I can be dense!

---

### Post by grewolf on 2008-09-29
> **erickghint said:**
> Honestly I would recommend that you install the beta drivers from nVidia. [www.nvidia.com.drivers](www.nvidia.com.drivers)

How do I download this from the command line?

I have done this and it has installed
```
apt-get install nvidia-glx-new
``` 

I have tried ```
startx
``` and I get this error 

```
PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Kinit: name_to_dev_t (/dev/disk/by-uuid/7bed3f20-2e63-43f4-9abb-0472f3661c27) = hda 5(3,5)
Kinit :No resume image
       doing normal boot
(==) log file:"/var/lag/xorg-o.log"
(==) using config file "etc/x11/xorg.conf
(EE) No devices detected

Fatal Server Error:
No screens found

XIO: fatal IO Error 104(connection reset by peer) on X server ":0.0"
```

---

### Post by grewolf on 2008-09-29
> **kansasnoob said:**
> This is probably really dumb, but did your new MOBO come with a BIOS disc? All newer boards do that I've ordered.

If so did you reconfigure BIOS with the new BIOS disc?

Don't shoot me! Sometimes I can be dense!

I'm not sure what you mean by reconfigure.  I've gone into the bios and changed boot items.  I have not changed anything else though.

---

### Post by LowSky on 2008-09-29
> **grewolf said:**
> I'm not sure what you mean by reconfigure.  I've gone into the bios and changed boot items.  I have not changed anything else though.

Does the board have onboard video? make sure you  have turned it off or set the board for PCIe only

---

### Post by grewolf on 2008-09-29
> **LowSky said:**
> Does the board have onboard video? make sure you  have turned it off or set the board for PCIe only

Sorry no onboard video and set to pci-e

and at the bottom of page 1 I have posted the error messages I have recieved

---

### Post by kansasnoob on 2008-09-29
> **grewolf said:**
> I'm not sure what you mean by reconfigure.  I've gone into the bios and changed boot items.  I have not changed anything else though.

Did you just run the defaults on the disc?

---

### Post by kansasnoob on 2008-09-29
I see that motherboard is very compatible:

[http://ubuntuhcl.org/browse/product?id=524](http://ubuntuhcl.org/browse/product?id=524)

But not so much with the video card. In fact NOT AT ALL with that video card!

---

### Post by grewolf on 2008-10-10
> **kansasnoob said:**
> I see that motherboard is very compatible:

[http://ubuntuhcl.org/browse/product?id=524](http://ubuntuhcl.org/browse/product?id=524)

But not so much with the video card. In fact NOT AT ALL with that video card!

I found a link stating that they were able to gety it to work on hardy 64 bit.  Would I be able to do something like this for gutsy?

Here is the link.  [HTML]http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4035118&Sku=E145-9500[/HTML]


here is the review
REVIEW BY: Ath Reviewed  Oct 01, 2008 	
This works well with Ubuntu Linux 8.04 (I am using 64 bit, don't know how it works with 32 bit.) I am not a gamer but I do some video work and gimp and the card works well for what I use it for. Right now the card is not auto detected but just install envyng-gtk and let it install Nvidia driver 173.14.12 and then you are set to go. Thanks Tigerdirect!!!

---

