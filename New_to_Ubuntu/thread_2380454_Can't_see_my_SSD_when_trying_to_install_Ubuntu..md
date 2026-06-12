---
title: "Can't see my SSD when trying to install Ubuntu."
date: 2017-12-18
forum: New to Ubuntu
---

### Post by guilhermefalcao on 2017-12-18
Hi guys, 
I just bought an Asus Strix gl753g and I really need to install Ubuntu on it. 
Every time I get to the step that I need to choose which partition I will place my Ubuntu, it doesn't show the SSD option, only the HDD. 

Details:
[LIST]
[*]This notebook already has a Windows 10 installed on this same SSD, it came from the store.
[*]I need to keep this Windows (for gaming)
[*]specifications: 2.8GHz Intel Core i7-7700HQ quad-core processor and 16GB of RAM, 1TB hard drive, 128GB solid-state drive, NVIDIA GeForce GTX 1050 Ti.
[/LIST]

Any idea of what I can do? 

Thank you in advance.

---

### Post by cmcanulty on 2017-12-18
I believe first you have to resize the windows partition from PC rt cl manage computer from within windows. Then use the extra space to create a new partition, then retry installing  ubuntu on the new partition.

---

### Post by yancek on 2017-12-18
Are you using the manual installation option; "Something Else".  You need to do that because if you don't and something goes wrong, you will have no clue what it was.  If you have any personal data on your windows that is important to you, you need to first back it up to another drive.  If windows is on the SSD, it is almost certainly taking up all the space on the drive so you need to shrink the windows partition as suggested above.  Best to do this with the windows tool Disk Management.  If you have been using windows for some time, you should probably run Disk Defragmenter prior to shrinking the windows partition.  After shrinking the partition, re-boot and run the chkdsk /f command on windows.

One other thing you need to be aware of is that a default install of windows 10 uses UEFI so I would suggest you read the Ubuntu documentation at the link below on dual booting with UEFI and save yourself a lot of grief later on.  I is particularly important if you are like the 90% of home computer users who have never installed any operating system.  You will need to identify the correct drive during the install so familiarize yourself with Linux drive/partition naming conventions. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by leunam12 on 2017-12-18
It seems to me that your Windows is hibernated and Linux cannot access it, you have to disable it first.
On Windows press WindowsKey+X and choose "command prompt(Admin)" from the menu (or Windows Powershell (admin) depending on your Windows version).
Grant authorization and then type: "powercfg &#8211;h off" (without quotes) and press enter. That command will disable hibernation on Windows.
Then reboot and the SSD drive should be available and the option to install Ubuntu alongside with windows should be available.
However, as suggested above, it is better to shrink the partition in windows using disk manager and run CHKDSK on the drive, and then boot Ubuntu installer
and choose "something else" and install on the newly created partition. It is better to work on NTFS drives using Windows tools.

But please, get Clonezilla first (clonezilla.org) and make a backup copy of your SSD before you attempt to do anything.

---

### Post by guilhermefalcao on 2017-12-18
Awesome! Right now I'm at work. As soon as I get home, I'm going to try what you guys suggested. 
I'll update the thread with the results. 
Thank you all!

---

### Post by guilhermefalcao on 2017-12-19
Hey, guys. 
It worked. I did everything leunam12 said and it worked. Thank you!

---

### Post by leunam12 on 2017-12-19
Great! would you now please mark the thread as SOLVED? Thank you.

---

