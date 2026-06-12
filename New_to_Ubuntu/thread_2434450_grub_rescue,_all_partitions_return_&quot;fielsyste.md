---
title: "grub rescue, all partitions return &quot;fielsystem unknown&quot;"
date: 2020-01-06
forum: New to Ubuntu
---

### Post by ledda on 2020-01-06
Hi everyone,

I have recently installed ubuntu alongside my Windows 10 installation. I have two disks installed in the machine, one SSD (sda) and a HDD (sdb). The SSD fits my Windows 10 OS comfortably and there wouldn't be much room for anything else, and so I partitioned my HDD, ~2TB data and ~1TB for the ubuntu installation. The installation was successful however upon rebooting my BIOS booted straight to Windows and I was unable to access the Linux installation, despite changing the boot order in my BIOS to boot from the HDD first - Windows would boot instead. 

I have a live installation of ubuntu on a USB stick and I searched for advice on the forums and reinstalled grub and updated. Here too the installation was successful, and now my computer boots into grub, yet all of the partitions displayed by the "ls" command return "filesystem unknown", I've tried several suggestions that I've come across in the forums. Running the default configuration of boot-repair also achieved nothing (well, it did the first time. The first time grub also told me that there was "no such device" as the one given, I'm assuming the number displayed was the unique identifier of the partition that I see when I mount the drive in ubuntu for example. This message is now gone and I only get "filesystem unknown").

Here is the pastebin output from boot-repair.

[http://paste.ubuntu.com/p/HTgmC5F6Z2/](http://paste.ubuntu.com/p/HTgmC5F6Z2/)

My hunch is that the partitioning is wrong. Some of the messages at the beginning of the paste look suss to me. I should also note that I have removed the ubuntu partition and reinstalled ubuntu twice with the same results. I cannot boot into Windows anymore because grub is installed on both drives. At the very least, I'd be happy to know how to return to booting into Windows as usual.

Any help would be appreciated, thanks.

---

### Post by oldfred on 2020-01-06
One thing I do not like about Boot-Repair is that its default repair installs grub to every drive's MBR. That way a user does not have to know or choose what drive BIOS uses to boot, it just boots grub and grub will usually boot Windows. So it works.

But new Windows now uses fast start up which sets hibernation flag. Then Linux NTFS driver will not mount NTFS partitions to prevent damage and grub will not boot Windows. If you want to boot Windows from grub or use NTFS partitions in read/write mode, you must have fast start up and any hibernation off in Windows. Grub only boots working Windows, so whenever Windows breaks, you have to directly boot it, to maybe get into internal repair console and fix it. But still best to have a Windows repair/recovery flash drive.

And best to then keep a Windows boot loader in the Windows drive & grub boot loader only in Ubuntu drive. Windows will turn fast start up back on, often in background with an update and then grub will not boot Windows again. If you have Windows boot loader in MBR, then you just need to got into BIOS and boot Windows drive & turn fast start up or make other Windows repairs. Then reset default boot to Ubuntu drive.

Since sdb is over 2TiB, you have to use gpt partitioning. And grub then requires a tiny 1 or 2 MB unformatted partition with bios_grub flag. That will show as an error in many tools as it is unformatted. 
And NTFS partitions with hibernation flag set will show as errors.

So use your Windows repair/recovery flash drive to restore a Windows boot loader (fixMBR) to MBR of sda.
And boot Windows to turn off hibernation.
Then reset BIOS to default boot Ubuntu drive first.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by ledda on 2020-01-06
Hi oldfred,

thanks for the response. I'll give that a shot. Currently creating a bootable USB for Windows. Will report back on results.

---

### Post by ledda on 2020-01-07
Thanks for the help, now I can boot into Windows normally again. Unfortunately my desktop doesn't support fast-startup anyway and I'm pretty sure I had already disabled hibernate when moving to the SSD to save space. I have double checked and disabled it through the console anyway just to be safe. Unfortunately, grub still can't recognise any of the filesystems. Any ideas? If not, I may just have to buy another SSD so I can fit both Windows and ubuntu on there and install it all fresh.

---

### Post by oldfred on 2020-01-07
Having both systems on same drive will not help issue.

Did Windows do update when you rebooted? If so it just may have turned fast start up back on.
Note that fast start up in Windows is different than fast boot in UEFI. And Microsoft requires both as default from vendor.

Once you have system finally configured you can turn fast boot back on, as long as you know how to get back into system. Fast boot assumes no system changes and very quickly starts boot as it does not scan system for changes in hardware or configuration. Then you normally do not have time to get into UEFI or UEFI boot key to boot repair flash drive. 
Often cold boot, full power down will force a full start up, but still have to press correct key quickly. Both Windows & grub have direct to UEFI options, if boot goes that far.

If not fast start up or hibernation, not sure why the Linux NTFS driver will not open NTFS partitions. 
Some have had to run chkdsk if Windows was abnormally shutdown.

---

### Post by jbodhi on 2020-01-08
I just ran into this problem. I fixed it by making a windows bootable usb drive. booting into that drive then following the instruction until I got to a screen that had repair system on it. I clicked it and opened cmd and typed these commands 

bootrec.exe /FixMbr  press enter
bootrec.exe/FixBoot 

Than I had to boot back into windows and uninstall Ubuntu delete the partition extend the windows partition and then remake the Ubuntu partition and install it again. 

Now it runs fine.

---

### Post by ledda on 2020-01-09
> **jbodhi said:**
> I just ran into this problem. I fixed it by making a windows bootable usb drive. booting into that drive then following the instruction until I got to a screen that had repair system on it. I clicked it and opened cmd and typed these commands 

bootrec.exe /FixMbr  press enter
bootrec.exe/FixBoot 

Than I had to boot back into windows and uninstall Ubuntu delete the partition extend the windows partition and then remake the Ubuntu partition and install it again. 

Now it runs fine.

Thanks, this sounds like it might be worth a shot.

@Oldfred: I definitely don't have the option for fast startup on windows. My motherboard is relatively old (circa 2011): [https://www.gigabyte.com/Motherboard/GA-Z68MA-D2H-B3-rev-10#ov](https://www.gigabyte.com/Motherboard/GA-Z68MA-D2H-B3-rev-10#ov)
It only supports legacy BIOS, UEFI was still up and coming back then if I'm not mistaken. Here's a screenshot: 

[IMG]https://scontent-ber1-1.xx.fbcdn.net/v/t1.15752-9/81702366_471524480226605_3965009955357982720_n.png?_nc_cat=108&_nc_ohc=n6KEafhYbTwAQkSzMbdK04Kp4RSzpW7tg_AsrBZFNqG9t3RFx_2FzTYwQ&_nc_ht=scontent-ber1-1.xx&oh=3c70250fe0d93791b758ba6407392d19&oe=5E98522E[/IMG]

Will report back after reinstalling ubuntu after extending the windows partition.

---

### Post by oldfred on 2020-01-09
Newer systems with UEFI have fast boot setting in UEFI/BIOS, which then you would not have.

But Windows 8 & 10 have fast start up which is just a hibernation and sets the hibernation flag. Then grub will not boot Windows and NTFS driver will not mount with normal read/write permissions to prevent damage.

---

