---
title: "Kernel Panic After GRUB update"
date: 2017-03-22
forum: New to Ubuntu
---

### Post by verzgr on 2017-03-22
I have very little knowledge in Ubuntu and Linux in general.
I dual booted Ubuntu with Windows 10, but Windows 10 wasn't showing up in Grub,
so I used the command > sudo update-grub and then I could boot Windows 10 and Ubuntu.
But after my first restart when I tried to boot ubuntu I got this error: > end Kernel panic - not syncing: VFS: Unable to mout root fs on unknown-block(0,0)   [URL="http://i.imgur.com/JjEzYeA.png"](IMAGE)
[/URL]
Every tip would be appriciated, cause I have no idea what I can do. (I haven't found any answers in other posts)

---

### Post by yancek on 2017-03-22
After running sudo update-grub, did you boot into both windows 10 and Ubuntu consecutively?  Which first/last.  Do you have windows hibernated?  Fast boot and related options on/off?
You probably will need to post more information which you can get by running boot repair.  If you don't have it on a CD, go to the site below and download and burn it to a CD and boot the CD selecting the Create BootInfo Summary option.  You will get a link at the end, post it here and that should provide more details and someone should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

