---
title: "Two &quot;Windows 7 boot loaders&quot;"
date: 2014-10-11
forum: New to Ubuntu
---

### Post by shravan2 on 2014-10-11
I've installed Ubuntu 14.04 LTS on the same hard drive(sda) which already has Windows 7 OS installed on another partition of this hard drive and I also have a second hard drive(sdb) which is just for backup purpose(no OS installed). Now the problem is, when the computer boots up to the Grub2 window... it shows Ubuntu and two Windows 7 loaders(sda1) and (sdb1).... I formatted (sdb) thrice using Windows 7 OS and Ubuntu OS and Gparted application.
How do I get rid of this second "Windows 7 loader(sdb1)" ?

---

### Post by fantab on 2014-10-11
You must run 'sudo update-grub' to refresh grub menu.

Do both entries boot successfully to Windows?

I have come across this issue on HP laptop... for me only one entry boots to windows. I ignored the other. 
(I am not sure what really the issue was and by then I had come to know the ease of custom menus).

If it bothers you then you can create your [custom grub menu]("https://help.ubuntu.com/community/Grub2/CustomMenus") and  '[maintenance free custom grub menu]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")'.
More [Grub info]("https://help.ubuntu.com/community/Grub2").

Welcome to the forum.

---

### Post by Mark Phelps on 2014-10-11
> How do I get rid of this second "Windows 7 loader(sdb1)" ? Had same problem -- but the "fix" was more trouble than it was worth.

Those entries are created by something know as os_prober -- and that looks for specific Windows files to determine if an OS is on a partition.

Typical preloaded Windows spreads those files over two partitions -- so, os_prober thinks Windows is installed in both partitions.

In my case, I have to choose the second instance to boot.

You can also install Grub-customizer and use it to both customize the boot menu and to set the default to either of the Windows entries.

---

### Post by shravan2 on 2014-10-11
Only the first entry(sda1) boots to Windows, thanks for the reply.

---

### Post by shravan2 on 2014-10-11
> **Mark Phelps said:**
> Had same problem -- but the "fix" was more trouble than it was worth.

Those entries are created by something know as os_prober -- and that looks for specific Windows files to determine if an OS is on a partition.

Typical preloaded Windows spreads those files over two partitions -- so, os_prober thinks Windows is installed in both partitions.

In my case, I have to choose the second instance to boot.

You can also install Grub-customizer and use it to both customize the boot menu and to set the default to either of the Windows entries.

Thanks for the info.

---

### Post by shravan2 on 2014-10-11
> **fantab said:**
> You must run 'sudo update-grub' to refresh grub menu.

Do both entries boot successfully to Windows?

I have come across this issue on HP laptop... for me only one entry boots to windows. I ignored the other. 
(I am not sure what really the issue was and by then I had come to know the ease of custom menus).

If it bothers you then you can create your [custom grub menu]("https://help.ubuntu.com/community/Grub2/CustomMenus") and  '[maintenance free custom grub menu]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")'.
More [Grub info]("https://help.ubuntu.com/community/Grub2").

Welcome to the forum.

'sudo update-grub' worked for me, thank you.

---

