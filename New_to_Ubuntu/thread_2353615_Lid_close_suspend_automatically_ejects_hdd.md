---
title: "Lid close suspend automatically ejects hdd"
date: 2017-02-23
forum: New to Ubuntu
---

### Post by sirajul.anik on 2017-02-23
I have HP Pavillion 450 G4 Laptop. I am using windows 10 and Ubuntu 16.04 dual boot on it. I have one PNY SSD and WD HDD. 
When I boot windows, I close the lid and it suspends the laptop. When I open the lid, SSD and HDD both works fine. 
When I use Ubuntu, close the lid. The laptop goes is suspend mode. When it comes back, I can't find the HDD. It's not showing up in nautilus or in disks application. 
What can I do now? I want both the suspend and the hdd to boot perfectly. A system log is attached in case you want. [http://pastebin.com/NvBN9txf](http://pastebin.com/NvBN9txf)


Before lid close: [http://pastebin.com/hJUiGrXt](http://pastebin.com/hJUiGrXt)
After lid close: [ http://pastebin.com/Cu55WUtg]("http://http://pastebin.com/Cu55WUtg")

---

### Post by DuckHook on 2017-02-24
Might your problem be related to the following? [https://ubuntuforums.org/showthread.php?t=2327715](https://ubuntuforums.org/showthread.php?t=2327715)

If so, try disabling fastboot on Windows.

---

### Post by sirajul.anik on 2017-02-24
> **DuckHook said:**
> If so, try disabling fast boot on Windows.
Disabled fast boot, but it's still not working! :(

---

### Post by DuckHook on 2017-02-27
I point out these events for you. The red highlights are mine. They occur during resume:

```
Line 151: Feb 22 22:52:20 Sirajul kernel: [  563.183358] ata3: SATA link down (SStatus 4 SControl 300)

Line 177 to 188:
Feb 22 22:52:20 Sirajul kernel: [  563.499132] ata2: SATA link down (SStatus 0 SControl 300)
Feb 22 22:52:20 Sirajul kernel: [  563.499138] ata2: limiting SATA link speed to 1.5 Gbps
Feb 22 22:52:26 Sirajul kernel: [  568.898007] ata2: SATA link down (SStatus 0 SControl 310)
Feb 22 22:52:26 Sirajul kernel: [  568.898011] ata2.00: disabled
Feb 22 22:52:26 Sirajul kernel: [  568.898025] sd 1:0:0:0: rejecting I/O to offline device
Feb 22 22:52:26 Sirajul kernel: [  568.898027] sd 1:0:0:0: killing request
Feb 22 22:52:26 Sirajul kernel: [  568.898033] ata2.00: detaching (SCSI 1:0:0:0)
Feb 22 22:52:26 Sirajul kernel: [  568.898058] sd 1:0:0:0: [sdb] Start/Stop Unit failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Feb 22 22:52:26 Sirajul kernel: [  568.900566] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
Feb 22 22:52:26 Sirajul kernel: [  568.900632] sd 1:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb 22 22:52:26 Sirajul kernel: [  568.900633] sd 1:0:0:0: [sdb] Stopping disk
Feb 22 22:52:26 Sirajul kernel: [  568.900637] sd 1:0:0:0: [sdb] Start/Stop Unit failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

Lines 191 to 193:
Feb 22 22:52:26 Sirajul [COLOR="#FF0000"]ntfs[/COLOR]-3g[2393]: Unmounting /dev/sdb1 (Files)
Feb 22 22:52:26 Sirajul [COLOR="#FF0000"]ntfs[/COLOR]-3g[2393]: Failed to sync device /dev/sdb1: Input/output error
Feb 22 22:52:26 Sirajul [COLOR="#FF0000"]ntfs[/COLOR]-3g[2393]: Failed to close volume /dev/sdb1: Input/output error
```

To my knowledge—which may very well be wrong—NTFS volumes are not suspendable in Ubuntu. Your Windows install resumes because it is using its native partition and filesystem. Your Ubuntu session can hardly be expected to gracefully resume a foreign partition and filesystem. It is amazing enough that Linux can even read NTFS.

I don't use Windows at all. The above is purely an educated conjecture. I hope someone with more knowledge will see this thread and advise. But that's what I'm guessing is your problem.

---

### Post by sirajul.anik on 2017-03-01
> **DuckHook said:**
> NTFS volumes are not suspendable in Ubuntu.
I have tried to convert the disk to ext4 and no luck. I'm not sure what to do. I went to the store from where I purchased, they said "we found no complaint using windows. So, we can't give you any solution now. If the SATA link is down what can we do? we just added the cable with your caddy. we have got nothing to do."
In this case, what can I do now? How can I let anyone know about this issue, advanced members? Tried ubuntu 14.04 & mint. Moreover, another Laptop I'm using still uses HPFS/NTFS partition type. Causes no issue. Maybe because the older one uses one hard drive and the newer one uses two?

---

### Post by DuckHook on 2017-03-01
I alert you again: My guess may be wrong. I don't think you should act on the basis of my expertise on this matter. Since I do not dual boot and have no NTFS filesystem, I really don't have the knowledge to act as your guide on this one.

Let's wait to see if a more knowledgeable member jumps in here.

---

### Post by sirajul.anik on 2017-03-03
Dear DuckHook, Thanks for your replies. Last day I went to the shop from where I bought my Laptop. Then they had some experiments. with hard disks and OS. They also swapped the SSD and HDD but found no result. Finally, they showed me another laptop with SSD and HDD on the caddy and it was working. Then they decided that maybe Ubuntu may have issues with intel's 7th generation processors. Told to wait until 17.04 releases. Hoping for the best. :)

---

