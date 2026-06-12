---
title: "no boot sector on USB device (will still boot)"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by joshuanyhus on 2013-12-12
Hello all,
This is my first time posting on the forums here. After a few hours of searching here and on Google for a solution to my problem, and not finding one, I'm at a complete loss. I am fairly new to Linux, having only been playing around with it for a month now; I do know some of the baisics.

I just did a fresh install of Ubuntu 12.04 (32bit) from a Live CD on to an external USB 2.0 HDD (Western Digital Passport 2.5in 160gb). Each time I start up I get the message "no boot sector on USB device", requiring me to restart and hit my F12 key to select my boot device. Now when I do this, I still get the same message (no boot sector), however this time it loads Ubuntu. I have to go through this extra step each time, and if I don't, it will fail and require me to.

Since Ubuntu loads and seemingly runs normally, I've just ignored this for the past month. But it is starting to annoy me. I would like to just start up my computer without needing to go through the extra step of hitting F12 and selecting my external HDD every time. Yes, my external is first on the boot list, infact I have deactivated the others in the list just to see if that would fix it, and it didn't.

Any help would be greatly appreciated.

---

### Post by sudodus on 2013-12-12
Welcome to the Ubuntu Forums :-)

It is normal to press a hotkey (F12 or some other key in other  computers) at boot to make the system show a menu to select device to  boot from. Many people think it is inconvenient to always try first to boot from USB, when such a device is connected. But that behaviour can often be set in a BIOS or UEFI menu.

-o-

I think the computer gets to another USB device, where it does not find any bootloader.

Is there some other USB mass storage device in the computer, that it might select at normal boot? Maybe a flash memory card or USB pendrive?

Is there an internal HDD, that it boots to, and you select the USB drive from that? And is the configuration (boot order or USB devices) changed after the installation?

---

### Post by oldfred on 2013-12-12
May be useful to see details.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by joshuanyhus on 2013-12-12
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

It is normal to press a hotkey (F12 or some other key in other  computers) at boot to make the system show a menu to select device to  boot from. Many people think it is inconvenient to always try first to boot from USB, when such a device is connected. But that behaviour can often be set in a BIOS or UEFI menu.

-o-

I think the computer gets to another USB device, where it does not find any bootloader.

Is there some other USB mass storage device in the computer, that it might select at normal boot? Maybe a flash memory card or USB pendrive?

Is there an internal HDD, that it boots to, and you select the USB drive from that? And is the configuration (boot order or USB devices) changed after the installation?

Hey,
Thanks for the welcome. Yes, the device order is set to boot from my external HDD first and it is selected. There are no other USB devices plugged in, and I currently do not have an internal HDD (need to buy a new one). The only other bootable devices are my NIC and CD/DVD device. I have tried completely disabling them, only leaving the external HDD active in the boot list and that did not have any effect.

What really has me... In all the other posts I have found, when people get the "no boot sector on usb device" message, they actually can't boot Ubuntu, but yet in my case, I get the message, but Ubuntu will still boot up as long as I select it from the boot list. It's the strangest damn thing.

---

### Post by joshuanyhus on 2013-12-12
> **oldfred said:**
> May be useful to see details.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I'll give it a try here in a few minutes.

---

### Post by joshuanyhus on 2013-12-12
> **oldfred said:**
> May be useful to see details.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Here is the link to the report.
[http://paste.ubuntu.com/6563111/](http://paste.ubuntu.com/6563111/)

---

### Post by sudodus on 2013-12-12
I have one testing computer set up like yours now: No internal drive, and I'm testing to boot from various USB 2 and USB 3 devices. I have not had your problem (yet).

I see nothing wrong in the BootInfo report. I don't think the position of the boot files are too far away (but I am not sure).

I'm guessing now: Maybe the USB is reading so slowly, that it does not reach to them before time-out. And when you select the boot drive manually, there is time for the system to get started.

Let us wait for *oldfred*'s advice :-)

---

### Post by oldfred on 2013-12-12
I agree with sudodus. It may just be time for spinup of drive. They keep trying to shorten boot time and it may then be too quick for some devices. Is drive externally powered or thru USB port? 

The issue on boot file too far from start is with some BIOS and grub combinations, primarily on USB boot devices. Your boot files currently are all within the first 100GB, but your / (root) is over 100GB and later updates could install grub or kernel beyond the 100GB. That usually then is a UUID or partition not found even though it is the correct partition.
If your BIOS is one with issues they you may have that in addition to drive being ready. I normally suggest / be 10 to 25GB and then rest of drive as /home or /mnt/data partition so all boot & system files are closer together on drive and reinstall can be a bit easier if your data is separate from your system.

---

### Post by joshuanyhus on 2013-12-13
> **oldfred said:**
> I agree with sudodus. It may just be time for spinup of drive. They keep trying to shorten boot time and it may then be too quick for some devices. Is drive externally powered or thru USB port? 

The issue on boot file too far from start is with some BIOS and grub combinations, primarily on USB boot devices. Your boot files currently are all within the first 100GB, but your / (root) is over 100GB and later updates could install grub or kernel beyond the 100GB. That usually then is a UUID or partition not found even though it is the correct partition.
If your BIOS is one with issues they you may have that in addition to drive being ready. I normally suggest / be 10 to 25GB and then rest of drive as /home or /mnt/data partition so all boot & system files are closer together on drive and reinstall can be a bit easier if your data is separate from your system.

Interesting stuff & The USB is powered via the USB port.

I  have tried creating the different partitions manually before, usuing  suggested ammounts, including /boot at the very front, but with no  difference to the "no boot sector" message. So the past few times I've  just let Ubuntu setup do it for me. It really does sound as though you  guys may have naild the cause on the head. It is probably the usb  reading slow, it makes sense to me. Are there any suggestions on how to  test this more soundly, or try and inprove the read time?

---

### Post by oldfred on 2013-12-13
I have seen this boot parameter. I think it slows down booting, but have no idea if it would work.
        rootdelay=90

I would add that in place of quiet splash. Use e on grub menu and scroll down to linux line. You also could try several different times for 90. Not sure if that is 90 sec or 90 millisec or something else. 
If it happens to work and you find a good time setting then you can make it permanent by editing /etc/default/grub.

Edit - found out what it is
>     rootdelay=    [KNL] Delay (in seconds) to pause before attempting to
            mount the root filesystem


You may not need 90 sec but 30 or 60 or something.

---

### Post by joshuanyhus on 2013-12-13
> **oldfred said:**
> I have seen this boot parameter. I think it slows down booting, but have no idea if it would work.
        rootdelay=90

I would add that in place of quiet splash. Use e on grub menu and scroll down to linux line. You also could try several different times for 90. Not sure if that is 90 sec or 90 millisec or something else. 
If it happens to work and you find a good time setting then you can make it permanent by editing /etc/default/grub.

Edit - found out what it is


You may not need 90 sec but 30 or 60 or something.

When you say "Use e on grub menu", would that be the same screen that gives me the option to skip the loading of my encrypted swap? I don't get a screen with options other than that and I don't recall seeing an E option, though I may have missed it.

I will probably give this a try tomorrow, been having a few drinks and don't want to make a mess of my fresh install so soon. ;)

---

### Post by oldfred on 2013-12-13
If only one install, you do not get menu by default unless you have a crash. It assumes the one install is really the one you want to boot.
But you should be able to hold shift key from BIOS screen until menu appears. It will show all kernels installed, recovery mode boot options, memory test etc. 
From that menu then on first or default entry use e for edit. I has other keys for the other options shown.

---

