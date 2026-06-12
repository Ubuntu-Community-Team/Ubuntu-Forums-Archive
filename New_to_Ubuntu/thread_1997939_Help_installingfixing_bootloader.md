---
title: "Help installing/fixing bootloader"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Martin Bannister on 2012-06-05
Hi,

I'm hoping you guys can help.  I'm not new to Linux or Ubuntu but am not savvy with the terminal either (just so you know I will need a little talking through anything involving it).  

I just installed 12.04 on my desktop but think I made a mistake with the bootloader!  

I've installed Ubuntu to an external HDD that I wasn't using for anything else, but that did have existing partitions on it that I wanted to keep.  I also wanted to preserve my desktop setup as it already has Windows Vista and Fedora (16 I think) installed.  

The external HDD already had Linux Mint on it but the Laptop that I used to run it off died and it doesn't seem to like the desktop so shrank it's partition to allow room to install Ubuntu.  

Ok, now I get to the problem.  With all the faffing about with the partitioning during the install wizard I neglected to change where the bootloader should have installed and instead of installing to the external HDD it appears to have installed to the internal HDD where Vista and Fedora were.  When I boot from the External HDD I now get the old Linux Mint bootloader menu that was on it before (that also shows a Windows 7 option that was on the laptop) .  If I boot from the internal HDD I get the option to boot Ubuntu 12.04, from which I am now typing, so it boots fine, the problem I have it that Fedora isn't an option and I haven't tried Vista yet...  

Is there a backup of the old bootloader config/menu somewhere that would have been made during install?  Is the easiest thing to do to add Fedora, however that is done, to the new/current bootloader menu, providing Vista also works?  

Any help would be appreciated.  I would love to switch to Ubuntu entirely but there are still things I need Windows for and there are still things I would like to retrieve from Fedora even if I abandon it eventually.  

If it helps:
SDA - is the internal HDD and where the bootloader currently is
SDB - is where Ubuntu is installed and I wanted the bootloader to be
I don't mind if the bootloader stays on SDA as long as all the options are there.  

Thanking you in advance.
Martin.

---

### Post by oldos2er on 2012-06-05
Post moved to its own thread.

---

### Post by wilee-nilee on 2012-06-05
Use the boot-repair app to run a bootinfo summary and post the URL of its location. The script will give us the low down on your setup.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-06-05
Best if we see details of your install.

But you can easily install grub2's boot loader to sdb. From Ubuntu just run this.

sudo grub-install /dev/sdb

But grub also remembers where it originally installed, so on a major update to grub where it reinstalls it reinstalls "correctly".

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If Fedora is in a LVM partition you have to have the lvm2 installed.
sudo apt-get install lvm2

Someone just posted that, that the os-prober still did not work unless you also mount the Fedora partition first. The os-prober must not be able to use the lvm module on its own to mount it.

---

