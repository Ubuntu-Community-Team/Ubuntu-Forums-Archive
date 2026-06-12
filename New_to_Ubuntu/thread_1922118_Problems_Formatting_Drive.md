---
title: "Problems Formatting Drive"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by Saminthebuilding on 2012-02-08
Hi all

Windows XP on my PC is shot to pieces it seems. So I downloaded Ubuntu after some advice from a friend. This worked! I accessed and backed up all the files i needed to save (As XP just wouldn't load at all). I've tried to completely reformat the drive so i could reinstall a new version of Windows but it give me this error message... "Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=1048576"

Any help to successfully reformat would be massively appreciated.

Thanks

---

### Post by pixiq on 2012-02-08
You have already done the first necessary thing: backup :KS

So now I suggest that you boot from your Ubuntu install CD or USB drive, and run gparted to edit your partitions (start by deleting) and then make what you want. Do you want a dual boot system with Windows and Ubuntu: then you should make a primary partition of suitable size for windows, and an extended partition for Ubuntu and common data.

Start installing Windows, let Windows create its file system! Install Ubuntu afterwards!

Good luck :)

---

### Post by Saminthebuilding on 2012-02-08
Thanks for your help Pixiq! A few problems...

I currently have Gparted open but it is not recognising my HDD :S

---

### Post by coffeecat on 2012-02-08
> **Saminthebuilding said:**
> 
I currently have Gparted open but it is not recognising my HDD :S

Can you clarify what you see when you open Gparted? Is there an error message? Is it that /dev/sda is not listed at all in the little drop down near the top of the Gparted window? or is it that Gparted is giving you an "unallocated" message? If the latter, that means that either there are no detectable partitions or that the partition table has been corrupted. Both of these are easily fixed.

---

### Post by Saminthebuilding on 2012-02-08
Thanks for your help Coffeecat, massively appreciated.

It basically does a search when I run Gparted and comes back with nothing. It just states no devices detected. Which is strange considering I backed up my data from that HDD... Thanks again!

---

### Post by Saminthebuilding on 2012-02-08
Also, I just rebooted and it stated that dev/sda signal was terminated..

---

### Post by pixiq on 2012-02-08
Your problems with Windows might be caused by different things. One is that your HDD is failing, that you have read/write errors or bad sectors. If the computer and HDD are new enough, you can check in your BIOS menu system, if there are S.M.A.R.T. errors. You can also check that with the ***disk utitlity*** (from the menu) alias ```
palimpsest
``` (from the command line). This might also show more than gparted about the partitions and file systems. If this is the case, please make a screen-dump file and attach the file to your next post.

It could also be that the partition table or file system is corrupted logically, although the disk hardware is still healthy. Please post the output of the following command, that should display partition sizes and file systems
```
sudo fdisk -lu
``` It might show more than gparted.

---

### Post by Bodsda on 2012-02-08
Do you get a similar error if you use the Window installation CD to delete and recreate the partitions?

Bodsda

---

### Post by coffeecat on 2012-02-08
+1 to all that pixiq and Bodsda said. Also, look in your BIOS settings. Is the hard drive detected by the BIOS? If not and this is a desktop, open it up and make sure the data cable is attached securely at both ends and the power cable is attached to the drive properly.

---

### Post by Saminthebuilding on 2012-02-08
Thanks to all of you. Your help is greatly appreciated.

@Pixiq: Ive tried the "sudo fdisk -lu" cmd but nothing happens. I'ts definitely noticing there is a HDD connected. And when it boots up the HDD is definitely spinning. 

@Bodsda: Windows does not let me make or delete any partitions when I boot the PC with the 7 disk. 

Thanks!

---

### Post by pixiq on 2012-02-08
> **Saminthebuilding said:**
> Thanks to all of you. Your help is greatly appreciated.

@Pixiq: Ive tried the "sudo fdisk -lu" cmd but nothing happens. I'ts definitely noticing there is a HDD connected. And when it boots up the HDD is definitely spinning. 
...

Did you try it from a terminal window, so that you could see the output?
Start the terminal window with [I][B]ctrl + alt + t

[/B]Edit: If you get no output at all (before you get the next prompt), I am afraid, that your HDD has failed, that is does not work, even if is spinning)[/I]

---

### Post by Saminthebuilding on 2012-02-08
Also, I am just installing Teamviewer on my machine... If anyone would be able to help by logging on I wouldn't mind sending some money through paypal to say thanks!

---

### Post by Saminthebuilding on 2012-02-08
My worst fears! Well thank you Pixiq, youve been a massive help. Suppose my css day is not today! 

Regards

---

### Post by pixiq on 2012-02-08
> **Saminthebuilding said:**
> Hi all

Windows XP on my PC is shot to pieces it seems. So I downloaded Ubuntu after some advice from a friend. This worked! I accessed and backed up all the files i needed to save (As XP just wouldn't load at all) ... 
Cheer up, it could have been much worse. Your friend gave you good advice and you saved the data while the drive was still working :-) That is worth much more than the price of a new HDD and the trouble to reinstall your system.

---

