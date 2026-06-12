---
title: "Dualboot Acer Apsire 5750Z help"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by ThunderMoon99 on 2013-09-15
[COLOR=#000000]Hello, my girlfriend wants me to dual boot Ubuntu along side her Windows 7 on her Acer Aspire 5750Z laptop, but I have encountered a few snags on the way. First I think there might be something wrong with the wifi when the live usb is on wifi doesn't register until I press continue after the checks window. Second, it doesn't show when re sizing the hard drive what will be Windows and what will be Ubuntu it also doesn't let me move the slider and it says it's some weird hdd. Thirdly after I cancel everything and boot back into Windows it says that "it is not a genuine copy of Windows 7 and that there is a corrupted disk". Lastly I can not partition the hard drive within Windows because A everything that I have see says I need to have a backup cd for windows (which I don't have) and I need to reinstall Windows after I dual boot it with Ubuntu. Which I can't do, that is too complicated and scary for me. Thanks in advance.
[EDIT]
This has also been posted in the installation board but so far has received no attention[/COLOR]

---

### Post by squakie on 2013-09-15
If ou want a true dual boot:  a menu (grub) presented at boot where you select which operating system you want to boot, then you will need to follow a standard installation procedure like are posted all over.

The first thing you will want to do is defragment the hard disk in Windows a couple of times before starting so you have less chance of losing something.  Back up anything important for the "just in case".

To see disk allocation, you need to select "other" or "something else" at the disk partitioning section of the installation.  You will be able to resize your Windows partition (to make room for Ubuntu) and it will show as NTFS.  Then you will allocate the new partition(s) for linux in the space you freed up.  This will be graphical and you can see what you are doing.

As for your wireless and linux:  usually it's just the need to install a driver.  To be prepared in advance, search these forums and the net with your wireless adapter make and model.  Some may have different chipsets for the same model depending on revision number.

It's also quite possible that your system may be using EFI/UEFI in the BIOS.  Don't start anything until you find that out and post back here for further instructions in that regard.

---

### Post by ThunderMoon99 on 2013-09-16
Wow, thanks. Haha I didn't realize it was that easy. :)

---

### Post by BlinkinCat on 2013-09-16
Hi,

Glad all is well!

In case you are unaware -  [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

oops - seems you were aware!

---

