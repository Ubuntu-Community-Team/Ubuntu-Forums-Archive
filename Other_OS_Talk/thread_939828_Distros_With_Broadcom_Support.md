---
title: "Distros With Broadcom Support?"
date: 2008-10-06
forum: Other OS Talk
---

### Post by Phasmus on 2008-10-06
I'm the proud owner of an elderly laptop with a dead hard drive.  The rest of it works fine and I can still get plenty of use out of the thing with a live-cd... if I can get online.  The problem is it has a broadcom wireless card (BCM4306 (rev 02)).

So far as I can tell Ubuntu won't work with this card without a lot of tweaking which ranges from difficult to impossible to carry out in a non-persistent environment.  So my question is this: are there any distros with live-cds that just support broadcom wireless out of the box?  Did this work with a version of Ubuntu before Hardy?

I'm pretty sure Ubuntu itself is out of the running here, but if anyone knows of a magic bullet to enable this card that isn't too tedious to do every time the machine is turned on and that doesn't require a reboot, that would be ideal. (Of course, this solution can't require that the machine is already online either.)

---

### Post by basenvironment on 2008-10-06
ebay - purchase a new drive
and/or
ebay - purchase a supported wireless card
and/or
customize a livecd on a system that can get online and use it

---

### Post by aysiu on 2008-10-06
You've got it the other way around. Broadcom does not support Linux. It's not on a distro-to-distro basis.

I did hear recently that Broadcom [released some Linux drivers](http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#tg3) but I think they're proprietary blobs and so won't be integrated into any Linux kernels in any distro, and I don't know if they are for all Broadcom cards.

---

### Post by Phasmus on 2008-10-06
> **basenvironment said:**
> ebay - purchase a new drive
and/or
ebay - purchase a supported wireless card
and/or
customize a livecd on a system that can get online and use it

#1:  This activity is pending, but very low priority.
#2:  #1 will make this moot.  Or moot-ish.
#3:  Unfavorable effort/benefit ratio.

Thanks.  I'm basically looking for a quick-fix until the laptop can rise again with a new drive (this may be months from now).  It's not urgent enough to spend a lot of time or money on though.  My theory is that somewhere out there someone has already done #3 and made the fruit of their labors available in the form of an easily acquired ISO file.

---

### Post by eragon100 on 2008-10-06
> **aysiu said:**
> You've got it the other way around. Broadcom does not support Linux. It's not on a distro-to-distro basis.

I did hear recently that Broadcom [released some Linux drivers](http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#tg3) but I think they're proprietary blobs and so won't be integrated into any Linux kernels in any distro, and I don't know if they are for all Broadcom cards.

To better support users, Broadcom has been actively supporting, maintaining, and testing the in-kernel Linux drivers for the NetXtreme, NetXtreme II, NetLink and 4401 product lines. The following is list of drivers supported for each prod

The Linux driver packages released by Broadcom are based on the latest in-kernel drivers with some added compatibility code to make it backwards compatible with most 2.6 kernels and some 2.4 kernels (generally newer than 2.4.24). ** If you are using the latest upstream kernel from [www.kernel.org](www.kernel.org), you generally do not need to download the Linux driver packages from Broadcom as the latest upstream kernel has the latest Linux driver patches. ** (emphasis mine)

How do you mean, don't ship in the kernel??

---

### Post by Phasmus on 2008-10-06
> **aysiu said:**
> You've got it the other way around. Broadcom does not support Linux. It's not on a distro-to-distro basis.

I did hear recently that Broadcom [released some Linux drivers](http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#tg3) but I think they're proprietary blobs and so won't be integrated into any Linux kernels in any distro, and I don't know if they are for all Broadcom cards.

Dang.  Thanks aysiu.  That gives a little more credence to #2 then.  But this laptop is too ancient and horrible to want to spend money on it.

Now I'm starting to lean toward #4 (Carry around a thumb-drive with the relevant deb/driver files and a script that gets everything started on Hardy).

---

### Post by aysiu on 2008-10-06
My big whoops. Thanks for the correction, eragon100.

---

### Post by Phasmus on 2008-10-06
Woah hey!  So assuming my card is supported I just need any distro with a very recent kernel?  Or is that too optimistic?  Could anyone suggest a relatively stable release with a bleeding-edge kernel I could try?

---

### Post by aysiu on 2008-10-06
> **Phasmus said:**
> Woah hey!  So assuming my card is supported I just need any distro with a very recent kernel?  Or is that too optimistic?  Could anyone suggest a relatively stable release with a bleeding-edge kernel I could try?
Ubuntu's next release is coming out the end of this month and should include the latest kernel.

---

### Post by NoWayBill on 2008-10-06
Fedora is bleeding edge.

But running off of a liveCD this shouldn't be problem as you're not going to have a lot of customizations being broken by updates.

---

### Post by crimesaucer on 2008-10-06
> **Phasmus said:**
> I'm the proud owner of an elderly laptop with a dead hard drive.  The rest of it works fine and I can still get plenty of use out of the thing with a live-cd... if I can get online.  The problem is it has a broadcom wireless card (BCM4306 (rev 02)).

So far as I can tell Ubuntu won't work with this card without a lot of tweaking which ranges from difficult to impossible to carry out in a non-persistent environment.  So my question is this: are there any distros with live-cds that just support broadcom wireless out of the box?  Did this work with a version of Ubuntu before Hardy?

I'm pretty sure Ubuntu itself is out of the running here, but if anyone knows of a magic bullet to enable this card that isn't too tedious to do every time the machine is turned on and that doesn't require a reboot, that would be ideal. (Of course, this solution can't require that the machine is already online either.)

Your card is supported by the b43legacy driver: [http://linuxwireless.org/en/users/Drivers/b43#supported](http://linuxwireless.org/en/users/Drivers/b43#supported)


The directions to install the b43legacy driver are here: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy](http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy)


> 
You are using the b43-legacy driver

If you are using the b43legacy driver, follow these instructions.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

Use version 3.130.20.0 of Broadcom's proprietary driver.
Download and extract the firmware from this driver:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
sudo ./b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta-3.130.20.0.o

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 


.... basically for that last part, you might have to "sudo mkdir /lib/firmware" (make the directory of "/lib/firmware" before you export the firmware to a directory you might not have yet).


.... when I had my old bcm4318 driver, this way worked very good for me..... better than the old way of ndiswrapper.

---

