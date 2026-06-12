---
title: "Following list of software packages is required. ntfsprogs / ntfs-3g"
date: 2015-09-19
forum: New to Ubuntu
---

### Post by kc110 on 2015-09-19
Having successfully installed 14.04 dual boot (Windows 7 Home) on my laptop, I am now having difficulties installing to my desktop PC. Also Windows 7 Home.

I am using the same usb drive but get the message:-

unable to read the contents of this files system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:
ntfsprogs / ntfs-3g

I have searched this site for solutions with no success.

I have defragged my main drive and chkdsk'ed it. Twice both and defraggler from Piriform.

The live usb installation tells me that ntfs-3g is already installed.

Any help will be much appreciated.

kc

---

### Post by kc110 on 2015-09-19
Should have said that my drive shows up in gparted with an exclamation mark and will not let me partition appropriately.

---

### Post by coffeecat on 2015-09-20
*Thread moved to **New to Ubuntu**,* at request of OP.

It's quite odd that the live USB session is telling you that you need the packages ntfs-3g and ntfsprogs. As you say, ntfs-3g is included in the live session, as it is in a default installation of Ubuntu. Also, the ntfsprogs and ntfs-3g packages were merged a few years ago, so you get all the ntfsprogs stuff with ntfs-3g. When exactly do you see that message? What are you doing when you see it?

And – please confirm whether or not the version of Ubuntu you are using in the live CD is also 14.04.

You say:

> Should have said that my drive shows up in gparted with an exclamation mark

I think you may mean that a partition shows up with an exclamation mark. So that members can help you, take a screenshot of the open Gparted window (alt + PrtScrn) and attach it to a post.

---

### Post by kc110 on 2015-09-20
Hi, 
Thanks for your response.
I have been looking through the forums and think the problem may be related to having multiple drives.

---

### Post by coffeecat on 2015-09-20
@kc110, you can't drag and drop images into the message editor. Or rather, you can but you simply trigger a Firefox bug. Use the manage attachments button below the advanced message editor to upload an image to the forum server and add a thumbnail to your post. I'll tidy up your posts because the large amount of invisible base64 code you've accidentally added to your posts will cause the thread to lag for some people.

**Edit**: edited one post and removed two.

---

### Post by kc110 on 2015-09-20
[ATTACH=CONFIG]264541[/ATTACH]

---

### Post by kc110 on 2015-09-20
I was trying to install 14.04. I had shrunk the volume in Windows 7 and created a new partition.
Then switched back to 14.04 install and attempted to create /, swap and /home partitions.

Although I was allowed to do this, the result was the install process was aborted.

---

### Post by kc110 on 2015-09-21
Could this be something to do with multiple drives and multiple OS'es? Position of grub loader?


[ATTACH=CONFIG]264567[/ATTACH]

---

### Post by coffeecat on 2015-09-21
No, nothing to do with multiple OSs or grub. Your 900+ GB sdc2 partition is the problem. You say you've chkdsk'd your "main partition". Do you mean your Windows 7 C: partition, because that is what sdc2 looks as though it could be?

The other possibility is that you didn't shut down Windows 7 properly, but hibernated it. If that is the case, boot into Windows 7 and then shut it down properly and see if Gparted no longer shows the exclamation mark beside sdc2.

If that fixes it, **do not resize the Windows 7 C: partition with Gparted or the Ubuntu installer**. If you do you may very well make Windows unbootable. Once you are sure the Windows 7 partition is clean, you need to shrink it with the Windows Disk Management tool. Once you have free space on your sdc drive for Ubuntu, you can make the partitions you need for Ubuntu with Gparted or the "Something Else" installer window you show in your latest screenshot.

**Edit:** Just noticed this:

[quote=kc110]I was trying to install 14.04. I had shrunk the volume in Windows 7 and created a new partition.
Then switched back to 14.04 install and attempted to create /, swap and /home partitions.
[/quote]

There is no evidence of any Linux or swap partitions in either of your screenshots. The unallocated space on your sdc drive is only 2.71 MiB, so the shrinking either didn't work or was somewhat modest in size!

---

### Post by kc110 on 2015-09-21
[ATTACH=CONFIG]264571[/ATTACH]

I have successfully dual booted 14.04 and Windows although the exclamation mark still appears.
I ran chkdsk and defrag in Windows a couple of times and although Windows even at the start said there was no defragmentation, it still relocated may files over many passes. I then downloaded Defraggler and could visibly see more relocation of files, (as Windows XP used to show).

I physically disconnected the two extra drives and then began the shrink volume process again. Loaded 14.04 live boot and although the error mark still showed, I was able to complete the install process. I couldn't complete it originally due to error warnings and the boot and home partitions not showing properly.

The screen shot I first posted was after I had undone the preparation for installation and was intended to show the multiple drives, OS'es and error mark.

I would not call the matter "solved" as there is no clear process to follow.

I have reconnected the other two drives and booted in to both systems with no problems.

Thanks for your input and help.

kc

---

