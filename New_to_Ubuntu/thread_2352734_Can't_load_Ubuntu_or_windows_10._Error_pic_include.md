---
title: "Can't load Ubuntu or windows 10. Error pic included"
date: 2017-02-15
forum: New to Ubuntu
---

### Post by agielchinsky on 2017-02-15
I just installed Ubuntu onto a desktop that already had windows 10. Ubuntu worked fine, but when I tried to restart and use Windows I was able to get to my desktop but the screen kept flashing. I shut down and now I can't use Ubuntu or windows. I've attached the Ubuntu error message. Any help would be much appreciated.

I've also attached a picture of my hard drive partition from when Ubuntu was working.

Thanks

---

### Post by termibuntu on 2017-02-15
hi. it seems that ubuntu is finding your partitions, but they may be damaged. you could also have done something wrong while they were running. you could check the partitions. if you have got a live usb or disk, boot from it and open gparted and see if there os an exclamation mark meaning the partition is damaged. if you dont have a usb or disk, get a iso of ubuntu and burn it to the removable media. for a usb flash drive, use unetbootin or pendrivelinux or rufus for windows to burn the iso. for linux and mac os x, use unetbootin to burn the iso. hope this helps to get your ubuntu and windows back.

---

### Post by leunam12 on 2017-02-15
Step one in troubleshooting is to fire up your live USB stick and open the "Disks" utility and go to the S.M.A.R.T. information to see if your drive has errors and re-allocated sectors, incorrectable errors in data, or sectors pending re-allocation. If this is the case, then the smartest thing to do is backup your data, get a new drive and reinstall

---

### Post by martemarziano on 2017-02-15
My guess would be that if you can boot into your Windows via Bios then there is no damage done to your Windows installation. In that case you can just reinstall Ubuntu and see if that would fix things up.

---

### Post by agielchinsky on 2017-02-15
Thanks for your help. I did a live boot from USB and ran boot repair. After that I was able to use Ubuntu, but not windows, however I was having trouble updating some packages in Ubuntu and it looked like something was corrupted so I reinstalled Ubuntu.

Now I can use Ubuntu normally. I've included a picture from Gparted and my current boot options. It looks like my windows partitions have some kind of issue. 

1) What can I do about my window partitions? (aside from deleting them, I'm not there yet)

2) Do my boot options look correct? Is windows boot manager the correct option for windows 10? I'm hesitant to select it because I selected it  before the Ubuntu reinstall and windows tried to fix something, and then I had trouble with Ubuntu.

Thanks

---

### Post by martemarziano on 2017-02-15
> **agielchinsky said:**
>  Do my boot options look correct? Is windows boot manager the correct option for windows 10? 
Your boot options look correct and "windows boot manager" is the option you choose if you want to boot into Windows. I am not sure what your next steps should be but I am sure more knowledgeable people will soon come along and help you out.

---

### Post by oldfred on 2017-02-15
Are you trying to boot Windows from grub menu or from UEFI boot menu, often f12 or f10?
See if Windows boots directly from UEFI.

Grub only boots working Windows.
And that means it cannot be hibernated nor need chkdsk.
And Windows fast start is a default setting, and Windows updates may keep turning it on.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by agielchinsky on 2017-02-15
I tried booting through UFEI (F9 on my HP) and got the options in the picture below. When I selected Windows Boot Manager I got the following error:

"Boot device not found

Please install an operating system on your hard disk.
Hard disk - (3F0)

F2    system diagnostics"
 

How do I get Windows working again?

Thanks

---

### Post by agielchinsky on 2017-02-15
I tried mounting my windows partition (the large one) from Disks in Ubuntu and got this error

Error mounting /dev/sda3 at /media/aryeh/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda3" "/media/aryeh/Windows"' exited with non-zero exit status 18: Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda3': No such file or directory
 (udisks-error-quark, 0)

---

### Post by agielchinsky on 2017-02-15
[http://paste2.org/7vw7Hn8x](http://paste2.org/7vw7Hn8x)

from Boot Repair

---

### Post by martemarziano on 2017-02-15
I believe you have to repair your MBR. This is how you can proceed:
[http://www.pcworld.com/article/3113585/windows/how-to-repair-windows-master-boot-record-and-fix-your-bricked-pc.html](http://www.pcworld.com/article/3113585/windows/how-to-repair-windows-master-boot-record-and-fix-your-bricked-pc.html)

ps. this a is only a suggestion from a tech novice, if you are unsure as to if this is the right procedure, please wait for the cavalry.

---

### Post by oldfred on 2017-02-15
You partition pic & Summary report show errors on the main Windows install.
The errors on the system reserved you can ignore as that has to be an unformatted partition, and Linux shows unformatted as an error.

Linux also cannot see or mount read/write NTFS partitions that are hibernated or need chkdsk. So grub will not boot Windows in either of those cases or if it otherwise is broken.
And if you cannot directly boot from UEFI, there is another issue.

I thought with UEFI, the BCD was also in the ESP - efi system partition, but not sure. Check if missing /boot/BCD

Also not sure of exact format of UEFI entry for Windows.

Did you at any point reformat ESP?
UEFI uses gpt's GUID as part of standard UEFI entry, but you Windows has a different structure, but number does not look like a current GUID. It says VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb). That must be some sort of default number as this user with Gentoo has exact same 99e275... number.
[https://forums.gentoo.org/viewtopic-t-1035390-start-0.html](https://forums.gentoo.org/viewtopic-t-1035390-start-0.html)
and this same number for a grub2 entry?
[https://bbs.archlinux.org/viewtopic.php?id=206280](https://bbs.archlinux.org/viewtopic.php?id=206280)

And you left Windows hibernation on. Grub cannot then boot Windows.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 


This just shows entries. 
sudo efibootmgr -v

You can add a standard UEFI entry , but do not know how to add a vn:
       New Windows entry - assumes default sda1  add     -d /dev/sda -p 2 , see man efibootmgr for details.

     Yours is sda1:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" 

But then you have two "Windows Boot Manager" entries. Some complain, others let you have multiple, but do not show if different.
If you have to delete one use efibootmgr
      
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). With Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by agielchinsky on 2017-02-16
I gave up, wiped everything and reinstalled Ubuntu. My SSD is only 256 GB and dual booting with any real windows partition would have eaten into the little space I have.

Thanks for all your help, now that my computer is Ubuntu only I'll probably be on this forum a lot more!

---

