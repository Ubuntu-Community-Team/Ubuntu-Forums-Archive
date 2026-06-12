---
title: "modifying ubuntu live iso ?"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by zebi on 2014-04-06
hi  i use ubuntu liveusd and i would like to install grsecurity on it, is it possible to add it on an ubunto live iso so i couuld run a hardened ubuntu?  thanks

---

### Post by Double.J on 2014-04-06
Hi there!

Welcome to the forums!

The live USB's format their partition with a file system called squash file system, or squashfs.  There is a good reason for this - it's compressed so all the necessary packages required for install and live operation across a huge array of hardware can be put onto relatively small USB sticks. (2GB)

The downside to this is that the data stored on the squashs is an image of ubuntu - a complete system frozen in time, compacted down onto the stick. this means that you can't modify it whilst running and restart - squashfs is read only. What actually happens when you run from a live USB is that EVERYTHING you download, create, and do is stored in RAM, not saved. for this reason a live USB will often automatically mount a swap partition (swapon) if it finds one on an internal drive to reduce the risk of system crashes, but at the end of the day no data will be saved unless you mount another partition and put it there.

What you can do is when creating the live USB through a tool such as [usb creator]("https://help.ubuntu.com/community/Installation/FromUSBStick") (ubuntu) or [pendrive linux]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") (windows), you can add a persistence image to the USB that is not compressed and will remember all the things you do - such as add more packages. obviously this is not compressed or encrypted and will take up more space, also usual filesystem rules apply - as the persistence fills up, so performance will reduce. You can also set up a persistence on the internal HDD of the machine you want to use with the live install. More information on persistence is available through the [Wiki]("https://help.ubuntu.com/community/LiveCD/Persistence")

If you still want a liveUSB that is reset at every boot, but with customised applications available, you need to edit the original ubuntu insallter .iso you downloaded to put on the USB. This can be done with the [Ubuntu Customisation Kit]("https://help.ubuntu.com/community/LiveCDCustomization"). It will basically edit the packages available in the liveUSB then compact it back up into an ISO to be burnt to flash.

In the past you could also create a liveUSB instance (still compacted and read only) with remastersys. However I have not attempted this in quite a long time and a look on their downloads page suggests that there hasn't been an update to this project in over 18 months, so I would not recommend it unless some has more accurate information?

Finally you can actually install Ubuntu direct to a USB flash drive. this means that ubuntu will preform exactly as it does installed to your hard drive (although much slower; don't forget that USB sticks are slower than hard drives!! Also over time all the extra writes will shorten the life of your USB stick) To do this you just use the installer as you normally would, just making sure that you put EVERYTHING on the USB. When I have done this, I've actually disconnected my HDD from he computer before running the installer. This protects your data from user error, but also stops the installer using the HDD's swap partition, or MBR. Obviously for this you would need two USB's or one DVD and a USB - the USB you want to install on, and the installer itself.

Hope it helps!!

Jj

---

