---
title: "Re: No partition available during installation"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Muzzab on 2011-09-15
OK so I'm was trying to install windows 7 Ultimate along side Ubuntu 10.04. Windows has installed no problem but when I boot the computer to install Ubuntu, step 4 takes me not to the screen asking me if I would like to install Ubuntu alongside windows as usual, but to the screen to edit and select the partitions to install Ubuntu on. The problem is there is no partitions available to select or edit. I tried running the dmraid as mentioned earlier to solve the problem but it says nothing is blocked. 

I have tried Ubuntu 9.10, 10.04, 11.04 as well as the alternate versions and Fedora on both cd and usb but always the same thing. I have searched the forums but found nothing that helps. That's all the information I have, sorry I'm not a computer genius. It's always worked no problem in the past.

Any info would be appreciated.
Cheers.

---

### Post by Daveth on 2011-09-15
was the windows 7 install a standard one to a standard hard drive, or does the pc have one of those proprietary recovery partitions? Is it set up as a RAID configuration, or a standard arrangement? Might also be worth noting the PC details, in case it is a hardware issue.

---

### Post by srs5694 on 2011-09-16
I posted a reply to your question [here.]("http://ubuntuforums.org/showthread.php?p=11258132#post11258132") Cutting-and-pasting my reply:

You've probably got damaged partition table data or leftover GPT data.  (Old RAID data is another possibility, but it sounds like you've taken  the steps to remove that.) My [FixParts program]("http://www.rodsbooks.com/fixparts/")  will take care of most of the partition table errors that cause this  problem. If you want more diagnosis before trying that, please boot the  Ubuntu installer to its "try it now" mode, launch a Terminal window, and  type:

   ```

    sudo fdisk -lu 

```
Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for  legibility. That will probably give us the information we need to  positively identify the problem. (If not, further tests will be  necessary, perhaps revisiting the leftover RAID data possibility.)

---

