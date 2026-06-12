---
title: "Ubuntu Install Issue on Acer Aspire M1640"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by rTxx on 2012-09-13
I have a Live CD of Ubuntu 12.04 from which I am attempting to boot an Acer Aspire M1640.  I am using the 64 bit Live CD method.  I downloaded the ISO from the Ubuntu site.  I get to the very early boot purple screen with the two low resolution icons at the bottom of the screen, and the boot stops there.

I have found this web page [http://darinshaw.com/blog/index.php/2010/04/ubuntu-10-04-install-on-acer-aspire-m1640/](http://darinshaw.com/blog/index.php/2010/04/ubuntu-10-04-install-on-acer-aspire-m1640/) which essentially seems to have found a solution for Ubuntu 10.04, and if I can find no 'certain' solution, I'll try the suggestions it makes which are essentially resetting the BIOS to failsafe defaults, and disabling "USB Controller", "AZALIA  AUDIO", and "On-Board 1394 Controller" in the BIOS. There is also a reference to activating the NVidia driver at a later point in the boot which I am currently uncertain about what that means I have to do.

The author of the page does not seem to fully comprehend why or how this works and I'm reluctant to 'play' with BIOS settings, especially as I am currently using Windows Vista until I can (hopefully) fully migrate to Ubuntu.  The reset to failsafe is also pragmatically irreversible as I'd have no way of knowing what had been changed.

Here is some more information about the machine as it does have some modifications from the standard Acer box:

GeForce 9500 GT video card
2Tb SATA III HDD WDC WD20 EARX (the main board does not have SATA III capability as far as I am aware)
250Gb SATA MAXSTOR S TM3250310AS HDD
4Gb RAM

I have partitioned the 2Tb HDD as follows (partition sizes are approximate):
10Gb Primary containing Acer stuff in NTFS format
70Gb Primary containing Win Vista NTFS format
75GB Primary formatted Ext4 - empty
8Gb Logical formatted Linux Swap - empty
75Gb Logical formatted NTFS - Windows data
244Gb Logical formatted NTFS - Windows data
1,381Gb Logical formatted Ext4 - empty

The Linux partitions are intended for Ubuntu install and data.

The 250GB HDD is NTFS Windows data.

Any suggestions gratefully received.

---

### Post by mips on 2012-09-13
Try this [http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso](http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso) or some of the other options in that F6 menu.

---

### Post by rTxx on 2012-09-13
Thank you.  Are the functions on the F6 menu documented anywhere?

---

### Post by mips on 2012-09-13
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Google will probably give you more specific info

---

### Post by rTxx on 2012-09-23
Thank you - will try again with different settings and report back as and when I succeed.

---

### Post by bennyboobooboo on 2013-07-12
I'm aware this is old, but I thought I'd update.

I was having the exact same problem trying to install lubuntu 13.04 on the acer aspire m1640. The instructions from the blog page in the original post are spot on. You have to change the bios settings as described :
[LIST=1]
[*]Entered the BIOS again and went into Integrated Peripherals => Onboard Device Setup. I disabled &#8220;USB Controller&#8221;. I disabled &#8220;AZALIA AUDIO&#8221;. I disabled &#8220;On-Board 1394 Controller&#8221;.
[/LIST]
, then press F6 on the ubuntu boot up screen (where it gives you options like Install / try without installing / check for disk errors etc,) tick all the boxes there (nomodeset, ascpi=off, etc) and it will install. Once installed and updated, change back the BIOS and it works a charm.

Many thanks to Darin Shaw.

---

