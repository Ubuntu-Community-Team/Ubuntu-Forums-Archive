---
title: "grub rescue - trouble removing Lubuntu"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by cudfather on 2012-12-31
Hello guys,
I have a problem with my mother's Windows 7 netbook. Some time ago I installed Lubuntu on it, but I didn't really use it, so I decided to remove it. Before removing its files I made myself a boot USB flashdrive to fix the MBR after the removal of Lubuntu (I used Hiren's BootCD, put it on a flashdrive).

Here's the problem: when I decided to try it out before deleting Lubuntu, both systems (Windows and Lubuntu) became inaccessible. I get the following message with the USB drive sticked in:
"An operating system wasn't found. Try disconnecting any drives that don't contain an operating system.
Press any key to restart"
Then I press a key, it yields:
"error: no such partition.
grub rescue>"

When I start the computer without the USB sticked in, it just says:
"error: no such partition.
grub rescue>"

So, the bootable USB is inaccessible AND so are the systems. Please help.

---

### Post by sudodus on 2012-12-31
Have you set your mother's computer to boot from USB?

Maybe Hiren's boot CD was not properly installed to the USB drive?

Use the Lubuntu install drive to boot a live session, and from it install or repair grub. You can boot Windows from grub as usual, even if you don't have Lubuntu installed.

If you no longer have Lubuntu on a USB drive but have another computer available, you can get it back.

Or if you have or get some installation or repair media for Windows, you can use that to reinstall the boot sector.

---

### Post by cudfather on 2012-12-31
Yes, it's set to boot from USB.
Yes, the Hiren's BootCD was installed properly - I could access it and browse through it. Problems began after rebooting.

I've formatted the Lubuntu install drive already, I'll make a new one and then tell you how it went.

Thanks for the swift reply :)

---

### Post by sudodus on 2012-12-31
> **cudfather said:**
> Yes, it's set to boot from USB.
Yes, the Hiren's BootCD was installed properly - [COLOR="Red"]I could access it and browse through it[/COLOR]. Problems began after rebooting.
...
But that is not the same as being bootable. You must use a special tool to make a bootable USB drive from an iso file. Can you test that it works in another computer?

---

### Post by cudfather on 2012-12-31
I meant, I could access it and browse it while in DOS. Not in the Windows Explorer. I guess that's what it's meant to do.

---

### Post by sudodus on 2012-12-31
I may have misunderstood what you meant. But anyway, please test if Hiren's Boot drive is bootable in another computer (if you have another computer available).

Otherwise reinstalling Lubuntu is a quick fix (it only costs some 3-4 GB of disk space). And afterwards you can remove most of it (if your mother needs the space). I think you really need only the /boot directory to boot Windows (and/or other operating systems).

---

### Post by cudfather on 2012-12-31
I wanted to remove Lubuntu since I don't use it anymore (got a new laptop). My mother was annoyed by the necessity of selecting Windows on boot (dual boot menu), as opposed to automatic Windows startup on a Lubuntu-free computer.

---

### Post by cudfather on 2012-12-31
@Sudodus: could you please explain what you mean by:
Use the Lubuntu install drive to boot a live session, and from it install or repair grub. You can boot Windows from grub as usual, even if you don't have Lubuntu installed.

I got the Lubuntu install drive now, did a repair session, it said 1 file was broken. When I remove it and boot normally from HDD, it still says "grub rescue", so it's not solved. How do I go to a Live session?

EDIT:
By repair session I mean File Integrity Check.

---

### Post by sudodus on 2012-12-31
> **cudfather said:**
> @Sudodus: could you please explain what you mean by:
Use the Lubuntu install drive to boot a live session, and from it install or repair grub. You can boot Windows from grub as usual, even if you don't have Lubuntu installed.

I got the Lubuntu install drive now, did a repair session, it said 1 file was broken. When I remove it and boot normally from HDD, it still says "grub rescue", so it's not solved. How do I go to a Live session?

EDIT:
By repair session I mean File Integrity Check.
A live session is to run Lubuntu booted from the USB drive (not install directly, not memtest, not file integrity check...).

But since the file integrity check found an error, you'd better check with md5sum, if your download was good. If bad, download again, if good, make a new attempt to make a USB boot drive from the iso (and check the file integrity again).

You can install Lubuntu and let it sit there. And from Lubuntu you can change the grub setting, so that the computer boots into Windows directly (or after say 2 seconds).

In the file /etc/default/grub you edit the lines

```
GRUB_DEFAULT=0
``` to
```
GRUB_DEFAULT=[COLOR="Red"]X[/COLOR]
```
where [COLOR="red"]X[/COLOR] is the line number where Windows is started. If Windows is started from the sixth line, [COLOR="red"]X[/COLOR] should be [COLOR="red"]5[/COLOR] (because the first line number is 0).
and
```
GRUB_TIMEOUT=10
``` to
```
GRUB_TIMEOUT=2
```

See also [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

***Edit***: you need superuser privileges, so edit as sudo:

```
sudo leafpad /etc/default/grub
```

---

### Post by cudfather on 2012-12-31
That sounds good, though I've ran into two issues:
1. Live mode brings up console mode only, no GUI (not sure if intended), can't edit grub from there
2. Installing it on a partition I used to have Lubuntu on is impossible (brings up an error)

What can be done about any of these?

---

### Post by sudodus on 2012-12-31
> **cudfather said:**
> That sounds good, though I've ran into two issues:
1. Live mode brings up console mode only, no GUI (not sure if intended), can't edit grub from there
2. Installing it on a partition I used to have Lubuntu on is impossible (brings up an error)

What can be done about any of these?
Lubuntu usually runs fine on netbooks, at least that is my experience.

Which version are you running?
Did it pass the file integrity test?

Try with some boot option. See these links
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2") and
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by sudodus on 2012-12-31
And what computer is it: brand name, cpu, ram, graphics chip?

How many partitions are there on the hard disk drive? If four your might need to install wubi or delete one partition.

Do you remember how the previous Lubuntu system was installed?

---

### Post by arpanaut on 2012-12-31
This tool Boot Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Has in it's advanced options has the ability to repair/reinstall the Windows boot files into the MBR and allow you to boot directly into windows, grub will no longer be in the MBR and your Mother will be pleased.

---

### Post by cudfather on 2013-01-01
Thank you sudodus and arpanaut, the Boot Repair tool finally did it :)

Don't know what I'd do without your help. See you around!

---

