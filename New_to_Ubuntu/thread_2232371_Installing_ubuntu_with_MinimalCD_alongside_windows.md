---
title: "Installing ubuntu with MinimalCD alongside windows"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by mweyler24 on 2014-07-01
I am trying to Istall ubuntu alongside windows using the [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") iso.

I already have the .iso file on the CD and tested it, it is booting up when i start my system.

The only problem im having is i dont know how to install ubuntu using the MinimalCD .iso file, while still keeping windows installed on my system.

Thanks in advance, if you need more details ill be here most of the day and tomorrow.

---

### Post by sudodus on 2014-07-01
Welcome to the Ubuntu Forums :-)

If I remember correctly, the mini.iso works well with BIOS, but if Windows is installed with UEFI, you must install Ubuntu from the 64-bit desktop iso file.

When you have told us about BIOS/UEFI, we can continue with the next steps.

---

### Post by mweyler24 on 2014-07-01
Windows is installed with Legacy I believe. I have just checked and it is not UEFI.

---

### Post by sudodus on 2014-07-01
OK, that's good.

0. Consider trying Ubuntu or some other flavour of it before starting the installation. You can try the installation by installing into a USB pendrive. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

1. Boot into Windows and use Windows tools to shrink the Windows partition. Standard Ubuntu needs at least 8 GB disk space, 16 GB is good but 25 GB is better. The lighter flavours Lubuntu and Xubuntu can work with less disk space, but the main difference is how they can work with older and weaker computers.

2. If you want advice about which flavour or packages that fit your computer, please specify

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

3. If you are not very used to linux, I suggest that you boot from a desktop iso file (a CD/DVD/USB drive made by burning/flashing an iso file) and run a 'live' session. If you want help with the partitioning, please run the following command from a terminal window and post the output to a reply

```
sudo parted -l
```
... space minus ell

In that live session you can use the program ***gparted***, which has an intuitive graphical user interface. Use this program to create partitions for Ubuntu. Make an extended partition of the unallocated space, and create logical partitions inside it. Prepare most of the space for the root partition and a smaller amount of space for the swap partition. If you intend to hibernate, you need swap of at least the same size in Gibibytes as the RAM. Otherwise you can use less (for example 1 GB if 2 GB or more RAM).

4. Boot into the mini.iso installer (12.04 LTS or 14.04 LTS). At the partitioning screen, select '***Something else***' and select the partitions that you created with gparted. It is also possible to create partitions here, but I think more difficult, particularly the first time.

Install the bootloader to the head of the internal drive, not to a partition, so to **/dev/sda** if that is the internal drive where you have Windows. D[COLOR=#696969]o *not* install to for example /dev/sda5.[/COLOR]

---

