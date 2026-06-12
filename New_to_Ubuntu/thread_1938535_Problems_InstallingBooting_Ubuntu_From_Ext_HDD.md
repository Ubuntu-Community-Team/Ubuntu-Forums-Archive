---
title: "Problems Installing/Booting Ubuntu From Ext HDD"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by SusieLinux on 2012-03-09
I'm trying to install the newest version of Ubuntu 64 bit.

I'm not very good at this I've already wiped my boyfriends "C" drive tonight so please bare with me.

I found an unused Western Digital drive still in it's box but it has been tested and works fine with Windows 7.  It's a 2TB USB 3.0 Ext HDD which I had formatted Fx4.

I used 10GB for the /
I used 8GB for the swap (this computer has 12GB RAM)
The rest was used for /home

I'm not sure how efficient that set up is so please feel free to correct me.

My motherboard support booting from USB HHD I've seen it done before but the drive would not boot.  I went back to the Live CD and erased that disc and just let it do a manual install.

It still won't boot.  I've set the computer to boot from USB HHD first and made sure it's the first HDD in the boot menu.  However it either hangs at the verifying pool screen or eventually boots into windows from an internal SSD.

Any ideas?

---

### Post by oldfred on 2012-03-10
Welcome to the forums.

It may be that you have not installed grub2's boot loader to the MBR of the external drive?  Or if it is a 2TB drive Ubuntu may have converted to gpt instead of the old MBR partitioning. You only have to have gpt if the drive is over about 2.2TB. But if gpt then it needs a bios_grub partition to install grub correctly.

This often fixes things and if not you can post the link to boot info script so we can look at the details.
You can download into liveCD to run only while in liveCD or download a full liveCd.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Since you have a large hard drive I may have made / (root) somewhat bigger. I normally suggest 10 to 25GB when you have a separate /home or separate data partitions. If you have Windows you may also want a NTFS partition for shared data. I still have my Firefox & Thunderbird profiles in my NTFS partition but rarely boot XP anymore. But that would only work if you have external plugged in all the time.

---

