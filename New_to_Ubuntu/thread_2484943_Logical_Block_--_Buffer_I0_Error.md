---
title: "Logical Block -- Buffer I/0 Error"
date: 2023-03-15
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-15
Hi,
During a live session of Ubuntu 20.04 (desktop) today, I was unable to copy screenshots and system log files onto a USB stick. The USB stick is fine, but when I tried to drag system logs and screenshots to the stick to copy them, something was interfering with the drag. The icons of the files "jumped" back into the file manager/browser. 

The security part of the log for this session records a Buffer I/O error, see the attached screenshots/thumbnails.

I have had this happen on another Lenovo Thinkpad as well, on which the Ubuntu 20.04 is installed as the OS. And on those occasions too, there was never anything wrong with the USB stick itself. Rather, it felt like the USB stick was forced not to be recognized, for when I logged out and logged back in, the USB stick was working fine again. This stick used during today's live session is working fine too. 

Perhaps there's something in the log indicating what was blocking the USB stick from getting recognized? 

Here's the log of this live session on pastebin: [https://pastebin.com/1ZBcei0e](https://pastebin.com/1ZBcei0e)

---

### Post by Impavidus on 2023-03-15
Did you mount the usb stick before attempting the file copy, was it automounted or was it unmounted? What if you attempt to copy the file from command line?

Sorry, I've always hated drag-and-drop interfaces. Far too easy to drop things in the wrong place.

---

### Post by bhubunt on 2023-03-15
I put the stick in during live session: I could open it and see that the files were on the stick, but I could not copy onto it. The stick is not broken.

Thanks for the suggestion. I will try from the terminal, just found this link: [https://linuxopsys.com/topics/copy-files-to-usb-using-terminal](https://linuxopsys.com/topics/copy-files-to-usb-using-terminal) 

I'm also hoping someone can look at the log and screenshot I posted. Perhaps the log reveals what went wrong. [https://pastebin.com/1ZBcei0e](https://pastebin.com/1ZBcei0e)

---

### Post by ActionParsnip on 2023-03-15
07:52:28 kernel: Buffer I/O error on dev sdb1, logical block 1, lost async page write
07:52:28 kernel: blk_update_request: I/O error, dev sdb, sector 33 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0

Doesn't look healthy. What file system are you using here?

---

### Post by bhubunt on 2023-03-15
> **ActionParsnip said:**
> 07:52:28 kernel: Buffer I/O error on dev sdb1, logical block 1, lost async page write
07:52:28 kernel: blk_update_request: I/O error, dev sdb, sector 33 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0

Doesn't look healthy. What file system are you using here?


Hi,
Thanks for the question. Can you give me some pointers as to how I can find the file system that was being used? 

I was logged into a live Ubuntu 20.04 session, not using the terminal and not making any specific choices about filesystems myself. 

I was simply trying to drag text files of logs and screenshots onto the USB stick but the dragging/copying was blocked. The stick works fine and I could open it. But the copying of the logs and screenshots onto the USB stick was blocked.

---

### Post by MAFoElffen on 2023-03-15
If i am understanding this right (I'm going off your description and the errors): Just to be clear about device /dev/sda... Isn't that the same USB as the "Live Session" was booted from? 

The Live Session media is (by default) "not persistent". If you wanted to save files to a LiveCD USB, it would either have to be setup as being persistent (having a writable area for persistent storage), or you would have to save to an additional USB storage device that was mounted after the Live Session was booted to be able to save files to... I think that others are assuming that, without noticing that it is saying the device is "/dev/sdaX"... which is normally assigned to the device that it booted from.

The LiveCD USB image is actually a compressed image file, that during boot, is uncompressed and exists in memory. That is why you are able to install packages, do updates, etc, in that environment. Any changes are lost when the Live Session is shut down. Anything else on that same media device (the original image), unless setup as persistent storage, is only read-only.

Many of us think that the old verbiage of continuing to call the LiveCD, created on a USB, of calling it a LiveCD inaccurate, and now refer to it as being a **L.I.E.** (Live Image Environment). And yes, we have a sense of humor. LOL

Does that make sense?

I'm not sitting there, seeing what you are doing, so I can only go off your description, and play the different scenarios in my head. Forgive me if I misunderstand that.

---

### Post by bhubunt on 2023-03-16
> **MAFoElffen said:**
> If i am understanding this right (I'm going off your description and the errors): Just to be clear about device /dev/sda... Isn't that the same USB as the "Live Session" was booted from? 

The Live Session media is (by default) "not persistent". If you wanted to save files to a LiveCD USB, it would either have to be setup as being persistent (having a writable area for persistent storage), or you would have to save to an additional USB storage device that was mounted after the Live Session was booted to be able to save files to... I think that others are assuming that, without noticing that it is saying the device is "/dev/sdaX"... which is normally assigned to the device that it booted from.

The LiveCD USB image is actually a compressed image file, that during boot, is uncompressed and exists in memory. That is why you are able to install packages, do updates, etc, in that environment. Any changes are lost when the Live Session is shut down. Anything else on that same media device (the original image), unless setup as persistent storage, is only read-only.

Many of us think that the old verbiage of continuing to call the LiveCD, created on a USB, of calling it a LiveCD inaccurate, and now refer to it as being a **L.I.E.** (Live Image Environment). And yes, we have a sense of humor. LOL

Does that make sense?

I'm not sitting there, seeing what you are doing, so I can only go off your description, and play the different scenarios in my head. Forgive me if I misunderstand that.


Hi 

No -- I was referring to another USB stick, not the installation stick which does not show.  I was trying to drag logs and screenshots onto this USB stick, but that dragging or copying was blocked. However, this stick is fine and I could open the stick, see the other files on it, *while* I was in this same Ubuntu 20.04 live session. So something was blocking the transfer of the system logs and screenshots onto this second USB stick, during the live session log-in of Ubuntu 20.04.

I posted the log on Pastebin and am hoping a forum member good at analyzing such logs could have a look at it. The logical block error is line 59 on this pastebin log: [https://pastebin.com/1ZBcei0e](https://pastebin.com/1ZBcei0e)

---

### Post by MAFoElffen on 2023-03-16
Try it again...

Looking at the logs:
```

07:53:40 kernel: sd 7:0:0:0: [sdb] Attached SCSI removable disk
07:53:40 kernel:  sdb: sdb1
07:53:40 kernel: sd 7:0:0:0: [sdb] Assuming drive cache: write through
07:53:40 kernel: scsi 7:0:0:0: Direct-Access     USB      USB DISK 3.2     2.00 PQ: 0 ANSI: 4
07:53:39 mtp-probe: bus: 4, device: 6 was not an MTP device
07:53:39 kernel: scsi host7: usb-storage 4-1:1.0
07:53:39 kernel: usb-storage 4-1:1.0: USB Mass Storage device detected
07:53:39 kernel: usb 4-1: SerialNumber: FC1507FA645C3
07:53:01 kernel: sd 7:0:0:0: [sdb] Attached SCSI removable disk
07:53:01 kernel:  sdb: sdb1
07:53:01 kernel: sd 7:0:0:0: [sdb] Assuming drive cache: write through
07:53:01 kernel: scsi 7:0:0:0: Direct-Access     USB      USB DISK 3.2     2.00 PQ: 0 ANSI: 4
07:53:00 mtp-probe: bus: 4, device: 5 was not an MTP device
07:52:59 kernel: scsi host7: usb-storage 4-2:1.0
07:52:59 kernel: usb-storage 4-2:1.0: USB Mass Storage device detected
07:52:59 kernel: usb 4-2: SerialNumber: FC1507FA645C3
07:52:58 systemd: tracker-store.service: Succeeded.
07:52:58 tracker-store: OK
07:52:52 systemd: systemd-hostnamed.service: Succeeded.
[COLOR=#ff0000]07:52:28 udisksd: Cleaning up mount point /media/ubuntu/disk (device 8:17 no longer exists)[/COLOR]
07:52:28 kernel: Buffer I/O error on dev sdb1, logical block 1, lost async page write
07:52:28 kernel: blk_update_request: I/O error, dev sdb, sector 33 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0
07:52:28 kernel: usb 3-2: USB disconnect, device number 6
07:52:25 nautilus: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

```
Look at line #57, highlighted in red above... The mount released and dropped out for some reason. That is why it had the I/O error in the next line.

---

### Post by bhubunt on 2023-03-16
Hi,
Thanks so much for the analysis. I really appreciate it.

Are there any indications what could have caused the released and dropped out mount, seeing that the USB stick is fine, intact and working perfectly.

As I mentioned in the original post, I have had the same thing happen repeatedly on two other computers with various USB sticks. Each time the USB stick is fine after I log out and log back in.

What does the bold section in this line of code mean?


```
 07:52:28 kernel: blk_update_request: I/O error, dev sdb, **sector 33 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0 **
```

(I now know how to cite code)

---

### Post by MAFoElffen on 2023-03-16
It could be various things, but one is this: RE: [https://www.reddit.com/r/pop_os/comments/gm13le/blk_update_request_io_error_dev_sdb_sector_0_op/](https://www.reddit.com/r/pop_os/comments/gm13le/blk_update_request_io_error_dev_sdb_sector_0_op/)

You have opened 3 threads in the past few days. That is not a bad thing. I am trying to understand. Just trying to paint the picture in my head of what is happening to what there...

One thread is this: [https://ubuntuforums.org/showthread.php?t=2484917](https://ubuntuforums.org/showthread.php?t=2484917) ... where you very likely have a failed 128GB internal hard disk. Or at least there are challenges to that system. (The BIOS no longer see's your hard disk.) Is this on the same Lenovo system as that thread? 

And the same system, as the networking question thread? ([https://ubuntuforums.org/showthread.php?t=2484974](https://ubuntuforums.org/showthread.php?t=2484974)). 

Is this happening on the same computer? Or on separate computers?

If the same computer, then please run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script from a LiveUSB and post the url of where the report uploads to, so we can see what your hardware is, and see how Linux see's it.

Let's see what is going on and paint an accurate picture.

---

### Post by bhubunt on 2023-03-16
Hi,
This is happening on the same computer, a Thinkpad x230.

Here is the result for the system info. It seems the system is asking me to fill in more information. Can you help? Also, if there is private info I need to mask, such as my location, let me know pls.

```
 --2023-03-16 19:18:37--  https://github.com/UbuntuForums/system-info/raw/main/system-info
Resolving github.com (github.com)... 140.82.121.4
Connecting to github.com (github.com)|140.82.121.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info [following]
--2023-03-16 19:18:37--  https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.109.133, 185.199.108.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 82324 (80K) [text/plain]
Saving to: &#8216;system-info&#8217;

system-info         100%[===================>]  80.39K  --.-KB/s    in 0.01s   

Last-modified header missing -- time-stamps turned off.
2023-03-16 19:18:37 (5.91 MB/s) - &#8216;system-info&#8217; saved [82324/82324]


This script needs some parts of it to run with elevated permissions.

Please enter your password for that to happen.
Running Script: system-info Version: 02.00-05, Script Date: 2022.12.08
 -------------------------------- 

The Script 'system-info' uses some very basic Linux utilities. 
Some of these utilities were not found.

The report will still run without them. It will just not answer related 
questions. Some of that information may be related to the diagnosis of 
your installed system. If missing utilities may have answered your 
specified problem, you may be asked by a 'Ubuntu Forums Member' supporting 
you if a program was missing, and if you could install it to answer that 
related question.

Program(s) curl, pastebinit,  is/are missing, 
but can be ignored as there still are installed utilities present to 
to be able to upload the report to an online PasteBin.

Some of these utilities are not default installed utilities to all Editions, 
versions, and flavors of Ubuntu... So may be considered as optional. 

<E>xit and install the program(s) or <C>ontinue anyway? <E/C> You can 'not' exit this script by pressing Control-C...Continue with last 'asked' input...
<E>xit and install the program(s) or <C>ontinue anyway? <E/C> c
Some task(s) will not work, but I'll do the best possible, continuing ...

Please provide some "Basic Information"...What is the Main Complaint summarized.

  
```

---

### Post by MAFoElffen on 2023-03-16
Run it. It only asks the user only two questions ( Summary of problem, any details you want to add)... You can put anything in those two fields. Not that important.

There is two version of the report... The onscreen preview is more detailed than the version it uploads. (it explains that in the onscreen version). What is uploaded is sanitized, to remove personal details and anything that may be a security risk if seen by the public. The script/report was reviewed and adopted by the Forum Admin Council.

It has been extensively tested and reviewed. (Even by DistroWatch) It is geared towards Ubuntu, but I made sure it also works on other distributions of Linux.

At the end of the script, it will ask you if you want to upload the report to a pastebin. Select yes. Copy down the URL and post it so we can review it.

I'm in the middle of testing a new PPA for it, with Debian installer packages, so that script is easier for new users to install on their systems. But we are not through testing that yet.

---

### Post by bhubunt on 2023-03-17
deleted

---

### Post by bhubunt on 2023-03-17
Hi,
For some reason, there is no url or link at the end of the report, just the following

```
 
This Report is prepared in two versions- 

The 'Your Eyes Only' version, only exists temporarily in memory, and is 
viewed onscreen by 'less'. The report that is viewed by 'less' onscreen 
contains 'sensitive data' that should NOT be posted publicly. 

The Final Report 'file' is saved to disk as a file. The Final Report is 
sanitized, filtered, with the sensitive data removed. It is safe to post 
online publicly. 


```

---

### Post by #&amp;thj^% on 2023-03-17
> **bhubunt said:**
> Hi,
For some reason, there is no url or link at the end of the report, just the following

```
 
This Report is prepared in two versions- 

The 'Your Eyes Only' version, only exists temporarily in memory, and is 
viewed onscreen by 'less'. The report that is viewed by 'less' onscreen 
contains 'sensitive data' that should NOT be posted publicly. 

The Final Report 'file' is saved to disk as a file. The Final Report is 
sanitized, filtered, with the sensitive data removed. It is safe to post 
online publicly. 


```
At this point just hit <q> and it will go on from there.

---

