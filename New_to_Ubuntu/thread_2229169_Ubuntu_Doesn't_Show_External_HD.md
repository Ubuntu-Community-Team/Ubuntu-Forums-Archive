---
title: "Ubuntu Doesn't Show External HD"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by webmanoffesto on 2014-06-11
I have a Windows machine, but I'm running Ubuntu off of an External HD. Whenever I reboot the computer GREP lets me choose Ubuntu or Windows. 

I want to move some files to the External HD that Ubuntu 13.10 is on. It's a 1 TB Ext HD, so I'm sure there The problem is that I can't find that External HD. I look in /mnt and I see another Ext HD (Seagate), but I don't see the 1 TB Transcent Ext HD.  

I had the same problem while using Windows. 

I swear that I am running Ubuntu off of the drive I can't find. Why is that? How do I resolve this problem?

I am not using the Ubuntu installer for Windows / WindowsDualBoot.

---

### Post by Vladlenin5000 on 2014-06-11
The drive from where you're running Ubuntu is also the one where your Ubuntu partitions are. Assuming you installed using the default options and told the installer to use that external HD then you have on that drive two partitions - / (root) and swap - and nothing else. Now, when you boot Ubuntu it uses those partitions with the aforementioned mount points therefore it won't show as an additional external drive because that IS your system drive and without further actions you can immediately copy to/from whatever is in your user area -> /home/yourusername where "yourusername" is, obviously, your username, the one you defined during the installation and the one you use to login.

The reason why you can't "see" it in Windows is because Windows cannot "see" Linux partitions and there's nothing else but Linux partitions in that HD. The truth is Windows actually detects (should detect) the external HD but it won't show any new drive in the file manager. You can "see" the drive (marked with "unknown" file systems) in Windows Disk Manager tool.

Bottom line: Everything is working as expected, no problem, therefore nothing to "resolve" here. Please mark this thread as solved using the thread tools in your first post.




PS - It's GRUB, not GREP.

---

### Post by yancek on 2014-06-11
You mention having windows but not which release??  Do you have windows on an internal hard drive?  You mention a Seagate and Transcent so that would mean you have 3 hard drives, correct.  Ubuntu is on the 1TB Transcent?  Did you look in the /media directory as that is where different partitions usually show.  You would need to click on them to access them and they are identified by uuid, a long series of letters/numbers.

You indicate you want to move files to the drive which has Ubuntu, does that mean to the Ubuntu partition(s)?  Where would you be moving them from?  As stated above, windows doesn't read/write or recognize Linux partitions although you may be able to install third party software which 'may' be able to do that.

---

### Post by webmanoffesto on 2014-06-12
Thank you.

---

