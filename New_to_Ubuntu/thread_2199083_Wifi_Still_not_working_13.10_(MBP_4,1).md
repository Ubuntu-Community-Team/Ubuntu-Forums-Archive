---
title: "Wifi Still not working 13.10 (MBP 4,1)"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by brandonjsnyder on 2014-01-12
I am dual booting OS X 10.8 and Ubuntu 13.10. I can't seem to get the situation right to have wifi. I have tried so many different tutorials and follow alongs on you tube and nothing seems to work. I don't have a cat5 so can't create a wired connection. I've been moving things from computer to USB drive to computer. I've got a Broadcom 4321. I believe I've installed the driver and the firmware and rebooted but still get nothing. I'm really new to terminal so I don't really know what the scripts mean. Help!

---

### Post by joachim_altmann on 2014-01-12
Hi,
there are already a lot of threads about wifi, well beyond my level of knowledge, but maybe, if you can detail what you tried so far and where your probems with the command line are, I may assist you.

---

### Post by sandyd on 2014-01-12
Download [http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb) on another computer, and put on USB drive.

On the affected computer, double click the file on the USB drive and install.

---

### Post by brandonjsnyder on 2014-01-12
Thanks for the replies. Sandy I opened that file and clicked install and I got an error message that said "Dependancy not satisfiable: dkms" I have also installed the following packages

broadcom-wl-4.150.10.5.tar.bzd
firmware-b43-installer_4.150.10.5-4_all.deb
firmware-b43legacy-installer_015-9_all.deb
wl_apasta-3.130.20.0.o

I've also used sudo get-apt command with various installers but always get an error message.

---

### Post by sandyd on 2014-01-12
Forgot about that - install [http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb) first

---

### Post by joachim_altmann on 2014-01-12
You may install the dkms ([dynamic kernel module support]("https://help.ubuntu.com/community/DKMS")) via the software center, if this is what its need to install sandyd's package.

Maybe this page for the broadcom-card under PCI helps. Is the card running as a pci or as an USB-device? From a command line you may try "lspci" for the pci-bus, "lsusb" for the usb-bus or simply "lshw" to check your card.

---

