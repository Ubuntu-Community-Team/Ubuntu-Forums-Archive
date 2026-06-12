---
title: "Dual boot broken from windows 7 to 10 upgrade"
date: 2015-12-07
forum: New to Ubuntu
---

### Post by HaggardHero on 2015-12-07
Hi there,

Through my research I've found that this issue is relatively common for those in similar situations. However, I have not yet found a solution to this problem.

I started out with a Windows 7 machine & then I was able to figure out how to dual boot with Ubuntu installed as well. 

I decided it was time to upgrade Windows 7 to Windows 10 & here I am with my problem: after a couple reboots from the windows upgrade process, I now get this error message: "error: no such partition. grub rescue>"

I started to follow this guide ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) in order to fix the issue but it leads me to the same error message. I added the boot-repair iso to an empty flash drive & then I did the recommended repair. It give me a successful message, but again... same error upon reboot.

Here's my log/pastebin:  [http://paste.ubuntu.com/13806564/](http://paste.ubuntu.com/13806564/)

I'm still pretty new to Linux/Ubuntu but I'm getting the hang of it all... I just don't know what to do next. Thanks in advance.

---

### Post by oldfred on 2015-12-07
Windows has had a bug for years. On major updates it seems to forget to write a Linux partition back into partition table.

```
 /dev/sdc4[COLOR=#ff0000]         910,391,294[/COLOR]   976,771,071    66,379,778   5 Extended
/dev/sdc5 [COLOR=#ff0000]        960,174,080[/COLOR]   976,771,071    16,596,992  82 Linux swap / Solaris


```

Your Linux partition was from one or two sectors after the start of the extended and ended a few sectors before the start of the swap partition. Many have just restored the partition and reinstall grub to have system fully restored.

Some have posted that parted rescue is easier if you know start & end sectors. Testdisk uses the older CHS so is a bit more difficult to know which partition is the one you want as it finds all the old ones as well. 

       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

