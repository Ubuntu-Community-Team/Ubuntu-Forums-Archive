---
title: "How to format a Sata SSD drive formally for Windows for use on Linux"
date: 2024-07-26
forum: New to Ubuntu
---

### Post by davel-999 on 2024-07-26
Hello folks. I just started using Ubuntu recently. Previous OS was Win 10. I have an external SATA USB hard drive I want to be able to use for Linux storage. Currently, it has an old Windows OS on it. I tried to format the drive with Linux, but it will not format. Probably because of permission issues. Can I force a format through the terminal, and what are the commands to do so? Or is there some other means to do so. What form should the format take to be able to be used on Linux? I have a desk top with Win 11 on it if needed in some format way. Thanks for any help I can get.

---

### Post by TheFu on 2024-07-26
It isn't a permission issue. It is a file system safety issue.  At least that's the most likely reason.

Linux will not touch any "open" file system.  MS-Windows has been leaving file systems "open" by default since Win8.  Connect the device to a MS-Windows machine and "eject" it. There's also a setting to prevent MS-Windows from leaving file systems open.  You can look that up on most MS-Windows how-to websites.

After that, you can create a new partition table (choose GPT), then add at least 1 partition, and format that partition as ext4.  **Gparted** is the tool for this. There are others, but no need to make it hard.   BTW, after you format with ext4, be certain to add a useful LABEL to the file system. This can be used to mount the storage where you want it much easier than having to use a UUID.  Make the LABEL, short, no spaces, no mixed case, and descriptive for the purpose of the file system.

Of course, if the disk is failing, partitioning and laying down a file system may not work.

Stop thinking of "drives" and start thinking of "file systems" which should be inside partitions.  Those "drive letters" used in MS-Windows?  Those are really partitions, not drives. MSFT has been over-simplifying things since the early 1980s.

---

### Post by currentshaft on 2024-07-26
> **davel-999 said:**
>  I tried to format the drive with Linux, but it will not format. Probably because of permission issues.

What does "will not format" mean? What does "permission issues" mean? Please be as unambiguous as possible when asking strangers for help.

---

### Post by ActionParsnip on 2024-07-26
Write a new file table to the disk (This will lose ALL data) then set it up as you need. You can use GpartEd for this

---

### Post by davel-999 on 2024-07-26
Thank you for the information and willingness to help.

---

### Post by davel-999 on 2024-07-26
Thank you for the in-depth information and willingness to help a newbie.

---

### Post by TheFu on 2024-07-26
> **davel-999 said:**
> Thank you for the information and willingness to help.

Who?  If you don't quote someone, we can't tell to whom you are writing.

Ideally, the shortest answer worked for you (I think it should and it is shorter than mine). Of course, both assume you don't have **anything** on the storage you want to keep.

When you are done, I think you'll find it was 2-4 minutes of effort that you posted about. I'd be surprised if it takes any longer.

---

### Post by davel-999 on 2024-07-26
> **TheFu said:**
> It isn't a permission issue. It is a file system safety issue.  At least that's the most likely reason.

Linux will not touch any "open" file system.  MS-Windows has been leaving file systems "open" by default since Win8.  Connect the device to a MS-Windows machine and "eject" it. There's also a setting to prevent MS-Windows from leaving file systems open.  You can look that up on most MS-Windows how-to websites.

After that, you can create a new partition table (choose GPT), then add at least 1 partition, and format that partition as ext4.  **Gparted** is the tool for this. There are others, but no need to make it hard.   BTW, after you format with ext4, be certain to add a useful LABEL to the file system. This can be used to mount the storage where you want it much easier than having to use a UUID.  Make the LABEL, short, no spaces, no mixed case, and descriptive for the purpose of the file system.

Of course, if the disk is failing, partitioning and laying down a file system may not work.

Stop thinking of "drives" and start thinking of "file systems" which should be inside partitions.  Those "drive letters" used in MS-Windows?  Those are really partitions, not drives. MSFT has been over-simplifying things since the early 1980s.

It turns out that G parted is an OS and must be burned to a CD. I have a desk top that does not have a CD Rom drive. Is there another tool that does not require burning as CD?

---

### Post by Dennis N on 2024-07-26
> **davel-999 said:**
> It turns out that G parted is an OS and must be burned to a CD. I have a desk top that does not have a CD Rom drive. Is there another tool that does not require burning as CD?

If you are using Ubuntu to work from, **gparted** is an application that you can install from Ubuntu Software or App Center - whichever you have on your system. There is no need to burn it on a CD. Then, use it to create a new GPT partition table on the external disk, and the desired partition(s).

---

### Post by yancek on 2024-07-27
If you still have the device (DVD or USB) you used to install Ubuntu, the gparted software is already on that device.  You were asked several questions in earlier posts which if answered, would have given members here useful information to help you but you chose not to answer them.  If you want help, post details and do not give cryptic responses.

If you don't have the install DVD/USB, you can install gparted to modify your external drive with one simple command from a terminal:

```
sudo apt install gparted 
```

---

### Post by TheFu on 2024-07-27
> **davel-999 said:**
> It turns out that G parted is an OS and must be burned to a CD. I have a desk top that does not have a CD Rom drive. Is there another tool that does not require burning as CD?

**Gparted** is just an application. Most Ubuntu ISOs include it.  You can put an ISO onto a flash drive.  Heck, the same ISO you used to install Ubuntu probably has it. Use that and boot into "Try Ubuntu" mode.  Then you can partition any disk as much as you like. Be careful, as data loss is likely. Don't pick the wrong partition, if you care about the data it holds.

There may be a gparted-centric ISO. You don't need that.

---

### Post by davel-999 on 2024-07-27
> **TheFu said:**
> Who?  If you don't quote someone, we can't tell to whom you are writing.

Ideally, the shortest answer worked for you (I think it should and it is shorter than mine). Of course, both assume you don't have **anything** on the storage you want to keep.

When you are done, I think you'll find it was 2-4 minutes of effort that you posted about. I'd be surprised if it takes any longer.

Who? Those who helped me as opposed to those who did not.

---

