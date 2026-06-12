---
title: "Can't boot Ubuntu after Windows install"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by macakcira on 2013-11-04
OK, I have installed Ubuntu first and then Win 7, and after that I don't get dual boot option. The system automatically loads Windows like it is the only OS. 

I want to have dual boot with Ubuntu and Windows 7, how do i do that? 

Thanks

---

### Post by Impavidus on 2013-11-04
[Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) should fix that. It's a common problem.

---

### Post by macakcira on 2013-11-04
[COLOR=#000000]I tried boot repair, but this is what I get:

1) "LDM-blocker detected. Please backup your data before this operation. Do you want to continue?" - I clicked yes[/COLOR]

[COLOR=#000000]2) "LDM-blocker detected. This will delete the 6th sector of sda. Do you want to continue?" - I clicked no. That sounds scary. After that rebooted, nothing changed, only Windows.

Can I just reinstall Ubuntu as I don't have anything important there? Will then I get dual boot option?[/COLOR]

---

### Post by Impavidus on 2013-11-04
That's not very common, but I found this post, which isn't very old: [http://ubuntuforums.org/showthread.php?t=2102460](http://ubuntuforums.org/showthread.php?t=2102460)

If it doesn't help, did boot-repair give a link with a summary? Also, does Windows use dynamic partitions? It's something we don't like when using Ubuntu, but Windows is often very eager about using dynamic partitions.

---

### Post by sandyd on 2013-11-04
> **macakcira said:**
> [COLOR=#000000]I tried boot repair, but this is what I get:

1) "LDM-blocker detected. Please backup your data before this operation. Do you want to continue?" - I clicked yes[/COLOR]

[COLOR=#000000]2) "LDM-blocker detected. This will delete the 6th sector of sda. Do you want to continue?" - I clicked no. That sounds scary. After that rebooted, nothing changed, only Windows.

Can I just reinstall Ubuntu as I don't have anything important there? Will then I get dual boot option?[/COLOR]

See [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

Workaround #3 is probably the one you want

---

### Post by macakcira on 2013-11-04
OK, now I'm writing you from Linux. I have reinstalled it and now I have dual boot options. That boot repair is some scary thing.

---

### Post by sandyd on 2013-11-04
> **macakcira said:**
> OK, now I'm writing you from Linux. I have reinstalled it and now I have dual boot options. That boot repair is some scary thing.

isnt boot repair - its a bug in grub

---

