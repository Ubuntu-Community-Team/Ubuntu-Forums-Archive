---
title: "Defragmenting windows from ubuntu"
date: 2016-01-18
forum: New to Ubuntu
---

### Post by gabriel66 on 2016-01-18
I have a little doubt and hope some of you can help me.

 I've been searching in some forums and websites, if there is the possibility to defrag the partition windows I have in my PC, from Ubuntu.

If there is not how to do that way, let me know how can I defragment my windows without opening it, the security mode or otherwise.

 Thanks in advance.

---

### Post by yancek on 2016-01-18
I don't think so.  The link below has a roundabout solution, post #4.  Same solution with a lot more detail at the second link.

[https://bbs.archlinux.org/viewtopic.php?id=126420](https://bbs.archlinux.org/viewtopic.php?id=126420)

---

### Post by ian-weisser on 2016-01-18
The safest answer we can give is that only Microsoft tools should be used to format, manipulate, or defragment NTFS partitions.
NTFS is a Microsoft-owned, proprietary format.
Microsoft does not support (or assist development of) any NTFS tools but their own.

This exact question is discussed in [http://askubuntu.com/questions/59007/defragging-ntfs-partitions-from-linux](http://askubuntu.com/questions/59007/defragging-ntfs-partitions-from-linux)
The tools suggested there are not Ubuntu software, and are not supported by the Ubuntu community.
If you choose to use them, backup your data first (which will, of course, defragment it), and use at your own risk.

Why do you wish to defrag an NTFS partition without using Windows?

---

### Post by maxinstuff2 on 2016-01-18
What version of Windows is it?

Windows will automatically defragment disks when it's needed in Windows 7 and up (IIRC), so you shouldn't need to do anything.......
Why the burning need to defrag?

---

### Post by Mark Phelps on 2016-01-19
With any modern SATA-III hard drive, defrag is going to make little or no discernable difference in runtime performance in MS Windows.

So, if your Windows system is running painfully slow, there is a different problem at work.  And for that, you need to consult the appropriate Windows forum for the version you are running.

---

