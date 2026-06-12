---
title: "bootloader error at end of dual boot 12.04 install"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by n17paul on 2012-07-20
I installed ubuntu 12.04 onto a laptop which already had W Vista on it, as I want to have a dual boot system.
Install appeared to go fine, having selected default options for partitioning the disc. However, right at the end  I got the error "Sorry, an error occurred and it was not possible to install the bootloader at the specified location". When I boot up it goes straight into Vista with no dual boot option.
I've attached the results.txt from bootinfoscript.
I'm new to Linux so would really appreciate some help.

---

### Post by NikTh on 2012-07-20
Hi ,
try to use this automatic tool  [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) and see if fix your problem. 

Thanks

---

### Post by oldfred on 2012-07-20
You are not showing grub2 installed at all. Not just the somewhat normal  error of the  grub2 boot loader not installed to the MBR.

 You can try the advance options in BootRepair to reinstall grub2.

---

### Post by n17paul on 2012-07-21
Thanks NikTh and oldfred. Boot-Repair doesn't appear to be on my live ubuntu system so I presume I need to download. I'm a little wary of using a GUI driven app for which I don't really know what it is happening underneath - can I be sure that it won't mess with my W Vista boot option?
I'd be happy to do it through a terminal session if that is more reliable - I'm new to Linux but comfortable  scripting, using command line.

---

### Post by NikTh on 2012-07-21
> **n17paul said:**
> Thanks NikTh and oldfred. Boot-Repair doesn't appear to be on my live ubuntu system so I presume I need to download. I'm a little wary of using a GUI driven app for which I don't really know what it is happening underneath - can I be sure that it won't mess with my W Vista boot option?
I'd be happy to do it through a terminal session if that is more reliable - I'm new to Linux but comfortable  scripting, using command line.


Hi , 

Boot from a liveCD / Usb , choose "Try Ubuntu" , open a terminal (Ctrl+alt+t) and run this command 
```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```Its one command , copy-paste it from here to your terminal.
Then select [recommended] repair and when finish , reboot to see if problem corrected.

Regards

---

### Post by n17paul on 2012-07-21
I've executed the code above, thanks for the input. I've now got a dual boot screen that is fine when I select W Vista. However, the boot into ubuntu gets stuck with the following:
"Warning: Fake initctl called, doing nothing."
Updated results from the boot-repair is at [http://paste.ubuntu.com/1103323/](http://paste.ubuntu.com/1103323/)
Any more help much appreciated!

---

### Post by oldfred on 2012-07-21
I have never seen that error. But perhaps some more parts were not installed correctly? This says a file util-linux in /bin/mount is missing.

[http://www.linuxforums.org/forum/ubuntu-linux/185846-wont-boot-up-2.html](http://www.linuxforums.org/forum/ubuntu-linux/185846-wont-boot-up-2.html)
> Just FYI, I finally figured it out, the /bin/mount belongs to the "mount" package...clever.  It comes
 from the util-linux source package though.  So if you installed util-linux, that would not have replaced /bin/mount 
 with a new copy.  You could always manually download it if you need to, it's here:
 

Two choices, that I see. A full chroot into system and a full update from that to see it that fixes it. Or reinstall.

---

### Post by YannBuntu on 2012-07-21
Hello
[QUOTE=Boot-Repair final message]The boot files of [Ubuntu 12.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair].[/QUOTE]

You may need a separate /boot partition. Tutorial here: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by n17paul on 2012-07-22
reinstalled ubuntu on top of the malfunctioning original install, without making any changes to partitions. Worked a treat - will boot up into either W Vista or ubuntu. Many thanks for your help!

---

