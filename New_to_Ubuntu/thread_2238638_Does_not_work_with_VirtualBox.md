---
title: "Does not work with VirtualBox"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by HelpifyouCan on 2014-08-09
**I am looking to test Ubuntu with VirtualBox.**

My computer work well with Windows XP, 2Gb mem, dual core Intel CPU.

After install (VirtualBox) Ubuntu 14.04.1 is unable to use Internet (unable to use Firefox). Live cd work (very slow) if you boot with DVD.

Try Ubuntu 10 ?. Unable to install under VirtualBox.

Can you help ?.

---

### Post by Vladlenin5000 on 2014-08-09
Hi, welcome.

If Ubuntu is the guest OS then it's a matter of configuring VirtualBox. Your question have little to nothing to do with Ubuntu.

---

### Post by The Cog on 2014-08-09
Try setting the virtualbox network settings to "NAT". Although in most places I have been "bridged" works nicely, bridged has its own MAC address and may not be able to use "secure" networks that implement MAC address filtering, require username/password to gain access, or only allow one MAC address on a network port.

I use 14.04 in virtualbox on windows7 regularly, so I know there is no fundamental problem with that arrangement.

---

### Post by mastablasta on 2014-08-09
you ram is a bit low. You should't give it more than 512 MB or maybe 768 MB because windows also needs ram to run itself and virtualbox. but hat kind of ram might not be enough for Ubuntu. for your setup i suggest you either use USB to boto into live session (DVD will be slow) or that you use Xubuntu which iwll work well with 512 MB ram in virtualbox. though might be still slow.

you never mentioned the GPU which would also have an impact if it is a poor one or not supported well and you run a livesession. Ubuntu actually needs quite modern hardware (and well supported GPU hardware) unless you know how to tweak it a bit.

---

### Post by SeijiSensei on 2014-08-09
Windows XP will happily run in 768MB of memory, so on a low-memory machine like yours I'd give the Ubuntu virtual machine at least 1280 MB.  

You probably also don't have the VB Expansion Pack installed which is pretty critical if you are using an operating system like Ubuntu that puts high demands on the graphics adapter. As others have suggested, you should try a more "lightweight" version of Ubuntu like Xubuntu or Lubuntu.

---

### Post by dave131 on 2014-08-09
I also noted a mention of 10.xx at the end of your opening post.  That is LONG out of support - I doubt you can get any updates, etc., for that anymore.  Better off using 12.04 or 14.04 BUT as mentioned use one of the "lighter" versions of Ubuntu - lubuntu would be a good choice since it is light all the way around, as well as xubuntu (which *if* I understand correctly is not "light" but does use the xfce desktop manager which is a lot "lighter").  Also, remember as SeijiSensei said to also install the extension pack.  I'm a newbie so hopefully someone will correct anything I might wrong.

---

### Post by Jonathan Precise on 2014-08-09
Xubuntu is light and is pretty mature. Lubuntu is lighter, yet has less time running, so there might be more bugs in Lubuntu than in Xubuntu.

VBox ext. pack: [http://download.virtualbox.org/virtualbox/4.3.14/Oracle_VM_VirtualBox_Extension_Pack-4.3.14-95030.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.14/Oracle_VM_VirtualBox_Extension_Pack-4.3.14-95030.vbox-extpack)

---

### Post by HelpifyouCan on 2014-08-12
**Thank you for all your answers **

**VirtualBox 4.3.12 works well with Windows ****XP.**

**I forget VirtualBox 4.3.14 malfunctioning. **

**Now I can test Ubuntu** 10, 14.

---

