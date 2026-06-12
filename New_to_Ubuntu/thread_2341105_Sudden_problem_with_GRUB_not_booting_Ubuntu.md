---
title: "Sudden problem with GRUB not booting Ubuntu"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by jacobono on 2016-10-24
Hey there,


I'm not completely new to Ubuntu, but I have only made one computer and put Ubuntu on it.

Did a lot of research, installed 12.10 from a live CD.

That was ~3 years ago, and it has held up as my NAS -- and it survived the upgrade(s) to 14.04.

Just yesterday I brought it up from a command line reboot and it just wouldn't boot up -- it kept sending me to the BIOS after showing me the black and white dialog box that usually has _*"Start Ubuntu 14.04"*_ but instead only has something like _*"Set up system"*_.

The BIOS shows the SSD with the OS on it and correctly shows the UEFI tag (just like I installed it with).

No dice starting anything -- here is what I have done so far:

[LIST]
[*]ran a live disk of gparted
[LIST]
[*]can see all of my drives, nothing looks corrupt.
[/LIST]

[*]ran a live disk of Ubuntu 16.04
[LIST]
[*]checked disk for error -- none showed up
[*]tried to install it, progressed until it recognized that I currently have Ubuntu 14.04 installed on the SSD
[*]tried to install it side by side 14.04 but it couldn't do it and crapped out trying to resize where to put 16.04
[/LIST]

[*]Ran boot-repair
[LIST]
[*]running the info script and it is at this pastebin  --->  [http://paste2.org/eCAF8a6g](http://paste2.org/eCAF8a6g)
[*]running an actual repair just hangs though -- the thing it hangs on every time is _*"purge kernels then re-intall last kernel sdb2 (ins) this my take a few minutes..."*_
[LIST]
[*]it took a whole night and made no progress from there.
[/LIST]
[/LIST]
[/LIST]
      
I'm hoping that someone can help me after reading the info script.

I'd love to learn a little bit more about this and what I can do to fix it (maybe what happened to cause it).  :)

I set up the drives to have 2 HDD's for data and I used zfs.  Those are sda and sdc -- and they both appear to be intact.

The SSD was the only drive I installed Ubuntu on (no dual boot) and seems ok too, I just can't get it to load.

I think it is the boot loader, but I am a little bit out of my element in regards to fixing it without any help.

Any help would be much appreciated.

Thanks, 

Daniel

---

### Post by oldfred on 2016-10-25
In UEFI mode, grub only installs to drive seen as sda.
You show ESP - efi system partition as sdb1, so you will not get grub to correctly install.
You can add an ESP on sda, disconnect drive seen as sda, or make sure SSD is in SATA0 port.
I had to make sure on my systems that I installed SSD to SATA0 and used SATA ports in order that I wanted drives seen. Skipping port or having my DVD in middle has caused issues.

You also have zfs file system, which I do not know. You probably even need to add the drivers to live installer so Boot-Repair and scripts can even see that format.

---

### Post by jacobono on 2016-10-27
Was able to fix the problem!

Posting here for a trail in case any one else stumbles upon this thread.

I tried removing all other drives and having the SSD moved to SATA0, but that still didn't seem to help boot-repair from not hanging nor did it boot properly.

Moved on to the manual method described in [this thread]("http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows/88432#88432").

That actually was successful in repairing boot, I still couldn't get it to actually boot up.

What finally worked was [this thread]("https://ubuntuforums.org/showthread.php?t=2223856&page=3&p=13025073#post13025073")! 

This step didn't work for me, but I kept going anyway.

```
[COLOR=#000000][FONT=&amp]sudo apt-get install grub-efi-amd64[/FONT][/COLOR]
```

I decided to use boot repair again as outlined in the latter thread (didn't think command line would work).
I remembered that boot-repair was getting stuck trying to purge and reinstall the last kernel, so I just removed that option from the advanced configuration and tried again.

It worked after that.

I learned that it is probably a really good idea to use the same version of a Live CD as your OS.

boot-repair did the rest, purged some packages and correctly installed ```
grub-efi-amd64
```.

Which are probably the two things I was missing.

Rebooted after following boot-repair and moved the SSD back to sdb and every thing works again.  :o

---

