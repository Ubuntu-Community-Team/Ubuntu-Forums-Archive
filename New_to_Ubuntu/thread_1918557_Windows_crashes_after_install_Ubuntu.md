---
title: "Windows crashes after install Ubuntu"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by agnesetbert on 2012-02-01
Installed a sata-disk in a computer. Did a new install of windows XP and after that a Ubuntu-install. Now I want to startup windows but it gives a blue-screen. Have no clue anymore, did a defragmentation on windows, but that did not change, restarted 3 times, but nothing helpes. Can anyone help me?

---

### Post by varunendra on 2012-02-02
> **agnesetbert said:**
> Installed a sata-disk in a computer. Did a new install of windows XP and after that a Ubuntu-install. Now I want to startup windows but it gives a blue-screen. Have no clue anymore, did a defragmentation on windows, but that did not change, restarted 3 times, but nothing helpes. Can anyone help me?
If all you got was a blue screen (BSOD?), then how did you perform a defragmentation??:-k

Any chance of intentionally or accidentally changing to AHCI mode in BIOS AFTER installing XP? Try toggling that in BIOS.

---

### Post by cafedefrance on 2012-02-02
Defragmentation was done directly after installing Windows and before installing Ubuntu. Same situation today, with only Windows no crash and the computer works fine. Next step I will try is with Wubi just to see what happens. No BIOS changes done yet.

---

### Post by Bartender on 2012-02-02
Good question, varunendra, I didn't catch that...

My guess would be that Windows didn't get pushed aside correctly.

Since we're talking about a brand new install, I'd suggest doing exactly the same thing as I described in this [thread]("http://ubuntuforums.org/showthread.php?t=1915536&page=2").

Start over.  Use another PC (Windows or Linux, doesn't matter) to build a GParted LiveCD.

Take that CD to your PC.  Boot from it.  Wipe out all partitions.  Create a **primary ntfs** partition for Windows.  Whatever size you think you want for Windows.  

PLAN A: With whatever's left, the simplest thing to do is to make one primary ext4 partition.  

PLAN B: The next simplest thing to do is to make one extended partition, then create a logical ext4 partition inside the extended.  

PLAN C: If you decide you want to set up your Ubuntu partitions beforehand, the next simplest thing to do would be to **either** create one primary ext4 partition for the Linux OS (referred to as /), then an extended partition.  Inside the extended create a linuxswap partition, and a logical ext4 partition for /home.  **Or** put all 3 partitions inside an extended partition that takes up all remaining space after the ntfs partition.

If that last paragraph made your head hurt, then just go back to Plan A.  That'll work fine for now.

Creating the primary ntfs partition for Windows BEFORE installing, and formatting the rest as Linux file systems, makes for a much smoother installation.

Install Windows, make sure it's working, then boot from your Ubuntu CD and make sure it installs to the ext4 partition.  Don't let it take the entire HDD.  I haven't dual-booted since 10.04 so I can't tell you exactly what the installer will try to do.

---

### Post by varunendra on 2012-02-02
> **agnesetbert said:**
> Installed a sata-disk in a computer. Did a new install of windows XP and after that a Ubuntu-install. Now I want to startup windows but it gives a blue-screen. Have no clue anymore, did a defragmentation on windows, but that did not change, restarted 3 times, but nothing helpes. Can anyone help me?

> **cafedefrance said:**
> Defragmentation was done directly after installing Windows and before installing Ubuntu. Same situation today, with only Windows no crash and the computer works fine. Next step I will try is with Wubi just to see what happens. No BIOS changes done yet.
Umm.... the mystery continues..
Are you two, as it appears by the reply, the same person? If yes, are you planning to make each of your posts from a different user-ID? Please don't do this as my poor brain is already too confused! :(

> **Bartender said:**
> Good question, varunendra, I didn't catch that... I think you didn't catch the above mystery either ;)

As for the partition plan you suggested, I agree with most of it. Most of such issues that are caused due to partition manipulation, can be avoided by _installing OSes in predefined partitions_, instead of creating or modifying them 'during installation'. So it is a good idea to create all the partitions beforehand using gparted, then install XP first, Ubuntu later - only choosing the pre-decided relevant partitions, not creating or 'pushing' them during installation.

However, I have one comment and one suggestion (kind of slight modification to your plan C):

**_Comment_:** Why do we keep suggesting to create a gparted live cd when it is already included on the live media from which the user is going to install Ubuntu?

**_Suggestion_: **My preferred partition layout for XP-Ubu dual boot is:

[LIST=1]
[*]Partition 1: Primary NTFS for XP (20 to 60GB, depending upon usage)
[*]Partition 2: Primary Ext4 for Ubuntu (with root, home,... everything in it) (20-40GB, depending upon usage)
[*]Partition 3: Primary Swap (2GB, or equal to the amount of RAM if Hibernation is to be used, whichever is larger)
[*]Partition 4: Extended (in the rest of the space)
[*]Partition 5: Logical NTFS (for User Data. Being NTFS, it can be seen and used by both Ubuntu and XP)
[*]More logical NTFS partitions if required.
[/LIST]
The advantage of having a separate Data partition is that your data is not only visible to and usable by both OSes, it also remains safe and easily accessible in case one or both OSes crash and you need to wipe them out. I never keep my user data in my /home. As such, it only contains configuration files which don't occupy too much space. And thus even 26GB is usually plenty for my Ubuntu installations on dual-boot systems.


The advantage of Not creating a separate /home or /boot partitions is that it keeps things simple and avoids any disk-space troubles, providing maximum utilization of the space allocated to Ubuntu.


That said, it's just a matter of preferences and specific requirements. For a new user, I always suggest my choice since it keeps things both simple and flexible. Again, that's just my opinion. :D

---

### Post by lisati on 2012-02-02
> **varunendra said:**
> Umm.... the mystery continues..
Are you two, as it appears by the reply, the same person? If yes, are you planning to make each of your posts from a different user-ID? Please don't do this as my poor brain is already too confused! :(


Thread closed for staff review.

---

