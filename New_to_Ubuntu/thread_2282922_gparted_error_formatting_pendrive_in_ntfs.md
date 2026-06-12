---
title: "gparted error formatting pendrive in ntfs"
date: 2015-06-17
forum: New to Ubuntu
---

### Post by Sabari_Balan_Ravic on 2015-06-17
I tried to format my pendrive in ntfs using gparted... This is what I got.

[TABLE]
[TR]
[TD="colspan: 2"]**Format /dev/sdb as ntfs**  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]calibrate /dev/sdb  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][I]path: /dev/sdb
start: 0
end: 30489407
size: 30489408 (14.54 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]clear old file system signatures in /dev/sdb  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]write 68.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 4.00 KiB of zeros at byte offset 15610572800  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]flush operating system cache of /dev/sdb  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]set partition type on /dev/sdb  00:00:00    ( ERROR )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]libparted messages    ( INFO )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][I]/dev/sdb: unrecognised disk label


Can you help me fix this problem. 
I have to format it in ntfs to make it bootable windows 7 usb stick [/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2015-06-17
Do not know why gparted has issues.

 Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by monkeybrain20122 on 2015-06-17
Why do you want your usb drive in NTFS? I just can't think of a reason.

---

### Post by Sabari_Balan_Ravic on 2015-06-17
I actually need to create a windows 7 ultimate bootable usb from ubuntu. For that I was instructed to format usb drive in ntfs and set boot flag to it. I tried unetbootin to do that in fat32 . But when I started booting , it showed boot error. I'll be happy to receive any suggestion from you regarding this.

---

### Post by monkeybrain20122 on 2015-06-18
Since you are using Windows just use a Windows partition tool. NTFS is Microsoft's format.

---

