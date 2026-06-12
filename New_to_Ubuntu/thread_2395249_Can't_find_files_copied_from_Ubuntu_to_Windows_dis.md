---
title: "Can't find files copied from Ubuntu to Windows disk partition when I log in Windows10"
date: 2018-06-28
forum: New to Ubuntu
---

### Post by shamiul93 on 2018-06-28
I use** Windows 10 and Ubuntu 16.04** on dual boot. 
I made a disk partition on windows and mounted it by** Ntfsfix** on Ubuntu. Then, I copied some files on this partition from Ubuntu. If I access this partition from Windows, I can not find it there. They are just not there. Just vanished. Even if I check properties of that drive, only files written from windows is counted. But In Ubuntu, I can see it. 
How can I solve this problem? Is there any command or software to do it?

---

### Post by coffeecat on 2018-06-29
You need to disable Windows fast startup. If you haven't done this, Windows does not shut down, but enters a hybrid hibernation state when you think you have shutdown. When you restart Windows, it will not recognise any changes made by Ubuntu to any partition it has access to. How to disable fast startup, and some useful basic information about this issue:

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

> **shamiul93 said:**
>  
I made a disk partition on windows and mounted it by** Ntfsfix** on Ubuntu.

Point of information: no, you didn't. ntfsfix is a basic Linux utility that can repair some ntfs problems. The actual Linux driver for ntfs is ntfs-3g.

---

### Post by yancek on 2018-06-29
If you created this partition in windows using a windows filesystem, I don't know why you would not be able to see the partition from windows.  Ordinarily when doing this, it should show up under Computer with a Drive Letter.  And as pointed out above, ntfsfix is a minor repair tool on Linux for ntfs filesystems.  You need to use the mount command in Ubuntu to either manually mount your windows partition or you need an entry in the Ubuntu /etc/fstab file to permanently mount that partition.

---

### Post by shamiul93 on 2018-06-30
> **yancek said:**
> If you created this partition in windows using a windows filesystem, I don't know why you would not be able to see the partition from windows. Ordinarily when doing this, it should show up under Computer with a Drive Letter. 
I'm quite new to Linux. I'm not sure if I stated my problem clearly. I made a partition study(D) on W10. Then I logged in Linux. In linux, I could see that there is a partition named study there but it couldn't be accessed. It said "sda5 can't be mounted...". So, I searched on google and found a solution that said, "use sudo ntfsfix /dev/sda5". I used it then I could enter into that partition from linux. Here we have to remember that, I created that partition from w10 but accessed by linux. Now, I copied some files to that partition. Then I shut down and restarted as w10. Now from w10, I went to "My Computer". There was my study(D) drive and I entered into that partition. I didn't find those files that I copied from linux. But other files which were already there before logging into linux at the first place were unchanged. Just those copied files from linux weren't there. How can I solve this problem? 

> **yancek said:**
> And as pointed out above, ntfsfix is a minor repair tool on Linux for ntfs filesystems. You need to use the mount command in Ubuntu to either manually mount your windows partition or you need an entry in the Ubuntu /etc/fstab file to permanently mount that partition. 
Could you please explain this part more clearly? I am quite new to linux. Some terminal commands or useful links would be very helpful. Thank you.

---

### Post by coffeecat on 2018-06-30
@shamiul93, did you read my post?

---

### Post by yancek on 2018-06-30
In all likelihood, the reason you got the message could not be mounted is because it was left hibernated.  See post two above and the links posted.  Windows default is to hibernate so the system boots faster.  Using ntfsfix is not a solution.  You need to disable all the fast boot and hibernate options if you want to access a windows data partition from Linux.  I"m not aware of any Linux OS which will mount a hibernated partition.

---

### Post by vanadium on 2018-07-01
When Windows hibernates, it does not fully close the ntfs partition. Linux won't mount a not properly closed disk. You need to disable fast start up and fully shut down Windows before you access that disk with Ubuntu, as explained in post #2.

---

