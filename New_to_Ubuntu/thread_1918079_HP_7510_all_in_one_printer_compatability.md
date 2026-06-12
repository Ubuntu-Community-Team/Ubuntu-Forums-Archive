---
title: "HP 7510 all in one printer compatability"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by a.v.l on 2012-01-31
Does the HP 7510 all-in-one printer work with all versions of Ubuntu?

---

### Post by mikechant on 2012-01-31
According to HP (search for 7510 in the following document)
[http://hplipopensource.com/hplip-web/supported_devices/combined.html](http://hplipopensource.com/hplip-web/supported_devices/combined.html)

This printer is fully supported by the 'hplip' HP Linux printer driver package.

However, you need version 3.11.10 of hplip and no currently released version of Ubuntu ships with this by default (Ubuntu 11.10 ships with hplip 3.11.7).

So you will need to upgrade hplip.

The best way is probably to use the following instructions to add a ppa (personal package archive); this will then let you upgrade hplip using the normal package tools such as synaptic:
[http://ubuntu-tweak.com/source/hplip-isv-ppa/](http://ubuntu-tweak.com/source/hplip-isv-ppa/)

note this bit particularly:
> You can easily enable this PPA by the following command:

sudo add-apt-repository ppa:hplip-isv/ppa

Once you've added the ppa the hplip upgrade should become available for installation in the same way as other routine package upgrades do.

If this is not suitable for you, the following page tells you how to upgrade hplip manually in Ubuntu 11.10 64 bit:
[http://linuxforums.org.uk/index.php?topic=9712.0](http://linuxforums.org.uk/index.php?topic=9712.0)

As far as I can see:
1/ These instructions should probably work for any recent 64-bit Ubuntu version
2/ For 32 bit Ubuntu you will probably find the instructions will work if you miss out steps 3&4

Note I haven't tried any of this myself (my HP printer is ancient and works with the supplied versions of hplip).

---

### Post by a.v.l on 2012-01-31
If instead I installed the printer software on a Windows 7 laptop, would my other linux computers be able to use the printer wirelessly without upgrading their own HP printer setting on each of these linux machines?

---

### Post by Double.J on 2012-01-31
> **a.v.l said:**
> If instead I installed the printer software on a Windows 7 laptop, would my other linux computers be able to use the printer wirelessly without upgrading their own HP printer setting on each of these linux machines?

You can share a printer on the network, but this requires that the host system be on every time you want to print...and puts windows 7 incharge of the network :/ Personally I'd just do as mikechant suggests - add the repo, update the driver - it'll take 5 mins :)

---

### Post by Bucky Ball on 2012-01-31
> **a.v.l said:**
> If instead I installed the printer software on a Windows 7 laptop, would my other linux computers be able to use the printer wirelessly without upgrading their own HP printer setting on each of these linux machines?

No. You would still need HPLip on the Linux boxes. Installing it is easy with the PPA (it is easy manually through a terminal also following HP's own instructions).

Incidentally, using the Linux boxes wirelessly to connect wirelessly has nothing to do with whether the Windows box is on, connected, or exists. If you have a router, setup the HP with a static IP address as explained in the documentation then setup your boxes to connect to it via the (wireless) router.

Once you have the printer recognised wirelessly by the wireless router, the recent HPLip installed on the Linux boxes, you should be able to search for the printer in 'Printers' in Ubuntu and the HP will pop up as a 'Network Printer' and it is a cinch from there.

---

### Post by a.v.l on 2012-02-04
Thanks everyone for the advice, just updating Ubuntu before proceeding. One thing I've noticed is the latest HPLIP version is 3.11.12. I take it this is ok to go with for the HP 7510 printer?


> **mikechant said:**
> According to HP (search for 7510 in the following document)
[http://hplipopensource.com/hplip-web/supported_devices/combined.html](http://hplipopensource.com/hplip-web/supported_devices/combined.html)

This printer is fully supported by the 'hplip' HP Linux printer driver package.

However, you need version 3.11.10 of hplip and no currently released version of Ubuntu ships with this by default (Ubuntu 11.10 ships with hplip 3.11.7).

So you will need to upgrade hplip.

The best way is probably to use the following instructions to add a ppa (personal package archive); this will then let you upgrade hplip using the normal package tools such as synaptic:
[http://ubuntu-tweak.com/source/hplip-isv-ppa/](http://ubuntu-tweak.com/source/hplip-isv-ppa/)

note this bit particularly:


Once you've added the ppa the hplip upgrade should become available for installation in the same way as other routine package upgrades do.

If this is not suitable for you, the following page tells you how to upgrade hplip manually in Ubuntu 11.10 64 bit:
[http://linuxforums.org.uk/index.php?topic=9712.0](http://linuxforums.org.uk/index.php?topic=9712.0)

As far as I can see:
1/ These instructions should probably work for any recent 64-bit Ubuntu version
2/ For 32 bit Ubuntu you will probably find the instructions will work if you miss out steps 3&4

Note I haven't tried any of this myself (my HP printer is ancient and works with the supplied versions of hplip).

---

### Post by a.v.l on 2012-02-08
The HP 7510 does work in Ubuntu 11.10 - I upgraded HPlip to version 3.12.2 first. You can find the download and how to install it in the following link.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Now, I'm able to wirelessly print from a linux desktop, a Windows 7 laptop and an HP touchpad. I'm also able to scan, and copy. From this next link, it appeared that faxing is not supported in Ubuntu, but I have been able to set up a fax account on this printer which registered and returned a message giving me a personal fax number. Haven't tried sending a fax with it yet.

[http://hplipopensource.com/hplip-web/supported_devices/photosmart.html](http://hplipopensource.com/hplip-web/supported_devices/photosmart.html)

Many thanks for your help.

---

### Post by stong98 on 2012-02-29
> **a.v.l said:**
> 
Now, I'm able to wirelessly print from a linux desktop

Sorry to dig up this old thread, but can you expand on your capability of wireless printing in Linux?  I have been able to print wireless in Windows without any issues, but after going through the process updating hplip on my linux box I have been unable to complete the setup for wireless.  When running hp-setup and selecting a network printer, it continuously tells me that a printer is not plugged in (even though it is).  If I select USB, it recognizes my printer, but I don't want to keep it plugged in so I have not completed that portion of setup.  

> **a.v.l said:**
> 
[http://hplipopensource.com/hplip-web/supported_devices/photosmart.html](http://hplipopensource.com/hplip-web/supported_devices/photosmart.html)

According to the link you posted here it does not appear that network printing is supported in Linux.  Were you able to complete the wireless portion of the setup, or did you simply set it up as a USB printer?

Thanks for the help,
Ryan

---

### Post by Bucky Ball on 2012-02-29
Have three computers printing wirelessly here. Is your printer already setup up and transmitting an IP address so it works fine in Windows and can be seen by the router (are you using one)??? Then:

Go to 'Printing' (under 'System' I think) in Ubuntu and hit the + sign to add a printer;
Click on 'Network Printer' and wait awhile.

Does your HP pop up (give this some time)?

---

### Post by stong98 on 2012-02-29
> **Bucky Ball said:**
> 
Go to 'Printing' (under 'System' I think) in Ubuntu and hit the + sign to add a printer;
Click on 'Network Printer' and wait awhile.

Does your HP pop up (give this some time)?

This seems to work; I think I was hoping for better support for the printers features - like being able to see the ink levels and setting print options like duplex printing.  I don't see any way to configure that from the printers dialog, is there another place to configure these type of options?

Thanks.

---

### Post by Bucky Ball on 2012-02-29
> **stong98 said:**
> This seems to work; I think I was hoping for better support for the printers features - like being able to see the ink levels and setting print options like duplex printing.  I don't see any way to configure that from the printers dialog, is there another place to configure these type of options?

Thanks.

Yea, you set duplex when you print something. All depends what software you are printing from. 

Or, right click the printer you are using in 'Printing' and select 'Properties'. in the left hand pane you can see print/toner levels and set just about anything you want on the printer.

---

