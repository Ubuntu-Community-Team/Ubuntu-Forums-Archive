---
title: "boot problem with ubuntu on HP PAVILION cx0012nl"
date: 2019-10-18
forum: New to Ubuntu
---

### Post by sawcom on 2019-10-18
[COLOR=#000000][FONT=HPSimplifiedLight]Hello everyone[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]Before entering this forum, I tried to find a solution to my problem in different ways, but without result. I came here to ask my problem, I hope to find someone to help me solve it[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]I bought a [COLOR=#ff0000]**HP PAVILION cx0012n****l**[/COLOR] computer and tried to install UBUNTU on it. I burned the Ubuntu ISO disk to USB via a Rufus program and tried to run the device via USB.[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]It worked, but the problem is when I run the Ubuntu desktop, I can not work and I try to open a file or anything on the computer, but it does not move .[/FONT][/COLOR]

---

### Post by sawcom on 2019-10-18
healp Please

---

### Post by uRock on 2019-10-18
Please allow at least 24 hours before bumping your thread. We're all volunteers and sometimes it takes time for someone who can help to see your thread.

---

### Post by oldfred on 2019-10-18
Have you updated UEFI from HP (even if new check version)?
If SSD have you updated firmware?


Did you install in UEFI boot mode?
Did you install the proprietary nVidia driver?

If not, you may need to boot with nomodeset boot parameter for low quality graphics & then install driver.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

