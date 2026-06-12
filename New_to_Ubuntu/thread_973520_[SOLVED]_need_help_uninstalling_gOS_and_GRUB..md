---
title: "[SOLVED] need help uninstalling gOS and GRUB."
date: 2008-11-06
forum: New to Ubuntu
---

### Post by mikeftl on 2008-11-06
Im trying to remove grub and linux so only windows vista is on my computer.(gOS is on my microsd card and windows is on my harddrive)
After taht i am going to install ubuntu to my microsd card/
how can i make it so that nexttime when i install ubuntu it loads windows by default, and it only loads linux when i have the sd card inserted.
(right now it wont load without the sd card inserted)
thanks.
I also need help with my partitions,
(here is what i am looking at)
I dont know which to delete and stuff.

[[img]http://img440.imageshack.us/img440/3021/screenshotng4.png[/img]]("http://imageshack.us")
[[img]http://img440.imageshack.us/img440/screenshotng4.png/1/w1024.png[/img]]("http://g.imageshack.us/img440/screenshotng4.png/1/")
[[img]http://img503.imageshack.us/img503/1789/screenshot1tg3.png[/img]]("http://imageshack.us")
[[img]http://img503.imageshack.us/img503/screenshot1tg3.png/1/w1024.png[/img]]("http://g.imageshack.us/img503/screenshot1tg3.png/1/")

---

### Post by Bölvaður on 2008-11-06
To remove ubuntu you delete the partitions, simple as that.
To let it boot straight into windows you need windows to take over the mbr again and s'it on everything else in the master boot record.

I think you should first deal with the windows problem first before you change the ubuntu partitions. And remove them by live cd with gparted.

---

### Post by mikeftl on 2008-11-06
> **Bölvaður said:**
> To remove ubuntu you delete the partitions, simple as that.
To let it boot straight into windows you need windows to take over the mbr again and s'it on everything else in the master boot record.

I think you should first deal with the windows problem first before you change the ubuntu partitions. And remove them by live cd with gparted.
which partitions do i remove?
and how do i ix the windows mbr?
Please help!

---

### Post by SuperSonic4 on 2008-11-06
it looks like just windows on sda so you don't need to delete anything.

to fix window's MBR you insert the windows cd/dvd and choose repair I believe.

It does mean you'll have to use the BIOS to boot from the flash pen before the hdd

---

### Post by mikeftl on 2008-11-06
> **SuperSonic4 said:**
> it looks like just windows on sda so you don't need to delete anything.

to fix window's MBR you insert the windows cd/dvd and choose repair I believe.

It does mean you'll have to use the BIOS to boot from the flash pen before the hdd

my computer did not come with a windows cd ,it came with like built in support or something.
I do havea  windows 2000 disk though.
And is it safe to delete all the partitions on my sd card and reformat it in windows? thanks
(what is another way to fix windows because i do not have the cd)

---

### Post by Durden on 2008-11-06
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download that, burn it to a cd and reboot. Follow their directions for changing the MBR to boot straight to windows.

Then boot from the linux cd and redo your partitions with gpartd.

---

### Post by mikeftl on 2008-11-06
> **Durden said:**
> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download that, burn it to a cd and reboot. Follow their directions for changing the MBR to boot straight to windows.

Then boot from the linux cd and redo your partitions with gpartd.
when i reboot nothing happens? Maybe im doing something wrong

---

### Post by mikeftl on 2008-11-06
> **mikeftl said:**
> when i reboot nothing happens? Maybe im doing something wrong
okay so i did the grub thing.
I got it to work.
Now im on windows and is it alright if i just reformat my sdcard on here?
after that, should i install windows 2000 or ubuntu, which would be better/easier.thanks

---

### Post by SuperSonic4 on 2008-11-07
If you don't mind losing all the data then yes it's fine to do so in windows. I would just leave it as unallocated space by deleting the partition instead of reformatting.This will make it easier, I'd install ubuntu myself but it is up to you.

If you do install ubuntu disconnect the windows drive (sda) because otherwise grub will install and you'd be back where you started

---

