---
title: "Triple booting: Vista, Gusty, and Hardy"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Onay on 2008-05-05
Okay here's the break down...

I have vista installed, and I am using EasyBCD to manage booting between my 2 ubuntu installations. Grub is installed onto my partition containing my Gutsy installation. Problem is I just installed Hardy freshly onto a new partition without any grub, and now I cannot boot into it.

Do I need to install grub on that partition and allow the windows bootloader to load it? Or can I add it to my existing grub menu.lst on the Gutsy partition? If so, how do I do that?

SOLVED: Thanks guys for the responses, using the symlink works perfectly.

---

### Post by confused57 on 2008-05-05
> **Onay said:**
> Okay here's the break down...

I have vista installed, and I am using EasyBCD to manage booting between my 2 ubuntu installations. Grub is installed onto my partition containing my Gutsy installation. Problem is I just installed Hardy freshly onto a new partition without any grub, and now I cannot boot into it.

Do I need to install grub on that partition and allow the windows bootloader to load it? Or can I add it to my existing grub menu.lst on the Gutsy partition? If so, how do I do that
You "should" be able to add an entry to boot Hardy from Gutsy's menu.lst.  Do you mean grub wasn't installed at all on Hardy, or it's installed but you didn't designate where to install grub's IPL(Initial Program Loader) or stage1?  If you're not sure, boot into Gutsy:
```
sudo grub
find /boot/grub/stage1
quit
```
If it shows a root entry for your Hardy install, you can use a configfile entry to boot Hardy...if it doesn't show a root entry, grub probably isn't installed, but you can boot using a symlink entry:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

To add an entry to Gutsy's menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Add the entry to the very end of the menu.lst, quit & save.

If you're unsure of the entry you need to use, post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by Onay on 2008-05-07
Thanks so much for your response it was really helpful, however I attempted to add the Hardy entry to my menu.lst but I don't know certain things to put in it. For instance my Gutsy entry has a UUID, and I'm not entirely sure what it is for Hardy. I also tried booting the kernel from (hd0,3) (the 24 one) it told me that it couldn't find the file, when I clearly see in my sda4 that it exists.

```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed1e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31454208    7  HPFS/NTFS
/dev/sda2            3917        6778    22989015   83  Linux
/dev/sda3            9329        9730     3229065    5  Extended
/dev/sda4            6779        9328    20482875   83  Linux
/dev/sda5            9329        9730     3229033+  82  Linux swap / Solaris
```

Thanks again for your help

---

### Post by confused57 on 2008-05-07
Did you get any results for "find /boot/grub/stage1"?

You can still try a symlink entry to boot Hardy:
```
title        Ubuntu Hardy
root         (hd0,3)
kernel       /vmlinuz root=/dev/sda4 ro quiet splash
initrd       /initrd.img
boot
```

---

### Post by bodhi.zazen on 2008-05-07
You might want to consider chainloading, it makes life much easier :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by Onay on 2008-05-07
Thanks you guys, the symlink works beautifully. Haha now on to fix all my other problems (I use a wireless usb dongle among other unsupported hardware)

---

