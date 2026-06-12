---
title: "Installation type empty on ubuntu-16.04.3-desktop-amd64 for a dual boot"
date: 2017-12-15
forum: New to Ubuntu
---

### Post by boreduser on 2017-12-15
[COLOR=#111111][FONT=Ubuntu]I'm trying to install a dual boot (with Window 10) on my [/FONT][/COLOR]K401UQ-[COLOR=#111111][FONT=Ubuntu]FR016T
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Everything works well [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]until I go on step "Installation type".

[/FONT][/COLOR][IMG]https://i.stack.imgur.com/kYKHU.jpg[/IMG]

---

### Post by oldfred on 2017-12-15
Are you booting in UEFI mode? See also steps to install in link in my signature.

Most common issue is that you have Windows fast start up on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

But can be drive is RAID or Intel SRT, or some other drive issues.

Looks like that model has nVidia also:
       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

