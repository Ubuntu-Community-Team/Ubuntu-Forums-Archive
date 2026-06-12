---
title: "Installation failed?"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by ke5wxn on 2012-03-03
Trying to install on an asus k8v-mx board with 512mb ram. Checked disk and memory all ok. I get an installation failed message, the installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem. It then freezes and requires a reset. I am new to linux but have installed it briefly on other machines without this issue. Thank you for your patients.

---

### Post by Bucky Ball on 2012-03-03
Welcome!

What size partition are you using to install to? 
When does this message appear? At what stage of the install?
Did you check the CD for defects before attempting install?
Which release are you attempting to install? Try 10.04 LTS. That is the most stable and you can work from there.

When you boot from the install CD and get to the options, could you hit F6 and choose 'nomodset' and see if that makes a difference?  

When you boot from the CD and 'Try Ubuntu' does that work ok?

---

### Post by NikTh on 2012-03-03
see this thread --> [http://ubuntuforums.org/showthread.php?t=1491117](http://ubuntuforums.org/showthread.php?t=1491117)   follow the mini how to , maybe help you.

---

### Post by ke5wxn on 2012-03-03
> **Bucky Ball said:**
> Welcome!

What size partition are you using to install to? IDE HD at 13.6 gigs that has xp on it. did not get an option to format or create partitions. 

When does this message appear? After the error codec not read with some hex numbers after.I will try to get the exact message on reboot and reinstall.
 At what stage of the install? Click install wait then previous error then desktop with error or frozen

Did you check the CD for defects before attempting install? Yes.

Which release are you attempting to install? 11.10
 Try 10.04 LTS. That is the most stable and you can work from there. Will try to download.

When you boot from the install CD and get to the options, could you hit F6 and choose 'nomodset' and see if that makes a difference?  

When you boot from the CD and 'Try Ubuntu' does that work ok? Boots to a desktop and freezes and requires a reset also. 
Thank you!

---

### Post by ke5wxn on 2012-03-03
Will try parted magic next Thanks!

---

### Post by Bucky Ball on 2012-03-03
Okay, I have a feeling you don't have any free space to install Ubuntu to. Where are you intending to put it? 

Are you wanting to dual-boot with Windows (this means Win on one partition, Ubuntu on others) or are you using a Wubi install (which installs Ubuntu inside Windows like any other Windows program - intended for trying, not a permanent solution, I wouldn't go there).

Make sure you have free space to actually install Ubuntu to. When you get to the partitioning stage of the install choose 'Something Else' which will let you manually partition. Then you can instruct the installer to install Ubuntu into the free space. You can also delete partitions and create them in here so BE AWARE that your Win install will be on a partition with the filetype NTFS. Don't go there. Just leave that partition alone.

As for 'Try Ubuntu' freezing, have you set the F6 option 'nomodset' *then* 'Try Ubuntu'?

* Just saw your last post. You don't need parted magic. You can do all partitioning as part of the install. You're deviating from the path there, unnecessarily complicating things. ;)

---

### Post by ke5wxn on 2012-03-03
Thanks bucky. I have 4 or 5 spare boxes here and i am wanting to get away from ms so there is no problem blowing away xp but have not found a way to partition or format. selected nomodset then push esc then select install enter. splash screen. codec_read: codec not valid. desktop. frozen. Any other info I can provide?

---

### Post by Bucky Ball on 2012-03-03
Boot from the Ubuntu CD, hit F6 and choose 'nomodset', select 'Try Ubuntu'.
At the desktop open 'Partition Editor' (Gparted), delete all partitions. 

Back at desktop, hit the 'Install Ubuntu; option.

---

### Post by ke5wxn on 2012-03-04
Bucky, following your last instructions I can get to desktop then it freezes with the caps lock and scroll lock lights flashing on the keyboard. There is no way for me to attempt to find Gparted. Thank you.

---

### Post by lindsay7 on 2012-03-04
You can download Gparted from their web site and burn an ISO image to a cd.  It will boot itself on start up and all of the partitons on the disk will be unmounted. so you can work on all or any of them.

---

### Post by Bucky Ball on 2012-03-04
> **lindsay7 said:**
> You can download Gparted from their web site and burn an ISO image to a cd.  It will boot itself on start up and all of the partitons on the disk will be unmounted. so you can work on all or any of them.

+1. This could be the way to go so you can see how your hard drive is set up. You could also try the F6 options again, but this time try 'acpi=off'.

---

### Post by ke5wxn on 2012-03-06
Update! After trying Gparted and having it freeze and trying a different video card with a whole page of errors I have decided to try a whole different box. So far I have encountered a completely different Try or Install screen and am making progress deleting xp and installing Ubuntu! Thanks for the help and I will be back on the original box after I am successful on this one.

---

