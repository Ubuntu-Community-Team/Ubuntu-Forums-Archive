---
title: "Triple-boot possible: Win7, NN, OO???"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by chimak111 on 2011-10-14
I downloaded Ocelot using [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.iso.torrent)
I did the checksum: ~$ md5sum ~/Downloads/ubuntu-11.10-desktop-i386.iso
It tallies with c396dd0f97bd122691bdb92d7e68fde5 *ubuntu-11.10-desktop-i386.iso from [http://releases.ubuntu.com/11.10/MD5SUMS](http://releases.ubuntu.com/11.10/MD5SUMS)



I have a laptop running Natty perfectly. It is a dual-boot setup with Win7 (since my ISP and hardware guy both suggested leaving Win7 in place to make "troubleshooting" easier for ***them***).

I have backed up my data and there's no need to remind me. I won't sue!

My set-up is like this:
```

4 GB RAM
500 GB single hard disk
	sda1	~100 MB (NTFS)
	sda2	~51 GB (NTFS)
	sda3	~210 GB (NTFS)
	sda4	~227 GB (extended)
		sda5	223 GB (Linux)
		sda6	  4 GB (Linux swap / Solaris)

```
sda4, sda5 and sda6 were created when I installed Natty alongside Win7.

I now want to install Ocelot from a LiveUSB **but retain everything else including Natty**.

I don't want to update Natty to Ocelot.

Is it possible? How? Any pointers? I don't have experience in partitioning (or Linux for that matter).

---

### Post by beew on 2011-10-14
Yes, you boot into a live usb/cd and then use gparted to shrink the natty partition and then install OO in the new space. When you install choose "Something else" which is basically manual install and if you want Natty to retain controls of grub, intsall the boot loader in the partition where OO is going to be instead of the drive (ie. something like sda7 instead of sda)

---

### Post by garvinrick4 on 2011-10-14
> 
Yes, you boot into a live usb/cd and then use gparted to shrink the  natty partition and then install OO in the new space. When you install  choose "Something else" which is basically manual install 
+1
 > intsall the boot loader in the partition where OO is going to be instead of the drive (ie. something like sda7 instead of sda)

There seems to be a few ways to install grub2 but I say just to install grub in sda always,
always, always and then can tell which install to be in control of grub by itself by.
```
sudo grub-install /dev/sda
```From within the install and that will make it the install in control of grub and first as menuentry sense its config file is in control. My personal opinion and a strong one at that.

---

### Post by HousieMousie2 on 2011-10-14
> **garvinrick4 said:**
> 
There seems to be a few ways to install grub2 but I say just to install grub in sda always,
always, always and then can tell which install to be in control of grub by itself by.

+1

Grub is smart, it will find your other boot-able partitions and have them in the menu for you.  It keeps you from having to edit it manually or rerun the Grub set up later.

Side note: When you do update your distros you can let the package maintainer's version do the work for you... unless you start getting some fairly exotic set ups, but what you are going for is pretty basic from a Linux standpoint.

Leaving Win 7 is not a bad idea actually, there are times when it can be helpful for troubleshooting, extra hardware data, network info (when it isn't playing nice with Linux), and borrowing software and drivers (Wine or ndiswrapper, respectively.)

---

### Post by chimak111 on 2011-10-14
Thank you guys for your feedback! But I want to change my mind. 

After seeing a lot of very positive reviews of Ocelot, I think there's no particular point in retaining Natty.

I made a liveUSB using Unetbootin and it works.
I could set up my net connection and browse the internet.
I could open my spreadsheets.
I could play music (.ogg files). That about covers my modest needs.

My question now becomes: suppose I use the Update Manager as is recommended by Ubuntu. Can I point it to the LiveUSB to get most of the stuff that is needed to upgrade from Natty to Ocelot? Will that be a problem?

My Natty is pretty updated and I don't have too many "other" ppas. Just one for Google Chrome browser (stable version) and one for System Load Indicator 0.2 (from launchpad).

My Flash (for Firefox) is also updated.

(Another reason for just having Ocelot is that fiddling with partitions and GRUB is something I'd rather not do at this stage of my learning.)

---

### Post by chimak111 on 2011-10-14
I was looking at the Upgrade notes.

Looks like I should have downloaded something called the "Alternate CD".

The one I have is not mentioned!

Live and learn. Oh, well ...

---

### Post by oldfred on 2011-10-14
Most do not need alternate CD. The standard liveCD should be the one you use for installing. But it is good to have the liveCD of your current install to make repairs or reinstall grub2's boot loader if needed.

But if upgrading you do not need any CD as it downloads the entire upgrade in place.

While one or two upgrades may be ok, after upgrading in place for 3 years, I did a clean install and really liked the housecleaning that took place. But you have to do a lot of planning for a clean install to have programs, settings & anything else you might need. Best then is to install to another partition as you can go back to the older install.

---

