---
title: "reinstalling Windows 8 after ubuntu 15.04"
date: 2015-05-25
forum: New to Ubuntu
---

### Post by evaristegalois on 2015-05-25
I have an Acer Aspire desktop computer. I installed ubuntu on it, which worked flawlessly. Before installing ubuntu, I created a Windows recovery USB stick. Now I want to use ubuntu on another computer and reinstall Windows 8. But there is a problem.

I insert the Recovery USB stick in the computer and boot the computer. All goes well. Windows recovery starts up. It gives me the option to REFRESH or RESET my computer. I choose RESET (which means erase everything and install Windows from scratch). Windows tells me that ``there is a problem resetting your PC.'' I've tried all kinds of things, and here are the only hints I can get out of the Acer Aspire. When I choose REFRESH instead of RESET, the complaint is ``The drive where Windows is installed is locked. Unlock the drive and try again.'' Of course, Windows isn't installed at all. Ubuntu is currently installed. 

I searched forum posts as much as I could but there wasn't much help. I tried doing this with ``Secure Boot'' enabled and disabled. No luck. I cannot find UEFI settings in the BIOS -- in one place I read that Windows can only start when ``UEFI only'' is selected in the BIOS. But there is no such option in my BIOS settings. I wonder if what I need to do is ``Restoring a Windows boot record'' as referred to here:

[https://wiki.archlinux.org/index.php/Master_Boot_Record](https://wiki.archlinux.org/index.php/Master_Boot_Record)

but the Acer Aspire is new-ish so I suspect it uses GPT and not MBR.

Can anyone help?

---

### Post by Vladlenin5000 on 2015-05-25
What you need to do is simply install on top with a normal Windows 8 DVD or USB, not use a recovery media. As its name suggests, recovery is meant to recover, not to install. You must have "something" to recover but as you correctly stated, you don't.

---

### Post by evaristegalois on 2015-05-25
I don't think that's the issue. A recovery USB should be able to recover Windows even if it's completely fried, which is equivalent to installing Ubuntu over top of it. There was a 16GB requirement for the recovery USB, so I can't imagine it doesn't have the whole system on it. I just need to make the drive bootable for Windows. 

Here is some more information. The recovery USB will give me an MS-DOS command line (nothing more, other than the RESET and REFRESH options). If I run chkdsk /f it says:

The type of the file system is NTFS. Cannot lock current drive. Windows cannot run disk checking on this volume because it is write protected.

When I run "diskpart", select disk 0 and run "list partition" it says:

Partition 1 System [type] 512MB [size]
Partition 2 Unknown [type] 923GB [size]

then, when I select a partition and run "active" it responds:

The selected disk is not a fixed MBR disk. The ACTIVE command can only be used on fixed MBR disks.

---

### Post by Vladlenin5000 on 2015-05-25
AFAIK, The recovery needs the original Windows partitions, the ones you no longer have. Probably not even the EFI partition if you installed Ubuntu in CSM or legacy mode.

Obviously I'm not an Windows expert. I suggest you ask for help in a Windows forum.

Good luck.

---

### Post by Vladlenin5000 on 2015-05-25
Apparently I'm right after all. Please read the answer here: [http://www.tomshardware.co.uk/answers/id-1944717/fresh-install-windows-ssd-windows-usb-recovery-drive.html](http://www.tomshardware.co.uk/answers/id-1944717/fresh-install-windows-ssd-windows-usb-recovery-drive.html)

---

### Post by tristan16 on 2015-05-25
> **Vladlenin5000 said:**
> Apparently I'm right after all. Please read the answer here: [http://www.tomshardware.co.uk/answers/id-1944717/fresh-install-windows-ssd-windows-usb-recovery-drive.html](http://www.tomshardware.co.uk/answers/id-1944717/fresh-install-windows-ssd-windows-usb-recovery-drive.html)

Since I have had to reinstall Windows 8 several times (a big factor in my switch to Ubuntu) I can confirm that a recovery USB only reinstalls an existing installation. You'll need the disk either way, so just install from disk.

---

### Post by evaristegalois on 2015-05-26
When I bought the computer it did not come with an installation disk. It appears that the expectation is that you create your own USB recovery and that you will never need anything else. Is this not a worry for many other Ubuntu users? If they install Ubuntu over top of Windows, they can't get windows back; if you want the option of getting Windows back you must do a dual-boot installation. Is that correct? Doesn't that stink? I called Acer. I have to mail it in, but they will reset it to its original condition. Thanks for your help, everybody.

---

### Post by oldfred on 2015-05-26
On my new Dell, it took 5 DVDs and two flash drives to make a Dell recovery, a Windows recovery and a full image backup with boot DVDs.
I also partitioned in advance and had downloaded Ubuntu. But it then only took 10 Minutes to install a full working system.

---

### Post by evaristegalois on 2015-05-26
Wow, I guess it takes a lot of forethought.

---

### Post by cariboo on 2015-05-26
The recovery image on my Toshiba laptop is 9GiB in size, a 16GiB usb thumb drive worked for me. I did a failed Ubuntu UEFI install on the laptop, and decided to start from scratch. The recovery image brought my system back to the way it was the day I purchased it.

---

### Post by leunam12 on 2015-05-27
One option is to download Windows 8.1 from Microsoft and start from zero. You will need a Windows computer to do this. You will also probably have to go to the computer manufacturer's website and download any drivers that are not installed via Windows Update and additional software that came with the computer if available. 

[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

