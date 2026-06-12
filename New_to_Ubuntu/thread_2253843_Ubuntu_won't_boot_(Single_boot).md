---
title: "Ubuntu won't boot (Single boot)"
date: 2014-11-22
forum: New to Ubuntu
---

### Post by rvu95 on 2014-11-22
I've tried bootrepair or using manual command to check the grub2. Here's my boot info  summary:   [http://paste.ubuntu.com/9186069/](http://paste.ubuntu.com/9186069/). It must be noted that I'm using UEFI mode for my Ubuntu (single boot) and at first I've no problem with that.  Any help will be useful, thanks.

---

### Post by yancek on 2014-11-22
What exactly is the problem and what do you want to check about Grub2?

---

### Post by oldfred on 2014-11-22
What brand & model computer.
Some only boot Windows. 
Since not using Windows you can use efibootmgr to make UEFI entry read Windows but boot grub, if you have a vendor that modified UEFI to only boot Windows.

See option d:
Although some others may also work.[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
http://ubuntuforums.org/showthread.php?t=2234019[/URL]

---

### Post by rvu95 on 2014-11-23
My laptop can't load the grub and always looping to find os. I just wanna check if the grub has been installed properly.

---

### Post by rvu95 on 2014-11-23
Samsung K-lite series, I've installed ubuntu before and nothing goes wrong at first,  the problems start appear about 2 days ago

---

### Post by oldfred on 2014-11-23
What else happened two days ago?
Did you install new drivers, system crash, anything?

Can you boot live installer?
If so install Boot-Repair and post link to its summary report. Best not to run auto-fix until someone has reviewed report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Other Samsung, may be similar?
 Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

---

### Post by Bloodcage on 2014-11-23
had a similar problem. after installing ubuntu the bootloader couldn't be installed first. then a miracle happened and it was able to be being installed on sda1 but it couldn't boot after the installation. I did the same procedure 2 times and out of a sudden it worked ....

---

### Post by rvu95 on 2014-11-23
I'm accidentally go to the BIOS menu, I change nothing but my laptop become strange since then. Thanks, I'll try it.

---

### Post by rvu95 on 2014-11-23
Is that the exact same method you've used back then?

---

### Post by rvu95 on 2014-11-24
Thanks for your help, finally I can handle it :p

---

