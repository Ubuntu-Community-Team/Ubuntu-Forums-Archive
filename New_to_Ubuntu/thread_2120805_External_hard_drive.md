---
title: "External hard drive"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by macjim on 2013-02-27
Hello,
I'm new to Ubuntu and a Mac fan. I'm interested in trying out Ubuntu and I want to know how to install it on an external hard drive to run it from there. My worry is about the installation: I don't want to erase or damage my OSX in the process. Can anyone advice me on how to do this please.

---

### Post by Mark_in_Hollywood on 2013-02-28
Read here:

[http://askubuntu.com/questions/21383/install-ubuntu-or-kubuntu-on-a-external-usb-drive](http://askubuntu.com/questions/21383/install-ubuntu-or-kubuntu-on-a-external-usb-drive)

Here is a portion of that post. You didn't say which "ver." you have, so I cannot be more detailed than this. You should netsearch (I cannot use Google as a verb just yet) for, example: 12.04 if you have Precise Pangolin. Also, while you have a Mac you didn't say whether it's BIOS can boot from an external USB device, so I'm sorta in the dark to help you. Most modern BIOSs can boot from external USB devices.

Installing Ubuntu Linux to an External Drive

To start the process of running Ubuntu/Linux off of a external hard drive connected via USB then it's actually quite simple to do. Here are the steps, or rather, the steps I took.

Please Note: The following steps were tested using Ubuntu Version 9.10, but has not been tested with the later versions. Use at your own risk & discretion.

What You Will Need
A Computer with Internet access.
A LiveCD or LiveUSB with Ubuntu.
An external Hard Drive with USB capability.
What To Do
Open up your computer and remove the Hard Drive.

Plug in your external USB Hard Drive via the USB cable.

Stick in your LiveUSB or LiveCD and then boot up your PC.

Open up the boot menu, and choose to boot from the LiveCD/LiveUSB.

During the installation process you should your external hard drive listed, install Ubuntu to that.

Finish the installation process, turn off your PC, and put your other hard drive back into your computer.

Reboot your computer, go to the boot menu and select your external hard drive and attempt to boot from it. If it does congratulations, you now have an external hard drive with a full fledged Operating System on it.

Enjoy your external hard drive running Ubuntu/Linux! Please do let me know if this helps you! If not let me know about that too. :)

---

### Post by ozz_man on 2013-02-28
> 
[COLOR=#000000]Open up your computer and remove the Hard Drive.[/COLOR]

That's easier said than done on a MAC... :p

---

### Post by UltimateCat on 2013-03-01
Hi:;)

Here are a few other webpages that may help you-
[https://scottlinux.com/2010/06/26/mac-how-to-install-ubuntu-to-external-usb-hard-drive/](https://scottlinux.com/2010/06/26/mac-how-to-install-ubuntu-to-external-usb-hard-drive/)

For a Mac this is a good article:
[http://www.makeuseof.com/tag/5-alternativ-ways-install-ubuntu-linux/](http://www.makeuseof.com/tag/5-alternativ-ways-install-ubuntu-linux/)

And here's how to install Linux on a Mac if you want to dual boot.
[http://askubuntu.com/questions/151371/how-to-install-ubuntu-12-04-on-mac-os-x](http://askubuntu.com/questions/151371/how-to-install-ubuntu-12-04-on-mac-os-x)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

Good luck!:cool:

---

### Post by nwalkey on 2013-03-01
If you don't have osx installed to the external(I'd assume you don't" You may need to install rEFIt in osx to get it to recognize the external drive although I don't know  if that is relevant anymore(I had to do this back in 2008 to boot of external drives)

---

### Post by macjim on 2013-03-01
It was the latest version I was thinking about. The external drive would need formatting first but I'm not really wanting to take out my hard drive from inside the MacBook Pro. Is that the only way?
PS. it's very simple to get at my hard drive in the MacBook Pro as all I need to do is unscrew the base off it, but I really don't want to go through all the trouble just to try Ubuntu out. 
I thought Ubuntu could be run off a pen drive or an external HDD?

---

### Post by Mark_in_Hollywood on 2013-03-01
I believe the poster who suggested swapping drives was joking. You would have to ask him to know for sure. Since this is as yet, unresolved, please give me the type of Mac you have and want to try Ubuntu on. I'll need the G4 or G5 or PowerMac or whatever. If you have a pendrive (flash drive, jumpdrive or AKA thumbdrive) and Ubuntu is installed already on the external pendrive, if you can boot from a USB device, then you can try Ubuntu. I found this, as a way to try Ubuntu on a Mac, but with a pendrive.

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)

---

### Post by macjim on 2013-03-02
Ubuntu 12.10
macbook pro 15" 2.4ghz 750hd 8gb ram non retina version. OSXMountain Lion.

---

### Post by Mark_in_Hollywood on 2013-03-02
See if this is "it" for you FIRST:

"Maybe I'm missing something here, but the way I'm reading this, there's a very easy solution for you:

[Install Ubuntu on second drive.]("http://askubuntu.com/questions/229719/best-way-to-use-ubuntu-on-mac-pro-desktop-off-of-second-drive")

Power up your Mac Pro and immediately hold down the Option key. That invokes the Mac's built-in boot drive chooser. It will still boot the Mac OS by default, but you can arrow over to the "Windows" icon (why it's called "Windows" I don't know) and hit the enter key to boot directly into Ubuntu. You will still end up going thru Grub, but can take the default choice there.

Not quite as clean as I might like, but it works for me...

There are a lot of recommendations for rEFIt. I tried it, but it seems to be just another "layer" of software to go thru, so I removed it. Ditto with it's older predecessor rEFInd; I don't use either."

Have a look at the Ubuntu "Mactel" Support page and see if your Mac is compatible.

[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages) (I believe you are good to go, but best to double check).

I found a great "How To" at Lifehacker,

[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

but it requires your 750gig to be partitioned. And I know you don't want to do that. 

You maybe can find some better help at the hackintosh forum. See:

[http://www.tonymacx86.com/search.php?googleSearch=dual%20booting%20hard%20drives%20ubuntu](http://www.tonymacx86.com/search.php?googleSearch=dual%20booting%20hard%20drives%20ubuntu)

From [http://stackoverflow.com/questions/15039146/dual-booting-a-macbook-pro-osx-with-ubuntu-12-10](http://stackoverflow.com/questions/15039146/dual-booting-a-macbook-pro-osx-with-ubuntu-12-10)

and another that shows the EFI/UEFI in perspective about this dual-drive stuff:

[http://www.insanelymac.com/forum/topic/279935-questiondual-booting-windows-and-mac-osx/](http://www.insanelymac.com/forum/topic/279935-questiondual-booting-windows-and-mac-osx/)

This post, gets us a little closer. It shows how to setup a dual drive schema for Mac.

[http://www.insanelymac.com/forum/topic/278049-dual-boot-lion-and-ubuntu-1204-on-mbr-disk-with-chimera-installed/](http://www.insanelymac.com/forum/topic/278049-dual-boot-lion-and-ubuntu-1204-on-mbr-disk-with-chimera-installed/)

and this post, shows how to set up the dual drive for Windows, but it's got good graphical detail and both this and the one taken immediately above, should help you steer your coarse.

I wish this were much easier. I want to build a Hackintosh. I cannot ask questions at this Forum about that, cause the forum mods say it's illegal.

---

### Post by macjim on 2013-03-02
OK, thanks for all your advice and help.

---

