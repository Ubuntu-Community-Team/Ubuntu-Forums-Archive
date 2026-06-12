---
title: "Finally able to leave Microsoft and join Linux family - advice on best procedure"
date: 2015-08-20
forum: New to Ubuntu
---

### Post by makem2 on 2015-08-20
I have been testing xubuntu on a previous machine which I have just swapped for a new Windows 8.1 'optimized for windows 10!' Toshiba laptop.

I have removed all of the bloatware and it is now partitioned as follows:

1. 1GB system
2 100mb system
3. C: Windows 8.1 - 97.8GB
4. D: Data - 722.46GB
5. Unallocated - partition for xubuntu
6. Recovery - 12.32GB

For a period of one month I want to leave the partitions as they are whilst I confirm the machine does not need to be replaced as was the previous HP one. During that month I will use xubuntu on the unallocated partition.

I need guidance on the best way to approach the change-over to all Linux.

The current data partition has 150GB of data and my windows profile is with that data having been moved to D partition. That data is backed up daily to a Raspberry Pi with two 1T hard drives

I would like to achieve something on similar lines to what I have now, OS on a partition, Home on another. This machine has 16GB of RAM and I anticipate using a RAM drive to speed up some things and to 'lose' the data when the drive is shut down.

[edit] PS. If anyone following this buys a Toshiba and finds they are unable to shrink the C: partition to less than some 450GB because 'Windows 8.1 needs that'. 1st level Toshiba support told me that! 2nd level  said just ignore and re-partition using 3rd party software after I said the machine was not fit for purpose if 400GB was unusable for 'safe' data storage. A lot of posts say it may break the system if you reduce the C: partition.

---

### Post by grahammechanical on 2015-08-20
The first thing that you must do is read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Second, look around the forum for those threads from others who have installed Ubuntu and then upgraded to Windows 10. See, what has happened to other people and understand that you are becoming an early adopter. You will end up having more experience in this matter than many of us who reply to threads on this forum. Certainly more experience than me. What will you do with that experience? Help others? Yes, please.

Third, if you are going to upgrade to Windows 10 do it before installing Xubuntu/Ubuntu.

Fourth, with all that RAM it is tempting to think of RAM drives but I think that you are thinking "Windows" thoughts and not "Linux" thoughts.


Regards.

---

### Post by v3.xx on 2015-08-20
> This machine has 16GB of RAM and I anticipate using a RAM drive to speed up some things and to 'lose' the data when the drive is shut down.

This will work only if your installing 14.04

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

Support is limited

---

### Post by makem2 on 2015-08-20
> **grahammechanical said:**
> The first thing that you must do is read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Second, look around the forum for those threads from others who have installed Ubuntu and then upgraded to Windows 10. See, what has happened to other people and understand that you are becoming an early adopter. You will end up having more experience in this matter than many of us who reply to threads on this forum. Certainly more experience than me. What will you do with that experience? Help others? Yes, please.

Third, if you are going to upgrade to Windows 10 do it before installing Xubuntu/Ubuntu.

Fourth, with all that RAM it is tempting to think of RAM drives but I think that you are thinking "Windows" thoughts and not "Linux" thoughts.


Regards.


Sorry, maybe I did not make myself clear. I have no intention of returning to windos, in fact the thought of HAVING at some stage to use 10 makes me shudder. Maybe there is no way to use, or a need to use a ram drive from Linux but that I will find out later.

---

### Post by makem2 on 2015-08-20
> **v3.xx said:**
> This will work only if your installing 14.04

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

Support is limited

Thank you. I have not intention of running the OS from a ram drive but will investigate the possibility of using ram for browsing and any package which has data that does not need storing such as internet history. It was just a thought as somone pointed out to me that using ram for these and some other purposes in windos was useful. I popped the mention in my post to bring up and suggestions if it was already a 'done thing' as I am new to Linux.

What I am really after but obviously didn't make it clear, is guidance how to transfer painlessly as possible and avoiding a complete new install, from windos to linux.

---

### Post by MartyBuntu on 2015-08-20
Image the drive, turn Secure Boot off in UEFI and have your Ubuntu installation wipe and prepare the entire disk for you.

---

### Post by makem2 on 2015-08-21
> **MartyBuntu said:**
> Image the drive, turn Secure Boot off in UEFI and have your Ubuntu installation wipe and prepare the entire disk for you.

Thank you.

However, I believe Ubuntu has an ability to deal with UEFI. (paid) I think it also involves 'fast boot'. I had an install of xubuntu on my previous HP machine without turning off UEFI. Is there a gain in turning it off regardless?

---

### Post by yancek on 2015-08-21
You are right that Ubuntu can easily be installed as UEFI.  The previouos poster may have been suggesting MBR install/boot as being simpler.  There are often multiple options relating to 'fast boot' and hibernation and it varies by manufacturer.  I don't use UEFI on my computers so can't suggest anything else.

---

### Post by cariboo on 2015-08-21
I have a toshiba laptop running Wily (15.10) and Windows 10. You already have unallocated space on your hard, so use Something else when you get to the partitioning option to set your partitions. On my system the partitions look like this:

```

Device         Start        End    Sectors   Size Type
/dev/sda1       2048    2099199    2097152     1G Windows recovery environment
/dev/sda2    2099200    2303999     204800   100M EFI System
/dev/sda3    2304000    2566143     262144   128M Microsoft reserved
/dev/sda4    2566144  419951225  417385082   199G Microsoft basic data
/dev/sda5  419952640  439481936   19529297   9.3G Linux filesystem
/dev/sda6  439482368  447295487    7813120   3.7G Linux swap
/dev/sda7  447295488 1465147391 1017851904 485.4G Linux filesystem
```

this is a UEFI install, that has performed flawlessly since April.

---

### Post by monkeybrain20122 on 2015-08-21
> **makem2 said:**
> Thank you.

However, I believe Ubuntu has an ability to deal with UEFI. (paid) I think it also involves 'fast boot'. I had an install of xubuntu on my previous HP machine without turning off UEFI. Is there a gain in turning it off regardless?

There are three things, UEFI, secure boot and fast boot. If you are not dualbooting with Win just go to legacy mode (BIOS) then it is all simple. I a a firm believer of not adding complications if there are no clear advantages.

---

### Post by makem2 on 2015-08-22
> **monkeybrain20122 said:**
> There are three things, UEFI, secure boot and fast boot. If you are not dualbooting with Win just go to legacy mode (BIOS) then it is all simple. I a a firm believer of not adding complications if there are no clear advantages.

Thank you for explaining.

---

