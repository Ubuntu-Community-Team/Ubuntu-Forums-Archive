---
title: "Can You Install a Physical OS on a Portable HDD and Boot It With And Without VirtualM"
date: 2014-11-22
forum: New to Ubuntu
---

### Post by khan3 on 2014-11-22
Hi,

Is it possible to a install a physical OS(Ubuntu) on a portable hard drive. 

Then either:

 1. Boot it using vmware on my PC which has a windows host. (Dual boot)
2. Boot it directly on my laptop/pc without the use of a virtual machine. (Single boot)

thanks.

---

### Post by ajgreeny on 2014-11-22
There is no simple yes or no answer to this question.

You can certainly install Ubuntu to an external (portable) hard drive and boot to it directly as if it were a normal internal drive.

You can not boot it using vmware as far as I am aware, but I don't know vmware.  However, I  do not think that you boot full installations using vmware, you use virtual machines.  I use VirtualBox and the VMs for that are[COLOR=#ff0000] .vdi[/COLOR] files ([COLOR=#ff0000]v[/COLOR]irtual [COLOR=#ff0000]d[/COLOR]isk[COLOR=#ff0000] i[/COLOR]mages); perhaps vmware also is able to use vdi files.

Most portable installations should be able to boot on many, or most, machines provided all drivers are open-source, but there may be problems if you have to install any proprietary drivers for graphics or wireless cards.

When installing to the portable disk it is also imperative that you use the "Something Else" option and make sure you put the OS on that disk's partitions, but very importantly that you put grub bootloader on the portable disk, not on the internal disk, which is the default.  So if your external disk is /dev/sdb make sure you put grub onto /dev/sdb, not onto a partition such as /dev/sdb1.

---

### Post by nerdtron on 2014-11-22
> **khan3 said:**
> Hi,

Is it possible to a install a physical OS(Ubuntu) on a portable hard drive. 

Then either:

 1. Boot it using vmware on my PC which has a windows host. (Dual boot)
**2. Boot it directly on my laptop/pc without the use of a virtual machine. (Single boot)**

thanks.

Number 2 is possible. I'm currently using it on my external hard drive.
For installation:
1. Make a bootable USB.
2. Disconnect all other hard drives (including internal ones) just to avoid any confusion.
3. Boot into the Live USB.
4. Plug the external/portable hard drive.
5. Install Ubuntu.

Done. Just always choose to boot from USB when you use it on other computers.
Issues: Some applications/ overall system is a little (just little) slower than usual due to slow USB connection. Also some computers have video cards which can cause display problems so don't install any proprietary codecs.

---

### Post by C.S.Cameron on 2014-11-22
My wife boots Ubuntu on her computer from a portable USB3 hard drive.
When we travel she takes the portable hard drive along and plugs it into one of my laptops.

I suggest that when installing Ubuntu to a portable hard drive, disable the internal drive and plug in the portable drive, then install Ubuntu as usual.
I you wish the option of booting either drive from grub, (when the external is plugged in), do an update-grub when booted from Ubuntu.

---

### Post by coldcritter64 on 2014-11-23
> Is it possible to a install a physical OS(Ubuntu) on a portable hard drive. 
For that specific quote, yes is the answer.

However for your 2 following questions:

1. I don't think that is possible without pretty high risk of corrupting the partition data. I seem to remember when using virtualbox a few years back reading about direct hard drive access from virtualbox. I dropped the idea real quick as it sounded very dangerous to my install data from what I read then. 
Refer to ajgreeny's answer for a good rundown on normal virtualbox usage. I have never used or tried vmware myself as well.

2. > Most portable installations should be able to boot on many, or most,  machines provided all drivers are open-source, but there may be problems  if you have to install any proprietary drivers for graphics or wireless  cards.
^^^ This OP. I use external installations all the time. Anything needing proprietary drivers are a hassle and some devices may fail as a result. Using an internet connection (wired ethernet usually works OK) and a terminal (alternatively the Software Center if you like a GUI) will fix all problems in a few minutes when you learn how. Most fixes require determing what the hardware is and downloading the appropriate firmware file from the repositories. Once you establish a temporary wired connection to get internet access you can even fix wireless networking issues easily as you can fire up a browser and ask away here on the forums for assistance. 

For when you actually try installing on an external device, note what both C.S.Cameron and nerdtron have noted, I quote C.S. Cameron ...
> disable the internal drive and plug in the portable drive, then install Ubuntu as usual Very good advice for you to note OP a VERY good idea. It gives anything currently installed protection from accidental overwriting. Without this, simply putting one letter wrong in a device name and ***BAM*** /dev/sda your main OS just got clobbered when you actually meant to write the data to /dev/sdb (the external drive). One letter can cause a big difference in outcomes, one positive and the second positively catastrophic.

However if you are uncomfortable physically disconnecting or removing hardware first ...[U][I]
Make sure your main system is backed up fully, both OS and any data, to external media first,[/I][/U] if you don't physically disconnect the current installation when setting up an external drive. You can at least rebuild any major mistake from a backup image if you do have a major failure.

Also as others above note, for best performance and compatibility try to stick to open source drivers where possible. I regularly use Nvidia drivers on external installs, can be very problematic when swapping the external between differing hardware. Simply purging the drivers in terminal and a reboot resets to Nouveau drivers, you can actually script the change over for even easier swapping.

 It is just far easier not to put them in the first place if you are not comfortable with terminal or scripting.

Cheers, coldcritter64

---

