---
title: "Unable to Boot into Windows after resizing Ubuntu Partition"
date: 2017-04-12
forum: New to Ubuntu
---

### Post by bbattleson on 2017-04-12
Hello,

So I initially installed Ubuntu and was able to boot into Ubuntu and Windows. Then, once I realized I needed a larger Ubuntu partition, I followed [these instructions]("https://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/") (basically used GParted from a live session on the installation USB). I shrank my Windows partition (sda5), and moved the Ubuntu partition (sda8) to the left and expanded it. When GParted finished, I was able to boot back into Ubuntu, but haven't been able to boot back into Windows. Next, I ran the Boot-Repair tool, (here is the [boot-info]("http://paste2.org/JtVBddgy")) and still can't boot into Windows. 

Any help would be appreciated.

Thanks!

---

### Post by yancek on 2017-04-12
It is always a good idea to run Disk Defragmenter from windows prior to modifying a partition.
It is always better to use a windows tool (Disk Management) to modify a windows partition.
After doing that, you should run chkdsk on the partition.

The information you posted indicates that your windows ntfs partition is in an inconsistent state.  That generally means you left the windows system hibernated prior to making the change although it is possible it is one of the other problems listed.  You could check the BIOS to turn off anything related to hibernation or fastboot.  What happens when you try to boot windows?

---

### Post by bbattleson on 2017-04-12
So just to check, I can't do any of those first three suggestions because I've already modified the partition, correct?

I looked through the UEFI settings and didn't see anything related to hibernation or fastboot. Is there somewhere specific I should look? However, I do know that I disabled fastboot before installing Ubuntu.

When I try boot into windows, the screen goes black, then restarts and I'm back at the GRUB menu (when I was previously able to boot into windows, a loading wheel would immediately pop up).

---

### Post by Bucky Ball on 2017-04-13
Welcome. You resized the Windows OS partition with Linux partitioning tools. This is a no-no and known to cause issues with Win boot. You have no doubt screwed the boot manager/sector of Windows. 

For future reference, NEVER resize Win OS partitions with Gparted or any other Linux partition manager. Use Windows tools, and as mentioned, defrag the partition two or three times prior to resizing. The default Win defragmenter is fairly piddling for this and something like PowerDefragger (from memory) is much better.

This goes vice versa for Linux partitions. Use Linux tools for resizing Linux partitions. 

Anyhow, you could try opening a terminal in Ubuntu and

```
sudo update-grub
```

... reboot and see if you get Windows on the grub list to choose. I doubt that will happen and can't really help with fixing your Windows boot (that is a Win issue), but hopefully someone else can leap in and give you exact instructions about fixing it (think you need to use the Win recovery disk so hopefully you have a legal Win and a legal recovery disk). 

Good luck.

---

### Post by yancek on 2017-04-13
> So just to check, I can't do any of those first three suggestions because I've already modified the partition, correct?

Yes that is correct.  I believe there are settings for hibernation/fastboot in both the BIOS and somewhere on windows.  I'm not sure if you need to turn them off in windows also or if doing it in the BIOS is all that is necessary.  You might be able to run chkdsk from a windows installation DVD with the Repair option, if you have one.  Other than running update-grub suggested above, I don't know of anything else you can do from Ubuntu.

---

### Post by oldfred on 2017-04-13
If an UEFI install, you may be able to directly boot Windows from UEFI boot menu, often f10 or f12 check manual. You probably have to press f8 and immediately get into its own repair console.
If BIOS you may have to temporarily reinstall Windows boot loader to try direct boot and f8.

If not then you have to use your Windows repair disk and boot that to make Windows repairs.

Grub only boots working Windows. That also means Windows cannot be hibernated, not need chkdsk. And whether dual booting or not, Windows may need repairs and you have  to be able to make those.

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by nojimon on 2017-04-13
> **yancek said:**
> Yes that is correct.  I believe there are settings for hibernation/fastboot in both the BIOS and somewhere on windows.  I'm not sure if you need to turn them off in windows also or if doing it in the BIOS is all that is necessary.  You might be able to run chkdsk from a windows installation DVD with the Repair option, if you have one.  Other than running update-grub suggested above, I don't know of anything else you can do from Ubuntu.

not the cause or solution

---

