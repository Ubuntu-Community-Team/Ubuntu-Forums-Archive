---
title: "Bootloader woes"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by snoish on 2013-01-25
Hi,
 
Model: Samsung NP700G7C
OS: Windows 8
Linux: Ubuntu (latest version)
 
So I burnt the latest ISO of linux to make a dual boot on my windows 8 laptop.
 
Installed it OK, selected the option to dual boot during installation.
 
Then noticed that I could no longer boot into windows 8, it was coming up with a drive missing error, drive map invalid.
 
So, after investigating and running boot-repair, I see that I should boot from recovery disc, but I cannot get my laptop to do this. I have set the BIOS to boot from DVD drive first, but I just get the windows needs repair option, I dont even get the Grub menu anymore.
 
Can anyone help me with this?

---

### Post by kc1di on 2013-01-25
you said you ran boot repair did you save the web page it gave you so we can look at the log of the repair?

if you wrote it down please post here.

More than likely the problem lies the the secure boot option of windows 8.

if your machine is a uefi machine [this page ]("http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/")may be of help.

---

### Post by snoish on 2013-01-25
I did:
 
[http://paste.ubuntu.com/1570325](http://paste.ubuntu.com/1570325)
 
If that helps!
 
Thanks for the link, but I can't even get the laptop to boot from dvd, usb or hard drive now I just get the same win 8 error message. It doesn't matter which one I select from the bios.
 
It might be that this is a samsung laptop and you have to press a specific key to get it to work, but I can't find anything that works at the moment i.e. F2, F4, F12.
 
In case it helps, this laptop has two hard drives, one ssd and one standard. I believe that windows was originally booting from the ssd but stored stuff on the regular drive. I'm a novice at Linux so don't really understand what has happened.

---

### Post by snoish on 2013-01-25
I've managed to find that the boot selection key is F10, thanks for you help. I' might come back for your help I may be back if I still can't get it to work lol

---

### Post by kc1di on 2013-01-26
Glad you've found a solution if it fixes the problem, please take a moment and mark this thread as solved.
:p

---

### Post by oldfred on 2013-01-26
It looks like you tried to install wubi, which is not a true partitioned dual boot. But wubi does not work with gpt partitions.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

    
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

