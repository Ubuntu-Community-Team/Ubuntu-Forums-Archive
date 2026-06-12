---
title: "Caught in a wifi web"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by nnjond on 2008-08-19
Hi,
I want to enable the wifi capability of this Laptop for when I travel as I use a landline at here.

I seem to have made things worse so far and think I should go back to the beginning as I'm quite confused.

May be this info will put you in the pcture:

nnjond@nnjond-laptop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



nnjond@nnjond-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)

nnjond@nnjond-laptop:~$ sudo make install

[sudo] password for nnjond: 

make: *** No rule to make target `install'. Stop.

nnjond@nnjond-laptop:~$

---

### Post by finer recliner on 2008-08-19
> **nnjond said:**
> 
nnjond@nnjond-laptop:~$ sudo make install

[sudo] password for nnjond: 

make: *** No rule to make target `install'. Stop.

nnjond@nnjond-laptop:~$

you didn't mention what you are trying to install.

also, when installing an application from the source code, you usually need to run the configure script first, then compile it by running 'make', then run 'make install'. here's an example:

```

$ ./configure
$ make
$ sudo make install

```

(this format is not true for all installations from source, but it is common for most)

---

### Post by nnjond on 2008-08-19
Thanks for your interest. I don't know what i need to install. i just want the wifi to work.

---

### Post by finer recliner on 2008-08-19
It looks like ubuntu 8.04 sometimes misdetects this wifi card. please boot into windows to determine if you really have a "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter" and not something else.

see this thread for more info:
[http://ph.ubuntuforums.com/showthread.php?t=766018](http://ph.ubuntuforums.com/showthread.php?t=766018)

---

### Post by nnjond on 2008-08-19
I've Ubuntued over MS; but the wifi did work ok in that os.


"That particular card has various names.

The actual card is called the AR5007EG, however in gutsy gibbon ubuntu it was called the AR5006EG, now under hardy heron it is called the AR242x

They're actually the same card...strange but true"

---

