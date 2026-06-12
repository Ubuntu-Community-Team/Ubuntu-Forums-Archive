---
title: "Ubuntu 12.04 install alongside windows 7 on an unpartitioned drive"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by SBiss on 2012-06-15
Hi all,

So my Dell laptop running windows 7 has gone wrong. I think it was an update that messed up, but i'm not sure. Anyway, it won't boot. So I figure I could dual boot the laptop by installing Ubuntu 12.04 off a USB stick.

I have the USB stick and am able to run the laptop off the stick without too much concern. However, I don't seem able to install codecs or anything to play media. I reckon this can be sorted by installing Ubuntu onto the harddrive (it's a software issue that is messing windows up. I intend to try to fix it by using Ubuntu...)

However, I get to the stage of where do I want to install it and I select alongside Windows, i.e. create a partition. But all the walkthroughs etc that I've seen assume that the HDD is the one that came originally, and has partitions etc, but mine is a replacement HDD with no partitions.

Basically, I don't really understand the partitions bit, and want help. I'm concerned about potentially wiping the data that I have on the HDD, which I really don't want to do!

If anyone can help, that'd be appreciated. Cheers!

---

### Post by wilee-nilee on 2012-06-15
> **SBiss said:**
> Hi all,

So my Dell laptop running windows 7 has gone wrong. I think it was an update that messed up, but i'm not sure. Anyway, it won't boot. So I figure I could dual boot the laptop by installing Ubuntu 12.04 off a USB stick.

I have the USB stick and am able to run the laptop off the stick without too much concern. However, I don't seem able to install codecs or anything to play media. I reckon this can be sorted by installing Ubuntu onto the hard drive (it's a software issue that is messing windows up. I intend to try to fix it by using Ubuntu...)

However, I get to the stage of where do I want to install it and I select alongside Windows, i.e. create a partition. But all the walkthroughs etc that I've seen assume that the HDD is the one that came originally, and has partitions etc, but mine is a replacement HDD with no partitions.

Basically, I don't really understand the partitions bit, and want help. I'm concerned about potentially wiping the data that I have on the HDD, which I really don't want to do!

If anyone can help, that'd be appreciated. Cheers!

We might be able to take care of the windows boot with enough information.

Windows codecs would not be fixed from ubuntu at least rarely anyway. 

In order to install ubuntu you need a unallocated space and be aware of the limitations of partition types and the number of.

You mention an un-partitioned drive in the header what does this mean that the 1 HD is showing this now or that you have a second HD?

---

### Post by SBiss on 2012-06-15
re: windows

when booting, it fails saying "shlwapi.dll missing". It doesn't actually seem to be missing, so I guess it's corrupted. I am in the process of trying to borrow a windows 7 disc to use for repairs.

re: ubuntu

the internal HDD is unpartitioned. I.e. just one big space, with the windows OS and all my data. However, when looking at the partition table during the installation process, it comes up at 500gb free. When in reality I think there is about 100gb free? So I'm scared of creating new partitions and it formatting the disk to make all the 400gb go byebye...

---

### Post by wilee-nilee on 2012-06-15
> **SBiss said:**
> re: windows

when booting, it fails saying "shlwapi.dll missing". It doesn't actually seem to be missing, so I guess it's corrupted. I am in the process of trying to borrow a windows 7 disc to use for repairs.

re: ubuntu

the internal HDD is unpartitioned. I.e. just one big space, with the windows OS and all my data. However, when looking at the partition table during the installation process, it comes up at 500gb free. When in reality I think there is about 100gb free? So I'm scared of creating new partitions and it formatting the disk to make all the 400gb go byebye...

Un-partitioned means no partitions, what you describe is a disc  with a full windows setup. That set-up has to be in a partition. You want to be specific here, we can miss things in the syntax used to describe.

W7 is best resized with its own partitioner, I would wait till its fixed to resize the disc, and make sure it is running okay. You seemed concerned that it is not destroyed.

AS far as the usb not alowing certain codecs you may need to go to the software sources and untick the cd and make sure the regular repos are open run a update then install like the ubuntu restricted extras and probably vlc, you should then be able to play most media.

This will be lost though on a power off if you do not have a persistent set up usb, if this was not a full install.

The software sources are in the edit of the ubuntu software center. If  this is a ISO loaded usb not a full install, you don't really want to run any update-upgrades, you can end up with problems, the OS is basically running off a read only ISO.

---

