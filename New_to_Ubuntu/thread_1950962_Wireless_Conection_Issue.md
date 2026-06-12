---
title: "Wireless Conection Issue"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Capt Sam on 2012-04-01
I have an older computer that I've decided to install Ubuntu on.  So I downloaded the ubuntu file and burned it onto an installation disk.

This computer did not have an internet connection, so I didn't get some additional stuff.  Fine, I'll get it later.  But this brings up a good point that has utterly confused me:

How am I supposed to connect online before Ubuntu even is installed?  There is no other OS on this computer.  And how am I supposed to find the correct driver to make the wireless card work if I can't even get online to download it?

I know what kind of wireless card I have (Broadcom BCM4318 ), and it is supported, but I have no idea how to turn it on, or even if the OS knows that it is there.

Can anyone here point me in the right direction?

---

### Post by roger_1960 on 2012-04-01
Hi

When you boot from the live disk you can install or "try".  If you "try" it should run Ubuntu without installing it and allow you to check that everything works, including the wifi.  Its a good idea to do this.

From searching for it in these forums, your BCM4318 probably needs to have the package firmware-b43-installer installed.  I believe its possible to install this from the ubuntu disk if you can't get online.  Does your PC have an ethernet wired port? If not, once Ubuntu is installed, in the software center, you can edit the software sources to include the Ubuntu CD you installed from.  The package is included (at least in 11.10)

---

### Post by Capt Sam on 2012-04-01
So you are suggesting that the firmware-b43-installer in somewhere on the install disk?  I'm looking at the contents of the disk, do you know where it might be?

Well I found something that might be what I need, so I can downloaded it and transfer it to my computer w/Ubuntu?  Is it like an installer that automatically updates?  This is all so very different from what I am used to.

[https://launchpad.net/ubuntu/oneiric/i386/firmware-b43-installer/1:014-9ubuntu0.1](https://launchpad.net/ubuntu/oneiric/i386/firmware-b43-installer/1:014-9ubuntu0.1)

---

### Post by Starcruiser322 on 2012-04-01
> **Capt Sam said:**
> Well I found something that might be what I need, so I can downloaded it and transfer it to my computer w/Ubuntu?  Is it like an installer that automatically updates?  This is all so very different from what I am used to.

[https://launchpad.net/ubuntu/oneiric/i386/firmware-b43-installer/1:014-9ubuntu0.1](https://launchpad.net/ubuntu/oneiric/i386/firmware-b43-installer/1:014-9ubuntu0.1)
Once you download the [firmware-b43-installer_014-9ubuntu0.1_all.deb]("http://launchpadlibrarian.net/93153681/firmware-b43-installer_014-9ubuntu0.1_all.deb")                   (3.2 KiB) file, you should be able to double click it and it will open your Ubuntu Software Center asking if you want to install it. 
However, it will most likely still need to be connected to the Internet, so if there is a way to get a wired connection it would be a lot easier than compiling from source code.

---

### Post by westie457 on 2012-04-01
It is possible to install 'b43-fwcutter' from the media you you did your ubuntu installation from.

The steps are 

1, Boot your system normally

2, Put your install CD in the tray or plug in your USB stick

3, Open the File-browser (nautilus)

4, In the left pane locate the CD/USB and click on it.

5, Navigate your way to /pool/main/b/b43-cutter. Double-click the b43*.deb file and it should install.


These instructions work in Ubuntu, they should also work in Kubuntu and others.

---

### Post by wildmanne39 on 2012-04-01
Hi, Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by Capt Sam on 2012-04-01
I found it.  Very strange when I try to open it in the software center.  It shows it as a patch, but the "install" button will not highlight or press.

---

### Post by wildmanne39 on 2012-04-01
Hi, if it is a patch then that is not what you need if you follow my directions in my previous post you should get it working.

You already have ubuntu installed correct?
Thanks

---

### Post by Capt Sam on 2012-04-01
> **wildmanne39 said:**
> Hi, if it is a patch then that is not what you need if you follow my directions in my previous post you should get it working.

You already have ubuntu installed correct?
Thanks

Yes Ubuntu is installed.

Thank you so much (and everyone else) that helped.  It worked.

---

### Post by wildmanne39 on 2012-04-01
Hi, your welcome! Glad I could help.

---

